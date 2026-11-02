---
tags:
  - subject
sources:
  - NM1_ea00.pdf
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
  - NM1_ea12.pdf
  - NM1_ea13.pdf
  - NM1AB_kovetelmenyek.pdf
  - nummodi-canvas-hogyan-keszuljek-a-vizsgara.md
  - nummodi-canvas-tanmenet.md
  - nummodi-canvas-tudnivalok-a-hianyzasokrol.md
  - nummodi-canvas-tudnivalok-a-vizsgarol.md
derivation: source
math: 85
updated: 2026-10-23
---

# Numerikus módszerek 1. (nummodi)

Bevezetés a numerikus analízis alapvető módszereibe: lebegőpontos számábrázolás, közelítő számítások hibaelemzése, lineáris egyenletrendszerek direkt és iteratív megoldása, mátrixfelbontások, kondícionáltság, nemlineáris egyenletek megoldása és polinomok kiértékelése. A szóbeli vizsga mind a 28 tételéhez tartozik kidolgozott lap (lásd a tételjegyzéket lent).

## Tárgykör

- Oktató: Krebsz Anna (ELTE IK)
- Félév: v. félév (2026/27 ősz)
- Kapcsolódó anyagok: `Wiki/outputs/nummodi/`
- [[concepts/nummodi/tematika]] — a kurzus tematikája félév és témakör szerint
- [[concepts/nummodi/kovetelmenyek]] — szóbeli tételjegyzék, 28 tétel Alap/Complex bontásban
- [[concepts/nummodi/beugro-kerdesek]] — a beugró 75 kérdésének rövid, pontos válaszai
- [[concepts/nummodi/peldatar-feladattipusok]] — a példatár feladattípusai és megoldási menetei (ZH-felkészülés)

## Követelmények

A félév követelményei (Programtervező informatikus BSc, A és B szakirány; forrás: a kari követelményrendszer és a Canvas-oldalak, 2026/27/1):

