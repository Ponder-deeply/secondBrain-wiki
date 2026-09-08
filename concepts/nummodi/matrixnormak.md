---
tags: [concept]
sources: [NM1_ea06.pdf]
derivation: source
updated: 2026-08-05
---

# Mátrixnormák

A mátrixnorma a mátrixok „nagyságának" mérőszáma, amelyet a vektornormák mintájára, de egy fontos extra axiómával (szubmultiplikativitás) definiálnak. Alapvető eszköz a lineáris egyenletrendszerek hibaelemzéséhez és az iteratív módszerek konvergencia-vizsgálatához.

## Definíció: mátrixnorma

Legyen $n \in \mathbb{N}$ rögzített. A $\|\cdot\| : \mathbb{R}^{n\times n} \to \mathbb{R}$ leképezést **mátrixnormának** nevezzük, ha

1. $\|A\| \geq 0 \quad (\forall A \in \mathbb{R}^{n\times n})$,
2. $\|A\| = 0 \iff A = 0$,
3. $\|\lambda \cdot A\| = |\lambda| \cdot \|A\| \quad (\forall \lambda \in \mathbb{R},\ \forall A \in \mathbb{R}^{n\times n})$,
4. $\|A + B\| \leq \|A\| + \|B\| \quad (\forall A, B \in \mathbb{R}^{n\times n})$,
5. $\|A \cdot B\| \leq \|A\| \cdot \|B\| \quad (\forall A, B \in \mathbb{R}^{n\times n})$.

Ugyanaz, mint a vektornormáknál, plusz az 5. axióma: **szubmultiplikativitás**. Ezek a mátrixnormák **axiómái**.

## Frobenius-norma

**Definíció:** A következő függvényt **Frobenius-normának** nevezzük:

$$\|\cdot\|_F : \mathbb{R}^{n\times n} \to \mathbb{R}, \qquad \|A\|_F = \left(\sum_{i=1}^n \sum_{j=1}^n |a_{ij}|^2\right)^{1/2}.$$

**Állítás:** A $\|\cdot\|_F$ függvény valóban mátrixnorma.

**Bizonyítás:** Az 1–4. axióma következik a $\|\cdot\|_2$ vektornorma tulajdonságaiból (az $n\times n$-es mátrixot $n^2$-es vektorként kezelve). Az 5. axióma belátható a CBS-egyenlőtlenség segítségével. $\square$

### Numerikus példa

$$A = \begin{bmatrix}1 & -4 \\ 2 & 2\end{bmatrix}, \quad B = \begin{bmatrix}3 & 2 \\ 1 & 5\end{bmatrix}.$$

$$\|A\|_F = \sqrt{1^2 + (-4)^2 + 2^2 + 2^2} = \sqrt{1+16+4+4} = 5,$$
$$\|B\|_F = \sqrt{3^2 + 2^2 + 1^2 + 5^2} = \sqrt{9+4+1+25} = \sqrt{39} \approx 6{,}24.$$

**Megjegyzés az előadáson:** $\|B\|_F = 6$ szerepelt (a $\sqrt{39}$ helyett), ami valószínűleg kerekítés volt a diában.

## Indukált (természetes) mátrixnormák

**Definíció:** Legyen $\|\cdot\|_v : \mathbb{R}^n \to \mathbb{R}$ tetszőleges vektornorma. Ekkor a

$$\|\cdot\| : \mathbb{R}^{n\times n} \to \mathbb{R}, \qquad \|A\| := \sup_{x \neq 0} \frac{\|Ax\|_v}{\|x\|_v}$$

függvényt a $\|\cdot\|_v$ **vektornorma által indukált mátrixnormának** hívjuk. Egy mátrixnormát **természetesnek** nevezünk, ha van olyan vektornorma, ami indukálja.

**Megjegyzések:**
- A sup helyett max is írható (a maximum felvétetik).
- Átfogalmazás: $\|A\| = \sup_{\|y\|_v = 1} \|Ay\|_v$.
- Következmény: $\dfrac{\|Ax\|_v}{\|x\|_v} \leq \|A\|$, azaz $\|Ax\|_v \leq \|A\| \cdot \|x\|_v$. Sőt, $\|A\|$ a legkisebb ilyen felső korlát.

