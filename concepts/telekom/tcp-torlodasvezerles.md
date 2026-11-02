---
tags: [concept]
sources: [Laki_Lecture_9.pdf, Laki_Lecture_10.pdf]
derivation: source
kind: procedure
element: water
updated: 2026-09-25
---

# TCP torlódásvezérlés: slow start, AIMD, Tahoe, Reno, CUBIC

Torlódás akkor van, ha a hálózat terhelése nagyobb, mint a kapacitása. A meghirdetett ablak csak a **fogadót** védi, a hálózatot nem, ezért a TCP a küldő oldalon egy **torlódási ablakot** (`cwnd`) is vezet, és a küldési rátát $\sim \text{wnd}/\text{RTT}$ ennek állításával szabályozza: csomagvesztésig növeli, vesztéskor csökkenti. A két fázis a **slow start** (exponenciális növekedés) és a **torlódáselkerülés** (AIMD).

## Tartalom

### Mi a torlódás, és miért rossz?

- A kapacitás nem egyenletes a hálózatban (modem, cellás, kábel, optika); számos folyam verseng a sávszélességért; a terhelés időben sem egyenletes.
- **Csomagvesztést** eredményez: a routerek puffere véges; az önhasonló Internet-forgalomhoz nincs olyan puffer, amelyben ne lenne vesztés; ahogy a puffer telítődik, a router dobni kezd (RED — [[concepts/telekom/aktiv-sorkezeles-es-dctcp]]).
- Gyakorlati következmények: a sorok telítődnek → **megnövekedett késleltetés**; **újraküldések** miatt pazarolt sávszélesség; alacsony hasznos átvitel (*goodput*).

### Könyök és szírt

A terhelés függvényében:
- **Könyök** (*knee*): utána az átvitel alig nő, a késleltetés viszont gyorsan emelkedik. Egy M/M/1 sorban késleltetés $= 1/(1 - \text{kihasználtság})$.
- **Szírt** (*cliff*): utána az átvitel lényegében 0-ra esik, a késleltetés $\to\infty$ — **teljes összeomlás**.

**Torlódáselkerülés:** maradj a könyök bal oldalán. **Torlódásvezérlés:** maradj a szírt bal oldalán. A könyök az ideális munkapont.

### Általános megoldások

1. **Ne csináljunk semmit** — nagy csomagvesztés, jósolhatatlan teljesítmény, teljes összeomláshoz vezethet.
2. **Erőforrás-foglalás** — a folyamokhoz előre sávszélességet allokálunk, tárgyalási szakasz kell; hálózati támogatást igényel.
3. **Dinamikus beállítás** (a TCP ezt választja) — próbák a torlódási szint becslésére; gyorsítás alacsony torlódásnál, lassítás, ahogy nő; nem rendezett dinamika, elosztott koordináció.

### A TCP megoldása

Két fő komponens:
1. **Torlódásdetektálás** — az eldobott csomag megbízható jel (a késleltetés alapú megoldások nehezek és kockázatosak). Detektálás nyugtával: lejár az időkorlát ACK nélkül, vagy **több duplikált ACK** jön.
2. **Rátabeállító algoritmus** — `cwnd` módosítása, sávszélesség-próba, válaszlépés a torlódásra. ACK érkezésekor növeljük `cwnd`-t (valószínűleg gyorsabban is küldhetünk), vesztéskor csökkentjük (torlódás van).

**Három változó:**
- `cwnd` — torlódási ablak;
- `adv_wnd` — a fogadó meghirdetett ablaka;
- `ssthresh` — vágási érték (küszöb).

Küldéskor: $\text{wnd} = \min(\text{cwnd},\ \text{adv\_wnd})$.

### 1. fázis: lassú indulás (slow start), ha cwnd < ssthresh

Cél a szűk keresztmetszet (*bottleneck*) sávszélességének gyors megtalálása, a könyökpont gyors elérése.
- Kapcsolat kezdetén (vagy újraindításkor): `cwnd = 1`, `ssthresh = adv_wnd`.
- **Minden nyugtázott szegmensre `cwnd++`.**
- Addig tart, amíg el nem érjük az `ssthresh`-t, vagy csomagvesztés nem történik.

A slow start valójában **nem lassú**: `cwnd` RTT-nként **duplázódik** (1 → 2 → 4 → 8…), mert egy RTT alatt `cwnd` darab ACK érkezik.

### 2. fázis: torlódáselkerülés — AIMD, ha cwnd ≥ ssthresh

*Additive Increase, Multiplicative Decrease.* Az `ssthresh` valójában alsó becslés a könyökpontra.
- Minden nyugtázott szegmensnél `cwnd += 1/cwnd` — vagyis **RTT-nként eggyel** nő.

**Példa** (`ssthresh = 8`): RTT-nként `cwnd` = 1, 2, 4, 8 (slow start), majd 9, 10, 11, 12 (lineáris).

### TCP Tahoe (az eredeti)

Slow start + AIMD + dinamikus RTO (RTT-becsléssel, [[concepts/telekom/tcp]]). **Időkorlát** esetén: `ssthresh = cwnd/2`, `cwnd = 1`, újra slow start. A `cwnd`–idő grafikon: exponenciális felfutás, időkorlát → nullára esés, slow start az új `ssthresh`-ig, onnan lineáris növekedés, és így tovább.

### TCP Reno