- **Jelenlét:** az előadások látogatása kötelező, legalább **8 előadáson** jelen kell lenni (katalógusrendszer); a vizsgára jelentkezést az ennek nem megfelelőktől letiltják. Az előző félév legalább 4,0-s kreditindexe alapján az 1. héten elektronikus kérvényben felmentés kérhető. Ütköző előadás esetén a félév elején e-mailben kell jelezni mindkét oktatónak (név, Neptun-kód, hová jár be), a félév végén igazolni kell.
- **Gyakorlati jegy:** két évfolyam-ZH (írásban, részletes indoklással; csak üres papír és toll, számológép sem), egyenként max. 50 pont, **18 pont** a sikeres szint. Mindkét ZH sikeres: összpontszám alapján 83–100 jeles (5), 67–82 jó (4), 51–66 közepes (3), 36–50 elégséges (2). Egy sikertelen ZH-t a félév végi javító ZH-n lehet pótolni (az eredmény felülírja a régit; sikertelen javítás vagy kihagyás: elégtelen); két sikertelen ZH: elégtelen (1). Jobb jegyért az egyik ZH javítható. Elégtelen gyakorlati jegyre egyszeri utóvizsga (gyakUV) tehető: mindkét témakörből külön-külön 40% kell; 40–70% között elégséges (2), 70% felett közepes (3).
- **Házi feladatok:** a Canvasban kiadott feladatokra feladatonként 1 pont, félévente legfeljebb 10 pont; határidő az adott ZH, a javító ZH előtt már nem adhatók be; csak akkor számítanak, ha mindkét ZH sikeres.
- **Vizsgára bocsátás:** legalább elégséges gyakorlati jegy (Neptunba beírva) és Neptunon keresztüli jelentkezés; arcképes igazolvány, papír, toll és a tételjegyzék viszik magukkal. Jelenléti vizsga.
- **Vizsga, 1. rész — beugró:** 15 pontos, 20 perces írásbeli a Canvasban közzétett kérdésekből ([[concepts/nummodi/beugro-kerdesek]]); **8 pont** kell a szóbelire bocsátáshoz, különben a vizsgajegy elégtelen (1). Minden szóbeli előtt újra meg kell írni, még ha korábban sikerült is. Időbeosztás a vizsga napján: beugró 8:00–8:20, szóbeli 8:30-tól kb. 11:00-ig.
- **Vizsga, 2. rész — szóbeli:** a vizsgáztató által kijelölt egy tétel kidolgozása részletesen (definíciók, tételek, bizonyítások), kb. 30–45 perc felkészüléssel ([[concepts/nummodi/kovetelmenyek]]). Az **a) rész** alaptudás: legalább egy előadáson elhangzott nem triviális tétel vagy levezetés kell az elégséges (2)-höz, teljes ismeretével legfeljebb közepes (3). A **b) rész** nagyobb bizonyítás vagy levezetés; csak ezzel szerezhető jó (4) vagy jeles (5), de nem helyettesíti az a) részt. A jegy eldöntésére más tételből is kérdezhetnek.
- **Beugró kiváltása félév közben:** a két gyakorlati ZH után 15–15 pontos kérdéssor (az 1. ZH után az 1–34., a 2. ZH után a 35–66. beugrókérdésekből); mindkettőből 8–8 pont és legalább elégséges (2) gyakorlati jegy kell. Nem pótolható és nem javítható későbbi időpontban; a gyakorlati jegybe nem számít bele. Kiváltás esetén is kötelező a szóbeli.
- **Felkészülési tanács (Canvas):** a vizsgára tanulás a feladatmegoldással indul, ehhez keresendők ki a definíciók és tételek; a bizonyításokat félév közben apránként érdemes átnézni; a vizsgaidőszakban az előadásanyag átnézése, összevetés a tételjegyzékkel, a nehéz bizonyítások lépéseinek vázlatos kiírása. A tételjegyzék szerkezete lehetővé teszi a nehezebb (b) bizonyítások kihagyását, ha közepes jegy a cél.
- **Irodalom:** Gergó Lajos: *Numerikus módszerek* (ELTE Eötvös Kiadó, 2013); Bozsik József – Krebsz Anna: *Numerikus módszerek példatár* (2010; [[concepts/nummodi/peldatar-feladattipusok]]); Stoyan Gisbert – Takó Galina: *Numerikus módszerek 1.* (Typotex, 2002).

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
- [[concepts/nummodi/ldu-felbontas]] — $A = LDU$; szimmetrikus esetben $A = LDL^T$, $\tfrac{1}{3}n^3$ igény
- [[concepts/nummodi/cholesky-felbontas]] — $A = LL^T$ szimmetrikus pozitív definit mátrixra: létezés és egyértelműség, közvetlen képletek, $\tfrac13 n^3$ + $n$ gyökvonás, összevetés $LDL^T$-vel

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
- [[concepts/nummodi/gauss-seidel-iteracio]] — $B_S = -(L+D)^{-1}U$, „helyben” számolható koordinátás alak, reziduumos algoritmus, SDD és SZPD konvergencia
- [[concepts/nummodi/relaxalt-gauss-seidel-iteracio]] — $S(\omega)$; szükséges feltétel $0 < \omega < 2$ (determinánsos bizonyítás); tridiagonális és SZPD tételek, optimális $\omega_0$; Jacobi–Gauss–Seidel összevetés
- [[concepts/nummodi/richardson-iteracio]] — $x^{(k+1)} = (I - pA)x^{(k)} + pb$; konvergens pontosan $p \in (0, 2/M)$-re, $p_0 = 2/(M+m)$, $q = (M-m)/(M+m)$
- [[concepts/nummodi/ilu-felbontas]] — részleges LU-felbontás $A = LU - Q$ pozícióhalmazzal, helyességi tétel, SDD-létezés; ILU-iteráció és az általános kétrétegű iteráció

A 10. előadás harmadik része (kerekítési hibák hatása az iterációkra, $\lim\|z^{(k)}\| \le \varepsilon/(1 - \|B\|)$) egyik tételhez sem tartozik, ezért nincs külön lapja.

### Nemlineáris egyenletek és polinomok (11–13. előadás)

