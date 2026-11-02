---
tags: [concept]
sources: [01.bevezetes.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-12
---

# Gráfreprezentáció

Minden útkeresési problémához tartozik egy, a modellezésből származó gráfreprezentáció: egy $(R, s, T)$ hármas, amelynek megoldása célcsúcs vagy az oda vezető (esetleg optimális) út.

## Tartalom

### A hármas

A gráfreprezentáció egy $(R, s, T)$ hármas, ahol

- $R = (N, A, c)$ a **reprezentációs gráf** ($\delta$-gráf vagy ÉS/VAGY gráf),
- $s \in N$ a **startcsúcs**,
- $T \subseteq N$ a **célcsúcsok** halmaza.

### A probléma megoldása

- egy $t$ cél vagy $\langle t_1, \dots, t_m \rangle$ célcsúcs-sorozat megtalálása ($t, t_1, \dots, t_m \in T$), vagy
- egy $s \to t$ vagy $s \to \langle t_1, \dots, t_m \rangle$ út megtalálása, esetleg egy optimális $s \to^* T$ úté.

## Kapocs

- [[concepts/mesint/utkeresesi-problema]] — a gráfreprezentációval adott útkeresési probléma
- [[concepts/mesint/modellezes-es-kereses]] — a modellezés adja a reprezentációt
- [[concepts/mesint/utkereses-delta-grafban]] — keresés a reprezentációs gráfban
- [[concepts/mesint/utkereses-es-vagy-grafban]] — keresés ÉS/VAGY reprezentációs gráfban
- [[concepts/mesint/es-vagy-grafok]] — a reprezentációs gráf egyik típusa
