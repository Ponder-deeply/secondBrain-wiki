---
tags: [concept, synthesis]
sources: []
derivation: unsourced
updated: 2026-09-04
---

# Lineáris algebra — vizuális szemléltetések

Animált intuíció a mátrixokkal/vektorokkal végzett műveletekről: a szummás
(elemenkénti) előállításokról, a sor–oszlop összefüggésekről, a leképezések
geometriájáról és a numerikus algoritmusok lényegéről. A sorozat a numerikus
módszerek tételeit (Gauss/LU, Cholesky, QR, normák, kondíciószám, iterációk)
támasztja alá geometriai és algebrai képpel.

> Szín-konvenció végig: **A / első mátrix = kék**, **második faktor = zöld**,
> **eredmény = sárga**, **ismert = teal**, **ismeretlen / kiemelt = piros**.

> **Állapot:** ez a lap a sorozat *forgatókönyve*. A 11 jelenet leírása
> kész, egyik animáció sincs még legyártva. A `manim` készség **törölve**
> (2026-09-04): a `manim` bináris nincs telepítve, így a készség sosem tudott
> lefutni. A legyártáshoz előbb a Manimot kell telepíteni; a kész fájlok helye
> `Wiki/outputs/`.

## Tartalom

**A modul — [[#A modul — Algebrai alapok: szumma és sor-oszlop nézetek|Algebrai alapok]]**
- [[#1. Mátrix · vektor — két olvasat|1. Mátrix · vektor — két olvasat]]
- [[#2. Mátrix · mátrix — négy nézet|2. Mátrix · mátrix — négy nézet]]
- [[#3. Transzponált és szimmetria|3. Transzponált és szimmetria]]

**B modul — [[#B modul — A leképezés geometriája|A leképezés geometriája]]**
- [[#4. Mátrix mint a sík torzítása|4. Mátrix mint a sík torzítása]]
- [[#5. Determináns = előjeles területváltozás|5. Determináns = előjeles területváltozás]]
- [[#6. Sajátvektor és sajátérték|6. Sajátvektor és sajátérték]]

**C modul — [[#C modul — Numerikus algoritmusok és normák|Numerikus algoritmusok és normák]]**
- [[#7. Gauss-elimináció = LU-felbontás|7. Gauss-elimináció = LU-felbontás]]
- [[#8. Gram–Schmidt és QR|8. Gram–Schmidt és QR]]
- [[#9. Vektornormák egységgömbjei|9. Vektornormák egységgömbjei]]
- [[#10. Kondíciószám: kör → ellipszis|10. Kondíciószám: kör → ellipszis]]
- [[#11. Fixpont-iteráció konvergenciája|11. Fixpont-iteráció konvergenciája]]

---

## A modul — Algebrai alapok: szumma és sor-oszlop nézetek

### 1. Mátrix · vektor — két olvasat

Az $Ax$ szorzatot kétféleképp olvashatjuk. **Sor-kép:** minden kimenő komponens
egy *sor* és $x$ skaláris szorzata. **Oszlop-kép:** $Ax$ az $A$ *oszlopainak*
lineáris kombinációja, ahol a súlyok $x$ komponensei — ez a geometriai jelentés
(vektor-összeg a síkban).

$$\underbrace{(Ax)_i = \sum_j a_{ij}\,x_j}_{\text{sor-kép}} \qquad
\underbrace{Ax = \sum_j x_j\, a_{:j}}_{\text{oszlop-kép}}$$

> ⏳ **Még nincs renderelve** — tervezett fájlnév: `matrix-vector-two-views.mp4`.
> A jelenet leírása fent teljes; a Manim-szkript megírása van hátra.

### 2. Mátrix · mátrix — négy nézet

Ugyanaz a $C = AB$ szorzat négy egyenértékű előállításban: **(a)** elemenként
(sor·oszlop skaláris szorzat), **(b)** oszloponként ($C$ egy oszlopa = $A$
oszlopainak lin. kombinációja), **(c)** soronként, **(d)** diád-összegként
(rang-1 mátrixok összege). A négy nézet ugyanannak a műveletnek a különböző
„olvasata".

$$c_{ij}=\sum_k a_{ik}b_{kj} \qquad C=\sum_k a_{:k}\,b_{k:}$$

> ⏳ **Még nincs renderelve** — tervezett fájlnév: `matrix-matrix-four-views.mp4`.
> A jelenet leírása fent teljes; a Manim-szkript megírása van hátra.

### 3. Transzponált és szimmetria

$A^T$ a főátlóra tükröz (sorok ↔ oszlopok). A szorzat transzponáltja megfordít:
$(AB)^T = B^TA^T$. A **Gram-mátrix** $A^TA$ $(i,j)$ eleme az $A$ $i$-edik és
$j$-edik *oszlopának* skaláris szorzata — innen ered az ortogonalitás (QR) és a
normák kapcsolata.

$$(A^T)_{ij}=A_{ji}\qquad (A^TA)_{ij}=\langle a_{:i},\,a_{:j}\rangle$$

> ⏳ **Még nincs renderelve** — tervezett fájlnév: `transpose-symmetry.mp4`.
> A jelenet leírása fent teljes; a Manim-szkript megírása van hátra.

---

## B modul — A leképezés geometriája

### 4. Mátrix mint a sík torzítása

Egy mátrix lineáris leképezésként deformálja a rácsot; az **oszlopai pontosan
az $e_1, e_2$ bázisvektorok képei**. Forgatás, nyújtás, nyírás, tükrözés — és
végül egy szinguláris vetítés, ami egy egyenesre lapít ($\det = 0$).

> ⏳ **Még nincs renderelve** — tervezett fájlnév: `linear-map-grid.mp4`.
> A jelenet leírása fent teljes; a Manim-szkript megírása van hátra.

### 5. Determináns = előjeles területváltozás

Az egységnégyzet képe paralelogramma, melynek területe $|\det A|$. A determináns
**előjele** az orientáció: negatív $\det$ = tükrözés. Ha $\det A = 0$, a négyzet
egy szakaszra omlik — a mátrix nem invertálható.

$$\text{terület}(A\,\square) = |\det A|$$

> ⏳ **Még nincs renderelve** — tervezett fájlnév: `determinant-area.mp4`.
> A jelenet leírása fent teljes; a Manim-szkript megírása van hátra.

### 6. Sajátvektor és sajátérték

A legtöbb vektort a mátrix elforgatja, de a **sajátirányok** nem fordulnak el —
azok mentén $Av$ csak $\lambda$-szorosára nyúlik: $Av = \lambda v$. Ez a kép adja
az iterációs módszerek konvergenciájának kulcsát (spektrálsugár).

$$A v = \lambda v$$

> ⏳ **Még nincs renderelve** — tervezett fájlnév: `eigenvectors.mp4`.
> A jelenet leírása fent teljes; a Manim-szkript megírása van hátra.

---

## C modul — Numerikus algoritmusok és normák

### 7. Gauss-elimináció = LU-felbontás

A Gauss-elimináció minden lépése elemi (alsó háromszög) mátrixszal való balszorzás.
A $m_{ik} = a_{ik}/a_{kk}$ **szorzók $L$-be gyűlnek**, a megmaradó felső háromszög
$U$. Eredmény: $A = LU$.

$$A = L\,U,\qquad m_{ik}=\frac{a_{ik}}{a_{kk}}$$

> ⏳ **Még nincs renderelve** — tervezett fájlnév: `gauss-lu.mp4`.
> A jelenet leírása fent teljes; a Manim-szkript megírása van hátra.

### 8. Gram–Schmidt és QR

$a_2$-ből levonjuk az $a_1$ irányú **vetületét** → merőleges komponens, majd
normálás → $q_2$. Az így kapott $q_1, q_2$ ortonormált; $A = QR$, ahol $R$ felső
háromszög a vetületi együtthatókból.

$$q_k \perp q_j\ (k\neq j),\qquad A = QR$$

> ⏳ **Még nincs renderelve** — tervezett fájlnév: `gram-schmidt-qr.mp4`.
> A jelenet leírása fent teljes; a Manim-szkript megírása van hátra.

### 9. Vektornormák egységgömbjei

A norma „mérete" attól függ, melyiket választjuk: az $\ell_1$ egységgömbje
rombusz, az $\ell_2$-é kör, az $\ell_\infty$-é négyzet. Az **indukált
mátrixnorma** az egységgömb maximális kinyúlása $A$ alatt.

$$\|A\| = \max_{\|x\|=1}\|Ax\|$$

> ⏳ **Még nincs renderelve** — tervezett fájlnév: `norms-unit-balls.mp4`.
> A jelenet leírása fent teljes; a Manim-szkript megírása van hátra.

### 10. Kondíciószám: kör → ellipszis

$A$ az egységkört ellipszissé nyújtja. A **kondíciószám** a leghosszabb és
legrövidebb féltengely aránya ($\sigma_{\max}/\sigma_{\min}$). Rosszul
kondicionált mátrixnál az ellipszis vékony, hosszú — kis bemeneti hiba nagy
kimeneti hibává nyúlik.

$$\operatorname{cond}(A)=\frac{\sigma_{\max}}{\sigma_{\min}}$$

> ⏳ **Még nincs renderelve** — tervezett fájlnév: `condition-number.mp4`.
> A jelenet leírása fent teljes; a Manim-szkript megírása van hátra.

### 11. Fixpont-iteráció konvergenciája

Az $x^{(k+1)} = B x^{(k)} + c$ iteráció a fixponthoz tart, ha a spektrálsugár
$\varrho(B) < 1$ — az iterátumok spirálban közelítenek. Ez a Jacobi / Gauss–Seidel
módszerek konvergenciájának geometriai képe.

$$x^{(k+1)} = B x^{(k)} + c,\qquad \varrho(B) < 1 \Rightarrow \text{konvergencia}$$

> ⏳ **Még nincs renderelve** — tervezett fájlnév: `fixed-point-iteration.mp4`.
> A jelenet leírása fent teljes; a Manim-szkript megírása van hátra.

---

## Kapocs

A vizsga-numerikus jelenetek a megfelelő tételekhez:

- [[concepts/nummodi/lu-felbontas]] — Gauss / LU (7. jelenet)
- [[concepts/nummodi/ldu-felbontas]] — Cholesky elemenkénti előállítás
  (lásd ott a beágyazott animációt)
- [[concepts/nummodi/qr-felbontas]], [[concepts/nummodi/gram-schmidt-ortogonalizacio]] — QR (8. jelenet)
- [[concepts/nummodi/matrixnormak]], [[concepts/nummodi/vektornormak]] — normák (9. jelenet)
- [[concepts/nummodi/kondicioszam]] — kondíciószám (10. jelenet)
- [[concepts/nummodi/jacobi-iteracio]], [[concepts/nummodi/iteracios-modszerek-ler]] — iteráció (11. jelenet)
- [[subjects/nummodi]] — a tárgy áttekintése
- [[concepts/nummodi/ortogonalis-matrixok]] — a 8. jelenet algebrai háttere
