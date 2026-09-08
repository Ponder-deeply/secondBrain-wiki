---
tags: [concept]
sources: [szóbeli-tételjegyzék 1.md]
derivation: source
updated: 2026-08-05
---

# Numerikus módszerek I. — Szóbeli tételjegyzék

A vizsga szóbeli részén kihúzandó tételek listája. Minden tétel **Alap** (elégséges/közepes, 2–3) és **Complex** (jó/jeles, 4–5) részből áll. A b) rész nem helyettesíti az a) részt.

## Lebegőpont, hibaszámítás

### 1. Lebegőpontos számok és tulajdonságaik

- **Alap**: [[concepts/nummodi/lebegopont-modell|lebegőpontos számábrázolás]] modellje, gépi számok definíciója; nevezetes mennyiségek (elemszám, $M_\infty$, $\varepsilon$) kiszámítása; halmaz szemléltetése számegyenesen; két példa a véges ábrázolás furcsaságaira.
- **Complex**: [[concepts/nummodi/lebegopont-modell|input függvény]] fogalma, ábrázolt szám hibájáról szóló tétel, $\varepsilon$ bevezetése és értelmezése.

### 2. Hibaszámítás

- **Alap**: [[concepts/nummodi/hibaszamitas|abszolút/relatív hiba és hibakorlát]] fogalmai; alapműveletek hibakorlátaira vonatkozó állítások; mely műveletek veszélyesek és miért; összeadás és szorzás hibakorlátjának igazolása.
- **Complex**: osztás és függvényérték hibakorlátjára vonatkozó tételek igazolása; függvény adott pontbeli [[concepts/nummodi/hibaszamitas|kondíciószámának]] definíciója.

## Mátrix-felbontások

### 3. A Gauss-elimináció

- **Alap**: [[concepts/nummodi/gauss-eliminacio|GE]] alapötlete [[concepts/nummodi/linearis-egyenletrendszerek|LER]] megoldására, képletek levezetése; további alkalmazások (azonos mátrixú LER-ek, determináns, inverz mátrix).
- **Complex**: visszahelyettesítés algoritmusának levezetése; elimináció és visszahelyettesítés műveletigénye.

### 4. A Gauss-elimináció és az LU-felbontás kapcsolata I.

- **Alap**: [[concepts/nummodi/gauss-eliminacio|GE]] algoritmus; részleges és teljes főelem-kiválasztás; elakadás részleges főelemkiválasztás esetén; miért érdemes teljes főelemkiválasztás.
- **Complex**: [[concepts/nummodi/gauss-eliminacio|GE]] lépései speciális mátrix-szorzásokkal; mátrixok inverzére és szorzatára vonatkozó állítások levezetése; [[concepts/nummodi/lu-felbontas|LU-felbontás]] előállítása.

### 5. A Gauss-elimináció és az LU-felbontás kapcsolata II.

- **Alap**: [[concepts/nummodi/gauss-eliminacio|GE]] algoritmus; szükséges és elégséges feltételek elakadásra/végrehajthatóságra; [[concepts/nummodi/linearis-egyenletrendszerek|LER]] megoldása [[concepts/nummodi/lu-felbontas|LU-felbontással]], előny [[concepts/nummodi/gauss-eliminacio|GE-vel]] szemben.
- **Complex**: $L$ és $U$ [[concepts/nummodi/haromszogmatrixok|háromszögmátrixokkal]] történő [[concepts/nummodi/linearis-egyenletrendszerek|LER]] megoldás képletei és műveletigénye.

### 6. Az LU-felbontás direkt módon

- **Alap**: [[concepts/nummodi/lu-felbontas|LU-felbontás]] definíciója; $L$ és $U$ elemenkénti meghatározása, képletek levezetése; sorrend, műveletigény.
- **Complex**: [[concepts/nummodi/lu-felbontas|LU-felbontás]] létezésére és egyértelműségére (főminorokkal) vonatkozó tétel igazolása.

### 7. A Schur-komplementer

- **Alap**: [[concepts/nummodi/schur-komplementer|Schur-komplementer]] definíciója; [[concepts/nummodi/gauss-eliminacio|GE]] megmaradási tételei és kapcsolódó fogalmak; determináns megmaradásának bizonyítása.
- **Complex**: szimmetria és pozitív definitás megmaradásának igazolása.

### 8. LDU-felbontás

- **Alap**: [[concepts/nummodi/ldu-felbontas|LDU]] fogalma, előállítása [[concepts/nummodi/lu-felbontas|LU-ból]]; elemenkénti [[concepts/nummodi/ldu-felbontas|LDU-algoritmus]], képletek levezetése, műveletigény.
- **Complex**: szimmetrikus mátrix felbontásának tétele; [[concepts/nummodi/ldu-felbontas|LDU]] vs. Cholesky alkalmazhatóság.

