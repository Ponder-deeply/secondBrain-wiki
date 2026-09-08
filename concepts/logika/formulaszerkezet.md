---
tags: [concept]
sources: [iteletlogika.pdf]
references: [Pásztorné Varga Katalin – Várterész Magda, A matematikai logika alkalmazásszemléletű tárgyalása]
derivation: source
updated: 2026-09-08
---

# Formulaszerkezet: részformula, szerkezeti fa, szintaxisfa

Az ítéletlogikai formulák négy szerkezeti típusra oszthatók, amelyekhez a közvetlen részformula fogalmán keresztül szerkezeti fa és szintaxisfa rendelhető.

## Tartalom

### A négy formulaszerkezet

Az [[concepts/logika/iteletlogikai-formula]] szerkezeti rekurziójának megfelelően minden formula a következő négy típus egyikébe tartozik:

- $\neg A$ — **negációs formula**
- $(A \wedge B)$ — **konjunkciós formula**
- $(A \vee B)$ — **diszjunkciós formula**
- $(A \supset B)$ — **implikációs formula**

ahol $A$ és $B$ tetszőleges formulák.

**Példák:** $\neg(X \wedge (\neg Z \supset X))$ negációs formula; $(X \wedge (Y \wedge \neg Z))$ konjunkciós; $(\neg X \vee (X \wedge Y))$ diszjunkciós; $((X \wedge \neg Y) \supset (X \vee Y))$ implikációs.

### Közvetlen részformula

1. Prímformulának (ítéletváltozónak) nincs közvetlen részformulája.
2. A $\neg A$ formula közvetlen részformulája $A$.
3. Az $(A \circ B)$ formula közvetlen részformulái az $A$ (baloldali) és a $B$ (jobboldali).

**Példa.** A $(\neg(Z \supset \neg X) \vee Y)$ formula baloldali részformulája $\neg(Z \supset \neg X)$, jobboldali részformulája $Y$.

### Szerkezeti fa

Egy formulához tartozó **szerkezeti fa** olyan fa, amelynek gyökere maga a formula, minden csúcs gyerekei a csúcshoz tartozó formula közvetlen részformulái, a fa levelei pedig ítéletváltozók.

### Szintaxisfa

Egy formulához tartozó **szintaxisfa** olyan fa, amelynek gyökere a formula fő logikai összekötőjele ([[concepts/logika/logikai-osszetettseg]]), minden csúcs gyerekei a csúcshoz tartozó formula közvetlen részformuláinak fő logikai összekötőjelei, a fa levelei pedig ítéletváltozók. A szintaxisfa tehát a szerkezeti fa csúcsait a hozzájuk tartozó formulák helyett azok fő összekötőjelével címkézi.

### Alkalmazás: bezárójelezés a fa felépítéséhez

Feladat gyanánt gyakran egy zárójelek nélkül megadott formula szerkezeti fáját kell megrajzolni; ehhez első lépésben a [[concepts/logika/zarojelelhagyas]] szabályai szerint vissza kell állítani a teljes zárójelezést.

**Példa.** Az $A \wedge \neg B \supset C \supset \neg A \wedge B$ formula teljesen zárójelezve: $((A \wedge \neg B) \supset (C \supset (\neg A \wedge B)))$. Ennek szerkezeti fája a gyökértől ($((A \wedge \neg B) \supset (C \supset (\neg A \wedge B)))$) a $(A \wedge \neg B)$ és $(C \supset (\neg A \wedge B))$ közvetlen részformulákon át halad tovább a levelekig ($A$, $\neg B$, $C$, $\neg A$, $B$).

## Kapocs

- [[concepts/logika/iteletlogikai-formula]] — a négy szerkezeti típus forrása: a szerkezeti rekurzió definíciója
- [[concepts/logika/logikai-osszetettseg]] — a fő logikai összekötőjel, amely a szintaxisfa csúcsait címkézi
- [[concepts/logika/zarojelelhagyas]] — a teljes zárójelezés visszaállítása a fa felépítése előtt
- [[concepts/logika/elsorendu-formula]] — ugyanezek a szerkezeti fogalmak elsőrendű formulákra, kvantorokkal kiegészítve
