---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf, SimonP-Anal2.pdf, An_III_Gyak_2022_tavasz.pdf, gyakorlat.pdf, RopzhKerdesek.pdf, ElozetesKerdesekMegajanlottVizsgajegyhez1.pdf, 02_gyak_An_III_2024_25_Ifelev.pdf]
references: ["Simon Péter: Analízis II., 1.2. iv)–v) megjegyzés"]
derivation: source
kind: definition
element: air
updated: 2026-10-21
---

# Normált vektortér

A normált vektortér olyan vektortér, amelyen a vektorok „hossza" mérhető; a norma automatikusan metrikát indukál, így minden normált tér metrikus tér is. A legfontosabb példák az $\mathbb{R}^p$-beli $L^q$-normák és a $C[a,b]$-beli maximumnorma.

## Tartalom

### Definíció

**Normált vektortér:** a $\bigl(V, \|\cdot\|\bigr)$ pár, ahol $V \neq \emptyset$ valós vagy komplex vektortér, és $\|\cdot\| : V \to [0,\infty)$ *norma*:

1. $\forall x \in V:\ \|x\| \geq 0$, és $\|x\| = 0 \iff x = 0$;
2. $\forall x \in V,\ c \in \mathbb{R}$ (ill. $\mathbb{C}$): $\|cx\| = |c| \cdot \|x\|$ (homogenitás);
3. $\forall x, y \in V:\ \|x + y\| \leq \|x\| + \|y\|$ (háromszög-egyenlőtlenség).

A $d(x,y) = \|y - x\|$ függvény metrika, tehát minden normált vektortér [[concepts/analiii/metrikus-ter]] is. A megfordítás nem igaz: a diszkrét metrika például nem származik normából.

### Az $L^q$-norma

$0 < q < \infty$ és $x \in \mathbb{R}^p$ esetén

$$\|x\|_q = \bigl(|x_1|^q + \dots + |x_p|^q\bigr)^{1/q}, \qquad \|x\|_\infty = \max\bigl(|x_1|, \dots, |x_p|\bigr).$$

Speciálisan $\|x\|_2 = |x|$ az euklideszi hossz, és $\|x\|_\infty = \lim_{q \to \infty} \|x\|_q$. A gyakorlatban leggyakrabban $L^1$, $L^2$ és $L^\infty$ szerepel.

**Fontos megszorítás:** $\|\cdot\|_q$ csak $q \geq 1$ esetén norma — a háromszög-egyenlőtlenség $0 < q < 1$-re elromlik. Két dimenzióban például

$$\bigl\|(1,1)\bigr\|_q = 2^{1/q} > 2 = \bigl\|(1,0)\bigr\|_q + \bigl\|(0,1)\bigr\|_q.$$

Az $1 \leq q \leq \infty$ esetben a háromszög-egyenlőtlenség sem triviális; ezt a [[concepts/analiii/holder-es-minkowski-egyenlotlenseg]] adja meg.

### Normák $C[a,b]$-n

- $q \geq 1$ esetén $\|f\|_q = \Bigl(\int_a^b |f(t)|^q\, \mathrm{d}t\Bigr)^{1/q}$;
- $\|f\|_\infty = \max |f|$ — a *maximumnorma*, a leggyakoribb; sokszor egyszerűen $\|f\|$-fel jelöljük.

### Sorozatterek

A $\mathbb{K}^n$ végtelen dimenziós megfelelője a $0<p<+\infty$ mellett értelmezett

$$\ell^p := \Bigl\{(x_n):\mathbb{N}\to\mathbb{K} \ :\ \sum_{n=0}^\infty |x_n|^p < +\infty\Bigr\}, \qquad \|x\|_p = \Bigl(\sum_{n=0}^\infty |x_n|^p\Bigr)^{1/p},$$

illetve a korlátos sorozatok $\ell^\infty$ tere a $\|x\|_\infty = \sup\{|x_n| : n\in\mathbb{N}\}$ normával. Ezek $1\leq p\leq+\infty$ esetén mind normált — sőt teljes, azaz Banach- — terek.

### Feladatok

*Forrás: An_III_Gyak_2022_tavasz.pdf 2–3. gyakorlat; gyakorlat.pdf „Metrikus terek" 23–24.*

**Módszer.** Norma ellenőrzése: pozitív definitség, homogenitás, háromszög-egyenlőtlenség. Ha $\|x\|$ lineáris leképezések abszolút értékeinek maximuma, a háromszög-egyenlőtlenség és a homogenitás azonnali, a nulla-tulajdonság pedig azon múlik, hogy a leképezések együtt elválasztanak-e minden nemnulla vektort.

