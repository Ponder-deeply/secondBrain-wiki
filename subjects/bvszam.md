---
tags:
  - subject
sources:
  - 1.-bevezetés.md
  - 2.-lingram-és-regexp.md
  - "3.-automata,-det-&-nemdet.md"
  - 4.-myhill-nerode-és-minimál-automata.md
  - "5.-környezetfüggetlen-gramm,-cnf,-cyk-pumpálási-lemma.md"
  - 6.-veremauto-és-környezetfüggetlen-nyelv.md
  - 07.md
  - 08.md
  - 09.md
  - 10.md
  - 11.md
  - 12.md
derivation: source
updated: 2026-08-05
state: "[[IV]]"
---

# Bevezetés a számításelméletbe (bvszam)

A tárgy a formális nyelvek, grammatikák, automaták és a Chomsky-hierarchia alapjait tárgyalja; a reguláris és környezetfüggetlen nyelvek elméletétől a Turing gépekig, eldönthetőségelméletig és bonyolultságelméletig.

## Témakörök

### Matematikai előismeretek
- Halmaz- és relációelméleti alapok, reflexív-tranzitív lezárt — [[concepts/bvszam/halmaz-relacio-alapfogalmak|halmaz-relacio-alapfogalmak]]
- Gráf-alapfogalmak: séta–út–kör, összefüggőség, fa, feszítőfa — [[concepts/bvszam/graf-alapfogalmak|graf-alapfogalmak]]
- Ítéletkalkulus: szintaxis, szemantika, kielégíthetőség, KNF — [[concepts/bvszam/itelet-kalkulus|itelet-kalkulus]]
- Elsőrendű logika: term, formula, interpretációs struktúra, kötött/szabad változó — [[concepts/bvszam/elsorendu-logika|elsorendu-logika]]

### Alapfogalmak
- Ábécé, szó, konkatenáció, Kleene-lezárt — [[concepts/bvszam/abece-es-szavak|abece-es-szavak]]
- Formális nyelv, nyelvi műveletek (unió, konkatenáció, tükrörkép, prefixnyelv) — [[concepts/bvszam/formalis-nyelvek|formalis-nyelvek]]
- Homomorfizmus — [[concepts/bvszam/homomorfizmus|homomorfizmus]]

### Grammatikák
- Generatív grammatika, levezetés, generált nyelv — [[concepts/bvszam/generativ-grammatika|generativ-grammatika]]
- Chomsky-hierarchia (0–3 típus) — [[concepts/bvszam/chomsky-hierarchia|chomsky-hierarchia]]
- Zártsági tulajdonságok — [[concepts/bvszam/zartsagi-tulajdonsagok|zartsagi-tulajdonsagok]]
- Lineáris grammatikák (bal- és jobblineáris) — [[concepts/bvszam/linearis-grammatika|linearis-grammatika]]
- Reguláris (3-as típusú) grammatikák normálformája — [[concepts/bvszam/regularis-normalforma|regularis-normalforma]]

### Reguláris nyelvek
- Reguláris kifejezések, Arden-tétel — [[concepts/bvszam/regularis-kifejezesek|regularis-kifejezesek]]
- Véges determinisztikus automata (VDA) — [[concepts/bvszam/vda|vda]]
- Véges nemdeterminisztikus automata (VNDA), determinizálás — [[concepts/bvszam/vnda|vnda]]
- Myhill–Nerode tétel, minimális automata — [[concepts/bvszam/myhill-nerode|myhill-nerode]]
- $\mathcal{L}_3$ algoritmikus problémák (üresség, egyenlőség, tartalmazás) — [[concepts/bvszam/l3-algoritmikus-problemak|l3-algoritmikus-problemak]]

