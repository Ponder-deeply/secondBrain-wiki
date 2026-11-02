---
tags: [concept]
sources: [Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-21
---

# Hányadostest

Legalább 2 elemű integritási tartomány testbe ágyazható: az $(a,b)$ párok ekvivalenciaosztályai, a törtek, testet alkotnak.

## Tartalom

**Definíció (hányadostest).** Legyen $R$ legalább 2 elemű integritási tartomány. A $T = \{(a,b) \mid a, b \in R,\ b \ne 0\} = R \times R^*$ halmazon legyen
$$(a,b) \sim (c,d) \iff a\cdot d = b\cdot c.$$
Ez ekvivalenciareláció. A $\sim$ által meghatározott osztályok testet alkotnak a következő műveletekre:
$$\overline{(a,b)} + \overline{(c,d)} = \overline{(ad + bc,\ bd)}, \qquad \overline{(a,b)} \cdot \overline{(c,d)} = \overline{(ac,\ bd)}.$$

Az $\overline{(a,b)}$ osztály a szokásos $a/b$ tört; $b \ne 0$ és $d \ne 0$ miatt $bd \ne 0$ (nullosztómentesség), ezért a műveletek értelmesek. Példa: $\mathbb{Z}$ hányadosteste $\mathbb{Q}$.

### Racionális függvénytest

**Definíció.** Valamely $K$ test esetén a $K[x]$ integritási tartomány hányadosteste a **racionális függvénytest**, jelölése $K(x)$. (Ebben a testben értelmezzük a Gauss-tétel „$K$ a hányadosteste" feltételét $R = K[x]$-re; lásd [[concepts/dimatii/primitiv-polinom-es-gauss-lemma]].)

## Kapocs

- [[concepts/dimatii/integritasi-tartomany]] — az $R$ szükséges tulajdonsága
- [[concepts/dimatii/test]] — a konstrukció eredménye
- [[concepts/dimatii/maximalis-es-primideal]] — a faktorgyűrű mint test
- [[concepts/dimatii/primitiv-polinom-es-gauss-lemma]] — Gauss-tétel: felbontás a hányadostest és a gyűrű fölött