**Tétel:** Az indukált mátrixnormák valóban mátrixnormák.

**Bizonyítás** (a 3. és 4. axiómára, $B \neq 0$ esetén az 5-re):

- **3. axióma:** $\|\lambda A\| = \sup_{x\neq 0}\frac{\|\lambda Ax\|_v}{\|x\|_v} = |\lambda|\sup_{x\neq 0}\frac{\|Ax\|_v}{\|x\|_v} = |\lambda|\cdot\|A\|$.
- **4. axióma:** $\|A+B\| = \sup_{x\neq 0}\frac{\|(A+B)x\|_v}{\|x\|_v} \leq \sup_{x\neq 0}\frac{\|Ax\|_v+\|Bx\|_v}{\|x\|_v} \leq \|A\| + \|B\|$.
- **5. axióma** ($B\neq 0$):
$$\|AB\| = \sup_{x\neq 0}\frac{\|ABx\|_v}{\|x\|_v} = \sup_{x\neq 0,Bx\neq 0}\frac{\|ABx\|_v}{\|Bx\|_v}\cdot\frac{\|Bx\|_v}{\|x\|_v} \leq \sup_{y\neq 0}\frac{\|Ay\|_v}{\|y\|_v}\cdot\sup_{x\neq 0}\frac{\|Bx\|_v}{\|x\|_v} = \|A\|\cdot\|B\|.$$
(Meggondolható, hogy a $Bx\neq 0$ feltétel nem változtatja meg a szuprémum értékét; közben bevezettük a $y := Bx$ jelölést.) $\square$

## Illeszkedő normák

**Definíció:** Ha egy $\|\cdot\|$ mátrix- és egy $\|\cdot\|_v$ vektornormára

$$\|Ax\|_v \leq \|A\| \cdot \|x\|_v \qquad (\forall x \in \mathbb{R}^n,\ A \in \mathbb{R}^{n\times n})$$

teljesül, akkor **illeszkedőknek** nevezzük őket.

**Állítás:** A természetes mátrixnormák illeszkednek az őket indukáló vektornormákhoz.

**Bizonyítás:** Láttuk az előbb ($\|Ax\|_v \leq \|A\|\cdot\|x\|_v$); az $x=0$ eset külön meggondolandó. $\square$

## Nevezetes indukált normák (1, 2, ∞)

**Tétel:** A $\|\cdot\|_p$ ($p = 1, 2, \infty$) vektornormák által indukált mátrixnormák:

$$\|A\|_1 = \max_{j=1}^n \sum_{i=1}^n |a_{ij}| \qquad \text{(oszlopnorma — oszloponként összegez, a maximumot veszi)},$$

$$\|A\|_\infty = \max_{i=1}^n \sum_{j=1}^n |a_{ij}| \qquad \text{(sornorma — soronként összegez, a maximumot veszi)},$$

$$\|A\|_2 = \left(\max_{i=1}^n \lambda_i(A^\top A)\right)^{1/2} \qquad \text{(spektrálnorma)},$$

ahol $\lambda_i(M)$ az $M$ mátrix $i$-edik sajátértékét jelöli ($Mv = \lambda v$, $v \neq 0$).

### Bizonyítás vázlata ($\|\cdot\|_1$ esetén)

*Állítás:* $\|A\|_1 = \max_{j=1}^n \sum_{i=1}^n |a_{ij}|$.

A bizonyítás két részből áll: (a) megmutatjuk, hogy $f(A) := \max_j\sum_i |a_{ij}|$ felső korlát; (b) egyenlőség is elérhető.

**Felső korlát:**
$$\|Ax\|_1 = \sum_{i=1}^n |(Ax)_i| = \sum_{i=1}^n \left|\sum_{j=1}^n a_{ij}x_j\right| \leq \sum_{i=1}^n\sum_{j=1}^n |a_{ij}|\cdot|x_j| = \sum_{j=1}^n |x_j|\left(\sum_{i=1}^n|a_{ij}|\right) \leq \left(\max_{j}\sum_i|a_{ij}|\right)\cdot\|x\|_1.$$

