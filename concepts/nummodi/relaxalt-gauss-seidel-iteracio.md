---
tags: [concept]
sources: [NM1_ea09.pdf]
derivation: source
kind: procedure
element: water
updated: 2026-09-25
---

# Relaxált Gauss–Seidel-iteráció ($S(\omega)$)

A [[concepts/nummodi/gauss-seidel-iteracio|Gauss–Seidel-iteráció]] $\omega$ paraméteres változata: komponensenként az előző érték és a Gauss–Seidel-érték súlyozott átlaga. Konvergenciájának szükséges feltétele $0 < \omega < 2$; szimmetrikus pozitív definit mátrixra ez elégséges is, tridiagonális esetben pedig optimális $\omega_0$ adható.

## Tartalom

### Levezetés (vektoros alak)

A Gauss–Seidel $(L+D)x = -Ux + b$ alakját $\omega$-val, a triviális $Dx = Dx$ egyenlőséget $(1-\omega)$-val szorozzuk, és összeadjuk:

$$(D + \omega L)x = \bigl[(1-\omega)D - \omega U\bigr]x + \omega b \iff x = (D+\omega L)^{-1}\bigl[(1-\omega)D - \omega U\bigr]x + \omega(D+\omega L)^{-1}b.$$

**Definíció — relaxált Gauss–Seidel-iteráció, $S(\omega)$:**

$$x^{(k+1)} = \underbrace{(D+\omega L)^{-1}\bigl[(1-\omega)D - \omega U\bigr]}_{B_{S(\omega)}}\,x^{(k)} + \underbrace{\omega(D+\omega L)^{-1}b}_{c_{S(\omega)}}.$$

$\omega = 1$ esetén visszakapjuk a Gauss–Seidelt: $S = S(1)$.

### Koordinátás alak

**Állítás.** $x_i^{(k+1)} = (1-\omega)\,x_i^{(k)} + \omega\,x_{i,S}^{(k+1)}$, ahol

$$x_{i,S}^{(k+1)} = -\frac{1}{a_{ii}}\Bigl(\sum_{j=1}^{i-1}a_{ij}x_j^{(k+1)} + \sum_{j=i+1}^n a_{ij}x_j^{(k)} - b_i\Bigr),$$

és minden lépés az $i = 1, 2, \dots, n$ sorrendben számolandó.

**Biz.**

$$(D+\omega L)x^{(k+1)} = (1-\omega)Dx^{(k)} - \omega Ux^{(k)} + \omega b$$
$$Dx^{(k+1)} = (1-\omega)Dx^{(k)} - \omega Lx^{(k+1)} - \omega Ux^{(k)} + \omega b$$
$$x^{(k+1)} = (1-\omega)x^{(k)} - \omega D^{-1}\bigl(Lx^{(k+1)} + Ux^{(k)} - b\bigr),$$

és a zárójeles tag $i$-edik komponense pontosan a Gauss–Seidel-lépés. $\square$

**Vigyázat:** $x^{(k+1)} = (1-\omega)x^{(k)} + \omega x_S^{(k+1)}$ *vektorként* nem igaz (ahol $x_S^{(k+1)}$ a teljes G–S-lépés $x^{(k)}$-ból), csak komponensenként: $x_{i,S}^{(k+1)}$ már a relaxált új komponenseket használja. (Szemben a [[concepts/nummodi/jacobi-iteracio|csillapított Jacobival]], ahol vektorra is igaz.)

### Reziduumvektoros alak

$$(D+\omega L)x^{(k+1)} = \bigl((1-\omega)D - \omega U\bigr)x^{(k)} + \omega b = Dx^{(k)} + \omega\underbrace{(-D-U)}_{L - A}x^{(k)} + \omega b = (D+\omega L)x^{(k)} + \omega r^{(k)},$$

így $x^{(k+1)} = x^{(k)} + \omega(D+\omega L)^{-1}r^{(k)}$. Az $s^{(k)} := \omega(D+\omega L)^{-1}r^{(k)}$ segédvektorral:

$$\begin{aligned}
&r^{(0)} := b - Ax^{(0)}\\
&k = 1, \dots, \text{leállásig:}\\
&\quad (D + \omega L)\,s^{(k)} = \omega r^{(k)} \ \text{ megoldása (alsó háromszögű LER)}\\
&\quad x^{(k+1)} := x^{(k)} + s^{(k)}\\
&\quad r^{(k+1)} := r^{(k)} - As^{(k)}
\end{aligned}$$

