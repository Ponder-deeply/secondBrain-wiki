---
tags: [concept]
sources: [DimatIIEa01.pdf, Lehman-Leighton-Meyer-Mathematics-for-Computer-Science.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, dimat2gyak02mo.pdf, dm2gy02_Szamelmelet.pdf, dm2gy06.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-21
---

# Euklideszi algoritmus

Maradékos osztások láncolata, amely véges sok lépésben megadja két egész legnagyobb közös osztóját — egyúttal bizonyítja, hogy az mindig létezik.

## Tartalom

**Tétel.** Bármely két egész számnak létezik legnagyobb közös osztója, és ez meghatározható az euklideszi algoritmussal.

**Bizonyítás.** Ha valamelyik szám $0$, akkor a legnagyobb közös osztó a másik szám. Tegyük fel, hogy $a, b$ nem nulla, és végezzük el a következő osztásokat:

$$
\begin{aligned}
a &= bq_1 + r_1, & 0 &< r_1 < |b|,\\
b &= r_1q_2 + r_2, & 0 &< r_2 < r_1,\\
r_1 &= r_2q_3 + r_3, & 0 &< r_3 < r_2,\\
&\;\;\vdots\\
r_{n-2} &= r_{n-1}q_n + r_n, & 0 &< r_n < r_{n-1},\\
r_{n-1} &= r_nq_{n+1}. &&
\end{aligned}
$$

*Végesség:* $|b| > r_1 > r_2 > \dots \geq 0$ szigorúan csökkenő nemnegatív egész sorozat, tehát az algoritmus véges sok lépésben véget ér.

*$r_n$ közös osztó:* $r_n \mid r_{n-1}$, ezért $r_n \mid r_{n-1}q_n + r_n = r_{n-2}$, és így visszafelé haladva $r_n \mid b$, majd $r_n \mid a$.

*$r_n$ a legnagyobb:* legyen $c \mid a$ és $c \mid b$. Ekkor $c \mid a - bq_1 = r_1$, majd $c \mid b - r_1q_2 = r_2$, és így tovább $c \mid r_{n-2} - r_{n-1}q_n = r_n$. $\square$

Az utolsó nem nulla maradék tehát a legnagyobb közös osztó: $(a,b) = r_n$.

**Példa.** $(172, 62)$:

| $i$ | $r_i$ | $q_i$ | $r_{i-2} = r_{i-1}q_i + r_i$ |
|---:|---:|---:|---|
| — | 172 | — | — |
| — | 62 | — | — |
| 1 | 48 | 2 | $172 = 62\cdot 2 + 48$ |
| 2 | 14 | 1 | $62 = 48\cdot 1 + 14$ |
| 3 | 6 | 3 | $48 = 14\cdot 3 + 6$ |
| 4 | 2 | 2 | $14 = 6\cdot 2 + 2$ |
| 5 | 0 | 3 | $6 = 2\cdot 3 + 0$ |

Tehát $(172,62) = 2$.

### Rekurzív alak

**Tétel.** Legyen $a \neq 0$. Ha $b = 0$, akkor $(a,b) = a$. Ha $b \neq 0$, akkor
$$(a,b) = \big(|b|,\; a \bmod |b|\big).$$

**Bizonyítás.** $b = 0$ esetén az állítás nyilvánvaló. Ha $b \neq 0$, osszuk el maradékosan $a$-t $|b|$-vel: $a = |b|\cdot q + (a \bmod |b|)$. Ez az euklideszi algoritmus első sora. $\square$

**Példa.** $(172,62)$ rekurzívan: $(172,62) \to (62,48) \to (48,14) \to (14,6) \to (6,2) \to (2,0)$, tehát $(172,62) = 2$.

### Az algoritmus mint invariáns, és gyorsasága (Lehman–Leighton–Meyer 9.2.1)

A lépés alapja: $b \neq 0$ esetén $(a,b) = (b, \operatorname{rem}(a,b))$. Bizonyítás: $a = qb + r$, így $a$ lineáris kombinációja $b$-nek és $r$-nek, és $r = a - qb$ lineáris kombinációja $a$-nak és $b$-nek; a két párnak tehát ugyanazok a közös osztói.

Állapotgépként: az állapot $(x,y)$, az átmenet $(x,y) \to (y, \operatorname{rem}(x,y))$ ($y > 0$), és az $(x,y) = (a,b)$ lnko-invariáns megmarad; ha $y = 0$, akkor $x = (a,b)$.

**Lépésszám.** Két lépés után az első koordináta legfeljebb a felére csökken, mert $0 < y \le x$ esetén $\operatorname{rem}(x,y) \le x/2$ (ha $y \le x/2$, akkor a maradék kisebb $y$-nál; ha $y > x/2$, akkor $\operatorname{rem}(x,y) = x - y < x/2$). Így az algoritmus legfeljebb $1 + 2\log_2 a$ lépésben leáll; a pontosabb korlát a $\log_\varphi a$, $\varphi$ az aranymetszés (a forrás szerint).

**Példa.** $(1147, 899)$: $1147 = 899 + 248$; $899 = 3\cdot 248 + 155$; $248 = 155 + 93$; $155 = 93 + 62$; $93 = 62 + 31$; $62 = 2\cdot 31$. Tehát $(1147, 899) = 31$. Ugyanígy $(26,21) = (21,5) = (5,1) = 1$.

### Végesség az előadásdiák szerint

*(Farkas Gábor előadásdiái.)* $\mathbb{Z}$-ben érvényes a maradékos osztás tétele ($a = qb + r$, $0 \leq r < |b|$), ezért az euklideszi algoritmus elvégezhető; a maradékok sorozata szigorúan monoton csökken, így véges sok lépés után véget ér.

### Feladattípusok és módszerek: táblázatos számolás

*(Gyakorlat 2. és a hozzá tartozó lnko/lkkt feladatok.)* Az algoritmust táblázatban futtatjuk: soronként $r_{i-2} = r_{i-1}q_i + r_i$, a végén az utolsó nem nulla maradék az lnko, és $[a,b] = \dfrac{ab}{(a,b)}$ ([[concepts/dimatii/legkisebb-kozos-tobbszoros]]). Ha $a < b$, az első lépés $q_1 = 0$ és megcseréli a két számot.

| $(a,b)$ | lnko | lkkt |
|---|---:|---:|
| $(13,14)$ | 1 | 182 |
| $(16,37)$ | 1 | 592 |
| $(90,111)$ | 3 | 3330 |
| $(168,219)$ | 3 | 12 264 |
| $(180,219)$ | 3 | 13 140 |
| $(756,795)$ | 3 | 200 340 |
| $(1440,1587)$ | 3 | 761 760 |
| $(3048,4611)$ | 3 | 4 684 776 |

Egy teljes futás: $(90,111)$: $111 = 90\cdot1 + 21$; $90 = 21\cdot4 + 6$; $21 = 6\cdot3 + 3$; $6 = 3\cdot2$; tehát lnko $= 3$, lkkt $= 90\cdot111/3 = 3330$.

**Tipikus hibák:** az lkkt képletben az lnko elhagyása; a számlálóban szereplő $a$-t és $b$-t elírni (a forrás megoldásában a $(180,219)$ osztója elírásból $(90,111)$, de a helyes lnko $3$, az lkkt $13\,140$); az utolsó *nulla* maradék kiolvasása az utolsó *nem nulla* helyett.

Kitevős kifejezések lnko-ja: [[concepts/dimatii/lnko-hatvanykifejezesekre]].

### Feladattípusok és módszerek (2020. 2. feladatsor)

**Lnko és lkkt számolása.** A feladatsor 16 számpárra kéri $(a,b)$-t euklideszi algoritmussal és $[a,b] = ab/(a,b)$-t. Az eredmények (a maradékos osztások láncolatával ellenőrizhetők):

| $(a,b)$ | $(a,b)$ | $[a,b]$ | $(a,b)$ | $(a,b)$ | $[a,b]$ |
|---|---:|---:|---|---:|---:|
| $86, 31$ | $1$ | $2666$ | $420, 154$ | $14$ | $4620$ |
| $139, 102$ | $1$ | $14178$ | $1080, 285$ | $15$ | $20520$ |
| $255, 111$ | $3$ | $9435$ | $2016, 880$ | $16$ | $110880$ |
| $332, 88$ | $4$ | $7304$ | $30, 22$ | $2$ | $330$ |
| $675, 471$ | $3$ | $105975$ | $430, 300$ | $10$ | $12900$ |
| $432, 300$ | $12$ | $10800$ | $2355, 450$ | $15$ | $70650$ |
| $756, 333$ | $9$ | $27972$ | $300, 132$ | $12$ | $3300$ |
| $504, 150$ | $6$ | $12600$ | $518, 154$ | $14$ | $5698$ |

Példa a lánc leírására: $86 = 2\cdot 31 + 24$, $31 = 1\cdot 24 + 7$, $24 = 3\cdot 7 + 3$, $7 = 2\cdot 3 + 1$, $3 = 3\cdot 1 + 0$, tehát $(86,31) = 1$. Több számra (2. feladatsor 9. feladata, bizonyítandó): a $d$ legnagyobb közös osztó definíciója $n$ számra ($d \mid a_i$ és minden közös osztó osztja $d$-t) mindig létezik, mert $(a_1,\dots,a_n) = ((a_1,\dots,a_{n-1}), a_n)$ ismételt alkalmazással kiszámolható. A hatványkifejezések lnko-ja ($(3^{13}-1, 3^8-1) = 3^{(13,8)}-1 = 2$ és $(3^{15}-1, 3^9-1) = 3^{(15,9)}-1 = 3^3 - 1 = 26$, 2024. 6. sorozat 4. feladata): [[concepts/dimatii/lnko-hatvanykifejezesekre]].

## Kapocs

- [[concepts/dimatii/legnagyobb-kozos-oszto]] — a kiszámított fogalom
- [[concepts/dimatii/bovitett-euklideszi-algoritmus]] — az algoritmus kiterjesztése $xa + yb = (a,b)$ előállítására
- [[concepts/dimatii/maradekos-osztas]] — az algoritmus elemi lépése
- [[concepts/dimatii/oszthatosag]] — a lineáris kombinációra vonatkozó tulajdonság, amin a helyesség múlik
- [[concepts/dimatii/polinomok-bovitett-euklideszi-algoritmusa]] — ugyanez az eljárás polinomokra, test fölött

- [[concepts/dimatii/lnko-hatvanykifejezesekre]] — az lnko-azonosságok kitevős kifejezésekre
- [[concepts/dimatii/lnko-hatvanykifejezesekre]] — a hatványkülönbségek lnko-ja az algoritmus szimbolikus lépéseivel
