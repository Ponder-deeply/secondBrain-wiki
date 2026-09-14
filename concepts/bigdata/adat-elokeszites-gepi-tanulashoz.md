---
tags: [concept]
sources: [BDAEM-2022-EA7.pptx]
derivation: source
updated: 2026-09-12
---

# Adat-előkészítés gépi tanuláshoz (preprocessing)

A nyers jellemzőadat gépi tanulási modell számára szükséges
előfeldolgozási lépései: hiányzó értékek kezelése, kategorikus változók
numerikus reprezentációja, valamint skálázás (normalizálás/standardizálás).

## Tartalom

### Hiányzó értékek (missing values)

A scikit-learn `Imputer` osztálya (régebbi API) a hiányzó értékek
pótlására szolgál. Fontos gyakorlati szabály: az imputert a
**tanítóadaton kell "betanítani"** (fit), majd a **tesztadaton ugyanazt a
betanított imputert kell alkalmazni** a predikció előtt — nem szabad a
tesztadaton külön imputálást végezni. Paraméterei:

- `strategy`: `mean` (átlag), `median` (medián), `most_frequent` (leggyakoribb
  érték),
- `axis`: `0` = oszlopok mentén, `1` = sorok mentén.

### Kategorikus változók (category variables)

- **Bináris jellemzők**: átalakíthatók 0/1 vagy -1/1 kódolásra; hiányzó
  érték esetén 0.5 (illetve a -1/1 kódolásnál 0) használható.
- **Nominális jellemzők**: több, egymástól nem rendezett érték (pl.
  `INNER_CITY`/`RURAL`/`SUBURBAN`/`TOWN`). Minden lehetséges értékhez külön
  bináris oszlopot kell létrehozni (one-hot jellegű kódolás); hiányzó érték
  esetén egy külön bináris oszlop vezethető be a hiányzás jelzésére.
- **Ordinális jellemzők**: több, de rendezett érték (pl. small/medium/large).
  Mivel van közöttük sorrend, egész számokká alakíthatók (pl. small=0,
  medium=1, large=2). Hiányzó érték esetén szélsőérték bevezethető, vagy —
  a nominális esethez hasonlóan — külön oszlop a hiányzás jelzésére.

### Skálázás (scaling)

Egyes algoritmusok megkövetelik, hogy a változók értékei egy adott
tartományba essenek, ezért a jellemzőket át kell skálázni:

- **normalizálás (Max-min normalization)**: a minimális érték 0-ra, a
  maximális érték 1-re transzformálódik,
- **standardizálás (Z-score normalization)**: az adatot nulla átlagra és
  1 szórásra transzformálja.

## Kapocs

- [[concepts/bigdata/gepi-tanulas-alapfogalmak]] — a felügyelt osztályozási
  feladat, amelynek jellemzőit (features) ez a lap előkészíti
- [[concepts/bigdata/modellertekeles-keresztvalidacio]] — a modelltanítás és
  -kiértékelés lépései, amelyeket az adat-előkészítés megelőz
