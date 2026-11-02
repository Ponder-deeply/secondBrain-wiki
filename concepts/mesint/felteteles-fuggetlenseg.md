---
tags: [concept]
sources: [10.bizonytalansag.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-12
---

# Feltételes függetlenség

$A$ és $B$ feltételesen függetlenek $E$-re nézve, ha nincs köztük közvetlen függőségi kapcsolat, csak $E$-n keresztül.

## Tartalom

- **Közönséges függetlenség**: $p(A,B) = p(A)\,p(B)$.
- **Feltételes függetlenség** $E$-re nézve:
$$p(A,B \mid E) = p(A \mid E)\,p(B \mid E)$$
  ekvivalensen $p(A \mid B,E) = p(A \mid E)$, illetve $p(B \mid A,E) = p(B \mid E)$.

### Esetei (irányított gráfként)

Három szerkezet esetén függetlenek $A$ és $B$ $E$ ismeretében:

1. $A \leftarrow E \rightarrow B$ — $A$ is, $B$ is függ $E$-től (közös ok);
2. $A \rightarrow E \rightarrow B$ — láncszerű függés;
3. $A \leftarrow E \leftarrow B$ — láncszerű függés fordított irányban.

### Alkalmazás

A fogászati példában a lyukas fog ($ly$) és a fájás ($f$) egyaránt a szuvasodás ($sz$) következménye, attól eltekintve függetlenek: $p(ly \mid f, sz) = p(ly \mid sz)$. Ez teszi lehetővé, hogy a [[concepts/mesint/bayes-tetel]] alkalmazásánál kevés apriori valószínűség elég legyen.

## Kapocs

- [[concepts/mesint/bayes-tetel]] — a példa, ahol a függetlenséget kihasználjuk
- [[concepts/mesint/bayes-halo]] — a feltételes függetlenségek gráfban való felismerése
- [[concepts/mesint/klasszikus-valoszinuseg-szamitas]] — a valószínűségi alapok
