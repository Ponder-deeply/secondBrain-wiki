---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Vonalintegrál homotóp görbéken

Ha egy folytonos vektormezőnek lokálisan létezik primitív függvénye, akkor homotóp görbéken a vonalintegrálja megegyezik, nullhomotóp zárt görbén pedig nulla.

## Tartalom

### A tétel

**Tétel.** Legyen $G \subset \mathbb{R}^p$ összefüggő, nyílt, $f : G \to \mathbb{R}^p$ folytonos vektormező, amelynek **lokálisan létezik primitív függvénye**, vagyis $G$ minden pontja körül egy környezetben $f$-nek van primitív függvénye. Ekkor

- **(a)** Ha $\gamma_0$ és $\gamma_1$ közös kezdő- és végpontú, $G$-ben homotóp, szak.$C^1$ görbék, akkor $\int_{\gamma_0} f = \int_{\gamma_1} f$.
- **(b)** Ha $\gamma_0$ és $\gamma_1$ zárt, $G$-ben homotóp, szak.$C^1$ görbék, akkor $\int_{\gamma_0} f = \int_{\gamma_1} f$.
- **(c)** Ha $\gamma$ zárt, $G$-ben nullhomotóp, szak.$C^1$ görbe, akkor $\int_\gamma f = 0$.

A (c) állítás a (b) speciális esete (a konstans görbén az integrál nyilván $0$).

A feltétel — *lokálisan* van primitív függvény — pontosan az, amit differenciálható, rotációmentes mezőre a Goursat-lemma következményei szolgáltatnak. A tétel tehát a lokális információt globálissá alakítja, feltéve, hogy a tartomány topológiája ezt megengedi.

### Bizonyítás (a) és (b)

Legyen $H : [0,1]\times[0,1] \to G$ a homotópia.

**Rácsfelosztás.** A $H$ képe, $K$, kompakt; van olyan $r > 0$, hogy $K$ bármely pontjának $r$ sugarú környezete $G$-ben van. A $H$ egyenletesen folytonos, ezért van olyan $n$ pozitív egész, hogy bármely $t,t',u,u' \in [0,1]$, $|t - t'| \leqslant \frac{1}{n}$, $|u - u'| \leqslant \frac{1}{n}$ esetén

$$\bigl|H(t,u) - H(t',u')\bigr| < r.$$

Osszuk a $[0,1]\times[0,1]$ négyzetet $n\times n$ részre, és legyen $0 \leqslant k,\ell \leqslant n$ esetén $a_{k,\ell} = H\!\left(\frac{k}{n}, \frac{\ell}{n}\right)$.

**Cellánként nulla.** Az $[a_{k,\ell}\,a_{k+1,\ell}\,a_{k+1,\ell+1}\,a_{k,\ell+1}\,a_{k,\ell}]$ zárt töröttvonal (egy „rácscella" négyszöge) a $B(a_{k,\ell}, r)$ gömbben fekszik, ahol $f$-nek van primitív függvénye, tehát ezen a zárt töröttvonalon a vonalintegrálja $0$.

**Teleszkopikus összegzés.** Adjuk össze az összes cellát. A belső élek mindegyikét két szomszédos cella ellenkező irányban járja be, ezért kiesnek; csak a nagy négyzet peremén futó élek maradnak:

$$0 = \sum_{k=0}^{n-1}\sum_{\ell=0}^{n-1}\int_{[a_{k,\ell}a_{k+1,\ell}a_{k+1,\ell+1}a_{k,\ell+1}a_{k,\ell}]} f = \int_{\gamma_0} f - \int_{\gamma_1} f + \sum_{\ell=0}^{n-1}\left(\int_{[a_{n,\ell}a_{n,\ell+1}]} f - \int_{[a_{0,\ell}a_{0,\ell+1}]} f\right).$$

Az alsó és a felső perem adja a $\gamma_0$, illetve a $-\gamma_1$ menti integrált (pontosabban azok töröttvonal-közelítéseit, amelyeken az integrál a lokális primitív függvények miatt megegyezik a görbe menti integrállal).

Az utolsó zárójel eltűnik:

- **közös végpontú görbék** esetén a két oldalsó perem mindkét szakasza egy-egy **pont** (a homotópia rögzíti a végpontokat);
- **zárt görbék** esetén a két oldalsó perem **ugyanaz** a szakasz (mert $H(0,u) = H(1,u)$), és ellenkező irányban van bejárva.

Mindkét esetben $\int_{\gamma_0} f = \int_{\gamma_1} f$.

### A bizonyítás gondolata

A homotópia egy „négyzetet" fektet a tartományba; ezt olyan apró cellákra vágjuk, hogy mindegyik beleférjen egy gömbbe, ahol már van primitív függvény, tehát ott a Newton–Leibniz-formula működik. A cellák összegzésekor a belső élek kiejtik egymást — pontosan ugyanaz a mechanizmus, mint a Goursat-lemmában a középvonalak kiejtésénél.

## Kapocs

- [[concepts/analiii/homotop-gorbek]] — a tétel feltételében szereplő deformáció fogalma.
- [[concepts/analiii/primitiv-fuggveny-csillagszeru-tartomanyon]] — a lokális primitív függvény létezése, a tétel feltétele.
- [[concepts/analiii/egyszeresen-osszefuggo-tartomany]] — a tétel közvetlen alkalmazása.
- [[concepts/analiii/goursat-lemma]] — a belső élek kiejtésének mintája.
- [[concepts/analiii/valos-vonalintegral]] — az additivitás, amelyre az összegzés épül.
