---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf, 03_ea_An3_2022_tavasz.pdf, gyakorlat.pdf, RopzhKerdesek.pdf, ElozetesKerdesekMegajanlottVizsgajegyhez1.pdf]
derivation: source
kind: definition
element: water
updated: 2026-10-21
---

# Kompakt halmazok

A kompaktság a nyílt fedésekkel megfogalmazott „végességi" tulajdonság: minden nyílt fedésből kiválasztható véges fedés. Tetszőleges metrikus térben ebből következik a korlátosság és a zártság; $\mathbb{R}^p$-ben a megfordítás is igaz.

## Tartalom

### Definíció

Legyen $(M,d)$ metrikus tér. A $K \subset M$ halmaz **kompakt**, ha minden nyílt fedéséből kiválasztható véges fedés: ha $G_i$ ($i \in I$) nyílt halmazok tetszőlegesen nagy számosságú rendszere, amelyre $K \subset \bigcup_{i \in I} G_i$, akkor van olyan véges $V \subset I$, hogy $K \subset \bigcup_{i \in V} G_i$.

### Minden kompakt halmaz korlátos és zárt

**Állítás.** Ha $K$ kompakt, akkor korlátos és zárt.

*Bizonyítás.*

*Korlátosság.* Legyen $a \in M$ tetszőleges. A $\bigcup_{r>0} B(a,r) = M$ fedi $K$-t; a kompaktság miatt véges sok gömb, tehát ezek közül a legnagyobb egyedül is lefedi $K$-t.

*Zártság.* Elég belátni, hogy minden $c \in M \setminus K$ külső pontja $K$-nak. A $G_r = M \setminus \overline{B}(c,r)$ halmazok nyíltak, uniójuk $M \setminus \{c\}$, tehát fedik $K$-t. Véges sok közül a legbővebb egyedül is fedi: van olyan $r$, hogy $K \subset G_r$. De akkor $K$ diszjunkt $B(c,r)$-től, tehát $c \in \operatorname{ext} K$. $\blacksquare$

A megfordítás általános metrikus térben nem igaz; $\mathbb{R}^p$-ben viszont igen, ez a [[concepts/analiii/heine-borel-tetel]].

**Ellenpélda végtelen dimenzióban.** Legyen $\ell_\infty := \{x = (x_k) : \mathbb{N} \to \mathbb{R} \mid \sup_k |x_k| < \infty\}$ a korlátos valós sorozatok tere, a szokásos $(+,\cdot)$ műveletekkel ellátott lineáris tér, a $\|x\|_\infty := \sup_k |x_k|$ normával. A

$$A := \{(x_k) \in \ell_\infty \mid x_k \in \{0,1\}\ (k \in \mathbb{N})\} \subset \ell_\infty$$

halmaz korlátos és zárt, de **nem kompakt**: bármely két különböző eleme $1$ távolságra van egymástól, ezért egyetlen $A$-beli sorozatnak sincs Cauchy- (tehát konvergens) részsorozata. Ez mutatja, hogy a „kompakt $\Leftrightarrow$ korlátos és zárt" ekvivalencia $\mathbb{R}^p$ véges dimenziójának lényegi következménye.

### Kompakt és zárt halmaz távolsága

**Definíció.** Ha $A, B \subset \mathbb{R}^p$ nemüres halmazok, akkor a **távolságuk**

$$\operatorname{dist}(A,B) = \inf\{|a-b| : a \in A,\ b \in B\}.$$

**Tétel.** Legyen $K \subset \mathbb{R}^p$ kompakt és $Z \subset \mathbb{R}^p$ zárt, egyik sem üres.

(a) Léteznek olyan $a \in K$, $b \in Z$ pontok, amelyekre $|a-b| = \operatorname{dist}(K,Z)$ — az infimum tehát felvétetik.
(b) Ha $K$ és $Z$ diszjunkt, akkor $\operatorname{dist}(K,Z) > 0$.

