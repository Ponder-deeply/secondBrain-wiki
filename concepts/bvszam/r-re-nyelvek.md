---
tags: [concept]
sources: [07.md, 08.md, 08.md]
derivation: source
updated: 2026-08-28
---

# Rekurzív és rekurzívan felsorolható nyelvek (R és RE)

Az R és RE osztályok a Turing gépek által felismerhető és eldönthető problémák osztályai; a Chomsky-hierarchia legfelső szintjét alkotják.

## Definíciók

**RE (rekurzívan felsorolható):** $L \in \text{RE}$, ha létezik $M$ TG, amelyre $L = L(M)$, azaz $M$ pontosan az $L$-beli szavakon áll meg elfogadó állapotban (nem $L$-beli szavakon megállhat elutasítóban, vagy hurokba eshet).

**R (rekurzív / eldönthető):** $L \in \text{R}$, ha létezik $M$ TG, amelyre minden bemenetre megáll, és $L = L(M)$. (M totálisan definiált.)

$$\mathcal{L}_0 = \text{RE}, \quad \text{R} \subsetneq \text{RE}$$

## Az univerzális TG és $L_u$

Az **univerzális Turing gép** $U$ képes szimulálni tetszőleges $M$ TG-t $\langle M \rangle$ kódolása alapján.

$$L_u = \{\langle M, w \rangle \mid M \text{ TG elfogadja } w\text{-t}\}$$

**Tétel:** $L_u \in \text{RE} \setminus \text{R}$ — azaz $L_u$ felsorolható, de nem eldönthető.

**Bizonyítás (diagonalizáció):** Feltéve, hogy $L_u \in \text{R}$, megkonstruálható egy $D$ TG, amely saját kódolásán pontosan akkor áll meg elfogadva, ha nem fogadja el önmagát — ellentmondás.

## Megállási probléma

$$L_{\text{halt}} = \{\langle M, w \rangle \mid M \text{ megáll } w\text{-n}\}$$

**Tétel:** $L_{\text{halt}} \notin \text{R}$ (visszavezethető $L_u$-ra).

Részletes tárgyalás: [[concepts/bvszam/megallasi-problema|megallasi-problema]].

## $\overline{L_u} \notin \text{RE}$

Ha $\overline{L_u} \in \text{RE}$ lenne, akkor $L_u \in \text{R}$ következne (mindkét irányból felsorolható ⟹ eldönthető). Ellentmondás.

## Összefüggések

| Osztály | Felismerhető | Eldönthető |
|---------|-------------|------------|
| R       | igen        | igen       |
| RE      | igen        | nem feltétlen |
| co-RE   | komplementer felsorolható | nem feltétlen |

**Tétel:** $L \in \text{R} \iff L \in \text{RE}$ és $\bar{L} \in \text{RE}$.

## Kapocs

- [[concepts/bvszam/turing-gep]] — TG definíciója
- [[concepts/bvszam/nemdeterminisztikus-turing-gep]] — NTG és RE kapcsolata
- [[concepts/bvszam/rice-tetel]] — RE-beli tulajdonságok eldönthetetlensége
- [[concepts/bvszam/chomsky-hierarchia]] — $\mathcal{L}_0 = \text{RE}$
- [[concepts/bvszam/univerzalis-turing-gep]] — $L_u$ 4-szalagos szimulációs bizonyítása
- [[concepts/bvszam/megallasi-problema]] — $L_h \in \text{RE} \setminus \text{R}$
- [[concepts/bvszam/visszavezetes]] — many-one visszavezetés, $L_u \leq L_h$, RE nem zárt komplementerre
- [[concepts/bvszam/kiszamithato-szofuggveny]] — a visszavezetési függvény fogalma
