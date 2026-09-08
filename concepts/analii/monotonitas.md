---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 2. előadás"]
derivation: source
updated: 2026-09-04
---

# Monotonitás

A monotonitás és a derivált előjelének kapcsolata nyílt, majd zárt intervallumra; szigorú monotonitás elégséges feltétele; kiterjesztés tetszőleges korlátos intervallumra.

## A tárgyalt monotonitásfogalmak

Emlékeztető: $f \nearrow$, $f \searrow$, $f \uparrow$, $f \downarrow$ jelölések (l. An. I., 10. ea.) a monoton növő, monoton csökkő, szigorúan monoton növő, illetve szigorúan monoton csökkő függvényekre.

## Alaptétel: monotonitás és derivált kapcsolata (nyílt intervallumon)

**Tétel.** Legyen $(a, b) \subset \mathbb{R}$ nyílt intervallum és $f \in D(a, b)$. Ekkor

$$1^\circ \quad f \nearrow\ [\searrow]\ (a,b)\text{-n} \iff f' \geq 0\ [f' \leq 0]\ (a,b)\text{-n.}$$

$$2^\circ \quad \text{ha } f' > 0\ [f' < 0]\ (a,b)\text{-n} \implies f \uparrow\ [\downarrow]\ (a,b)\text{-n.}$$

**Bizonyítás.**

$1^\circ$ ($\Rightarrow$) Ha $f \nearrow (a, b)$-n és $t \in (a, b)$ tetszőleges pont, akkor
$$f'(t) = f'_+(t) = \lim_{x \to t+0} \frac{f(x) - f(t)}{x - t} \geq 0,$$
hiszen $x - t > 0$ és a monotonitás miatt $f(x) - f(t) \geq 0$.

($\Leftarrow$) Ha $\forall x \in (a, b) : f'(x) \geq 0$, legyenek $x, y \in (a, b)$, $x < y$. Ekkor $f \in C[x, y]$, $f \in D(x, y)$, és a [[concepts/analii/kozeptertekek|Lagrange-féle középértéktétel]] szerint
$$\exists\, \xi \in (x, y) : \frac{f(y) - f(x)}{y - x} = f'(\xi) \geq 0 \implies f(x) \leq f(y).$$
Ezért $f \nearrow (a, b)$-n. $\blacksquare$

$2^\circ$ Alkalmazzuk az „éles" egyenlőtlenségeket az $1^\circ$ ($\Leftarrow$) irányban.

## Megjegyzések

**1.** A derivált előjeléből következtethetünk a (szigorú) monotonitásra.

**2.** A tételben lényeges feltétel, hogy intervallumon értelmezett függvényről legyen szó. Példa: $f(x) := \dfrac{1}{x}$ ($x \in \mathbb{R} \setminus \{0\}$) esetén $f'(x) = -\dfrac{1}{x^2} < 0$ minden $x \in \mathcal{D}_f$-re, de $f$ nem szigorúan csökkő $\mathcal{D}_f = \mathbb{R} \setminus \{0\}$-n (ami nem intervallum), hiszen $f \downarrow \mathbb{R}^-$-on és $f \downarrow \mathbb{R}^+$-on.

**3.** A szigorú monotonitás elégséges feltételei nem szükségesek: $f(x) := x^3$ esetén $f \uparrow \mathbb{R}$-en, de $f'(0) = 0$.

## Szükséges és elégséges feltétel a szigorú monotonitásra

**Tétel.** Legyen $(a, b) \subset \mathbb{R}$ nyílt intervallum és $f \in D(a, b)$. Ekkor

$$f \uparrow\ [\downarrow]\ (a,b)\text{-n} \iff f' \geq 0\ [f' \leq 0]\ (a,b)\text{-n, és $(a,b)$-nek nincs olyan részintervalluma, amelyen $f'$ azonosan $0$.}$$

**Bizonyítás.** Meggondolható. $\blacksquare$

## Kiterjesztés zárt intervallumra

**Tétel.** Legyen $-\infty < a < b < +\infty$. T.f.h. $f \in C[a, b]$ és $f \in D(a, b)$. Ekkor

$$f \nearrow\ [\searrow]\ [a,b]\text{-n} \iff f' \geq 0\ [f' \leq 0]\ (a,b)\text{-n.}$$

**Bizonyítás.** Az előző tételek és a folytonosságra vonatkozó átviteli elv felhasználásával megondolható. $\blacksquare$

## Kiterjesztés tetszőleges korlátos intervallumra

**Tétel.** Legyen $-\infty < a < b < +\infty$. Ha $f$ (szigorúan) monoton $(a, b)$-n és folytonos az intervallum egyik (vagy mindkét) végpontjában, akkor a (szigorú) monotonitás kiterjeszthető a végpontokkal bővített intervallumra.

## Példa: egyenlőtlenség monotonitással

Igazoljuk az $x - \dfrac{x^2}{2} < \ln(1+x) < x$ ($x > 0$) jobb részét, monotonitási módszerrel.

**$\ln(1+x) < x$ (2. megoldás).** Legyen $f(x) := x - \ln(1+x)$ ($x \geq 0$). Ekkor $f \in C(\mathbb{R}_0^+)$, $f \in D(\mathbb{R}^+)$ és
$$f'(x) = 1 - \frac{1}{1+x} = \frac{x}{x+1} > 0 \quad (x > 0).$$
Tehát $f \uparrow \mathbb{R}_0^+$-on, és $f(0) = 0$, ezért $f(x) > 0$ ($\forall x > 0$), azaz $\ln(1+x) < x$. $\blacksquare$

## Kapocs

- [[concepts/analii/kozeptertekek]] — a Lagrange-féle középértéktétel az alaptétel $(\Leftarrow)$ irányának alapja
- [[concepts/analii/lokalis-szelsertekek]] — az 1. rendű elégséges feltétel bizonyítása monotonitáson alapul
- [[concepts/analii/konvex-konkav-fuggvenyek]] — $f''$ előjele az $f'$ monotonitását, így $f$ konvexitását határozza meg
- [[concepts/analii/teljes-fuggvenyvizsgalat]] — monotonitási intervallumok meghatározása a függvényvizsgálat 3. lépése
- [[concepts/analii/primitiv-fuggveny]] — a deriváltak egyenlőségének tétele összeköti a monoton egyediséggel
