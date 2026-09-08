---
tags: [concept]
sources: [NM1_ea06.pdf]
derivation: source
updated: 2026-08-05
---

# Vektornormák

A vektornorma a vektorok „hosszának" általánosítása véges dimenziós valós tereken. Numerikus módszerekben a hibák és perturbációk mérésére, valamint a konvergencia vizsgálatára szolgál.

## Emlékeztető: kettes norma

Az $x \in \mathbb{R}^n$ vektor hagyományos („kettes normája"):

$$\|x\|_2 := \sqrt{\langle x, x\rangle} = \sqrt{x^\top x} = \left(\sum_{k=1}^n x_k^2\right)^{1/2}.$$

Ez skaláris szorzat által generált norma.

## Definíció: vektornorma

Legyen $n \in \mathbb{N}$ rögzített. A $\|\cdot\| : \mathbb{R}^n \to \mathbb{R}$ leképezést **vektornormának** nevezzük, ha

1. $\|x\| \geq 0 \quad (\forall x \in \mathbb{R}^n)$,
2. $\|x\| = 0 \iff x = 0$,
3. $\|\lambda \cdot x\| = |\lambda| \cdot \|x\| \quad (\forall \lambda \in \mathbb{R},\ \forall x \in \mathbb{R}^n)$,
4. $\|x + y\| \leq \|x\| + \|y\| \quad (\forall x, y \in \mathbb{R}^n)$.

Ezek a vektornormák **axiómái**: a leképezés „pozitív", „pozitív homogén" és „szubadditív" (háromszög-egyenlőtlenség).

**Állítás:** Ha $\langle\cdot,\cdot\rangle : \mathbb{R}^n \times \mathbb{R}^n \to \mathbb{R}$ skaláris szorzat, akkor az $f(x) := \sqrt{\langle x,x\rangle}$ függvény norma (jele: $\|x\|_2$).

**Bizonyítás:** Nem kell — ez a „hagyományos hossz". $\square$

## Cauchy–Bunyakovszkij–Schwarz-egyenlőtlenség (CBS)

$$|\langle x, y\rangle| \leq \|x\|_2 \cdot \|y\|_2 \qquad (x, y \in \mathbb{R}^n).$$

**Bizonyítás:** Bármely $\alpha \in \mathbb{R}$ esetén $\|x - \alpha y\|_2^2 \geq 0$:

$$0 \leq \|x - \alpha y\|_2^2 = \langle x, x\rangle - 2\alpha\langle x, y\rangle + \alpha^2\langle y, y\rangle = \|x\|_2^2 - 2\alpha\langle x,y\rangle + \alpha^2\|y\|_2^2.$$

A jobb oldal $\alpha$-ban másodfokú, diszkriminánsának nemnegatívnak kell lennie:

$$\langle x,y\rangle^2 - \|x\|_2^2 \cdot \|y\|_2^2 \leq 0 \implies \langle x,y\rangle^2 \leq \|x\|_2^2 \cdot \|y\|_2^2. \quad \square$$

## Nevezetes vektornormák (1, 2, ∞)

**Állítás:** A következő formulák vektornormákat **definiálnak** $\mathbb{R}^n$ felett:

- $\displaystyle\|x\|_1 := \sum_{i=1}^n |x_i|$ — **Manhattan-norma** (taxinorma),
- $\displaystyle\|x\|_2 := \left(\sum_{i=1}^n |x_i|^2\right)^{1/2}$ — **Euklideszi-norma**,
- $\displaystyle\|x\|_\infty := \max_{i=1}^n |x_i|$ — **Csebisev-norma** (maximumnorma).

**Bizonyítás:** Házi feladat.

### Numerikus példa

$$x = \begin{bmatrix}3\\4\end{bmatrix}, \quad y = \begin{bmatrix}4\\-8\\1\end{bmatrix}.$$

| Norma | $\|x\|$ | $\|y\|$ |
|---|---|---|
| $\|\cdot\|_1$ | $3+4=7$ | $4+8+1=13$ |
| $\|\cdot\|_2$ | $\sqrt{9+16}=5$ | $\sqrt{16+64+1}=\sqrt{73}$ |
| $\|\cdot\|_\infty$ | $\max\{3,4\}=4$ | $\max\{4,8,1\}=8$ |

## p-normák

**Állítás:** A következő $\mathbb{R}^n \to \mathbb{R}$ függvények is vektornormákat definiálnak:

$$\|x\|_p := \left(\sum_{i=1}^n |x_i|^p\right)^{1/p} \qquad (p \in \mathbb{R},\ 1 \leq p < \infty).$$

**Bizonyítás:** Nem kell. A háromszög-egyenlőtlenség a Minkovszki-egyenlőtlenség. $\square$

**Megjegyzések:**
- $0 \leq p < 1$ esetén nem norma,
- $p_1 \leq p_2 \implies \|x\|_{p_1} \geq \|x\|_{p_2}$,
- $p = 1 \rightsquigarrow \|x\|_1$, $p = 2 \rightsquigarrow \|x\|_2$,
- $\displaystyle\lim_{p\to\infty}\|x\|_p = \|x\|_\infty$.

## Normák közötti egyenlőtlenségek

**Állítás:** Az $1, 2, \infty$-normák között fennállnak az alábbi egyenlőtlenségek:

$$\|x\|_\infty \leq \|x\|_1 \leq n \cdot \|x\|_\infty,$$
$$\|x\|_\infty \leq \|x\|_2 \leq \sqrt{n} \cdot \|x\|_\infty,$$
$$\|x\|_2 \leq \|x\|_1 \leq \sqrt{n} \cdot \|x\|_2,$$

sőt ezek alapján $\|x\|_\infty \leq \|x\|_2 \leq \|x\|_1$.

**Bizonyítás:** Nem kell. (Az első egyenlőtlenség könnyen belátható, a negyedikre korábban láttunk példát.) $\square$

## Ekvivalens normák

**Definíció:** A $\|\cdot\|_a$ és $\|\cdot\|_b$ vektornormák **ekvivalensek**, ha $\exists c_1, c_2 \in \mathbb{R}^+$, amelyekre

$$c_1 \cdot \|x\|_b \leq \|x\|_a \leq c_2 \cdot \|x\|_b \qquad (\forall x \in \mathbb{R}^n).$$

**Állítás — végesdimenziós normák ekvivalenciája:** Tetszőleges $\mathbb{R}^n$-en értelmezett vektornorma ekvivalens az Euklideszi-vektornormával. (Azaz adott véges dimenziós térben **minden norma ekvivalens**.)

## Konvergencia vektornormában

**Definíció:** Az $(x_k) \subset \mathbb{R}^n$ sorozat **konvergens**, ha létezik $x^* \in \mathbb{R}^n$, amelyre

$$\lim_{k\to\infty} \|x_k - x^*\| = 0.$$

$x^*$ a sorozat **határértéke**.

**Megjegyzés:** Mivel $\mathbb{R}^n$-en a vektornormák ekvivalensek, ha egy sorozat konvergens az egyik vektornormában, akkor mindegyikben konvergens (és ugyanoda tart). Két ekvivalens átfogalmazás:

- $\forall\varepsilon > 0\ \exists N_0 \in \mathbb{N}\ \forall k \geq N_0 :\ \|x_k - x^*\| < \varepsilon$,
- $\forall\varepsilon > 0\ \exists N_0 \in \mathbb{N}\ \forall k \geq N_0 :\ x_k \in K_\varepsilon(x^*)$ (azaz $x_k$ az $x^*$ körüli $\varepsilon$-gömbbe esik).

## Kapocs

- [[concepts/nummodi/matrixnormak]] — mátrixnormák definíciója, Frobenius-norma, indukált normák
- [[concepts/nummodi/hibaszamitas]] — kondíciószám, hibák jellemzése és terjedése
- [[concepts/nummodi/ortogonalis-matrixok]] — ortogonális mátrixok és a kettes norma kapcsolata
- [[concepts/nummodi/householder-transzformacio]] — a Householder-transzformáció hosszmegtartó (kettes norma megmarad)
- [[subjects/nummodi]] — kurzus áttekintése
