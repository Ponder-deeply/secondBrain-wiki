---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 8. előadás"]
derivation: source
updated: 2026-09-04
---

# Integrálegyenlőtlenségek

A Riemann-integrál értékére egyszerűen kaphatunk becsléseket a monotonitásból és az abszolút értékre vonatkozó egyenlőtlenségekből. Ezek alapja az első középértéktétel.

## Előjeltartó integrál és monotonitás

**Tétel.** T.f.h. $f, g \in R[a,b]$. Ekkor:

**1° (Előjeltartó integrál)** Ha $f \geq 0$ az $[a,b]$-n, akkor $\displaystyle\int_a^b f \geq 0$.

**2° (Integrálban monoton)** Ha $f \leq g$ az $[a,b]$-n, akkor $\displaystyle\int_a^b f \leq \int_a^b g$.

*Bizonyítás.* 1° Minden $\tau \in \mathcal{F}[a,b]$ felosztásra $s(f, \tau) \geq 0 \Rightarrow I_*(f) = \int_a^b f \geq 0$.
2° $f \leq g \Rightarrow g - f \geq 0 \Rightarrow \int_a^b (g-f) \geq 0 \Rightarrow \int_a^b g \geq \int_a^b f$. $\blacksquare$

## Abszolút érték az integráljel alatt

**Tétel.** T.f.h. $f \in R[a,b]$. Ekkor:

**1°** $|f| \in R[a,b]$.

**2°** $\displaystyle\left|\int_a^b f\right| \leq \int_a^b |f|$.

*Bizonyítás.* 1° Mivel $\bigl||f(x)| - |f(y)|\bigr| \leq |f(x) - f(y)|$, ezért $\Omega(|f|, \tau) \leq \Omega(f, \tau) < \varepsilon$, tehát $|f| \in R[a,b]$.

2° Mivel $-|f| \leq f \leq |f|$, ezért $-\int_a^b |f| \leq \int_a^b f \leq \int_a^b |f|$, amiből $\left|\int_a^b f\right| \leq \int_a^b |f|$. $\blacksquare$

**Megjegyzés.** Az 1° fordítottja nem igaz: ha $|f| \in R[a,b]$, abból nem következik $f \in R[a,b]$. Ellenpélda: $f(x) := 1$ ha $x \in [0,1] \cap \mathbb{Q}$, $f(x) := -1$ ha $x \in [0,1] \setminus \mathbb{Q}$. Ekkor $|f| = 1 \in R[0,1]$, de $f \notin R[0,1]$.

## Az integrálszámítás első középértéktétele

**Tétel.** T.f.h. $f, g \in R[a,b]$ és $g \geq 0$. Legyenek $m := \inf_{[a,b]} f$, $M := \sup_{[a,b]} f$. Ekkor:

**1°**
$$m \cdot \int_a^b g \leq \int_a^b f \cdot g \leq M \cdot \int_a^b g.$$

**2°** Ha még $f \in C[a,b]$ is teljesül, akkor $\exists\, \xi \in [a,b]$:
$$\int_a^b f \cdot g = f(\xi) \cdot \int_a^b g.$$

*Bizonyítás.* 1° Tetszőleges $x \in [a,b]$ esetén $m \leq f(x) \leq M$ és $g(x) \geq 0$, ezért $m\cdot g(x) \leq f(x)\cdot g(x) \leq M\cdot g(x)$. Mivel $m\cdot g,\, f\cdot g,\, M\cdot g \in R[a,b]$, a monotonitásból adódik $(*)$.

2° Ha $\int_a^b g = 0$, akkor $\int_a^b f\cdot g = 0$ is (a becslésből), és bármely $\xi \in [a,b]$ megfelel. Ha $\int_a^b g > 0$, akkor $(*)$-ból:

$$m \leq \frac{\int_a^b f \cdot g}{\int_a^b g} \leq M.$$

Mivel $f \in C[a,b]$, a Bolzano–Darboux-tételből következik, hogy $f$ minden $m$ és $M$ közötti értéket felvesz, így $\exists\, \xi \in [a,b]$:

$$f(\xi) = \frac{\int_a^b f \cdot g}{\int_a^b g}. \qquad \blacksquare$$

**Megjegyzések.**
- Ha az 1° állításban $g(x) \equiv 1$ ($x \in [a,b]$), akkor az **integrálközép** fogalma adódik:
$$m = \inf_{[a,b]} f \leq \frac{1}{b-a} \cdot \int_a^b f \leq \sup_{[a,b]} f = M.$$
  Az $\frac{1}{b-a}\int_a^b f$ értéket az $f$ függvény integrálközepének nevezzük ($\approx$ számtani közép általánosítása, „átlagolás").
- Ha $g(x) = 1$ és $f \in C[a,b]$, akkor $\exists\, \xi \in [a,b]$: $\int_a^b f = f(\xi)(b-a)$, ami a klasszikus első középértéktételt adja.
- Az integrálközép lépcsősfüggvény esetén: $a := 0$, $b := n$, $f(x) := a_i$ ($x \in (i-1, i)$) esetén $\frac{1}{n}\int_0^n f = \frac{a_1 + \cdots + a_n}{n}$.

## Kapocs

- [[concepts/analii/muvelet-integralhato-fuggvenyekkel]] — $\lambda f$, $f+g$, $f \cdot g$ integrálhatósága
- [[concepts/analii/riemann-integral-tulajdonsagok]] — integrál további alaptulajdonságai
- [[concepts/analii/folytonos-fuggvenyek-integralhatasaga]] — $C[a,b] \subset R[a,b]$; a 2° állításban szükséges
- [[concepts/analii/integralfuggveny]] — az integrálfüggvény folytonossága az abszolút értékes becslésen alapul
- [[concepts/analii/newton-leibniz-tetel]] — az integráltétel alkalmazása: az $\xi$ kifejezésmód
