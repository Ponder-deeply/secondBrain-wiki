---
tags:
  - concept
sources:
  - Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf
  - An_III_Gyak_2022_tavasz.pdf
  - gyakorlat.pdf
  - ElozetesMegajanlottVizsgaTetelek1.pdf
  - RopzhKerdesek.pdf
  - ElozetesKerdesekMegajanlottVizsgajegyhez1.pdf
  - 03_gyak_An_III_2022_tavasz.pdf
derivation: source
kind: definition
element: air
updated: 2026-10-21
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

### Feladatok

*Forrás: An_III_Gyak_2022_tavasz.pdf 3. gyakorlat; gyakorlat.pdf „Metrikus terek" 11–13.*

**Módszer.** Függvénysorozat konvergenciája $C[a,b]$-ben: számítsuk ki a pontonkénti limeszt $g$-t (egyenletes konvergencia esetén más limesz nem lehet), majd vizsgáljuk $\|f_k-g\|$-t a kért normában: $\|\cdot\|_\infty$-nél a szuprémumot (szélsőérték-keresés), $\|\cdot\|_1$-nél az integrált. Ha $g$ nem folytonos, $\|\cdot\|_\infty$-ben a sorozat biztosan divergens.

- **Diszkrét metrika.** Konvergens sorozatai a végül konstansak ($\rho<1$ csak $0$-t jelent). A tér teljes: egy Cauchy-sorozat az $\varepsilon=\tfrac12$-re már végül konstans.
- **A limesz egyértelmű** normált térben: $\|x_k-\alpha\|<\varepsilon$ és $\|x_k-\beta\|<\varepsilon$ ⇒ $\|\alpha-\beta\|<2\varepsilon$ minden $\varepsilon$-ra.
- **A távolság folytonossága.** Ha $x_n\to a$, akkor $\rho(a,y)=\lim\rho(x_n,y)$, mert a fordított háromszög-egyenlőtlenség szerint $|\rho(x_n,y)-\rho(a,y)|\le\rho(x_n,a)\to0$.
- **Példák $C[a,b]$-ben:**

| $f_k$ | $\|\cdot\|_\infty$ | $\|\cdot\|_1$ |
|---|---|---|
| $\frac{k^2x^3}{1+k^2x^4}$, $x\in[1,2]$ | $\to\frac1x$ ($\lvert f_k-\frac1x\rvert=\frac1{x(1+k^2x^4)}\le\frac1{1+k^2}$) | $\to\frac1x$ |
| $x^k-x^{2k}$, $[0,1]$ | divergens: a maximum $\tfrac14$ (ahol $x^k=\tfrac12$), a pontonkénti limesz $0$ | $\to0$ ($\tfrac1{k+1}-\tfrac1{2k+1}\to0$) |
| $x^k$, $[0,1]$ | divergens (a limesz nem folytonos) | $\to0$ ($\tfrac1{k+1}$) |
| $x^k$, $[0,\alpha]$, $\alpha<1$ | $\to0$ ($\alpha^k$) | $\to0$ |
| $\frac{kx^2}{1+kx^2}$, $[0,1]$ | divergens (limesz: $1$ ha $x>0$, $0$ ha $x=0$) | $\to1$ ($\int_0^1\frac{dx}{1+kx^2}=\frac{\operatorname{arctg}\sqrt k}{\sqrt k}\to0$) |
| $\frac1{x+k}$, $[0,2]$ | $\to0$ (supremum $\frac1k$) | $\to0$ |
| $\frac{kx}{1+k^2x^2}$, $[0,2]$ | divergens (maximum $\tfrac12$ az $x=\tfrac1k$-ban) | $\to0$ ($\frac1{2k}\ln(1+4k^2)$) |
| $x^k-x^{k+1}$, $[0,1]$ | $\to0$ (maximum $\frac1{k+1}(\frac k{k+1})^k\approx\frac1{ek}$) | $\to0$ |

A tanulság: $\|\cdot\|_1$-ben jóval több sorozat konvergens, mint $\|\cdot\|_\infty$-ben — a két norma nem ekvivalens ([[concepts/analiii/ekvivalens-normak]]).

- **Kvázikonstans sorozat (3. gyak 1. feladat).** $(x_k)$ kvázikonstans, ha $\exists\beta\,\exists N\,\forall k>N:x_k=\beta$. Minden metrikus térben konvergens (limesze $\beta$); a diszkrét metrikus térben pontosan a kvázikonstans sorozatok a konvergensek, mert $\varepsilon<1$-re $\rho(x_k,\alpha)<\varepsilon$ csak $x_k=\alpha$ esetén lehet.
- **Függvénysorozat-példák megoldása** (3. gyak 3–4. feladat): lásd [[concepts/analiii/fuggvenysorozat-egyenletes-konvergenciaja]].

## Kapocs

- [[concepts/analiii/fuggvenysorozat-egyenletes-konvergenciaja]] — a $C[a,b]$-beli normakonvergencia és a pontonkénti limesz kapcsolata
- [[concepts/analiii/metrikus-ter]] — a definíció alapstruktúrája
- [[concepts/analiii/halmaz-pontjai-metrikus-terben]] — a gömbökre épülő pont-osztályozás
- [[concepts/analiii/nyilt-es-zart-halmazok]] — a zártság sorozatos jellemzése
- [[concepts/analiii/cauchy-sorozat-es-teljes-ter]] — a limesz létezésének belső kritériuma
- [[concepts/analiii/ekvivalens-normak]] — a konvergencia metrikafüggése és normafüggetlensége véges dimenzióban
- [[concepts/analiii/vizsgakerdesek-es-bizonyitando-tetelek]] — a témához tartozó megajánlott vizsgajegy- és röpdolgozat-kérdések.
