---
tags: [concept]
sources: [02_ea_An3_2022_tavasz.pdf]
derivation: source
updated: 2026-09-14
---

# Bolzano–Weierstrass-féle kiválasztási tétel normált terekben

$\mathbb{R}^n$-ben minden korlátos sorozatnak van konvergens részsorozata, de ez a tulajdonság **nem** öröklődik automatikusan tetszőleges normált térre: végtelen dimenzióban van korlátos, konvergens részsorozat nélküli sorozat. A tétel érvényessége tehát pontosan a véges dimenzióhoz kötődik.

## Tartalom

### A tétel $\mathbb{R}^n$-ben

**Tétel.** $(\mathbb{R}^n, \|\cdot\|_\infty)$ normált térben minden korlátos sorozatnak van konvergens részsorozata.

A bizonyítás a koordinátasorozatokra alkalmazza egymás után az egydimenziós [[concepts/analiii/cantor-metszettetel|Bolzano–Weierstrass-tételt]]: minden koordináta szerint kiválasztjuk az előző részsorozat egy konvergens rész-részsorozatát, és a végén az összes koordinátasorozat egyszerre konvergens lesz. Mivel $\mathbb{R}^n$-en minden norma ekvivalens (ld. [[concepts/analiii/ekvivalens-normak]]), a tétel bármelyik normával fogalmazva igaz.

**Tyihonov-tétel.** Tetszőleges véges dimenziós $X$ lineáris téren bármely két norma ekvivalens egymással. Mivel minden $n$-dimenziós $X$ lineáris tér algebrailag izomorf $\mathbb{R}^n$-nel, ebből következik, hogy $(X, \|\cdot\|)$ normált tér minden korlátos sorozatának van konvergens részsorozata.

### A tétel általában hamis végtelen dimenzióban

**Példa.** Legyen $f_k(x) := \sin(2^k\pi x)$ ($x\in[0,1]$, $k\in\mathbb{N}$). Ekkor $(f_k)$ korlátos sorozat a $\bigl(C[0,1], \|\cdot\|_\infty\bigr)$ normált térben ($\|f_k\|_\infty \leq 1$ minden $k$-ra), de nincs konvergens részsorozata.

*Bizonyítás.* Legyen $k<l$ és $x^* := \dfrac{1}{2^{k+1}}$. Ekkor

$$f_k(x^*) = \sin\Bigl(2^k\pi\cdot\tfrac{1}{2^{k+1}}\Bigr) = \sin\tfrac{\pi}{2} = 1, \qquad f_l(x^*) = \sin\Bigl(2^l\pi\cdot\tfrac{1}{2^{k+1}}\Bigr) = \sin\bigl(2^{l-k-1}\pi\bigr) = 0,$$

hiszen $l-k-1 \in \mathbb{N}$ egész. Tehát

$$\|f_k - f_l\|_\infty = \max_{x\in[0,1]} |f_k(x)-f_l(x)| \geq |f_k(x^*)-f_l(x^*)| = 1 \qquad (k\neq l).$$

Ha $(f_{\nu_k})$ konvergens részsorozat lenne, egy $f\in C[0,1]$ függvényhez tartana; ekkor $\|f_{\nu_k}-f_{\nu_l}\|_\infty \leq \|f_{\nu_k}-f\|_\infty + \|f_{\nu_l}-f\|_\infty < 2\varepsilon$ állna elő elég nagy indexekre, ami ellentmond a fenti $\geq 1$ becslésnek. $\blacksquare$

### Következmény

A Bolzano–Weierstrass-féle kiválasztási tétel tehát nem topológiai, hanem **dimenziófüggő** jelenség: $\mathbb{R}^n$-ben (és minden véges dimenziós normált térben) mindig igaz, végtelen dimenziós normált terekben általában nem. Ez rokon azzal a ténnyel, hogy $\bigl(C[0,1],\|\cdot\|_1\bigr)$ [[concepts/analiii/cauchy-sorozat-es-teljes-ter|nem Banach-tér]]: mindkettő azt mutatja, hogy a véges dimenziós $\mathbb{R}^n$-ből ismert kompaktsági és teljességi jelenségek végtelen dimenzióban nem automatikusak, külön kell igazolni vagy megcáfolni őket.

## Kapocs

- [[concepts/analiii/cantor-metszettetel]] — az egydimenziós Bolzano–Weierstrass-tétel és $\mathbb{R}^p$-beli általánosítása, amelyre ez a tétel épül
- [[concepts/analiii/ekvivalens-normak]] — a véges dimenziós normaekvivalencia, amely a Tyihonov-tétel bizonyításának kulcslépése
- [[concepts/analiii/cauchy-sorozat-es-teljes-ter]] — a rokon jelenség: $C[a,b]$ teljessége is normafüggő
- [[concepts/analiii/normalt-vektorter]] — a $C[a,b]$ tér és a maximumnorma, amelyben az ellenpélda él
- [[concepts/analiii/kompaktsag-ekvivalens-jellemzesei]] — a sorozatos kompaktság általános metrikus téri fogalma, amelynek ez a tétel az $\mathbb{R}^n$-beli speciális esete