### 9. A Cholesky-féle $LL^T$-felbontás

- **Alap**: Cholesky-felbontás definíciója; elemenkénti algoritmus, képletek, művelet- és tárigény.
- **Complex**: Cholesky-felbontás létezése és egyértelműsége; $LDL^T$ vs. Cholesky alkalmazhatóság.

### 10. A QR-felbontás Gram–Schmidt ortogonalizációval

- **Alap**: [[concepts/nummodi/qr-felbontas|QR-felbontás]] definíciója; [[concepts/nummodi/gram-schmidt-ortogonalizacio|Gram–Schmidt]] levezetés; elakadásmentesség feltétele; [[concepts/nummodi/ortogonalis-matrixok|ortogonális mátrixok]] szorzatára vonatkozó tétel.
- **Complex**: [[concepts/nummodi/qr-felbontas|QR]] egyértelműségének tétele; [[concepts/nummodi/qr-felbontas|QR]] vs. [[concepts/nummodi/lu-felbontas|LU-alapú]] [[concepts/nummodi/linearis-egyenletrendszerek|LER]] megoldás (műveletigény, alkalmazhatóság).

### 24. ILU algoritmus

- **Alap**: részleges [[concepts/nummodi/lu-felbontas|LU-felbontás]] definíciója és előállító algoritmusa; elégséges feltétel létezésre/egyértelműségre; algoritmus helyességének bizonyítása.
- **Complex**: ILU levezetése; reziduumvektoros alak; nevezetes példák speciális esetekként.

## Householder

### 11. A Householder-transzformáció I.

- **Alap**: [[concepts/nummodi/householder-transzformacio|Householder-transzformáció]] definíciója, geometriai tartalma, elemi tulajdonságok levezetése; alkalmazás vektorra és mátrixra (mindkét irányból), műveletigények.
- **Complex**: azonos hosszúságú $a, b$ vektorokhoz $H$ meghatározása ($Ha = b$); tetszőleges vektor $\sigma e$ alakra hozása, $\sigma$ megválasztásának indoklása.

### 12. A Householder-transzformáció II.

- **Alap**: [[concepts/nummodi/householder-transzformacio|Householder]] definíció, geometriai tartalom, elemi tulajdonságok (biz. nélkül); alkalmazás vektorra/mátrixra, műveletigény; alkalmazás [[concepts/nummodi/linearis-egyenletrendszerek|LER]] megoldására.
- **Complex**: [[concepts/nummodi/householder-transzformacio|Householder]] [[concepts/nummodi/qr-felbontas|QR-felbontásra]]; összevetés [[concepts/nummodi/gram-schmidt-ortogonalizacio|Gram–Schmidt-tel]] műveletigény és [[concepts/nummodi/algoritmus-stabilitas|numerikus stabilitás]] szempontjából.

## Mátrixnorma

### 13. Mátrixnormák és tulajdonságaik I.

- **Alap**: vektornorma, mátrixnorma, indukált mátrixnorma definíciói; indukált mátrixnorma teljesíti a mátrixnorma-tulajdonságokat; $1$-es, $2$-es, $\infty$ mátrixnormák.
- **Complex**: tetszőleges norma és spektrálsugár közti egyenlőtlenség igazolása; $1$-es vektornorma által indukált mátrixnorma képletének igazolása.

### 14. Mátrixnormák és tulajdonságaik II.

- **Alap**: mátrixnorma és indukált mátrixnorma definíciói; illeszkedés fogalma; indukált norma mindig illeszkedik; $\infty$ által indukált mátrixnorma képletének igazolása.
- **Complex**: $2$-es vektornorma által indukált mátrixnorma képlete; normális mátrix $2$-es normája; [[concepts/nummodi/ortogonalis-matrixok|ortogonális mátrix]] $2$-es normája.

### 15. Frobenius mátrixnorma, illeszkedés

- **Alap**: Frobenius-norma képlete (biz. nélkül); nem indukált norma; illeszkedés fogalma; indukált norma illeszkedése.
- **Complex**: Frobenius-norma sajátértékekkel való kifejezése; ezt felhasználva olyan vektornorma, amelyhez Frobenius illeszkedik.

## Iterációs módszerek

### 16. LER érzékenysége I.

- **Alap**: [[concepts/nummodi/linearis-egyenletrendszerek|LER]] jobboldalának perturbációja; megoldás megváltozásának mértékére vonatkozó tételek (biz. nélkül); [[concepts/nummodi/hibaszamitas|kondíciószám]] definíciója és tulajdonságai.
- **Complex**: jobboldal megváltozásáról szóló tétel bizonyítása; [[concepts/nummodi/hibaszamitas|kondíciószám]] változása [[concepts/nummodi/lu-felbontas|LU]], [[concepts/nummodi/qr-felbontas|QR]] szorzatfelbontásnál.

