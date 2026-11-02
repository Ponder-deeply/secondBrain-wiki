---
tags: [concept]
sources: [NM1_ea09.pdf]
derivation: source
kind: procedure
element: water
updated: 2026-09-25
---

# Richardson-iteráció ($R(p)$)

Szimmetrikus, pozitív definit $A$ esetén az $Ax = b$ LER-t a $p$ paraméterrel $x = (I - pA)x + pb$ alakra írjuk. Pontosan a $0 < p < 2/M$ értékekre konvergens ($M$ a legnagyobb sajátérték); az optimális paraméter $p_0 = 2/(M+m)$, a kontrakciós együttható ekkor $(M-m)/(M+m)$.

## Tartalom

### Levezetés

Legyen $A$ szimmetrikus, pozitív definit, $p \in \mathbb{R}$:

$$Ax = b \iff pAx = pb \iff 0 = -pAx + pb \iff x = x - pAx + pb = (I - pA)x + pb.$$

**Definíció — Richardson-iteráció $p$ paraméterrel, $R(p)$:**

$$x^{(k+1)} = \underbrace{(I - pA)}_{B_{R(p)}}\,x^{(k)} + \underbrace{pb}_{c_{R(p)}}.$$

### Reziduumvektoros alak

$$x^{(k+1)} = x^{(k)} - pAx^{(k)} + pb = x^{(k)} + p\,(b - Ax^{(k)}) = x^{(k)} + p\,r^{(k)}.$$

Az $s^{(k)} := p\,r^{(k)}$ segédvektorral $x^{(k+1)} = x^{(k)} + s^{(k)}$ és $r^{(k+1)} = r^{(k)} - As^{(k)}$.

$$\begin{aligned}
&r^{(0)} := b - Ax^{(0)}\\
&k = 1, \dots, \text{leállásig:}\\
&\quad s^{(k)} := p\,r^{(k)}\\
&\quad x^{(k+1)} := x^{(k)} + s^{(k)}\\
&\quad r^{(k+1)} := r^{(k)} - As^{(k)}
\end{aligned}$$

**Jelentősége:** ez a legolcsóbb lépés — egyáltalán nincs LER-megoldás, csak egy mátrix–vektor szorzás $As^{(k)}$ (ritka $A$-ra nagyon olcsó); a lépés iránya maga a reziduum. A reziduum közvetlenül méri, mennyire teljesül az egyenlet, így leállási feltételnek is jó. A kétrétegű iterációs alakban $P = \tfrac1p I$ (lásd [[concepts/nummodi/ilu-felbontas]]).

**Megj.** Ha az $Ax = b$ helyett a $D^{-1}Ax = D^{-1}b$ LER-re ($D = \operatorname{diag}(a_{11},\dots,a_{nn})$) alkalmazzuk $R(p)$-t, az eredeti LER-re felírt [[concepts/nummodi/jacobi-iteracio|csillapított Jacobi-iterációt]] $J(p)$-t kapjuk.

### Konvergenciatétel

**Tétel.** Ha $A \in \mathbb{R}^{n\times n}$ szimmetrikus, pozitív definit, sajátértékei $m = \lambda_1 \le \dots \le \lambda_n = M$, akkor az $R(p)$ iteráció pontosan a

$$p \in \Bigl(0, \frac{2}{M}\Bigr)$$

értékekre konvergens minden kezdővektorra. Az optimális paraméter $p_0 = \dfrac{2}{M+m}$, a hozzá tartozó kontrakciós együttható

$$q = \varrho(B_{R(p_0)}) = \|B_{R(p_0)}\|_2 = \frac{M - m}{M + m}.$$

**Bizonyítás.**

