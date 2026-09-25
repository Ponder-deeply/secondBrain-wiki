---
tags: [concept, logika/rezolucio-iteletlogika]
sources: [Rezolúció_I.pdf]
references: [Tk. 93-96. o., Tk. 99-100. o.]
derivation: source
updated: 2026-09-08
---

# Klóz és klózhalmaz

A klóz (elemi diszjunkció) és a klózhalmaz a rezolúciós kalkulus alapfogalmai: egy KNF alakú formula kielégíthetetlenségének vizsgálata visszavezethető a benne szereplő klózok halmazának kielégíthetetlenségére.

## Tartalom

### Literál, elemi konjunkció/diszjunkció

**Literál:** egy prímformula (ítéletváltozó) vagy annak negáltja. A literál **alapja** a benne szereplő prímformula. A literált **egységkonjunkciónak** vagy **egységdiszjunkciónak** (egységklóz) is nevezzük — részletesebben lásd [[concepts/logika/iteletlogikai-formula]].

**Elemi konjunkció / elemi diszjunkció:** egységkonjunkció/diszjunkció, illetve különböző alapú literálok konjunkciója/diszjunkciója. Az **elemi diszjunkciót klóznak is nevezzük** — ez a rezolúciós kalkulus alapegysége.

**Teljes elemi konjunkció/diszjunkció:** egy elemi konjunkció/diszjunkció *teljes* egy adott $n$ változós logikai műveletre nézve, ha mind az $n$ ítéletváltozó alapja valamelyik benne szereplő literálnak.

### KNF/KKNF és DNF/KDNF

Ezekre az elnevezésekre épül a normálformák fogalma:

- **KNF** (konjunktív normálforma): elemi diszjunkciók (klózok) konjunkciója. **KKNF** (kitüntetett KNF), ha teljes elemi diszjunkciók konjunkciója.
- **DNF** (diszjunktív normálforma): elemi konjunkciók diszjunkciója. **KDNF** (kitüntetett DNF), ha teljes elemi konjunkciók diszjunkciója.

**Példa** — a $\neg(Z \supset \neg X) \vee Y$ formula igazságtáblája alapján:

$$\text{KKNF: } (\neg X \vee Y \vee Z) \wedge (X \vee Y \vee \neg Z) \wedge (X \vee Y \vee Z)$$

$$\text{KDNF: } (X \wedge Y \wedge Z) \vee (X \wedge Y \wedge \neg Z) \vee (X \wedge \neg Y \wedge Z) \vee (\neg X \wedge Y \wedge Z) \vee (\neg X \wedge Y \wedge \neg Z)$$

$$\text{KNF (egyszerűsítés után): } (Y \vee Z) \wedge (X \vee Y)$$

A rezolúciós kalkulus szempontjából ennyi elég: a klózhalmaz, amiből a rezolúció dolgozik, épp egy (nem feltétlen kitüntetett) KNF klózainak halmaza. A normálformákhoz tartozó ekvivalens átalakításokat (DeMorgan-szabályok, egyszerűsítési szabályok) lásd [[concepts/bvszam/itelet-kalkulus]] "Literál, klóz, konjunktív normálforma" szakaszában.

### Klóz mint klóz — elnevezések argumentumszám szerint

- **$n$-változós (n-argumentumos) klóz** — $n$ különböző alapú literálból áll.
- **1-változós klóz** — **egységklóz**.
- **0-változós klóz** — az **üres klóz**, jele $\square$.

Az üres klóz szemantikailag azonosan hamis: nincs olyan interpretáció, amely kielégítené.

### Igazhalmaz, hamishalmaz

Egy $n$-változós formula az igazságtáblájával megadott $\{i,h\}^n \to \{i,h\}$ leképezést ír le.

- Egy formula **igazhalmaza** azon $I$ interpretációk halmaza, amelyekre a formula helyettesítési értéke igaz.
- Egy formula **hamishalmaza** azon $I$ interpretációk halmaza, amelyekre a formula helyettesítési értéke hamis.

Kielégíthetetlen formula igazhalmaza üres — ekkor a KKNF alakjában minden teljes elemi konjunkció szerepel. Ha szisztematikusan egyszerűsítünk, a klózok literálszáma addig csökken, amíg $0$ nem lesz (üres klóz). Így egy KNF alakú formuláról egyszerűsítéssel eldönthető, hogy kielégíthetetlen-e.

### Klózhalmaz

Egy KNF alakú formula kielégíthetetlenségének vizsgálata ekvivalens a KNF-ben szereplő klózok $S$ **halmaza** kielégíthetetlenségének vizsgálatával. Az $S$ klózhalmaz kielégíthetetlen, ha $S$ tetszőleges interpretációjában legalább egy $C \in S$ hamis; egy $C$ klóz hamis egy interpretációban, ha *minden* literálja hamis.

Ez a klózhalmaz-szemléletű megfogalmazás az alapja mind az [[concepts/logika/iteletlogikai-szemantikus-fa]]-nak (a klózok interpretációkra való illesztésének), mind a [[concepts/logika/rezolucios-kalkulus]] rezolúciós levezetésének.

## Kapocs

- [[concepts/logika/iteletlogikai-formula]] — a literál, elemi konjunkció/diszjunkció fogalmának ítéletlogikai háttere
- [[concepts/logika/iteletlogikai-szemantikus-fa]] — klózok illesztése szemantikus fára, zárt szemantikus fa
- [[concepts/logika/rezolucios-kalkulus]] — a klózhalmaz kielégíthetetlenségének eldöntése rezolúcióval
- [[concepts/bvszam/itelet-kalkulus]] — a $Form$ szintaxis, amelyben a klóz mint speciális alakú formula értelmezhető
