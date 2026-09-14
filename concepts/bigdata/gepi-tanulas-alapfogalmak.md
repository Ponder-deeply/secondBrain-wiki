---
tags: [concept]
sources: [BDAEM-2022-EA7.pptx]
derivation: source
updated: 2026-09-12
---

# Gépi tanulás – alapfogalmak és osztályozási feladat

A felügyelt (supervised) és felügyelet nélküli (unsupervised) tanulás
megkülönböztetése, valamint az osztályozási (classification) feladat
formális felépítése: adat, jellemzők, címkék és a betanított modell szerepe.

## Tartalom

### Felügyelt vs. felügyelet nélküli tanulás

- **Felügyelt tanulás (supervised learning)**: a tanítóadat elő-definiált
  osztályokkal (címkékkel) van ellátva — mintha egy "tanár" adná meg az
  osztályokat. A cél egy célfüggvény (target function) megtanulása, amely
  előre jelzi egy diszkrét osztályattribútum értékét (pl. jóváhagyva /
  elutasítva, magas kockázatú / alacsony kockázatú). Ezt a feladatot
  osztályozásnak (classification) vagy induktív tanulásnak (inductive
  learning) is nevezik. Tipikus algoritmusok: naiv Bayes, döntési fák
  (lásd [[concepts/bigdata/dontesi-fa]]), SVM, neurális hálók.
- **Felügyelet nélküli tanulás (unsupervised learning / clustering)**: az
  adat osztálycímkéi ismeretlenek; a feladat osztályok vagy klaszterek
  létezésének megállapítása az adatban, adatmintázatok (patterns)
  feltárása — önvezérelt (self-guided) tanulás. Tipikus algoritmusok:
  k-means, genetikus algoritmusok, egyéb klaszterezési módszerek.

A forrás emberi tanuláshoz hasonlítja a felügyelt tanulást: az ember múltbeli
tapasztalatokból tanul, a számítógépnek nincsenek "tapasztalatai", helyette
adatból tanul, amely egy alkalmazási terület múltbeli tapasztalatait
reprezentálja.

### Az osztályozási feladat felépítése

- **Adat**: rekordok (más néven példák, instanciák vagy esetek) halmaza,
  amelyeket $k$ jellemző (feature/attribútum: $A_1, A_2, \dots, A_k$) és egy
  osztálycímke ír le. Minden példa egy előre definiált osztállyal van
  megcímkézve.
- **Cél**: osztályozási modell tanulása az adatból, amely új (jövőbeli, vagy
  teszt-) esetek osztályát képes előre jelezni.
- **Jellemzők (features) és címkék (labels)**: a jellemzők (pl. tempó,
  intenzitás, műfaj) az input, a címke (pl. "tetszik" / "nem tetszik") az
  előrejelzendő kimenet.
- **Döntési felület (decision surface)**: kétdimenziós szemléltetésen (pl.
  tempó vs. intenzitás szórásdiagram) az osztályozó modell egy olyan
  felületet határoz meg, amely elválasztja egymástól az osztályokat. Ha ez a
  felület egyenessel (vagy hipersíkkal) leírható, az adat **lineárisan
  szeparálható**; ha nem, a probléma nem-lineárisan szeparálható (ilyenkor
  van szükség pl. döntési fákra, amelyek több lineáris kérdés egymás utáni
  feltevésével közelítik a döntési felületet).

### Példák a forrásból

- Fénykép-albumból egy személy felismerése (tagged photos alapján).
- Bankkártya-tranzakciók elemzése csalás (fraud) gyanús esetek jelzésére.
- Zenei ajánlás jellemzők (tempó, műfaj stb.) alapján.
- Kórházi sürgősségi osztályon 17 mért változó alapján magas kockázatú
  betegek azonosítása (intenzív osztályra sorolás priorizálása).
- Hitelkártya-igénylések elbírálása (jóváhagyva / nem jóváhagyva) az
  igénylő adatai (életkor, családi állapot, jövedelem, tartozások,
  hitelminősítés stb.) alapján.
- Diákok tanulási stílus szerinti klaszterekbe sorolása — ez felügyelet
  nélküli tanulás példája, mivel nincs előre definiált osztálycímke.

## Kapocs

- [[concepts/bigdata/dontesi-fa]] — az egyik legelterjedtebb felügyelt
  osztályozó algoritmus, amely lineáris kérdések sorozatával közelíti a
  döntési felületet
- [[concepts/bigdata/modellertekeles-keresztvalidacio]] — a betanított
  osztályozó modell kiértékelésének módszerei
- [[concepts/bigdata/adat-elokeszites-gepi-tanulashoz]] — a nyers adat
  jellemzőinek előkészítése a modell tanítása előtt
- [[concepts/bigdata/big-data]] — a Big Data feldolgozás tágabb kontextusa,
  amelyben a gépi tanulási módszerek alkalmazásra kerülnek
- [[concepts/bigdata/k-legkozelebbi-szomszed]] — lusta tanulású osztályozó
  módszer, amely szomszédság alapján dönt
- [[concepts/bigdata/logisztikus-regresszio]] — lineáris osztályozó módszer
- [[concepts/bigdata/linearis-regresszio]] — a felügyelt tanulás másik fő
  feladattípusa, az előrejelzés (regresszió) alapmódszere