### Környezetfüggetlen nyelvek
- Környezetfüggetlen grammatika, redukált grammatika — [[concepts/bvszam/kornyezetfuggetlen-grammatika|kornyezetfuggetlen-grammatika]]
- Chomsky normálforma (CNF) — [[concepts/bvszam/chomsky-normalforma|chomsky-normalforma]]
- Levezetési fa, egyértelmű grammatika — [[concepts/bvszam/levezetes-fa|levezetes-fa]]
- Bar-Hillel lemma (pumpálási lemma) — [[concepts/bvszam/bar-hillel-lemma|bar-hillel-lemma]]
- CYK algoritmus — [[concepts/bvszam/cyk-algoritmus|cyk-algoritmus]]

### Veremautomaták és magasabb osztályok
- Veremautomata (nemdeterminisztikus és determinisztikus) — [[concepts/bvszam/veremautomata|veremautomata]]
- Végállapottal vs. üres veremmel elfogadás — [[concepts/bvszam/verem-elfogadas|verem-elfogadas]]
- Veremautomata ↔ KF grammatika ekvivalencia — [[concepts/bvszam/va-kf-ekvivalencia|va-kf-ekvivalencia]]
- Környezetfüggő nyelvek, hossz-nemcsökkentő grammatika — [[concepts/bvszam/kornyezetfuggo-nyelvek|kornyezetfuggo-nyelvek]]
- Kuroda normálforma — [[concepts/bvszam/kuroda-normalforma|kuroda-normalforma]]

### Turing gépek és kiszámíthatóság
- A kiszámíthatóságelmélet története: Hilbert programja, Gödel/Church/Turing — [[concepts/bvszam/kiszamithatosagelmelet-tortenete|kiszamithatosagelmelet-tortenete]]
- Problémák formális nyelvként; számossági érv eldönthetetlen problémák létezésére — [[concepts/bvszam/problemak-mint-formalis-nyelvek|problemak-mint-formalis-nyelvek]]
- Determinisztikus Turing gép (DTG), konfiguráció, Church–Turing tézis — [[concepts/bvszam/turing-gep|turing-gep]]
- $k$-szalagos Turing gép, „$f(n)$ időben eldönthető" — [[concepts/bvszam/tobb-szalagos-turing-gep|tobb-szalagos-turing-gep]]
- Egyirányban végtelen szalagú TG és ekvivalenciája a kétirányúval — [[concepts/bvszam/turing-gep-egyiranyu-szalag|turing-gep-egyiranyu-szalag]]
- $k$-szalagos TG szimulálása egyszalagossal, $O(f(n)^2)$ — [[concepts/bvszam/turing-gep-szimulacio|turing-gep-szimulacio]]
- Nemdeterminisztikus Turing gép (NTG), számítási fa, DTG szimulálása — [[concepts/bvszam/nemdeterminisztikus-turing-gep|nemdeterminisztikus-turing-gep]]
- Turing gépek bináris kódolása, $\langle M, w \rangle$ — [[concepts/bvszam/turing-gep-kodolas|turing-gep-kodolas]]
- Univerzális Turing gép; $L_u \in \text{RE}\setminus\text{R}$ — [[concepts/bvszam/univerzalis-turing-gep|univerzalis-turing-gep]]
- TG mint szófüggvény-kiszámító; kiszámítható függvény — [[concepts/bvszam/kiszamithato-szofuggveny|kiszamithato-szofuggveny]]

### Eldönthetőség
- Rekurzív (R) és rekurzívan felsorolható (RE) nyelvek, $L_u$, megállási probléma — [[concepts/bvszam/r-re-nyelvek|r-re-nyelvek]]
- Many-one és polinom idejű visszavezetés ($\leq$, $\leq_p$) — [[concepts/bvszam/visszavezetes|visszavezetes]]
- Eldönthetetlen problémák: $L_u$, $L_\emptyset$, $L_{EQ}$, KF- és logikai problémák — [[concepts/bvszam/eldonthetetlen-problemak|eldonthetetlen-problemak]]
- A megállási probléma $L_h$; $L_h \in \text{RE}\setminus\text{R}$ — [[concepts/bvszam/megallasi-problema|megallasi-problema]]
- Rice tétel (RE-beli tulajdonságok eldönthetetlensége) — [[concepts/bvszam/rice-tetel|rice-tetel]]
- Post megfelelkezési probléma (PMP, MPMP) — [[concepts/bvszam/post-megfelelkezesi-problema|post-megfelelkezesi-problema]]
- Eldönthetetlenség az elsőrendű logikában (PMP-visszavezetés) — [[concepts/bvszam/elsorendu-logika-eldonthetetlenseg|elsorendu-logika-eldonthetetlenseg]]
- $\mathcal{L}_0 = \text{RE}$; $\mathcal{L}_1 \subsetneq \text{R}$; összefoglaló táblázat — [[concepts/bvszam/l0-re-ekvivalencia|l0-re-ekvivalencia]]
- Lineárisan korlátolt automata (LKA) — [[concepts/bvszam/linearis-korlatolt-automata|linearis-korlatolt-automata]]