**Egyenlőség:** Legyen $x = e_k$, ahol $k$ a maximális oszlopösszeget adó index. Ekkor $\|Ae_k\|_1 = \sum_i|a_{ik}| = f(A)$ és $\|e_k\|_1 = 1$. $\square$

### Bizonyítás ($\|\cdot\|_\infty$ esetén)

Hasonló stílusú a $\|\cdot\|_1$ esetéhez; az egyenlőséghez $x = (\pm1,\ldots,\pm1)^\top$-t választunk, megfelelő előjelekkel.

### Bizonyítás ($\|\cdot\|_2$ esetén)

**Az $A^\top A$ sajátértékei nemnegatívak:** $(A^\top A)^\top = A^\top A$, szimmetrikus. Ha $A^\top A y = \lambda y$ ($y\neq 0$), akkor $y^\top A^\top Ay = \lambda y^\top y$, azaz $\|Ay\|_2^2 = \lambda\|y\|_2^2 \geq 0$.

**Dializálhatóság:** Mivel $A^\top A$ szimmetrikus, létezik $U$ ortogonális mátrix, amelyre $A^\top A = U^\top DU$ ($D$ diagonális, a sajátértékekkel). Legyen $y := Ux$:

$$\|Ax\|_2^2 = x^\top A^\top Ax = x^\top U^\top DUx = (Ux)^\top D(Ux) = y^\top Dy = \sum_{i=1}^n d_{ii}|y_i|^2 \leq \max_i d_{ii}\cdot\sum_i|y_i|^2 = \max_i\lambda_i(A^\top A)\cdot\|y\|_2^2.$$

Mivel $\|y\|_2^2 = y^\top y = (Ux)^\top(Ux) = x^\top U^\top Ux = x^\top x = \|x\|_2^2$:

$$\|Ax\|_2^2 \leq \max_i\lambda_i(A^\top A)\cdot\|x\|_2^2, \quad \text{azaz} \quad \frac{\|Ax\|_2}{\|x\|_2} \leq \left(\max_i\lambda_i(A^\top A)\right)^{1/2}.$$

**Egyenlőség:** Legyen $\lambda_m = \max_i\lambda_i(A^\top A)$ és $v_m \neq 0$ a hozzá tartozó sajátvektor, $\|v_m\|_2 = 1$:

$$\|Av_m\|_2^2 = v_m^\top A^\top A v_m = \lambda_m \cdot \underbrace{v_m^\top v_m}_{=1} = \lambda_m. \quad \square$$

## Spektrálsugár

**Definíció:** Az $A \in \mathbb{R}^{n\times n}$ mátrix **spektrálsugara**:

$$\varrho(A) := \max_{i=1}^n |\lambda_i(A)|.$$

**Megjegyzés:** A spektrálnormát a spektrálsugárral is megadhatjuk:

$$\|A\|_2 = \sqrt{\varrho(A^\top A)}.$$

**Állítás:** Ha $A \in \mathbb{R}^{n\times n}$ szimmetrikus (önadjungált), akkor $\|A\|_2 = \varrho(A)$.

**Bizonyítás:** Triviális (szimmetrikus mátrixra $A^\top A = A^2$, ezért $\varrho(A^\top A) = \varrho(A)^2$). $\square$

**Állítás:** Ha $A$ normális ($A^*A = AA^*$), akkor $\|A\|_2 = \varrho(A)$.

**Bizonyítás:** Normális mátrixokra (lineáris algebrából ismert) létezik $U$ unitér hasonlósági transzformáció, amellyel $A$ diagonálisra hozható: $U^*AU = D = \text{diag}(\lambda_i(A))$. Innen:
$$A^*A = (UDU^*)^*(UDU^*) = UD^*U^*UDU^* = UD^*DU^*, \qquad \lambda_i(A^*A) = \lambda_i(D^*D) = |\lambda_i(A)|^2,$$
$$\varrho(A^*A) = \varrho(A)^2, \qquad \|A\|_2 = \varrho(A^*A)^{1/2} = \varrho(A). \quad \square$$

## Frobenius-norma nem természetes

**Állítás:** A Frobenius-norma **nem** természetes mátrixnorma.

