---
tags: [concept]
sources: [NM1_ea11.pdf, NM1_ea12.pdf]
derivation: source
kind: definition
element: water
updated: 2026-10-21
---

# Konvergenciarend

Egy konvergens sorozat $p$-edrendben konvergens, ha $|x_{k+1} - x^*|/|x_k - x^*|^p$ véges, pozitív határértékhez tart. A fixpont-iteráció rendjét a $\varphi$ deriváltjai adják a fixpontban: ha az első $p-1$ derivált nulla, de a $p$-edik nem, a konvergencia $p$-edrendű.

## Tartalom

### Definíció

Az $(x_k)$ konvergens sorozat ($\lim x_k = x^*$) **$p$-edrendben konvergens**, ha $\exists\, c \in (0; +\infty)$:

$$\lim_{k\to\infty}\frac{|x_{k+1} - x^*|}{|x_k - x^*|^p} = c.$$

### Elemi tulajdonságok

- $p$ egyértelmű, és $p \ge 1$.
- $p$ nem feltétlenül egész (a [[concepts/nummodi/hurmodszer-szelomodszer|szelőmódszernél]] $p = \tfrac{1+\sqrt5}{2}$).
- $p = 1$: **elsőrendű** (lineáris) konvergencia, ekkor $c \le 1$; $p = 2$: **másodrendű** (kvadratikus); $p > 1$: **szuperlineáris**.
- Ha a próbált $p$-re a határérték $c = 0$, a valódi rend nagyobb; ha $c = \infty$, kisebb.
- Gyakorlatban a **legalább $p$-edrendű** konvergencia: $\exists\, K \in \mathbb{R}^+$: $|x_{k+1} - x^*| \le K|x_k - x^*|^p$ $\forall k$.
- A fixponttételek nem mondanak rendet, csak annyit, hogy legalább elsőrendű.

**Szemléletesen** ($\sqrt2$ közelítése): elsőrendű sorozatnál lépésenként kb. egy újabb tizedesjegy lesz pontos, másodrendűnél lépésenként kb. megduplázódik a pontos jegyek száma.

**Példa.** $x_k = \tfrac{1}{2^k}$, $x^* = 0$. $p = 2$-vel $\lim \tfrac{2^{2k}}{2^{k+1}} = \lim 2^{k-1} = \infty$, tehát a rend kisebb. $p = 1$-gyel $\lim\tfrac{2^k}{2^{k+1}} = \tfrac12$, tehát elsőrendű.

### Tétel — $p$-edrendben konvergens fixpont-iterációk

**Tétel.** Legyen $\varphi \in C^p[a;b]$, és az $x_{k+1} = \varphi(x_k)$ sorozat konvergens, határértéke $x^*$. Ha

$$\varphi'(x^*) = \dots = \varphi^{(p-1)}(x^*) = 0, \quad \text{de} \quad \varphi^{(p)}(x^*) \ne 0,$$

akkor a konvergencia $p$-edrendű, és

$$|x_{k+1} - x^*| \le \frac{M_p}{p!}|x_k - x^*|^p, \qquad M_p = \max_{\xi\in[a;b]}|\varphi^{(p)}(\xi)|.$$

**Biz.**

1. $\varphi$ [[concepts/analii/taylor-formula-maradektag|Taylor-formulája]] $x^*$ körül Lagrange-maradéktaggal: $\exists\,\xi$ $x$ és $x^*$ között,
   $$\varphi(x) = \varphi(x^*) + \varphi'(x^*)(x - x^*) + \dots + \frac{\varphi^{(p-1)}(x^*)}{(p-1)!}(x - x^*)^{p-1} + \frac{\varphi^{(p)}(\xi)}{p!}(x - x^*)^p.$$
2. $x = x_k$ helyen, a deriváltak eltűnését és $\varphi(x^*) = x^*$-ot felhasználva ($\exists\,\xi_k$ $x_k$ és $x^*$ között):
   $$x_{k+1} = \varphi(x_k) = x^* + \frac{\varphi^{(p)}(\xi_k)}{p!}(x_k - x^*)^p \implies x_{k+1} - x^* = \frac{\varphi^{(p)}(\xi_k)}{p!}(x_k - x^*)^p.$$
3. $x_k \to x^*$ miatt $\xi_k \to x^*$, és $\varphi^{(p)}$ folytonos, így
   $$\lim_{k\to\infty}\frac{|x_{k+1} - x^*|}{|x_k - x^*|^p} = \lim_{k\to\infty}\frac{|\varphi^{(p)}(\xi_k)|}{p!} = \frac{|\varphi^{(p)}(x^*)|}{p!} \ne 0,$$
   tehát a sorozat $p$-edrendben konvergens.
4. A hibabecslés: $|x_{k+1} - x^*| = \dfrac{|\varphi^{(p)}(\xi_k)|}{p!}|x_k - x^*|^p \le \dfrac{M_p}{p!}|x_k - x^*|^p$. $\square$

**Következmény.** Ha $\varphi : [a;b] \to [a;b]$ kontrakció, $x^*$ a fixpontja, és $\varphi'(x^*) = \dots = \varphi^{(p-1)}(x^*) = 0 \ne \varphi^{(p)}(x^*)$, akkor a fixpont egyértelmű, minden $x_0 \in [a;b]$-ből konvergál hozzá a sorozat, és $|x_{k+1} - x^*| \le \tfrac{M_p}{p!}|x_k - x^*|^p$. (A [[concepts/nummodi/nemlinearis-egyenletek-fixpont|Banach-tétel]] adja a konvergenciát, a fenti tétel a rendet.)

**Példák** ($\sqrt2$ közelítései): $x_{k+1} = 1 + \tfrac{1}{1 + x_k}$ (lánctört, $p = 1$); $x_{k+1} = \tfrac12\bigl(x_k + \tfrac{2}{x_k}\bigr)$ ([[concepts/nummodi/newton-modszer|Newton]] $f(x) = x^2 - 2$-re, $p = 2$); $x_{k+1} = x_k\dfrac{x_k^2 + 6}{3x_k^2 + 2}$ ($p = 3$).

### Vizsgán

- **25. b):** fogalom és elemi tulajdonságok; a $p$-edrendű fixpont-iterációk tételének bizonyítása (Taylor + határérték).
- **26. a):** a fogalom; a húr- ($p = 1$), szelő- ($p = \tfrac{1+\sqrt5}{2}$) és Newton-módszer ($p = 2$) rendjének összevetése.

## Kapocs

- [[concepts/nummodi/nemlinearis-egyenletek-fixpont]] — fixpont-iteráció, Banach-tétel $[a;b]$-n
- [[concepts/nummodi/newton-modszer]] — másodrendű módszer; lokális konvergenciatétele közvetlenül is bizonyítja a rendet
- [[concepts/nummodi/hurmodszer-szelomodszer]] — elsőrendű ill. $\tfrac{1+\sqrt5}{2}$-rendű módszerek
- [[concepts/analii/taylor-formula-maradektag]] — a bizonyítás eszköze
