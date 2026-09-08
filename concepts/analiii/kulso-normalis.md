---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Külső normális és a $\mathbf{t}\,\mathrm{d}s$, $\mathbf{n}\,\mathrm{d}s$ jelölések

Pozitív irányítású síkgörbén az érintő egységvektor $-90^\circ$-os elforgatottja a kifelé mutató normális. A hozzá tartozó jelölésrendszer teszi egysoros képletté a síkbeli integráltételeket.

## Tartalom

### Sebesség-, érintő- és normálvektor

Legyen $\gamma(t) = \bigl(x(t), y(t)\bigr)$ szakaszonként $C^1$ görbe. A *sebességvektora* a $t$ időpontban $\dot\gamma(t) = (\dot x(t), \dot y(t))$. Ha ez nem a nullvektor, akkor az *érintővektor* (érintő egységvektor)

$$\mathbf{t} = \frac{\dot\gamma(t)}{|\dot\gamma(t)|} = \frac{(\dot x, \dot y)}{\sqrt{\dot x^2 + \dot y^2}},$$

ennek $(-90^\circ)$-kal elforgatottja pedig a **külső normális**:

$$\mathbf{n} = \frac{(\dot y, -\dot x)}{\sqrt{\dot x^2 + \dot y^2}} .$$

A $-90^\circ$ nem önkényes: pozitív (az óramutató járásával ellentétes) irányítású határgörbén a haladási irányhoz képest jobbra van a tartomány külseje, tehát éppen ez a vektor mutat kifelé.

### A differenciáljelölések

- Ívhossz szerinti integráloknál: $\mathrm{d}\mathbf{s} = \mathrm{d}\mathbf{x}$ és $\mathrm{d}s = |\mathrm{d}\mathbf{x}|$.
- Terület szerinti integráloknál: $\mathrm{d}A = \mathrm{d}x\,\mathrm{d}y$.

A szokásos helyettesítésekkel a görbén

$$\mathbf{t}\,\mathrm{d}s = \begin{pmatrix}\mathrm{d}x\\ \mathrm{d}y\end{pmatrix}, \qquad \mathbf{n}\,\mathrm{d}s = \begin{pmatrix}\mathrm{d}y\\ -\mathrm{d}x\end{pmatrix} .$$

Ez a két azonosság a síkbeli integráltételek fordítókulcsa: bármelyik tétel „geometriai" alakja ($\mathbf{t}$-vel vagy $\mathbf{n}$-nel) ezekkel írható át a Green-tétel közvetlenül kezelhető $\mathrm{d}x$, $\mathrm{d}y$ szerinti alakjára, és vissza. A $\mathbf{t}$-vel felírt integrálok a **cirkulációt**, az $\mathbf{n}$-nel felírtak a **fluxust** mérik.

### Egy dimenzióban

A jelölés egydimenziós megfelelője is értelmes: egy $f : [a,b]\to\mathbb{R}$ függvénynél a „határ" két, egységnyi súlyú pontból áll, és a kifelé mutató normálvektor a felső végpontban $+1$, az alsóban $-1$. Ezért

$$\int_{[a,b]} f'(x)\,\mathrm{d}x = f(a)\cdot(-1) + f(b)\cdot(+1),$$

ami éppen a Newton–Leibniz formula — a külső normális tehát az, ami a végpontok előjelezését magasabb dimenzióra általánosítja.

## Kapocs

- [[concepts/analiii/newton-leibniz-formula-tobbvaltozos]] — az $\mathbf{n}\,\mathrm{d}s$ jelöléssel felírt síkbeli formula
- [[concepts/analiii/gauss-osztrogradszkij-tetel]] — a fluxus felírása külső normálissal
- [[concepts/analiii/stokes-tetel]] — a cirkuláció felírása érintővektorral
- [[concepts/analiii/jordan-gorbetetel]] — a pozitív irányítás, amelyre a „külső" jelző hivatkozik
- [[concepts/analii/newton-leibniz-tetel]] — az egydimenziós eset
