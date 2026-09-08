---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 4. előadás"]
derivation: source
updated: 2026-09-04
---

# L'Hospital-szabályok

L'Hospital-szabályai hatékony módszert nyújtanak ún. **kritikus határértékek** — $\frac{0}{0}$, $\frac{\pm\infty}{\pm\infty}$, $(+\infty)+(-\infty)$, $0 \cdot (\pm\infty)$, $0^0$, $1^\infty$ stb. — kiszámolásához, azaz egy hányados határértékét a számlálő és nevező deriváltjainak hányadosával helyettesíti.

## A $\frac{0}{0}$ eset

**Tétel (L'Hospital-szabály, $\frac{0}{0}$ eset).** Legyen $-\infty \leq a < b \leq +\infty$ és $f, g \in D(a,b)$. Tegyük fel, hogy

- (a) $\lim_{a+0} f = \lim_{a+0} g = 0$,
- (b) $g(x) \neq 0$ és $g'(x) \neq 0$ minden $x \in (a,b)$-re,
- (c) $\exists \lim_{a+0} \frac{f'}{g'} \in \overline{\mathbb{R}}$.

Ekkor

$$\exists \lim_{a+0} \frac{f}{g} \in \overline{\mathbb{R}} \quad \text{és} \quad \lim_{a+0} \frac{f}{g} = \lim_{a+0} \frac{f'}{g'}.$$

### Bizonyítás vázlata (véges $a > -\infty$ eset)

Értelmezzük $f(a) := 0$, $g(a) := 0$ kiterjesztéssel. A Cauchy-féle [[concepts/analii/kozeptertekek|középértéktétel]] feltételei teljesülnek $[a, x]$ intervallumon minden $x \in (a, b)$-re, tehát $\exists \xi_x \in (a, x)$, amelyre

$$\frac{f(x)}{g(x)} = \frac{f(x) - f(a)}{g(x) - g(a)} = \frac{f'(\xi_x)}{g'(\xi_x)}.$$

Mivel $\xi_x \to a+0$, ha $x \to a+0$, ezért $\frac{f'(\xi_x)}{g'(\xi_x)} \to \lim_{a+0} \frac{f'}{g'} = A$.

Az $a = -\infty$ eset visszavezethető a $\frac{0}{0}$ esetre az $F(x) := f(-1/x)$, $G(x) := g(-1/x)$ helyettesítéssel ($x \in (0,d)$, $d := -1/b$).

## A $\frac{+\infty}{+\infty}$ eset

**Tétel (L'Hospital-szabály, $\frac{+\infty}{+\infty}$ eset).** Legyen $-\infty \leq a < b \leq +\infty$ és $f, g \in D(a,b)$. Tegyük fel, hogy

- (a) $\lim_{a+0} f = \lim_{a+0} g = +\infty$,
- (b) $g(x) \neq 0$ és $g'(x) \neq 0$ minden $x \in (a,b)$-re,
- (c) $\exists \lim_{a+0} \frac{f'}{g'} \in \overline{\mathbb{R}}$.

Ekkor ugyanaz a következtetés érvényes:

$$\lim_{a+0} \frac{f}{g} = \lim_{a+0} \frac{f'}{g'}.$$

## Megjegyzések és figyelmeztetések

**1°** A tételt jobb oldali határértékre fogalmaztuk meg. Hasonló állítások érvényesek bal oldali határértékre, kétoldali határértékre, és a $(+\infty)$-ben vett határértékre ($a = +\infty$).

**2°** A $\frac{+\infty}{-\infty}$, $\frac{-\infty}{+\infty}$, $\frac{-\infty}{-\infty}$ kritikus határértékekre, bal oldali határértékekre, kétoldali határértékekre, és a $(+\infty)$-ben vett határértékre hasonló állítások érvényesek.

**3°** A többi típusú kritikus határértéket ($0 \cdot \infty$, $\infty - \infty$, $0^0$, $1^\infty$, $\infty^0$) általában vissza lehet vezetni $\frac{0}{0}$ vagy $\frac{\pm\infty}{\pm\infty}$ típusra.

**4° Vigyázat!** A feltételeket ellenőrizni kell — „hagyja magát alkalmazni" akkor is, ha nem lehet. Például $f(x) := \cos x$, $g(x) := x+1$ esetén $\lim_{x\to 0} \frac{f}{g} = 1$, de $\lim_{x\to 0} \frac{f'}{g'} = \frac{-\sin 0}{1} = 0 \neq 1$.

**5°** Sokszor a szabályt **többször egymás után** kell alkalmazni. Például:

$$\lim_{x\to 0} \frac{1-\cos x}{x^2} \overset{\frac{0}{0}}{=} \lim_{x\to 0} \frac{\sin x}{2x} \overset{\frac{0}{0}}{=} \lim_{x\to 0} \frac{\cos x}{2} = \frac{1}{2}.$$

**6°** Előfordulhat, hogy $\exists \lim \frac{f}{g}$, de $\nexists \lim \frac{f'}{g'}$. Pl. $f(x)/g(x) = x^2 \sin\frac{1}{x} \cdot \frac{1}{x} \to 0$, de $\frac{f'(x)}{g'(x)} = 2x\sin\frac{1}{x} - \cos\frac{1}{x}$ nem tart határhoz.

**7°** Néha a L'Hospital-szabály körbe vezet (ciklikus alkalmazás). Például $\lim_{x\to+\infty} \frac{x}{\sqrt{1+x^2}}$: kétszeri alkalmazás visszaadja az eredeti alakot. Ilyenkor más módszer szükséges (pl. $\frac{x}{\sqrt{1+x^2}} = \frac{1}{\sqrt{1/x^2+1}} \to 1$).

## Fontos példák

**1°** $0 \cdot (-\infty)$ eset:
$$\lim_{x\to 0+} x \cdot \ln x \overset{0 \cdot (-\infty)}{=} \lim_{x\to 0+} \frac{\ln x}{1/x} \overset{\frac{-\infty}{+\infty}}{=} \lim_{x\to 0+} \frac{1/x}{-1/x^2} = \lim_{x\to 0+}(-x) = 0.$$

**2°** $0^0$ eset:
$$\lim_{x\to 0+} x^x = \lim_{x\to 0+}\left(e^{\ln x}\right)^x = \lim_{x\to 0+} e^{x \ln x} = e^0 = 1.$$

**3°** $\infty - \infty$ eset:
$$\lim_{x\to 0} \left(\frac{1}{\sin x} - \frac{1}{x}\right) = \lim_{x\to 0} \frac{x - \sin x}{x \sin x} \overset{\frac{0}{0}}{=} \lim_{x\to 0} \frac{1-\cos x}{\sin x + x\cos x} \overset{\frac{0}{0}}{=} \lim_{x\to 0} \frac{\sin x}{\cos x + \cos x - x\sin x} = \frac{0}{2} = 0.$$

## exp $\gg$ hatvány $\gg$ logaritmus

L'Hospital-szabály $n$-szeri alkalmazásával belátható az alábbi két növekedési összehasonlítás:

**Tétel.** Ha $a > 1$ és $1 \leq n, m \in \mathbb{N}$, akkor

$$\lim_{x\to+\infty} \frac{a^x}{x^n} = +\infty \qquad \text{(exp gyorsabb, mint bármely hatvány)},$$

$$\lim_{x\to+\infty} \frac{\ln^n x}{x^m} = 0 \qquad \text{(logaritmus lassabb, mint bármely hatvány)}.$$

Röviden: $x^n \ll a^x$ és $(\ln x)^n \ll x^m$, ha $x$ elég nagy.

## Kapocs

- [[concepts/analii/kozeptertekek]] — Cauchy-féle középértéktétel alapozza meg a bizonyítást
- [[concepts/analii/aszimptota]] — aszimptota meghatározásakor kritikus határértékek léphetnek fel
- [[concepts/analii/teljes-fuggvenyvizsgalat]] — L'Hospital a határértékek kiértékelésének eszköze a vizsgálatban
- [[concepts/analii/derivalt-fogalma]] — a szabály lényege: hányados határértéke helyett deriváltak hányadosát vesszük
- [[concepts/analii/taylor-polinom]] — Taylor-közelítés alternatív eszköz sok kritikus határérték kiszámolásához
