---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Pontsorozat konvergenciája metrikus térben

A számsorozat-limesz $\varepsilon$–$n_0$ definíciója szó szerint átvihető metrikus térbe, ha az abszolút értéket a metrikára cseréljük; a gömbök nyelvén ugyanez azt jelenti, hogy a sorozat minden $\varepsilon$ sugarú gömbbe véges sok tag kivételével beleesik.

## Tartalom

### Nyílt és zárt gömbök

Ha $(H, d)$ metrikus tér, akkor az $a \in H$ körüli, $r > 0$ sugarú **nyílt**, illetve **zárt gömb**

$$B(a,r) = \{x \in H : d(x,a) < r\}, \qquad \overline{B}(a,r) = \{x \in H : d(x,a) \leq r\}.$$

Az euklideszi térben ezek $\{x \in \mathbb{R}^p : |x-a| < r\}$, illetve $\{x \in \mathbb{R}^p : |x-a| \leq r\}$.

### A limesz definíciója

Legyenek $b, a_1, a_2, \dots$ pontok egy metrikus térben. Az $(a_n)$ sorozat **limesze** $b$ (jelben $a_n \to b$, $\lim a_n = b$), ha

$$\forall \varepsilon > 0\ \ \exists n_0\ \ \forall n > n_0 : \quad d(a_n, b) < \varepsilon, \quad \text{azaz} \quad a_n \in B(b,\varepsilon).$$

Az „$\exists n_0\ \forall n > n_0$", „$\exists n_0\ \forall n \geq n_0$", „elég nagy $n$-re", „véges sok $n$ kivételével" megfogalmazások egyenértékűek. A sorozat *konvergens*, ha van limesze, és *divergens*, ha nincs.

### Trivialitások

- $a_n \to b$ akkor és csak akkor, ha $d(a_n, b) \to 0$ (számsorozatként).
- A limeszpont **egyértelmű**.
- Véges sok elem hozzáadása, elhagyása, a sorozat átrendezése, az elemek véges sokszori ismétlése nem változtatja meg a konvergenciát.
- Konvergens sorozat minden részsorozata ugyanoda tart.

### Koordinátánkénti konvergencia $\mathbb{R}^p$-ben

**Tétel.** Legyenek $\mathbf{a}_n = (a_{n,1},\dots,a_{n,p})^\top$ és $\mathbf{b} = (b_1,\dots,b_p)^\top$. Ekvivalensek:

(a) $\mathbf{a}_n \to \mathbf{b}$; (b) $|\mathbf{a}_n - \mathbf{b}| \to 0$; (c) minden $1 \leq i \leq p$ esetén $a_{n,i} \to b_i$.

A vektorsorozat konvergenciája tehát $p$ darab számsorozat konvergenciájára esik szét.

### Konvergencia $C[a,b]$-ben

**Tétel.** Legyenek $g, f_1, f_2, \dots \in C[a,b]$. A $\|\cdot\|_\infty$ metrikában $f_n \to g$ akkor és csak akkor, ha $f_n \to g$ **egyenletesen**.

**Bizonyítás.** A definíciók egymásba írásával:

$$f_n \xrightarrow{L_\infty} g \iff \forall \varepsilon>0\ \exists n_0\ \forall n>n_0:\ \|f_n - g\| < \varepsilon$$
$$\iff \forall \varepsilon>0\ \exists n_0\ \forall n>n_0\ \forall x \in [a,b]:\ |f_n(x)-g(x)| < \varepsilon,$$

ami pontosan az egyenletes konvergencia definíciója. $\blacksquare$

A maximumnorma tehát nem valami új konvergenciafogalmat vezet be, hanem a már ismert egyenletes konvergenciát öltözteti metrikus térbe.

## Kapocs

- [[concepts/analiii/metrikus-ter]] — a definíció alapstruktúrája
- [[concepts/analiii/halmaz-pontjai-metrikus-terben]] — a gömbökre épülő pont-osztályozás
- [[concepts/analiii/nyilt-es-zart-halmazok]] — a zártság sorozatos jellemzése
- [[concepts/analiii/cauchy-sorozat-es-teljes-ter]] — a limesz létezésének belső kritériuma
- [[concepts/analiii/ekvivalens-normak]] — a konvergencia metrikafüggése és normafüggetlensége véges dimenzióban
