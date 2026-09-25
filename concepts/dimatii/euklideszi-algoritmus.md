---
tags: [concept, dimatii/elemi-szamelmelet]
sources: [DimatIIEa01.pdf]
derivation: source
updated: 2026-09-08
---

# Euklideszi algoritmus

Maradékos osztások láncolata, amely véges sok lépésben megadja két egész legnagyobb közös osztóját — egyúttal bizonyítja, hogy az mindig létezik.

## Tartalom

**Tétel.** Bármely két egész számnak létezik legnagyobb közös osztója, és ez meghatározható az euklideszi algoritmussal.

**Bizonyítás.** Ha valamelyik szám $0$, akkor a legnagyobb közös osztó a másik szám. Tegyük fel, hogy $a, b$ nem nulla, és végezzük el a következő osztásokat:

$$
\begin{aligned}
a &= bq_1 + r_1, & 0 &< r_1 < |b|,\\
b &= r_1q_2 + r_2, & 0 &< r_2 < r_1,\\
r_1 &= r_2q_3 + r_3, & 0 &< r_3 < r_2,\\
&\;\;\vdots\\
r_{n-2} &= r_{n-1}q_n + r_n, & 0 &< r_n < r_{n-1},\\
r_{n-1} &= r_nq_{n+1}. &&
\end{aligned}
$$

*Végesség:* $|b| > r_1 > r_2 > \dots \geq 0$ szigorúan csökkenő nemnegatív egész sorozat, tehát az algoritmus véges sok lépésben véget ér.

*$r_n$ közös osztó:* $r_n \mid r_{n-1}$, ezért $r_n \mid r_{n-1}q_n + r_n = r_{n-2}$, és így visszafelé haladva $r_n \mid b$, majd $r_n \mid a$.

*$r_n$ a legnagyobb:* legyen $c \mid a$ és $c \mid b$. Ekkor $c \mid a - bq_1 = r_1$, majd $c \mid b - r_1q_2 = r_2$, és így tovább $c \mid r_{n-2} - r_{n-1}q_n = r_n$. $\square$

Az utolsó nem nulla maradék tehát a legnagyobb közös osztó: $(a,b) = r_n$.

**Példa.** $(172, 62)$:

| $i$ | $r_i$ | $q_i$ | $r_{i-2} = r_{i-1}q_i + r_i$ |
|---:|---:|---:|---|
| — | 172 | — | — |
| — | 62 | — | — |
| 1 | 48 | 2 | $172 = 62\cdot 2 + 48$ |
| 2 | 14 | 1 | $62 = 48\cdot 1 + 14$ |
| 3 | 6 | 3 | $48 = 14\cdot 3 + 6$ |
| 4 | 2 | 2 | $14 = 6\cdot 2 + 2$ |
| 5 | 0 | 3 | $6 = 2\cdot 3 + 0$ |

Tehát $(172,62) = 2$.

### Rekurzív alak

**Tétel.** Legyen $a \neq 0$. Ha $b = 0$, akkor $(a,b) = a$. Ha $b \neq 0$, akkor
$$(a,b) = \big(|b|,\; a \bmod |b|\big).$$

**Bizonyítás.** $b = 0$ esetén az állítás nyilvánvaló. Ha $b \neq 0$, osszuk el maradékosan $a$-t $|b|$-vel: $a = |b|\cdot q + (a \bmod |b|)$. Ez az euklideszi algoritmus első sora. $\square$

**Példa.** $(172,62)$ rekurzívan: $(172,62) \to (62,48) \to (48,14) \to (14,6) \to (6,2) \to (2,0)$, tehát $(172,62) = 2$.

## Kapocs

- [[concepts/dimatii/legnagyobb-kozos-oszto]] — a kiszámított fogalom
- [[concepts/dimatii/bovitett-euklideszi-algoritmus]] — az algoritmus kiterjesztése $xa + yb = (a,b)$ előállítására
- [[concepts/dimatii/maradekos-osztas]] — az algoritmus elemi lépése
- [[concepts/dimatii/oszthatosag]] — a lineáris kombinációra vonatkozó tulajdonság, amin a helyesség múlik
- [[concepts/dimatii/polinomok-bovitett-euklideszi-algoritmusa]] — ugyanez az eljárás polinomokra, test fölött
