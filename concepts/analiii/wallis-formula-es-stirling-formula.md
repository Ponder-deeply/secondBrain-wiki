---
tags: [concept]
sources: [An_III_Gyak_2022_tavasz.pdf]
derivation: source
kind: theorem
element: fire
updated: 2026-10-21
---

# Wallis- és Stirling-formula

A Wallis-formula a $\pi/2$-t végtelen szorzatként adja meg; a $G_n=\int_0^\infty x^n e^{-x^2}\,\mathrm{d}x$ integrálok rekurziójával együtt ez ad egy elemi bizonyítást a Gauss-integrálra, és a Stirling-formula levezetésének is ez a kulcsa.

## Tartalom

### Wallis-formula

$$\lim_{n\to\infty} \frac{2^2}{1^2}\cdot\frac{4^2}{3^2}\cdots\frac{(2n)^2}{(2n-1)^2}\cdot\frac{1}{2n+1} = \frac{\pi}{2}.$$

Ekvivalens alakja: $\dfrac{2\cdot4\cdots(2n)}{1\cdot3\cdots(2n-1)}\cdot\dfrac{1}{\sqrt{2n+1}} \to \sqrt{\pi/2}$.

### A Gauss-integrál a $G_n$ rekurzióval

Legyen $G_n=\int_0^\infty x^n e^{-x^2}\,\mathrm{d}x$ ($n=0,1,2,\dots$). A gyakorlati útmutató lépései:

1. Az integrálok konvergensek (majoráns: $e^{-x^2}\le e^{-x}$ az $[1,\infty)$-en). $G_1=\tfrac12$, és parciális integrálással $G_n=\dfrac{n-1}{2}G_{n-2}$ ($n\ge2$). Ebből $G_{2n}$ és $G_{2n+1}$ zárt alakban kifejezhető $G_0$-lal, illetve $G_1$-gyel.
2. **Cauchy–Schwarz-trükk:** a $G_{n-1}t^2+2G_nt+G_{n+1}=\int_0^\infty x^{n-1}(t+x)^2e^{-x^2}\mathrm{d}x>0$ polinom diszkriminánsa negatív, tehát $G_n^2<G_{n-1}G_{n+1}$.
3. Ebből $\frac{2}{2n+1}G_{2n+1}^2<G_{2n}^2<G_{2n-1}G_{2n+1}$; a rekurzióval kifejezve a Wallis-szorzat egy $G_0^2$-es kifejezés közrefogásába kerül.
4. A Wallis-formulát alkalmazva $G_0^2=\pi/4$, vagyis $\int_0^\infty e^{-x^2}\mathrm{d}x=\sqrt{\pi}/2$.

Ez a polárkoordinátás bizonyítás elemi, egyváltozós alternatívája: [[concepts/analiii/gauss-integral]].

### Stirling-formula

$$n!\sim\sqrt{2\pi n}\left(\frac{n}{e}\right)^n\qquad\Longleftrightarrow\qquad \lim_{n\to\infty}\frac{n!}{\left(\frac ne\right)^n\sqrt{2\pi n}}=1.$$

**Bizonyítás vázlata (gyakorlati jegyzet).**

- $\int_1^n\ln x\,\mathrm{d}x=n\ln n-n+1=\ln\!\bigl(e(n/e)^n\bigr)$.
- A konkáv $\ln$ grafikonjába írt törtvonal alatti terület (háromszög és $n-1$ trapéz) $\ln\frac{n!}{\sqrt n}$. A két terület különbsége $\triangle_n=\ln\dfrac{e\,(n/e)^n\sqrt n}{n!}>0$, monoton nő és felülről korlátos ($\le\frac{\ln2}{2}$), tehát konvergens.
- Így $a_n=\dfrac{n!}{(n/e)^n\sqrt n}$ is konvergens, határértéke pozitív. Mivel $\lim a_n=\lim a_{2n}$, ezért $\lim a_n=\lim\dfrac{a_n^2}{a_{2n}}$.
- Kiszámolva $\dfrac{a_n^2}{a_{2n}}=\dfrac{2\cdot4\cdots(2n)}{1\cdot3\cdots(2n-1)}\cdot\dfrac{1}{\sqrt{2n+1}}\cdot\sqrt{\dfrac{2(2n+1)}{n}}$, ami a Wallis-formula miatt $\sqrt{\pi/2}\cdot2=\sqrt{2\pi}$-hez tart.

### Kapcsolódó gyakorlófeladatok

- Normális eloszlás: $f(x)=\frac{1}{\sigma\sqrt{2\pi}}e^{-(x-\mu)^2/2\sigma^2}$ esetén $\int f=1$, $\int xf=\mu$, $\int(x-\mu)^2f=\sigma^2$ — a $\sqrt{\pi}$-s Gauss-integrálból, helyettesítéssel és a $G_1$, $G_2$ értékekkel.
- Exponenciális eloszlás: $\int_0^\infty\lambda e^{-\lambda x}\mathrm{d}x=1$; $\int_0^\infty(x-\tfrac1\lambda)^2\lambda e^{-\lambda x}\mathrm{d}x=\tfrac1{\lambda^2}$.
- $\int_{-\infty}^{\infty}\frac{x}{1+x^2}\mathrm{d}x$ divergens, bár $\lim_{b\to\infty}\int_{-b}^b\frac{x}{1+x^2}=0$: az improprius integrál két külön határértékkel értelmezett ([[concepts/analii/improprius-integral]]).

## Kapocs

- [[concepts/analiii/gauss-integral]] — a $G_0$ értékének másik bizonyítása.
- [[concepts/analiii/gamma-fuggveny]] — $G_n=\tfrac12\Gamma\!\left(\tfrac{n+1}{2}\right)$ az $x^2=t$ helyettesítéssel; $n!=\Gamma(n+1)$ a Stirling-formula tárgya.
- [[concepts/analii/improprius-integral]] — konvergenciakritériumok, integrálkritérium.
- [[concepts/analii/hatarozott-integral-parcialisintegrals]] — a $G_n$ rekurzió parciális integrálással.
