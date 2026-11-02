---
tags: [concept]
sources: [02.modellek.pdf]
derivation: source
kind: model
element: earth
updated: 2026-10-12
---

# Hanoi tornyai probléma

A Hanoi tornyai az [[concepts/mesint/allapotter-modell]] alappéldája: $n$ korong három rúd között mozgatható, az állapot a korongok elhelyezkedése, az állapot-gráf pedig $3^n$ csúcsú, önhasonló háromszögstruktúra.

## Tartalom

### Modell

- **Állapottér**: $AT = \{1,2,3\}^n$ — egy $1..n$ intervallummal indexelt egydimenziós tömb, elemei az $\{1,2,3\}$ halmazból valók. A tömb $i$-edik eleme az $i$-edik korong rúdjának száma; a korongok a rudakon méretük szerint fentről lefelé növekvő sorrendben vannak.
- **Kezdőállapot**: $[3,3,3]$ (minden korong a 3. rúdon). **Célállapot**: $[1,1,1]$.
- **Művelet**: `Rak(honnan, hova): AT → AT`.
  - HA a *honnan* és *hova* rudak léteznek és nem azonosak, és van korong a *honnan* rúdon, és a *hova* rúd vagy üres, vagy a legfelső korongja nagyobb, mint a *honnan* rúd legfelső (mozgatandó) korongja,
  - AKKOR `this[honnan legfelső korongja] := hova`.

### Implementáció

A C++ osztály sablonparamétere $n$ (alapértelmezés 3), egy `_a[n]` tömböt tárol. A `move(from, to)` megkeresi a `from` és `to` rúd legfelső korongját (a legkisebb indexű, azon a rúdon lévő elem), és csak akkor rakja át, ha a `from` nem üres, és a `to` üres vagy a legfelső korongja nagyobb. `final()` akkor igaz, ha minden elem 1; `init()` mindent 3-ra állít.

### Állapot-gráf

- Csúcsok száma: $3^n$.
- Csúcsok ki-foka: 2 vagy 3.
- Körök hossza: 2, 3, 6, 7, 9, ...
- A gráf rekurzívan háromszögekből épül fel (Sierpiński-háromszög alakú); a start és a cél a két csúcsa.

## Kapocs

- [[concepts/mesint/allapotter-modell]] — az általános modell
- [[concepts/mesint/allapotter-vs-problemater]] — a válasz itt műveletsorozat, nem állapot
- [[concepts/mesint/n-kiralyno-problema]] — másik mintapélda
