---
tags: [concept]
sources: [DimatIIEa05.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, dm2gy07.pdf, dm2gy08_Polinomok.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-21
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

**Példa (Farkas-diák).** $f(x) = 5x^3 - 7x^2 + x - 8 = ((5x - 7)x + 1)x - 8$, $c = 3$:

| | 5 | −7 | 1 | −8 | |
|---|---|---|---|---|---|
| $3$ | 5 | 8 | 25 | | **67** |

Ellenőrzés: $5\cdot3 - 7 = 8$, $8\cdot3 + 1 = 25$, $25\cdot3 - 8 = 67 = f(3)$.

### Feladattípusok és módszerek (gyakorlati feladatsorok, 7–8. hét)

**Típus 1: helyettesítési érték.** $f(x)=x^4-3x^3+x+6$ értéke a $3,-1,2,-2$ helyeken: $f(3)=9$, $f(-1)=9$, $f(2)=0$, $f(-2)=44$ (a $2$ gyök, a Horner-tábla alsó sora $1,-1,-2,-3\mid0$, azaz $f=(x-2)(x^3-x^2-2x-3)$). Hiányzó tagot nulla együtthatóval mindig be kell írni a tábla első sorába.

- $\mathbb{Q}$ fölött $f=3x^7+5x^6+4x^5-7x+1$, $c=2$: a sor $3,\,11,\,26,\,52,\,104,\,208,\,409\mid819$, tehát $f(2)=819$.
- $\mathbb{Z}_5$ fölött $f=3x^7+3x^6+4x^5+3x+1$, $c=1$: $f(1)=14\equiv4$. $\mathbb{Z}_3$ fölött $f=2x^7+x^6+2x^3+x^2+1$, $c=2$: sor $2,\,2,\,1,\,2,\,0,\,1,\,2\mid2$ (minden lépés után redukálunk mod $3$): $f(2)=2$. $\mathbb{Z}_2$ fölött $f=x^7+x^6+x^5+x^2+x+1$, $c=1$: hat tag, $f(1)=0$.
- $\mathbb{C}[x]$-ben (komplex $c$) ugyanígy: $x^4-3x^3+6x^2-10x+16$ értéke $c=4$-nél $136$; $x^5+(1+2i)x^4-(1+3i)x^2+7$ értéke $c=-2-i$-nél $-1-44i$; $x^4-3ix^3-4x^2+5ix-1$ értéke $c=1+2i$-nél $-12-2i$.

**Típus 2: hányados és maradék $x-c$-vel (Horner-módszer).** $f=3x^5+2x^2-7x+2$ (együtthatók $3,0,0,2,-7,2$):

| $g$ és gyűrű | hányados | maradék |
|---|---|---|
| $x-3$, $\mathbb{Z}$ | $3x^4+9x^3+27x^2+83x+242$ | $728$ |
| $x+2$, $\mathbb{Z}$ ($c=-2$) | $3x^4-6x^3+12x^2-22x+37$ | $-72$ |
| $x-\tfrac12$, $\mathbb{Q}$ | $3x^4+\tfrac32x^3+\tfrac34x^2+\tfrac{19}{8}x-\tfrac{93}{16}$ | $-\tfrac{29}{32}$ |
| $x-3$, $\mathbb{Z}_3$ ($c\equiv0$) | $2x+2$ | $2$ |
| $x-3$, $\mathbb{Z}_5$ | $3x^4+4x^3+2x^2+3x+2$ | $3$ |

A $\mathbb{Z}_3$ esetben $c=3\equiv0$, $f\equiv2x^2+2x+2$, és $x(2x+2)+2=f$. Komplex $c$-vel: $4x^3+x^2$ osztva $x+1+i$-vel ($c=-1-i$): hányados $4x^2-(3+4i)x+(-1+7i)$, maradék $8-6i$; $x^3-x^2-x$ osztva $x-1+2i$-vel ($c=1-2i$): hányados $x^2-2ix-(5+2i)$, maradék $-9+8i$.

**Típus 3: paraméter, hogy $x-c\mid f$.** $x^5+3x^4+5x+p$ osztható $x-2$-vel $\Leftrightarrow f(2)=0$; $32+48+10+p=0$, tehát $p=-90$.

**Típus 4: polinom felírása $x-a$ hatványaiban** (ismételt Horner-osztás, a maradékok adják $c_0,c_1,\dots$): $x^4+2x^3-3x^2-4x+1=(x+1)^4-2(x+1)^3-3(x+1)^2+4(x+1)+1$ ($a=-1$; a maradékok $1,4,-3,-2,1$), és $x^5=(x-1)^5+5(x-1)^4+10(x-1)^3+10(x-1)^2+5(x-1)+1$.

**Tipikus hibák:** $c$ előjele ($x+2$-nél $c=-2$); kihagyott nulla együtthatók; $\mathbb{Z}_n$ fölött a redukció elmaradása; $x-1/2$-nél a törtek hibás kezelése.

## Kapocs

- [[concepts/dimatii/helyettesitesi-ertek-es-polinomfuggveny]] — az itt kiszámított mennyiség
- [[concepts/dimatii/gyoktenyezo-es-gyokok-szama]] — a gyöktényező leválasztásának tétele
- [[concepts/dimatii/polinomok-maradekos-osztasa]] — a Horner-elrendezés az $(x-c)$-vel való maradékos osztás elvégzése
- [[concepts/dimatii/lagrange-interpolacio]] — az interpolációs polinom ellenőrzése Horner-táblákkal
- [[concepts/dimatii/gyok-multiplicitasa]] — a többszörös gyökök vizsgálata az ismételt osztással és a deriválttal
