---
tags: [concept, bigdata/gepi-tanulas-osztalyozas-es-regresszio]
sources: [BDAEM-2022-EA8.pptx]
derivation: source
updated: 2026-09-12
---

# Naive Bayes

Valószínűségi osztályozó, amely a Bayes-tételt alkalmazza egy megfigyelés
(pl. egy pozitív teszteredmény, vagy egy szöveg szavai) alapján az egyes
osztályok utólagos (posterior) valószínűségének becslésére, azzal a
leegyszerűsítő (**naiv**) feltevéssel, hogy a megfigyelt jellemzők egymástól
függetlenek az osztályon belül.

## Tartalom

### Bayes-tétel

$$P(A \mid B) = \frac{P(A) \cdot P(B \mid A)}{P(B)}$$

szavakkal: **prior valószínűség** (a priori ismeret az osztályról) szorozva a
**megfigyelt bizonyítékkal** (a teszt/jellemző valószínűsége az adott osztály
mellett), osztva egy **normalizáló** taggal (a bizonyíték teljes
valószínűsége), adja a **posterior valószínűséget**.

### Levezetett példa: orvosi teszt

A forrás egy klasszikus diagnosztikai példán vezeti le a számítást:

- Prior: $P(C) = 0{,}01$ (a betegség előfordulása), tehát $P(\text{nincs } C)
  = 0{,}99$.
- Teszt megbízhatósága: $P(\text{Pos}\mid C) = 0{,}9$,
  $P(\text{Neg}\mid \text{nincs } C) = 0{,}9$, tehát $P(\text{Pos}\mid
  \text{nincs } C) = 0{,}1$.
- Együttes valószínűségek: $P(C, \text{Pos}) = P(C)\cdot P(\text{Pos}\mid C) =
  0{,}01 \cdot 0{,}9 = 0{,}009$; $P(\text{nincs } C, \text{Pos}) = 0{,}99
  \cdot 0{,}1 = 0{,}099$.
- Normalizáló: $P(\text{Pos}) = P(C,\text{Pos}) + P(\text{nincs }
  C,\text{Pos}) = 0{,}108$.
- Posterior: $P(C \mid \text{Pos}) = 0{,}009 / 0{,}108 \approx 0{,}08$;
  $P(\text{nincs } C \mid \text{Pos}) \approx 0{,}92$.

A tanulság: még egy 90%-os pontosságú teszt pozitív eredménye esetén is csak
kb. 8% az esély a tényleges betegségre, mert a betegség priorja (1%) nagyon
alacsony — ez a **bázisarány-torzítás** (base rate) tankönyvi illusztrációja.

### Bayes-tétel osztályozásra: szöveges példa

A forrás egy szövegosztályozási példán mutatja be, hogyan válik a Bayes-tétel
osztályozóvá: két személy (Bob, Jen) egyenlő priorral ($P(\text{Bob}) =
P(\text{Jen}) = 0{,}5$), és mindegyikükhöz tartozik egy szóhasználati
valószínűség-eloszlás (pl. mennyi eséllyel mondanák az „LOVE”, „LIFE”, „DEAL”
szavakat). Egy megfigyelt szósorozat (pl. „LIFE DEAL”) esetén a **naiv**
feltevés — hogy az egyes szavak előfordulása egymástól függetlenül,
szorzatszabállyal kombinálható — teszi lehetővé az egyes beszélők utólagos
valószínűségének becslését:

$$P(\text{Bob} \mid \text{„LIFE DEAL”}) = \frac{P(\text{Bob}) \cdot
P(\text{„LIFE DEAL”} \mid \text{Bob})}{P(\text{„LIFE DEAL”})}$$

### Miért „naiv”?

A modell csak az egyes szavak (jellemzők) előfordulását veszi figyelembe, a
szavak sorrendjét és a szöveg hosszát **nem** — ez az egyszerűsítő, ténylegesen
hibás függetlenségi feltevés adja a „naiv” jelzőt.

### `sklearn` implementáció

A `scikit-learn` több Naive Bayes-változatot kínál; a forrás a
**Gaussian Naive Bayes**-t (`sklearn.naive_bayes.GaussianNB`) említi, amely
folytonos jellemzőkre normális eloszlást feltételez osztályonként.

### Szöveges bemenet előkészítése

Szöveges adaton (pl. a Bob/Jen példa) a Naive Bayes alkalmazásának
előfeltétele, hogy a szöveget numerikus jellemzővektorrá alakítsuk — ezt a
lépést a [[concepts/bigdata/szoveg-reprezentacio]] lap tárgyalja részletesen.

## Kapocs

- [[concepts/bigdata/svm]] — másik, a forrásban közvetlenül ezt megelőzően
  tárgyalt osztályozó módszer
- [[concepts/bigdata/szoveg-reprezentacio]] — a szöveges bemenet
  jellemzővektorrá alakítása (bag-of-words, TF-IDF), amelyre a szöveges Naive
  Bayes-osztályozás épül
