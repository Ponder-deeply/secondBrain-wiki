---
tags: [concept]
sources: [12.md, szelmJegyzet.pdf]
derivation: source
updated: 2026-08-05
---

# NP-köztes problémák és coNP

A bonyolultságelmélet finomabb szerkezete: az NP-teljes és P között elhelyezkedő NP-köztes osztály, valamint a komplementer coNP osztály.

## NP-köztes

**Definíció:** $L$ **NP-köztes**, ha $L \in \text{NP}$, de $L \notin \text{P}$ és $L$ nem NP-teljes.

**Ladner tétele (1975):** Ha $\text{P} \neq \text{NP}$, akkor létezik NP-köztes probléma.

(Bizonyítás: diagonalizáció — mesterségesen konstruált nyelv, amely "lassabban" NP-teljes, mint bármely konkrét NP-teljes.)

**Jelöltek valódi NP-köztes problémákra:**

| Probléma | Megjegyzés |
|---------|-----------|
| GRÁFIZOMORFIZMUS | Babai László (2017): quasi-polinom idejű ($n^{O(\log n)}$); NP-beli, de NP-teljessége nem ismert |
| PRÍMFAKTORIZÁCIÓ | $\text{FACTORING} \in \text{NP} \cap \text{coNP}$; kriptográfia alapja (RSA) |

## coC bonyolultsági osztályok

**Definíció:** Bármely $\mathcal{C}$ osztályra $\text{co}\mathcal{C} = \{\bar{L} \mid L \in \mathcal{C}\}$.

$$\text{coNP} = \{L \mid \bar{L} \in \text{NP}\}$$

**Determinisztikus osztályokra** a $\mathcal{C}$ és $\text{co}\mathcal{C}$ megegyezik (lásd lentebb a $\text{P} = \text{coP}$ tételt). **Nemdeterminisztikus** osztályoknál ez nem ilyen egyszerű: a sejtés szerint az NP és a coNP összehasonlíthatatlanok (egyik osztály problémái sincsenek benne a másikban).

**Következmény:** coNP zárt polinom idejű visszavezetésre nézve.

**3.27. Tétel:** Ha $\mathcal{C}$ zárt a $v$-beli visszavezetésekre, akkor $\text{co}\mathcal{C}$ is az.

**3.28. Tétel:** Ha $\mathcal{C}$ zárt a $v$-beli visszavezetésekre, és van olyan $L \in \mathcal{C}$ nyelv, ami $\text{co}\mathcal{C}$-teljes a $v$-beli visszavezetésekre, akkor $\mathcal{C} = \text{co}\mathcal{C}$. Ebből: ha egy coNP-teljes probléma NP-belinek bizonyulna, akkor $\text{NP} = \text{coNP}$.

## P = coP

**Tétel:** $\text{P} = \text{coP}$.

**Bizonyítás:** Ha $L \in \text{P}$, akkor létezik polinom idejű DTG $M$, amely $L$-t dönt el. $\bar{L}$-t egy módosított $M'$ dönti el, amelyben $q_i$ és $q_n$ állapotait felcseréljük.

## NP $\neq$ coNP?

**Sejtés:** $\text{NP} \neq \text{coNP}$.

A fenti DTG-trükk NTG-re nem működik: az elfogadó állapotot felcserélve $\bar{L}$ nem feltétlenül dönthető el NTG-vel.

Mivel NP zárt a polinom idejű visszavezetésekre, a 3.28. tétel alapján: ha sikerülne megmutatni, hogy $\text{UNSAT} \in \text{NP}$, akkor $\text{NP} = \text{coNP}$ teljesülne.

**Tétel (3.26.):** $L$ $\mathcal{C}$-teljes $\iff$ $\bar{L}$ co$\mathcal{C}$-teljes.

**Bizonyítás:**
- Ha $L \in \mathcal{C}$ és $\bar{L} \in \text{co}\mathcal{C}$ → definíció.
- Legyen $L' \in \mathcal{C}$, $L' \leq_p L$. Ekkor $\bar{L'} \leq_p \bar{L}$. $\bar{L'}$ befutja $\text{co}\mathcal{C}$-t, így $\bar{L}$ co$\mathcal{C}$-teljes.

## coNP-teljes problémák

$$\text{UNSAT} = \{\langle \varphi \rangle \mid \varphi \text{ kielégíthetetlen nulladrendű formula}\}$$
$$\text{TAUT} = \{\langle \varphi \rangle \mid \varphi \text{ nulladrendű tautológia}\}$$

**Tétel:** UNSAT és TAUT coNP-teljesek.

**Bizonyítás:**
- $\overline{\text{ÁLTSAT}} = \text{UNSAT}$, ahol ÁLTSAT NP-teljes (SAT speciális esete) → UNSAT coNP-teljes.
- $\text{UNSAT} \leq_p \text{TAUT}$: $\varphi \mapsto \neg\varphi$ polinom idejű visszavezetés.

## Összefüggések

$$\text{P} \subseteq \text{NP} \cap \text{coNP}$$

**Sejtések:** $\text{P} \neq \text{NP} \cap \text{coNP}$; $\text{NP} \neq \text{coNP}$.

Ha egy coNP-teljes probléma kiderülne NP-belinek, akkor $\text{NP} = \text{coNP}$ következne.

## Tárbonyolultsági megfelelők

A tárbonyolultsági osztályoknál a co-kérdés részben eldől:

- $\text{NPSPACE} = \text{coNPSPACE}$ — Savitch tételéből ($\text{NPSPACE} = \text{PSPACE}$, ami determinisztikus, így co-zárt).
- $\text{NL} = \text{coNL}$ — **Immermann–Szelepcsényi tétel** (3.46.), lásd [[concepts/bvszam/logaritmikus-tarbonyolultsag|logaritmikus-tarbonyolultsag]].

Ezzel szemben az NP vs. coNP kérdés továbbra is nyitott.

## Kapocs

- [[concepts/bvszam/bonyolultsagelmeleti-osztalyok]] — P, NP, NP-teljesség, TIME, NTIME
- [[concepts/bvszam/tarbonyolultsag-pspace]] — PSPACE, Savitch tétele, NPSPACE = PSPACE
- [[concepts/bvszam/logaritmikus-tarbonyolultsag]] — NL = coNL (Immermann–Szelepcsényi)
- [[concepts/bvszam/3szinezes]] — NP-teljes gráfprobléma
