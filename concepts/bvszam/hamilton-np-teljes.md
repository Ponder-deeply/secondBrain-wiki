---
tags: [concept]
sources: [szelmJegyzet.pdf]
derivation: source
updated: 2026-08-05
---

# Hamilton-úttal kapcsolatos NP-teljes problémák

Több olyan probléma, ahol gráfokban Hamilton-utat vagy -kört kell keresni, NP-teljes. A láncszerű visszavezetés a SAT-ból indul, és eljut az Utazó ügynök, a Leghosszabb út és a Korlátozott feszítőfa problémákig.

## Definíciók

$$\text{Hamilton-út} = \{\langle G, s, t\rangle \mid G \text{ irányított gráf},\ s,t \in V,\ \exists \text{ } s\text{-ből } t\text{-be Hamilton-út}\}$$

$$\text{Irányítatlan Hamilton-út} = \{\langle G, s, t\rangle \mid G \text{ irányítatlan},\ s,t \in V,\ \exists \text{ } s\text{-ből } t\text{-be Hamilton-út}\}$$

$$\text{Tetszőleges Hamilton-út} = \{\langle G\rangle \mid G \text{ irányítatlan},\ \exists s,t \in V : \text{van } s\text{-ből } t\text{-be Hamilton-út}\}$$

$$\text{Irányítatlan Hamilton-kör} = \{\langle G\rangle \mid G \text{ irányítatlan, van benne Hamilton-kör}\}$$

$$\text{Utazó ügynök} = \{\langle G, k\rangle \mid G \text{ irányítatlan, élein pozitív egész súlyokkal, van } \leq k \text{ összsúlyú Hamilton-kör}\}$$

$$\text{Leghosszabb út} = \{\langle G, k\rangle \mid G \text{ irányítatlan},\ k \leq |V|,\ \text{van legalább } k \text{ csúcsot érintő út}\}$$

$$\text{Korlátozott feszítőfa} = \{\langle G, k\rangle \mid G \text{ irányítatlan},\ k \leq |V|,\ \text{van olyan feszítőfa, melyben minden csúcs foka} \leq k\}$$

Mind NP-beli: egy NTG megsejti a csúcsok sorrendjét / az élhalmazt, majd polinom időben ellenőriz.

## Hamilton-út (irányított) NP-teljes — SAT $\leq_p$ Hamilton-út

$\varphi$ KNF-hez egy $G_\varphi$ irányított gráfot építünk:
- Minden $x_i$ változóhoz egy „kétirányú soros" részgráf, amelyben az egymás melletti csúcspárok a $\varphi$ tagjainak felelnek meg. A részgráfot balról jobbra bejárva $x_i$ = igaz, jobbról balra bejárva $x_i$ = hamis.
- A részgráfok egy lánccá fűződnek $s$-től $t$-ig.
- Minden $c_j$ taghoz egy külön csúcs. Ha $x_i$ szerepel $c_j$-ben (pozitívan), a megfelelő csúcspárból kitérő él vezet $c_j$-be és vissza úgy, hogy a kitérő csak balról-jobbra bejáráskor (igaz értéknél) tehető meg; $\neg x_i$ esetén a kitérő a jobbról-balra bejáráshoz illeszkedik.

Ekkor $\langle\varphi\rangle \in \text{SAT} \iff \langle G_\varphi, s, t\rangle \in \text{Hamilton-út}$: egy Hamilton-út pontosan akkor érinti minden $c_j$ csúcsot, ha minden klózban van legalább egy igaz literál.

## A láncolat további lépései

**Irányítatlan Hamilton-út** NP-teljes — Hamilton-út $\leq_p$ Irányítatlan Hamilton-út. Minden $v$ csúcsot három csúccsá ($v^{(0)}, v^{(1)}, v^{(2)}$) bontunk, $\{v^{(0)},v^{(1)}\}$ és $\{v^{(1)},v^{(2)}\}$ élekkel; minden $(v,w)$ irányított élnek $\{v^{(2)}, w^{(0)}\}$ él felel meg. A három csúcs kényszeríti a $0 \to 1 \to 2$ áthaladási irányt.

**Tetszőleges Hamilton-út** NP-teljes — Irányítatlan Hamilton-út $\leq_p$ Tetszőleges Hamilton-út. $G$-hez hozzáveszünk egy $s'$ csúcsot $s$-sel összekötve és egy $t'$ csúcsot $t$-vel összekötve; egy Hamilton-út $G'$-ben kényszerűen $s'$-ből $t'$-be megy, tehát $G$-ben $s$-ből $t$-be.

**Irányítatlan Hamilton-kör** NP-teljes — Irányítatlan Hamilton-út $\leq_p$ Irányítatlan Hamilton-kör. $G$-hez egy új $u$ csúcsot veszünk, és $u$-t összekötjük $s$-sel és $t$-vel; $G_k$-ban pontosan akkor van Hamilton-kör, ha $G$-ben van $s$-ből $t$-be Hamilton-út.

## Utazó ügynök, Leghosszabb út, Korlátozott feszítőfa

**Segédtétel:** ha $P_1$ a $P_2$ speciális esete és $P_1$ NP-nehéz, akkor $P_2$ is NP-nehéz (egy $P_2$-t eldöntő algoritmus $P_1$-et is eldönti).

- **Utazó ügynök** NP-teljes: az Irányítatlan Hamilton-kör speciális esete (minden élsúly 1, $k = |V|$).
- **Leghosszabb út** NP-teljes: a Tetszőleges Hamilton-út speciális esete ($k = |V|$).
- **Korlátozott feszítőfa** NP-teljes: a Tetszőleges Hamilton-út speciális esete ($k = 2$), mert egy gráfban pontosan akkor van Hamilton-út, ha van olyan feszítőfája, melyben minden csúcs foka legfeljebb 2.

## Kapocs

- [[concepts/bvszam/np-teljesseg]] — NP-teljesség, NP-nehézség, speciális eset segédtétel
- [[concepts/bvszam/grafelmeleti-np-teljes]] — Teljes részgráf, Független csúcshalmaz, Csúcslefedés
- [[concepts/bvszam/ksat-es-3sat]] — SAT/3SAT, a visszavezetési lánc kiindulópontja
- [[concepts/bvszam/bonyolultsagelmeleti-osztalyok]] — P, NP, NP-teljesség
