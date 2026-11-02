---
tags: [concept]
sources: [11.gepi_tanulas.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-12
---

# Információnyereség (információs előny)

Egy attribútum szerinti felbontás információs előnye a szülőcsúcs mintáinak entrópiája mínusz a gyerekcsúcsok entrópiáinak súlyozott összege; döntési fa építésekor a legnagyobb nyereségű attribútumot választjuk.

## Tartalom

### Entrópia

A $P$-beli minták információtartalma (entrópiája):
$$E(P) = E(p_1, \dots, p_n) = -\sum_{i=1}^{n} p_i \log_2 p_i$$
ahol $P$-ben $n$-féle eltérő értékű minta van, gyakoriságaik aránya $p_1 : \dots : p_n$, $\sum p_i = 1$.

Kétféle (pozitív/negatív) kimenet esetén: $E(P) = -p^+ \log_2 p^+ - p^- \log_2 p^-$, $p^+ + p^- = 1$.

- 2 pozitív, 3 negatív: $E(2/5, 3/5) = 0{,}97$.
- 0 pozitív, 3 negatív: $E(0/3, 3/3) = 0$ (egységes minta-halmaz).

### Információs előny

Ha a $P$ mintákkal rendelkező csúcsot az $a \in A$ attribútummal bontjuk, a gyerekek $P_{a=v} = \{p \in P \mid p.a = v\}$, $v \in Ertek(a)$:

$$C(P, a) = E(P) - \sum_{v \in Ertek(a)} \frac{|P_{a=v}|}{|P|}\, E(P_{a=v})$$

### Számolt példa (étterem, tele ág)

A „tele" ág mintái $\{2,4,5,9,10,12\}$: $E(2/6, 4/6) = 0{,}92$. A *Más* szerint $\{9\}$ ($E = 0$) és $\{2,4,5,10,12\}$ ($E(2/5,3/5) = 0{,}97$):

$$C = 0{,}92 - \left(\tfrac16 \cdot 0 + \tfrac56 \cdot 0{,}97\right) = 0{,}92 - 0{,}81 = 0{,}11.$$

Az összes attribútum gyerekentrópia-összege (a $0{,}92$-ből levonandó):

| Attribútum | Súlyozott entrópia |
|---|---|
| Más | 0,81 |
| Bár | 0,92 |
| P/Sz | 0,81 |
| Éhes | 0,67 |
| Ár | 0,67 |
| Eső | 0,81 |
| Fogl | 0,67 |
| Fajt | 0,67 |
| Idő | 0,67 |

Minél kisebb a súlyozott entrópia, annál nagyobb a nyereség; a *Bár* nem nyer semmit ($0{,}92 - 0{,}92 = 0$). Több attribútum holtversenyben 0,67 értékű (nyereség $0{,}25$) a diák szerint.

## Kapocs

- [[concepts/mesint/dontesi-fa-epitese]] — ahol az attribútum-választást használjuk
- [[concepts/mesint/dontesi-fa-tanulo-algoritmus]] — az algoritmus, amely ezt hívja
- [[concepts/dimatii/entropia]] — az entrópia általános definíciója és tulajdonságai
- [[concepts/bigdata/dontesi-fa]] — az információnyereség a big data-s anyagban