Gyökkereső módszerek nemlineáris $f(x) = 0$ egyenletekre: intervallumfelezés (lassú, robusztus), fixpont-iteráció (konvergencia a Banach-tételből), valamint a Newton-, húr- és szelőmódszer, amelyeket konvergenciarendjük különböztet meg. A 13. előadás önálló blokk: a gyökbecslési tétel megmondja, hol keressük a gyököket, a Horner-algoritmus pedig a kiértékelési eszköz, amelyre a gyökkeresők támaszkodnak.

- [[concepts/nummodi/nemlinearis-egyenletek-fixpont]] — a feladat; Bolzano, Brouwer (bizonyítással), kontrakció $[a;b]$-n, $|\varphi'| < 1$ elégséges feltétel, Banach-tétel, lokális fixponttétel
- [[concepts/nummodi/konvergenciarend]] — $p$-edrendű konvergencia, elemi tulajdonságok; $p$-edrendű fixpont-iterációk tétele bizonyítással
- [[concepts/nummodi/intervallumfelezes]] — algoritmus és $(b-a)/2^k$ hibabecslés
- [[concepts/nummodi/newton-modszer]] — levezetés; monoton és lokális konvergenciatétel bizonyítással; többváltozós Newton-módszer
- [[concepts/nummodi/hurmodszer-szelomodszer]] — húr- és szelőmódszer képlete, konvergenciatételei; összevetés a Newton-módszerrel
- [[concepts/nummodi/polinom-gyokbecsles]] — $r < |x_k| < R$ körgyűrű, bizonyítás reciprok-polinommal
- [[concepts/nummodi/horner-algoritmus]] — $\mathcal{O}(n)$ kiértékelés, deriváltak és Taylor-együtthatók ismételt Horner-sorokkal

### Gyakorló- és vizsgaanyagok

A beugró kérdései és a példatár feladatai az elméleti lapokra épülnek, a vizsga írásbeli, illetve a ZH-k számonkérési formáját fedik le.

- [[concepts/nummodi/beugro-kerdesek]] — a beugró 75 kérdésének rövid, pontos válaszai témakörönként (1–34. és 35–66. kérdés a ZH-s kiváltáshoz)
- [[concepts/nummodi/peldatar-feladattipusok]] — a példatár 1–4. és 9. fejezetének feladattípusai, megoldási menetei és megoldott minták

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
| 9 | A Cholesky-féle $LL^T$-felbontás | [[concepts/nummodi/cholesky-felbontas]] |
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
| 21 | A Gauss–Seidel-iteráció | [[concepts/nummodi/gauss-seidel-iteracio]]; b): [[concepts/nummodi/relaxalt-gauss-seidel-iteracio]] |
| 22 | A Gauss–Seidel relaxációs módszer | [[concepts/nummodi/relaxalt-gauss-seidel-iteracio]] |
| 23 | A Richardson-típusú iterációk | [[concepts/nummodi/richardson-iteracio]] |
| 24 | A részleges LU-felbontás és az ILU algoritmus | [[concepts/nummodi/ilu-felbontas]] |
| 25 | Nemlineáris egyenletek megoldása I. (fixponttételek, konvergenciarend) | [[concepts/nummodi/nemlinearis-egyenletek-fixpont]], [[concepts/nummodi/konvergenciarend]] |
| 26 | Nemlineáris egyenletek megoldása II. (húr-, szelő-, Newton-módszer) | [[concepts/nummodi/hurmodszer-szelomodszer]], [[concepts/nummodi/newton-modszer]] |
| 27 | Nemlineáris egyenletek megoldása III. (intervallumfelezés, Newton-módszer) | [[concepts/nummodi/intervallumfelezes]], [[concepts/nummodi/newton-modszer]] |
| 28 | Polinomok gyökeinek becslése, Horner-algoritmus | [[concepts/nummodi/polinom-gyokbecsles]], [[concepts/nummodi/horner-algoritmus]] |

## Kapocs

- [[subjects/analii]] — a derivált és a Taylor-formula, amire a numerikus módszerek épülnek
