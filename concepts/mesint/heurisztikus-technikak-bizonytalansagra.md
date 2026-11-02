---
tags: [concept]
sources: [10.bizonytalansag.pdf]
derivation: source
kind: overview
element: water
updated: 2026-10-12
---

# Heurisztikus technikák bizonytalanság kezelésére

A valószínűségi (Bayes-hálós) számítás nehézkessége miatt a szabályalapú rendszerekben heurisztikus technikákat használnak: a szabályokhoz és tényekhez bizonytalansági értéket rendelnek, és új következtetési elvvel számolják tovább.

## Tartalom

### Szabályok bizonytalansággal: betörés–riasztó–szomszéd

Szabályok:

- $Sz \to R\ (0{,}9)$: ha a szomszéd hallani véli a riasztót, akkor szól a riasztónk.
- $R \to B\ (0{,}95)$: ha szól a riasztónk, akkor betörtek hozzánk.

Tény: $Sz$ (a szomszéd telefonál, hogy hallja a riasztót).

Kérdés: betörtek-e hozzánk? A klasszikus ([[concepts/mesint/szabalyalapu-kovetkeztetes]]) lépések: $Sz,\ Sz \to R \Rightarrow R$; $R,\ R \to B \Rightarrow B$.

### Új következtetési elv

$$T(p),\ T \to K\ (q) \Rightarrow K\ (p \cdot q)$$

Ha a feltétel $T$ bizonyossága $p$, és a szabály ereje $q$, akkor a következmény $K$ bizonyossága $p \cdot q$. A példában:

$$Sz(1) \Rightarrow R(0{,}9) \Rightarrow B(0{,}855),$$

mivel $1 \cdot 0{,}9 = 0{,}9$ és $0{,}9 \cdot 0{,}95 = 0{,}855$.

Megjegyzés: ez az eredmény ($0{,}855$) eltér a Bayes-hálós pontos számítás eredményétől ($p(B \mid Sz) = 0{,}0166$, ld. [[concepts/mesint/bayes-halo-kovetkeztetes]]), mert a heurisztikus szorzás nem veszi figyelembe a $B$ a priori valószínűségét és a téves riasztás lehetőségét; a szabályok ereje nem feltételes valószínűség.

### Ismert heurisztikus technológiák

A dia csak felsorolja (részletek nélkül):

- a MYCIN bizonytalanságkezelési technikája,
- a Dempster–Shafer-elmélet,
- a fuzzy következtetés.

## Kapocs

- [[concepts/mesint/bizonytalansagkezeles]] — a bizonytalanságkezelés áttekintése, amelynek ez a harmadik megközelítése
- [[concepts/mesint/bayes-halo-kovetkeztetes]] — a pontos valószínűségi alternatíva
- [[concepts/mesint/szabalyalapu-kovetkeztetes]] — a szabályalapú következtetés, amelyet a bizonytalansági értékek bővítenek