**Bizonyítás:** Tekintsük az $I \in \mathbb{R}^{n\times n}$ egységmátrixot.
- Indukált mátrixnormák esetén $\|I\| = \sup_{x\neq 0}\frac{\|Ix\|_v}{\|x\|_v} = 1$.
- Másrészt $\|I\|_F = \sqrt{n}$.
- Tehát ha $n > 1$, nincs olyan vektornorma, ami a Frobenius-normát indukálná. $\square$

## Spektrálsugár és norma viszonya

**Állítás:** Tetszőleges mátrixnormára $\varrho(A) \leq \|A\|$.

**Bizonyítás:** Legyen $\lambda$ tetszőleges sajátérték és $v \neq 0$ a hozzá tartozó sajátvektor: $Av = \lambda v$. Ekkor $Avv^\top = \lambda vv^\top$, tehát $\|A\|\cdot\|vv^\top\| \geq \|Avv^\top\| = \|\lambda vv^\top\| = |\lambda|\cdot\|vv^\top\|$. Leosztva $\|vv^\top\| \neq 0$-val: $\|A\| \geq |\lambda|$. $\square$

## Nevezetes példa: $\|\cdot\|_1$, $\|\cdot\|_\infty$ és $\|\cdot\|_2$ mátrixnormára

$$A = \begin{bmatrix}1 & -4 \\ 2 & 2\end{bmatrix}.$$

$$\|A\|_1 = \max\{1+2,\,|-4|+2\} = \max\{3,6\} = 6 \quad \text{(maximális oszlopösszeg)},$$
$$\|A\|_\infty = \max\{1+|-4|,\,2+2\} = \max\{5,4\} = 5 \quad \text{(maximális sorösszeg)},$$

$$A^\top A = \begin{bmatrix}1 & 2\\-4 & 2\end{bmatrix}\begin{bmatrix}1 & -4\\2 & 2\end{bmatrix} = \begin{bmatrix}5 & 0\\0 & 20\end{bmatrix},$$

$$\|A\|_2 = \left(\max\{5,20\}\right)^{1/2} = \sqrt{20} \approx 4{,}4721 \quad \text{(spektrálnorma)}.$$

## Feladatok a gyakorlatra (összefoglaló)

Az előadáson szereplő, bizonyítandó állítások:

- Ha $Q$ ortogonális (unitér), akkor $\|Qx\|_2 = \|x\|_2$, $\|Q\|_2 = 1$, $\|QA\|_2 = \|AQ\|_2 = \|A\|_2$.
- $\|A\|_F^2 = \operatorname{tr}(A^\top A)$, ahol $\operatorname{tr}(B) := \sum_{k=1}^n b_{kk}$ a mátrix nyoma.
- Ha $Q$ ortogonális, akkor $\|QA\|_F = \|AQ\|_F = \|A\|_F$.
- $\|A\|_F^2 = \sum_{i=1}^n \lambda_i(A^\top A)$.
- $\|\cdot\|_F$ és $\|\cdot\|_2$ ekvivalens mátrixnormák.
- A Frobenius-norma illeszkedik a kettes vektornormához.

## Kapocs

- [[concepts/nummodi/vektornormak]] — vektornormák definíciója, p-normák, ekvivalencia, konvergencia
- [[concepts/nummodi/hibaszamitas]] — kondíciószám; mátrixnormák szerepe a hibaanalízisben
- [[concepts/nummodi/kondicioszam]] — kondíciószám $\operatorname{cond}(A)=\|A\|\cdot\|A^{-1}\|$; normafüggőség, sajátérték-kapcsolat
- [[concepts/nummodi/ler-erzekenysege]] — LER perturbációs tételei; illeszkedő normák szerepe a bizonyításban
- [[concepts/nummodi/relativ-maradek]] — relatív maradék ($\eta$) és $\|\Delta A\|/\|A\|$ kapcsolata
- [[concepts/nummodi/ortogonalis-matrixok]] — ortogonális mátrixok és a spektrálnorma kapcsolata ($\|Q\|_2=1$)
- [[concepts/nummodi/linearis-egyenletrendszerek]] — LER hibaanalízise, kondíciószám és normák
- [[concepts/nummodi/householder-transzformacio]] — Householder-mátrix mint ortogonális mátrix; $\|H\|_2 = 1$
- [[subjects/nummodi]] — kurzus áttekintése
