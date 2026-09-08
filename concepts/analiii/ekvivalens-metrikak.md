---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 1.4. vi)–ix) és 1.8. ii)–v) megjegyzés"]
derivation: source
updated: 2026-09-07
---

# Ekvivalens metrikák

Két metrika ekvivalens, ha konstans szorzókkal kölcsönösen becsülhetők egymással. Az ekvivalencia pontosan azt garantálja, hogy a rájuk épülő fogalmak — konvergencia, határérték, nyíltság, zártság, kompaktság — nem változnak, ha az egyik metrikát a másikra cseréljük.

## Tartalom

### Definíció

Legyen $X \neq \emptyset$ és $\rho, \sigma : X^2 \to [0,+\infty)$ metrika. A $\rho$ és a $\sigma$ **ekvivalens** (jelben $\rho \sim \sigma$), ha alkalmas $c, C > 0$ számokkal

$$c\cdot\rho(x,y) \leq \sigma(x,y) \leq C\cdot\rho(x,y) \qquad (x,y \in X).$$

Az $X$-en értelmezett metrikák $M$ halmazán a $\sim$ reláció ekvivalenciareláció — innen ered az elnevezés.

### A $\rho_p$ metrikák $p \geq 1$ esetén ekvivalensek

**Állítás.** A $(\mathbb{K}^n,\rho_p)$ terekben bármely két $\rho_p$, $\rho_q$ metrika ekvivalens, ha $1 \leq p,q \leq +\infty$.

*Bizonyítás.* Elég $\rho_p \sim \rho_\infty$-t belátni, mert $\sim$ tranzitív. Legyen $1 \leq p < +\infty$. Egyrészt

$$\rho_p(x,y) = \Bigl(\sum_{i=1}^n |x_i-y_i|^p\Bigr)^{1/p} \leq \bigl(n\cdot\rho_\infty(x,y)^p\bigr)^{1/p} = n^{1/p}\cdot\rho_\infty(x,y),$$

másrészt minden $i$-re $\rho_p(x,y) \geq |x_i-y_i|$, tehát $\rho_p(x,y) \geq \rho_\infty(x,y)$. Így

$$\rho_\infty(x,y) \leq \rho_p(x,y) \leq n^{1/p}\cdot\rho_\infty(x,y). \qquad\blacksquare$$

Ebből az általános becslés is adódik:

$$n^{-1/p}\cdot\rho_p(x,y) \leq \rho_q(x,y) \leq n^{1/q}\cdot\rho_p(x,y) \qquad (x,y\in\mathbb{K}^n,\ 1\leq p,q<+\infty).$$

### $p < 1$ esetén elromlik

A $p \geq 1$ kikötés nem véletlen. Legyen $0<p<q<1$ és a $(\mathbb{K}^2,\rho_p)$ terekben

$$x := (u,0)\ (u>0), \qquad y := (0,0),$$

amikor is $\rho_p(x,y) = u^p$ és $\rho_q(x,y)=u^q$. Ha $\rho_p \sim \rho_q$ teljesülne, akkor valamilyen $C>0$-val $u^p \leq Cu^q$, azaz $u^{p-q} \leq C$ állna minden $u>0$-ra. Ez lehetetlen, hiszen $p-q<0$ miatt $u^{p-q}\to+\infty$, ha $u \to 0+$.

### Mit őriz meg az ekvivalencia?

**Konvergencia.** Ha $\rho \sim \sigma$, akkor tetszőleges $(x_n) : \mathbb{N}\to X$ sorozatra és $\alpha \in X$-re

$$c\cdot\rho(x_n,\alpha) \leq \sigma(x_n,\alpha) \leq C\cdot\rho(x_n,\alpha),$$

így $\lim\rho(x_n,\alpha)=0 \iff \lim\sigma(x_n,\alpha)=0$. Ekvivalens metrikák tehát ugyanazokat a sorozatokat találják konvergensnek, ugyanazzal a határértékkel.

**Topológia.** $\mathcal{T}_\rho(X) = \mathcal{T}_\sigma(X)$, azaz ugyanazok a halmazok nyíltak.

*Bizonyítás.* A becslésekből $K^{(\rho)}_{r/C}(a) \subset K^{(\sigma)}_r(a)$ és $K^{(\sigma)}_{cr}(a) \subset K^{(\rho)}_r(a)$: ha ugyanis $\rho(x,a)<r/C$, akkor $\sigma(x,a) \leq C\rho(x,a) < r$. Így egy $K^{(\sigma)}_r(a) \subset A$ tartalmazásból $K^{(\rho)}_{r/C}(a)\subset A$ következik és fordítva; tehát az $a \in \operatorname{int}A$ tény, és így az $\operatorname{int}A = A$ egyenlőség is, független attól, melyik metrikában dolgozunk. $\blacksquare$

**Zártság és kompaktság.** A zárt halmazok a nyíltak komplementerei, a kompaktság pedig a konvergencián keresztül fogalmazható meg, ezért $\rho\sim\sigma$ esetén

$$\mathcal{C}_\rho(X) = \mathcal{C}_\sigma(X), \qquad \mathcal{K}_\rho(X)=\mathcal{K}_\sigma(X),$$

ahol $\mathcal{C}_\delta$, illetve $\mathcal{K}_\delta$ a $\delta$ szerint zárt, illetve kompakt halmazok rendszere.

**Következmény.** $(\mathbb{K}^n,\rho_p)$-ben egy $A \subset \mathbb{K}^n$ halmaz nyíltsága, zártsága és kompaktsága ugyanazt jelenti minden $1 \leq p \leq +\infty$ mellett. Ezért használhatjuk a $\mathbb{K}^n$-nel kapcsolatos vizsgálódásokban szabadon a $\rho_1$, $\rho_2$, $\rho_\infty$ metrikák bármelyikét — többnyire a $\rho_2$ euklideszi metrikát.

### Geometriai kép

Az ekvivalencia a környezetek egymásba illeszthetőségét jelenti: bármely $a$ és $r>0$ esetén vannak olyan $u,v>0$, hogy

$$K^{(\sigma)}_u(a) \subset K^{(\rho)}_r(a) \subset K^{(\sigma)}_v(a).$$

$\mathbb{R}^2$-ben ez azt mondja, hogy az $a$ középpontú $\rho_1$-**rombuszok**, $\rho_2$-**körlemezek** és $\rho_\infty$-**négyzetek** kölcsönösen egymásba illeszthetők.

## Kapocs

- [[concepts/analiii/ekvivalens-normak]] — a normákra szóló változat; véges dimenzióban minden norma ekvivalens
- [[concepts/analiii/topologikus-ter]] — a $\mathcal{T}_\rho$ topológia, amelyet az ekvivalencia megőriz
- [[concepts/analiii/metrikabol-uj-metrika]] — transzformációval kapott metrikák, amelyek nem mind ekvivalensek az eredetivel
- [[concepts/analiii/metrikus-terek-szorzata]] — a $\rho_p$ szorzatmetrikák, amelyekre az állítás vonatkozik
- [[concepts/analiii/konvergencia-metrikus-terben]] — a fogalom, amit az ekvivalencia változatlanul hagy
