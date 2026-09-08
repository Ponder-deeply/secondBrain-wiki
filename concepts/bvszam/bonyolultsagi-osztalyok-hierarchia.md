---
tags: [concept]
sources: [szelmJegyzet.pdf]
derivation: source
updated: 2026-08-05
---

# Bonyolultsági osztályok hierarchiája

A számításelméletben tárgyalt bonyolultsági osztályok egy láncot alkotnak L-től R-ig; a legtöbb tartalmazásról nem tudjuk, valódi-e. Egyúttal: némely nehéz probléma egyszerű módosítással könnyűvé válik.

## Könnyű vagy nehéz?

Több NP-teljes (nehéz) probléma egyszerű módosítással **könnyűvé** válik:

- **3SAT** nehéz, de **2SAT** könnyű (P-beli, sőt NL-teljes).
- Két csúcs közti **Hamilton-út** keresése nehéz, de tetszőleges út keresése könnyű.
- **Korlátozott feszítőfa** keresése egy gráfban nehéz, de tetszőleges feszítőfa hatékonyan megkonstruálható.

Tanulság: ha egy problémát nem tudunk hatékonyan megoldani, érdemes átgondolni, nem fogalmazható-e újra egyszerűbben, céljainknak megfelelően.

## Az osztályok lánca

**3.48. Következmény:**
$$\text{L} \subseteq \text{NL} = \text{coNL} \subseteq \text{P} \subseteq \text{NP} \subseteq \text{PSPACE} = \text{NPSPACE} \subseteq \text{EXPTIME}$$

Az indoklások:

- $\text{L} \subseteq \text{NL}$, $\text{P} \subseteq \text{NP}$ — definíció szerint (determinisztikus $\subseteq$ nemdeterminisztikus).
- $\text{NL} = \text{coNL}$ — Immermann–Szelepcsényi tétel (3.46.).
- $\text{NL} \subseteq \text{P}$ — a konfigurációs gráf polinom méretű (3.45.).
- $\text{PSPACE} = \text{NPSPACE}$ — Savitch tételének következménye (3.34.).
- $\text{NP} \subseteq \text{PSPACE}$ — polinom idejű TG legfeljebb polinom tárat használhat.
- $\text{PSPACE} \subseteq \text{EXPTIME}$ — egy $p(n)$ tárú TG konfigurációs gráfja $2^{O(p(n))}$ méretű, ebben polinom időben kereshető út.

Biztosan tudjuk: $\text{P} \subsetneq \text{EXPTIME}$ és $\text{NL} \subsetneq \text{PSPACE}$. A sejtés, hogy a fenti tartalmazások **mindegyike** valódi.

## A PSPACE osztályon túl

$$(\text{N})\text{EXPTIME} = \bigcup_{k\geq 1}(\text{N})\text{TIME}(2^{n^k})$$
$$\text{EXPSPACE} = \bigcup_{k\geq 1}\text{SPACE}(2^{n^k})$$
$$k\text{EXPTIME} = \text{TIME}\big(\underbrace{2^{\cdot^{\cdot^{2^{n^k}}}}}_{k}\big), \qquad \text{ELEMENTARY} = \bigcup_{k\geq 1}k\text{EXPTIME}(n^k)$$

A teljes lánc (3.13. ábra):
$$\text{L} \subseteq \text{NL} \subseteq \text{P} \subseteq \text{NP} \subseteq \text{PSPACE} \subseteq \text{EXPTIME} \subseteq \text{NEXPTIME} \subseteq \text{EXPSPACE} \subseteq \text{2EXPTIME} \subseteq \text{ELEMENTARY} \subseteq \text{R}$$

Az ELEMENTARY-beli függvényeket **elemi függvényeknek** nevezzük; jól ismert nem elemi függvény az **Ackermann-függvény**.

## Kapocs

- [[concepts/bvszam/bonyolultsagelmeleti-osztalyok]] — P, NP, idő- és tárbonyolultság alapjai
- [[concepts/bvszam/tarbonyolultsag-pspace]] — PSPACE, Savitch tétele, PSPACE-teljesség
- [[concepts/bvszam/logaritmikus-tarbonyolultsag]] — L, NL, NL = coNL, NL ⊆ P
- [[concepts/bvszam/np-koztes-es-conp]] — coNP, NP ≠ coNP sejtés
- [[concepts/bvszam/ksat-es-3sat]] — 3SAT nehéz, 2SAT könnyű
