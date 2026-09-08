---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 3. előadás"]
derivation: source
updated: 2026-09-04
---

# Konvex és konkáv függvények

A konvexitás a függvénygrafikon „húr alatti/feletti" viselkedését írja le. Differenciálszámítással karakterizálható: $f$ konvex $\Leftrightarrow$ $f'$ monoton növekvő $\Leftrightarrow$ $f'' \geq 0$.

## Definíció

**Definíció.** Az $f : I \to \mathbb{R}$ függvény **konvex az $I$ intervallumon**, ha

$$\forall a, b \in I,\ a < b \text{ esetén} \qquad f(x) \leq \frac{f(b)-f(a)}{b-a}(x-a) + f(a) \quad (\forall x \in (a,b)).$$

Ha $(*)$-ban $\leq$ helyett $<$ áll, akkor $f$-et $I$-n **szigorúan konvexnek**, ha $\geq$, ill. $>$ áll, akkor $f$-et **konkávnak**, ill. **szigorúan konkávnak** nevezzük.

**Megjegyzések.**

1. $f$ konkáv $I$-n $\Leftrightarrow$ $-f$ konvex $I$-n.
2. Az abs függvény konvex, de nem szigorúan konvex $\mathbb{R}$-en.
3. Az $f(x) := cx + d$ ($x \in \mathbb{R}$, $c, d \in \mathbb{R}$) függvény egyszerre konvex és konkáv $\mathbb{R}$-en, de nem szigorú értelemben.

## Ekvivalens jellemzés: $\lambda$-feltétel

**Tétel.** Az $f \in \mathbb{R} \to \mathbb{R}$ függvény akkor és csak akkor konvex az $I \subset \mathbb{R}$ intervallumon, ha

$$\forall a, b \in I,\ a < b \text{ és } \forall \lambda \in (0,1) \text{ esetén} \quad f\bigl(\lambda a + (1-\lambda)b\bigr) \leq \lambda f(a) + (1-\lambda)f(b).$$

**Bizonyítás.** L. Analízis I. 12. előadás. $\blacksquare$

**Megjegyzés.** Szigorúan konvex, konkáv és szigorúan konkáv függvényekre hasonló állítások érvényesek.

## Jensen-egyenlőtlenség

**Tétel (Jensen-egyenlőtlenség).** Az $f$ függvény akkor és csak akkor konvex az $I$ intervallumon, ha bármely $n \in \mathbb{N}^+$ mellett tetszőleges $a_1, \ldots, a_n \in I$ esetén fennáll az

$$f(\lambda_1 a_1 + \cdots + \lambda_n a_n) \leq \lambda_1 f(a_1) + \cdots + \lambda_n f(a_n)$$

egyenlőtlenség minden olyan $\lambda_1, \ldots, \lambda_n > 0$ számokra, amelyekre $\lambda_1 + \cdots + \lambda_n = 1$.

Ha $f$ szigorúan konvex, akkor szigorú egyenlőtlenség áll, feltéve, hogy az $a_k$-k nem mind egyenlők.

**Alkalmazás — számtani és négyzetes közép közötti egyenlőtlenség.** Legyen $n \in \mathbb{N}^+$ és $a_1, \ldots, a_n \in \mathbb{R}$. Ekkor

$$\frac{a_1 + \cdots + a_n}{n} \leq \sqrt{\frac{a_1^2 + \cdots + a_n^2}{n}}.$$

**Bizonyítás.** Az $f(x) := x^2$ ($x \in \mathbb{R}$) függvény szigorúan konvex $\mathbb{R}$-en. A Jensen-egyenlőtlenséget $\lambda_1 = \cdots = \lambda_n = \frac{1}{n}$ választással alkalmazva:

$$\left(\frac{a_1 + \cdots + a_n}{n}\right)^2 \leq \frac{a_1^2 + \cdots + a_n^2}{n}.$$

Ebből négyzetgyököt vonva adódik az egyenlőtlenség. Egyenlőség pontosan akkor áll, ha $a_1 = \cdots = a_n$. $\blacksquare$

## Konvexitás és a derivált kapcsolata

**Tétel.** T.f.h. $I \subset \mathbb{R}$ nyílt intervallum és $f \in D(I)$. Ekkor

$$f \text{ konvex } I\text{-n} \iff f' \nearrow I\text{-n.}$$

**Megjegyzés.** $\nearrow$ helyett szigorúan konvex esetben $\uparrow$, konkáv esetben $\searrow$ és szigorúan konkáv esetben $\downarrow$ áll.

**Bizonyítás** ($\Rightarrow$). Legyen $u, v \in I$, $u < v$ tetszőleges és $x \in (u, v)$ is tetszőleges. T.f.h. $f$ konvex $I$-n. Ekkor

$$f(x) \leq \frac{f(v)-f(u)}{v-u}(x-u) + f(u) \quad \text{és} \quad f(x) \leq \frac{f(v)-f(u)}{v-u}(x-v) + f(v).$$

Egyszerű átrendezésekkel azt kapjuk, hogy

$$\frac{f(x)-f(u)}{x-u} \leq \frac{f(v)-f(u)}{v-u} \leq \frac{f(x)-f(v)}{x-v}.$$

Vegyük itt az $x \to u$, ill. az $x \to v$ határátmenetet: $f'(u) \leq \frac{f(v)-f(u)}{v-u} \leq f'(v)$. Tehát $f'$ monoton növekvő $I$-n.

