---
tags: [concept, bigdata/gepi-tanulas-osztalyozas-es-regresszio]
sources: [gyak3.pdf]
derivation: inferred
updated: 2026-09-12
---

# Logisztikus regresszió

A logisztikus regresszió egy lineáris osztályozó módszer, amely a
jellemzők lineáris kombinációját a **logisztikus (sigmoid) függvényen**
keresztül egy $[0,1]$ közötti valószínűségre képezi le, amelyből egy
küszöbérték (jellemzően 0,5) alapján származik a bináris osztálycímke.

## Tartalom

### A modell

A jellemzővektor $x$ és a súlyvektor $w$ lineáris kombinációját
($z = w^Tx + b$) a sigmoid függvény torzítja $[0,1]$ tartományba:

$$\sigma(z) = \frac{1}{1 + e^{-z}}$$

Az eredmény $\sigma(z)$ az adott osztályhoz tartozás becsült
valószínűsége. A döntés a valószínűség egy küszöbértékkel (pl. 0,5) való
összevetésével születik: $\sigma(z) \ge 0{,}5$ esetén az egyik, egyébként a
másik osztályba soroljuk az esetet.

### Tanítás

A modell paramétereit ($w$, $b$) jellemzően a **log-likelihood**
maximalizálásával (vagy ezzel ekvivalensen, a keresztentrópia-hiba
minimalizálásával) illesztik a tanítóadatra, gradiens alapú optimalizáló
eljárással.

### Viszonya a lineáris regresszióhoz és a döntési felülethez

A logisztikus regresszió a [[concepts/bigdata/linearis-regresszio]]-hoz
hasonlóan lineáris kombinációból indul ki, de folytonos érték helyett
osztályvalószínűséget jelez előre — ezért **osztályozó**, nem
**előrejelző (regressziós)** módszer a szó szokásos gépi tanulási
értelmében. A döntési felülete (a $\sigma(z)=0{,}5$ szint) a jellemzőtérben
egy hipersík, tehát a logisztikus regresszió lineárisan szeparálható
esetekre alkalmas — vö.
[[concepts/bigdata/gepi-tanulas-alapfogalmak]].

## Kapocs

- [[concepts/bigdata/linearis-regresszio]] — a folytonos célváltozót
  előrejelző rokon módszer, amelyből a logisztikus regresszió a sigmoid
  transzformációval osztályozót képez
- [[concepts/bigdata/k-legkozelebbi-szomszed]] — másik, a gyakorlaton
  szintén tárgyalt osztályozó módszer
- [[concepts/bigdata/gepi-tanulas-alapfogalmak]] — a lineáris szeparálhatóság
  és a döntési felület fogalma
- [[concepts/bigdata/modellertekeles-keresztvalidacio]] — a betanított
  osztályozó kiértékelésének módszerei
