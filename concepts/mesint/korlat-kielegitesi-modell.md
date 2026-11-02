---
tags: [concept]
sources: [04.visszalep.pdf]
derivation: source
kind: model
element: water
updated: 2026-10-12
---

# Korlát-kielégítési modell (bináris)

A korlát-kielégítési modell olyan $n$-est keres a véges $D_1,\dots,D_n$ tartományok szorzatában, amely kielégíti a változópárokra előírt bináris korlátokat; a visszalépéses keresés vágó szabályai ezen a modellen általánosan megfogalmazhatók.

## Tartalom

### Az $n$-királynő újabb modellje

Legyen $D_i$ az $i$-dik sor szabad mezőinek oszlopszámai, kezdetben $D_i=\{1..n\}$. Keressük azt az $(x_1,\dots,x_n)\in D_1\times\dots\times D_n$ elhelyezést ($x_i$ az $i$-dik sorban elhelyezett királynő oszlopszáma), amelyben nincs ütés: minden $i,j$ párra

$$C_{ij}(x_i,x_j) \equiv (x_i\neq x_j \;\wedge\; |x_i-x_j|\neq|i-j|).$$

A megoldás visszalépéses kereséssel adható, vágási szabályokkal, amelyek folyamatosan törlik a $D_i$-k haszontalan elemeit, és ha valamelyik $D_i$ kiürül, visszalépésre kényszerítik az algoritmust. Lásd [[concepts/mesint/n-kiralyno-problema]].

### Általános bináris modell

Keressük azt az $(x_1,\dots,x_n)\in D_1\times\dots\times D_n$ $n$-est ($D_i$ véges), amely kielégít néhány $C_{ij}\subseteq D_i\times D_j$ bináris korlátot.

Példák:

1. **Házasságközvetítő probléma** ($n$ férfi, $m$ nő): $x_i$ az $i$-dik férfi felesége, $D_i=\{1..m\}$ azon elemei, amelyekre $\text{szimpatikus}(i,x_i)$; minden $(i,j)$-re $C_{ij}(x_i,x_j)\equiv(x_i\neq x_j)$ (nincs bigámia).
2. **Gráfszínezés** ([[concepts/mesint/grafszinezes]]): $n$ csúcs, $m$ szín; $x_i$ az $i$-dik csúcs színe, $D_i=\{1..m\}$; szomszédos $i,j$-re $C_{ij}(x_i,x_j)\equiv(x_i\neq x_j)$.

### Modellfüggő vezérlési stratégia

Az FC, PLF, LF vágó szabályai a korlátokkal fogalmazhatók meg anélkül, hogy a korlátok jelentését ismernünk kellene:

- $\text{Töröl}(i,k): D_i := D_i - \{e\in D_i \mid \neg C_{ik}(e,x_k)\}$
- $\text{Szűr}(i,j): D_i := D_i - \{e\in D_i \mid \forall f\in D_j: \neg C_{ij}(e,f)\}$

Ezek tehát nem heurisztikák, hanem [[concepts/mesint/modellfuggo-vezerles]] szerinti stratégiák: a modellezési módszerhez kapcsolódnak, nem a feladathoz. Modellfüggő sorrendi szabályok is konstruálhatók:

- mindig a legkisebb tartományú, még kitöltetlen komponensnek válasszunk előbb értéket;
- egy adott korlát által vizsgált komponenseket lehetőleg közvetlenül egymás után töltsük ki.

## Kapocs

- [[concepts/mesint/forward-checking]] — Töröl-alapú vágó szabály
- [[concepts/mesint/look-forward]] — Szűr-alapú vágó szabályok
- [[concepts/mesint/sorrendi-heurisztikak]] — sorrendi szabályok
- [[concepts/mesint/allapotter-modell]] — a modell, amelyből a korlát-kielégítési nézet kinőtt
