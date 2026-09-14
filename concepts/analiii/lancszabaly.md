---
tags: [concept]
sources: [SimonP-Anal2.pdf, 05_ea_An3_2022_tavasz.pdf]
references: ["Simon Péter: Analízis II., 4.1.4. Tétel, 4.2. i), vi), vii) megjegyzés"]
derivation: source
updated: 2026-09-14
---

# Láncszabály

Összetett függvény deriváltja a két Jacobi-mátrix szorzata: $(f \circ g)'(a) = f'(g(a))\cdot g'(a)$ — a többváltozós differenciálszámítás legfontosabb művelet-tétele.

## Tartalom

### A tétel

Legyen $g \in \mathbb{R}^n \to \mathbb{R}^m$, $f \in \mathbb{R}^m \to \mathbb{R}^s$, továbbá $a \in D_g$ olyan, hogy $g(a) \in D_f$, valamint $g \in D\{a\}$ és $f \in D\{g(a)\}$. Ekkor $f \circ g \in D\{a\}$, és

$$(f \circ g)'(a) = f'(g(a))\cdot g'(a).$$

A jobb oldal $\mathbb{R}^{s \times m}$ és $\mathbb{R}^{m \times n}$ mátrixok szorzata, tehát $\mathbb{R}^{s \times n}$-beli — pontosan az a típus, amit egy $\mathbb{R}^n \to \mathbb{R}^s$ függvény deriváltjától várunk. **A tétel tartalma ezért nem a képlet, hanem az, hogy a képlet típushelyes:** a mátrixszorzás nem kommutatív, a sorrend kötött.

### Miért működik

A bizonyítás a $g$ megváltozását helyettesíti be az $f$ megváltozásába:

$$(f\circ g)(a+x) - (f\circ g)(a) = f'(g(a))\big(g'(a)x + \eta(x)\|x\|\big) + \tilde\eta\big(g(a+x)-g(a)\big)\cdot\|g'(a)x + \|x\|\eta(x)\|.$$

A maradék $\varphi(x)$ nullához tartását három lépés adja: (i) $\|f'(g(a))\eta(x)\| \le q\|\eta(x)\| \to 0$ az $f'(g(a))$ mátrixnormájával; (ii) $g$ folytonos $a$-ban, ezért $g(a+x) - g(a) \to 0$, amiből $\tilde\eta(g(a+x)-g(a)) \to 0$; (iii) a harmadik tag hányadosa a $g'(a)$ normájával felülről $Q + \|\eta(x)\|$-nal becsülhető, tehát korlátos. A **belső pont** feltétel itt is előfeltétel: a $g$ folytonossága miatt az $r$ sugár úgy választható, hogy $g[K_r(a)] \subset K_\delta(g(a)) \subset D_f$, azaz $a \in \operatorname{int} D_{f \circ g}$.

### A gyakorlatban használt alakok

**Skalárértékű külső függvény, egyváltozós belső** ($n = s = 1$): ha $g \in \mathbb{R} \to \mathbb{R}^m$, $f \in \mathbb{R}^m \to \mathbb{R}$, akkor

$$(f \circ g)'(a) = \langle \operatorname{grad} f(g(a)),\, g'(a)\rangle.$$

**Parciális deriváltakkal kiírva:** ha $g = (g_1, \dots, g_n) \in \mathbb{R}^s \to \mathbb{R}^n$ és $f \in \mathbb{R}^n \to \mathbb{R}$, akkor

$$\partial_k (f\circ g)(a) = \sum_{j=1}^n \partial_j f(g(a))\cdot \partial_k g_j(a) \qquad (k = 1, \dots, s).$$

Ez a mátrixszorzás $k$-adik oszlopának kiírása; a szokásos $\frac{\partial}{\partial x_k} = \sum_j \frac{\partial f}{\partial y_j}\frac{\partial y_j}{\partial x_k}$ formula.

### Az iránymenti derivált mint következmény

