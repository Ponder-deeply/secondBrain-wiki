---
tags: [concept]
sources: [Laki_Lecture_12_new.pdf]
derivation: source
kind: overview
element: water
updated: 2026-09-25
---

# Tartalomkiszolgálás: terheléselosztás, CDN és P2P (BitTorrent)

A webes tartalom kiszolgálása az egyetlen „szekrényben álló” szervertől a replikált szervereken és terheléselosztókon át a **CDN**-ekig (*Content Delivery Network*) fejlődött, amelyek a tartalom másolatait a felhasználók közelébe viszik, és DNS-sel vagy anycasttal irányítják a klienseket a legjobb replikához. A **P2P** rendszerek (BitTorrent) ugyanezt dedikált infrastruktúra és központi felügyelet nélkül, a résztvevők egymást segítésével érik el.

## Tartalom

### Miért kell?

- A forgalom nagy része HTTP (a web legalább 52%); a medián objektumméret 2,7 KB, az átlag 85 KB (2007). A HTTP TCP-t használ, így ACK-ütemezett, és webes objektumoknál **valószínűleg el sem hagyja a slow startot** ([[concepts/telekom/tcp-torlodasvezerles]]) — a teljesítményt az **RTT** dominálja.
- Weboldalaknál az RTT, videónál a rendelkezésre álló sávszélesség számít a legtöbbet; **nincs olyan hely, amely mindenkinek a legjobb**.
- A sebesség pénz: Amazon — 100 ms-onkénti oldalbetöltési-idő-csökkenés 1% bevételnövekedést hozott; Shopzilla — 6 s-ról 1,2 s-ra csökkentve 12%-ot. A videóindítási késleltetés növekedésével nő a megszakított nézések aránya. (Boston–Los Angeles ping: ~100 ms.)

### A fejlődés lépései

1. **Egyetlen szerver** — gondok: megbízhatóság (kábelkihúzás, hardverhiba, katasztrófa) és skálázhatóság (*flash crowd*, „Slashdot-hatás”).
2. **Replikált webszolgáltatás** — több szerver: jobb skálázhatóság és megbízhatóság, de melyik szervert használjuk, és hogyan szinkronizáljuk az állapotot?
3. **Terheléselosztó** (*load balancer*) — eszköz, amely a kéréseket szerverek egy csoportja között multiplexálja; minden szerver **egy közös nyilvános IP-n** osztozik, a balancer átlátszóan irányít. Hozzárendelés: véletlen / round-robin vagy terhelés alapú. Kihívás: skálázhatóság, állapot (korábbi döntések nyilvántartása — a RESTful API-k csökkentik). Előny: IP-cím-független skálázás, könnyű karbantartás. Hátrány: drága, **egyetlen hibapont**, és a **hely** kérdése (hová tegyük a Wikipédia balancerét?).
4. **Web cache az ISP-knél** — a tartalom közelebb van, és csak egyszer lépi át a hálózathatárt; de a teljes webtartalom túl nagy, és a tartalom **dinamikus és személyre szabott** (banki oldal, keresési eredmény nem cache-elhető). Ld. még a proxykat: [[concepts/telekom/http-es-web]].
5. **CDN**.

### CDN — Content Delivery Network

A világ bitjeinek legalább fele (valószínűleg 80–90%-a) CDN-en keresztül érkezik. **Célok:** a tartalom replikáinak létrehozása az Internet-szerte; a replikák folyamatos elérhetősége; a kliensek jó teljesítményű replikához irányítása.

**Fő komponensek:** elosztott szerverek (általában más ISP-k belsejében, gyakran IXP-kben), az ezeket összekötő nagysebességű hálózat, a kliensek („eyeballs”), és a „ragasztó”, amely a klienseket a közeli replikához köti. A szerverek **klaszterekben** állnak (a megbízhatóság miatt; egyesek hiba vagy energiatakarékosság miatt offline-ok), jól bekötött **PoP**-okban és ISP-kben. Példák: Akamai (147 ezer+ szerver, 1200+ hálózat, 92 ország), Limelight, Edgecast; továbbá Google, Facebook, AWS, AT&T, Level3.

**Kliensek leképezése szerverekre** — a „legjobb” szerver időben változik (hely, hálózati állapot, terhelés):

