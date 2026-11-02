---
tags: [concept]
sources: [Laki_Lecture_7b.pdf, Laki_Lecture_8.pdf]
derivation: source
kind: procedure
element: water
updated: 2026-09-25
---

# BGP és az autonóm rendszerek közötti forgalomirányítás

Az Internet kétszintű hierarchia: az első szintet az **autonóm rendszerek** (AS) alkotják, amelyeken belül *intra-domain* (RIP, OSPF), közöttük pedig *inter-domain* routing működik. Az utóbbi egyetlen protokollja a **BGP** (*Border Gateway Protocol*, ma BGP-4), amely **útvonalvektor** (*path vector*) protokoll: a teljes AS-utat hirdeti, így hurkokat detektál, és politikai (üzleti) szabályok szerint választ utat.

## Tartalom

### Autonóm rendszerek

- **AS**: egy adminisztratív tartomány alatti hálózat — pl. ELTE, Comcast, AT&T, Verizon, Sprint.
- Minden AS-t egy **AS-szám (ASN)** azonosít: 16 bites érték (a legújabb protokollok már 32 bitest is támogatnak); a 64512–65535 tartomány más célra foglalt. Kb. 40 000 AS-szám létezik. Példák: AT&T 5074, 6341, 7018…; Sprint 1239, 1240…; **ELTE 2012**; Google 15169, 36561 (korábban YouTube); Facebook 32934.

**Miért van szükség AS-ekre?**
- a routing algoritmusok **nem elég hatékonyak** a teljes Internet-topológiához;
- a szervezetek **más-más politika** (*policy*) mentén akarnak routolni;
- elrejthetik belső hálózatuk szerkezetét;
- eldönthetik, mely más szervezeteken keresztül forgalmaznak.

Eredmény: egyszerűbb útvonalszámítás, nagyobb rugalmasság, nagyobb autonómia.

### Inter-domain routing követelményei

A globális összeköttetéshez **minden AS-nek ugyanazt** a protokollt kell használnia (szemben az intra-domain routinggal, ahol mindenki maga választ). Követelmények: skálázódás, rugalmas útvonalválasztás (költség, hibák kikerülése). Link state vagy distance vector? Válasz: egyik sem — a BGP **path vector** protokoll.

### A BGP általános jellemzői

- AS-ek közötti (*exterior gateway*) protokoll, eltérő célokkal, mint az AS-en belüliek; **politikai szempontok** is szerepet játszanak.
- Példák forgalomirányítási korlátozásra: ne legyen átmenő forgalom bizonyos AS-eken keresztül; csak akkor haladjunk át Albánián, ha nincs más út; az IBM-nél kezdődő vagy végződő forgalom ne menjen át a Microsofton.
- A politikai szabályokat **kézzel** konfigurálják a BGP-routeren.
- A BGP-router szemszögéből a világ AS-ekből és a közöttük átmenő vonalakból áll; két AS **összekötött**, ha van köztük a BGP-routereiket összekötő él.

**Hálózatok az átmenő forgalom szempontjából:**
1. **Csonka** (*stub*) hálózatok — csak egyetlen összeköttetésük van a BGP-gráffal.
2. **Többszörösen bekötött** hálózatok — használhatná őket az átmenő forgalom, de ezt megtagadják.
3. **Tranzit** hálózatok — némi megkötéssel, általában fizetség ellenében kezelik harmadik fél csomagjait.

### Működés

- A BGP-routerek páronként **TCP-összeköttetést** létesítenek (a **179-es porton**): munkamenet létrehozása → aktív útvonalak kicserélése → folyamatos frissítések cseréje.
- A BGP alapvetően távolságvektor protokoll, de a router **nyomon követi a használt útvonalat**, és az útvonalat mondja meg a szomszédainak.

**Példa:** F-nek a D-re vonatkozó információi a szomszédoktól: B: „BCD-t használom”; G: „GCD-t”; I: „IFGCD-t”; E: „EFGCD-t”. Az I-től és E-től jövő utak **F-en át vezetnek**, ezért F azonnal eldobja őket (hurok). Marad a BCD és a GCD — F ezek közül választ (pl. FGCD vagy FBCD), a saját politikája szerint.

### Útvonalvektor (path vector)

- **AS-útvonal**: az AS-ek sorozata, amelyeken az útvonal áthalad; hasonló a távolságvektorhoz, de több információt tartalmaz.
- Hurkok detektálása és különböző továbbítási politikák (pl. a legolcsóbb/legrövidebb út).
- Routing a **leghosszabb prefix-egyezés** alapján ([[concepts/telekom/ipv4-cimzes-es-cidr]]).
- Példa AS 1 táblája: 120.10.0.0/16: AS2 → AS3 → AS4; 130.10.0.0/16: AS2 → AS3; 110.10.0.0/16: AS2 → AS5.

A **távolságvektor kiterjesztése**: rugalmas továbbítási politikák, és **megoldja a végtelenig számolás problémáját** ([[concepts/telekom/tavolsagvektor-routing]]), mert egy router a saját AS-számát látva felismeri a kört. Útvonalvektor: célállomás, következő ugrás, AS-útvonal. Ötlet: a távolságvektor célonként egy metrikát küld, az útvonalvektor célonként a **teljes útvonalat**.

### Rugalmas forgalomirányítás

Minden állomás saját útválasztási politikát alkalmaz:
- **útvonal-kiválasztás** — melyik útvonalat használjuk? (pl. a 2. állomás a „2, 3, 1” utat preferálja a „2, 1” helyett);
- **útvonal-export** — melyik útvonalat hirdessük meg? (pl. az 1. állomás nem hagyja, hogy a 3. értesüljön az „1, 2” útról).

**Üzleti kapcsolatok:** az ügyfél (*customer*) fizet a szolgáltatónak (*provider*); a *peer*-ek egymás között díjmentesen cserélnek forgalmat, de egy peer nem szállít tranzitforgalmat két másik peer vagy szolgáltató között. A **Tier-1** szolgáltatók (AT&T, Level 3, Sprint, Verizon, CenturyLink…) teljes gráfban peerelnek egymással — Tier-1-gyé válni annyit jelent, hogy minden Tier-1 üzemeltetőt rá kell venni, hogy legyen a peered („nem túl könnyű”).

### eBGP, iBGP, IGP

- **eBGP** — routing információk cseréje autonóm rendszerek között.
- **iBGP** — útválasztás egy AS-en belül egy **külső** célállomáshoz.
- **IGP** — útválasztás egy AS-en belül egy **belső** célállomáshoz. A határrouterek is beszélik az IGP-t.

Menet: (1) eBGP: A AS határroutere megismeri az utat a célhoz; (2) iBGP: az A-ban lévő router megtanulja a célhoz vezető utat (következő ugrás a határrouter); (3) IGP: ennek segítségével eljuttatja a csomagot A határrouteréig.

A hirdetett prefixek száma folyamatosan nő (2015-re > 500 000).

**Vizsgaszempont:** miért kellenek AS-ek; path vector vs. distance vector (hurokdetektálás a teljes úttal); a csonka/többszörösen bekötött/tranzit felosztás; eBGP/iBGP/IGP szerepe.

## Kapocs

- [[concepts/telekom/hierarchikus-es-adatszoro-routing]] — IGP és EGP, hierarchikus routing
- [[concepts/telekom/tavolsagvektor-routing]] — az alap, amelyet a BGP kiterjeszt
- [[concepts/telekom/kapcsolatallapot-routing]] — OSPF és IS-IS mint IGP
- [[concepts/telekom/tcp]] — a BGP-munkamenetek szállítója
