---
tags:
  - subject
sources:
  - NM1_ea01.pdf
  - NM1_ea02.pdf
  - NM1_ea03.pdf
  - NM1_ea04.pdf
  - NM1_ea05.pdf
  - NM1_ea06.pdf
  - NM1_ea07.pdf
  - NM1_ea08.pdf
  - NM1_ea09.pdf
  - NM1_ea10.pdf
  - NM1_ea11.pdf
  - NM1_ea13.pdf
derivation: source
updated: 2026-08-05
state: "[[IV]]"
---

# Numerikus módszerek 1. (nummodi)

Bevezetés a numerikus analízis alapvető módszereibe: lebegőpontos számábrázolás, közelítő számítások hibaelemzése, lineáris egyenletrendszerek direkt és iteratív megoldása, mátrixfelbontások, kondícionáltság, valamint nemlineáris egyenletek megoldása.

## Tárgykör

- Oktató: Krebsz Anna (ELTE IK)
- Félév: iv. félév
- Kapcsolódó anyagok: `Wiki/outputs/nummodi/`
- [[concepts/nummodi/tematika]] — a kurzus tematikája félév és témakör szerint
- [[concepts/nummodi/kovetelmenyek]] — szóbeli tételjegyzék, 28 tétel Alap/Complex bontásban

## Fogalomlapok

### Gépi számábrázolás és hibaszámítás (1. előadás)

A lebegőpontos számábrázolás modellje és a numerikus hibák rendszeres elemzése — ezek alkotják az egész kurzus fogalmi alapját.

- [[concepts/nummodi/lebegopont-modell]] — normalizált $M(t,k^-,k^+)$ gépi számhalmaz, mantissza, karakterisztika, input függvény és az input hiba tétele
- [[concepts/nummodi/hibaszamitas]] — abszolút/relatív hiba és korlátaik, alapműveletek hibaterjedési tételei, kondíciószám kapcsolata
- [[concepts/nummodi/algoritmus-stabilitas]] — stabil algoritmus definíciója, $T_n$ rekurzió és Fibonacci példák, stabilitás vs. kondíció

### Lineáris egyenletrendszerek és Gauss-elimináció (2. előadás)

Az $Ax = b$ rendszer megoldásának direkt megközelítése: Gauss-elimináció általános lépésformulája, visszahelyettesítés, főelemkiválasztás, determináns- és inverzszámítás.

- [[concepts/nummodi/linearis-egyenletrendszerek]] — $Ax = b$ alak, megoldhatósági feltételek, módszerek taxonómiája (direkt, iteratív, variációs)
- [[concepts/nummodi/gauss-eliminacio]] — elimináció + visszahelyettesítés, főelemkiválasztás, determináns, inverz, $\tfrac{2}{3}n^3$ és $n^2$ műveletigény

### LU-felbontás (3. előadás)

Mátrixfelbontás alsó és felső háromszögmátrixok szorzataként: $A = LU$, ahol $L \in \mathcal{L}_1$ és $U \in \mathcal{U}$. A felbontás a Gauss-elimináció mátrixos átírásából adódik, és lineáris egyenletrendszerek hatékony (és újrafelhasználható) megoldását teszi lehetővé.

- [[concepts/nummodi/haromszogmatrixok]] — $\mathcal{L}/\mathcal{U}/\mathcal{L}_1/\mathcal{U}_1$ halmazok, zártsági állítások, $L_k = I - \ell_k e_k^T$ eliminációs mátrixok
- [[concepts/nummodi/lu-felbontas]] — definíció, GE-alapú levezetés, létezés/egyértelműség (főminorok), Doolittle-képletek, LER-megoldás, $\tfrac{2}{3}n^3$ műveletigény

### Megmaradási tételek és speciális felbontások (4. előadás)

A GE blokkos értelmezése a Schur-komplementer fogalmán keresztül; a mátrixtulajdonságok öröklődése az eliminálás során; tridiagonális és szimmetrikus speciális esetekre épülő hatékony felbontások.

