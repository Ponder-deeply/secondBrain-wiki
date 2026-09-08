---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 3.1.5. Tétel"]
derivation: source
updated: 2026-09-07
---

# A differenciálhatóság elégséges feltétele

A parciális deriválhatóságból önmagában nem következik a differenciálhatóság; ha viszont egy változó kivételével az összes parciális deriváltfüggvény létezik egy környezetben és **folytonos** a pontban, akkor a függvény ott már differenciálható.

## Tartalom

### A tétel

**3.1.5. Tétel.** Legyen $1 \le n \in \mathbb{N}$, $h \in \mathbb{R}^n \to \mathbb{R}$ és $a \in \operatorname{int} D_h$. Tegyük fel, hogy valamely $i \in \{1, \dots, n\}$ indexre:

- alkalmas $r > 0$ mellett $K_r(a) \subset D_h$, és minden $x \in K_r(a)$ helyen léteznek a $\partial_j h(x)$ ($j \ne i$) parciális deriváltak;
- mindegyik $\partial_j h$ ($j \ne i$) parciális deriváltfüggvény **folytonos** az $a$-ban;
- létezik a $\partial_i h(a)$ parciális derivált.

Ekkor $h \in D\{a\}$.

A feltétel aszimmetriája lényeges: **egyetlen** kitüntetett változó szerint elég a puszta pontbeli parciális deriválhatóság, a többinél kell a környezetbeli létezés és a pontbeli folytonosság.

### A bizonyítás gondolatmenete

Feltehető $n \ge 2$ és $i = 1$; $\mathbb{R}^n$-ben a $\|\cdot\|_\infty$ normát használjuk. A trükk: a $h(a+x) - h(a)$ megváltozást olyan különbségek **teleszkópikus összegére** bontjuk, amelyekben egyszerre csak **egy** koordináta változik. Az $n = 2$ esetben az $A := (a_1,a_2)$, $B := (a_1+x_1, a_2+x_2)$, $C := (a_1+x_1, a_2)$ pontokkal

$$h(B) - h(A) = \bigl(h(C) - h(A)\bigr) + \bigl(h(B) - h(C)\bigr),$$

ahol az első tagban csak az első, a másodikban csak a második koordináta változik.

Az **első** tagot a feltételezett $\partial_1 h(a)$ parciális derivált létezésével kezeljük: alkalmas $\omega(t) \to 0$ függvénnyel

$$h(a_1+x_1, a_2, \dots, a_n) - h(a) = \partial_1 h(a)\cdot x_1 + \omega(x_1)\cdot x_1 .$$

A **többi** tagra a $K_r(a)$-beli parciális deriválhatóság miatt alkalmazható az egyváltozós **Lagrange-középértéktétel**: alkalmas $\xi_i$ közbülső helyekkel

$$h(a+x) - h(a) = \partial_1 h(a) x_1 + \omega(x_1)x_1 + \sum_{i=2}^n \partial_i h(a_{x,i})\cdot x_i,$$

ahol $a_{x,i} := (a_1+x_1, \dots, a_{i-1}+x_{i-1}, \xi_i, a_{i+1}, \dots, a_n)$. Ez az a pont, ahol a Lagrange-tétel megkívánja, hogy a parciális derivált ne csak $a$-ban, hanem egy egész környezetben létezzen.

Ezt átrendezve

$$h(a+x) - h(a) = \sum_{i=1}^n \partial_i h(a)\,x_i + \omega(x_1)x_1 + \sum_{i=2}^n \bigl(\partial_i h(a_{x,i}) - \partial_i h(a)\bigr) x_i = \langle A, x\rangle + \langle \varphi(x), x\rangle,$$

ahol $A := \bigl(\partial_1 h(a), \dots, \partial_n h(a)\bigr)$ és $\varphi(x) := \bigl(\omega(x_1),\ \partial_2 h(a_{x,2}) - \partial_2 h(a),\ \dots\bigr)$.

Itt lép be a **folytonosság**: mivel $\partial_i h \in C\{a\}$ ($i \ge 2$), tetszőleges $\varepsilon > 0$-hoz van olyan $0 < \delta < r$, hogy $|\partial_i h(z) - \partial_i h(a)| < \varepsilon$ minden $z \in K_\delta(a)$ esetén. A közbülső pontokra $\|a_{x,i} - a\|_\infty \le \|x\|_\infty$, tehát $\|x\|_\infty < \delta$ már elég, és így $\|\varphi(x)\|_\infty < \varepsilon$, vagyis $\varphi(x) \to 0$.

Végül az $\eta(x) := \langle \varphi(x),\, x/\|x\|_\infty\rangle$ ($x \ne 0$), $\eta(0) := 0$ választással

$$h(a+x) - h(a) = \langle A, x\rangle + \eta(x)\cdot\|x\|_\infty,$$

és a Cauchy–Bunyakovszkij-egyenlőtlenséggel $|\eta(x)| \le \|\varphi(x)\|_2 \cdot \|x/\|x\|_\infty\|_2 \le n\,\|\varphi(x)\|_\infty \to 0$. Tehát $h \in D\{a\}$, és $h'(a) = \operatorname{grad} h(a) = A$. $\square$

### Mire használjuk

A gyakorlatban ez az egyetlen kézzelfogható eszköz a differenciálhatóság igazolására: a parciális deriváltak kiszámíthatók, és általában láthatóan folytonosak (elemi függvények kompozíciói). A definíció szerinti közvetlen ellenőrzés csak a patologikus eseteknél kerülhetetlen.

## Kapocs

- [[concepts/analiii/parcialis-derivalt]] — a feltételekben szereplő objektumok.
- [[concepts/analiii/gradiens-parcialis-derivaltakbol]] — a fordított irányú, feltétel nélküli implikáció.
- [[concepts/analiii/folytonosan-differencialhato-fuggveny]] — a $C^1$ osztály, amelyet ez a tétel jellemez.
- [[concepts/analiii/differencialhatosagi-fogalmak-hierarchiaja]] — miért kell a folytonossági feltétel: ellenpéldák nélküle.
- [[concepts/analii/kozeptertekek]] — a bizonyítás motorja, a Lagrange-középértéktétel.
