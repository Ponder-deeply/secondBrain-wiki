---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 5. előadás"]
derivation: source
updated: 2026-09-04
---

# Nevezetes sorfejtések

A legfontosabb elemi függvények Maclaurin-sorai és konvergenciakészleteik, teljes bizonyítással. Mindegyik sorfejtés az „egyedi eszközök" módszerével készül: ismert sorokból, tagonkénti deriválással vagy integrálással vezeti le az új sorfejtést, majd igazolja az egyenlőséget.

## 1° — Mértani sor

$$\boxed{\frac{1}{1+x} = 1 - x + x^2 - x^3 + \cdots} \qquad (|x| < 1).$$

**Bizonyítás.** Legyen $f(x) := \frac{1}{1+x}$ $(x > -1)$. Ekkor $f \in D^\infty$ és $f^{(n)}(x) = (-1)^n n!\,(1+x)^{-n-1}$, tehát $f^{(n)}(0) = (-1)^n n!$. Így

$$T_0 f(x) = \sum_{n=0}^{\infty} \frac{(-1)^n n!}{n!} x^n = \sum_{n=0}^{\infty} (-x)^n.$$

Ez $(-x)$ hányadosú geometriai sor, konvergens $\iff |x| < 1$, és ekkor összege $\frac{1}{1-(-x)} = \frac{1}{1+x}$. $\blacksquare$

## 2° — $\frac{1}{1+x^2}$ sorfejtése

$$\boxed{\frac{1}{1+x^2} = 1 - x^2 + x^4 - x^6 + \cdots} \qquad (|x| < 1).$$

**Bizonyítás.** Az 1° sorfejtésében $x$ helyett $x^2$-et írva adódik. $\blacksquare$

## 3° — Természetes logaritmus

$$\boxed{\ln(1+x) = x - \frac{x^2}{2} + \frac{x^3}{3} - \frac{x^4}{4} - \cdots} \qquad (x \in (-1,1]).$$

Ha $x = 1$: $\displaystyle\ln 2 = 1 - \frac{1}{2} + \frac{1}{3} - \frac{1}{4} + \cdots$

**Bizonyítás (vázlat).** Legyen $f(x) := \ln(1+x)$ $(x > -1)$. Ekkor $f \in D^\infty$ és $f^{(n)}(x) = (-1)^{n+1}(n-1)!\,(1+x)^{-n}$ $(n \in \mathbb{N}^+)$, tehát $f(0) = 0$ és $f^{(n)}(0) = (-1)^{n+1}(n-1)!$ $(n \in \mathbb{N}^+)$. Így

$$T_0 f(x) = \sum_{n=1}^{\infty} (-1)^{n+1}\frac{x^n}{n} \qquad (x \in \mathbb{R}).$$

A sor konvergenciahalmaza a $(-1,1]$ intervallum.

**Az előállítás.** Legyen $g$ a $T_0 f$ sor összegfüggvénye $(x \in (-1,1])$. Ekkor $g \in D(-1,1)$ és

$$g'(x) = \sum_{n=1}^{\infty}(-1)^{n+1}\cdot n \cdot \frac{x^{n-1}}{n} = \sum_{n=0}^{\infty}(-x)^n = \frac{1}{1+x}$$

(l. 2° a $(-1,1)$ intervallumon). Mivel $f'(x) = \frac{1}{1+x}$ $(x > -1)$, ezért $f' = g'$ a $(-1,1)$-en, tehát $\exists c \in \mathbb{R}$: $f(x) - g(x) = c$ $(x \in (-1,1))$. Az $f(0) - g(0) = 0$ feltétel adja $c = 0$. Az $x = 1$ pontban az állítás $f$ és $g$ folytonosságából következik. $\blacksquare$

## 4° — Arkusztangens

$$\boxed{\operatorname{arc\,tg}\, x = x - \frac{x^3}{3} + \frac{x^5}{5} - \frac{x^7}{7} - \cdots} \qquad (x \in [-1,1]).$$

Ha $x = 1$: $\displaystyle\operatorname{arc\,tg}\, 1 = \frac{\pi}{4} = 1 - \frac{1}{3} + \frac{1}{5} - \frac{1}{7} + \cdots$ (Leibniz-formula $\pi$-re).

**Bizonyítás (vázlat).** Az $f(x) := \operatorname{arc\,tg}\, x$ deriváltja $f'(x) = \frac{1}{1+x^2}$, amelynek sorfejtése ismert (2°):

$$T_0 f'(x) = 1 - x^2 + x^4 - x^6 + \cdots \qquad (|x| < 1).$$

Legyen $g(x) := x - \frac{x^3}{3} + \frac{x^5}{5} - \frac{x^7}{7} + \cdots$ $(|x| < 1)$. Ekkor $g'(x) = 1 - x^2 + x^4 - x^6 + \cdots = f'(x)$, tehát $f(x) - g(x) = c$. Az $f(0) = g(0) = 0$ feltétel adja $c = 0$. A $\pm 1$ pontokban az állítás hasonlóan bizonyítható. $\blacksquare$

**Megjegyzés.** Az $f(x) := \operatorname{arc\,tg}\, x$ Taylor-sorának előállítása a definíció alapján nem egyszerű feladat; az „egyedi eszközök" módszere lényegesen rövidebb.

## 5° — Binomiális sor