**Bizonyítás** ($\Leftarrow$). T.f.h. $f'$ monoton növekvő $I$-n. Legyen $a, b \in I$, $a < b$ tetszőleges és $x \in (a, b)$. A Lagrange-féle középértéktétel szerint $\exists\,\xi_1 \in (a, x)$ és $\exists\,\xi_2 \in (x, b)$:

$$f'(\xi_1) = \frac{f(x)-f(a)}{x-a} \quad \text{és} \quad f'(\xi_2) = \frac{f(b)-f(x)}{b-x}.$$

Mivel $f' \nearrow$ $I$-n, ezért $f'(\xi_1) \leq f'(\xi_2)$, vagyis $\frac{f(x)-f(a)}{x-a} \leq \frac{f(b)-f(x)}{b-x}$. Átrendezve azt kapjuk, hogy $f(x) \leq \frac{f(b)-f(a)}{b-a}(x-a) + f(a)$, tehát $f$ konvex $I$-n. $\blacksquare$

## Konvexitás és a második derivált kapcsolata

**Tétel.** T.f.h. $I \subset \mathbb{R}$ nyílt intervallum és $f \in D^2(I)$. Ekkor

1. $f$ konvex $I$-n $\Leftrightarrow$ $f'' \geq 0$ $I$-n.  
   $f$ konkáv $I$-n $\Leftrightarrow$ $f'' \leq 0$ $I$-n.
2. Ha $f'' > 0$ $I$-n $\Rightarrow$ $f$ szigorúan konvex $I$-n.  
   Ha $f'' < 0$ $I$-n $\Rightarrow$ $f$ szigorúan konkáv $I$-n.

## Példák

| Függvény | $f''$ | Konvexitás |
|----------|-------|------------|
| $e^x$ ($x \in \mathbb{R}$) | $e^x > 0$ | Szigorúan konvex $\mathbb{R}$-en |
| $\ln x$ ($x > 0$) | $-\frac{1}{x^2} < 0$ | Szigorúan konkáv $\mathbb{R}^+$-on |
| $a^x$ ($x > 0$, $0 < a \neq 1$) | $a^x \cdot \ln^2 a > 0$ | Szigorúan konvex $\mathbb{R}$-en |
| $\log_a x$ ($x > 0$, $0 < a < 1$) | $> 0$ | Szigorúan konvex $\mathbb{R}^+$-on |
| $\log_a x$ ($x > 0$, $a > 1$) | $< 0$ | Szigorúan konkáv $\mathbb{R}^+$-on |
| $x^\alpha$ ($x > 0$, $\alpha < 0$ v. $\alpha > 1$) | $> 0$ | Szigorúan konvex $\mathbb{R}^+$-on |
| $x^\alpha$ ($x > 0$, $0 < \alpha < 1$) | $< 0$ | Szigorúan konkáv $\mathbb{R}^+$-on |

## Konvexitás és érintő kapcsolata

**Tétel.** T.f.h. $I \subset \mathbb{R}$ nyílt intervallum és $f \in D(I)$. Ekkor

$$f \text{ konvex [konkáv] } I\text{-n} \iff \forall a \in I :\ f(x) \geq e_{f,a}(x)\ \ [f(x) \leq e_{f,a}(x)] \quad (x \in I),$$

vagyis $f$ grafikonja egy tetszőleges pontjában húzott érintője felett [alatt] halad.

**Bizonyítás** ($\Rightarrow$, konvex eset). Azt már tudjuk, hogy ekkor $f' \nearrow$ $I$-n. Legyen $a \in I$ és $\varphi(x) := f(x) - e_{f,a}(x)$ ($x \in I$). Ekkor $\varphi \in D(I)$ és $\varphi'(x) = f'(x) - f'(a)$ ($x \in I$). Mivel $\varphi(a) = 0$ és $f' \nearrow$ $I$-n, ezért $\varphi'(x) \leq 0 \leq \varphi'(t)$ ($x, t \in I$, $x \leq a \leq t$). Így $\varphi \searrow$ $I \cap (-\infty, a]$-n és $\varphi \nearrow$ $I \cap [a, +\infty)$-n, tehát $\varphi$-nek $a$-ban abszolút minimuma van. $\varphi(a) = 0$ miatt $\varphi \geq 0$ $I$-n, azaz $f(x) \geq e_{f,a}(x)$ ($x \in I$). $\blacksquare$

## Konvexitás, folytonosság és deriválhatóság kapcsolata

**Tétel.** Tegyük fel, hogy az $f$ függvény konvex [konkáv] az $I$ nyílt intervallumon. Ekkor

1. $f$ folytonos $I$-n.
2. $\forall a \in I$ pontban $\exists f'_-(a)$ és $\exists f'_+(a)$.

**Bizonyítás.** Nélkül. $\blacksquare$

## Kapocs

- [[concepts/analii/monotonitas]] — $f' \nearrow$ $\Leftrightarrow$ $f$ konvex: a két fogalom szoros kapcsolata
- [[concepts/analii/lokalis-szelsertekek]] — szélsőértékek és a konvexitás/konkávitás összefüggése
- [[concepts/analii/inflexios-pont]] — ahol a konvexitás iránya megváltozik
- [[concepts/analii/erintofuggveny]] — érintő definíciója; konvex függvény grafikonja az érintő felett halad
- [[concepts/analii/magasabb-rendu-derivaltak]] — $f''$ előjele a konvexitás meghatározásában
- [[concepts/analii/taylor-polinom]] — Taylor-polinom és a konvex függvény közelítése
