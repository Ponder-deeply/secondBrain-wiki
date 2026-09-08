---
tags: [concept]
sources: [10.md]
derivation: source
updated: 2026-04-09
---

# HORNSAT

A HORNSAT az a kielégíthetőségi probléma, amelynél a formula Horn-formula. Polinom időben eldönthető, így P-beli — szemben a SAT és 3SAT NP-teljességével.

## Definíció

**Horn-formula:** olyan KNF, amelynek minden klóza **legfeljebb egy pozitív** (nem negált) literált tartalmaz.

**Példa:**
$$(\neg x_1 \lor x_3) \land (\neg x_1 \lor \neg x_3 \lor x_4) \land (\neg x_2 \lor \neg x_4 \lor \neg x_6)$$

$$\text{HORNSAT} = \{ \langle \varphi \rangle \mid \varphi \text{ kielégíthető Horn-formula} \}$$

## Tétel: HORNSAT $\in$ P

(A bizonyítást a forrás nem részletezi.)

A szokásos algoritmus: mohó egységpropagáció — ha egy klóz egyetlen literálból áll (egységklóz), az egyértelműen igaz kell legyen; ezzel más klózok egyszerűsödnek. Ez addig folytatható, amíg ellentmondás vagy kielégítő értékadás adódik.

## Kapocs

- [[concepts/bvszam/ksat-es-3sat]] — 3SAT NP-teljes; összehasonlítás
- [[concepts/bvszam/2sat]] — 2SAT szintén P-beli, implikációs gráffal
- [[concepts/bvszam/bonyolultsagelmeleti-osztalyok]] — P és NP osztályok
