---
tags: [concept]
sources: [gyak2.pdf]
derivation: source
updated: 2026-09-12
---

# Adattisztítás (data cleaning)

Az adattisztítás a nyers adat hibáinak és hiányosságainak feltárása és
javítása a gépi tanulási modellezés előtt: hiányzó adatok, duplikátumok,
pontatlanságok, formátumeltérések és kiugró értékek kezelése.

## Tartalom

### Az adattisztítás típusai

- **Hiányzó adat kezelése** — lásd alább.
- **Duplikátumok eltávolítása** — ugyanazon rekord többszöri előfordulásának
  kiszűrése az adathalmazból.
- **Pontatlanságok javítása** — pl. elírások (typo) korrekciója szöveges
  mezőkben.
- **Standardizálás** — eltérő formátumú, de azonos jelentésű értékek egységes
  alakra hozása (pl. dátumformátumok egységesítése).
- **Kiugró értékek (outlierek) kezelése** — a többi adattól szélsőségesen
  eltérő értékek felismerése és kezelése.

### Hiányzó adatok kezelése

Két fő stratégia áll szemben egymással: a hiányzó érték **pótlása**
(imputálás), vagy az érintett rekord/oszlop **eldobása**.

**Imputálás (imputing)** — a hiányzó érték kitöltése egy becsült értékkel:

- **ffill** (forward fill) — a hiányzó érték az előző (nem hiányzó) értékkel
  töltődik ki,
- **bfill** (backward fill) — a hiányzó érték a következő (nem hiányzó)
  értékkel töltődik ki,
- **interpolálás (interpolate)** — a hiányzó érték a szomszédos (nem
  hiányzó) értékek alapján, interpolációval becsülhető.

**Eldobás (dropping)**:

- azoknak a **soroknak** az eldobása, amelyekben hiányzó adat van,
- azoknak az **oszlopoknak** az eldobása, amelyekben túl sok az adat
  hiányzik (az oszlop így már nem hordoz elég információt).

A választás a hiányzás mértékétől és mintázatától függ: kevés, szórványos
hiányzás esetén az imputálás, sok vagy rendszeres hiányzás esetén inkább az
eldobás (oszlop- vagy sorszinten) az ésszerű választás.

## Kapocs

- [[concepts/bigdata/adat-elokeszites-gepi-tanulashoz]] — a modelltanítás
  előtti előkészítés további lépései (kategorikus változók kódolása,
  skálázás), amelyek az adattisztítást követik
- [[concepts/bigdata/gepi-tanulas-alapfogalmak]] — a gépi tanulási feladat,
  amelynek adatát az adattisztítás előkészíti
