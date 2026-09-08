---
tags: [concept]
sources: [szelmJegyzet.pdf]
derivation: source
updated: 2026-08-05
---

# NP-teljesség és NP-nehézség

Az NP-teljes problémák az NP osztály legnehezebb nyelvei: minden NP-beli probléma polinom időben visszavezethető rájuk. Ez a lap a definíciókat és a gyakorlatban használt terjesztési tételeket gyűjti össze.

## Polinom idejű visszavezetés

Legyenek $L_1 \in \Sigma^*$ és $L_2 \in \Delta^*$ nyelvek, $v$ pedig kiszámítható függvények egy osztálya. $L_1$ **visszavezethető $v$ szerint** $L_2$-re ($L_1 \leq_v L_2$), ha $L_1 \leq L_2$ és az alkalmazott $f$ visszavezető függvény $v$-ben van.

Ha $v$ a polinom időben kiszámítható függvények osztálya, akkor $L_1$ **polinom időben visszavezethető** $L_2$-re: jelölés $L_1 \leq_p L_2$.

Egy $\textbf{C}$ problémaosztály **zárt a $v$-beli visszavezetésekre**, ha tetszőleges $L_1, L_2$ esetén $L_1 \leq_v L_2$ és $L_2 \in \textbf{C}$ $\Rightarrow$ $L_1 \in \textbf{C}$.

**Tétel:** P és NP zártak a polinom idejű visszavezetésekre.
*Bizonyítás vázlat:* ha $L_2 \in \text{NP}$ ($M_2$ NTG dönti) és $L_1 \leq_p L_2$ ($f$ kiszámítja $M$), akkor $M_1$ először $f(w)$-t számolja, majd $M_2$-t hívja; a $p_1, p_2$ polinom időigények kompozíciója polinom. P esetén $M_2$ determinisztikus.

## Definíció

Legyen $L$ egy probléma. $L$ **NP-teljes**, ha
1. $L \in \text{NP}$, és
2. minden további $L' \in \text{NP}$ polinom időben visszavezethető $L$-re.

Ha csak a 2. pont teljesül, $L$ **NP-nehéz**.

## Alaptételek

**Tétel:** Ha $L$ NP-teljes és $L \in \text{P}$, akkor $\text{P} = \text{NP}$.
*Bizonyítás:* tetszőleges $L' \in \text{NP}$-re $L' \leq_p L$, és mivel P zárt a $\leq_p$-re, $L' \in \text{P}$. Tehát $\text{NP} \subseteq \text{P}$, és $\text{P} \subseteq \text{NP}$ triviális.

**Tétel (terjesztés):** Ha $L_1$ NP-teljes, $L_2 \in \text{NP}$ és $L_1 \leq_p L_2$, akkor $L_2$ is NP-teljes.
*Bizonyítás:* tetszőleges $L \in \text{NP}$-re $L \leq_p L_1 \leq_p L_2$; a két visszavezetés kompozíciója polinom idejű, tehát $L \leq_p L_2$.

Ez a két tétel adja a gyakorlati módszert: az **első** NP-teljes problémát (SAT) közvetlenül a definícióból kell bizonyítani (Cook–Levin), minden továbbit pedig egy már ismert NP-teljes problémából való visszavezetéssel.

## Ismert NP-teljes problémák (e fejezetből)

- SAT, 3SAT — kielégíthetőség
- Teljes részgráf, Független csúcshalmaz, Csúcslefedés — gráfelméleti problémák
- 3SZÍNEZÉS
- Hamilton-út (irányított és irányítatlan), Irányítatlan Hamilton-kör, Tetszőleges Hamilton-út, Utazó ügynök, Leghosszabb út, Korlátozott feszítőfa, Részgráf izomorfizmus

## NP-köztes nyelvek

**Tétel (bizonyítás nélkül):** Ha $\text{P} \neq \text{NP}$, akkor van olyan $L \in \text{NP}$, hogy $L \notin \text{P}$, de $L$ nem NP-teljes. Az ilyen nyelveket **NP-köztes** nyelveknek nevezzük. Lehetséges jelölt: Gráf izomorfizmus.

## Kapocs

- [[concepts/bvszam/bonyolultsagelmeleti-osztalyok]] — P, NP osztályok, NP szerkezete
- [[concepts/bvszam/cook-levin-bizonyitas]] — SAT NP-teljessége a definícióból
- [[concepts/bvszam/ksat-es-3sat]] — 3SAT NP-teljes; SAT $\leq_p$ 3SAT
- [[concepts/bvszam/grafelmeleti-np-teljes]] — Teljes részgráf, Független csúcshalmaz, Csúcslefedés
- [[concepts/bvszam/hamilton-np-teljes]] — Hamilton-úttal kapcsolatos NP-teljes problémák
- [[concepts/bvszam/3szinezes]] — 3SZÍNEZÉS NP-teljessége
- [[concepts/bvszam/visszavezetes]] — a visszavezetés általános (kiszámíthatóságelméleti) fogalma
- [[concepts/bvszam/np-koztes-es-conp]] — NP-köztes nyelvek, coNP
