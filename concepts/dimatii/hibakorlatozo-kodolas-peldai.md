---
tags: [concept, dimatii/hibakorlatozo-es-linearis-kodok]
sources: [DimatIIEa09.pdf, DimatIIEa10.pdf]
derivation: source
updated: 2026-09-08
---

# Hibakorlátozó kódolás példái

Az ISBN ellenőrző számjegye, a paritásbites kód és a kétdimenziós paritásellenőrzés: három elemi, a gyakorlatban használt hibakorlátozó kód.

## Tartalom

### ISBN (International Standard Book Number)

Legyen $d_1, d_2, \dots, d_n$ decimális számjegyek egy sorozata ($n \le 10$). Egészítsük ki a sorozatot egy $n+1$-edik számjeggyel, amelynek értéke
$$d_{n+1} = \sum_{j=1}^n j \cdot d_j \pmod{11},$$
ha az nem 10, különben $d_{n+1}$ legyen X.

Ha valamelyik számjegyet elírjuk, akkor az összefüggés nem teljesülhet: $d_{n+1}$ elírása esetén ez nyilvánvaló, $j \le n$ esetén pedig $d_j$ helyett $d_j'$-t írva az összeg $j(d_j' - d_j)$-vel nőtt, ami nem lehet 11-gyel osztható.

Két szomszédos számjegy felcserélése is észrevehető: ha $j < n$ esetén $d_j$-t és $d_{j+1}$-et felcseréljük, az összeg
$$j d_{j+1} + (j+1) d_j - j d_j - (j+1) d_{j+1} = d_j - d_{j+1}$$
-gyel nő, ami csak akkor lehet 11-gyel osztható, ha $d_j = d_{j+1}$.

Az ISBN 2007 óta 13 jegyű. A személyi számnál is hasonló ellenőrzést használnak. Az ISBN 1-hibajelző.

### Paritásbites kód

Egy $n$ hosszú 0-1 sorozatot egészítsünk ki egy $n+1$-edik bittel, ami legyen 1, ha a sorozatban páratlan sok 1-es van, különben pedig legyen 0. Ha egy bit megváltozik, akkor észleljük a hibát. A paritásbites kód 1-hibajelző.

### Kétdimenziós paritásellenőrzés

Rendezzük a biteket táblázatba, és az oszlopok és sorok végén helyezzünk el paritásbitet:

$$\begin{matrix}
b_{0,0} & \cdots & b_{0,j} & \cdots & b_{0,n-1} & \mid & b_{0,n}\\
\vdots & & \vdots & & \vdots & \mid & \vdots\\
b_{m-1,0} & \cdots & b_{m-1,j} & \cdots & b_{m-1,n-1} & \mid & b_{m-1,n}\\
\hline
b_{m,0} & \cdots & b_{m,j} & \cdots & b_{m,n-1} & \mid & b_{m,n}
\end{matrix}$$

Ha megváltozik egy bit, akkor a sor és az oszlop végén jelez az ellenőrző bit, és ebből tudjuk javítani a hibát. Ha két bit változik meg, akkor észleljük a hibát, de nem tudjuk javítani. A kétdimenziós paritásellenőrzés tehát 2-hibajelző, és egyben FEC-jellegű, mert egy hibát javítani is tud.

## Kapocs

- [[concepts/dimatii/hibajelzes-es-hibajavitas]] — a fogalmi keret, amelynek ezek a példái
- [[concepts/dimatii/hamming-tavolsag]] — a példák hibajelző képessége a kód távolságából adódik
- [[concepts/dimatii/linearis-kod]] — a paritásbites kód lineáris, $[n, n-1, 2]_2$ paraméterekkel
- [[concepts/dimatii/generatormatrix]] — a paritásbites kód generátormátrixa
