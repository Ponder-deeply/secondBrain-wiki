---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 4. előadás"]
derivation: source
updated: 2026-09-04
---

# Aszimptota

Egy $f$ függvény aszimptotája $(+\infty)$-ben egy $l(x) = Ax + B$ elsőfokú függvény, amelyhez a függvény „tart", azaz $\lim_{x \to +\infty}(f(x) - l(x)) = 0$.

## Definíció

Legyen $a \in \mathbb{R}$ és $f : (a, +\infty) \to \mathbb{R}$. Az $f$ függvénynek **van aszimptotája $(+\infty)$-ben**, ha létezik $l(x) = Ax + B$ ($x \in \mathbb{R}$) elsőfokú függvény, amelyre

$$\lim_{x \to +\infty}(f(x) - l(x)) = 0.$$

Ekkor $l(x) = Ax + B$ az $f$ **aszimptotája $(+\infty)$-ben**.

A $(-\infty)$-beli aszimptota definíciója hasonlóan adódik.

## Szükséges és elégséges feltétel

**Tétel.** Az $f : (a, +\infty) \to \mathbb{R}$ függvénynek akkor és csak akkor van aszimptotája $(+\infty)$-ben, ha léteznek és végesek az alábbi határértékek:

$$\lim_{x \to +\infty} \frac{f(x)}{x} =: A \in \mathbb{R}, \qquad \lim_{x \to +\infty}(f(x) - Ax) =: B \in \mathbb{R}.$$

Ekkor az $l(x) = Ax + B$ ($x \in \mathbb{R}$) egyenes az $f$ függvény aszimptotája $(+\infty)$-ben.

Hasonló állítás érvényes a $(-\infty)$-beli aszimptotákra is.

### Bizonyítás vázlata

$(\Rightarrow)$ Ha $\lim_{x \to +\infty}(f(x) - Ax - B) = 0$, akkor $\lim_{x\to+\infty} \frac{1}{x} = 0$ miatt

$$\frac{f(x) - Ax - B}{x} \to 0 \implies \frac{f(x)}{x} - A - \frac{B}{x} \to 0 \implies \frac{f(x)}{x} \to A.$$

Majd ebből $f(x) - Ax \to B$ következik.

$(\Leftarrow)$ Ha mindkét határérték létezik és véges, az $l(x) = Ax + B$ egyenes kielégíti a definíciót, azaz $\lim_{x\to+\infty}(f(x) - l(x)) = 0$.

## Ferde aszimptota meghatározása — példa

**Feladat.** Van-e az

$$f(x) := \frac{2x^2 + 3x - 5}{4x + 1} \qquad \left(x \in \mathbb{R} \setminus \left\{-\tfrac{1}{4}\right\}\right)$$

függvénynek aszimptotája $(+\infty)$-ben?

**Megoldás.**

$$\frac{f(x)}{x} = \frac{2x^2 + 3x - 5}{4x^2 + x} = \frac{2 + \frac{3}{x} - \frac{5}{x^2}}{4 + \frac{1}{x}} \xrightarrow{x\to+\infty} \frac{2}{4} = \frac{1}{2} =: A.$$

$$f(x) - \frac{1}{2}x = \frac{2x^2 + 3x - 5}{4x+1} - \frac{x}{2} = \frac{4x^2+6x-10-4x^2-x}{2(4x+1)} = \frac{5x-10}{8x+2} \xrightarrow{x\to+\infty} \frac{5}{8} =: B.$$

Mindkét határérték létezik és véges, tehát $f$-nek van aszimptotája $(+\infty)$-ben:

$$l(x) = \frac{1}{2}x + \frac{5}{8}.$$

## Kapcsolat a függvényvizsgálattal

Az aszimptota meghatározása a [[concepts/analii/teljes-fuggvenyvizsgalat|teljes-fuggvenyvizsgalat]] 4. lépése: a határértékek vizsgálata a $\mathcal{D}'_f \setminus \mathcal{D}_f$ pontokban és $\pm\infty$-ben. Ha $A = 0$, az aszimptota vízszintes; ha $A \neq 0$, ferde aszimptotáról beszélünk.

## Kapocs

- [[concepts/analii/teljes-fuggvenyvizsgalat]] — az aszimptota a szisztematikus függvényvizsgálat egyik lépése
- [[concepts/analii/lhospital-szabalyok]] — aszimptota meghatározásakor szükség lehet L'Hospital-szabályra
- [[concepts/analii/kozeptertekek]] — a határértékes feltétel a Cauchy-középértéktétellel kapcsolatos
- [[concepts/analii/derivalt-fogalma]] — az aszimptota meredeksége $A = \lim f(x)/x$