*Bizonyítás.* Az infimumhoz sorozattal tartunk: vannak $x_n \in K$, $y_n \in Z$ pontok, hogy $|x_n - y_n| \to \operatorname{dist}(K,Z)$. Bolzano–Weierstrass szerint van olyan $(n_i)$ indexsorozat, amelyre $x_{n_i}$ konvergens; legyen $a = \lim x_{n_i} \in K$ ($K$ zárt). Az $(y_{n_i})$ sorozat korlátos, mert

$$|y_{n_i}| \leq |y_{n_i} - x_{n_i}| + |x_{n_i} - a| + |a|,$$

és a jobb oldal mindhárom tagja konvergens, tehát korlátos. Ismét Bolzano–Weierstrass szerint van olyan $(m_i)$ részsorozata $(n_i)$-nek, amelyre $y_{m_i}$ konvergens; legyen $b = \lim y_{m_i} \in Z$ ($Z$ zárt). Ekkor

$$\operatorname{dist}(K,Z) = \lim |x_n - y_n| = \lim |x_{m_i} - y_{m_i}| = |a-b|.$$

A (b) rész ebből következik: ha $K \cap Z = \emptyset$, akkor $a \neq b$, tehát $|a-b| > 0$. $\blacksquare$

### Feladatok

*Forrás: gyakorlat.pdf „Metrikus terek" 16–17, 20.*

- **Kompakt halmaz zárt részhalmaza kompakt.** $B\subset A$ zárt, $A$ kompakt: $B$-beli sorozatnak $A$-ban van konvergens részsorozata, a limesz $B$-ben van, mert $B$ zárt.
- **Metszet és unió.** $A_\gamma$ ($\gamma\in\Gamma\neq\emptyset$) kompakt ⇒ $\bigcap A_\gamma$ kompakt: zárt (a kompakt halmaz zárt) részhalmaza egy kompaktnak. Véges $\Gamma$ esetén $\bigcup A_\gamma$ kompakt: egy sorozatnak végtelen sok tagja esik valamelyik $A_\gamma$-ba, és abban van konvergens részsorozat.
- **$P_n$ kompakt $C[0,1]$-ben.** A legfeljebb $n$-edfokú, legfeljebb $1$ abszolút értékű együtthatójú polinomok halmaza a $[-1,1]^{n+1}$ kompakt kocka folytonos (sőt Lipschitz: $\|\sum(a_i-b_i)x^i\|_\infty\le(n+1)\max|a_i-b_i|$) képe, tehát kompakt.
- **Nem teljes tér ⇒ van korlátos, zárt, nem kompakt halmaz:** [[concepts/analiii/cauchy-sorozat-es-teljes-ter]] Feladatok.

## Kapocs

- [[concepts/analiii/kompaktsag-ekvivalens-jellemzesei]] — a fedéses, a sorozatos és a torlódási pontos definíció ekvivalenciája
- [[concepts/analiii/heine-borel-tetel]] — $\mathbb{R}^p$-ben a kompaktság ekvivalens a korlátos és zárt tulajdonsággal
- [[concepts/analiii/cantor-metszettetel]] — a bizonyításokban használt Bolzano–Weierstrass-tétel
- [[concepts/analiii/nyilt-es-zart-halmazok]] — a fedéseket alkotó nyílt halmazok
- [[concepts/analiii/halmaz-pontjai-metrikus-terben]] — a külső pont fogalma a zártság bizonyításában
- [[concepts/analiii/weierstrass-tetel-kompakt-halmazon]] — kompakt halmaz folytonos képe kompakt
- [[concepts/analiii/egyenletes-folytonossag-metrikus-terben]] — a Heine-tétel: kompakt tartományon a folytonosság egyenletes
- [[concepts/analiii/vizsgakerdesek-es-bizonyitando-tetelek]] — a témához tartozó megajánlott vizsgajegy- és röpdolgozat-kérdések.