### 17. LER érzékenysége II.

- **Alap**: [[concepts/nummodi/linearis-egyenletrendszerek|LER]] mátrixának perturbációja; megoldás megváltozásának tételei (biz. nélkül); [[concepts/nummodi/hibaszamitas|kondíciószám]] definíciója és tulajdonságai.
- **Complex**: mátrix megváltozására vonatkozó tétel és a felhasznált lemma bizonyítása.

### 18. Iterációs módszerek konvergenciája

- **Alap**: iterációs alapötlet, összevetés direkt módszerekkel; kontrakció $\mathbb{R}^n$-en; konvergencia elégséges feltétele; szükséges és elégséges feltétele.
- **Complex**: Banach-féle fixponttétel ismertetése és bizonyítása.

### 19. A Jacobi-iteráció

- **Alap**: mátrixos és koordinátás alak levezetése; reziduumvektoros alak és szerepe.
- **Complex**: Jacobi-iteráció konvergenciatételének igazolása.

### 20. A csillapított Jacobi-iteráció

- **Alap**: mátrixos és koordinátás alak levezetése; reziduumvektoros alak és szerepe.
- **Complex**: csillapított Jacobi konvergenciatételének igazolása.

### 21. A Gauss–Seidel-iteráció

- **Alap**: vektoros és koordinátás alak levezetése; reziduumvektoros alak és szerepe.
- **Complex**: relaxációs módszer konvergenciájának szükséges feltételének bizonyítása.

### 22. A Gauss–Seidel relaxációs módszer

- **Alap**: relaxált változat vektoros és koordinátás alakja; reziduumvektoros alak és szerepe.
- **Complex**: relaxációs módszer konvergenciájának szükséges feltétele; Jacobi és Gauss–Seidel összevetése; speciális mátrixosztályokra tanult tételek (biz. nélkül).

### 23. A Richardson-típusú iterációk

- **Alap**: képlet levezetése; reziduumvektoros alak és jelentősége; konvergenciatétel megfogalmazása (biz. nélkül).
- **Complex**: konvergenciatétel igazolása.

## Nemlineáris egyenletek

### 25. Nemlineáris egyenletek megoldása I.

- **Alap**: feladat ismertetése; megoldás létezéséhez Bolzano-tétel (biz. nélkül), Brouwer-féle fixpont-tétel igazolása, kontrakció $[a;b]$-n és Banach-féle fixpont-tétel (biz. nélkül).
- **Complex**: kontrakció elégséges feltételének igazolása; konvergenciarend fogalma és tulajdonságai; magasabb rendű konvergencia tétele fixpont-iterációkra.

### 26. Nemlineáris egyenletek megoldása II.

- **Alap**: húrmódszer és szelőmódszer alapötlete, működés szemléltetése, képletek levezetése; konvergenciarend; két módszer összehasonlítása egymással és Newton-módszerrel.
- **Complex**: Newton-módszer alapötlete; lokális konvergenciatételének igazolása.

### 27. Nemlineáris egyenletek megoldása III.

- **Alap**: intervallumfelezés algoritmusa és hibabecslés; Newton-módszer alapötlete, szemléltetés és képlet levezetése; többváltozós Newton-módszer levezetése.
- **Complex**: Newton-módszer monoton konvergenciájának igazolása.

### 28. Polinomok gyökeinek becslése, helyettesítési és derivált értékek

- **Alap**: polinom gyökeinek elhelyezkedésére vonatkozó becslés és bizonyítása.
- **Complex**: Horner-algoritmus levezetése helyettesítési érték kiszámítására; algoritmus előnyei; alkalmazás polinom deriváltjainak helyettesítési értékeire.

## Kapocs

- [[subjects/nummodi]] — kurzus áttekintése, tematika, irodalom
- [[concepts/nummodi/lebegopont-modell]], [[concepts/nummodi/hibaszamitas|hibaszamitas]]
- [[concepts/nummodi/gauss-eliminacio]], [[concepts/nummodi/lu-felbontas|lu-felbontas]], [[concepts/nummodi/ldu-felbontas|ldu-felbontas]], [[concepts/nummodi/schur-komplementer|schur-komplementer]]
- [[concepts/nummodi/qr-felbontas]], [[concepts/nummodi/gram-schmidt-ortogonalizacio|gram-schmidt-ortogonalizacio]], [[concepts/nummodi/householder-transzformacio|householder-transzformacio]], [[concepts/nummodi/ortogonalis-matrixok|ortogonalis-matrixok]]
- [[concepts/nummodi/haromszogmatrixok]], [[concepts/nummodi/linearis-egyenletrendszerek|linearis-egyenletrendszerek]], [[concepts/nummodi/algoritmus-stabilitas|algoritmus-stabilitas]], [[concepts/nummodi/progonka-modszer|progonka-modszer]]
