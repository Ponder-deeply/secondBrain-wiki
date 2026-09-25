---
tags: [concept, dimatii/hibakorlatozo-es-linearis-kodok]
sources: [DimatIIEa09.pdf, DimatIIEa10.pdf]
derivation: source
updated: 2026-09-08
---

# Ciklikus kód

Olyan kód, amely zárt a kódszavak koordinátáinak ciklikus eltolására.

## Tartalom

### Definíció

Egy $K \subset \mathbb{F}_q^n$ kód **ciklikus**, ha minden $(u_1, u_2, \dots, u_{n-1}, u_n) \in K$ esetén
$$(u_2, u_3, \dots, u_n, u_1) \in K .$$

### Példa

A $K = \{000, 101, 110, 011, 111\}$ bináris kód ciklikus: minden elemének ciklikus eltoltja is szerepel benne.

Ez a kód azonban **nem lineáris**: $101 + 111 = 010 \notin K$. A ciklikusság tehát önmagában nem vonja maga után a linearitást; a fontos kódcsalád a ciklikus *lineáris* kódoké, ahol a két szerkezet együtt van jelen.

### Jelentősége

A ciklikus lineáris kódok azért kiemelkedően fontosak, mert a ciklikus eltolás az $\mathbb{F}_q[x]/(x^n - 1)$ maradékosztály-gyűrűben az $x$-szel való szorzásnak felel meg; így a kód ideálként írható le, a kódolás és a dekódolás pedig polinomaritmetikára vezethető vissza. A polinomgyűrűk apparátusát az előadás korábbi része tárgyalja.

## Kapocs

- [[concepts/dimatii/linearis-kod]] — a szerkezet, amellyel a ciklikusság együtt hasznos igazán
- [[concepts/dimatii/hamming-tavolsag]] — a kódok minősítésének közös metrikája
- [[concepts/dimatii/polinomgyuru]] — az algebrai háttér, amelyen a ciklikus kódok elmélete nyugszik
