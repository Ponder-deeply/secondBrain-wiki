---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Kettős integrálok felcserélhetősége

Folytonos függvény esetén a két integrálási sorrend ugyanazt adja, de általában nem: van olyan függvény, amelyre mindkét kettős integrál létezik és különbözik, és olyan is, amelyre az egyik sorrend értelmetlen.

## Tartalom

### A „rózsaszínű álom"

Szeretnénk, hogy mindig fennálljon

$$\int_{[a,b]\times[c,d]} f(x,y)\,\mathrm{d}x\mathrm{d}y = \int_{y=c}^{d}\left(\int_{x=a}^{b} f(x,y)\,\mathrm{d}x\right)\mathrm{d}y = \int_{x=a}^{b}\left(\int_{y=c}^{d} f(x,y)\,\mathrm{d}y\right)\mathrm{d}x,$$

sőt a téglán vett integrál közbeiktatása nélkül is szabadon szeretnénk többszörös integrálokat csereberélni. Ez a **Petruska-elv** egyik esete: bármilyen két, egymás utáni operációt fel kell cserélni, és többszörös operáció esetén ki kell találni a jó sorrendet. Rokon példák: a Jensen-egyenlőtlenség (átlagolás és behelyettesítés), összeg tagonkénti deriválása vagy integrálása, a vegyes parciális deriváltak Young-tétele, kettős szummák, valamint a paraméteres integrálok deriválása — például a $\Gamma(s) = \int_0^\infty x^{s-1}e^{-x}\mathrm{d}x$ függvényre $\Gamma'(s) = \int_0^\infty x^{s-1}(\log x)e^{-x}\mathrm{d}x$.

### A pozitív eredmény

**Következmény (az integrálok felcserélhetősége).** Ha $f : [a,b]\times[c,d] \to \mathbb{R}$ folytonos, akkor

$$\int_{x=a}^{b}\left(\int_{y=c}^{d} f(x,y)\,\mathrm{d}y\right)\mathrm{d}x = \int_{y=c}^{d}\left(\int_{x=a}^{b} f(x,y)\,\mathrm{d}x\right)\mathrm{d}y.$$

Ez a [[concepts/analiii/lebontasi-tetel]] közvetlen következménye: folytonos függvény a kompakt téglán integrálható, tehát mindkét kettős integrál a $\int_C f$ értékkel egyenlő. A felcserélhetőség tehát **nem önálló tétel, hanem az együttes integrálhatóság következménye**.

### Ellenpélda: mindkét kettős integrál létezik, de különböznek

$$f(x,y) = \begin{cases} \dfrac{x-y}{(x+y)^3} & \text{ha } x,y > 0, \\[4pt] 0 & \text{ha } x\leq 0 \text{ vagy } y\leq 0. \end{cases}$$

Ha $x > 0$:

$$\int_{y=0}^{1} f(x,y)\,\mathrm{d}y = \int_{y=0}^{1}\left(\frac{2x}{(x+y)^3} - \frac{1}{(x+y)^2}\right)\mathrm{d}y = \left[\frac{y}{(x+y)^2}\right]_{y=0}^{1} = \frac{1}{(x+1)^2},$$

így

$$\int_{x=0}^{1}\left(\int_{y=0}^{1} f(x,y)\,\mathrm{d}y\right)\mathrm{d}x = \int_{x=0}^{1}\frac{\mathrm{d}x}{(x+1)^2} = \frac{1}{2},$$

miközben szimmetrikus számolással

$$\int_{y=0}^{1}\left(\int_{x=0}^{1} f(x,y)\,\mathrm{d}x\right)\mathrm{d}y = -\frac{1}{2}.$$

A függvény tehát a $[0,1]^2$ téglán **nem** integrálható — nem korlátos az origó közelében.

### Ellenpélda: az egyik sorrend értelmetlen

Legyen $f(x,y) = D(x)\cdot R(y)$, ahol $D$ a Dirichlet-függvény,

$$D(x) = \begin{cases} 1 & \text{ha } x\in\mathbb{Q}, \\ 0 & \text{ha } x\notin\mathbb{Q}, \end{cases}$$

és $R$ a Riemann-függvény ($R(p/q) = 1/q$ relatív prím $p,q$-ra, $R(x) = 0$ irracionális $x$-re). Mivel $\int_0^1 R = 0$,

$$\int_{x=0}^{1}\left(\int_{y=0}^{1} f(x,y)\,\mathrm{d}y\right)\mathrm{d}x = \int_{x=0}^{1} D(x)\cdot 0\,\mathrm{d}x = 0.$$

A másik sorrendben viszont racionális $y$ esetén $\int_{x=0}^{1} D(x)R(y)\,\mathrm{d}x$ nem létezik (a Dirichlet-függvény nem integrálható), ezért a külső integrál nem is értelmes.

Jó házi feladat olyan példát keresni, ahol mindkét kettős integrál létezik, különböznek, és ráadásul $f \geq 0$.

## Kapocs

- [[concepts/analiii/lebontasi-tetel]] — a felcserélhetőség egyetlen forrása; ellenpélda csak ott lehet, ahol az együttes integrálhatóság sérül
- [[concepts/analiii/szukcessziv-integralas]] — a sorrendcsere gyakorlati alkalmazása
- [[concepts/analiii/tobbvaltozos-integralhatosag]] — a Dirichlet-függvény nem integrálhatósága és a Riemann-függvény integrálhatósága innen érthető
- [[concepts/analii/riemann-fuggveny]] — az ellenpéldában szereplő $R$ egyváltozós tárgyalása: integrálható, de végtelen sok pontban szakad
