---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Konzervatív vektormező

Folytonos vektormezőre a primitív függvény létezése, a vonalintegrál úttól való függetlensége és a zárt görbéken vett nulla vonalintegrál ekvivalens; az ilyen mezőt konzervatívnak nevezzük.

## Tartalom

### A nagy ekvivalenciatétel

**Tétel (a primitív függvény létezésének feltételei).** Legyen $G \subset \mathbb{R}^p$ **összefüggő, nyílt**, $f : G \to \mathbb{R}^p$ **folytonos**. Az alábbiak ekvivalensek:

- **(a)** $f$-nek van primitív függvénye: van olyan differenciálható $F : G \to \mathbb{R}$, amelyre $f = \operatorname{grad} F$.
- **(b1)** $G$-ben fekvő, közös végpontú, szak.$C^1$ görbéken $f$ vonalintegrálja egyenlő.
- **(b2)** $f$ vonalintegrálja $0$ minden $G$-beli zárt, szak.$C^1$ görbén.
- **(c1)** $G$-ben fekvő, közös végpontú **töröttvonalakon** $f$ vonalintegrálja egyenlő.
- **(c2)** $f$ vonalintegrálja $0$ minden $G$-beli zárt **töröttvonalon**.

**Definíció (konzervatív vektormező).** Az $f$ vektormező **konzervatív**, ha a fenti (egymással ekvivalens) tulajdonságokat teljesíti.

A (c) verziók haszna gyakorlati: a későbbi bizonyításokban elég **töröttvonalakat** vizsgálni, ami sokkal kezelhetőbb, mint az összes szak.$C^1$ görbe — és a tétel garantálja, hogy ezzel semmit nem veszítünk.

### Segédállítás: konstans mező vonalintegrálja

**Trivialitás.** Ha $f \in \mathbb{R}^p$ konstans vektormező és $\gamma$ folytonos görbe $x$ kezdő- és $y$ végponttal, akkor $\int_\gamma f = \langle f; y - x\rangle$.

*Bizonyítás.* Bármely felosztásra az integrálközelítő összeg teleszkopikusan összecsúszik:

$$\sum_{i=1}^{n}\bigl\langle f; \gamma(t_i) - \gamma(t_{i-1})\bigr\rangle = \Bigl\langle f; \sum_{i=1}^{n}\bigl(\gamma(t_i)-\gamma(t_{i-1})\bigr)\Bigr\rangle = \bigl\langle f; \gamma(b)-\gamma(a)\bigr\rangle.$$

### A bizonyítás

**(a) $\Rightarrow$ (b1).** Triviális a Newton–Leibniz-formulából: ha $\gamma_1(a) = \gamma_2(a)$ és $\gamma_1(b) = \gamma_2(b)$, akkor

$$\int_{\gamma_1} f = F(\gamma_1(b)) - F(\gamma_1(a)) = F(\gamma_2(b)) - F(\gamma_2(a)) = \int_{\gamma_2} f.$$

**(b1) $\Rightarrow$ (b2).** Ha $\gamma : [0,1] \to G$ zárt szak.$C^1$ görbe, legyen $\gamma_1$ a $\gamma(0) = \gamma(1)$ pontba tartó **konstans** görbe. A két görbe kezdő- és végpontja közös, tehát $\int_\gamma f = \int_{\gamma_1} f = 0$.

**(b2) $\Rightarrow$ (b1).** Legyen $\gamma_1, \gamma_2$ közös kezdő- és végpontú. Fűzzük egymás után $\gamma_1$-et és $\gamma_2$ **megfordítását** ($\overline{\gamma_2}$); az így kapott $\gamma_3$ zárt görbe. Az additivitás és a megfordítás előjelváltása szerint

$$0 = \int_{\gamma_3} f = \int_{\gamma_1} f + \int_{\overline{\gamma_2}} f = \int_{\gamma_1} f - \int_{\gamma_2} f.$$

**(c1) $\Leftrightarrow$ (c2).** Ugyanaz a két lépés, töröttvonalakra.

**(b1) $\Rightarrow$ (c1)** és **(b2) $\Rightarrow$ (c2).** Triviális, hiszen minden töröttvonal egyben szak.$C^1$ görbe is.

**(c1) $\Rightarrow$ (a) — a primitív függvény megkonstruálása.** Rögzítsünk egy $x_0 \in G$ kezdőpontot. Mivel $G$ összefüggő és nyílt, bármely $x \in G$-hez létezik $G$-ben olyan $\gamma$ töröttvonal, amelynek kezdőpontja $x_0$, végpontja $x$. Definiáljuk:

$$F(x) = \int_\gamma f.$$

A (c1) tulajdonság szerint mindegy, melyik töröttvonalat választjuk — ezért $F$ **jóldefiniált**.

Igazoljuk, hogy $\operatorname{grad} F(x) = f(x)$. Legyen $\varepsilon > 0$ és $x \in G$. Mivel $x$ belső pont és $f$ folytonos $x$-ben, van olyan $\delta > 0$, hogy $B(x,\delta) \subset G$, és $y \in B(x,\delta)$ esetén $|f(y) - f(x)| < \varepsilon$.

Ha $\gamma$ összeköti $x_0$-t $x$-szel, akkor $\gamma$-hoz az $[x,y]$ szakaszt hozzáfűzve $x_0$-t $y$-nal összekötő töröttvonalat kapunk, tehát

$$F(y) - F(x) = \int_{z \in [x,y]}\bigl\langle f(z); \mathrm{d}z\bigr\rangle = \bigl\langle f(x); y-x\bigr\rangle + \int_{z\in[x,y]}\bigl\langle f(z) - f(x); \mathrm{d}z\bigr\rangle,$$

ahol az első tagot a konstans mezőről szóló trivialitás adta. A maradéktagra a triviális becslés:

$$\Bigl|F(y) - F(x) - \bigl\langle f(x); y-x\bigr\rangle\Bigr| \leqslant \max_{z\in[x,y]}\bigl|f(z)-f(x)\bigr|\cdot|y-x| < \varepsilon\cdot|y-x|.$$

Tehát minden $\varepsilon > 0$-hoz van $\delta > 0$, hogy minden $y \in B(x,\delta)$-ra a fenti becslés áll, ami pontosan azt jelenti, hogy $F$ differenciálható $x$-ben, és $\operatorname{grad} F(x) = f(x)$.

### Megjegyzés

A konstrukció szépsége, hogy a primitív függvényt magukból a vonalintegrálokból építi fel — ugyanaz a gondolat, mint az egyváltozós esetben az integrálfüggvény. A konzervatív elnevezés a fizikából jön: ilyen mezőben az energia megmarad, körbejárva nem nyerhetünk munkát (Escher „Waterfall" rajza éppen egy nem konzervatív mezőt ábrázol).

## Kapocs

- [[concepts/analiii/vektormezo-primitiv-fuggvenye]] — az (a) tulajdonság fogalma és az egyértelműség.
- [[concepts/analiii/newton-leibniz-formula-vonalintegralra]] — az (a) $\Rightarrow$ (b1) irány eszköze.
- [[concepts/analiii/valos-vonalintegral]] — az additivitás, a megfordítás előjelváltása és a triviális becslés mind itt szerepel.
- [[concepts/analiii/rotaciomentes-vektormezo]] — differenciálható mezőre ehhez járul egy ellenőrizhető, lokális kritérium.
- [[concepts/analii/integralfuggveny]] — az egyváltozós megfelelője a (c1) $\Rightarrow$ (a) konstrukciónak: ott is az integrál mint a felső határ függvénye adja a primitív függvényt.
