---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 2.2. Tétel és 2.1. xiv) megjegyzés"]
derivation: source
updated: 2026-09-07
---

# Átviteli elv metrikus terekben

Az átviteli elv a folytonosságot és a határértéket sorozatok konvergenciájára fordítja le: $f$ akkor és csak akkor folytonos $a$-ban, ha minden $a$-hoz tartó sorozat képe $f(a)$-hoz tart. Ez teszi átemelhetővé a sorozatokra vonatkozó műveleti szabályokat a függvényekre.

## Tartalom

### 2.2. Tétel — a folytonosság átviteli elve

**Tétel.** Legyenek $(X,\rho)$, $(Y,\sigma)$ metrikus terek, $f \in X \to Y$, $a \in D_f$. Ekkor $f \in C\{a\}$ azzal ekvivalens, hogy minden

$$(x_n) : \mathbb{N} \to D_f, \qquad \lim(x_n) = a$$

sorozatra az $\bigl(f(x_n)\bigr)$ sorozat konvergens, és $\lim\bigl(f(x_n)\bigr) = f(a)$.

*Bizonyítás.* ($\Rightarrow$) Legyen $A := f(a)$ és $K(A)$ tetszőleges környezet. A folytonosság miatt van olyan $k(a)$, hogy $f(x) \in K(A)$ minden $x \in k(a)\cap D_f$ esetén. Mivel $x_n \to a$, alkalmas $N$ küszöbtől $x_n \in k(a)$, tehát $f(x_n) \in K(A)$.

($\Leftarrow$) Indirekt: ha $f \notin C\{a\}$, akkor alkalmas $K(A)$ környezethez minden $k(a)$-ban van olyan $x \in k(a)\cap D_f$, amelyre $f(x) \notin K(A)$. A $k(a) := k_{1/n}(a)$ választással kapott $x_n$ pontokra $\rho(x_n,a) < 1/n$, tehát $x_n \to a$, viszont $f(x_n) \notin K(A)$ minden $n$-re — ez ellentmond annak, hogy $f(x_n) \to f(a)$. $\blacksquare$

### A határérték átviteli elve

**Tétel.** Legyen $a \in D_f'$. Az $f$-nek az $a$ helyen akkor és csak akkor létezik határértéke, ha minden

$$(x_n) : \mathbb{N} \to D_f \setminus \{a\}, \qquad \lim(x_n) = a$$

sorozatra az $\bigl(f(x_n)\bigr)$ sorozatnak van határértéke. Ekkor minden ilyen sorozatra $\lim\bigl(f(x_n)\bigr) = A := \lim_a f$.

*Bizonyítás (a nemtriviális irány).* Először azt kell látni, hogy a határérték nem függ a sorozat választásától. Ha $(x_n)$ és $(\tilde x_n)$ két ilyen sorozat, akkor az összefésült

$$x_n^* := \begin{cases} x_{n/2} & (n = 2k) \\ \tilde x_{(n-1)/2} & (n = 2k+1)\end{cases}$$

sorozat is ilyen, tehát $\bigl(f(x_n^*)\bigr)$-nak van határértéke; ennek két részsorozata $\bigl(f(x_n)\bigr)$ és $\bigl(f(\tilde x_n)\bigr)$, így a két határérték megegyezik. Legyen $A$ ez a közös érték. Ha $\lim_a f = A$ nem teljesülne, akkor alkalmas $K(A)$-hoz minden $k_{1/n}(a)$-ban lenne olyan $a \ne x_n \in D_f$, hogy $f(x_n) \notin K(A)$; erre $x_n \to a$, de $f(x_n) \not\to A$ — ellentmondás. $\blacksquare$

### Mire jó

Az átviteli elv a fejezet szinte minden állításának bizonyítási eszköze:

- a kompozíció folytonossága (2.3. Tétel);
- a [[concepts/analiii/weierstrass-tetel-kompakt-halmazon|Weierstrass-tétel]] és a [[concepts/analiii/folytonos-inverz-kompakt-halmazon|folytonos inverz tétele]] — ott a kompaktságból nyert konvergens részsorozatot kell átvinni;
- a [[concepts/analiii/koordinatafuggvenyek-folytonossaga|koordinátafüggvények]] tétele — a sorozatok koordinátánkénti konvergenciájára visszavezetve;
- a műveleti szabályok (összeg, szorzat, hányados) folytonosságra és határértékre.

**Kontrakció fixpontja.** A Banach-fixponttételben az $f(\alpha) = \alpha$ egyenlőség is az átviteli elvvel adódik:
$$\alpha = \lim(x_n) = \lim(x_{n+1}) = \lim\bigl(f(x_n)\bigr) = f\bigl(\lim(x_n)\bigr) = f(\alpha).$$

### A tagadás használható alakja

Ha $f$-nek az $a \in D_f'$ helyen **nincs** határértéke, az azt jelenti: minden $A \in Y$-hoz van olyan $\varepsilon > 0$, hogy minden $\delta > 0$ mellett alkalmas $x \in D_f$, $0 < \rho(x,a) < \delta$ helyen $\sigma(f(x),A) \ge \varepsilon$. Ezt rendszerint $\delta := 1/n$ választással sorozattá alakítjuk: van olyan $x_n \to a$, $x_n \ne a$, hogy $\sigma(f(x_n),A) \ge \varepsilon$. Ez a nemlétezés bizonyításának standard receptje.

## Kapocs

- [[concepts/analiii/folytonossag-metrikus-terben]] — a folytonosság $\varepsilon$–$\delta$ és környezetes definíciója
- [[concepts/analiii/fuggvenyhatarertek-metrikus-terben]] — a határérték fogalma, amire a második változat vonatkozik
- [[concepts/analiii/konvergencia-metrikus-terben]] — a sorozatkonvergencia, amire az elv fordít
- [[concepts/analiii/banach-fixponttetel-metrikus-terben]] — a fixpontegyenlőség átviteli elvvel