$$\boxed{(1+x)^\alpha = \sum_{n=0}^{+\infty} \binom{\alpha}{n} x^n} \qquad (x \in (-1,1),\ \alpha \in \mathbb{R}),$$

ahol a **binomiális együtthatók** általánosított alakja:

$$\binom{\alpha}{0} := 1, \qquad \binom{\alpha}{n} := \frac{\alpha(\alpha-1)\cdots(\alpha-n+1)}{n!} \quad (n \in \mathbb{N}^+).$$

**Bizonyítás (vázlat).** Legyen $f(x) := (1+x)^\alpha$ $(x > -1,\ \alpha \in \mathbb{R})$.

1. **Taylor-sor.** $f^{(n)}(0) = \alpha(\alpha-1)\cdots(\alpha-n+1)$, tehát $T_0 f(x) = \sum_{n=0}^{\infty}\binom{\alpha}{n}x^n$.

2. **Konvergencia.** A $T_0 f$ sor a $(-1,1)$ intervallumon konvergens (hányadoskritérium).

3. **Előállítás.** $f \in D^\infty(-1,+\infty)$ és $(1+x)\cdot f'(x) = \alpha \cdot f(x)$ $(x > -1)$. Legyen $g(x) := \sum_{n=0}^{\infty}\binom{\alpha}{n}x^n$ $(|x| < 1)$; ekkor $g \in D^\infty(-1,1)$ és $(1+x)\cdot g'(x) = \alpha \cdot g(x)$ $(|x| < 1)$.

4. **Összehasonlítás.** A $h(x) := \frac{g(x)}{(1+x)^\alpha}$ hányados deriváltja:

$$h'(x) = \frac{g'(x)(1+x)^\alpha - g(x)\cdot\alpha(1+x)^{\alpha-1}}{(1+x)^{2\alpha}} = \frac{(1+x)\cdot g'(x) - \alpha \cdot g(x)}{(1+x)^{\alpha+1}} = 0.$$

Ezért $\exists c \in \mathbb{R}$: $g(x) = c\cdot(1+x)^\alpha$ $(|x|<1)$. Mivel $g(0) = \binom{\alpha}{0} = 1$, ezért $c = 1$, tehát $(1+x)^\alpha = g(x)$. $\blacksquare$

## 6° — $\frac{1}{\sqrt{1-x^2}}$ sorfejtése

A binomiális sorban $\alpha = -\frac{1}{2}$ és $x$ helyett $(-x^2)$ behelyettesítve:

$$\frac{1}{\sqrt{1-x^2}} = \sum_{n=0}^{+\infty}(-1)^n \binom{-\tfrac{1}{2}}{n} x^{2n} \qquad (|x|<1),$$

ahol $\binom{-1/2}{n} = (-1)^n \binom{2n}{n}/4^n$, tehát $(-1)^n \binom{-1/2}{n} = \binom{2n}{n}/4^n$.

## 7° — Arkuszszinusz

$$\boxed{\arcsin x = \sum_{n=0}^{+\infty}\binom{2n}{n}\frac{x^{2n+1}}{4^n(2n+1)}} \qquad (|x| \leq 1).$$

**Bizonyítás (vázlat).** $f(x) := \arcsin x$ $(x \in [-1,1])$, $f \in D(-1,1)$ és $f'(x) = \frac{1}{\sqrt{1-x^2}}$ $(|x|<1)$. A 6° példát és a 3° gondolatmenetét alkalmazva (tagonkénti integrálással a 0-tól $x$-ig) adódik az állítás. $\blacksquare$

## Összefoglaló táblázat

| Függvény | Sor | Konvergenciakészlet |
|---|---|---|
| $\frac{1}{1+x}$ | $\sum_{n=0}^\infty (-1)^n x^n$ | $\|x\| < 1$ |
| $\frac{1}{1+x^2}$ | $\sum_{n=0}^\infty (-1)^n x^{2n}$ | $\|x\| < 1$ |
| $\ln(1+x)$ | $\sum_{n=1}^\infty (-1)^{n+1}\frac{x^n}{n}$ | $x \in (-1,1]$ |
| $\operatorname{arc\,tg}\, x$ | $\sum_{n=0}^\infty (-1)^n \frac{x^{2n+1}}{2n+1}$ | $x \in [-1,1]$ |
| $(1+x)^\alpha$ | $\sum_{n=0}^\infty \binom{\alpha}{n} x^n$ | $\|x\| < 1$ |
| $\frac{1}{\sqrt{1-x^2}}$ | $\sum_{n=0}^\infty \binom{2n}{n}\frac{x^{2n}}{4^n}$ | $\|x\| < 1$ |
| $\arcsin x$ | $\sum_{n=0}^\infty \binom{2n}{n}\frac{x^{2n+1}}{4^n(2n+1)}$ | $\|x\| \leq 1$ |

## Kapocs

- [[concepts/analii/taylor-polinom]] — Taylor-sor és Taylor-polinom definíciója; együtthatók meghatározása
- [[concepts/analii/taylor-sor-eloallitas]] — konvergencia vs. előállítás; ellenpélda
- [[concepts/analii/taylor-formula-maradektag]] — a Lagrange-maradéktag az előállítás bizonyításához
- [[concepts/analii/elemi-fuggvenyek-kiegeszites]] — $\arcsin$, $\arctan$ és más inverz függvények definíciói és deriváltjai
- [[concepts/analii/derivalasi-szabalyok]] — lánc-szabály, tagonkénti deriválás alkalmazása sorfejtéseknél