- [[concepts/nummodi/schur-komplementer]] — $[A\mid A_{11}] = A_{22} - A_{21}A_{11}^{-1}A_{12}$; megmaradási tételek (det, szimmetria, pozitív definitség, diagonális dominancia, sávszélesség, profil)
- [[concepts/nummodi/progonka-modszer]] — rövidített GE tridiagonális LER-re; előre/vissza rekurzió; $8n + O(1)$ műveletigény; köbös spline alkalmazás
- [[concepts/nummodi/ldu-felbontas]] — $A = LDU$; szimmetrikus esetben $A = LDL^T$; Cholesky-felbontás ($A = LL^T$) pozitív definit esetben; $\tfrac{1}{3}n^3$ igény

### QR-felbontás és ortogonalizáció (5. előadás)

Reguláris $A \in \mathbb{R}^{n \times n}$ mátrix felírható $A = QR$ alakban, ahol $Q$ ortogonális és $R$ felső háromszögmátrix. A felbontás numerikusan stabilabb LER-megoldást ad, mint a közvetlen Gauss-elimináció.

- [[concepts/nummodi/ortogonalis-matrixok]] — ortogonális/ortonormált rendszerek, skaláris szorzat, kettes norma, szorzatra való zártság
- [[concepts/nummodi/qr-felbontas]] — definíció, egzisztencia/egyértelműség, LER-megoldás $Rx = Q^Tb$ alakban, $\tfrac{2}{3}n^3$ előállítás
- [[concepts/nummodi/gram-schmidt-ortogonalizacio]] — Gram–Schmidt normálással és anélkül, $2n^3 + O(n^2)$ műveletigény, kidolgozott $2\times2$ példa
- [[concepts/nummodi/householder-transzformacio]] — $H(v) = I - 2vv^T$, tükrözési tétel, stabil előjelválasztás, felső háromszög alakra hozás

**Módszerek összehasonlítása:** Gram–Schmidt: $2n^3$ (QR), egyszerűbb; Householder: $\tfrac{8}{3}n^3$ (QR), de numerikusan stabilabb — az ipari standard.

### Vektor- és mátrixnormák (6. előadás)

A normák elmélete az $Ax = b$ rendszerek kondícionáltságának és numerikus stabilitásának vizsgálatához alapvetően szükséges.

- [[concepts/nummodi/vektornormak]] — normák axiómái; $\ell^1$, $\ell^2$, $\ell^\infty$ és p-normák; ekvivalencia $\mathbb{R}^n$-en; CBS-egyenlőtlenség
- [[concepts/nummodi/matrixnormak]] — szubmultiplikativitás, Frobenius-norma, indukált normák ($\|A\|_1$, $\|A\|_\infty$, $\|A\|_2$), spektrálsugár, illeszkedő normák

### LER érzékenysége és kondícionáltság (7. előadás)

Az $Ax = b$ rendszer megoldásának stabilitása a bemeneti adatok kis megváltozásakor. A kondíciószám ($\operatorname{cond}(A) = \|A\|\cdot\|A^{-1}\|$) méri, mennyire erősíti fel a mátrix a relatív hibákat.

- [[concepts/nummodi/kondicioszam]] — definíció, $\operatorname{cond}(A) \geq 1$, ortogonális/szimmetrikus/pozitív definit esetek, Hilbert- és Vandermonde-példák
- [[concepts/nummodi/ler-erzekenysege]] — perturbációs tételek jobboldalra és mátrixra; Neumann-lemma; egyesített tétel
- [[concepts/nummodi/relativ-maradek]] — maradékvektor $r = b - A\tilde{x}$, relatív maradék $\eta$, stabilitási értelmezés

### Iteratív módszerek LER-re (8–10. előadás)

Az iteratív módszerek az $Ax = b$ rendszert $x = Bx + c$ fixpontalakká írják át. Konvergencia szükséges és elégséges feltétele $\varrho(B) < 1$. Az $A = L + D + U$ felbontás az alapja a Jacobi-, Gauss–Seidel- és SOR-módszereknek.

- [[concepts/nummodi/iteracios-modszerek-ler]] — általános keret ($A = P + Q$, $A = L+D+U$), fixpont-iteráció, átmenetmátrix $B$, ILU-előkészítés
- [[concepts/nummodi/banach-fixponttetel-rn]] — fixpont és kontrakció; Banach-tétel 4 állítása teljes bizonyítással; $\varrho(B) < 1$ ekvivalens feltétel
- [[concepts/nummodi/jacobi-iteracio]] — $B_J = -D^{-1}(L+U)$, komponensenkénti és reziduumos alak, SDD konvergenciatétel, csillapított $J(\omega)$

