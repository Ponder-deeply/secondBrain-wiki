---
tags: [concept]
sources: [01.bevezetes.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-12
---

# ÉS/VAGY gráfok

Az ÉS/VAGY gráf élsúlyozott irányított hipergráf, amelyben egy csúcsból induló hiperél ÉS kapcsolatú élek kötege; a probléma dekompozíciós modell reprezentációja.

## Tartalom

$R=(N,A)$ élsúlyozott irányított hipergráf, ahol

- $N$ a csúcsok halmaza,
- $A\subseteq\{(n,M)\in N\times N^+ \mid 0\ne\lvert M\rvert<\infty\}$ a **hiperélek** halmaza; a hiperél ugyanazon csúcsból induló, ÉS kapcsolatú élek kötege,
- $\lvert M\rvert$ a hiperél **rendje**,
- $c(n,M)$ az $(n,M)$ él költsége.

Egy csúcsból csak véges sok hiperél indulhat, és $0<\delta\le c(n,M)$.

Egy csúcsból induló több hiperél egymás közti kapcsolata VAGY, egy hiperélen belül az $M$ csúcsai ÉS kapcsolatúak. A hiperutak és az útkeresés: [[concepts/mesint/hiperut]], [[concepts/mesint/utkereses-es-vagy-grafban]].

## Kapocs

- [[concepts/mesint/graf-fogalmak]] — az egyszerű ($\delta$-)gráf, amelyet általánosít
- [[concepts/mesint/problema-dekompozicios-modell]] — ezt a reprezentációt használja
- [[concepts/mesint/hiperut]] — út az ÉS/VAGY gráfban
