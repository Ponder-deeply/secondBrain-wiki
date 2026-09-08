---
tags: [concept]
sources: [1.-bevezetés.md, szelmJegyzet.pdf]
derivation: source
updated: 2026-08-05
---

# Formális nyelvek és nyelvi műveletek

Egy $V$ ábécé feletti **nyelv** a $V^*$ egy részhalmaza; a formális nyelvelmélet ezek szerkezetét, megadhatóságát és osztályait vizsgálja.

## Tartalom

### Nyelv definíciója

- **Üres nyelv**: $\emptyset$ (egyetlen szót sem tartalmaz)
- **Véges/végtelen** nyelv: véges ill. végtelen sok szót tartalmaz
- **Nyelvcsalád** ($\mathcal{L}$): nyelvek egy halmaza (pl. $\mathcal{L}_3$ = reguláris nyelvek)

### Halmazműveletek

| Művelet | Definíció |
|---|---|
| Unió | $L_1 \cup L_2$ |
| Metszet | $L_1 \cap L_2$ |
| Különbség | $L_1 \setminus L_2$ |
| Komplementer | $\bar{L} = V^* \setminus L$ |

### Konkatenáció és hatványozás

$$L_1 L_2 = \{u_1 u_2 \mid u_1 \in L_1,\, u_2 \in L_2\}$$

- Asszociatív, de általában **nem kommutatív**
- $L^0 = \{\varepsilon\}$, $L^i = L \cdot L^{i-1}$

### Kleene-lezárt és pozitív lezárt

$$L^* = \bigcup_{i \geq 0} L^i \qquad L^+ = \bigcup_{i \geq 1} L^i$$

Ha $\varepsilon \in L$: $L^+ = L^*$; egyébként $L^+ = L^* \setminus \{\varepsilon\}$.

Azonosságok: $L^* L^* = L^*$, $(L^*)^* = L^*$, $(L_1 \cup L_2)^* = (L_1^* L_2^*)^*$.

### Tükrörkép-nyelv

$L^{-1} = \{u^{-1} \mid u \in L\}$. Tulajdonságok: $(L_1 L_2)^{-1} = L_2^{-1} L_1^{-1}$, $(L^*)^{-1} = (L^{-1})^*$.

### Prefix- és suffixnyelv

- $\text{PRE}(L) = \{u \mid \exists v : uv \in L\}$
- $\text{SUF}(L) = \{u \mid \exists v : vu \in L\}$

### Zártsági tulajdonságok

Egy $\mathcal{L}$ nyelvcsalád **zárt** egy $n$-változós $\varphi$ műveletre nézve, ha $L_1, \ldots, L_n \in \mathcal{L}$ esetén $\varphi(L_1, \ldots, L_n) \in \mathcal{L}$.

Minden $\mathcal{L}_i$ ($i = 0,1,2,3$) zárt az unióra, konkatenációra és Kleene-lezártra (reguláris műveletek). Részletesen: [[concepts/bvszam/zartsagi-tulajdonsagok|zartsagi-tulajdonsagok]].

## Kapocs

- [[concepts/bvszam/abece-es-szavak]] — az alap szóműveletek
- [[concepts/bvszam/chomsky-hierarchia]] — a négy nyelvcsalád ($\mathcal{L}_0$–$\mathcal{L}_3$)
- [[concepts/bvszam/homomorfizmus]] — nyelvek képe homomorfizmus alatt
- [[concepts/bvszam/zartsagi-tulajdonsagok]] — részletes zártsági bizonyítások
