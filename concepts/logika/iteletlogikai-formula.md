---
tags: [concept]
sources: [iteletlogika.pdf]
references: [Pásztorné Varga Katalin – Várterész Magda, A matematikai logika alkalmazásszemléletű tárgyalása]
derivation: source
updated: 2026-09-08
---

# Ítéletlogikai formula ($L_0$)

Az ítéletlogika leíró nyelvének szintaxisa, $L_0$, szerkezeti rekurzióval jelöli ki, hogy a $V_0$ ábécé jeleinek mely sorozatai számítanak formulának.

## Tartalom

### A formula definíciója

**Ítéletlogikai formula** (szerkezeti rekurzióval):

1. **(alaplépés)** Minden ítéletváltozó ítéletlogikai formula. Ezeket **prímformulának** nevezzük.
2. **(rekurzív lépés)**
   - Ha $A$ ítéletlogikai formula, akkor $\neg A$ is az.
   - Ha $A$ és $B$ ítéletlogikai formulák, akkor $(A \circ B)$ is ítéletlogikai formula, ahol $\circ$ a három binér művelet ($\wedge$, $\vee$, $\supset$) bármelyike.
3. Minden ítéletlogikai formula az 1. és 2. szabály **véges sokszori** alkalmazásával áll elő.

A harmadik pont a lezárási feltétel: nélküle a definíció nem jelölné ki egyértelműen a formulák halmazát. A jelölésről — miért $\supset$ és nem $\to$ — lásd [[concepts/logika/iteletlogika-abece]].

A definíció **teljesen zárójelezett** formulákat ad: minden binér művelet alkalmazása egy külön zárójelpárt hoz be, a negáció viszont nem. A gyakorlatban ezt a zárójelözönt a [[concepts/logika/zarojelelhagyas]] szabályai enyhítik.

### Szerkezeti rekurzió és szerkezeti indukció

Két egymást kiegészítő módszer, amelyek a fenti definíció alakját követik:

- **Szerkezeti rekurzió** — *definíciós* módszer: alaplépés + rekurzív lépés. Így definiáljuk a formulákon értelmezett függvényeket, például a logikai összetettséget ([[concepts/logika/logikai-osszetettseg]]) vagy a helyettesítési értéket ([[concepts/logika/iteletlogikai-interpretacio]]).
- **Szerkezeti indukció** — *bizonyítási* módszer rekurzívan definiált struktúrák tulajdonságairól: alaplépés + indukciós lépés. Speciális esete a természetes számokon vett teljes indukció.

### Példák: szintaktikailag helyes-e?

| Formula | Helyes? | Megjegyzés |
|---|---|---|
| $X$ | igen | prímformula |
| $X \vee Y$ | nem | hiányzik a külső zárójelpár; helyesen: $(X \vee Y)$ |
| $(X \wedge Y)$ | igen | |
| $\neg X \wedge (Y \supset \neg X)$ | nem | helyesen: $(\neg X \wedge (Y \supset \neg X))$ |
| $(A \vee B) \wedge \neg X \wedge Z$ | nem | többféleképpen javítható, pl. $((A \vee B) \wedge (\neg X \wedge Z))$ |

Az utolsó sor tanulsága, hogy a hiányzó zárójelek nem csak formai hibát jelentenek: a lánc `∧`-jainak zárójelezése többféle formulát ad, és a definíció szerint egyik sem előbbre való a másiknál. Konjunkciós és diszjunkciós láncoknál ez a többértelműség szemantikailag ártalmatlan (asszociativitás), implikációnál viszont nem — lásd [[concepts/logika/zarojelelhagyas]].

### Literál, elemi konjunkció, elemi diszjunkció

Az $L_0$-beli formulák néhány kitüntetett alakja:

- **Literál:** ha $X$ ítéletváltozó, akkor $X$ és $\neg X$ literál. Az $X$ ítéletváltozó a literál **alapja**; $X$ és $\neg X$ azonos alapú literálok.
- **Elemi konjunkció:** különböző literálok konjunkciója, pl. $X \wedge \neg Y \wedge \neg W \wedge Z$.
- **Elemi diszjunkció:** különböző literálok diszjunkciója, pl. $\neg X \vee Y \vee \neg W \vee \neg Z$.

Az elemi diszjunkció a normálformák elméletében **klóz** néven szerepel; a konjunktív normálformát lásd [[concepts/bvszam/itelet-kalkulus]].

## Kapocs

- [[concepts/logika/iteletlogika-abece]] — a $V_0$ ábécé, amelynek jeleiből a formulák épülnek
- [[concepts/logika/formulaszerkezet]] — részformula, szerkezeti fa, szintaxisfa
- [[concepts/logika/zarojelelhagyas]] — a teljes zárójelezés enyhítése
- [[concepts/logika/logikai-osszetettseg]] — szerkezeti rekurzióval definiált mérőszám a formulákon
- [[concepts/bvszam/itelet-kalkulus]] — ugyanez a szintaxis $Form$ „legszűkebb halmaz” alakban
