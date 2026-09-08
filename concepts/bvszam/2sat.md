---
tags: [concept]
sources: [10.md]
derivation: source
updated: 2026-04-09
---

# 2SAT

A 2SAT az a kielégíthetőségi probléma, amelynél a formula 2KNF alakú (minden klózban pontosan 2 literál). Szemben a 3SAT NP-teljességével, 2SAT polinom időben eldönthető.

## Tétel: 2SAT $\in$ P

## Bizonyítás — implikációs gráf

Legyen $\varphi$ egy $x_1, \ldots, x_n$ változókat tartalmazó 2KNF formula $m$ klózzal.

Konstruáljuk a $G_\varphi$ **implikációs gráfot**:
- **Csúcsok:** $2n$ darab — minden $x_i$-hez $x_i$ és $\neg x_i$.
- **Élek:** minden $l_i \lor l_j$ klózhoz adjuk hozzá a $(\neg l_i, l_j)$ és $(\neg l_j, l_i)$ irányított éleket.

**Motiváció:** $l_i \lor l_j \equiv (\neg l_i \Rightarrow l_j) \land (\neg l_j \Rightarrow l_i)$.

## Kielégíthetőségi feltétel

**Állítás:** $\varphi$ akkor és csak akkor kielégíthető, ha egyetlen $i$-re sem kerül $x_i$ és $\neg x_i$ ugyanabba az erősen összefüggő komponensbe (EÖK) $G_\varphi$-ben.

**Bizonyítás (vázlat):**
- Ha $x_i$ és $\neg x_i$ ugyanabban az EÖK-ban van, az ellentmondást ad (egyszerre kellene igaz és hamis).
- Ha nem kerülnek ugyanabba az EÖK-ba, megadható kielégítő értékadás: minden $i$-re $x_i$ értéke igaz, ha $G_\varphi$-ben $\neg x_i$-ből $x_i$-be vezet irányított út (vagyis $x_i$ EÖK-ja a topologikus sorrendben később jön); egyébként hamis.

## Algoritmikus következmény

$G_\varphi$ felépítése $O(n + m)$, az EÖK-ok meghatározása (pl. Tarjan-algoritmussal) szintén $O(n + m)$ — így 2SAT polinom időben eldönthető.

## Kapocs

- [[concepts/bvszam/ksat-es-3sat]] — 3SAT NP-teljes; kSAT összehasonlítás
- [[concepts/bvszam/hornsat]] — HORNSAT szintén P-beli, más módszerrel
- [[concepts/bvszam/bonyolultsagelmeleti-osztalyok]] — P vs. NP, komplexitásosztályok
