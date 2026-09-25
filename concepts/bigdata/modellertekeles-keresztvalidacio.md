---
tags: [concept, bigdata/gepi-tanulas-alapfogalmak-es-elokeszites]
sources: [BDAEM-2022-EA7.pptx]
derivation: source
updated: 2026-09-12
---

# Osztályozó modellek kiértékelése és keresztvalidáció

Egy betanított osztályozó modell minőségének mérésére használt szempontok
(pontosság, hatékonyság, robusztusság stb.) és a leggyakoribb kiértékelési
eljárás, a keresztvalidáció (cross-validation) fő változatai.

## Tartalom

### Tanítás és tesztelés két fázisa

- **Tanítás (training)**: a modell megtanulása a tanítóadatból (training
  data).
- **Tesztelés (testing)**: a modell pontosságának mérése eddig nem látott
  (unseen) tesztadaton.

### Kiértékelési szempontok

Az osztályozó módszerek összehasonlításának fő szempontjai:

- **prediktív pontosság (predictive accuracy)**,
- **hatékonyság (efficiency)** — a modell felépítésének és alkalmazásának
  ideje,
- **robusztusság (robustness)** — zaj és hiányzó értékek kezelése,
- **skálázhatóság (scalability)** — hatékonyság nagy, lemezen tárolt
  adatbázisokon,
- **interpretálhatóság (interpretability)** — mennyire érthető a modell és
  milyen belátást ad,
- **a modell kompaktsága** — pl. a fa mérete vagy a szabályok száma.

### Precision és Recall

A pontosság finomabb mérésére szolgáló további metrikák: **precision**
(pontosság — a pozitívnak jelölt esetek közül mennyi valóban pozitív) és
**recall** (fedés — a valódi pozitív esetek közül mennyit talált meg a
modell).

### Keresztvalidáció (cross-validation)

Széles körben használt stratégia a modell prediktív pontosságának
becslésére és modellkiválasztásra (pl. változók kiválasztása regresszióban,
paraméterhangolás). Alapötlete: a modellt olyan adaton kell tesztelni,
amelyet nem használtunk a becsléshez — az adatot egyszer vagy többször
szétosztjuk **tanító mintára (training sample)**, amelyen a modellt
becsüljük, és **validációs mintára (validation sample)**, amelyen a
predikciós hibát mérjük.

#### K-fold keresztvalidáció

Az adatot $k$ egymást nem átfedő, közel egyenlő méretű részmintára osztja.
Minden körben egy résszel validálunk, a többivel tanítunk, ezt $k$-szor
megismételve minden résszel egyszer validálva. Nevezetes esetek:

- $k = 2$: 2-fold keresztvalidáció,
- $k = 10$: 10-fold keresztvalidáció,
- $k = N$ (a minta mérete): **leave-one-out cross-validation (LOOCV)**.

#### További változatok

- **Monte-Carlo keresztvalidáció**: az adatot véletlenszerűen, ismétlés
  nélkül (without replacement) többször két részre (tanító és validációs)
  osztja.
- **Hold-out módszer**: egyetlen véletlenszerű felosztás tanító és
  validációs részre.

#### Modellkiválasztás keresztvalidációval

A cél a legkisebb **generalizációs hiba** (generalisation error) modell
kiválasztása: minden $k$ mintára megbecsüljük a modellt a tanítóhalmazon, és
kiszámítjuk a hibát a validációs halmazon; a generalizációs hiba becslése a
$K$ ismétlés hibáinak átlaga.

#### Gyakorlati megvalósítás (sklearn)

A forrás a scikit-learn `StratifiedKFold` és `cross_val_score` függvényeit
mutatja be a k-fold keresztvalidációs pontszám kiszámítására: a
`cross_val_score` a klasszifikátort, a jellemzőket, a címkéket és a `cv`
felosztást kapja, és minden foldra visszaadja a pontosságot, amelyből átlag
és szórás számítható.

## Kapocs

- [[concepts/bigdata/gepi-tanulas-alapfogalmak]] — a felügyelt osztályozási
  feladat, amelynek modelljeit ez a lap értékeli ki
- [[concepts/bigdata/dontesi-fa]] — egy konkrét osztályozó modell, amelynek
  kiértékelésére a keresztvalidáció is alkalmazható
- [[concepts/bigdata/adat-elokeszites-gepi-tanulashoz]] — az adat-előkészítés
  lépései, amelyek a modelltanítást (és ezáltal a kiértékelés minőségét)
  megelőzik
