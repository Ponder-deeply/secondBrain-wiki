---
tags: [concept]
sources: [Lehman-Leighton-Meyer-Mathematics-for-Computer-Science.pdf, dimat2gyak03mo.pdf]
references: [Lehman–Leighton–Meyer, Mathematics for Computer Science, 9.1.3 és 9.2.3]
derivation: source
kind: theorem
element: water
updated: 2026-10-22
---

# A vízkancsó-feladat

Két mérőjelölés nélküli edénnyel pontosan akkor tölthető ki $c$ egység folyadék, ha $c$ többszöröse az edények űrtartalma lnko-jának. A bizonyítás invariánst használ, a kivitelezés a bővített euklideszi algoritmust.

## Tartalom

### A feladat

Adott két edény $a$ és $b$ űrtartalommal, egy csap (vagy hordó) és lefolyó. Műveletek: edény teljes megtöltése, kiürítése, átöntés az egyikből a másikba, amíg az első üres vagy a második tele nem lesz. Cél: egy edényben pontosan $c$ egység folyadék.

### Invariáns: lineáris kombináció

**Lemma.** Minden edényben lévő mennyiség mindig $a$ és $b$ egész együtthatós lineáris kombinációja.

*Bizonyítás indukcióval a lépések számára.* Kezdetben $0 = 0a + 0b$. Megtöltés után az egyik edényben $a$ vagy $b$ van. Kiürítés után $0$. Átöntésnél az egyik edény kiürül vagy megtelik, a másikban $x + y$, $x + y - a$ vagy $x + y - b$ lesz, és ezek $x, y$ lineáris kombinációi. $\square$

Mivel az $a$ és $b$ közös osztója osztja minden lineáris kombinációjukat ([[concepts/dimatii/oszthatosag]]), a mennyiség mindig $(a,b)$ többszöröse.

**Következmény.** $12$ és $18$ egységű edényből nem lehet $4$ egységet kimérni ($(12,18) = 6 \nmid 4$); $899$ és $1147$ egységűből $32$-t sem, mert $(899,1147) = 31$ (az euklideszi algoritmus: $1147, 899, 248, 155, 93, 62, 31, 0$).

### Megfordítás: minden többszörös kimérhető

**Tétel.** Ha $c \in [0, a]$ az $a$ űrtartalmú edényben, akkor kimérhető pontosan akkor, ha $(a,b) \mid c$.

Ha $(a,b) \mid c$, akkor a bővített euklideszi algoritmus ([[concepts/dimatii/bovitett-euklideszi-algoritmus]]) szerint $c = sa + tb$, és $s > 0$ elérhető $s$ növelésével $b$-vel és $t$ csökkentésével $a$-val (ugyanaz a nulla-előállítás, amit a diofantikus egyenlet általános megoldásánál használunk). Az eljárás ekkor:

1. töltsük meg a kisebbik edényt;
2. öntsük át a nagyobba; ha a nagyobb megtelik, ürítsük ki, és folytassuk az átöntést;
3. ismételjük, amíg a kívánt mennyiség elő nem áll.

A lépéseket nem kell az együtthatókból kiszámolni: az eljárás előbb-utóbb minden $(a,b)$-többszöröst előállít.

**Példa.** $21$ és $26$ egységű edényből $3$ egység: $(21,26) = 1 \mid 3$. Az eljárást követve a $26$ egységű edény tartalma a töltések után $21, 16, 11, 6, 1, 22, 17, 12, 7, 2, 23, 18, 13, 8, 3$: minden körben $21$-gyel nő, és ha túlcsordulna, $26$-tal csökken, tehát $5$-tel csökken modulo $26$. A $3$ egység a $15$. töltés után áll elő, közben $12$ kiürítés történt: $3 = 21 \cdot 15 - 26 \cdot 12$.

### Három és öt pint

Pontosan $4$ pint sör elfogyasztása egy $3$ és egy $5$ pintes edénnyel ($(3,5) = 1 \mid 4$, tehát lehetséges):

1. megtöltjük a hármast, és átöntjük az ötösbe (az ötösben $2$ pint hely marad);
2. újra megtöltjük a hármast, és az ötöst csurig töltjük belőle ($2$ pint megy át), így a hármasban $1$ pint marad, ezt megisszuk;
3. az ötösből (tele van, $5$ pint) csurig töltjük a (most üres) hármast, az ötösben $2$ pint marad, a hármas $3$ pintjét megisszuk.

Összesen $1 + 3 = 4$ pint fogyott, a hordóból $3 + 3 = 6$ pintet engedtünk, és $2$ pint maradt az ötös edényben. Az elérhető mennyiségeket a $3s + 5t$ lineáris kombinációk adják, itt $4 = 3\cdot 3 + 5 \cdot (-1)$, és az összes megoldás a [[concepts/dimatii/linearis-diofantikus-egyenlet]] módszerével kapható.

## Kapocs

- [[concepts/dimatii/bovitett-euklideszi-algoritmus]] — a kivitelezés eszköze
- [[concepts/dimatii/linearis-diofantikus-egyenlet]] — a megoldhatóság feltétele és az összes megoldás
- [[concepts/dimatii/legnagyobb-kozos-oszto]] — a kimérhető mennyiségek generátora
- [[concepts/dimatii/oszthatosag]] — az invariáns: közös osztó oszt minden lineáris kombinációt
