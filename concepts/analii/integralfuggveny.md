---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 10. előadás"]
derivation: source
updated: 2026-09-04
---

# Integrálfüggvény

Az integrálfüggvény egy rögzített $x_0$ „eltünő" ponthoz rendeli a $f$ függvény $x_0$-tól $x$-ig vett integrálját. Alapvető kapocs a határozott integrál és a primitív függvény fogalma között.

## Definíció

Legyen $f \in R[a,b]$ és $x_0 \in [a,b]$. Az

$$F : [a,b] \ni x \mapsto \int_{x_0}^x f(t)\, dt$$

függvényt $f$ **$x_0$-ban eltűnő integrálfüggvényének** nevezzük.

**Megjegyzés.** Az „$x_0$-ban eltűnő" elnevezés arra utal, hogy $F(x_0) = 0$.

### Példák

1. Ha $f(x) := x^2$ ($x \in \mathbb{R}$) és $x_0 = 0$, akkor
   $$F(x) = \int_0^x t^2\, dt = \left[\frac{t^3}{3}\right]_0^x = \frac{x^3}{3} \qquad (x \in \mathbb{R}).$$

2. Ha $f(x) := \begin{cases} 0, & -1 \leq x < 0 \\ 1, & 0 \leq x \leq 1 \end{cases}$ és $x_0 = 0$, akkor
   $$F(x) = \begin{cases} 0, & -1 \leq x < 0 \\ x, & 0 \leq x \leq 1. \end{cases}$$
   Figyeljük meg: $f$ nem folytonos 0-ban, de $F$ igen — sőt $F$ folytonos az egész $[-1,1]$-en, de 0-ban nem differenciálható.

## Az integrálfüggvény tulajdonságai

**Tétel.** Legyen $f \in R[a,b]$, $x_0 \in [a,b]$, és $F(x) := \int_{x_0}^x f(t)\, dt$ ($x \in [a,b]$). Ekkor:

**1° $F$ folytonos** az $[a,b]$ intervallumon.

*Bizonyítás.* Tetszőleges $x, y \in [a,b]$, $x < y$ esetén

$$|F(y) - F(x)| = \left|\int_x^y f\right| \leq \int_x^y |f| \leq M \cdot (y-x),$$

ahol $M$ az $f$ függvény egy korlátja ($|f(x)| \leq M$, $x \in [a,b]$). Ha $M\delta < \varepsilon$, akkor $|x-y| < \delta$ esetén $|F(y) - F(x)| < \varepsilon$. Tehát $F$ egyenletesen folytonos $[a,b]$-n. $\square$

**2° Ha $f$ folytonos valamely $d \in [a,b]$ pontban, akkor $F$ deriválható $d$-ben és $F'(d) = f(d)$.**

*Bizonyítás.* T.f.h. $d \in (a,b)$ és $f \in C\{d\}$ (a végponti eset egyoldali deriváltokra hasonlóan megy). Ekkor

$$F(d+h) - F(d) = \int_{x_0}^{d+h} f - \int_{x_0}^d f = \int_d^{d+h} f.$$

Mivel $f(d) = \frac{1}{h}\int_d^{d+h} f(d)\, dt$, ezért

$$\frac{F(d+h) - F(d)}{h} - f(d) = \frac{1}{h}\int_d^{d+h} \bigl(f(t) - f(d)\bigr)\, dt.$$

$f \in C\{d\}$: $\forall \varepsilon > 0$-hoz $\exists \delta > 0$, hogy $|t-d| < \delta \Rightarrow |f(t) - f(d)| < \varepsilon$.

Ha $0 < h < \delta$:
$$\left|\frac{F(d+h)-F(d)}{h} - f(d)\right| < \frac{1}{h}\int_d^{d+h} \varepsilon\, dt = \varepsilon.$$

Ha $-\delta < h < 0$:
$$\left|\frac{F(d+h)-F(d)}{h} - f(d)\right| \leq \frac{1}{|h|}\int_{d+h}^d |f(t)-f(d)|\, dt < \varepsilon.$$

Tehát $\lim_{h \to 0} \frac{F(d+h)-F(d)}{h} = f(d)$, azaz $F \in D\{d\}$ és $F'(d) = f(d)$. $\blacksquare$

**3° Ha $f \in C[a,b]$, akkor $F \in D[a,b]$ és $F'(x) = f(x)$ minden $x \in [a,b]$ pontban. Következésképpen ha $f$ folytonos $[a,b]$-n, akkor itt van primitív függvénye.**

**Megjegyzés.** A 2° tételben a végpontoknál ($d = a$ vagy $d = b$) a jobb-, illetve bal oldali deriváltról van szó.

## Kapcsolat a Newton–Leibniz-tétellel

Az integrálfüggvény 3° tulajdonsága adja a [[concepts/analii/newton-leibniz-tetel|Newton–Leibniz-tétel]] elégséges feltételét: ha $f \in C[a,b]$, akkor $F$ maga egy primitív függvény, és a Newton–Leibniz-tétel alkalmazható. Ez a kapocs teszi lehetővé, hogy a határozott integrált primitív függvénnyel számítsuk ki.

## Kapocs

- [[concepts/analii/newton-leibniz-tetel]] — az integrálfüggvény deriválhatóságát felhasználó alaptétel
- [[concepts/analii/primitiv-fuggveny]] — primitív függvény definíciója; az integrálfüggvény $C[a,b]$ esetén primitív függvény
- [[concepts/analii/folytonos-fuggvenyek-integralhatasaga]] — $C[a,b] \subset R[a,b]$
- [[concepts/analii/egyenletes-folytonossag]] — az 1° bizonyításában az egyenletes folytonosság jelenik meg
- [[concepts/analii/hatarozott-integral-ertelmezese]] — $R[a,b]$ és a Riemann-integrál definíciója
