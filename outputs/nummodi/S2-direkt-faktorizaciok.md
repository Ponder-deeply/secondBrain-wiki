---
tags: [synthesis]
sources: [tetel-03-gauss-eliminacio.md, tetel-04-lu-kapcsolat-1.md, tetel-05-lu-kapcsolat-2.md, tetel-06-lu-direkt.md, tetel-07-schur-komplementer.md, tetel-08-ldu-felbontas.md, tetel-09-cholesky.md, tetel-10-qr-gram-schmidt.md, tetel-11-householder-1.md, tetel-12-householder-2.md]
updated: 2026-06-09
---

# S2 – Direkt faktorizációk

A 03–12 tételek mind **ugyanazt az egy receptet** variálják: bontsd fel az $A$ mátrixot két "egyszerű" (háromszög vagy ortogonális) mátrix szorzatára, majd az $Ax=b$-t oldd meg olcsó helyettesítésekkel. A tételek közötti különbség mindössze annyi, hogy *milyen szorzótényezőkkel* nullázzuk ki az átló alatti részt, és *milyen struktúrát* (szimmetria, pozitív definitség) használunk ki a munka csökkentésére.

## A közös recept

### A váz: faktorizálj → helyettesíts

Minden direkt módszer két fázisra esik:

1. **Faktorizáció** – $A$-t balról szorozzuk elemi *eliminációs* (alsó háromszög) vagy *ortogonális* (tükröző) mátrixokkal, amíg felső háromszög $U$ (ill. $R$) nem lesz. Ez a drága, $O(n^3)$ fázis, de **csak $A$-tól függ** → egyszer kell, sok jobboldalhoz újrahasznosítható.
2. **Helyettesítés** – a kapott háromszögrendszer(eke)t megoldjuk, fejenként $O(n^2)$ művelettel:
$$Ax=b \;\Longleftrightarrow\; \begin{cases} Ly=b & \text{(előrehelyettesítés)} \\ Ux=y & \text{(visszahelyettesítés)}\end{cases}$$

**Üzenet (LU vs. ismételt GE):** ha $m$ darab jobboldalunk van ugyanahhoz az $A$-hoz, a faktorizáció $\tfrac{2}{3}n^3$-ja **egyszer** szerepel, és csak $m\cdot 2n^2$ adódik hozzá; az elimináció minden $b$-re való újrafuttatása viszont $m\cdot\tfrac{2}{3}n^3$. Megtakarítás $\sim (m-1)\tfrac{2}{3}n^3$.

### A két ág

| Ág | Szorzótényezők | Eredmény | Mit használ ki |
|---|---|---|---|
| **Háromszög (Gauss/LU-család)** | egységalsó-háromszög eliminációs mátrixok | $A=LU$ (ill. $LDU$, $LL^T$) | szimmetria, poz. definitség → kevesebb munka |
| **Ortogonális (QR-család)** | $Q$ ortogonális (Gram–Schmidt / Householder) | $A=QR$ | numerikus stabilitás → több munka |

A háromszög ág **olcsóbb**, de pivotálni kell (numerikus stabilitás). Az ortogonális ág **drágább**, de $\kappa(Q)=1$ miatt a hibafelerősödés minimális.

### Műveletigény-skála

| Módszer | Vezető tag | Mit nyer |
|---|---|---|
| LU / Gauss-elimináció | $\tfrac{2}{3}n^3$ | alapeset (általános $A$) |
| **Cholesky** $LL^T$ (SPD) | $\tfrac{1}{3}n^3$ | **fele** — szimmetria + poz. def. |
| $LDL^T$ (szimmetrikus) | $\tfrac{1}{3}n^3$ | fele — csak $L,D$ tárol/számol |
| QR – Gram–Schmidt | $2n^3$ | ortogonalitás (de instabilabb) |
| Householder-LER | $\tfrac{4}{3}n^3$ | stabil $QR$, $Q$ nem épül fel |
| Householder-QR (teljes $Q$) | $\tfrac{8}{3}n^3$ | explicit $Q$, legstabilabb |

