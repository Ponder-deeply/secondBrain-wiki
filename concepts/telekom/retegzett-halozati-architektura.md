---
tags: [concept]
sources: [Laki_Lecture_1.pdf, Laki_Lecture_2.pdf]
derivation: source
kind: model
element: water
updated: 2026-09-25
---

# Rétegzett hálózati architektúra

A hálózati funkciókat egymásra épülő rétegekbe (*layered network stack*) szervezzük: minden réteg csak az alatta lévő réteg szolgáltatását használja, és jól definiált interfészen keresztül nyújtja a sajátját. A küldő oldalon minden réteg saját fejlécet tesz az adat elé (beburkolás), a fogadó oldalon fordított sorrendben leveszi.

## Tartalom

### Előnyök és hátrányok

- **Modularitás** — a hálózati funkciókat egységekbe szervezi.
- **Beburkolás / enkapszuláció** (*encapsulation*) — interfészek definiálják a rétegközi interakciókat; a rétegek csak az alattuk lévőkre épülnek.
- **Rugalmasság** — kód-újrafelhasználás; egy modul implementációja lecserélhető a többi érintése nélkül.
- **Hátrányok** — az interfészek információt rejtenek el, és a sok réteg teljesítménycsökkenést okoz.

A rétegzés két fő tervezési kérdése: *hogyan osszuk rétegekbe* a funkciókat (útvonal-meghatározás, torlódásvezérlés, hibaellenőrzés, biztonság, fairség…), és *hogyan osszuk el őket az eszközök között* (ki felel az útvonalért — a router? ki a torlódásért — a végpont?).

### Egy réteg három jellemzője

| Fogalom | Kérdés |
|---|---|
| **Szolgáltatás** (*service*) | *Mit csinál* az adott réteg? |
| **Interfész** (*interface*) | *Hogyan férhetünk hozzá* a réteghez? |
| **Protokoll** (*protocol*) | *Hogyan implementáljuk* a réteget? |

Ezt a hármast a [[concepts/telekom/osi-referenciamodell]] minden rétegére végigveszi.

### Peer-to-peer kommunikáció

Logikailag minden réteg a másik hoszt **azonos szintű** rétegével kommunikál (a TCP a TCP-vel, a HTTP a HTTP-vel); fizikailag az adat lefelé halad a küldő veremben, átmegy a médiumon, és felfelé a fogadóban. A közbülső eszközök csak az alsó rétegeket valósítják meg: a **switch** a fizikai és adatkapcsolati, a **router** a hálózati rétegig „bontja ki” a csomagot.

### Beburkolás — Internet példa

Egy weboldal útja lefelé a vermen:

1. Alkalmazás: `HTTP fejléc | weboldal`
2. Szállítói réteg: `TCP fejléc | HTTP fejléc | weboldal` — ez a **TCP szegmens**
3. Hálózati réteg: `IP fejléc | TCP szegmens` — ez az **IP datagram**
4. Adatkapcsolati réteg: `Ethernet fejléc | IP datagram | Ethernet trailer` — ez az **Ethernet keret**

Postai analógia: a levél (adat) borítékba kerül, a címke hordozza az útvonal-információt; a posta nem ismeri a levél tartalmát, a címzett pedig semmit sem tud a posta működéséről — csak kicsomagol.

**Vizsgaszempont:** az egyes rétegek adategységének neve (szegmens, datagram/csomag, keret, bit) gyakori tesztkérdés.

### Az Internet homokóra

Az IP réteg a homokóra „dereka”: fölötte sok alkalmazás (HTTP, FTP, RTP, IMAP…) és szállítói protokoll, alatta sok médium (optikai szál, koax, sodrott érpár, rádió…). Az IP-nek köszönhetően minden hálózat képes együttműködni, és minden alkalmazás működik minden médiumon; a réteg fölött és alatt szabadon lehet fejleszteni. Ára: **az IP-t lecserélni nagyon nehéz** — ezt mutatja az IPv6 lassú bevezetése ([[concepts/telekom/ipv6]]).

### Merőleges síkok

- **Vezérlési sík** (*control plane*): hogyan határozzuk meg az útvonalakat? — BGP, RIP, OSPF ([[concepts/telekom/routing-alapok]]).
- **Adatsík** (*data plane*): hogyan továbbítjuk az adatot egy adott útvonal mentén?

### A rétegzés határai a valóságban

Az absztrakció nem mindig tartható: a **tűzfalak** az alkalmazási réteg fejléceit is vizsgálhatják, a **proxyk** alkalmazási végpontot szimulálnak a hálózatban, a **NAT**-ok pedig megtörik a végpont–végpont elérhetőséget ([[concepts/telekom/nat]]).

## Kapocs

- [[concepts/telekom/osi-referenciamodell]] — a hétrétegű referenciamodell rétegenként
- [[concepts/telekom/tcp-ip-modell]] — az Internet négy-, illetve ötrétegű modellje
- [[concepts/telekom/internet-tortenete-es-tervezesi-elvei]] — miért van szükség rétegzésre
