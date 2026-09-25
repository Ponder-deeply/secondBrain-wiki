---
tags: [concept, dimatii/algebrai-strukturak]
sources: [DimatIIEa03.pdf, DimatIIEa04.pdf]
derivation: source
updated: 2026-09-08
---

# Művelet

Egy halmazon értelmezett művelet nem más, mint egy $X^r \to X$ függvény; a definíció szigora (mindenütt értelmezett, és az érték is $X$-beli) dönti el, hogy egy ismerős számolási szabály művelet-e egyáltalán.

## Tartalom

### Definíció

Egy $X$ halmazon értelmezett ($r$-változós, „$r$-ér") **művelet** alatt egy

$$* : X^r \to X$$

függvényt értünk. Két nevezetes eset:

- **bináris** (kétváltozós) művelet: $* : X \times X \to X$; gyakran $*(x, y)$ helyett $x * y$-t írunk;
- **unér** (egyváltozós) művelet: $* : X \to X$.

A $0$-változós (**nullér**) művelet egy konstans kijelölése.

### Példák és ellenpéldák

- A $\mathbb{C}$ halmazon a $+$ és a $\cdot$ bináris műveletek.
- A $\mathbb{C}$ halmazon az osztás **nem** művelet, mert $\mathrm{dmn}(\div) \ne \mathbb{C} \times \mathbb{C}$ (nullával nem osztható).
- A $\mathbb{C}^* = \mathbb{C} \setminus \{0\}$ halmazon viszont az osztás már bináris művelet.
- A $\mathbb{C}$ halmazon a $0$, illetve az $1$ konstans kijelölése nullér művelet.
- Az $\mathbb{R}^n$ ($n > 1$) vektortéren a vektorok skaláris szorzata **nem** művelet, mert $\mathrm{rng}(\langle \cdot, \cdot \rangle) = \mathbb{R} \ne \mathbb{R}^n$ (a szorzás eredménye nem vektor).
- Az $\mathbb{R}^n$ vektortéren egy rögzített $\lambda \in \mathbb{R}$ skalárral való szorzás unér művelet.

### Műveleti tulajdonságok

Egy $* : X \times X \to X$ művelet

- **asszociatív**, ha $\forall a, b, c \in X : (a * b) * c = a * (b * c)$;
- **kommutatív**, ha $\forall a, b \in X : a * b = b * a$.

Példák:

- A $\mathbb{C}$-n a $+$ és a $\cdot$ művelet asszociatív és kommutatív.
- A függvények halmazán a kompozíció asszociatív: $(f \circ g) \circ h = f \circ (g \circ h)$.
- A kompozíció **nem** kommutatív: $f(x) = x + 1$, $g(x) = x^2$ mellett $(f \circ g)(x) = x^2 + 1 \ne (g \circ f)(x) = (x+1)^2$.
- A kivonás az egészek halmazán **nem** asszociatív: $-1 = (1 - 1) - 1 \ne 1 - (1 - 1) = 1$.

Ez a két tulajdonság a további építkezés alapja: az asszociativitás a félcsoport, a kommutativitás pedig az Abel-csoport, illetve a kommutatív gyűrű definíciójában jelenik meg.

## Kapocs

- [[concepts/dimatii/algebrai-struktura]] — halmaz a rajta értelmezett műveletek halmazával
- [[concepts/dimatii/felcsoport-es-monoid]] — az asszociativitás első következménye
- [[concepts/dimatii/muvelettarto-lekepezes]] — a műveleti szerkezetet megőrző függvények
- [[concepts/dimatii/csoport]] — asszociativitás, egységelem és inverz együtt
