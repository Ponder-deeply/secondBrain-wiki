---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Általános vonalintegrál

A valós vonalintegrál kiterjesztése tetszőleges bilineáris szorzásra: a görbe sebességvektorát nem csak skalárisan, hanem bármilyen szorzással szorozhatjuk össze az integrandussal. Ez foglalja egységes keretbe az ívhossz szerinti, a valós, a komplex és az egyes változók szerinti vonalintegrálokat.

## Tartalom

Az integráltételekhez nem elég a skaláris szorzáson alapuló valós vonalintegrál: kelleni fog vektor és skalár szorzata, a háromdimenziós vektoriális szorzás és a komplex szorzás is. Cserébe a definíciót leszűkíthetjük arra az esetre, amelyet ténylegesen használunk: **folytonos** függvényekre és **szakaszonként $C^1$** görbékre.

### Ívhossz szerinti integrál

Legyen $G \subset \mathbb{R}^p$ összefüggő, nyílt, $\gamma : [a,b] \to G$ szakaszonként $C^1$ görbe, $f : G \to \mathbb{R}$ folytonos. Az $f$ *ívhossz szerinti integrálja* a $\gamma$ görbén

$$\int_\gamma f\,\mathrm{d}s = \int_a^b f(\gamma(t))\,|\dot\gamma(t)|\,\mathrm{d}t,$$

jelölése $\int_\gamma f\,\mathrm{d}s$ vagy $\int_\gamma f(x)\,|\mathrm{d}x|$. Vektorértékű $f : G \to \mathbb{R}^q$ ívhossz szerinti integrálját koordinátánként számoljuk.

Itt $|\dot\gamma(t)|$ szerepel, nem maga a sebességvektor: az integrál ezért nem függ a görbe irányításától, és $f \equiv 1$ mellett éppen a görbe ívhosszát adja.

### Az általános definíció

Legyen ezen felül

$$* : \mathbb{R}^q \times \mathbb{R}^p \to \mathbb{R}^r$$

bilineáris függvény, azaz „valamilyen szorzás", és $f : G \to \mathbb{R}^q$ folytonos. Ekkor

$$\int_\gamma f(\mathbf{x}) * \mathrm{d}\mathbf{x} = \int_{t=a}^{b} \bigl( f(\gamma(t)) * \dot\gamma(t) \bigr)\,\mathrm{d}t .$$

Ha $r > 1$, akkor az integrandus és az integrál is $r$-dimenziós vektor, és minden koordinátában a szorzat megfelelő koordinátáját kell integrálni.

### Speciális esetek

| $p$ | $q$ | $r$ | $*$ | Az integrál neve |
|---|---|---|---|---|
| $1$ | $1$ | $1$ | valós szorzás, $\gamma(t)=t$ | egyváltozós Riemann-integrál |
| $p$ | $p$ | $1$ | skaláris szorzás | valós vonalintegrál |
| $2$ | $2$ | $2$ | komplex szorzás | komplex vonalintegrál |
| $p$ | $1$ | $1$ | szorzás a $\dot\gamma_i$ komponenssel | $x_i$ változó szerinti vonalintegrál |

Az utolsó eset explicit alakja

$$\int_\gamma f(\mathbf{x})\,\mathrm{d}x_i = \int_a^b f(\gamma(t))\,\dot\gamma_i(t)\,\mathrm{d}t .$$

### Visszavezetés a változók szerinti integrálokra

**Mindegyik** vonalintegrál felírható az egyes változók szerinti vonalintegrálok lineáris kombinációjaként — ez teszi a fogalmat gyakorlatilag kiszámíthatóvá:

$$\int_\gamma \langle f(\mathbf{x}), \mathrm{d}\mathbf{x}\rangle = \sum_{i=1}^p \int_\gamma f_i(\mathbf{x})\,\mathrm{d}x_i,$$

$$\int_\gamma f(\mathbf{x})\cdot \mathrm{d}\mathbf{x} = \left( \int_\gamma f_1\,\mathrm{d}x - \int_\gamma f_2\,\mathrm{d}y,\ \int_\gamma f_2\,\mathrm{d}x + \int_\gamma f_1\,\mathrm{d}y \right) \quad \text{(komplex szorzás)} .$$

### Példa: az $f(z) = z$ integrálja az egységkörvonalon

Legyen $\gamma(t) = (\cos t, \sin t)$, $0 \le t \le 2\pi$, tehát $\dot\gamma(t) = (-\sin t, \cos t)$, azaz $\mathrm{d}x = -\sin t\,\mathrm{d}t$ és $\mathrm{d}y = \cos t\,\mathrm{d}t$; koordinátás alakban $f(x,y) = (x, -y)$. A négy alapintegrál:

$$\int_\gamma x\,\mathrm{d}x = \int_0^{2\pi}\cos t\,(-\sin t)\,\mathrm{d}t = 0, \qquad \int_\gamma x\,\mathrm{d}y = \int_0^{2\pi}\cos^2 t\,\mathrm{d}t = \pi,$$

$$\int_\gamma (-y)\,\mathrm{d}x = \int_0^{2\pi}\sin^2 t\,\mathrm{d}t = \pi, \qquad \int_\gamma (-y)\,\mathrm{d}y = \int_0^{2\pi}(-\sin t)\cos t\,\mathrm{d}t = 0 .$$

Ezekből a komplex vonalintegrál $(0-0;\ \pi+\pi) = (0, 2\pi)$, azaz

$$\int_{|z|=1} z\,\mathrm{d}z = 2\pi i .$$

## Kapocs

- [[concepts/analiii/valos-vonalintegral]] — a skaláris szorzáshoz tartozó speciális eset, ebből általánosítunk
- [[concepts/analiii/sikvektorok-keresztszorzata]] — további bilineáris szorzás, amivel a síkbeli integráltételeket írjuk fel
- [[concepts/analiii/korulfordulasi-szam]] — vonalintegrállal felírt topológiai mennyiség
- [[concepts/analii/ivhossz]] — az ívhossz egyváltozós fogalma, amelyet az ívhossz szerinti integrál általánosít
- [[concepts/analii/newton-leibniz-tetel]] — a $p=q=r=1$ eset, minden integráltétel őse
