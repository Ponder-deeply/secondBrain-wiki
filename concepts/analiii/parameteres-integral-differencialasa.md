---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Paraméteres integrál differenciálása

Az integráljel alatti deriválás: mikor szabad a $t$ szerinti deriválást és az $x$ szerinti integrálást felcserélni, azaz mikor igaz, hogy $F'(t) = \int \frac{\partial}{\partial t} f(t,x)\,\mathrm{d}x$.

## Tartalom

### A motiváló példa

$$\int_0^1 \frac{x-1}{\log x}\,\mathrm{d}x = ?$$

Az integrandusnak nincs elemi primitív függvénye. A heurisztika: építsünk **paraméterezett családot**, amelyben a kitevő szabad, deriváljunk a paraméter szerint, és így egy könnyű integrálhoz jussunk. Legyen

$$F(t) = \int_0^1 \frac{x^t - 1}{\log x}\,\mathrm{d}x.$$

Ekkor $F(0) = 0$, és — *ha* szabad felcserélni —

$$F'(t) = \int_0^1 \frac{\partial}{\partial t}\left(\frac{x^t - 1}{\log x}\right)\mathrm{d}x = \int_0^1 x^t\,\mathrm{d}x = \frac{1}{t+1},$$

hiszen $\frac{\partial}{\partial t} x^t = x^t \log x$, és a $\log x$ kiesik. Innen

$$\int_0^1 \frac{x-1}{\log x}\,\mathrm{d}x = F(1) = F(1) - F(0) = \int_0^1 \frac{\mathrm{d}t}{t+1} = \log 2.$$

A kérdés tehát: **milyen feltételekkel szabad az $x$ szerinti integrálást és a $t$ szerinti deriválást felcserélni?**

### A tétel

- **(a)** Legyen $I \subset \mathbb{R}$ nyílt intervallum. Ha $f : I \times [a,b] \to \mathbb{R}$ folytonos, és $\frac{\partial}{\partial t} f(t,x)$ létezik és folytonos, akkor az $F(t) = \int_{x=a}^{b} f(t,x)\,\mathrm{d}x$ paraméteres integrál differenciálható, és

$$F'(t) = \int_{x=a}^{b} \frac{\partial}{\partial t} f(t,x)\,\mathrm{d}x.$$

- **(b)** Tegyük fel, hogy $I \subset \mathbb{R}$ és $(\alpha,\beta) \subset \mathbb{R}$ nyílt intervallumok, $f : I \times (\alpha,\beta) \to \mathbb{R}$ folytonos, az $\int_{x=\alpha}^{\beta} f(t,x)\,\mathrm{d}x$ és az $\int_{x=\alpha}^{\beta} \frac{\partial}{\partial t} f(t,x)\,\mathrm{d}x$ improprius integrál minden $t \in I$-re konvergens, és van olyan $g : (\alpha,\beta) \to [0,\infty)$, amelyre $\int_\alpha^\beta g$ létezik, véges, és $g$ **a $\frac{\partial}{\partial t} f(t,x)$-et dominálja**. Ekkor $F$ differenciálható, és ugyanez a formula érvényes.

Figyelemre méltó, hogy a dominancia itt nem $f$-re, hanem a **parciális deriváltjára** kell.

### Bizonyítás

Válasszunk egy $t_0 \in I$ kezdőpontot, és legyen

$$G(t) = \int_{x=\alpha}^{\beta} \frac{\partial}{\partial t} f(t,x)\,\mathrm{d}x.$$

A folytonossági tétel szerint (a $\frac{\partial}{\partial t} f$-re és annak $g$ domináns függvényére alkalmazva) $G$ folytonos. Bármely $t_1 \in I$-re, az integrálási sorrend felcserélésével és az egyváltozós Newton–Leibniz-formulával:

$$\int_{t_0}^{t_1} G(t)\,\mathrm{d}t = \int_{x=\alpha}^{\beta}\left(\int_{t_0}^{t_1} \frac{\partial}{\partial t} f(t,x)\,\mathrm{d}t\right)\mathrm{d}x = \int_{x=\alpha}^{\beta}\bigl(f(t_1,x) - f(t_0,x)\bigr)\,\mathrm{d}x = F(t_1) - F(t_0).$$

Vagyis $F$ a $G$ függvény **integrálfüggvénye** (egy konstans erejéig). $G$ folytonossági pontjaiban tehát $F' = G$, és mivel $G$ mindenütt folytonos, $F$ az $I$ minden pontjában differenciálható, deriváltja pedig éppen $G(t)$.

A bizonyítás szerkezete tanulságos: nem közvetlenül a differenciahányadossal dolgozik, hanem a deriválást **visszavezeti az integrálásra**, ahol a sorrendcsere már bizonyított.

### Alkalmazás

A bevezető példában $f(t,x) = \frac{x^t-1}{\log x}$, és $\frac{\partial}{\partial t} f(t,x) = x^t$ folytonos, tehát a felcserélés jogos, és $\int_0^1 \frac{x-1}{\log x}\,\mathrm{d}x = \log 2$ valóban helyes.

## Kapocs

- [[concepts/analiii/parameteres-integral]] — a fogalom és a folytonossági tétel; a bizonyítás $G$ folytonosságához ezt használja.
- [[concepts/analiii/parameteres-integral-integralhatosaga]] — a bizonyítás gerince a sorrendcsere.
- [[concepts/analiii/gamma-fuggveny]] — a tétel legfontosabb következménye: a $\Gamma$-függvény differenciálhatósága.
- [[concepts/analii/integralfuggveny]] — a bizonyítás azt mutatja meg, hogy $F$ a $G$ integrálfüggvénye, és onnan örökli a deriváltját.
- [[concepts/analii/newton-leibniz-tetel]] — az egyváltozós formula, amely a belső $t$ szerinti integrált elvégzi.
