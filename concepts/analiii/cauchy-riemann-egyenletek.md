---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 3.2. xv) megjegyzés"]
derivation: source
updated: 2026-09-07
---

# Cauchy–Riemann-egyenletek

Egy $f \in \mathbb{C} \to \mathbb{C}$ függvény komplex értelemben pontosan akkor differenciálható, ha valós és képzetes része $\mathbb{R}^2 \to \mathbb{R}$ függvényként differenciálható, **és** a két gradiens között fennáll a Cauchy–Riemann-féle összefüggés. A komplex differenciálhatóság tehát valós differenciálhatóság plusz egy szigorú lineáris megkötés.

## Tartalom

### Az azonosítás

Legyen $f \in \mathbb{C} \to \mathbb{C}$, és bontsuk fel valós és képzetes részre:

$$f_1(z) := \operatorname{Re} f(z), \qquad f_2(z) := \operatorname{Im} f(z), \qquad f = f_1 + \imath f_2 .$$

Egy $g \in \mathbb{C} \to \mathbb{R}$ függvényhez hozzárendelhető a $G(x,y) := g(x + \imath y)$ képlettel egy $G \in \mathbb{R}^2 \to \mathbb{R}$ függvény; a továbbiakban a $G$-re is a $g$ jelölést használjuk. Így $f_1, f_2$ egyszerre tekinthető $\mathbb{C} \to \mathbb{R}$ és $\mathbb{R}^2 \to \mathbb{R}$ leképezésnek.

Az egyetlen érdemi különbség: $\mathbb{C}$-ben a derivált egy **komplex számmal való szorzás**, $\mathbb{R}^2$-ben pedig egy tetszőleges $2\times 2$-es valós mátrix. A komplex differenciálhatóság az a megkötés, hogy a Jacobi-mátrix éppen egy komplex szorzás mátrixa legyen.

### Komplex differenciálhatóságból valós

Legyen $a = a_1 + \imath a_2 \in \mathbb{C}$, és tegyük fel, hogy $f \in D\{a\}$ komplex értelemben, $f'(a) = d_1 + \imath d_2$ ($d_1, d_2 \in \mathbb{R}$). A definíció szerint alkalmas $\eta = \eta_1 + \imath\eta_2$, $\lim_a \eta = 0$ függvénnyel

$$f(a+\delta) - f(a) = f'(a)\cdot\delta + \eta(\delta)\cdot|\delta| \qquad (\delta \in \mathbb{C},\ a+\delta \in D_f).$$

A $\delta = x + \imath y$ felbontással, a **komplex szorzást kifejtve**

$$(d_1 + \imath d_2)(x + \imath y) = (d_1 x - d_2 y) + \imath(d_2 x + d_1 y),$$

és a valós, illetve képzetes részeket különválasztva ($|\delta| = \sqrt{x^2+y^2} = \|(x,y)\|_2$):

$$f_1(a_1+x, a_2+y) - f_1(a_1,a_2) = \langle (d_1, -d_2), (x,y)\rangle + \eta_1(x,y)\cdot\|(x,y)\|_2,$$
$$f_2(a_1+x, a_2+y) - f_2(a_1,a_2) = \langle (d_2, d_1), (x,y)\rangle + \eta_2(x,y)\cdot\|(x,y)\|_2 .$$

Mivel $\eta_1, \eta_2 \to 0$, ez pontosan azt jelenti, hogy $f_1, f_2 \in D\{(a_1,a_2)\}$ valós értelemben, és

$$\operatorname{grad} f_1(a_1,a_2) = (d_1, -d_2), \qquad \operatorname{grad} f_2(a_1,a_2) = (d_2, d_1),$$

azaz

$$\partial_1 f_1 = d_1, \quad \partial_2 f_1 = -d_2, \quad \partial_1 f_2 = d_2, \quad \partial_2 f_2 = d_1 \qquad \text{(mind } (a_1,a_2)\text{-ben)}.$$

### Az ekvivalencia és az egyenletek

A gondolatmenet megfordítható, tehát igaz az alábbi **ekvivalencia**: $f \in D\{a\}$ komplex értelemben akkor és csak akkor, ha $f_1, f_2 \in D\{(a_1,a_2)\}$ valós értelemben, és teljesülnek a **Cauchy–Riemann-egyenletek**:

$$\partial_1 f_1(a_1,a_2) = \partial_2 f_2(a_1,a_2), \qquad \partial_1 f_2(a_1,a_2) = -\partial_2 f_1(a_1,a_2).$$

Klasszikus $u := f_1$, $v := f_2$, $x, y$ jelöléssel: $u_x = v_y$ és $v_x = -u_y$.

A derivált innen kétféleképp is kiolvasható:

$$f'(a) = \partial_1 f_1(a_1,a_2) - \imath\,\partial_2 f_1(a_1,a_2) = \partial_2 f_2(a_1,a_2) + \imath\,\partial_1 f_2(a_1,a_2).$$

### Mit jelent a megkötés

A valós Jacobi-mátrix a fentiek szerint

$$\begin{pmatrix} d_1 & -d_2 \\ d_2 & d_1\end{pmatrix},$$

azaz forgatva nyújtás. A komplex differenciálhatóság tehát azt követeli, hogy $f$ lokálisan **szögtartó** (konform) módon viselkedjen — ez a négy szabad mátrixelemet kettőre szorítja le, és ez a szigorúság magyarázza, miért olyan erősek a komplex függvénytan tételei a valós többváltozós analízis tételeihez képest.

## Kapocs

- [[concepts/analiii/frechet-derivalt]] — a differenciálhatóság definíciója, amelyet mindkét oldalon alkalmazunk.
- [[concepts/analiii/gradiens-parcialis-derivaltakbol]] — a gradiens és a parciális deriváltak azonosítása, amelyben az egyenletek megfogalmazódnak.
- [[concepts/analiii/koordinatafuggvenyek-differencialhatosaga]] — a valós és képzetes részre bontás mint koordinátafüggvényekre bontás.
- [[concepts/analiii/goursat-lemma]] — a rotációmentesség és a Goursat-lemma valós megfelelője a komplex függvénytan Cauchy-tételének.
- [[concepts/analiii/altalanos-vonalintegral]] — a komplex vonalintegrál mint a valós eset bilineáris szorzással kapott változata.
