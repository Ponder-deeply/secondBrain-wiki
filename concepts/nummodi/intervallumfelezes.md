---
tags: [concept]
sources: [NM1_ea11.pdf]
derivation: source
kind: procedure
element: water
updated: 2026-10-21
---

# Intervallumfelezés (bisection)

Ha $f \in C[a;b]$ és $f(a)f(b) < 0$, a gyököt tartalmazó intervallumot lépésenként felezzük, mindig azt a felét tartva meg, amelyen $f$ előjelet vált. Mindig konvergál, és a $k$-adik lépés után a hiba $(b-a)/2^k$ alatt marad, de lassú (elsőrendű).

## Tartalom

### Algoritmus

A [[concepts/nummodi/nemlinearis-egyenletek-fixpont|Bolzano-tétel]] feltételei mellett ($f \in C[a;b]$, $f(a)\cdot f(b) < 0$):

1. $x_0 := a$, $y_0 := b$.
2. Ismételjük:
   - $s_k := \tfrac12(x_k + y_k)$, az intervallum felezőpontja;
   - ha $f(x_k)\cdot f(s_k) < 0$, akkor $x_{k+1} := x_k$, $y_{k+1} := s_k$;
   - ha $f(x_k)\cdot f(s_k) > 0$, akkor $x_{k+1} := s_k$, $y_{k+1} := y_k$.
3. Megállunk, ha
   - $f(s_k) = 0$: ekkor $x^* = s_k$ (általában nem fordul elő), vagy
   - elértük a kívánt pontosságot: $x^* \in (x_k, y_k)$, ahol $y_k - x_k = \tfrac{y_{k-1} - x_{k-1}}{2}$.

Ez egyben a Bolzano-tétel konstruktív bizonyítása: az egymásba skatulyázott intervallumok végpontsorozatai (analízisből) közös határértékhez tartanak, ahol $f$ folytonossága miatt $f = 0$.

### Hibabecslés

Minden lépésben megfeleződik az intervallum, így $y_k - x_k = \tfrac{b-a}{2^k}$, és $x^* \in (x_k, y_k)$ miatt

$$|x_k - x^*| < \frac{b - a}{2^k}, \qquad |y_k - x^*| < \frac{b - a}{2^k}, \qquad |s_k - x^*| < \frac{b - a}{2^{k+1}}.$$

(A felezőpont legfeljebb a fél intervallumhossznyira van bármely belső ponttól.) A szükséges lépésszám előre kiszámítható: $\varepsilon$ pontossághoz $\tfrac{b-a}{2^k} < \varepsilon$.

### Példa

$P(x) = x^3 + 3x - 2$ egy gyöke $0{,}1$ pontossággal, $[0;1]$-en. $P(0) = -2 < 0$, $P(1) = 2 > 0$, tehát van gyök $(0;1)$-ben. $\tfrac{1}{2^k} < \tfrac{1}{10} \iff k > 3$, tehát legalább $4$ lépés kell. Lassú.

**Egyértelműség:** ha még $f \in D(a;b)$ és $f' > 0$ (vagy $< 0$), a gyök egyértelmű — itt $P'(x) = 3x^2 + 3 > 0$.

### Tulajdonságok

- Robusztus: csak folytonosság és előjelváltás kell, mindig konvergál.
- Lassú: a hibakorlát lépésenként feleződik — elsőrendű jellegű (lásd [[concepts/nummodi/konvergenciarend]]); egy tizedesjegyhez kb. $3{,}3$ lépés.
- Gyakran jó kezdőpontot ad egy gyorsabb módszerhez (pl. a [[concepts/nummodi/newton-modszer|Newton-módszer]] lokális konvergenciájához).

### Vizsgán (27. tétel, a) első fele)

Az algoritmus vázolása és a hibabecslés. A tétel többi része a [[concepts/nummodi/newton-modszer]] lapon.

## Kapocs

- [[concepts/nummodi/nemlinearis-egyenletek-fixpont]] — Bolzano-tétel, a gyök létezése és egyértelműsége
- [[concepts/nummodi/newton-modszer]] — a 27. tétel másik (fő) része
- [[concepts/nummodi/hurmodszer-szelomodszer]] — a húrmódszer ugyanígy tartja az előjelváltást, de felező pont helyett a húr zérushelyét veszi
- [[concepts/nummodi/konvergenciarend]] — sebesség összevetése
