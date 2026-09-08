---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 1.2. viii)–xiv) megjegyzés"]
derivation: source
updated: 2026-09-07
---

# Új metrikák előállítása meglévőkből

Egy meglévő metrikából két mechanikus úton kaphatunk újat: kompozícióval egy alkalmas $f : [0,\infty)\to[0,\infty)$ függvénnyel, illetve leszűkítéssel egy részhalmazra. Az első teszi lehetővé, hogy minden metrikát **korlátossá** alakítsunk, és így például a kibővített $\overline{\mathbb{R}}$ elemei között is távolságot értelmezzünk.

## Tartalom

### Metrika kompozíciója monoton szubadditív függvénnyel

**Tétel.** Legyen $f : [0,+\infty) \to [0,+\infty)$ olyan, hogy

- $\alpha)$ $f$ monoton növekvő: $f(x) \leq f(y)$, ha $x \leq y$;
- $\beta)$ $f(x)=0 \iff x=0$;
- $\gamma)$ $f$ szubadditív: $f(x+y) \leq f(x)+f(y)$.

Ekkor tetszőleges $(X,\rho)$ metrikus tér esetén $\sigma(x,y) := f\bigl(\rho(x,y)\bigr)$ is metrika $X$-en.

*Bizonyítás.* A nemnegativitás $R_f \subset [0,\infty)$ miatt áll. Ha $\sigma(x,y)=0$, akkor $\beta)$ szerint $\rho(x,y)=0$, tehát $x=y$. A szimmetria $\rho$ szimmetriájából öröklődik. Végül a háromszög-egyenlőtlenséghez $\rho(x,y) \leq \rho(x,z)+\rho(y,z)$ és $\alpha)$ alapján

$$\sigma(x,y) = f\bigl(\rho(x,y)\bigr) \leq f\bigl(\rho(x,z)+\rho(y,z)\bigr) \overset{\gamma)}{\leq} f\bigl(\rho(x,z)\bigr) + f\bigl(\rho(y,z)\bigr) = \sigma(x,z)+\sigma(y,z). \qquad\blacksquare$$

### A szokásos $f$-ek

Tetszőleges $0 < a \in \mathbb{R}$ és $r \in (0,1]$ mellett kielégíti a feltételeket:

| $f$ | az adódó metrika | korlátos-e |
|---|---|---|
| $f(x)=ax$ | $a\rho$ | nem |
| $f(x)=\dfrac{x}{1+x}$ | $\dfrac{\rho}{1+\rho}$ | igen ($<1$) |
| $f(x)=x^r$ | $\rho^r$, speciálisan $\sqrt{\rho}$ | nem |
| $f(x)=\lg(1+x)$ | $\lg(1+\rho)$ | nem |
| $f(x)=\min\{1,x\}$ | $\min\{1,\rho\}$ | igen ($\leq 1$) |

A monotonitás $g(x)=\frac{x}{1+x}$-re az $x+xy \leq y+xy \iff x \leq y$ átalakításból, a szubadditivitása pedig az

$$\frac{x+y}{1+x+y} = \frac{x}{1+x+y}+\frac{y}{1+x+y} \leq \frac{x}{1+x}+\frac{y}{1+y}$$

becslésből látszik. A $h(x)=x^r$ ($0<r\leq 1$) szubadditivitása az $F(x):=x^r-(x+y)^r+y^r$ függvény vizsgálatából adódik: $F(0)=0$ és $F'(x)=r\bigl(x^{r-1}-(x+y)^{r-1}\bigr) \geq 0$, mert $-1 < r-1 \leq 0$.

**Következmény.** Valós vagy komplex számok távolságát a megszokott $|x-y|$ helyett az

$$\frac{|x-y|}{1+|x-y|}$$

számmal is mérhetnénk — ebben az értelemben bármely két szám távolsága $1$-nél kisebb.

### A kibővített $\overline{\mathbb{R}}$ metrizálása

Az előbbi következmény adja a kulcsot: a $\overline{\mathbb{R}} = \mathbb{R}\cup\{-\infty,+\infty\}$ halmazon

$$\rho(x,y) := \begin{cases}\dfrac{|x-y|}{1+|x-y|} & (x,y \in \mathbb{R})\\[4pt] 1 & (x \in \mathbb{R},\ y=\pm\infty)\\[2pt] 1 & (x=+\infty,\ y=-\infty)\\[2pt] 0 & (x=y=\pm\infty)\end{cases}$$

(és szimmetrikusan) metrika. A korlátos „átskálázás" nélkül a végtelenek nem férnének bele a képbe.

### Metrika leszűkítése: altér

**Állítás.** Ha $(X,\rho)$ metrikus tér és $\emptyset \neq Y \subset X$, akkor a

$$\sigma(x,y) := \rho(x,y) \qquad \bigl((x,y) \in Y^2\bigr)$$

leszűkítés metrika, azaz $(Y,\sigma)$ is metrikus tér — az $(X,\rho)$ tér **altere**.

**Példa.** Legyen $A \neq \emptyset$ és $X := \{f : A\to\mathbb{K} : \sup R_{|f|} < +\infty\}$ a korlátos függvények halmaza a

$$\rho(f,g) := \sup\{|f(x)-g(x)| : x \in A\}$$

metrikával. Ha $A = [a,b]$, akkor $C[a,b] \subset X$, és $\rho$ leszűkítése $C[a,b]$-re éppen a maximumnorma metrikája: $\rho_\infty = \rho|_{C[a,b]^2}$.

## Kapocs

- [[concepts/analiii/metrikus-ter]] — az axiómák, amelyeket a konstrukciók megőriznek
- [[concepts/analiii/ekvivalens-metrikak]] — az $a\rho$ ekvivalens $\rho$-val, a $\rho/(1+\rho)$ általában nem
- [[concepts/analiii/felmetrikus-ter]] — a félmetrikák szuprémumából adódó metrika ugyanezt a $\rho/(1+\rho)$ trükköt használja
- [[concepts/analiii/metrikus-terek-szorzata]] — a másik metrikakonstruáló művelet
