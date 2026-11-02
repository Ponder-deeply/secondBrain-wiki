---
tags: [concept]
sources: [Laki_Lecture_9.pdf, Laki_Lecture_10.pdf]
derivation: source
kind: procedure
element: water
updated: 2026-09-25
---

# TCP: kapcsolatkezelés, folyamvezérlés, megbízhatóság

„A TCP egy **kapcsolatorientált**, **megbízható** szolgáltatás **kétirányú bájtfolyamokhoz**.” Portszámokkal demultiplexál, háromutas kézfogással épít fel kapcsolatot, minden bájtot sorszámoz, a vevő meghirdetett ablakával szabályozza a forgalmat (csúszóablak), és az RTT-ből becsült időkorláttal küldi újra az elveszett szegmenseket. A torlódásvezérlését külön lap tárgyalja: [[concepts/telekom/tcp-torlodasvezerles]].

## Tartalom

### A fejléc (20 bájt + opciók)

| 0–15 bit | 16–31 bit |
|---|---|
| Forrás port | Cél port |
| Sequence Number (sorszám, 32 bit) | |
| Acknowledgement Number (nyugtaszám, 32 bit) | |
| HLen · Flags | Advertised Window (meghirdetett ablak) |
| Checksum | Urgent Pointer |
| Options | |

Fontos 1 bites **flagek**: **SYN** — szinkronizáció, kapcsolatfelépítéshez; **ACK** — fogadott adat nyugtázása; **FIN** — vége, kapcsolatbontáshoz.

### Kapcsolatfelépítés: háromutas kézfogás

Miért kell? Mindkét végponton **állapotot** kell kialakítani; a legfontosabb állapot a **sorszám** (az elküldött bájtok nyilvántartása, véletlenszerű kezdőértékkel).

```
Kliens → Szerver:  SYN     <SeqC, 0>
Szerver → Kliens:  SYN/ACK <SeqS, SeqC+1>
Kliens → Szerver:  ACK     <SeqC+1, SeqS+1>
```

Mindkét oldal értesíti a másikat a saját kezdő sorszámáról, és nyugtázza a másikét. A **+1** azért kell, mert a SYN flag maga is „elfogyaszt” egy sorszámot — a nyugta mindig a következő várt sorszám.

**Problémák:** *kapcsolódási zűrzavar* — azonos hoszt kapcsolatainak egyértelműsítése, a véletlen kezdő sorszám biztonsági okból is kell; *forráshamisítás* (Kevin Mitnick esete) — jó véletlenszám-generátor kell; *állapotkezelés* — minden SYN állapotot foglal a szerveren, erre épül a **SYN flood** DoS támadás. Megoldás: **SYN cookie-k** — a szerver nem tárol kezdeti állapotot, hanem a SYN/ACK sorszámmezőjébe kódolja, a kliensnek pedig vissza kell tükröznie.

### Kapcsolatbontás

Mindkét oldal kezdeményezheti; a másik oldal még folytathatja a küldést (**félig nyitott kapcsolat**, `shutdown()`). Menet: `FIN <SeqA>` → `ACK <SeqA+1>` → (még adat mehet) → `FIN <SeqB>` → `ACK <SeqB+1>`. Az utolsó FIN nyugtája is sorszám + 1.

### Sorszámok

- A TCP absztrakt **bájtfolyamot** valósít meg; **minden bájt számozott**; a sorszám 32 bites, egy idő után körbefordul; kezdetben véletlen.
- A folyamot **szegmensekre** bontjuk, méretüket a **MSS** (*Maximum Segment Size*) korlátozza — úgy kell beállítani, hogy elkerüljük a fragmentációt ([[concepts/telekom/ipv4-fejlec-es-fragmentacio]]). Példa: a 8. szegmens a 13450., a 9. a 14950., a 10. a 16050. bájttal kezdődik.
- **Kétirányú kapcsolat**: mindkét fél küldhet és fogadhat, a két irányban különböző sorszámokkal; adat és nyugta ugyanabban a csomagban utazik (*piggybacking*). Példa: kliens (Seq 1, Ack 23) 1460 bájtot küld → szerver 730 bájt adattal és Ack 1461-gyel válaszol → kliens (Seq 1461, Ack 753) …
- **Miért 32 bites?** A csúszóablakhoz kell: $|\text{sorszámtér}| > 2\cdot|\text{küldő ablak}|$, azaz $2^{32} > 2\cdot 2^{16}$. Emellett az elkóborolt csomagok kivédése: az IP-csomagok maximális élettartama (MSL) 120 s, egy csomag 2 percig bolyonghat.

### Folyamvezérlés — meghirdetett ablak

Probléma: túl sok csomag túlterhelheti a fogadót, és a fogadó pufferének mérete változhat. Megoldás: **csúszóablak** ([[concepts/telekom/csuszoablak-protokollok]]):
- a fogadó elküldi pufferének méretét — ez a **meghirdetett ablak** (*advertised window*);
- $n$ ablakméretnél a küldő $n$ bájtot küldhet nyugta nélkül; minden ACK után léptetjük az ablakot;
- az ablak **akár nulla** is lehet.