### Bonyolultságelmélet
- $O$, $\Omega$, $\Theta$ aszimptotikus jelölések — [[concepts/bvszam/aszimptotikus-jeloles|aszimptotikus-jeloles]]
- TIME, NTIME, P, NP; P $\neq$ NP sejtés; NP-teljesség — [[concepts/bvszam/bonyolultsagelmeleti-osztalyok|bonyolultsagelmeleti-osztalyok]]
- NP-teljesség és NP-nehézség, osztály-zártság — [[concepts/bvszam/np-teljesseg|np-teljesseg]]
- Cook–Levin tétel: SAT NP-teljes (tableau-kódolás) — [[concepts/bvszam/cook-levin-bizonyitas|cook-levin-bizonyitas]]
- kSAT; SAT $\leq_p$ 3SAT klóz-felosztással — [[concepts/bvszam/ksat-es-3sat|ksat-es-3sat]]
- 2SAT $\in$ P; implikációs gráf, EÖK-feltétel — [[concepts/bvszam/2sat|2sat]]
- HORNSAT $\in$ P; Horn-formulák — [[concepts/bvszam/hornsat|hornsat]]
- 3SZÍNEZÉS NP-teljessége (visszavezetés 3SAT-ból) — [[concepts/bvszam/3szinezes|3szinezes]]
- Gráfelméleti NP-teljes problémák: teljes részgráf, független csúcshalmaz, csúcslefedés — [[concepts/bvszam/grafelmeleti-np-teljes|grafelmeleti-np-teljes]]
- Hamilton-út/-kör, utazó ügynök, leghosszabb út — [[concepts/bvszam/hamilton-np-teljes|hamilton-np-teljes]]
- NP-köztes (Ladner), GRÁFIZOMORFIZMUS, PRÍMFAKTORIZÁCIÓ; coNP, UNSAT, TAUT — [[concepts/bvszam/np-koztes-es-conp|np-koztes-es-conp]]
- Tárbonyolultság: SPACE/NSPACE/PSPACE, Savitch tétele, QSAT — [[concepts/bvszam/tarbonyolultsag-pspace|tarbonyolultsag-pspace]]
- L, NL, log-tárú visszavezetés, Immermann–Szelepcsényi — [[concepts/bvszam/logaritmikus-tarbonyolultsag|logaritmikus-tarbonyolultsag]]
- A szóprobléma bonyolultsága a Chomsky-hierarchiában — [[concepts/bvszam/szoproblema-bonyolultsag|szoproblema-bonyolultsag]]
- Összefoglalás: L⊆NL=coNL⊆P⊆NP⊆PSPACE=NPSPACE⊆EXPTIME — [[concepts/bvszam/bonyolultsagi-osztalyok-hierarchia|bonyolultsagi-osztalyok-hierarchia]]

## Kapocs

- [[concepts/bvszam/chomsky-hierarchia]] — a tárgy gerince
- [[concepts/bvszam/vda]] — reguláris felismerők
- [[concepts/bvszam/veremautomata]] — KF felismerők
- [[concepts/bvszam/turing-gep]] — TG felismerők / döntők
- [[concepts/bvszam/bonyolultsagelmeleti-osztalyok]] — P, NP
