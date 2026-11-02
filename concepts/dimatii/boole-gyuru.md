---
tags: [concept]
sources: [Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf]
derivation: source
kind: model
element: fire
updated: 2026-10-21
---

# Hatványhalmaz-gyűrű és Boole-gyűrű

Egy halmaz részhalmazai a szimmetrikus differenciával mint összeadással és a metszettel mint szorzással gyűrűt alkotnak, amely kommutatív, 2 karakterisztikájú és nem nullosztómentes.

## Tartalom

### A példa

Legyen $H$ tetszőleges halmaz, $R$ a $H$ részhalmazainak halmaza. Az $(R; \Delta, \cap)$ struktúrában $\Delta$ a szimmetrikus differencia, $\cap$ a metszet. Az előadás szerint bizonyítható:

- **a)** $R$ gyűrű, nullelemmel $\emptyset$;
- **b)** minden $A \subseteq H$-ra $A \cap A = A^2 = A$ (**Boole-gyűrű**);
- **c)** minden $A \subseteq H$-ra $A \,\Delta\, A = \emptyset$, tehát $\mathrm{char}\,R = 2$;
- **d)** $R$ kommutatív;
- **e)** $R$ nem nullosztómentes: diszjunkt, nemüres halmazokra $A \cap B = \emptyset$;
- **f)** a c) és d) állítás minden Boole-gyűrűben igaz.

A bizonyításokat az előadásdiák nem részletezi.

### Miért érdekes

Ellenpélda arra, hogy a karakterisztika-tétel a nullosztómentességre épül: itt minden elem additív rendje 2, de a gyűrű nem nullosztómentes (lásd e)).

## Kapocs

- [[concepts/dimatii/gyuru]] — az alapfogalom
- [[concepts/dimatii/nullosztomentes-gyuru]] — karakterisztika és nullosztók
