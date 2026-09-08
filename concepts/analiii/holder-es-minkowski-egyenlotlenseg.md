---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Hölder- és Minkowski-egyenlőtlenség

A két egyenlőtlenség együtt igazolja, hogy $\|\cdot\|_q$ minden $1 \leq q \leq \infty$ esetén valóban norma: a Hölder-egyenlőtlenség a szorzatösszeget becsli konjugált kitevőpárral, a belőle levezetett Minkowski-egyenlőtlenség pedig maga a háromszög-egyenlőtlenség.

## Tartalom

### Hölder-egyenlőtlenség

**Tétel.** Ha $1 \leq q, r \leq \infty$ és $\frac{1}{q} + \frac{1}{r} = 1$ (*konjugált kitevőpár*), akkor tetszőleges $a_1,\dots,a_p$ és $b_1,\dots,b_p$ számokra

$$\|a\|_q \cdot \|b\|_r = \Bigl(\sum |a_i|^q\Bigr)^{1/q} \cdot \Bigl(\sum |b_i|^r\Bigr)^{1/r} \geq \sum_{i=1}^p |a_i b_i|.$$

**Bizonyítás.** Speciális esetek: ha $a$ vagy $b$ a nullvektor, mindkét oldal $0$. Ha $q = 1, r = \infty$, akkor a bal oldal $(\sum|a_i|)\cdot\max|b_i|$, ami legalább a jobb oldal; $q=\infty, r=1$ ugyanígy.

Általános eset ($a, b \neq 0$, $1 < q, r < \infty$): az egyenlőtlenség homogén, mindkét vektor végigosztható egy-egy számmal, ezért feltehető $\|a\|_q = \|b\|_r = 1$. A súlyozott számtani–mértani közép egyenlőtlensége az $|a_i|^q$ és $|b_i|^r$ számokra $1/q$ és $1/r$ súlyokkal:

$$|a_i b_i| = (|a_i|^q)^{1/q}(|b_i|^r)^{1/r} \leq \tfrac{1}{q}|a_i|^q + \tfrac{1}{r}|b_i|^r.$$

Összegezve $\sum |a_i b_i| \leq \frac{1}{q}\|a\|_q^q + \frac{1}{r}\|b\|_r^r = \frac{1}{q} + \frac{1}{r} = 1 = \|a\|_q\|b\|_r$. $\blacksquare$

### Cauchy–Bunyakovszkij–Schwarz-egyenlőtlenség

A $q = r = 2$ speciális eset:

$$\|a\|_2 \cdot \|b\|_2 = \sqrt{\textstyle\sum |a_i|^2} \cdot \sqrt{\textstyle\sum |b_i|^2} \geq \sum |a_i b_i| \geq |\langle a, b\rangle|.$$

### Minkowski-egyenlőtlenség

**Tétel.** Ha $1 \leq q \leq \infty$ és $a, b \in \mathbb{R}^p$, akkor $\|a+b\|_q \leq \|a\|_q + \|b\|_q$.

**Következmény.** $\|\cdot\|_q$ norma minden $1 \leq q \leq \infty$ esetén.

**Bizonyítás.** Speciális esetek: $q = \infty$-re $\max|a_i+b_i| \leq \max(|a_i|+|b_i|) \leq \max|a_i| + \max|b_i|$; $q = 1$-re tagonként a háromszög-egyenlőtlenség; $\|a+b\|_q = 0$ esetén triviális.

Általános eset ($1 < q < \infty$, $a + b \neq 0$): legyen $r = \frac{q}{q-1}$ a $q$ konjugáltja, így $\frac{q}{r} = q - 1$. Ekkor

$$\|a+b\|_q^q = \sum |a_i+b_i|\cdot|a_i+b_i|^{q/r} \leq \sum |a_i|\,|a_i+b_i|^{q/r} + \sum |b_i|\,|a_i+b_i|^{q/r}.$$

Mindkét szummára a Hölder-egyenlőtlenséget alkalmazva a $q, r$ kitevőkkel

$$\sum |a_i|\,|a_i+b_i|^{q/r} \leq \|a\|_q \cdot \|a+b\|_q^{q/r} = \|a\|_q \cdot \|a+b\|_q^{q-1},$$

és ugyanígy $b$-re. Beírva $\|a+b\|_q^q \leq (\|a\|_q + \|b\|_q)\,\|a+b\|_q^{q-1}$, végül $\|a+b\|_q^{q-1}$-nel leosztunk. $\blacksquare$

## Kapocs

- [[concepts/analiii/normalt-vektorter]] — a tétel célja: $\|\cdot\|_q$ normavolta
- [[concepts/analiii/ekvivalens-normak]] — a CBS-egyenlőtlenség adja a $\|x\|_1 \leq \sqrt{p}\,|x|$ becslést
- [[concepts/analii/integral-egyenlotlensegek]] — az egyenlőtlenségek integrálos rokonai Analízis II-ből
