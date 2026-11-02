---
tags: [concept]
sources: [01.bevezetes.pdf]
derivation: source
kind: theorem
element: water
updated: 2026-10-12
---

# Útkeresés ÉS/VAGY gráfban

Az ÉS/VAGY gráfbeli megoldás-gráf keresése visszavezethető egy $\delta$-gráfban történő útkeresésre: a hiperutak bejárásai egy $\delta$-gráfot határoznak meg.

## Tartalom

A startcsúcsból induló hiperutakat (köztük a megoldás-gráfokat is) a **bejárásukkal** (közönséges irányított utakkal) ábrázolhatjuk, amelyek egy $\delta$-gráfot határoznak meg. Ennek a $\delta$-gráfnak

- csúcsai az eredeti ÉS/VAGY gráf csúcsainak sorozatai,
- startcsúcsa az ÉS/VAGY gráf startcsúcsából álló sorozat,
- célcsúcsai az ÉS/VAGY gráf célcsúcsaiból álló sorozatok.

Az így nyert $\delta$-gráf megoldási útjai az eredeti ÉS/VAGY gráfbeli megoldás-gráfokat reprezentálják. Ezért az ÉS/VAGY gráfban a megoldás-gráf megkeresése a neki megfeleltetett $\delta$-gráfban történő megoldási út megkeresésével helyettesíthető.

## Kapocs

- [[concepts/mesint/hiperut]] — hiperút, megoldás-gráf és bejárás
- [[concepts/mesint/es-vagy-grafok]] — az eredeti ÉS/VAGY gráf
- [[concepts/mesint/utkereses-delta-grafban]] — a visszavezetett keresés
- [[concepts/mesint/graf-reprezentacio]] — a reprezentációs gráf két típusa
- [[concepts/mesint/problema-redukcios-modell]] — ÉS/VAGY gráfot használó modell
