---
tags: [concept]
sources: [BDAEM-2022-EA9.pptx]
references: ["Breiman, L. (1996): Bagging predictors — a bootstrap aggregating eredeti forrása"]
derivation: source
updated: 2026-09-12
---

# Bagging (bootstrap aggregating)

A bagging homogén ensemble módszer (Breiman, 1996), amely a tanuló adat
véletlen, visszatevéses újramintavételezésével (*bootstrap resampling*)
állít elő több tanuló halmazt, majd a rájuk épített modellek döntéseit
többségi szavazással kombinálja.

## Tartalom

### Az algoritmus

Adott egy $n$ méretű tanuló adathalmaz. A bagging:

1. $m$ darab, egyenként $n$ méretű mintát készít az eredeti adatból
   **visszatevéssel** (*with replacement*) — ezek a *bootstrap minták*.
2. Mindegyik bootstrap mintán önállóan felépít egy-egy klasszifikátort.
3. A kapott $m$ modell döntéseit **többségi szavazással** (lásd
   [[concepts/bigdata/ensemble-modszerek]]) egyesíti egyetlen végső
   döntéssé.

A bagging elsősorban instabil tanulók (pl. döntési fák) hibáját csökkenti:
a hiba varianciakomponensét mérsékli azáltal, hogy a tagmodellek eltérő
mintákon, egymástól kevésbé korrelált hibákat vétenek.

### Miért ~63%-a az eredeti adatnak egy bootstrap minta tényleges lefedettsége?

Mivel a mintavétel visszatevéssel történik, egy adott rekord esélye, hogy egy
adott húzáskor kiválasztásra kerül, $1/N$. Annak valószínűsége, hogy egy
rekord az $N$ húzás egyikén sem kerül kiválasztásra:

$$\left(1 - \frac{1}{N}\right)^N \xrightarrow{N \to \infty} \frac{1}{e} \approx 0{,}368$$

Ebből következik, hogy egy rekord kiválasztásának valószínűsége legalább
egyszer az $N$ húzás során kb. $1 - 1/e \approx 0{,}632$. Emiatt egy bootstrap
minta várhatóan az eredeti adat rekordjainak mintegy **63%-át** tartalmazza
(némelyiket többször is), a maradék ~37% pedig kimarad az adott mintából —
ez utóbbi szolgálhat pl. *out-of-bag* validációra.

## Kapocs

- [[concepts/bigdata/ensemble-modszerek]] — az ensemble koncepció és a
  homogén/heterogén megkülönböztetés, amelynek a bagging egy konkrét esete
- [[concepts/bigdata/adaboost]] — a másik fő homogén ensemble technika,
  amely újramintavételezés helyett újrasúlyozással dolgozik
- [[concepts/bigdata/random-forest]] — a bagging elvét döntési fákra
  alkalmazó, jellemzők véletlenszerű részhalmazolásával kiegészített
  konkrét módszer
</content>