A TCP-t 1974-ben találták fel; az első népszerű változat a Reno, amely a Tahoe-hoz két dolgot ad:
- **Gyors újraküldés** (*fast retransmit*): Tahoe-nál egy elveszett csomag után hosszú a várakozás az RTO-ig. Reno **3 duplikált ACK** (ugyanaz a nyugtaszám) esetén azonnal újraküld — ez a vesztés explicit jele. Példa: a 4. szegmens elvész, az 5., 6., 7. megérkezik, mindegyikre „ACK 4” jön → újraküldés.
- **Gyors helyreállítás** (*fast recovery*): gyors újraküldés után `cwnd := cwnd/2` (ez a *multiplicative decrease*), `ssthresh :=` az új `cwnd` — tehát **nem** állítjuk vissza 1-re, elkerüljük a felesleges slow startot és a költséges időkorlátokat.
- **Ha viszont az RTO lejár**, továbbra is `cwnd = 1` és slow start (mint Tahoe) — ez nagyon súlyos torlódást jelez (egyáltalán nem szállított csomagokat).

Stabil állapotban a `cwnd` **fűrészfogszerűen** oszcillál az optimális ablakméret körül; a TCP mindig kikényszeríti a csomagdobásokat.

### További változatok

| Változat | Lényeg |
|---|---|
| **Tahoe** | slow start, AIMD, dinamikus RTO |
| **Reno** | + fast retransmit (3 dupACK), fast recovery (cwnd/2) |
| **NewReno** | javított gyors újraküldés: minden duplikált ACK újraküldést vált ki — de a > 3 sorrenden kívül fogadott csomag is (hibásan) újraküldést okoz |
| **Vegas** | késleltetés alapú torlódáselkerülés |
| **Compound TCP** (Windows) | Reno alapú, két ablak: `wnd = min(cwnd + dwnd, adv_wnd)`; `cwnd`-t AIMD vezérli, a késleltetés alapú `dwnd` csökken, ha nő az RTT, és nő, ha csökken (a változással arányosan) |
| **CUBIC** (Linux) | a BIC fejlettebb változata; az AIMD-t köbös függvény váltja fel |

**Nagy késleltetés–sávszélesség szorzat** (*delay-bandwidth product*, $b\cdot d$ — a maximálisan úton lévő adat): ekkor a TCP gyengén teljesít, mert a slow start és az additive increase lassan konvergál, és a TCP ACK-ütemezett (nagy RTT → késleltetett nyugták → lassú reakció). Célok: gyorsabb ablaknövelés, de fairség más TCP-változatokkal szemben; javított RTT-fairség (a Tahoe/Reno nem fair nagyon eltérő RTT-knél); egyszerű implementáció.

**Compound TCP:** agresszívan reagál az RTT változására; előnye a gyors felfutás és a fairebb viselkedés eltérő RTT-k esetén; hátránya a folyamatos RTT-becslés.

**TCP CUBIC:**
$$W_{cubic} = C\,(T - K)^3 + W_{max},\qquad K = \sqrt[3]{\frac{W_{max}\,\beta}{C}},$$
ahol $C$ skálázó konstans, $\beta$ a *multiplicative decrease* konstansa, $T$ a legutóbbi csomagvesztés óta eltelt idő, $W_{max}$ a `cwnd` a legutolsó vesztéskor. A görbe: **gyors felfutás** $W_{max}$ felé, **stabil régió** $W_{max}$ körül, majd **lassú gyorsítás** a sávszélesség teszteléséhez. Kevésbé pazarolja a sávszélességet; a stabil régió és a lassú gyorsítás segíti a fairséget.

### A TCP problémái

- **Kis folyamok:** 1 RTT kell a kapcsolatfelépítésre; `cwnd` mindig 1-gyel indul, nincs idő felgyorsulni. Az Internet-forgalom nagy része kis folyam (HTTP, < 100 KB) — a legtöbb TCP-folyam **el sem hagyja a slow startot**. Google-javaslat: kezdeti `cwnd` = 10; **TCP Fast Open** — kriptográfiai hash (cookie) a SYN-ben, a kézfogás elhagyható.
- **Vezeték nélküli hálózatok:** Tahoe/Reno szerint csomagvesztés = torlódás; WAN-on ez igaz (ritka bithiba), wirelessben hamis (gyakori interferencia). A TCP átvitele $\sim 1/\sqrt{\text{vesztési ráta}}$, így néhány interferencia miatti vesztés is drasztikusan rontja. Megoldások: réteg-modell megsértése (adatkapcsolati információ a TCP-be), késleltetés alapú vezérlés (Vegas), **ECN**.
- **DoS:** a SYN flood ([[concepts/telekom/tcp]]).

**Vizsgaszempont:** a `cwnd` alakulásának lejátszása adott `ssthresh`-sel és vesztési eseményekkel (időkorlát vs. 3 dupACK) — klasszikus feladat; slow start vs. AIMD; Tahoe vs. Reno; a CUBIC képlet tagjainak jelentése.

## Kapocs

- [[concepts/telekom/tcp]] — meghirdetett ablak, RTO, nyugták
- [[concepts/telekom/aktiv-sorkezeles-es-dctcp]] — RED, ECN, DCTCP: a hálózat segítsége
- [[concepts/telekom/csuszoablak-protokollok]] — az ablakozás elve
