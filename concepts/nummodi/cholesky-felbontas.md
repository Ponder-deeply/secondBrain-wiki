---
tags: [concept]
sources: [NM1_ea04.pdf]
derivation: source
kind: procedure
element: water
updated: 2026-10-21
---

# Cholesky-felbontás ($LL^\top$-felbontás)

Szimmetrikus, pozitív definit mátrix egyértelműen felírható $A = LL^\top$ alakban, ahol $L$ pozitív átlójú alsó háromszögmátrix. Elemei közvetlen képletekkel számolhatók $\tfrac13 n^3 + \mathcal{O}(n^2)$ szorzással/osztással és $n$ gyökvonással; csak $L$-et kell tárolni.

## Tartalom

### Definíció

Az $A \in \mathbb{R}^{n\times n}$ szimmetrikus mátrix **Cholesky-felbontásának** (avagy $LL^\top$-felbontásának) nevezzük az $L \cdot L^\top$ szorzatot, ha

$$A = LL^\top, \qquad L \in \mathbb{R}^{n\times n} \text{ alsó háromszögmátrix}, \qquad l_{ii} > 0 \ (i = 1,\dots,n).$$

### Tétel — létezés és egyértelműség

**Tétel.** Ha $A$ szimmetrikus és pozitív definit, akkor egyértelműen létezik Cholesky-felbontása.

**Egyértelműség (indirekt).** Tegyük fel, hogy két különböző felbontás van: $A = L_1L_1^\top = L_2L_2^\top$, ahol $L_1, L_2 \in \mathcal{L}$ pozitív átlóval. Legyen $D_1 = \operatorname{diag}((L_1)_{ii})$, $D_2 = \operatorname{diag}((L_2)_{ii})$. Ekkor

$$\underbrace{(L_1D_1^{-1})}_{\in \mathcal{L}_1}\cdot\underbrace{(D_1L_1^\top)}_{\in\mathcal{U}} = \underbrace{(L_2D_2^{-1})}_{\in\mathcal{L}_1}\cdot\underbrace{(D_2L_2^\top)}_{\in\mathcal{U}}.$$

Mindkét oldal egy-egy [[concepts/nummodi/lu-felbontas|LU-felbontás]]. Az LU-felbontás egyértelmű (a főminorok nem nullák), ezért $D_1L_1^\top = D_2L_2^\top$. A főátlók egyezéséből $(L_1)_{ii}^2 = (L_2)_{ii}^2$ minden $i$-re, a pozitivitás miatt $(L_1)_{ii} = (L_2)_{ii}$, tehát $D_1 = D_2$ és így $L_1 = L_2$. Ellentmondás. $\square$

**Létezés.** Mivel $A$ szimmetrikus és pozitív definit, minden főminora pozitív: $\det(A_k) > 0$ ($k = 1,\dots,n$). Ebből létezik (egyértelmű) $A = \widetilde L\widetilde U$ LU-felbontás, és $\widetilde u_{ii} > 0$ minden $i$-re (a főminorok hányadosai). Legyen $D = \operatorname{diag}(\sqrt{\widetilde u_{11}},\dots,\sqrt{\widetilde u_{nn}})$, és

$$A = \underbrace{(\widetilde L D)}_{B}\cdot\underbrace{(D^{-1}\widetilde U)}_{C}.$$

Itt $B \in \mathcal{L}$, $C \in \mathcal{U}$, és mindkettő átlója a $\sqrt{\widetilde u_{ii}}$ elemekből áll. Be kell látni, hogy $C^\top = B$. A szimmetria miatt $BC = A = A^\top = C^\top B^\top$. Balról $B^{-1}$-gyel, jobbról $(B^\top)^{-1}$-gyel szorozva:

$$\underbrace{C(B^\top)^{-1}}_{\in\,\mathcal{U}_1} = \underbrace{B^{-1}C^\top}_{\in\,\mathcal{L}_1}.$$

(A két szorzat átlója $1$, mert $B$ és $C$ átlója megegyezik.) Egy mátrix, amely egyszerre egységátlójú felső és alsó háromszögmátrix, csak $I$ lehet: $B^{-1}C^\top = I$, azaz $C^\top = B$. Így $A = BB^\top$, és $L := B$ pozitív átlójú. $\square$

### A közvetlen (elemenkénti) algoritmus

**Tétel.** Az $L$ elemei az $A$ alsó háromszögbeli elemeiből:

$$i = j \ (\text{átló}):\quad l_{jj} = \sqrt{a_{jj} - \sum_{k=1}^{j-1} l_{jk}^2}, \qquad i > j \ (\text{alsó}):\quad l_{ij} = \frac{1}{l_{jj}}\Bigl(a_{ij} - \sum_{k=1}^{j-1} l_{ik}l_{jk}\Bigr).$$

**Levezetés.** Írjuk fel $A = LL^\top$ $(i,j)$ elemét, kihasználva, hogy $k > j$ esetén $l_{jk} = 0$ és $(L^\top)_{kj} = l_{jk}$:

- $i = j$: $\displaystyle a_{jj} = \sum_{k=1}^{n} l_{jk}(L^\top)_{kj} = \sum_{k=1}^{j} l_{jk}^2 = l_{jj}^2 + \sum_{k=1}^{j-1} l_{jk}^2$, ebből $l_{jj}$ kifejezhető.
- $i > j$: $\displaystyle a_{ij} = \sum_{k=1}^{j} l_{ik}l_{jk} = l_{ij}l_{jj} + \sum_{k=1}^{j-1} l_{ik}l_{jk}$, és ha $l_{jj} \neq 0$, ebből $l_{ij}$ kifejezhető.

