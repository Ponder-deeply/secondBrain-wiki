---
tags: [concept]
sources: [szelmJegyzet.pdf]
derivation: source
updated: 2026-08-05
---

# Gráfelméleti NP-teljes problémák

Három egymással szorosan kapcsolódó gráfprobléma — **Teljes részgráf**, **Független csúcshalmaz** és **Csúcslefedés** — NP-teljessége, mind 3SAT-ból (illetve egymásból) való visszavezetéssel. Az alábbiakban $G$ mindig irányítatlan gráf.

## Definíciók

$$\text{Teljes részgráf} = \{\langle G, k\rangle \mid k \geq 1,\ G\text{-nek van } k \text{ csúcsú teljes részgráfja}\}$$

$$\text{Független csúcshalmaz} = \{\langle G, k\rangle \mid k \geq 1,\ G\text{-nek van } k \text{ elemű független csúcshalmaza}\}$$

$$\text{Csúcslefedés} = \{\langle G, k\rangle \mid k \geq 1,\ G\text{-nek van } k \text{ elemű csúcshalmaza, amely } G \text{ minden élének legalább egyik végpontját tartalmazza}\}$$

Mindhárom NP-beli: egy NTG megsejt $k$ csúcsot, majd polinom időben ellenőrzi a megfelelő tulajdonságot (teljes részgráf: minden pár össze van kötve; független halmaz: egyik pár sincs összekötve; csúcslefedés: minden él lefedett).

## Teljes részgráf NP-teljes — 3SAT $\leq_p$ Teljes részgráf

Legyen $\varphi = c_1 \land \dots \land c_k$ egy 3SAT-példány, $c_i = l_{i_1} \lor l_{i_2} \lor l_{i_3}$. A $G_\varphi$ gráf:
- Minden $c_i$ taghoz egy **háromszög** (3 csúcs, a tag literáljaihoz rendelve).
- Minden élt behúzunk, **kivéve**:
  - az egy klózhoz tartozó háromszög csúcsai közti éleket, és
  - az ellentétes literálokkal (pl. $x$ és $\neg x$) címkézett csúcsok közti éleket.

Ekkor $\langle \varphi \rangle \in \text{3SAT} \iff \langle G_\varphi, k\rangle \in \text{Teljes részgráf}$: egy $k$ csúcsú klikk pontosan akkor létezik, ha minden klózból kiválasztható egy igazzá tehető (egymásnak nem ellentmondó) literál. $G_\varphi$ polinom időben megkonstruálható.

## Független csúcshalmaz NP-teljes — Teljes részgráf $\leq_p$ Független csúcshalmaz

Legyen $\overline{G}$ a $G$ **komplementer gráfja** (ugyanazok a csúcsok, és két csúcs között pontosan akkor van él $\overline{G}$-ben, ha $G$-ben nincs). Ekkor $G$-ben van $k$ elemű teljes részgráf $\iff$ $\overline{G}$-ben van $k$ elemű független csúcshalmaz. $\overline{G}$ polinom időben megkonstruálható.

## Csúcslefedés NP-teljes — Független csúcshalmaz $\leq_p$ Csúcslefedés

Egy $n$ csúcsú $G$ gráfban a csúcsok egy $k$ elemű részhalmaza pontosan akkor független, ha a komplementere ($n-k$ csúcs) csúcslefedés. Tehát
$$\langle G, k\rangle \in \text{Független csúcshalmaz} \iff \langle G, n-k\rangle \in \text{Csúcslefedés}.$$
Az $n-k$ szám polinom időben kiszámítható.

## Kapocs

- [[concepts/bvszam/np-teljesseg]] — NP-teljesség definíciója, terjesztési tételek
- [[concepts/bvszam/ksat-es-3sat]] — 3SAT NP-teljes (a visszavezetések kiindulópontja)
- [[concepts/bvszam/hamilton-np-teljes]] — további NP-teljes gráfproblémák
- [[concepts/bvszam/3szinezes]] — 3SZÍNEZÉS NP-teljessége 3SAT-ból
- [[concepts/bvszam/bonyolultsagelmeleti-osztalyok]] — P, NP, NP-teljesség