Szerepe ugyanaz, mint a többi módszernél: nincs inverz, lépésenként egy háromszögű LER és egy mátrix–vektor szorzás, és $s^{(k)} = x^{(k+1)} - x^{(k)}$, $r^{(k)}$ ingyen adja a leállási feltételt.

### A konvergencia szükséges feltétele

**Lemma.** $\displaystyle\det(B) = \prod_{i=1}^n \lambda_i(B)$.

**Biz.** A karakterisztikus polinom gyökei a sajátértékek; $\lambda$ hatványai szerint rendezve

$$p(\lambda) = \det(B - \lambda I) = \prod_{i=1}^n(\lambda_i - \lambda) = (-1)^n\lambda^n + \dots + \prod_{i=1}^n\lambda_i.$$

$\lambda = 0$-t helyettesítve a konstans tagot kapjuk: $p(0) = \det(B) = \prod_i \lambda_i$. $\square$

**Tétel.** Ha egy mátrixra az $S(\omega)$ módszer (minden kezdővektorra) konvergens, akkor $0 < \omega < 2$.

**Biz.** A konvergencia ekvivalens feltétele $\varrho(B_{S(\omega)}) < 1$ ([[concepts/nummodi/banach-fixponttetel-rn]]). Ebből minden $|\lambda_i(B_{S(\omega)})| < 1$, tehát a lemma szerint

$$\bigl|\det(B_{S(\omega)})\bigr| = \Bigl|\prod_{i=1}^n\lambda_i(B_{S(\omega)})\Bigr| < 1.$$

Másrészt $B_{S(\omega)} = (D+\omega L)^{-1}\bigl[(1-\omega)D - \omega U\bigr]$ két háromszögmátrix szorzata, és háromszögmátrix determinánsa a főátló szorzata (nem függ az átlón kívüli elemektől). $D + \omega L$ átlója $D$ átlója, $(1-\omega)D - \omega U$ átlója $(1-\omega)D$ átlója:

$$\bigl|\det(B_{S(\omega)})\bigr| = \underbrace{\bigl|\det\bigl((D+\omega L)^{-1}\bigr)\bigr|}_{1/|\det D|}\cdot\underbrace{\bigl|\det\bigl((1-\omega)D - \omega U\bigr)\bigr|}_{|1-\omega|^n\,|\det D|} = |1-\omega|^n < 1.$$

Ebből $|1 - \omega| < 1$, ami ekvivalens a $0 < \omega < 2$ feltétellel. $\square$

**Megj.** $\omega \notin (0,2)$ esetén tehát (a kezdővektortól függetlenül garantáltan) nem konvergál. A feltétel csak *szükséges*: $(0,2)$-beli $\omega$ mellett is lehet divergens.

### Speciális mátrixosztályok (bizonyítás nélkül)

1. **SZPD.** Ha $A$ szimmetrikus, pozitív definit és $\omega \in (0,2)$, akkor $S(\omega)$ konvergens. — SZPD mátrixra tehát a szükséges feltétel elégséges is.
2. **Tridiagonális.** Ha $A$ tridiagonális, akkor a Jacobi- és a Gauss–Seidel-iteráció egyszerre konvergens vagy divergens, mert
   $$\varrho(B_S) = \varrho(B_J)^2.$$
   Konvergencia esetén a Gauss–Seidel kétszer gyorsabb (egy G–S-lépés két Jacobi-lépést ér).
3. **Tridiagonális, SZPD.** Ekkor a Jacobi, a Gauss–Seidel és a relaxált Gauss–Seidel is konvergens, és $S(\omega)$-ra az optimális paraméter
   $$\omega_0 = \frac{2}{1 + \sqrt{1 - \varrho(B_J)^2}}.$$
   Ha $\varrho(B_J) = 0$, akkor $\omega_0 = 1$ és $\varrho(B_S) = \varrho(B_{S(\omega_0)}) = 0$; ha $\varrho(B_J) \ne 0$, akkor
   $$\varrho(B_{S(\omega_0)}) = \omega_0 - 1 < \varrho(B_S) = \varrho(B_J)^2.$$

Az utóbbi két tétel blokktridiagonális mátrixokra is igaz, a megfelelő blokkiterációkkal.

