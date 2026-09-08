---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf, SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 4.5.6.1. Tétel"]
derivation: source
updated: 2026-09-07
---

# Paraméteres integrál

Egy $F(t) = \int_a^b f(t,x)\,\mathrm{d}x$ alakú függvény, ahol az integrálás $x$ szerint történik, a $t$ pedig szabad paraméter marad. Alapkérdés: mikor öröklődik $f$ folytonossága $F$-re.

## Tartalom

### A fogalom

Legyen $f$ kétváltozós függvény. A

$$F(t) = \int_{x=a}^{b} f(t,x)\,\mathrm{d}x$$

függvényt **paraméteres integrálnak**, a

$$F(t) = \int_{x=\alpha}^{\beta} f(t,x)\,\mathrm{d}x = \lim_{a \searrow \alpha,\; b \nearrow \beta} \int_{x=a}^{b} f(t,x)\,\mathrm{d}x$$

függvényt **paraméteres improprius integrálnak** nevezzük. Az $x$ az integrálási változó, a $t$ a paraméter: minden rögzített $t$-re egy szám adódik, tehát $F$ a $t$ egyváltozós függvénye.

### Domináns függvény

Improprius esetben a puszta folytonosság nem elég, mert az integrálási tartomány végtelen „széle" felől bármikor beszökhet tömeg. A védekezés egy $t$-től **független** felső korlát:

Egy $g : (\alpha,\beta) \to [0,\infty)$ függvény **dominálja** az $x \mapsto f(t,x)$ paraméteres függvényeket (más szóval $g$ **domináns függvénye** $f$-nek), ha

- $\int_\alpha^\beta g$ konvergens (létezik és véges), és
- bármely $x \in (\alpha,\beta)$ és $t \in I$ esetén $\bigl|f(t,x)\bigr| \leqslant g(x)$.

### Ellenpélda: folytonos $f$, szakadó $F$

Legyen $f : [0,1] \times (-\infty,\infty) \to \mathbb{R}$,

$$f(t,x) = \begin{cases} \dfrac{1}{1 + \left(x - \frac{1}{t}\right)^2} & \text{ha } t > 0,\\[2mm] 0 & \text{ha } t = 0,\end{cases}$$

ekkor

$$F(t) = \int_{-\infty}^{\infty} f(t,x)\,\mathrm{d}x = \begin{cases} \pi & \text{ha } t > 0,\\ 0 & \text{ha } t = 0.\end{cases}$$

Az $f$ függvény folytonos, $F$ mégis szakad a $0$-ban: ahogy $t \searrow 0$, a „púp" a $\frac{1}{t}$ helyre, tehát a végtelenbe vándorol, de a területe végig $\pi$ marad. Nincs olyan integrálható $g$, amely az összes $f(t,\cdot)$-t egyszerre dominálná — pontosan ez hiányzik.

### Tétel (a paraméteres integrál folytonossága)

- **(a)** Legyen $I \subset \mathbb{R}$ intervallum, $a,b \in \mathbb{R}$, és $f : I \times [a,b] \to \mathbb{R}$ folytonos. Ekkor az $F(t) = \int_{x=a}^{b} f(t,x)\,\mathrm{d}x$ paraméteres integrál folytonos.
- **(b)** Tegyük fel, hogy $I \subset \mathbb{R}$ és $(\alpha,\beta) \subset \mathbb{R}$ intervallumok, $f : I \times (\alpha,\beta) \to \mathbb{R}$ folytonos, az $F(t) = \int_{x=\alpha}^{\beta} f(t,x)\,\mathrm{d}x$ improprius integrál minden $t \in I$-re konvergens, és $f$-nek van $g$ domináns függvénye. Ekkor $F$ folytonos.

**Bizonyítás.** Elég (b)-t igazolni, az $I$ egy tetszőleges kompakt $[c,d]$ részintervallumán; ott $F$ egyenletes folytonosságát mutatjuk meg. Legyen $\varepsilon > 0$.

- A dominancia miatt van olyan $\alpha < a < b < \beta$, hogy $\int_\alpha^a g < \frac{\varepsilon}{5}$ és $\int_b^\beta g < \frac{\varepsilon}{5}$ — a két „farok" tehát egyszerre, minden $t$-re kicsi.
- A megmaradó $[c,d]\times[a,b]$ **kompakt** téglalapon $f$ egyenletesen folytonos; vegyünk $\frac{\varepsilon}{5(b-a)}$-hoz $\delta$-t.
- Ha $|t_1 - t_2| < \delta$, akkor

$$\bigl|F(t_1) - F(t_2)\bigr| \leqslant \int_\alpha^\beta \bigl|f(t_1,x) - f(t_2,x)\bigr|\,\mathrm{d}x < \int_\alpha^a 2g + \int_a^b \frac{\varepsilon}{5(b-a)} + \int_b^\beta 2g < \frac{2\varepsilon}{5} + \frac{\varepsilon}{5} + \frac{2\varepsilon}{5} = \varepsilon.$$

Tehát $F$ egyenletesen folytonos minden $[c,d] \subset I$-n, így folytonos $I$-n.

A bizonyítás mintája — *farkak levágása a domináns függvénnyel, kompakt magon egyenletes folytonosság* — a fejezet mindhárom tételében visszatér.

### Vektorparaméteres változat

A paraméter nem csak valós szám lehet. Legyen $[a,b]$ kompakt intervallum, $\emptyset \ne U \subset \mathbb{R}^n$ nyílt, és $f : U\times[a,b]\to\mathbb{R}$ folytonos; ekkor minden $x \in U$-ra az $f_x(t) := f(x,t)$ függvény folytonos, tehát Riemann-integrálható, és

$$F(x) := \int_a^b f(x,t)\,\mathrm{d}t \qquad (x \in U)$$

értelmes. Erre az $F : U \to \mathbb{R}$ függvényre:

1. $F$ folytonos;
2. ha valamely $i$-re létezik és folytonos a $\partial_i f$ parciális deriváltfüggvény, akkor létezik $\partial_i F$ is, és $\partial_i F(x) = \int_a^b \partial_i f(x,t)\,\mathrm{d}t$;
3. ha $f \in C^1$, akkor $F \in C^1$.

A bizonyítás ugyanaz a séma, mint az egyparaméteres esetben: a $G_r := \{y \in U : \|x-y\| \le r\}$ zárt gömb és $[a,b]$ szorzata [[concepts/analiii/kompakt-halmazok|kompakt]], ott $f$ egyenletesen folytonos, és a becslés koordinátánként megy. A 2. pont az integráljel alatti deriválás többváltozós alakja: a paraméter szerinti deriválás **koordinátánként** cserélhető fel az integrálással.

## Kapocs

- [[concepts/analiii/parameteres-integral-integralhatosaga]] — az integrálási sorrend felcserélhetősége ugyanezen feltételek mellett.
- [[concepts/analiii/parameteres-integral-differencialasa]] — az integráljel alatti deriválás, a fejezet fő eszköze.
- [[concepts/analiii/gamma-fuggveny]] — a legfontosabb konkrét paraméteres improprius integrál.
- [[concepts/analii/improprius-integral]] — az improprius integrál egyváltozós fogalma; itt ugyanez, de paramétersereggel, és a konvergencia egyenletességét a domináns függvény biztosítja.
- [[concepts/analiii/folytonosan-differencialhato-fuggveny]] — a vektorparaméteres változat 3. pontjában szereplő $C^1$ osztály.
- [[concepts/analii/egyenletes-folytonossag]] — a bizonyítás kulcslépése a kompakt téglalapon vett egyenletes folytonosság.