**Tendencia:** több *struktúra* (szimmetria, poz. definitség) → kevesebb munka; több *stabilitás* (ortogonalitás) → több munka.

### Az egyértelműség-trükk

A felbontások egyértelműségének közös fogása:

> **Ha egy mátrix egyszerre alsó és felső háromszög, akkor diagonális; ha ráadásul egységátlójú, akkor $=I$.**

Ezt a trükköt alkalmazza a 08-as tétel az $U=L^T$ levezetésében: $A=A^T$-ből $LDU=U^TDL^T$, és $L^{-1},(L^T)^{-1}$-vel átrendezve egy felső háromszög $=$ egy alsó háromszög adódik, ami csak diagonális lehet → kiesik, hogy $U=L^T$. Ugyanez a "kétoldali háromszög $\Rightarrow$ diagonális" gondolat adja az LU egyértelműségét és bukkan fel mindenhol, ahol egy egységnormált felbontás egyetlen alakját kell igazolni.

## Tétel-delták

Mi az *egyetlen új dolog*, amit az adott tétel a vázhoz tesz hozzá:

| Tétel                      | Delta (az egyetlen új motívum)                                                                                                                                                                         |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **03 – GE**                | Maga az eliminációs lépés: $m_{ik}=a_{ik}^{(k-1)}/a_{kk}^{(k-1)}$, pivot $\neq 0$ feltétel $\Leftrightarrow$ főminorok $D_k\neq 0$. Determináns = pivotok szorzata, inverz = $n$ jobboldal.            |
| **04 – Főelemkiválasztás** | Elakadás ($a_{kk}^{(k-1)}=0$) kezelése: **részleges** (sorcsere, max oszlopelem, $\|l_{ik}\|\le 1$) és **teljes** (sor+oszlopcsere) pivot. *Nemszinguláris $\Rightarrow$ részleges pivot nem akad el.* |
| **05 – GE⟺LU**             | A híd: GE végrehajtható (cserék nélkül) $\Leftrightarrow$ $D_k\neq 0$ ($k<n$), és **$u_{kk}=D_k/D_{k-1}$**. Az LU egyszeri felbontás $m$ jobboldalra hatalmas megtakarítás.                            |
| **06 – Doolittle**         | $L,U$ **direktben**, GE nélkül: elemenkénti rekurzív képletek az $a_{ij}=\sum l_{ik}u_{kj}$-ből. Ugyanaz a $\tfrac{2}{3}n^3$.                                                                          |
| **07 – Schur**             | Blokk-GE egy lépésben: $S=A_{22}-A_{21}A_{11}^{-1}A_{12}$. **$\det A=\det A_{11}\cdot\det S$**, és öröklődés: szimmetria, poz. def., SDD, sávszélesség, profil.                                        |
| **08 – LDU**               | Az átló kiemelése: $A=LDU$ két egységháromszöggel, $D=$ pivotok. Szimmetrikusra **$U=L^T$ ⟹ $LDL^T$**, $\tfrac{1}{3}n^3$.                                                                              |
| **09 – Cholesky**          | SPD-re a "fél-felbontás": $A=LL^T$, $l_{kk}=\sqrt{\dots}$ (a gyök a poz. def. miatt értelmes). $\tfrac{1}{3}n^3 + n$ gyökvonás, egyértelmű.                                                            |
| **10 – Gram–Schmidt**      | Átváltás az ortogonális ágra: $A=QR$, $Q^TQ=I$. **Megakad $\Leftrightarrow$ oszlopok lin. függők.** $2n^3$.                                                                                            |
| **11 – Householder I.**    | A tükrözés mint elemi szorzó: $H(v)=I-2vv^T$ **szimmetrikus + ortogonális + involutív** ($H^2=I$). $\sigma=-\operatorname{sgn}(a_1)\|a\|$ a jegyvesztés ellen.                                         |
| **12 – Householder II.**   | A reflexiók sorozata felbontássá: $n-1$ tükrözés $\Rightarrow R$. LER $\tfrac{4}{3}n^3$ ($Q$ nem épül fel), teljes $QR$ $\tfrac{8}{3}n^3$.                                                             |

