---
tags: [concept]
sources: [Laki_Lecture_5.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-09-25
---

# CSMA/CD, bináris exponenciális hátralék és minimális keretméret

A *CSMA with Collision Detection* a klasszikus, adatszóró Ethernet MAC-protokollja: az állomás küldés közben is figyeli a csatornát, ütközéskor azonnal abbahagyja az adást, „jam” jelet küld, és a **bináris exponenciális hátralék** szerint vár az újrapróbálkozással. Hogy minden ütközést észrevegyen, a keretnek legalább két propagációs késésnyi ideig kell tartania — ebből adódik a **64 bájtos minimális keretméret** és a maximális kábelhossz.

## Tartalom

### Háttér: adatszóró Ethernet

Eredetileg az Ethernet adatszóró technológia volt: a **10Base2** koaxiális kábelen T-csatlakozókkal és lezárókkal (*terminator*) kötötték össze a gépeket, a **10BaseT** és **100BaseT** („T” = sodrott érpár, *twisted pair*) hubokkal. A **hubok és repeaterek 1. rétegbeli** (csak fizikai) eszközök, így minden állomás egy ütközési tartományban van.

### Az algoritmus

Alapvetés: a közeg lehetőséget ad a csatornába hallgatásra.

1. Valamely CSMA-variánssal kezdünk ([[concepts/telekom/csma]]).
2. A keret kiküldése közben figyeljük a közeget, hogy történik-e ütközés.
3. Ha nem volt ütközés, a keretet leszállítottuk.
4. Ha ütközés történt, **azonnal megszakítjuk a küldést** — miért folytatnánk, hisz a keret már sérült.
5. Az újraküldéshez a **bináris exponenciális hátralékot** alkalmazzuk.

A CSMA/CD három állapota: **versengés**, **átvitel** és **szabad**.

**Mikor biztos egy állomás abban, hogy megszerezte a csatornát?** Ha minden más állomás érzékeli az átvitelét. Az ütközésdetektálás minimális ideje az az idő, ami egy jelnek a két legtávolabbi állomás közötti átviteléhez kell.

### Bináris exponenciális hátralék (binary exponential backoff)

- Ütközés érzékelésekor a küldő egy **„jam” jelet** küld, hogy minden állomás tudomást szerezzen az ütközésről.
- $n$ ütközés után válasszunk egy $k \in [0,\ 2^n - 1]$ egész számot egyenletes eloszlás szerint, és várjunk $k$ időegységet (versengési rést) az újraküldésig.
- $n$ felső határa 10; **16 sikertelen próbálkozás után** a keretet eldobjuk.

Két ütköző állomás esetén:
- 1. ütközés után 2 rés közül választanak: siker esélye **50%**, átlagos várakozás 1,5 rés;
- 2. ütközés után 4 rés közül: siker esélye **75%**, átlagos várakozás 2,5 rés;
- általában az $m$-edik ütközés után a siker esélye $1 - 2^{-m}$, az átlagos késleltetés $0{,}5 + 2^{m-1}$ rés.

Előny: kevés ütközésnél kicsi a várakozás, sok versengő állomásnál a várakozási ablak gyorsan nő, és a terhelés szétterül.

### Minimális keretméret

Mi a kapcsolat a keretméret és a kábelhossz között? Legyen $d$ a két legtávolabbi állomás, A és B közötti propagációs késés:

1. $t$: A megkezdi az átvitelt;
2. $t + d - \varepsilon$: B (még nem hallva A-t) szintén elkezd adni;
3. $t + 2d$: B jele visszaér A-hoz — **A ekkor érzékeli az ütközést**.

Ha A addigra már befejezte az adást, azt hiszi, sikeres volt. Ezért **A-nak legalább $2d$ ideig kell küldenie**:

$$T_f \ge 2T_{pg},$$

ahol $T_f$ egy keret elküldésének ideje, $T_{pg}$ a propagációs késés A és B között. Bitekben:

$$\text{min\_keret} = \text{ráta} \cdot 2d = \text{ráta}\cdot\frac{2\cdot\text{távolság}}{\text{fénysebesség}},\qquad \text{max\_kábelhossz} = \frac{\text{min\_keret}\cdot\text{fénysebesség}}{2\cdot\text{ráta}}.$$

**Példa (10 Mbps Ethernet):** 64 bájtos minimális keret, $2\cdot10^8$ m/s jelsebesség:
$$\frac{(64\cdot 8)\cdot 2\cdot10^8}{2\cdot 10^7} = 5120 \text{ méter}.$$

További változatok:
- min. keret 1024 bájt, 10 Mbps → **81,9 km**;
- min. keret 64 bájt, **1 Gbps** → **51 m**;
- 1024 bájt és 1 Gbps → **819 m**.

Tanulság: a gyorsabb szabványokkal a keretméret és a kábelhossz is változik — ugyanakkora keret 100-szor gyorsabb vonalon 100-szor rövidebb kábelen fér el.

### Maximális keretméret (MTU)

Az Ethernet *Maximum Transmission Unit*-ja **1500 bájt**.
- Mellette: hosszú csomagokban a hibák jelentős javítási költséget okoznak (túl sok adatot kell újraküldeni).
- Ellene (kis keretnél): több bájt vész el a fejlécekben, és összességében nagyobb a csomagfeldolgozási idő.
- Adatközpontokban **jumbo keretek**: 9000 bájt.

**Vizsgaszempont:** a $T_f \ge 2T_{pg}$ feltétel indoklása és a min. keret / max. kábelhossz számolás (rátával, távolsággal, fénysebességgel) szinte biztos feladat; a bináris exponenciális hátralék szabályai.

## Kapocs

- [[concepts/telekom/csma]] — a vivőjel-érzékelés perzisztencia-változatai
- [[concepts/telekom/ethernet]] — a CSMA/CD-t használó LAN-technológia
- [[concepts/telekom/halozati-alapfogalmak]] — propagációs és átviteli késleltetés
- [[concepts/telekom/aloha]] — az ütközésalapú protokollok kiindulópontja
