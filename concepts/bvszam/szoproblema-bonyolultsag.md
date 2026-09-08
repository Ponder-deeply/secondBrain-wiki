---
tags: [concept]
sources: [szelmJegyzet.pdf]
derivation: source
updated: 2026-08-05
---

# A szóprobléma bonyolultsága

A szóprobléma — adott $G$ grammatikára és $u$ szóra eldönteni, hogy $u \in L(G)$ — bonyolultsága a Chomsky-hierarchiában lefelé haladva nő: regulárisra lineáris, környezetfüggetlenre köbös idő, környezetfüggőre PSPACE-teljes, általános grammatikára pedig eldönthetetlen.

## A probléma

**Szóprobléma:** a bemenet egy $G=(V,\Sigma,R,S)$ grammatika és egy $u \in \Sigma^*$ szó, a kérdés, hogy $u \in L(G)$ teljesül-e.

Gyakorlati jelentősége nagy: számos programozási nyelv szintaxisa környezetfüggetlen nyelvtanra épül, így a szóprobléma a programozási nyelvek elemzésének absztrakciójaként is felfogható.

## Bonyolultság a Chomsky-hierarchiában

| Grammatikatípus | Szóprobléma bonyolultsága |
|---|---|
| Reguláris (3. típus) | lineáris idő |
| Környezetfüggetlen (2. típus) | köbös idejű algoritmus ismert (pl. CYK) |
| Környezetfüggő (1. típus) | **PSPACE-teljes** — kifejezetten nehéz |
| Általános / mondatszerkezetű (0. típus) | **eldönthetetlen** |

Az általános nyelvtanok egyszerűen képesek szimulálni egy egyszalagos Turing-gépet, ezért az ő esetükben a szóprobléma eldönthetetlen.

## Kapocs

- [[concepts/bvszam/cyk-algoritmus]] — köbös idejű szóprobléma-eldöntés KF grammatikákra
- [[concepts/bvszam/chomsky-hierarchia]] — a négy grammatikatípus
- [[concepts/bvszam/kornyezetfuggo-nyelvek]] — 1. típusú nyelvek
- [[concepts/bvszam/tarbonyolultsag-pspace]] — PSPACE és PSPACE-teljesség
- [[concepts/bvszam/eldonthetetlen-problemak]] — eldönthetetlenség
- [[concepts/bvszam/l3-algoritmikus-problemak]] — reguláris nyelvek algoritmikus kérdései