- **Norma ⇒ metrika.** $\rho(x,y)=\|x-y\|$: pozitivitás a norma pozitivitásából, szimmetria $\|-v\|=\|v\|$-ből, háromszög $\|x-z\|\le\|x-y\|+\|y-z\|$.
- **$\|\cdot\|_1,\|\cdot\|_2,\|\cdot\|_\infty$ norma $\mathbb R^n$-en.** $p=1,\infty$: koordinátánként a háromszög-egyenlőtlenség; $p=2$: [[concepts/analiii/holder-es-minkowski-egyenlotlenseg]] (Cauchy–Schwarz ⇒ Minkowski).
- **$\|x\|_\infty=\lim_{p\to\infty}\|x\|_p$.** Mivel $\|x\|_\infty\le\|x\|_p\le n^{1/p}\|x\|_\infty$ és $n^{1/p}\to1$, a rendőrelv adja. $C[a,b]$-n ugyanez: $\|f\|_p\le(b-a)^{1/p}\|f\|_\infty$ felülről; alulról a maximumhely $\delta$-környezetén $|f|\ge\|f\|_\infty-\varepsilon$, így $\|f\|_p\ge(\|f\|_\infty-\varepsilon)(\delta)^{1/p}$.
- **$0<p<1$ nem norma.** $e_1,e_2$ esetén $\|e_1+e_2\|_p=2^{1/p}>2=\|e_1\|_p+\|e_2\|_p$.
- **Házi:** $\|x\|=\max\{|2x_1-x_2|,|4x_1|\}$ norma $\mathbb R^2$-n: két lineáris funkcionál abszolút értékének maximuma, és $\|x\|=0\Rightarrow x_1=0\Rightarrow x_2=0$ (a funkcionálok mátrixának determinánsa $4\neq0$).
- **Egydimenzióban** minden norma $\|x\|=\alpha|x|$ alakú, $\alpha=\|1\|>0$, mert $\|x\|=\|x\cdot 1\|=|x|\,\|1\|$.
- **$C[a,b]$ normái** ($p=1,2,\infty$). A $p=1$ pozitív definitsége: ha $\int|f|=0$ és $f$ folytonos, akkor $f\equiv0$; $p=2$ háromszög-egyenlőtlensége a Minkowski-egyenlőtlenségből.
- **Sorozatterek.** $\ell_1$, $\ell_2$, $\ell_\infty$ lineáris tér és norma: az összeg konvergenciája/korlátossága a $|a+b|\le|a|+|b|$, illetve $(a+b)^2\le2a^2+2b^2$ becslésből jön; az $\ell_2$ háromszög-egyenlőtlensége Minkowski-egyenlőtlenség a részletösszegekre, határátmenettel.
- **Általános következmények.** $\|x_1+\dots+x_n\|\le\sum\|x_i\|$ (indukció) és $\bigl|\|x\|-\|y\|\bigr|\le\|x-y\|$; ebből a **norma folytonos** (Lipschitz-1) függvény $X\to\mathbb R$.
- **Korlátosság normafüggése.** $f_n(x)=2n^2x$ ($0\le x\le\frac1{2n}$), $2n^2(\frac1n-x)$ ($\frac1{2n}\le x\le\frac1n$), $0$ egyébként: $\|f_n\|_1=\frac12$ (háromszög területe), de $\|f_n\|_\infty=n$. Az $\{f_n\}$ halmaz tehát $\|\cdot\|_1$-ben korlátos, $\|\cdot\|_\infty$-ben nem — a két norma nem ekvivalens ([[concepts/analiii/ekvivalens-normak]]).

- **Normált térben nincs gömb, amely nagyobb sugarú valódi részgömböt tartalmaz (2. gyak 6. feladat).** Ha $X\ne\{\theta\}$ és $K_r(a)\subset K_R(b)$, akkor $r\le R$. *$a=b$:* ha $r>R$ volna, lenne $u\in K_R(a)\setminus K_r(a)$ ($r\le\|u-a\|<R$), ami $r<R$-et ad. *$a\ne b$:* az $a$-ból $a-b$ irányba induló $L=\{a+t(a-b):t\ge0\}$ félegyenesen $\varphi(t)\in K_r(a)\iff t<\frac r{\|a-b\|}$, és $\varphi(t)\in K_R(b)\iff t<\frac R{\|a-b\|}-1$; a tartalmazásból $\frac r{\|a-b\|}\le\frac R{\|a-b\|}-1$, azaz $r+\|a-b\|\le R$, tehát $r\le R$. (Metrikus térben ez hamis: [[concepts/analiii/metrikus-ter]] Feladatok.)
- **$p=2$ háromszög-egyenlőtlenség (2. gyak 8. feladat).** $\|x+y\|_2^2\le\|x\|_2^2+2\bigl|\sum x_ky_k\bigr|+\|y\|_2^2\le(\|x\|_2+\|y\|_2)^2$ a Cauchy-egyenlőtlenséggel; $p=1,\infty$ koordinátánként. A $0<p<1$ eset ellenpéldája a sheet szerint $x=(1,0,\dots)$, $y=(0,1,0,\dots)$: $\|x+y\|_p=2^{1/p}>2$ (gyak 2. lap 10. feladata).
- **$\lim_{p\to\infty}\|x\|_p=\|x\|_\infty$ (2. gyak 9. feladat).** $\|x\|_\infty\le\|x\|_p\le n^{1/p}\|x\|_\infty$, $n^{1/p}\to1$, rendőrelv (megegyezik a fenti levezetéssel).

## Kapocs

- [[concepts/analiii/metrikus-ter]] — a norma által indukált metrika alapstruktúrája
- [[concepts/analiii/holder-es-minkowski-egyenlotlenseg]] — az $L^q$-norma háromszög-egyenlőtlenségének bizonyítása
- [[concepts/analiii/ekvivalens-normak]] — véges dimenzióban minden norma ekvivalens
- [[concepts/analiii/cauchy-sorozat-es-teljes-ter]] — a teljes normált tér a Banach-tér
- [[concepts/analiii/skalaris-szorzat-ter]] — a norma erősebb rokona; $\|\cdot\|_p$ csak $p=2$-re származik skaláris szorzatból
- [[concepts/analiii/metrikus-terek-szorzata]] — szorzatnorma véges sok normált tér Descartes-szorzatán
- [[concepts/analiii/vizsgakerdesek-es-bizonyitando-tetelek]] — a témához tartozó megajánlott vizsgajegy- és röpdolgozat-kérdések.