1. **$B_{R(p)}$ sajátértékei.** Ha $Av = \lambda_i v$, akkor $(I - pA)v = v - p\lambda_i v = (1 - p\lambda_i)v$. Tehát $\lambda_i(p) = 1 - p\lambda_i$; speciálisan $\lambda_1(p) = 1 - pm$, $\lambda_n(p) = 1 - pM$.
2. **Spektrálsugár rögzített $p$-re:** $\varrho(B_{R(p)}) = \max_i |1 - p\lambda_i|$. Mivel $1 - p\lambda$ $\lambda$-ban lineáris, a maximumot a szélső sajátértékek egyike adja: $\varrho(B_{R(p)}) = \max\{|1 - pm|, |1 - pM|\}$.
3. **Ábra.** A $p \mapsto |1 - p\lambda_i|$ függvények „V” alakúak, $p = 1/\lambda_i$-ben nullák, $p = 0$-ban $1$ értékűek. Felső burkolójuk kis $p$-re $|1 - pm|$ (ez csökken lassabban), nagy $p$-re $|1 - pM|$ (ez nő meredekebben).
4. **Konvergencia.** A $\varrho(B_{R(p)}) < 1$ [[concepts/nummodi/banach-fixponttetel-rn|ekvivalens feltétel]] miatt: $|1 - p\lambda_i| < 1 \iff 0 < p\lambda_i < 2$ minden $i$-re, és mivel $\lambda_i > 0$, ez pontosan $0 < p < 2/M$. (A határ az $|1 - pM| = 1$ egyenlet nemnulla megoldása.)
5. **Optimális paraméter.** A burkoló minimuma ott van, ahol a két szélső ág találkozik: $|1 - pM| = |1 - pm|$ nemnulla megoldása, azaz $-1 + pM = 1 - pm$, $p(M + m) = 2$:
   $$p_0 = \frac{2}{M + m}.$$
6. **Kontrakciós együttható:**
   $$\varrho(B_{R(p_0)}) = 1 - p_0 m = \frac{M + m}{M + m} - \frac{2m}{M + m} = \frac{M - m}{M + m}.$$
7. **Kettes norma.** $A$ szimmetrikus, így $B_{R(p)} = I - pA$ is; szimmetrikus mátrix kettes normája egyenlő a spektrálsugarával ([[concepts/nummodi/matrixnormak]]), tehát $q = \|B_{R(p_0)}\|_2 = \tfrac{M-m}{M+m}$ kettes normabeli kontrakciós együttható. $\square$

**Megj.** $\dfrac{M - m}{M + m} = \dfrac{\operatorname{cond}_2(A) - 1}{\operatorname{cond}_2(A) + 1}$ (SZPD $A$-ra $\operatorname{cond}_2(A) = M/m$) — rosszul kondicionált mátrixra még optimális $p$-vel is lassú.

### Példa

$A = \begin{bmatrix}3&-1\\-1&3\end{bmatrix}$, $b = \begin{bmatrix}1\\5\end{bmatrix}$. Sajátértékek: $2$ és $4$, tehát $M = 4$, $m = 2$.

- Konvergens pontosan $p \in (0, \tfrac12)$-re.
- $p_0 = \tfrac{2}{4+2} = \tfrac13$, $\varrho(B_{R(p_0)}) = \tfrac{4-2}{4+2} = \tfrac13$.
- $B_{R(p_0)}$ szimmetrikus, ezért $\|B_{R(p_0)}\|_2 = \tfrac13 = q$.

### Vizsgán (23. tétel)

- **a)** $R(p)$ levezetése; reziduumvektoros alak és jelentősége; a konvergenciatétel kimondása.
- **b)** a tétel bizonyítása a fenti 7 lépésben (sajátértékek, V-ábra, két egyenlet, kettes norma).

## Kapocs

- [[concepts/nummodi/jacobi-iteracio]] — $R(p)$ a $D^{-1}$-gyel skálázott LER-en éppen $J(p)$
- [[concepts/nummodi/banach-fixponttetel-rn]] — $\varrho(B) < 1$ szükséges és elégséges feltétel
- [[concepts/nummodi/matrixnormak]] — szimmetrikus mátrixra $\|B\|_2 = \varrho(B)$
- [[concepts/nummodi/kondicioszam]] — $M/m = \operatorname{cond}_2(A)$ SZPD mátrixra
- [[concepts/nummodi/ilu-felbontas]] — kétrétegű alakban $P = \tfrac1p I$
- [[concepts/nummodi/iteracios-modszerek-ler]] — általános keret
