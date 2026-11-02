---
tags: [concept]
sources: [07.jatek.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-12
---

# Alfa-béta algoritmus

Az alfa-béta algoritmus a minimax kiértékelést visszalépéses bejárással végzi, és vágásokkal kihagyja azokat a részfákat, amelyek nem befolyásolhatják az eredményt.

## Tartalom

### Működés

A részfát visszalépéses algoritmussal járjuk be (olyan mélységi bejárás, amely mindig csak egy utat tárol; vö. [[concepts/mesint/visszalepeses-kereses]]). Az aktuális úton fekvő csúcsok ideiglenes értékei:

- a MAX szintjein $\alpha$ érték: ennél rosszabb értékű állásba innen már nem juthatunk,
- a MIN szintjein $\beta$ érték: ennél jobb értékű állásba onnan már nem juthatunk.

Szabályok:

- **Lefelé haladva** a fában $\alpha := -\infty$ és $\beta := +\infty$.
- **Visszalépéskor** az éppen elhagyott gyerekcsúcs értéke (felhozott érték) módosíthatja a szülő értékét:
  - MAX szinten: $\alpha := \max(\text{felhozott érték}, \alpha)$,
  - MIN szinten: $\beta := \min(\text{felhozott érték}, \beta)$.
- **Vágás**: ha az úton van olyan $\alpha$ és $\beta$, hogy $\alpha \ge \beta$.

### Példa

A dia fáján (gyökér MAX, levelek pl. $8, 2, -2, 7, 8, 4, -1, 2$) a bal részfa kiértékelése után a gyökérben $\alpha = 2$. A jobb ágon a MIN csúcs értéke ($-1$, majd 2) már nem lehet jobb $2$-nél, így a hozzá tartozó további testvérek és részfák vágásra kerülnek (a dián szaggatott ívek jelölik). A végeredmény a gyökérben 2.

### Elemzés

- Ugyanazt a kezdőlépést kapjuk, amit a minimax talál. (Több egyforma kezdőirány esetén a "baloldalit" választjuk.)
- **Memóriaigény**: csak egy utat tárol.
- **Futási idő**: a vágások miatt sokkal jobb, mint a minimaxé.
  - *Átlagos eset*: egy csúcs alatt két belőle kiinduló ág megvizsgálása után már vághatunk.
  - *Optimális eset*: egy $d$ mélységű, $b$ elágazású fában a kiértékelt levélcsúcsok száma $\sqrt{b^d}$.
  - *Jó eset*: a részfa megfelelő rendezésével érhető el.

## Kapocs

- [[concepts/mesint/minimax-algoritmus]] — az alapalgoritmus, amelynek eredményét megőrzi.
- [[concepts/mesint/negamax-algoritmus]] — az egyszerűsített értékfelfuttatás, vele kombinálva használják.
- [[concepts/mesint/sorrendi-heurisztikak]] — a jó csúcssorrend itt is a vágások számát növeli.
- [[concepts/mesint/jatekot-jatszo-program]] — a programok alfa-béta kiértékelést végeznek.