Ha az $(i,j)$ indexeken „jó sorrendben” megyünk végig (pl. oszlopfolytonosan, mint az [[concepts/nummodi/lu-felbontas|LU-felbontásnál]]), a jobb oldalon minden mennyiség már ismert.

### Műveletigény és tárigény

**Tétel.** A Cholesky-felbontás előállításához $\tfrac13 n^3 + \mathcal{O}(n^2)$ szorzás/osztás (és ugyanennyi nagyságrendű összeadás), valamint $n$ négyzetgyökvonás szükséges.

**Biz.** Rögzített $j$-re $l_{jj}$-hez $2(j-1)$ művelet (szorzás és összeadás) kell; rögzített $i > j$-re $l_{ij}$-hez $1$ osztás, $j-1$ szorzás és $j-1$ összeadás, összesen $2j-1$. Összegezve:

$$\sum_{j=1}^n 2(j-1) + \sum_{i=2}^n\sum_{j=1}^{i-1}(2j-1) = \sum_{s=1}^{n-1}2s + \sum_{i=2}^n (i-1)^2 = 2\cdot\frac{(n-1)n}{2} + \frac{(n-1)n(2n-1)}{6} = \frac13 n^3 + \mathcal{O}(n^2). \ \square$$

**Tárigény:** csak $L$ alsó háromszögét kell tárolni, $\tfrac{n(n+1)}{2}$ elem — feleannyi, mint az LU-nál; az $A$ alsó háromszögét felül is írhatja.

### Egyéb előállítási módok

1. **LU-ból LDU-n át:** $A = \widetilde L\widetilde U$; pozitív definit $A$-ra $\widetilde u_{ii} > 0$ (ebből látszik, elkészíthető-e a felbontás). $\sqrt D := \operatorname{diag}(\sqrt{\widetilde u_{ii}})$ mellett $A = (\widetilde L\sqrt D)(\sqrt D\widetilde L^\top) = LL^\top$. Az $LDL^\top$-t nem kell külön előállítani.
2. **„Mechanikusan” GE-vel:** $a_{11}$ helyére $\sqrt{a_{11}}$-et írunk, az 1. oszlopot végigosztjuk $\sqrt{a_{11}}$-gyel, a maradék $(n-1)\times(n-1)$-es részen eliminálunk, és így tovább; a végén csak az alsó háromszöget olvassuk le. Az utolsó átlóelemből is gyököt kell vonni.

**Példa.** $A = \begin{bmatrix}4&2&4\\2&10&5\\4&5&6\end{bmatrix}$: a GE-ből $\widetilde U$ átlója $4, 9, 1$, így

$$L = \begin{bmatrix}2&0&0\\1&3&0\\2&1&1\end{bmatrix}, \qquad LL^\top = \begin{bmatrix}4&2&4\\2&10&5\\4&5&6\end{bmatrix}.$$

### Alkalmazás LER-re

Ha $A$ szimmetrikus, pozitív definit és $A = LL^\top$, akkor $Ax = L\underbrace{L^\top x}_{y} = b$ helyett:

1. $Ly = b$ alsó háromszögű LER ($n^2 + \mathcal{O}(n)$),
2. $L^\top x = y$ felső háromszögű LER ($n^2 + \mathcal{O}(n)$).

Előnyös, ha sok jobb oldalra kell megoldani ugyanazzal az $A$-val.

### $LDL^\top$ és Cholesky összevetése

| | $LDL^\top$ | $LL^\top$ (Cholesky) |
|---|---|---|
| Feltétel | $A$ szimmetrikus, főminorai nem nullák | $A$ szimmetrikus **és pozitív definit** |
| Gyökvonás | nincs | $n$ darab |
| Műveletigény | $\tfrac13 n^3 + \mathcal{O}(n^2)$ | $\tfrac13 n^3 + \mathcal{O}(n^2)$ |
| Tárolás | $L$ alsó része + $D$ átlója | $L$ alsó háromszöge |

Az [[concepts/nummodi/ldu-felbontas|$LDL^\top$-felbontás]] tehát tágabb mátrixosztályon (indefinit szimmetrikus mátrixokon is) működik, gyökvonás nélkül. A Cholesky csak pozitív definit mátrixra alkalmazható, cserébe egyetlen háromszögmátrixot ad, és elvégezhetősége (minden gyök alatti kifejezés pozitív) egyben a pozitív definitség tesztje.

### Vizsgán (9. tétel)

- **a)** definíció; a közvetlen képletek levezetése $A = LL^\top$ elemeiből; műveletigény ($\tfrac13n^3$ + $n$ gyökvonás) kiszámolva, tárigény.
- **b)** létezés és egyértelműség bizonyítása (fenti két bizonyítás); $LDL^\top$ vs. Cholesky alkalmazhatósága.

## Kapocs

- [[concepts/nummodi/ldu-felbontas]] — az $LDL^\top$-felbontás, amelyből $\sqrt D$-vel a Cholesky adódik (8. tétel)
- [[concepts/nummodi/lu-felbontas]] — létezés főminorokkal és egyértelműség; mindkét bizonyítás erre épül
- [[concepts/nummodi/schur-komplementer]] — a pozitív definitség megmarad a GE során
- [[concepts/nummodi/haromszogmatrixok]] — $\mathcal{L}$, $\mathcal{L}_1$, $\mathcal{U}_1$ zártsága, amit az $I$-vel való egyezés használ
- [[concepts/nummodi/kondicioszam]] — a Cholesky-felbontás nem rontja a kondíciót