## Felmondható tételmondatok

A vizsgán *pontosan kimondandó* állítások (bizonyítás nélkül):

- **GE elvégezhetőség (03/05):** A GE (sor- és oszlopcsere nélkül) akkor és csak akkor hajtható végre, ha minden vezető főminor $D_k\neq 0$ ($k=1,\dots,n-1$). Ekkor létezik az $A=LU$ felbontás.
- **Pivot-formula (05):** A pivotokra $u_{kk}=a_{kk}^{(k-1)}=\dfrac{D_k}{D_{k-1}}$ ($D_0:=1$). Speciálisan $D_k=u_{11}\cdots u_{kk}$.
- **Pivotálás (04):** Ha $A$ nemszinguláris ($\det A\neq 0$), akkor a részleges főelemkiválasztással végzett GE **nem akad el**. Részleges pivotnál $|l_{ik}|\le 1$.
- **Doolittle-képletek (06):** $\displaystyle u_{kj}=a_{kj}-\sum_{s=1}^{k-1}l_{ks}u_{sj}\;(j\ge k)$, valamint $\displaystyle l_{ik}=\frac{1}{u_{kk}}\Big(a_{ik}-\sum_{s=1}^{k-1}l_{is}u_{sk}\Big)\;(i>k)$.
- **Schur det-tétel (07):** $\det A=\det A_{11}\cdot\det S$, ahol $S=A_{22}-A_{21}A_{11}^{-1}A_{12}$. **Öröklődés:** ha $A$ szimmetrikus / poz. definit / szig. diag. domináns, akkor $S$ is az; $S$ fél sávszélessége $\le A$-é.
- **LDU szimmetrikus eset (08):** Ha $A=A^T$, akkor az LDU-felbontásban szükségszerűen $U=L^T$, azaz $A=LDL^T$.
- **Cholesky (09):** Ha $A$ szimmetrikus pozitív definit, akkor **egyértelműen** létezik az $A=LL^T$ felbontás $l_{ii}>0$ pozitív főátlóval.
- **Householder $H$ (11):** $H(v)=I-2vv^T$ ($\|v\|_2=1$) szimmetrikus ($H^T=H$), ortogonális ($H^TH=I$) és involutív ($H^2=I$, tehát $H^{-1}=H$).
- **Gram–Schmidt megakadás (10):** A Gram–Schmidt-eljárás **nem akad el $\Leftrightarrow$ $A$ oszlopai lineárisan függetlenek** ($\det A\neq 0$). Két ortogonális mátrix szorzata ortogonális ($O(n)$ csoport).

## Bizonyítás-magok

A nemtriviális levezetések 2–4 soros csontváza:

**GE eliminációs képlet (03).** A multiplikátor a kinullázás követelményéből esik ki: $E_i\leftarrow E_i-m_{ik}E_k$ után megköveteljük $a_{ik}^{(k-1)}-m_{ik}a_{kk}^{(k-1)}=0\Rightarrow m_{ik}=a_{ik}^{(k-1)}/a_{kk}^{(k-1)}$. A frissítés $a_{ij}^{(k)}=a_{ij}^{(k-1)}-m_{ik}a_{kj}^{(k-1)}$.

**$D_k=u_{11}\cdots u_{kk}$ (03/05).** A sorművelet ($E_i\leftarrow E_i-m_{ik}E_k$, $i>k$) nem változtatja a bal felső $k\times k$-as determinánst → $D_k$ a felhozott háromszög átlóelemeinek szorzata. Rekurzívan $D_k=D_{k-1}\cdot a_{kk}^{(k-1)}$, így $u_{kk}=D_k/D_{k-1}$. (LU-ból: $\det A_k=\det L_k\det U_k=1\cdot u_{11}\cdots u_{kk}$.)

