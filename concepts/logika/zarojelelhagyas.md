---
tags: [concept, logika/iteletlogika-szintaxis]
sources: [iteletlogika.pdf]
references: [Pásztorné Varga Katalin – Várterész Magda, A matematikai logika alkalmazásszemléletű tárgyalása]
derivation: source
updated: 2026-09-08
---

# Zárójelelhagyás

A zárójelelhagyás célja, hogy egy teljesen zárójelezett [[concepts/logika/iteletlogikai-formula|ítéletlogikai formulából]] a szerkezet megtartása mellett a lehető legtöbb zárójelet elhagyjuk, a műveletek prioritásának bevezetésével.

## Tartalom

### Műveleti precedencia

A műveletek prioritása csökkenő sorrendben:

$$\neg, \ \wedge, \ \vee, \ \supset$$

Azaz a negáció köt legerősebben, utána a konjunkció, majd a diszjunkció, végül az implikáció.

### A zárójelelhagyás lépései

1. A formula külső zárójelpárjának elhagyása (ha van ilyen).
2. Egy binér logikai összekötő hatáskörébe eső részformula külső zárójele elhagyható, ha a részformula fő logikai összekötőjele nagyobb prioritású, mint a befoglaló összekötőjel.

### Láncformulák zárójelezése

Tetszőleges $A_1, \dots, A_n$ formulák esetén:

- **Konjunkciós lánc** ($A_1 \wedge A_2 \wedge \dots \wedge A_n$): tetszőlegesen zárójelezhető — a $\wedge$ asszociatív, a zárójelezés nem befolyásolja a jelentést.
- **Diszjunkciós lánc** ($A_1 \vee A_2 \vee \dots \vee A_n$): tetszőlegesen zárójelezhető, ugyanezen okból.
- **Implikációs lánc** ($A_1 \supset A_2 \supset \dots \supset A_n$): a zárójelezés **jobbról balra** kötelező —
  $$A_1 \supset (A_2 \supset ( \dots (A_{n-1} \supset A_n) \dots))$$
  mert az implikáció nem asszociatív; ezt a különbséget az [[concepts/logika/iteletlogikai-formula]] lapon tárgyalt szintaktikai helyesség-példák is illusztrálják, ahol a konjunkciós/diszjunkciós lánc többértelműsége szemantikailag ártalmatlan, az implikációé viszont nem.

### Példák

| Teljesen zárójelezett | Zárójelelhagyás után |
|---|---|
| $(((X \supset Y) \wedge (Y \supset Z)) \supset (\neg X \vee Z))$ | $(X \supset Y) \wedge (Y \supset Z) \supset \neg X \vee Z$ |
| $((Y \wedge \neg X) \supset (\neg Z \vee V))$ | $Y \wedge \neg X \supset \neg Z \vee V$ |
| $(((Y \supset X) \supset \neg Z) \supset V)$ | $((Y \supset X) \supset \neg Z) \supset V$ |

A harmadik példa mutatja, hogy egy belső implikáció zárójele — mivel az implikáció a legalacsonyabb prioritású — nem hagyható el akkor sem, ha az egész formula fő összekötőjele is implikáció: a $((Y \supset X) \supset \neg Z)$ részformula zárójele a bal-jobb szerkezet egyértelműsítéséhez szükséges marad.

## Kapocs

- [[concepts/logika/iteletlogikai-formula]] — a teljesen zárójelezett formula definíciója, amelyet a zárójelelhagyás enyhít
- [[concepts/logika/formulaszerkezet]] — a szerkezeti fa, amely a zárójelezéstől függetlenül egyértelmű
- [[concepts/logika/igazsagtabla]] — a rövidített jelölés az igazságtáblák fejlécében
- [[concepts/logika/logikai-osszetettseg]] — a hatáskör fogalma, amely a zárójelelhagyás szabályának alapja
