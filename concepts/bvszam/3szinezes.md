---
tags: [concept]
sources: [11.md]
derivation: source
updated: 2026-04-09
---

# 3SZÍNEZÉS NP-teljessége

A 3SZÍNEZÉS probléma az egyik alapvető NP-teljes gráfprobléma; bizonyítása 3SAT-ból való visszavezetéssel történik.


## Definíció

Egy $G = (V, E)$ gráf **$k$-színezhető**, ha létezik $c : V \to \{1, \ldots, k\}$ színezés úgy, hogy minden $\{u,v\} \in E$ élre $c(u) \neq c(v)$.

$$\text{3SZÍNEZÉS} = \{\langle G \rangle \mid G \text{ 3-színezhető}\}$$

## NP-beli

Egy NTG nemdeterminisztikusan kioszt minden csúcsnak egy színt $\{1,2,3\}$-ból, majd polinom időben ellenőrzi az éleket.

## NP-teljesség: 3SAT $\leq_p$ 3SZÍNEZÉS

**Visszavezetés konstrukciója** $\varphi$ 3-CNF formulából $G_\varphi$ gráfot épít:

**Változócsúcsok:** Minden $x_i$ változóhoz két csúcs: $x_i$ és $\bar{x}_i$, köztük él (komplementer pár).

**Paletta csúcsok:** Három speciális csúcs: $A$ (igaz/zöld), $B$ (hamis/piros), $\top$ (alap/kék). $A$, $B$, $\top$ klikket alkotnak (egymással összekötöttek).

Minden $x_i$–$\bar{x}_i$ pár kötve van $\top$-hoz: ezért egyikük $A$ (igaz), a másik $B$ (hamis) lesz.

**Klózcsúcsok:** Minden klózhoz egy ötszög-szerkezet (5 csúcsos részgráf) épül a 3 literál csúcsaiból és $B$-ből, amelynek lényege: ha mindhárom literál hamis (piros), az ötszög nem 3-színezhető.

**G$_0$ lemma:** Az ötszög-szerkezet pontosan akkor terjeszthető ki érvényes 3-színezéssé, ha legalább egy literál igaz (zöld szomszédot ad $B$-nek).

## Visszavezetés helyessége

- $\varphi$ kielégíthető $\Rightarrow$ $G_\varphi$ 3-színezhető:
  Legyenek a színek piros, zöld, kék. Ha $x_i$ igaz: $x_i$ zöld, $\bar{x}_i$ piros. $A$ kék, $B$ piros. Minden klóz legalább egy igaz literált tartalmaz, így a lemma alapján az ötszög kiterjeszthető.

- $G_\varphi$ 3-színezhető $\Rightarrow$ $\varphi$ kielégíthető:
  $A$ kék, $B$ piros (feltehetőleg). $x_1,\ldots,x_n,\bar{x}_1,\ldots,\bar{x}_n$ mind $A$ szomszédai, tehát nem lehetnek kékek. Minden $(x_i, \bar{x}_i)$ párban pontosan egy piros és egy zöld van. Az ötszögök 3-színezéséből következik, hogy minden klóznak van zöld szomszédja — azaz legalább egy igaz literálja.

A visszavezetés polinom idejű (a gráf mérete $O(|\varphi|)$).

## 2-színezés

A 2-színezhető gráfok pontosan a **páros gráfok**. Ez lineáris időben eldönthető (BFS/DFS).

## Kapocs

- [[concepts/bvszam/bonyolultsagelmeleti-osztalyok]] — P, NP, NP-teljesség definíciói
- [[concepts/bvszam/np-koztes-es-conp]] — NP-köztes, coNP