A Gauss–Seidel-, relaxációs, Richardson- és ILU-módszerek (21–24. tétel) lapjai még nincsenek megírva.

**Megjegyzés:** A forrás (NM1_ea10.md) a kerekítési hibák iteratív módszerekre gyakorolt hatásáról szóló szekciót nem tartalmazza (csonka PDF-konverzió).

### Nemlineáris egyenletek és polinomok (11., 13. előadás)

Gyökkereső módszerek nemlineáris $f(x) = 0$ egyenletekre: intervallumfelezés (lassú, robusztus) és fixpont-iteráció (potenciálisan gyors, konvergencia-analízist igényel). A 13. előadás önálló blokk: a gyökbecslési tétel megmondja, hol keressük a gyököket, a Horner-algoritmus pedig a kiértékelési eszköz, amelyre a gyökkeresők támaszkodnak.

Ezek anyagának lapjai (25–28. tétel) még nincsenek megírva.

## Tételjegyzék (szóbeli)

A 28 vizsgatétel kidolgozása, egy lap tételenként — lásd [[concepts/nummodi/kovetelmenyek|kovetelmenyek]] az Alap/Complex bontásért.

| # | Tétel | Lap |
|---|---|---|
| 1 | Lebegőpontos számok és tulajdonságaik | [[concepts/nummodi/lebegopont-modell]] |
| 2 | Hibaszámítás | [[concepts/nummodi/hibaszamitas]] |
| 3 | A Gauss-elimináció | [[concepts/nummodi/gauss-eliminacio]] |
| 4 | GE és LU kapcsolata I. | [[concepts/nummodi/lu-felbontas]] |
| 5 | GE és LU kapcsolata II. | [[concepts/nummodi/lu-felbontas]] |
| 6 | Az LU-felbontás direkt módon | [[concepts/nummodi/lu-felbontas]] |
| 7 | A Schur-komplementer | [[concepts/nummodi/schur-komplementer]] |
| 8 | LDU-felbontás | [[concepts/nummodi/ldu-felbontas]] |
| 9 | A Cholesky-féle $LL^T$-felbontás | [[concepts/nummodi/ldu-felbontas]] |
| 10 | QR-felbontás Gram–Schmidt ortogonalizációval | [[concepts/nummodi/gram-schmidt-ortogonalizacio]] |
| 11 | A Householder-transzformáció I. | [[concepts/nummodi/householder-transzformacio]] |
| 12 | A Householder-transzformáció II. | [[concepts/nummodi/householder-transzformacio]] |
| 13 | Mátrixnormák és tulajdonságaik I. | [[concepts/nummodi/matrixnormak]] |
| 14 | Mátrixnormák és tulajdonságaik II. | [[concepts/nummodi/matrixnormak]] |
| 15 | Frobenius mátrixnorma, illeszkedés | [[concepts/nummodi/matrixnormak]] |
| 16 | LER érzékenysége I. (jobboldal perturbációja) | [[concepts/nummodi/ler-erzekenysege]] |
| 17 | LER érzékenysége II. (mátrix perturbációja) | [[concepts/nummodi/ler-erzekenysege]] |
| 18 | Iterációs módszerek konvergenciája | [[concepts/nummodi/iteracios-modszerek-ler]] |
| 19 | A Jacobi-iteráció | [[concepts/nummodi/jacobi-iteracio]] |
| 20 | A csillapított Jacobi-iteráció | [[concepts/nummodi/jacobi-iteracio]] |
| 21 | A Gauss–Seidel-iteráció | — *(nincs lap)* |
| 22 | A Gauss–Seidel relaxációs módszer | — *(nincs lap)* |
| 23 | A Richardson-típusú iterációk | — *(nincs lap)* |
| 24 | ILU algoritmus (részleges LU-felbontás) | — *(nincs lap)* |
| 25 | Nemlineáris egyenletek megoldása I. | — *(nincs lap)* |
| 26 | Nemlineáris egyenletek megoldása II. | — *(nincs lap)* |
| 27 | Nemlineáris egyenletek megoldása III. | — *(nincs lap)* |
| 28 | Polinomok gyökeinek becslése | — *(nincs lap)* |

## Kapocs

- [[subjects/analii]] — a derivált és a Taylor-formula, amire a numerikus módszerek épülnek
- [[subjects/linalg]] — a mátrixfelbontások és normák vizuális szemléltetése