**Értelmezés.** A konvergencia sebességét a $q$ kontrakciós együttható adja ($0$ közelében gyors, $1$ közelében nagyon lassú). Mivel $\inf\{\|B\| : \|\cdot\| \text{ indukált norma}\} = \varrho(B)$, a sebességet végső soron a spektrálsugár határozza meg — ezért hasonlítják a tételek a spektrálsugarakat.

### Példa

$A = \begin{bmatrix}2&-1&0\\-1&2&-1\\0&-1&2\end{bmatrix}$ szimmetrikus, pozitív definit, tridiagonális. Ezért $J(1)$ konvergens; $J(\omega)$ konvergens $\omega \in (0,1)$-re; $S(1)$ konvergens; $S(\omega)$ pontosan $\omega \in (0,2)$-re konvergens.

$$B_J = \frac12\begin{bmatrix}0&1&0\\1&0&1\\0&1&0\end{bmatrix}, \qquad B_S = \frac18\begin{bmatrix}0&4&0\\0&2&4\\0&1&2\end{bmatrix}.$$

$B_J$ sajátértékei $0, \pm\tfrac{1}{\sqrt2}$, így $\varrho(B_J) = \tfrac{1}{\sqrt2}$; $B_S$ sajátértékei $0, 0, \tfrac12$, így $\varrho(B_S) = \tfrac12 = \varrho(B_J)^2$. Az optimális paraméter

$$\omega_0 = \frac{2}{1 + \sqrt{1 - \tfrac12}} = \frac{2\sqrt2}{\sqrt2 + 1} = 4 - 2\sqrt2 \approx 1{,}1716, \qquad \varrho(B_{S(\omega_0)}) = \omega_0 - 1 = 3 - 2\sqrt2 \approx 0{,}1716.$$

Matlab-kísérlet a $\operatorname{tridiag}(-1, 4, -1)$ mátrixra: a tapasztalati kontrakciós együttható $\omega = 1$-re $\approx 0{,}125$, $\omega = 1{,}033$-ra $\approx 0{,}040$ (optimum közelében), $\omega = 0{,}8$-ra $\approx 0{,}375$, $\omega = 0{,}6$-ra $\approx 0{,}565$; $\omega = -0{,}1;\ 2;\ 2{,}5$ mellett divergens.

### Jacobi és Gauss–Seidel típusú iterációk összevetése

| | Jacobi $J(\omega)$ | Gauss–Seidel $S(\omega)$ |
|---|---|---|
| $P$ (kétrétegű alakban) | $\tfrac1\omega D$ | $\tfrac1\omega D + L$ |
| Lépésenkénti LER | diagonális | alsó háromszögű |
| Tárolás | két vektor ($x^{(k)}$, $x^{(k+1)}$) | egy vektor, helyben felülír |
| SDD mátrixra | konvergens ($\omega = 1$) | konvergens, $\|B_S\|_\infty \le \|B_J\|_\infty$ |
| SZPD mátrixra | (nincs tanult tétel) | $S(\omega)$ konvergens $\omega \in (0,2)$-re |
| Tridiagonálisra | — | $\varrho(B_S) = \varrho(B_J)^2$: kétszer gyorsabb |
| Paramétertartomány | $J(\omega)$: $0 < \omega < 1$ elégséges, ha $J$ konvergens | $0 < \omega < 2$ szükséges |

### Vizsgán (22. tétel)

- **a)** $S(\omega)$ vektoros alakjának levezetése (súlyozott összeg), koordinátás alak, reziduumvektoros alak és algoritmus.
- **b)** a szükséges feltétel bizonyítása (lemma + determináns); Jacobi–Gauss–Seidel összevetés; a három speciális tétel kimondása és értelmezése.

A 21. tétel b) része ugyanezt a bizonyítást kéri.

## Kapocs

- [[concepts/nummodi/gauss-seidel-iteracio]] — $\omega = 1$ eset, SDD és SZPD konvergenciatételek
- [[concepts/nummodi/jacobi-iteracio]] — csillapított Jacobi $J(\omega)$, az analóg konstrukció
- [[concepts/nummodi/banach-fixponttetel-rn]] — $\varrho(B) < 1$ mint szükséges és elégséges feltétel
- [[concepts/nummodi/iteracios-modszerek-ler]] — $A = L + D + U$ felbontás
- [[concepts/nummodi/matrixnormak]] — spektrálsugár és indukált normák kapcsolata
- [[concepts/nummodi/ilu-felbontas]] — általános kétrétegű iteráció, $P = \tfrac1\omega D + L$