**Részleges pivot nem akad el (04).** *Állítás:* ha $A$ nemszinguláris, a részleges főelemkiválasztással végzett GE nem akad el. *Indirekt bizonyítás.* Tegyük fel, az első $k-1$ lépés kész, és a $k$-adik lépésben indirekt $a_{ik}^{(k-1)}=0$ minden $i=k,\dots,n$-re (azaz nincs nemnulla pivot). A GE sorműveletei ($E_i\leftarrow E_i-l_{ik}E_k$) a determinánst nem változtatják, egy sorcsere csak előjelet vált, így
$$\det(A^{(k-1)})=\pm\det(A)\neq0.$$
Viszont ha a $k$-adik oszlop $k$-tól lefelé csupa nulla, akkor $A^{(k-1)}$ bal felső $k\times k$-as blokkjának utolsó oszlopa csak az első $k-1$ pozícióban lehet nemnulla, így a már háromszöggé alakított rész $k$-adik átlóeleme $0$ → a felső háromszög alak átlójában nulla áll → $\det(A^{(k-1)})=0$, ellentmondás. Tehát van nemnulla $a_{ik}^{(k-1)}$ ($i\ge k$); a részleges kiválasztás éppen az abszolút értékben maximálisat hozza pivotnak, a lépés elvégezhető. Mivel $k$ tetszőleges, az elimináció végigvihető. Ráadásul a pivot a $k$-adik oszlop legnagyobb abszolút értékű eleme, így $|l_{ik}|=|a_{ik}^{(k-1)}/a_{kk}^{(k-1)}|\le1$. $\square$

**Schur $\det A=\det A_{11}\det S$ (07).** Blokk-GE: $E=\begin{bmatrix}I&0\\-A_{21}A_{11}^{-1}&I\end{bmatrix}$, $\det E=1$. Ekkor $EA=\begin{bmatrix}A_{11}&A_{12}\\0&S\end{bmatrix}$ felső blokk-háromszög, melynek determinánsa $\det A_{11}\cdot\det S$, és $\det(EA)=\det A$.

**Schur szimmetria + poz. definitség öröklődése (07).** *Szimmetria.* $A=A^\top$-ból $A_{11}^\top=A_{11}$, $A_{22}^\top=A_{22}$, $A_{21}^\top=A_{12}$. Mivel $(A_{11}^{-1})^\top=(A_{11}^\top)^{-1}=A_{11}^{-1}$:
$$S^\top=(A_{22}-A_{21}A_{11}^{-1}A_{12})^\top=A_{22}^\top-A_{12}^\top(A_{11}^{-1})^\top A_{21}^\top=A_{22}-A_{21}A_{11}^{-1}A_{12}=S.$$
*Pozitív definitség (kulcstrükk).* Legyen $x_2\neq0$ tetszőleges, és válasszuk $x_1:=-A_{11}^{-1}A_{12}x_2$-t, $x=\begin{bmatrix}x_1\\x_2\end{bmatrix}\neq0$. Ez a választás kinullázza az első blokksort: $A_{11}x_1+A_{12}x_2=0$. Ekkor $A$ poz. definitsége miatt
$$0<\langle Ax,x\rangle=\underbrace{\langle A_{11}x_1+A_{12}x_2,x_1\rangle}_{=0}+\langle A_{21}x_1+A_{22}x_2,x_2\rangle=\langle(A_{22}-A_{21}A_{11}^{-1}A_{12})x_2,x_2\rangle=\langle Sx_2,x_2\rangle,$$
ahol $A_{21}x_1=-A_{21}A_{11}^{-1}A_{12}x_2$. Mivel ez minden $x_2\neq0$-ra teljesül, $S$ pozitív definit. $\square$

