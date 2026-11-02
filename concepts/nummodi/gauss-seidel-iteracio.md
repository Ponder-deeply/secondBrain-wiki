---
tags: [concept]
sources: [NM1_ea09.pdf]
derivation: source
kind: procedure
element: water
updated: 2026-09-25
---

# Gauss–Seidel-iteráció

Az $Ax = b$ LER iteratív megoldása az $A = L + D + U$ felbontásból $P = L + D$ választással. Koordinátánként a már kiszámolt új komponenseket azonnal felhasználja, ezért „helyben” számolható; szigorúan diagonálisan domináns és szimmetrikus pozitív definit mátrixra konvergens.

## Tartalom

### Levezetés (mátrixos alak)

Az [[concepts/nummodi/iteracios-modszerek-ler|iterációs módszerek]] keretében, $A = L + D + U$ (szigorú alsó rész, átló, szigorú felső rész):

$$Ax = b \iff (L + D + U)x = b \iff (L + D)x = -Ux + b \iff x = -(L+D)^{-1}Ux + (L+D)^{-1}b.$$

**Definíció — Gauss–Seidel-iteráció ($S$ vagy $S(1)$):**

$$x^{(k+1)} = \underbrace{-(L+D)^{-1}U}_{B_S}\,x^{(k)} + \underbrace{(L+D)^{-1}b}_{c_S}.$$

### Koordinátás alak

**Állítás.**

$$x_i^{(k+1)} = -\frac{1}{a_{ii}}\Bigl(\sum_{j=1}^{i-1} a_{ij}x_j^{(k+1)} + \sum_{j=i+1}^{n} a_{ij}x_j^{(k)} - b_i\Bigr) \qquad (i = 1, 2, \dots, n).$$

**Biz.** Átrendezve, majd a mátrixszorzást soronként kiírva:

$$(L+D)x^{(k+1)} = -Ux^{(k)} + b \iff Dx^{(k+1)} = -Lx^{(k+1)} - Ux^{(k)} + b \iff x^{(k+1)} = -D^{-1}\bigl(Lx^{(k+1)} + Ux^{(k)} - b\bigr).$$

Az $i$-edik sorban $Lx^{(k+1)}$ csak az $x_1^{(k+1)},\dots,x_{i-1}^{(k+1)}$ komponenseket tartalmazza, amelyeket $i = 1, 2, \dots, n$ sorrendben haladva már kiszámoltunk. $\square$

Ezért az új értékek felülírhatják a régieket: egyetlen vektor elég („helyben” számolás). Ez a különbség a [[concepts/nummodi/jacobi-iteracio|Jacobi-iterációhoz]] képest, ahol a jobb oldalon csak $x^{(k)}$ szerepel.

### Reziduumvektoros alak

$$(L+D)x^{(k+1)} = -Ux^{(k)} + b = \bigl((L+D) - A\bigr)x^{(k)} + b = (L+D)x^{(k)} + \underbrace{(b - Ax^{(k)})}_{r^{(k)}},$$

tehát $x^{(k+1)} = x^{(k)} + (L+D)^{-1}r^{(k)}$. Az $s^{(k)} := (L+D)^{-1}r^{(k)}$ segédvektorral $x^{(k+1)} = x^{(k)} + s^{(k)}$, és az új reziduum

$$r^{(k+1)} = b - A(x^{(k)} + s^{(k)}) = r^{(k)} - As^{(k)}.$$

**Algoritmus.**

$$\begin{aligned}
&r^{(0)} := b - Ax^{(0)}\\
&k = 1, \dots, \text{leállásig:}\\
&\quad (D + L)\,s^{(k)} = r^{(k)} \ \text{ megoldása (alsó háromszögű LER, nem invertálunk)}\\
&\quad x^{(k+1)} := x^{(k)} + s^{(k)}\\
&\quad r^{(k+1)} := r^{(k)} - As^{(k)}
\end{aligned}$$

**A reziduumos alak szerepe:** lépésenként egy mátrix–vektor szorzás és egy háromszögű LER; $x^{(k+1)} - x^{(k)} = s^{(k)}$ közvetlenül adott, így olcsó a tapasztalati kontrakciós együttható és a leállási feltétel ($\|s^{(k)}\|$ vagy $\|r^{(k)}\|$ kicsi) számolása. Ugyanez a séma közös minden iterációnkban, csak a $P$ mátrix más (lásd [[concepts/nummodi/ilu-felbontas|általános kétrétegű iteráció]]).

### Konvergenciatételek

**Tétel (SDD).** Ha $A$ szigorúan diagonálisan domináns a soraira, akkor

$$\|B_S\|_\infty \le \|B_J\|_\infty < 1,$$

tehát a Gauss–Seidel-iteráció bármely $x^{(0)}$-ra konvergens. (Biz. nélkül.)

**Tétel (SZPD).** Ha $A$ szimmetrikus és pozitív definit, akkor a Gauss–Seidel-iteráció konvergens. (Biz. nélkül.)

A konvergencia a [[concepts/nummodi/banach-fixponttetel-rn|Banach-féle fixponttételből]] ill. a $\varrho(B_S) < 1$ ekvivalens feltételből következik. Tridiagonális mátrixra $\varrho(B_S) = \varrho(B_J)^2$ — lásd [[concepts/nummodi/relaxalt-gauss-seidel-iteracio]].

### Vizsgán (21. tétel)

- **a)** vektoros alak levezetése $A = L+D+U$-ból; koordinátás alak; reziduumvektoros alak és algoritmus, a szerepével.
- **b)** a *relaxációs módszer* konvergenciájának szükséges feltétele ($0 < \omega < 2$) — a bizonyítás a [[concepts/nummodi/relaxalt-gauss-seidel-iteracio]] lapon van (determináns-lemma + háromszögmátrixok determinánsa); $\omega = 1$ a Gauss–Seidel.

## Kapocs

- [[concepts/nummodi/relaxalt-gauss-seidel-iteracio]] — $S(\omega)$ általánosítás, a 21. b) bizonyítása
- [[concepts/nummodi/jacobi-iteracio]] — $P = D$; a Gauss–Seidel $P = D + L$
- [[concepts/nummodi/iteracios-modszerek-ler]] — $A = L + D + U$ felbontás, átmenetmátrix
- [[concepts/nummodi/banach-fixponttetel-rn]] — konvergencia $\|B\| < 1$ ill. $\varrho(B) < 1$ mellett
- [[concepts/nummodi/matrixnormak]] — $\|\cdot\|_\infty$ sornorma
