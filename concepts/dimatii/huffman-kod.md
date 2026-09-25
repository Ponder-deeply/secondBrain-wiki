---
tags: [concept, dimatii/forraskodolas]
sources: [DimatIIEa08.pdf]
derivation: source
updated: 2026-09-08
---

# Huffman-kód

Alulról felfelé építkező kódkonstrukció, amely adott betűeloszláshoz optimális — minimális átlagos szóhosszúságú — prefix kódot ad.

## Tartalom

### A konstrukció

Legyen $\{a_1, a_2, \dots, a_n\}$ az üzenetek halmaza, a hozzájuk tartozó eloszlás $\{p_1, p_2, \dots, p_n\}$, a kódábécé elemszáma $r$.

1. Rendezzük relatív gyakoriság szerint csökkenő sorrendbe a betűket.
2. Osszuk el maradékosan $n - 2$-t $r - 1$-gyel:
   $$n - 2 = q(r-1) + m, \qquad 0 \le m < r - 1,$$
   és legyen $t = m + 2$.
3. Helyettesítsük az utolsó $t$ betűt egy új betűvel, amihez az elhagyott betűk relatív gyakoriságainak összegét rendeljük, és ezt az új betűt a gyakoriságának megfelelő helyre szúrjuk vissza a sorozatba.
4. Ezek után ismételjük meg az előző redukciót, de most már minden lépésben $r$ betűvel csökkentve a kódolandó halmazt, mígnem már csak $r$ betű marad.

Most a redukált ábécé legfeljebb $r$ betűt tartalmaz, és ha volt redukció, akkor pontosan $r$-et. Ezeket a kódoló ábécé elemeivel kódoljuk, majd a redukciónak megfelelően visszafelé haladva az összevont betűk kódját az összevonáskor kapott betű már meglévő kódjának a kódoló ábécé különböző betűivel való kiegészítésével kapjuk.

A $t$ kezdeti csoportméret éppen azt biztosítja, hogy a végén a fa minden belső csúcsa $r$-ágú legyen, vagyis a kódfában ne maradjon kihasználatlan ág.

### Optimalitás

**Tétel.** A Huffman-kód optimális.

### Példa

Legyen $A = \{a, b, \dots, j\}$, a relatív gyakoriságok
$$0{,}17;\ 0{,}02;\ 0{,}13;\ 0{,}02;\ 0{,}01;\ 0{,}31;\ 0{,}02;\ 0{,}17;\ 0{,}06;\ 0{,}09,$$
a kódoló ábécé pedig $\{0,1,2\}$. Itt $10 - 2 = 4\cdot(3-1) + 0$, így $t = 0 + 2 = 2$.

Az összevonások után a kapott kód:
$$a \mapsto 00,\quad h \mapsto 01,\quad c \mapsto 02,\quad f \mapsto 1,\quad j \mapsto 20,\quad i \mapsto 22,$$
$$b \mapsto 211,\quad d \mapsto 212,\quad g \mapsto 2100,\quad e \mapsto 2101 .$$

Entrópia: $\approx 1{,}73$. Átlagos szóhossz: $1{,}79$. Ugyanezen eloszlásra a Shannon-kód $2{,}3$ átlagos szóhosszat ad, tehát itt a Huffman-kód érezhetően jobb.

## Kapocs

- [[concepts/dimatii/optimalis-kod]] — a fogalom, amelyet a konstrukció megvalósít
- [[concepts/dimatii/shannon-kod]] — az egyszerűbb, de általában rosszabb konstrukció
- [[concepts/dimatii/kodfa]] — a konstrukció valójában egy kódfát épít alulról felfelé
- [[concepts/dimatii/entropia]] — a viszonyítási alap, amelyhez az átlagos szóhosszat mérjük
- [[concepts/dimatii/prefix-kod]] — a kapott kód prefix, tehát felbontható
