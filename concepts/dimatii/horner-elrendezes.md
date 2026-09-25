---
tags: [concept, dimatii/polinomok]
sources: [DimatIIEa05.pdf]
derivation: source
updated: 2026-09-08
---

# Horner-elrendezés

A Horner-elrendezés egy $n$-ed fokú polinom helyettesítési értékét $n$ szorzással és $n$ összeadással számolja ki, és melléktermékként megadja a gyöktényezővel való osztás hányadosát.

## Tartalom

### Az átrendezés

Legyen $f(x) = f_nx^n + f_{n-1}x^{n-1} + \dots + f_1x + f_0$, ahol $f_n \neq 0$. Ekkor $f$ átrendezhető a következő alakba:

$$f(x) = \big(\cdots((f_n \cdot x + f_{n-1})\cdot x + f_{n-2})\cdot x + \dots + f_1\big)\cdot x + f_0,$$

és így

$$f(c) = \big(\dots((f_n \cdot c + f_{n-1})\cdot c + f_{n-2})\cdot c + \dots + f_1\big)\cdot c + f_0.$$

Vagyis $f(c)$ kiszámítható $n$ db szorzás és $n$ db összeadás segítségével.

### A táblázat

| | $f_n$ | $f_{n-1}$ | $f_{n-2}$ | $\dots$ | $f_0$ | |
|---|---|---|---|---|---|---|
| $c$ | $c_n = f_n$ | $c_{n-1} = c_nc + f_{n-1}$ | $c_{n-2} = c_{n-1}c + f_{n-2}$ | $\dots$ | $c_0 = c_1c + f_0$ | $f(c) = c_0$ |

Általánosan $c_k = c_{k+1}c + f_{n-k+1}$ rekurzióval haladunk balról jobbra; az utolsó cella a helyettesítési érték.

**Példa.** Határozzuk meg az $f(x) = x^4 - 3x^3 + x + 6$ polinom $-2$ helyen vett helyettesítési értékét.

| | 1 | −3 | 0 | 1 | 6 | |
|---|---|---|---|---|---|---|
| $-2$ | 1 | −5 | 10 | −19 | | **44** |

Tehát $f(-2) = 44$.

### Gyöktényező kiemelése a Horner-táblából

Ha az $f(c)$ helyettesítési érték nulla, azaz $c$ gyöke $f$-nek, akkor a Horner-elrendezés alsó sorában — a helyettesítési érték előtt — **annak a $g$ polinomnak az együtthatói szerepelnek, amelyre $f(x) = (x-c)\cdot g(x)$**. A Horner-elrendezés tehát egyszerre helyettesítési érték- és gyöktényező-kiemelő eljárás.

**Példa.** Az $f(x) = x^4 - 4x^3 + 6x^2 - 4x + 1$ polinom $c = 1$ helyen vett helyettesítési értéke nulla:

| | 1 | −4 | 6 | −4 | 1 | |
|---|---|---|---|---|---|---|
| $1$ | 1 | −3 | 3 | −1 | | **0** |

Tehát $f(x) = (x-1)\cdot(x^3 - 3x^2 + 3x - 1)$.

## Kapocs

- [[concepts/dimatii/helyettesitesi-ertek-es-polinomfuggveny]] — az itt kiszámított mennyiség
- [[concepts/dimatii/gyoktenyezo-es-gyokok-szama]] — a gyöktényező leválasztásának tétele
- [[concepts/dimatii/polinomok-maradekos-osztasa]] — a Horner-elrendezés az $(x-c)$-vel való maradékos osztás elvégzése
- [[concepts/dimatii/lagrange-interpolacio]] — az interpolációs polinom ellenőrzése Horner-táblákkal
