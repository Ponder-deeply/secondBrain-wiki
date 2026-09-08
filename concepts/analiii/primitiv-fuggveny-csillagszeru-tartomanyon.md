---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Primitív függvény létezése konvex és csillagszerű tartományon

A Goursat-lemma következményei: konvex, illetve csillagszerű tartományon a rotációmentesség már elégséges is a primitív függvény létezéséhez, és minden differenciálható rotációmentes mezőnek van lokálisan primitív függvénye.

## Tartalom

### Konvex tartomány

**Következmény.** Legyen $G \subset \mathbb{R}^p$ összefüggő nyílt, **konvex**, és $f : G \to \mathbb{R}^p$ differenciálható. Az $f$-nek akkor és csak akkor van primitív függvénye, ha rotációmentes.

**Bizonyítás.** A „csak akkor" irányt már tudjuk. Legyen tehát $f$ rotációmentes; a konzervativitás ekvivalenciatétele szerint elég megmutatni, hogy bármely zárt töröttvonalon nulla a vonalintegrálja.

Vegyünk egy tetszőleges $[a_0a_1a_2\dots a_n]$ zárt töröttvonalat. Ezt az $a_0a_1, \dots, a_0a_{n-1}$ **átlókkal** háromszögekre bonthatjuk, és a belső átlókon vett integrálok páronként kiesnek:

$$\int_{[a_0a_1\dots a_n]} f = \sum_{i=1}^{n}\int_{[a_0a_{i-1}a_i]} f.$$

A konvexitás miatt mindegyik $[a_0a_{i-1}a_i]$ **zárt háromszöglemez** $G$-ben van, így a jobb oldalon a Goursat-lemma szerint mindegyik integrál $0$.

A konvexitás pontosan arra kellett, hogy a háromszögek **belseje** is a tartományban maradjon — a Goursat-lemma feltétele éppen ez.

### Lokális primitív függvény

**Következmény.** Legyen $G \subset \mathbb{R}^p$ összefüggő nyílt, és $f : G \to \mathbb{R}^p$ differenciálható, rotációmentes. Ekkor minden $a \in G$ pontnak van olyan környezete, amelyben $f$-nek van primitív függvénye.

**Bizonyítás.** Minden gömbi környezet konvex, és $G$ minden konvex részén az előző következmény szerint létezik primitív függvény.

Ez az állítás a rotációmentesség valódi tartalma: **lokálisan** mindig van primitív függvény, a probléma kizárólag az, hogy a lokális darabok összeilleszthetők-e egyetlen globális függvénnyé. A kilyukasztott sík „szög" függvénye pontosan ezen bukik el.

### Csillagszerű tartomány

**Definíció.** Legyen $G \subset \mathbb{R}^p$ összefüggő, nyílt. A $G$ **csillagszerű**, ha van olyan $x_0 \in G$ pont (a „csillag közepe"), hogy bármely $x \in G$ esetén az $[x_0, x]$ szakasz része $G$-nek.

**Példák.**

- Minden konvex tartomány csillagszerű (bármely pontja lehet a közép).
- $\mathbb{R}^2\setminus\{(x,0) : x \geqslant 0\}$ csillagszerű (a pozitív $x$-tengely mentén felvágott sík).
- $\mathbb{R}^p\setminus\{0\}$ **nem** csillagszerű: bármely $x_0$ választásra a $-x_0$ irányba mutató szakasz áthaladna az origón.

**Következmény.** Legyen $G \subset \mathbb{R}^p$ összefüggő nyílt, **csillagszerű**, és $f : G \to \mathbb{R}^p$ differenciálható. Az $f$-nek akkor és csak akkor van primitív függvénye, ha rotációmentes.

**Bizonyítás.** Legyen $c$ a csillag közepe. Tetszőleges $G$-ben fekvő $[a_1a_2\dots a_n]$ zárt töröttvonalat most nem az egyik csúcsából, hanem $c$-ből bontunk háromszögekre: az összes $[ca_{i-1}a_i]$ háromszöglemez $G$-ben fekszik, mert a $c$-ből induló szakaszok mind a tartományban maradnak. Így

$$\int_{[a_1a_2\dots a_n]} f = \sum_{i=1}^{n}\int_{[ca_{i-1}a_i]} f = 0$$

a Goursat-lemma szerint.

### A gondolatmenet íve

A három állítás egy fokozatosan táguló feltételsort ad: konvex $\to$ csillagszerű $\to$ (a következő lépésben) egyszeresen összefüggő. Mindegyik lépésben ugyanaz kell: a zárt töröttvonal háromszögekre bontható úgy, hogy a háromszöglemezek a tartományban maradjanak. Az utolsó általánosítás ehhez már topológiai eszközt, a homotópiát igényli.

## Kapocs

- [[concepts/analiii/goursat-lemma]] — mindhárom következmény ezen múlik.
- [[concepts/analiii/rotaciomentes-vektormezo]] — a feltétel, amely itt elégségessé válik; a kilyukasztott sík példája éppen azt mutatja, hogy csillagszerűség nélkül nem az.
- [[concepts/analiii/egyszeresen-osszefuggo-tartomany]] — a végleges, legáltalánosabb feltétel.
- [[concepts/analiii/vonalintegral-homotop-gorbeken]] — a lokális primitív függvény létezése ennek a tételnek is a feltétele.
- [[concepts/analiii/konzervativ-vektormezo]] — a bizonyítások a zárt töröttvonalas kritériumot használják.
