---
tags: [concept]
sources: [szelmJegyzet.pdf]
derivation: source
updated: 2026-08-05
---

# Gráf-alapfogalmak

A gráfok csúcsok és élek halmazából álló struktúrák; a számításelméletben számos algoritmikus probléma (út-, kör-, Hamilton-út-keresés) gráfokon fogalmazódik meg.

## Tartalom

### Irányítatlan és irányított gráf

Egy $G$ **gráf** csúcsok $V$ és élek $E$ halmazából áll.

- $G$ **irányítatlan gráf**, ha $E$ a $V$-beli elempárok rendezetlen halmaza, azaz $E \subseteq \{\{a,b\} \mid a, b \in V\}$.
- $G$ **irányított gráf**, ha $E$ a $V$-beli elempárok rendezett halmaza, azaz $E \subseteq V \times V$ — ekkor $E$ egy kétváltozós $V$-feletti reláció.

Az élek lehetnek **címkézettek** valamilyen objektumhalmaz elemeivel; alapesetben ezt nem követeljük meg.

### Séta, út, kör

Legyen $G = (V, E)$ irányítatlan gráf és $u = a_1 a_2 \ldots a_n$ ($n \ge 2$, $a_i \in V$).

- $u$ **$G$-beli séta**, ha minden $i \in [n-1]$-re $\{a_i, a_{i+1}\} \in E$.
- $u$ **út**, ha séta és a csúcsai páronként különböznek.
- $u$ **kör**, ha $a_1 = a_n$ és az $a_1, \ldots, a_{n-1}$ csúcsok páronként különböznek.

Irányított gráfokban a fenti fogalmak hasonlóan definiálhatók.

### Hamilton-út és Hamilton-kör

Egy $G$-beli utat **Hamilton-útnak**, illetve egy kört **Hamilton-körnek** nevezünk, ha tartalmazza a $G$ összes csúcsát. $G$ **körmentes**, ha nem tartalmaz kört.

### Összefüggőség, fa, feszítőfa

- $G$ **összefüggő**, ha bármely két csúcsa között vezet út.
- $G$ **fa**, ha összefüggő és körmentes.
- Egy $G' = (V', E')$ a $G$ **feszítőfája**, ha $G'$ fa, $V' = V$ és $E' \subseteq E$.

### Csúcs foka

Legyen $u \in V$. Az $u$ **foka** $|\{v \in V \mid \{u,v\} \in E\}|$, azaz az $u$-val éllel összekötött csúcsok száma.

## Kapocs

- [[concepts/bvszam/halmaz-relacio-alapfogalmak]] — az irányított gráf mint kétváltozós reláció
- [[concepts/bvszam/chomsky-hierarchia]] — a számításelmélet más alapmodelljei
