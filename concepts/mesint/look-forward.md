---
tags: [concept]
sources: [04.visszalep.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-12
---

# Partial Look Forward és Look Forward

A Partial Look Forward (PLF) és a Look Forward (LF) a Forward Checking ([[concepts/mesint/forward-checking]]) erősebb vágó szabályai: a törlések mellett a még kitöltetlen sorok tartományait egymáson is szűrik.

## Tartalom

Mindkettő: **VL1 + vágó szabály**, a $k$-dik lépésben a FC törlései után további szűrést végez.

**Szűr(i, j):** törli $D_i$ azon haszontalan szabad mezőit, amelyek ütik a $j$-edik sor összes szabad mezőjét. (Ha egy $e\in D_i$ értékhez nincs $D_j$-ben vele összeférő érték, $e$ nem lehet megoldás része.)

### PLF

```
for i = k+1 .. n loop
    for j = i+1 .. n loop      (i < j)
        Szűr(i, j)
    endloop
endloop
if ∃i ∈ [k+1..n]: D_i = ∅ then visszalép
```

A slide példája: $k=3$, $i=4$, $j=6$, ekkor $D_4=\emptyset$, tehát visszalép.

### LF

```
for i = k+1 .. n loop
    for j = k+1 .. n and i ≠ j loop
        Szűr(i, j)
    endloop
endloop
if ∃i ∈ [k+1..n]: D_i = ∅ then visszalép
```

Az LF mindkét irányban szűr ($i\neq j$), a PLF csak $i<j$ esetén. A példa: $k=2$, a szűrések $(i,j)=(4,3),(5,4),(6,4),(6,5)$ után $D_6=\emptyset$.

Erősség szerint: FC < PLF < LF, de egyre drágább szűrés lépésenként. Korlát-kielégítési alakban: $\text{Szűr}(i,j): D_i := D_i - \{e\in D_i \mid \forall f\in D_j: \neg C_{ij}(e,f)\}$ ([[concepts/mesint/korlat-kielegitesi-modell]]).

## Kapocs

- [[concepts/mesint/forward-checking]] — a leggyengébb vágó szabály
- [[concepts/mesint/visszalepeses-kereses]] — az alapalgoritmus
- [[concepts/mesint/korlat-kielegitesi-modell]] — a Szűr általános definíciója