A $t \mapsto a + te$ függvény differenciálható és deriváltja $e$, ezért a láncszabály szerint az $f_e(t) := f(a+te)$ függvényre

$$\partial_e f(a) = f_e'(0) = f'(a)e.$$

Az [[concepts/analiii/iranymenti-derivalt|iránymenti derivált]] és a derivált kapcsolata tehát nem külön tétel, hanem a láncszabály egysoros folyománya.

### Ellenőrző példa

$g(t) := (t, t^2)$, $f(x,y) := x + y$. Ekkor $(f\circ g)(t) = t + t^2$, tehát $(f\circ g)'(t) = 1 + 2t$. Másfelől $g'(t) = (1, 2t)$ és $\operatorname{grad} f \equiv (1,1)$, így $\langle (1,1), (1,2t)\rangle = 1 + 2t$. Egyezik.

### Egy összetettebb példa: ellenőrzés közvetlen behelyettesítéssel

Legyen $f(u,v,w) := u + vw$ és $g(x_1,x_2,x_3) := \bigl(x_1^2+x_2^2+x_3^2,\ x_1x_2x_3,\ x_1\bigr) \in \mathbb{R}^3 \to \mathbb{R}^3$. Mivel $f$ és $g$ koordinátafüggvényei polinomok, mindkettő [[concepts/analiii/differencialasi-szabalyok-tobbvaltozos|mindenütt differenciálható]], tehát $F := f \circ g \in \mathbb{R}^3 \to \mathbb{R}$ is az, és a láncszabály szerint $F'(x) = f'(g(x))\cdot g'(x)$.

Mivel $f'(u,v,w) = \begin{bmatrix} 1 & w & v\end{bmatrix}$ és

$$g'(x) = \begin{bmatrix} 2x_1 & 2x_2 & 2x_3 \\ x_2x_3 & x_1x_3 & x_1x_2 \\ 1 & 0 & 0\end{bmatrix},$$

behelyettesítve $f'(g(x)) = \begin{bmatrix}1 & x_1 & x_1x_2x_3\end{bmatrix}$, és a szorzat elvégzése után

$$F'(x) = \begin{bmatrix} 2x_1 + 2x_1x_2x_3 & 2x_2 + x_1^2x_3 & 2x_3 + x_1^2x_2\end{bmatrix}.$$

**Ellenőrzés.** Kis $n$, $m$, $s$ esetén a láncszabály megkerülhető: $F$ közvetlenül felírható a behelyettesítéssel, és tagonként deriválható. Itt $F(x) = g_1(x) + g_2(x)g_3(x) = x_1^2+x_2^2+x_3^2 + x_1^2x_2x_3$, amiből

$$\partial_1 F(x) = 2x_1 + 2x_1x_2x_3, \qquad \partial_2 F(x) = 2x_2 + x_1^2x_3, \qquad \partial_3 F(x) = 2x_3 + x_1^2x_2,$$

ami pontosan megegyezik a láncszabállyal kapott eredménnyel. A közvetlen módszer itt egyszerűbb volt, de bonyolultabb $f$, $g$ esetén a láncszabály lényegesen kevesebb számolást igényel — ez a gyakorlati oka annak, hogy nem behelyettesítéssel, hanem a tétellel dolgozunk.

## Kapocs

- [[concepts/analiii/differencialasi-szabalyok-tobbvaltozos]] — a szorzat- és hányadosszabály, amelyek ennek speciális esetei.
- [[concepts/analiii/jacobi-matrix]] — a szorzandó mátrixok.
- [[concepts/analiii/iranymenti-derivalt]] — a $\partial_e f(a) = f'(a)e$ formula innen adódik.
- [[concepts/analiii/nivofelulet-es-gradiens]] — a gradiens merőlegessége szintén láncszabály-következmény.
- [[concepts/analiii/tobbvaltozos-taylor-formula]] — a bizonyítása az $F(t) = f(a+th)$ függvényre alkalmazza a láncszabályt.
- [[concepts/analii/derivalasi-szabalyok]] — az egyváltozós összetett-függvény-szabály.