**LDU $U=L^T$ (08).** $A=A^T$-ből $LDU=U^TDL^T$. Bal $L^{-1}$, jobb $(L^T)^{-1}$ szorzás: $DU(L^T)^{-1}=L^{-1}U^TD$. A bal oldal felső, a jobb alsó háromszög → közös értékük **diagonális**; a főátló $=D$, így $DU(L^T)^{-1}=D$, ahonnan $U(L^T)^{-1}=I$, azaz $U=L^T$.

**Cholesky $l_{kk},l_{ik}$ (09).** Az $a_{ik}=\sum_{j=1}^{\min(i,k)}l_{ij}l_{kj}$-ből. Átlóra: $a_{kk}=\sum_{j<k}l_{kj}^2+l_{kk}^2\Rightarrow l_{kk}=\sqrt{a_{kk}-\sum_{j<k}l_{kj}^2}$ (a gyök alatt $>0$ a poz. def. miatt). Átló alatt: $l_{ik}=\frac{1}{l_{kk}}\big(a_{ik}-\sum_{j<k}l_{ij}l_{kj}\big)$.

**Householder $H^2=I$ (11).** $(I-2vv^T)^2=I-4vv^T+4(vv^T)(vv^T)$, és $(vv^T)(vv^T)=v(v^Tv)v^T=vv^T$ mert $v^Tv=1$. Így $H^2=I-4vv^T+4vv^T=I$. ($H^T=H$ miatt ez egyben $H^TH=I$.)

**Householder-LER teljes levezetése (12).** *Faktorizáció.* Alkalmazzunk $n-1$ Householder-reflexiót $H_1,\dots,H_{n-1}$ sorban, ahol a $k$-adik az aktuális mátrix $k$-adik oszlopának $k$ alatti elemeit nullázza ki ($v_k$ első $k-1$ komponense $0$, így $H_k$ a bal felső $I_{k-1}$ blokkot rögzíti). $n-1$ lépés után
$$H_{n-1}\cdots H_2H_1\,A=R\quad(\text{felső háromszög}).$$
Legyen $Q:=H_1\cdots H_{n-1}$. Minden $H_k$ ortogonális, ezért $Q$ is az, és $Q^\top=H_{n-1}\cdots H_1$, tehát $Q^\top A=R$. *Visszavezetés.* Az $Ax=b$-t balról $Q^\top$-vel szorozva: $Q^\top Ax=Q^\top b$, azaz $Rx=Q^\top b=:d$. *$Q$ nem épül fel:* mivel $Q^\top=H_{n-1}\cdots H_1$, a $d=H_{n-1}\cdots H_1 b$ ugyanazoknak a $H_k$-knak a $b$-re való alkalmazásával adódik — gyakorlatban a $[A\mid b]$ kibővített mátrixon hajtjuk végre a $k=1,\dots,n-1$ transzformációkat, így $H_k$ egyszerre hat a mátrixra és a jobboldalra. Végül $Rx=d$ visszahelyettesítéssel: $x_n=d_n/r_{nn}$, $x_i=\frac1{r_{ii}}\big(d_i-\sum_{j>i}r_{ij}x_j\big)$. *Műveletigény.* A $k$-adik lépés részmátrixa $h_k=n-k+1$ méretű, a reflexió költsége $\approx 4h_k^2$. Összegezve $\sum_{k=1}^{n-1}4h_k^2=4\sum_{s=2}^{n}s^2=4\cdot\frac{n(n+1)(2n+1)}{6}+O(n^2)=\frac{4}{3}n^3+O(n^2)$.

## Kapcsolódó oldalak

- [[tetel-03-gauss-eliminacio]] · [[tetel-04-lu-kapcsolat-1]] · [[tetel-05-lu-kapcsolat-2]] · [[tetel-06-lu-direkt]] — háromszög ág, GE⟺LU
- [[tetel-07-schur-komplementer]] · [[tetel-08-ldu-felbontas]] · [[tetel-09-cholesky]] — blokk-GE és szimmetrikus/SPD finomítások
- [[tetel-10-qr-gram-schmidt]] · [[tetel-11-householder-1]] · [[tetel-12-householder-2]] — ortogonális ág