A küldő sorszámtengelye: nyugtázott | elküldött, nem nyugtázott (pufferelni kell a nyugtáig) | elküldhető | ablakon kívüli.

**Megfigyelések:** az átvitel $\sim w/\text{RTT}$ ($w$ a küldési ablak); a küldőnek pufferelnie kell a nyugtázatlan csomagokat; a fogadó elfogadhat nem sorrendben érkezőket, amíg elférnek. A TCP ACK **ütemezett** (*ACK clocking*): rövid RTT → gyors ACK → gyorsan csúszó ablak.

**Mit nyugtázhat a fogadó?** (1) minden csomagot; (2) **kumulált nyugta** — az $n$ sorszámú nyugta minden $k < n$-et nyugtáz (TCP alapból ez); (3) **negatív nyugta** (NACK); (4) **szelektív nyugta** (SACK) — mely csomagok érkeztek meg, akár sorrenden kívül (TCP-kiterjesztés).

**Buta ablak szindróma:** nagyon kicsi ablaknál sok apró csomag megy, a fejlécek dominálják az átvitelt — mintha bájtonként küldenénk. **Nagle algoritmusa**: (1) ha az ablak ≥ MSS és az elérhető adat ≥ MSS, küldj teljes szegmenst; (2) különben, ha van nyugtázatlan adat, várakoztasd az adatot pufferben a nyugtáig; (3) különben küldd el. Hátránya a késleltetés; kikapcsolható a `TCP_NODELAY` socket-opcióval.

### Hibadetektálás és újraküldés

- A **kontrollösszeg** a hibás csomagokat jelzi; az IP- és TCP-fejlécből és az adatból számoljuk.
- A **sorszámok** a sorrendhelyességhez: duplikátumok eldobása, sorrenden kívüliek rendezése vagy eldobása, hiányzó sorszám = elveszett csomag.
- A küldő oldalon: **időtúllépés** a hiányzó nyugtákra; ehhez **RTT-becslés** kell; minden nyugtázatlan csomagot pufferelni kell.

**RTO** (*Retransmission Time Out*): ha túl rövid, felesleges újraküldés; ha túl hosszú, lassú reakció. Az eredeti TCP RTT-becslője mozgó átlag:
$$\text{new\_rtt} = \alpha\cdot\text{old\_rtt} + (1-\alpha)\cdot\text{new\_sample},\qquad \alpha \in [0{,}8;\ 0{,}9]\ (\text{jellemzően } 0{,}875),$$
$$\text{RTO} = 2\cdot\text{new\_rtt}\quad(\text{konzervatív becslés}).$$

**Karn algoritmusa:** az újraküldött csomag nyugtájából vett RTT-minta kétértelmű (nem tudni, az eredetire vagy az újraküldöttre jött-e), ezért az **újraküldésből származó mintákat eldobjuk**.

**RTO adatközpontban — TCP Incast:** sok szimultán küldő egy fogadóhoz (Hadoop, MapReduce, HDFS, GFS); a switch pufferei telítődnek, csomagok vesznek el, és mindenki az RTO-ra vár — de az RTO-becslést WAN-ra tervezték, adatközpontban az RTT 1–2 ms vagy kevesebb ([[concepts/telekom/aktiv-sorkezeles-es-dctcp]]).

### Összefoglalás — a definíció három eleme

- **Kapcsolatorientált:** két résztvevő, mindegyiket IP-cím + port azonosítja; a kapcsolatot a pár egyértelműen azonosítja; nincs multi- és broadcast; fel kell építeni és le kell bontani; a lezárásig aktív.
- **Megbízható:** minden csomag nyugtázva; a nyugtázatlanokat újraküldi; fejléc és adat ellenőrzőösszeggel; sorszámozás és sorba rendezés a fogadónál; duplikátumok törlése.
- **Kétirányú bájtfolyam:** két ellentétes irányú bájtsorozat; a tartalmat nem interpretálja; a csomagok időbeli viselkedése változhat; igyekszik időben közel szállítani, és hatékonyan használni a közeget.

**Vizsgaszempont:** a háromutas kézfogás sorszámokkal, a bontás négy lépése; a meghirdetett ablak szerepe; Nagle és a buta ablak; az RTT/RTO képletek és Karn algoritmusa; SYN flood és SYN cookie.

## Kapocs

- [[concepts/telekom/tcp-torlodasvezerles]] — cwnd, slow start, AIMD, Reno, CUBIC
- [[concepts/telekom/udp]] — a kapcsolat nélküli alternatíva, a demultiplexálás alapjai
- [[concepts/telekom/csuszoablak-protokollok]] — a csúszóablak elve az adatkapcsolati rétegben
- [[concepts/telekom/http-es-web]] — a TCP-re épülő alkalmazási protokoll
