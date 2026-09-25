---
tags: [concept, logika/iteletlogika-szintaxis]
sources: [iteletlogika.pdf]
references: [Pásztorné Varga Katalin – Várterész Magda, A matematikai logika alkalmazásszemléletű tárgyalása]
derivation: source
updated: 2026-09-08
---

# Logikai összetettség

A logikai összetettség egy szerkezeti rekurzióval definiált mérőszám, amely egy ítéletlogikai formulához a benne előforduló logikai műveletek számát rendeli; ez alapján definiálható a logikai összekötőjel hatásköre és a formula fő logikai összekötőjele is.

## Tartalom

### Definíció szerkezeti rekurzióval

A formula $\ell$ logikai összetettsége:

**Alaplépés.** Ha $A$ ítéletváltozó, akkor $\ell(A) = 0$.

**Rekurziós lépések.**
$$\ell(\neg A) = \ell(A) + 1$$
$$\ell(A \circ B) = \ell(A) + \ell(B) + 1$$

Vagyis egy formula logikai összetettsége a benne szereplő logikai műveleti jelek (a negáció és a három binér művelet) összes előfordulásának száma. A definíció az [[concepts/logika/iteletlogikai-formula]] szerkezeti rekurziójának alakját követi: minden lépésben eggyel nő az összetettség.

**Példa.**
$$\ell((X \wedge Y) \supset (\neg Z \vee V)) = \ell(X \wedge Y) + \ell(\neg Z \vee V) + 1$$
$$= (\ell(X) + \ell(Y) + 1) + ((\ell(Z) + 1) + \ell(V) + 1) + 1 = (0+0+1) + ((0+1)+0+1) + 1 = 4$$

### Logikai művelet hatásköre

Egy logikai összekötőjel **hatásköre** a formula részformulái közül az a legkisebb logikai összetettségű, amelyben az adott összekötőjel előfordul.

**Példa.** A $(X \supset Y) \wedge (Y \supset Z) \supset \neg X \vee Z$ formula $\wedge$ műveletet tartalmazó részformulái közül:

- az egész formula: $\ell = 6$,
- $(X \supset Y) \wedge (Y \supset Z)$: $\ell = 3$.

A kisebb összetettségű, azaz $(X \supset Y) \wedge (Y \supset Z)$, a $\wedge$ hatásköre.

### Fő logikai összekötőjel

Egy formula **fő logikai összekötőjele** az az összekötőjel, amelynek a hatásköre maga a formula. Ez az az összekötőjel, amely a formula gyökerét adja a [[concepts/logika/formulaszerkezet|szerkezeti fában]], és amely a [[concepts/logika/zarojelelhagyas]] szabályainak alkalmazásakor meghatározza, mely részformulák zárójele hagyható el.

## Kapocs

- [[concepts/logika/iteletlogikai-formula]] — a szerkezeti rekurzió, amelynek alakját a logikai összetettség definíciója követi
- [[concepts/logika/formulaszerkezet]] — a hatáskör és a fő összekötőjel geometriai megfelelője a szerkezeti fában
- [[concepts/logika/zarojelelhagyas]] — a hatáskör fogalmára épülő zárójelelhagyási szabály
