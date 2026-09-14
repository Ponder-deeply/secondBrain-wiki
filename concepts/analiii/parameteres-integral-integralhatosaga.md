---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf, 08_ea_An3_2022_tavasz.pdf]
derivation: source
updated: 2026-09-14
---

# Paraméteres integrál integrálhatósága

Elégséges feltétel arra, hogy a paraméter szerinti és az integrálási változó szerinti integrálás sorrendje felcserélhető legyen.

## Tartalom

### A tétel

- **(a)** Legyen $f : [c,d] \times [a,b] \to \mathbb{R}$ folytonos és $F(t) = \int_{x=a}^{b} f(t,x)\,\mathrm{d}x$. Ekkor

$$\int_{t=c}^{d} F(t)\,\mathrm{d}t = \int_{x=a}^{b}\left(\int_{t=c}^{d} f(t,x)\,\mathrm{d}t\right)\mathrm{d}x.$$

- **(b)** Tegyük fel, hogy $[c,d] \subset \mathbb{R}$ és $(\alpha,\beta) \subset \mathbb{R}$ intervallumok, $f : [c,d]\times(\alpha,\beta) \to \mathbb{R}$ folytonos, az $F(t) = \int_{x=\alpha}^{\beta} f(t,x)\,\mathrm{d}x$ improprius integrál minden $t$-re konvergens, és van olyan $g : (\alpha,\beta) \to [0,\infty)$ domináns függvénye $f$-nek, amelyre $\int_\alpha^\beta g$ létezik és véges. Ekkor

$$\int_{t=c}^{d} F(t)\,\mathrm{d}t = \int_{x=\alpha}^{\beta}\left(\int_{t=c}^{d} f(t,x)\,\mathrm{d}t\right)\mathrm{d}x.$$

### Bizonyítás

Azt már tudjuk, hogy $F(t)$ folytonos, tehát integrálható $[c,d]$-n; a bal oldal létezik.

Legyen $\varepsilon > 0$ tetszőleges. A dominancia miatt van olyan $\alpha < a_0 < b_0 < \beta$, hogy

$$\int_\alpha^{a_0} g < \frac{\varepsilon}{2(d-c)} \qquad \text{és} \qquad \int_{b_0}^\beta g < \frac{\varepsilon}{2(d-c)}.$$

Bármely $a \in (\alpha,a_0)$ és $b \in (b_0,\beta)$ esetén, **minden** $t$-re egyszerre,

$$\left|F(t) - \int_{x=a}^{b} f(t,x)\,\mathrm{d}x\right| \leqslant \int_\alpha^a \bigl|f(t,x)\bigr|\,\mathrm{d}x + \int_b^\beta \bigl|f(t,x)\bigr|\,\mathrm{d}x \leqslant \int_\alpha^a g + \int_b^\beta g < \frac{\varepsilon}{d-c}.$$

Ezt $t$ szerint $c$-től $d$-ig integrálva, és a **kompakt** téglalapon már érvényes (a) állítást használva a sorrendcserére:

$$\int_c^d F - \varepsilon < \int_{t=c}^{d}\left(\int_{x=a}^{b} f(t,x)\,\mathrm{d}x\right)\mathrm{d}t = \int_{x=a}^{b}\left(\int_{t=c}^{d} f(t,x)\,\mathrm{d}t\right)\mathrm{d}x < \int_c^d F + \varepsilon.$$

Mivel ez minden $\varepsilon > 0$-ra és minden elég bő $[a,b]$-re teljesül,

$$\int_{x=\alpha}^{\beta}\left(\int_{t=c}^{d} f(t,x)\,\mathrm{d}t\right)\mathrm{d}x = \lim_{a\searrow\alpha,\; b\nearrow\beta}\int_{x=a}^{b}\left(\int_{t=c}^{d} f(t,x)\,\mathrm{d}t\right)\mathrm{d}x = \int_{t=c}^{d} F(t)\,\mathrm{d}t.$$

### Másik bizonyítás az (a) esetre — segédfüggvényekkel

A kompakt téglalapon vett esetre ((a), $f : [a,b]\times[c,d] \to \mathbb{R}$ folytonos) van egy második, direkt $\varepsilon$-becslés nélküli bizonyítás is, amely a [[concepts/analiii/parameteres-integral-differencialasa|paraméteres integrál deriválhatóságára]] vonatkozó tételre vezeti vissza az állítást.

Legyen $I := [a,b]\times[c,d]$, és vezessük be a
$$h(u,v) := \int_c^v f(u,s)\,\mathrm{d}s \qquad \bigl((u,v)\in I\bigr)$$
függvényt. Mivel $f$ folytonos és $I$ [[concepts/analiii/kompakt-halmazok|kompakt]], a [[concepts/analiii/egyenletes-folytonossag-metrikus-terben|Heine-tétel]] szerint $f$ egyenletesen folytonos, ebből következik, hogy $h \in C(I)$. A valós-valós függvények integrálfüggvényének deriválhatóságára vonatkozó tételből
$$\frac{\partial h}{\partial v}(u,v) = f(u,v) \qquad \bigl((u,v)\in I\bigr),$$
és ez a parciális deriváltfüggvény is folytonos $I$-n.

Vezessünk be még két függvényt. Rögzített $y \in [c,d]$ esetén legyen
$$F(y) := \int_a^b h(x,y)\,\mathrm{d}x = \int_a^b\left(\int_c^y f(x,v)\,\mathrm{d}v\right)\mathrm{d}x, \qquad G(y) := \int_c^y\left(\int_a^b f(x,v)\,\mathrm{d}x\right)\mathrm{d}v.$$
A paraméteres integrál deriválhatóságára vonatkozó tétel szerint
$$F'(y) = \int_a^b \frac{\partial h}{\partial y}(x,y)\,\mathrm{d}x = \int_a^b f(x,y)\,\mathrm{d}x,$$
és ismét a valós-valós integrálfüggvények deriválhatóságára vonatkozó tétel szerint
$$G'(y) = \int_a^b f(x,y)\,\mathrm{d}x.$$
Tehát $F' - G' \equiv 0$, azaz $F - G$ állandó; mivel $F(c) = G(c) = 0$, ezért $F(y) = G(y)$ minden $y \in [c,d]$-re. A $y = d$ választással éppen az (a) állítást kapjuk.

Ez a bizonyítás a fejezet másik két tételét (a folytonossági és a deriválhatósági tételt) egyszerre használja, míg a fenti közvetlen bizonyítás csak a folytonossági tételre és a Heine-tételre épít.

### Szerepe

Ez a tétel nemcsak önmagában érdekes: az integráljel alatti deriválás improprius esetének bizonyítása éppen ezen múlik, hiszen ott a $\frac{\partial}{\partial t} f$ paraméteres integráljának $t$ szerinti integrálását kell az $x$ szerintivel felcserélni.

## Kapocs

- [[concepts/analiii/parameteres-integral]] — a fogalom, a domináns függvény és a folytonossági tétel.
- [[concepts/analiii/parameteres-integral-differencialasa]] — annak bizonyítása erre a sorrendcserére épül.
- [[concepts/analiii/szorzathalmaz-merteke-es-integralja]] — a sorrendcsere másik, szorzatalakú integrandusra vonatkozó esete.