- **DNS-alapú átirányítás**: a kliens `www.foo.com`-ot kér, a CDN DNS-szervere a **kérő IP-címe alapján** egy vagy több IP-t ad vissza, **rövid TTL**-lel, hogy korlátozza a cache-elés hatását. Példa (`dig www.fox.com`): CNAME → `www.fox-rma.com.edgesuite.net` → CNAME `a2047.w7.akamai.net` → kilenc A rekord, 4 s TTL-lel ([[concepts/telekom/dns]]).
  - Előnyök: a meglévő, skálázható DNS-infrastruktúrát használja; az URL-ek lényegében változatlanok; a TTL szabályozza a „frissességet”.
  - Korlátok: a DNS-szerver csak a **feloldó** IP-jét látja (feltételezi, hogy a kliens közel van hozzá); a kis TTL-eket gyakran figyelmen kívül hagyják; a tartalomtulajdonos lemond a kontrollról; az unicast címek korlátozhatják a megbízhatóságot.
- **Anycast**: egy IP-cím olyan prefixből, amelyet **több helyről hirdetnek** (pl. 120.10.0.0/16 két AS-ből); a kliens a BGP szerinti legjobb úton a „legközelebbi” példányhoz jut ([[concepts/telekom/bgp]]). Előny: egyszerűbb hálózatkezelés (a replikák ugyanabban a hálózati doménben lehetnek), a legjobb BGP-utat használja. Hátrány: a BGP-út nem feltétlenül optimális; az állapottartó szolgáltatások bonyolultak lehetnek (útváltáskor más replikához kerülhet a kliens). (A DNS root szerverek közül is 6 anycastolt.)

### P2P tartalommegosztás

**A CDN-ek hátrányai:** dedikált infrastruktúrát és centralizált vezérlést igényelnek. **Cél:** dedikált infrastruktúra és központi felügyelet nélküli, mégis hatékony és megbízható kézbesítés. **Kulcs:** a résztvevők (*peer*-ek) segítsenek magukon — Napster (1999, zene), BitTorrent (2001, bármilyen tartalom).

**Jellemzők:** nincs szerver; a kommunikáció peerek között folyik, önszerveződő; skálázási problémák merülnek fel. A peerek kettős szerepe: **feltöltés** a többiek segítésére és **letöltés** saját maguknak.

**Kihívások:** (1) korlátozott lehetőségek — hogyan juttat el egy peer tartalmat mindenki másnak? (2) a részvétel ösztönzése — miért segítenének egymásnak? (3) decentralizálás — hogyan találják meg a tartalmat? Ez utóbbira a **DHT** (*Distributed Hash Table*): teljesen decentralizált, hatékony algoritmusok egy elosztott indexhez — az index a peerek között terjed, listázza a tartalommal rendelkező peereket, bárki kikeresheti (tudományos munkaként indult 2001-ben).

### BitTorrent

A legelterjedtebb P2P rendszer (Bram Cohen, 2001); az Internet-forgalom nagy része; legális és illegális tartalomra is. A fájlokat **darabonként** osztják meg, figyelemreméltó ösztönző módszerrel, trackerekkel vagy decentralizált indexszel.

**Egy torrent letöltésének lépései:**
1. A **torrent** leírásával (metafájl) kezdődik.
2. (a) A **tracker**-hez fordul, és elkéri a peerek listáját, amelyen legalább egy *seed peer* van (régi módszer); vagy (b) **DHT** index a peerekhez (új).
   - **seed peer**: a fájl összes darabjával rendelkezik;
   - **leech peer**: fel és le is tölt, nincs meg minden darabja.
3. Darabcsere a különböző peerekkel.
4. **Előnyben részesíti** azokat a peereket, akik gyorsan töltenek fel neki; a **choke** (fojtott) peer az, akinek a letöltését korlátozzuk — ez az ösztönző mechanizmus.

**Vizsgaszempont:** a CDN céljai és komponensei; DNS-alapú átirányítás vs. anycast előnyei és korlátai; a P2P három kihívása; seed/leech/choke és a tracker vs. DHT.

## Kapocs

- [[concepts/telekom/dns]] — CNAME-láncok és rövid TTL az átirányításhoz
- [[concepts/telekom/bgp]] — az anycast a BGP útválasztására épül
- [[concepts/telekom/http-es-web]] — web caching és proxy
- [[concepts/telekom/tcp-torlodasvezerles]] — miért az RTT dominál a webes teljesítményben
