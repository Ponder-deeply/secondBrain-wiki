---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# A Jordan-mérték kockázásos definíciója

A teret $1/n$ élű rácskockákra bontva a fedő, illetve belső kockák összterülete a külső, illetve belső Jordan-mértékhez tart; ebből adódik a $b(H) \le k(H)$ egyenlőtlenség és a téglák mérhetősége.

## Tartalom

### Kockatípusok

Legyen $H \subset \mathbb{R}^p$ korlátos, $n \in \mathbb{N}$, $a_1,\dots,a_p \in \mathbb{Z}$, és

$$K = \left[\tfrac{a_1}{n}, \tfrac{a_1+1}{n}\right] \times \dots \times \left[\tfrac{a_p}{n}, \tfrac{a_p+1}{n}\right]$$

egy $1/n$ élű rácskocka. Ekkor $K$

- **belső kockája** $H$-nak, ha $K \subset \operatorname{int} H$;
- **külső kockája** $H$-nak, ha $K \subset \operatorname{ext} H$;
- **határkockája** $H$-nak, ha $K \cap \partial H \neq \emptyset$;
- **fedő kockája** $H$-nak, ha $K \cap \operatorname{cl} H \neq \emptyset$.

A fedő kockák pontosan a belső és a határkockák együtt.

### Az $n$-edik közelítések

$$k_n(H) = (\text{a fedő kockák száma}) \cdot \frac{1}{n^p}, \qquad b_n(H) = (\text{a belső kockák száma}) \cdot \frac{1}{n^p}.$$

Triviálisan

$$b_n(H) \leq k_n(H), \qquad b_n(H) \leq b(H), \qquad k(H) \leq k_n(H).$$

### Lemma: téglára a közelítések a térfogathoz tartanak

Bármely $R$ tengelypárhuzamos téglára $k_n(R) \to \tau(R)$ és $b_n(R) \to \tau(R)$.

**Bizonyítás.** Legyen $R$ éleinek végpontjai $a_i < b_i$. Minden $i$-re az $[a_i,b_i]$ intervallumban legalább $(b_i - a_i)n - 2$ darab $1/n$ hosszú kis intervallum fér el, és legfeljebb $(b_i-a_i)n + 2$ darab fedi le. Így

$$\prod_{i=1}^{p}\left(b_i - a_i - \tfrac{2}{n}\right) \leq b_n(R) \leq k_n(R) \leq \prod_{i=1}^{p}\left(b_i - a_i + \tfrac{2}{n}\right),$$

és a két szélső becslés is $\prod (b_i - a_i) = \tau(R)$-hez tart. $\square$

### A fő tétel

Minden korlátos $H \subset \mathbb{R}^p$ halmazra

$$b_n(H) \to b(H), \qquad k_n(H) \to k(H), \qquad b(H) \leq k(H).$$

**Bizonyítás vázlata.** Adott $\varepsilon > 0$-hoz vannak egymásba nem nyúló $R_1,\dots,R_m \subset H$ téglák, melyekre $\sum \tau(R_i) > b(H) - \varepsilon/2$. A lemma miatt elég nagy $n$-re $b_n(R_i) > \tau(R_i) - \varepsilon/(2m)$. Mivel a téglák egymásba nem nyúlók, belső kockáik különbözők, ezért

$$b(H) \geq b_n(H) \geq \sum_{i=1}^{m} b_n(R_i) > b(H) - \varepsilon,$$

amiből $b_n(H) \to b(H)$. A külső mértéknél ugyanez a gondolat: fedő téglákat választva $\sum \tau(F_i) < k(H) + \varepsilon/2$, és mivel $H$ minden fedő kockája legalább egy $F_i$-nek is fedő kockája,

$$k(H) \leq k_n(H) \leq \sum_{i=1}^{m} k_n(F_i) < k(H) + \varepsilon.$$

Végül minden $n$-re $b_n(H) \leq k_n(H)$, és az $n \to \infty$ határátmenetből $b(H) \leq k(H)$. $\square$

### Következmény: a téglák mérhetők

Mivel $k_n(R) \to \tau(R)$ és $k_n(R) \to k(R)$, illetve $b_n(R) \to \tau(R)$ és $b_n(R) \to b(R)$, ezért

$$k(R) = b(R) = \tau(R),$$

vagyis minden tengelypárhuzamos tégla Jordan-mérhető, és mértéke a térfogata. Ettől kezdve $\tau$ helyett mindenütt $t$ írható.

## Kapocs

- [[concepts/analiii/jordan-kulso-belso-mertek]] — a fedéssel/kitöltéssel adott eredeti definíció, amellyel ez ekvivalens
- [[concepts/analiii/kulso-belso-mertek-tulajdonsagai]] — a $k_n$, $b_n$ közelítésekre vonatkozó triviális egyenlőtlenségekből határátmenettel adódó tulajdonságok
- [[concepts/analiii/also-felso-osszegek-kockazassal]] — ugyanez a kockázásos technika, de függvények integrálközelítő összegeire alkalmazva
