---
tags: [concept]
sources: [Numerikus-modszerek-peldatar-ELTE-IK.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-23
---

# Példatár: feladattípusok és megoldási menetek

A Bozsik József – Krebsz Anna *Numerikus módszerek példatár* (ELTE IK, 2010) NM1-es fejezeteinek (1–4. és 9.) feladattípusai, a hozzájuk tartozó módszerrel és a fogalomlappal; a gyakorlati zárthelyik (ZH-k) számonkérése feladatmegoldás, írásban, részletes indoklással, számológép nélkül.

## Tartalom

A példatár minden fejezete *Feladatok* és *Megoldások* részre oszlik, a megoldások lépésről lépésre részletezettek. A PDF a teljes könyvnek csak az NM1-hez tartozó fejezeteit tartalmazza (1–4., 9.); a könyv további fejezetei (sajátérték-feladatok, interpoláció, spline, approximáció, integrálás) nem szerepelnek benne.

### 1. fejezet — Gépi számábrázolás és hibaszámítás (24 feladat)

Fogalomlapok: [[concepts/nummodi/lebegopont-modell]], [[concepts/nummodi/hibaszamitas]].

| Feladattípus | Menet |
|---|---|
| $M(t,k^-,k^+)$ elemszáma, $\varepsilon_0$, $\varepsilon_1$, $M_\infty$ | elemszám $= 2\cdot 2^{t-1}\cdot(k^+-k^-+1)+1$ (előjel, mantissza, karakterisztika, plusz a 0); $\varepsilon_0 = \tfrac12 2^{k^-}$; $\varepsilon_1 = 2^{1-t}$; $M_\infty = (1-2^{-t})2^{k^+}$ |
| $fl(x)$ kiszámítása | egész és törtrész külön átváltása kettes számrendszerbe (maradékos osztás, ill. ismételt kettővel szorzás), kerekítés $t$ mantisszajegyre, normalizálás, karakterisztika leolvasása |
| gépi művelet és hibakorlátja | $fl(a)\pm fl(b)$ a megadott aritmetikában; a bemenet hibája az input függvény tételéből, az eredményé a hibaterjedési képletekből |
| művelet hibája közelítő értékekkel | tizedes közelítés: a hibakorlát a kerekítés fél egysége; szorzatnál, hányadosnál relatív hibakorlátok összeadódnak |
| jegyveszítés elkerülése | kivonásnál az ekvivalens alak, pl. $\sqrt{2007}-\sqrt{2006} = \dfrac{1}{\sqrt{2007}+\sqrt{2006}}$; a két számítás hibabecslését össze kell vetni |
| függvényérték hibája | $\Delta_{f(a)} = M_1\Delta_a$, ill. a kondíciószámos relatív alak ($3^\pi$, $e^2$, $\cos 0{,}8$, $\sin 0{,}5$ közelítése) |

A példatár megoldott mintái (1–3. feladat):

| Halmaz | Elemszám | $\varepsilon_0$ | $\varepsilon_1$ | $M_\infty$ |
|---|---|---|---|---|
| $M(6,-3,3)$ | $2\cdot2^5\cdot7+1 = 449$ | $2^{-4} = \tfrac1{16}$ | $2^{-5} = \tfrac1{32}$ | $(1-2^{-6})2^3 = 7{,}875$ |
| $M(5,-4,4)$ | $2\cdot2^4\cdot9+1 = 289$ | $2^{-5} = \tfrac1{32}$ | $2^{-4} = \tfrac1{16}$ | $(1-2^{-5})2^4 = 15{,}5$ |
| $M(8,-4,4)$ | $2\cdot2^7\cdot9+1 = 2305$ | $2^{-5} = \tfrac1{32}$ | $2^{-7} = \tfrac1{128}$ | $(1-2^{-8})2^4 = 15{,}9375$ |

A 4. feladat megoldása: $fl(4{,}21)$ az $M(6,-4,4)$ halmazban a kerekítés után $[100010|3] = \tfrac{17}{4} = 4{,}25$ (az egész rész $100_2$, a tört rész négy jegyig számolva, a 4. törtjegy 1, ezért felfelé kerekítünk).

### 2. fejezet — Mátrix-szorzatfelbontások (75 feladat)

| Alfejezet (feladatok) | Módszer | Fogalomlap |
|---|---|---|
| Gauss-elimináció és determináns (1–10) | elimináció + visszahelyettesítés; részleges, ill. teljes főelemkiválasztás (5–7); több jobboldal egy eliminációval (8); általános $n$ méretű bidiagonális rendszerek (9–10) | [[concepts/nummodi/gauss-eliminacio]] |
| Mátrix inverze (11–18) | $[A\,|\,I]$ eliminálása; determináns a főelemek szorzata (előjellel, sorcserénél); általános $n\times n$ alakok | [[concepts/nummodi/gauss-eliminacio]] |
| LU-felbontás (19–33) | GE-vel párhuzamosan; mátrixszorzással; parketta-, sorfolytonos és oszlopfolytonos elrendezés; a 33. feladat a Schur-komplementer azonosítása $A_{22}$ helyén | [[concepts/nummodi/lu-felbontas]], [[concepts/nummodi/schur-komplementer]] |
| LDU az LU-ból (34–40) | $A = LU$, majd $D = \operatorname{diag}(U)$ és $U \to D^{-1}U$ | [[concepts/nummodi/ldu-felbontas]] |
| $LDL^T$ és $LL^T$ (41–46) | szimmetrikus mátrixokra; a Cholesky szimmetrikus pozitív definit mátrixra létezik | [[concepts/nummodi/cholesky-felbontas]] |
| ILU (47–51) | adott $J$ pozícióhalmazra $L$, $U$, $Q$ meghatározása, $A = LU - Q$ | [[concepts/nummodi/ilu-felbontas]] |
| QR Gram–Schmidttel (52–60) | a teljes és az egyszerűsített módszer; az egyszerűsítettnél a végén a normálást nem szabad elfelejteni | [[concepts/nummodi/gram-schmidt-ortogonalizacio]] |
| Householder (61–75) | $a$-t $k\cdot e_1$ alakra hozó $H$; $k = \mp\|a\|_2$ (előjelválasztás a kioltás elkerülésére); alkalmazás vektorra a mátrix felírása nélkül; felső háromszög alakra hozás; LER megoldása adott $QR$-ből | [[concepts/nummodi/householder-transzformacio]], [[concepts/nummodi/qr-felbontas]] |

### 3. fejezet — Vektor- és mátrixnormák, kondíciószám (25 feladat)

Fogalomlapok: [[concepts/nummodi/vektornormak]], [[concepts/nummodi/matrixnormak]], [[concepts/nummodi/kondicioszam]].

- **Vektornormák:** $\|x\|_1$, $\|x\|_2$, $\|x\|_\infty$ kiszámítása (pl. $x = (1,2,-3)$: $6$, $\sqrt{14}$, $3$); normák ekvivalenciája két egyenlőtlenségre bontva: $\|x\|_\infty \le \|x\|_1 \le n\|x\|_\infty$, ill. $\|x\|_\infty \le \|x\|_2$.
- **Mátrixnormák:** $\|A\|_1$, $\|A\|_2$, $\|A\|_\infty$, $\|A\|_F$ számolása; $\|A\|_F$ nem indukált; $\varrho(A) \le \|A\|$; normális mátrixra $\|A\|_2 = \varrho(A)$; unitér mátrixszal szorzás nem változtatja a 2-es és a Frobenius-normát; $\|A\|_F = (\operatorname{tr}(A^*A))^{1/2} = (\sum\lambda_i(A^*A))^{1/2}$; a Frobenius-norma illeszkedik a 2-es vektornormához.
- **Kondíciószám:** $\operatorname{cond}(A)$ több normában (1, 2, $\infty$, Frobenius); a $QR$-felbontás nem változtat a kondicionáltságon; Cholesky-nál $\operatorname{cond}_2(A) = \operatorname{cond}_2(L)\operatorname{cond}_2(L^T) = (\operatorname{cond}_2(L))^2$.

### 4. fejezet — LER iterációs módszerei (40 feladat)

Fogalomlapok: [[concepts/nummodi/iteracios-modszerek-ler]], [[concepts/nummodi/jacobi-iteracio]], [[concepts/nummodi/gauss-seidel-iteracio]], [[concepts/nummodi/relaxalt-gauss-seidel-iteracio]], [[concepts/nummodi/richardson-iteracio]], [[concepts/nummodi/ilu-felbontas]].

| Típus | Kérdés és menet |
|---|---|
| Egyszerű iteráció (1–4) | konvergencia az elégséges feltétellel ($\|B\| < 1$ valamely illeszkedő normában); hibabecslés $\|x_k - x^*\| \le \dfrac{q^k}{1-q}\|x_1 - x_0\|$; lépésszám a becslés megoldásával |
| Jacobi (5–10) | konvergál-e $J(1)$: SDD vagy $\varrho(B_J) < 1$; néhány lépés végrehajtása |
| Gauss–Seidel (11–20) | konvergál-e $S(1)$; lépések; lépésszám adott pontossághoz |
| Csillapított Jacobi, relaxáció (21–29) | milyen $\omega$-ra konvergens, melyik optimális; $\omega = \tfrac12$ mellett két lépés |
| Richardson (30–35) | $p \in (0, 2/M)$, $p_0 = 2/(M+m)$; konvergencia-bizonyítás $\varrho(A) < c$ mellett |
| ILU-algoritmus (36–40) | $P$, $Q$, $b$ adott: konvergál-e, két lépés, lépésszám |

Minta (1. feladat, egyszerű iteráció): $\|B\|_1 = 0{,}6 < 1$, tehát minden $x_0$-ra konvergens; $x_0 = 0$-val $x_1 = c = (0{,}1;\,0{,}5;\,0{,}1)^T$, így $\|x_k - x^*\|_1 \le \dfrac{0{,}6^k}{1-0{,}6}\cdot 0{,}7$; a $10^{-3}$ pontossághoz $k \ge \dfrac{\lg(\tfrac74\cdot10^3)}{\lg\tfrac53} \approx 14{,}6$, azaz 15 lépés.

### 9. fejezet — Nemlineáris egyenletek (28 feladat)

Fogalomlapok: [[concepts/nummodi/polinom-gyokbecsles]], [[concepts/nummodi/intervallumfelezes]], [[concepts/nummodi/nemlinearis-egyenletek-fixpont]], [[concepts/nummodi/konvergenciarend]], [[concepts/nummodi/newton-modszer]].

| Típus | Menet |
|---|---|
| Gyökbecslés (1–4) | $r = \dfrac{1}{1 + \max_{i\ge1}|a_i|/|a_0|} \le |x_k| \le R = 1 + \dfrac{\max_{i<n}|a_i|}{|a_n|}$ |
| Intervallumfelezés (5–9) | előjelváltás ellenőrzése (Bolzano), felezés, az utolsó intervallum felezőpontja; lépésszám a $(b-a)/2^k$ becslésből |
| Fixpont-iteráció (10–21) | $\varphi$ kontrakció volta az $[a;b]$-n ($|\varphi'| \le q < 1$, és $\varphi$ az intervallumot önmagába képezi); hibabecslés; konvergenciarend a $\varphi'(x^*) = 0$ feltételből; különböző átrendezések ($x_k$, $y_k$ sorozatok) közül a konvergens kiválasztása |
| Newton-módszer (22–28) | az iteráció felírása; másodrendű lokális konvergencia ($f'(x^*) \ne 0$); az indulóintervallum a monoton konvergencia tételéből; a 28. feladat $f(x) = -\tfrac{x}{1+x}$ egyenletére a konvergenciarendről is kérdez |

Minták a gyökbecslésre: $P(x) = 3x^4 - x^3 - 5x^2 + 4x - 6$ gyökeire $\tfrac{6}{11} \le |x_k| \le 3$; $P(x) = -x^5 + 2x^3 + x^2 + 8$ gyökeire $\tfrac45 \le |x_k| \le 9$; $4x^4 - 3x^3 - 6x^2 + x - 1$ gyökeire $\tfrac17 \le |x_k| \le 2{,}5$; $x^3 - 6x^2 - 2x + 4$ gyökeire $\tfrac45 \le |x_k| \le 7$. Intervallumfelezés ($x^2 - 2 = 0$, $[1;2]$): három lépés után az intervallum $[1{,}375;\,1{,}5]$ (hossza $0{,}125$), a felezőpont $1{,}4375$ már $\tfrac1{10}$ pontosságú.

## Kapocs

- [[concepts/nummodi/beugro-kerdesek]] — az elmélet, amire a feladatok épülnek (a definíciók és tételek kivonata)
- [[concepts/nummodi/kovetelmenyek]] — a szóbeli tételek; a feladatok a gyakorlati jegy (ZH) anyagát adják
- [[concepts/nummodi/tematika]] — a kurzus tematikája
- [[subjects/nummodi]] — kurzus áttekintése, követelmények
