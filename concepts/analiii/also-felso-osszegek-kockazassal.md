---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf, 09_ea_An3_2022_tavasz.pdf]
derivation: source
updated: 2026-09-14
---

# Alsó és felső összegek kockázással

Az integrálási tartományt $1/n$ élű rácskockákkal metszve kapott alsó és felső összegek az alsó, illetve a felső integrálhoz tartanak; általánosabban minden végtelenül finomodó felosztássorozat ugyanezt teszi.

## Tartalom

### Definíció

Legyen $A \in \mathcal{J}_p$, $f : A \to \mathbb{R}$ korlátos, $n$ pozitív egész, és

$$\mathcal{K} = \left\{ K = \left[\tfrac{k_1}{n},\tfrac{k_1+1}{n}\right]\times\dots\times\left[\tfrac{k_p}{n},\tfrac{k_p+1}{n}\right] \;:\; K \cap A \neq \emptyset \right\}$$

az $A$-t metsző rácskockák rendszere. Az $n$-edik alsó és felső összeg

$$s_n(f,A) = \sum_{K \in \mathcal{K}} t(K \cap A)\cdot \inf_{K\cap A} f, \qquad S_n(f,A) = \sum_{K \in \mathcal{K}} t(K\cap A)\cdot \sup_{K\cap A} f.$$

### Konvergencia

**Állítás.** $s_n(f,A) \to \underline{\int}_A f$ és $S_n(f,A) \to \overline{\int}_A f$.

**Bizonyítás (felső összegre).** Legyen $M$ felső korlátja $|f|$-nek, és $g = f + M$, tehát $0 \leq g \leq 2M$. Adott $\varepsilon > 0$-hoz van olyan $\mathcal{F} = \{B_1,\dots,B_m\}$ felosztás, hogy $S(f,\mathcal{F}) < \overline{\int}_A f + \varepsilon/2$. Legyen $H = \bigcup_i \partial B_i$; ez nullmértékű, ezért $k_n(H) \to 0$, és van olyan $n_0$, hogy $n > n_0$ esetén $k_n(H)\cdot 4M < \varepsilon$. Ekkor a kockákat aszerint bontva, hogy valamelyik $\operatorname{int} B_i$-be esnek-e:

$$\sum_{K\in\mathcal{K}} t(K\cap A)\sup_{K\cap A} g \leq \sum_{i=1}^m t(B_i)\sup_{B_i} g + k_n(H)\cdot 2M,$$

amiből $S_n(f,A) \leq S(f,\mathcal{F}) + \varepsilon/2 \leq \overline{\int}_A f + \varepsilon$. Mivel $\overline{\int}_A f \leq S_n(f,A)$ mindig fennáll, ez éppen a konvergencia. Az alsó összegre ugyanez megy. $\square$

A bizonyítás lelke az, hogy a felosztás darabjainak **határa nullmértékű**, így a „rossz", több darabot is metsző kockák össztérfogata elhanyagolható.

### Az általános, finomsággal megfogalmazott állítás

**Állítás.** Legyen $A \in \mathcal{J}_p$, $f : A \to \mathbb{R}$ korlátos. Minden $\varepsilon > 0$-hoz van olyan $\delta_0 > 0$, hogy az $A$ bármely, $\delta_0$-nál finomabb $\mathcal{F}$ felosztására

$$\underline{\int}_A f - \varepsilon < s(f,\mathcal{F}) \leq \underline{\int}_A f \quad \text{és} \quad \overline{\int}_A f \leq S(f,\mathcal{F}) < \overline{\int}_A f + \varepsilon.$$

A kockázásos állítás ennek speciális esete; a tételek bizonyításához rendszerint elég a speciális eset. (Bizonyítás: LTS2, Csenge.)

### Következmény: végtelenül finomodó felosztássorozatok

Ha $\mathcal{F}_1, \mathcal{F}_2, \dots$ az $A$ felosztásainak **végtelenül finomodó** sorozata, azaz $\delta(\mathcal{F}_n) \to 0$, akkor

- $s(f,\mathcal{F}_n) \to \underline{\int}_A f$;
- $S(f,\mathcal{F}_n) \to \overline{\int}_A f$;
- ha $f$ integrálható $A$-n, akkor $s(f,\mathcal{F}_n) \to \int_A f$ és $S(f,\mathcal{F}_n) \to \int_A f$.

Ez teszi lehetővé, hogy az integrált egyetlen alkalmasan választott felosztássorozattal számoljuk ki, szuprémum- és infimumkeresés nélkül.

## Kapocs

- [[concepts/analiii/jordan-mertek-szerinti-integral]] — az alsó és felső integrál definíciója, amelyhez ezek az összegek tartanak
- [[concepts/analiii/jordan-mertek-kockazassal]] — ugyanez a rácskockás technika halmazok mértékére
- [[concepts/analiii/jordan-nullmerteku-halmazok]] — a bizonyításban a felosztás darabjainak határa nullmértékű, ezért hagyható el
- [[concepts/analiii/tobbvaltozos-integralhatosag]] — a végtelenül finomodó sorozatok az oszcillációs kritérium megfogalmazásában is szerepelnek
