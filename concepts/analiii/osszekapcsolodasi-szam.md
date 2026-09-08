---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Gauss-féle összekapcsolódási szám

Két diszjunkt zárt térbeli görbe kettős vonalintegrállal felírt, mindig egész értékű topológiai invariánsa: azt méri, hányszor bújik át az egyik görbe a másikon. Az elektrodinamikából, a Biot–Savart és az Ampère-törvényből vezethető le.

## Tartalom

Az elektrodinamika olyan tudományterület, ahol a fizika összetalálkozik a topológiával — az összekapcsolódási szám ennek legszebb példája.

### Biot–Savart törvény

Ha egy rövid, $\Delta\ell$ hosszú vezetődarabban $I$ áram fut, akkor $r$ vektorral arrébb ez az áramdarab

$$\Delta B = \frac{\mu_0}{4\pi}\cdot\frac{I\,\Delta\ell\times r}{|r|^3}$$

mágneses indukciót hoz létre. Ha a $\gamma$ görbe mentén $I$ áram folyik, akkor az áram által létrehozott mágneses indukció az $x$ pontban

$$B(x) = \frac{\mu_0}{4\pi}\int_{y\in\gamma}\frac{I\,\mathrm{d}y\times(x-y)}{|x-y|^3}.$$

### Ampère- (gerjesztési) törvény

Ha a $\gamma$ zárt görbe által határolt felületen $I$ stacionárius áram folyik keresztül (a töltés nem gyűlik össze — tipikusan zárt áramkör, kondenzátorok nélkül), akkor a $\gamma$ görbe mentén a mágneses örvényerősség

$$\int_{y\in\gamma}\langle B, \mathrm{d}y\rangle = \mu_0 I .$$

### A levezetés

Képzeljünk el egy $\gamma_1$ zárt görbét, amely egy felületnek a pereme, és egy másik, $\gamma_2$ zárt görbét, amely $N$-szer átdöfi ezt a felületet. Ha $\gamma_2$ mentén $I$ áram folyik, akkor a $\gamma_1$ menti mágneses örvényerősséget kétféleképpen is kiszámíthatjuk: az Ampère-törvényből, illetve a Biot–Savart törvényből:

$$\mu_0\cdot NI \overset{\text{Átv}}{=} \int_{x\in\gamma_1}\langle B, \mathrm{d}x\rangle \overset{\text{BStv}}{=} \int_{x\in\gamma_1}\left\langle \frac{\mu_0}{4\pi}\int_{y\in\gamma_2}\frac{I\,\mathrm{d}y\times(x-y)}{|x-y|^3},\ \mathrm{d}x\right\rangle = \frac{\mu_0 I}{4\pi}\int_{x\in\gamma_1}\int_{y\in\gamma_2}\frac{\langle \mathrm{d}x\times\mathrm{d}y,\ x-y\rangle}{|x-y|^3}.$$

$\mu_0 I$-vel osztva egy tisztán geometriai képlet marad:

$$N = \frac{1}{4\pi}\int_{x\in\gamma_1}\int_{y\in\gamma_2}\frac{\langle \mathrm{d}x\times\mathrm{d}y,\ x-y\rangle}{|x-y|^3}.$$

A fizika eltűnt a képletből — csak a két görbe geometriája maradt.

### Definíció

**Definíció (Gauss-féle összekapcsolódási szám, linking number).** Legyen $\gamma_1$ és $\gamma_2$ két diszjunkt, zárt, szakaszonként folytonosan differenciálható görbe $\mathbb{R}^3$-ben. A két görbe *összekapcsolódási száma*

$$\frac{1}{4\pi}\int_{x\in\gamma_1}\int_{y\in\gamma_2}\frac{\langle \mathrm{d}x\times\mathrm{d}y,\ x-y\rangle}{|x-y|^3}.$$

### Tulajdonságok

- A kettős vonalintegrál értéke **mindig egész szám** — ezért kell $4\pi$-vel osztani, ami az egységgömb felszíne.
- Akár ebből, akár közvetlenül ellenőrizhető, hogy **homotóp görbepár-párokra ugyanaz** az érték: folytonos deformáció közben nem változhat, amíg a görbék nem metszik egymást.
- Ennek sok topológiai alkalmazása van; például ezzel bizonyítható, hogy az egymáson átfűzött karikákat nem lehet szétválasztani (ha a linking number nem nulla, akkor a lánc nem bontható szét folytonos mozgatással).

## Kapocs

- [[concepts/analiii/kelvin-stokes-tetel]] — az Ampère-törvény integrális alakja mögötti integráltétel
- [[concepts/analiii/maxwell-egyenletek-es-integraltetelek]] — az elektrodinamikai háttér
- [[concepts/analiii/korulfordulasi-szam]] — a síkbeli megfelelő: egy görbe indexe egy pontra
- [[concepts/analiii/korulfordulasi-szam-valtozatok]] — a három képlet összehasonlítása
- [[concepts/analiii/altalanos-vonalintegral]] — a felírásban használt vonalintegrál-fogalom
