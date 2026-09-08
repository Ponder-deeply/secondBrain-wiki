---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Vektormező primitív függvénye

Egy $f : G \to \mathbb{R}^p$ vektormező primitív függvénye az az $F : G \to \mathbb{R}$ skalármező, amelyre $f = \operatorname{grad} F$; a potenciálfüggvény ennek ellentettje. A primitív függvény konstans erejéig egyértelmű.

## Tartalom

### Heurisztika: a potenciálból a gradiens

Tegyük fel, hogy a $g : G \to \mathbb{R}^p$ gravitációs vektormezőhöz létezik olyan $V : G \to \mathbb{R}$ potenciálfüggvény, hogy bármely $[a,x] \subset G$ szakaszon $\int_{[a,x]} g = V(a) - V(x)$. Ha $x$ közel van $a$-hoz, akkor a szakasz mentén a térerősség körülbelül $g(a)$, tehát

$$V(a) - V(x) = \int_{[a,x]} g \approx \bigl\langle g(a); x-a\bigr\rangle, \qquad \text{azaz} \qquad V(x) \approx V(a) - \bigl\langle g(a); x-a\bigr\rangle.$$

Összehasonlítva a többváltozós derivált definíciójával ez pontosan azt mondja, hogy $V$ differenciálható $a$-ban, és $V'(a) = -g(a)$. Ennek minden $a \in G$-ben teljesülnie kell, tehát $V' = -g$ az egész $G$-n.

### Definíciók

**Definíció (primitív függvény).** Legyen $G \subset \mathbb{R}^p$ nyílt, $f : G \to \mathbb{R}^p$ és $F : G \to \mathbb{R}$. Az $F$ skalármező az $f$ vektormező **primitív függvénye**, ha

$$f = \operatorname{grad} F.$$

**Definíció (potenciálfüggvény).** Ugyanilyen feltételek mellett $F$ az $f$ **potenciálfüggvénye**, ha

$$f = -\operatorname{grad} F.$$

A potenciálfüggvényben szereplő negatív előjel felcseréli a határokat a Newton–Leibniz-formulában; ettől lesz kerekebb az energiamegmaradás törvénye (a mező által végzett munka a helyzeti energia **csökkenése**). Matematikailag a két fogalom között csak előjel a különbség: $F$ pontosan akkor primitív függvény, ha $-F$ potenciálfüggvény.

### Egyértelműség konstans erejéig

**Tétel.** Legyen $G \subset \mathbb{R}^p$ **összefüggő**, nyílt, $f : G \to \mathbb{R}^p$ folytonos. Ekkor az $f$ primitív függvényei — ha léteznek — csak konstansban térnek el egymástól: ha $F_1$ és $F_2$ is primitív függvénye $f$-nek, akkor $F_1 - F_2$ konstans. (Megfordítva triviális: ha $F$ primitív függvény, akkor $F + c$ is az.)

**Bizonyítás.** Legyenek $x, y \in G$ tetszőlegesek. $G$ összefüggő és nyílt, ezért $x$ és $y$ összeköthető egy $G$-ben fekvő $\gamma$ töröttvonallal. A Newton–Leibniz-formulát mindkét primitív függvényre felírva:

$$\int_\gamma f = F_1(y) - F_1(x) = F_2(y) - F_2(x),$$

átrendezve $F_1(x) - F_2(x) = F_1(y) - F_2(y)$. Mivel ez minden $x,y$ párra igaz, $F_1 - F_2$ konstans.

Az **összefüggőség** itt nem díszlet: egy két komponensből álló $G$-n a két komponensen egymástól függetlenül más-más konstanst adhatnánk hozzá.

### A létezés kérdése

A puszta definícióból nem látszik, mikor van primitív függvénye egy vektormezőnek. A választ két lépcsőben kapjuk meg:

- **folytonos** $f$ esetén a vonalintegrálok úttól való függetlensége az ekvivalens jellemzés (konzervatív vektormezők);
- **differenciálható** $f$ esetén a rotációmentesség szükséges feltétel, amely elég sok jó tulajdonságú tartományon (konvex, csillagszerű, egyszeresen összefüggő) elégséges is.

## Kapocs

- [[concepts/analii/primitiv-fuggveny]] — az egyváltozós primitív függvény, ahol $F' = f$ egy intervallumon, és minden folytonos $f$-nek van primitív függvénye. A vektormezős általánosításban a derivált helyére a **gradiens** lép, és — döntő különbségként — a létezés már **nem** következik a folytonosságból: a tartomány topológiája is beleszól.
- [[concepts/analiii/newton-leibniz-formula-vonalintegralra]] — a primitív függvény és a vonalintegrál összekapcsolása.
- [[concepts/analiii/konzervativ-vektormezo]] — a létezés ekvivalens jellemzései folytonos mezőre.
- [[concepts/analiii/rotaciomentes-vektormezo]] — a differenciálható esetben szükséges feltétel.
- [[concepts/analiii/skalarmezo-es-vektormezo]] — a $V$ potenciál és a $g$ térerősség szereposztása.
