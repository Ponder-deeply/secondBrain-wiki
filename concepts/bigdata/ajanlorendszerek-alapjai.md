---
tags: [concept]
sources: [BDAEM-2022-EA11.pdf]
derivation: source
updated: 2026-09-12
---

# Ajánlórendszerek alapjai

Ajánlórendszerek (recommender systems) olyan személyre szabott,
webalapú alkalmazások, amelyek a felhasználóknak olyan tartalmakról adnak
személyre szabott javaslatokat, amelyek iránt feltehetően érdeklődnek.

## Tartalom

### Motiváció: a felfedezés kora

A forrás Chris Andersont („The Long Tail”) idézi: „elhagyjuk az információ
korát, és belépünk az ajánlás korába” — a keresés (amikor tudjuk, mit
keresünk) helyét egyre inkább a felfedezés veszi át (amikor a rendszer talál
meg számunkra valami olyat, amiről nem is tudtuk, hogy keressük). Az internetes
üzletek sikere ma jelentős részben a személyre szabott felhasználói élmény
nyújtásának képességén múlik.

### Az ajánlások értéke (gyakorlati adatok)

A forrás konkrét, gyakran idézett üzleti számokat sorol fel az ajánlórendszerek
hatásának illusztrálására:

- Netflix: a megnézett filmek kétharmada ajánlásból származik.
- Google News: az ajánlások 38%-kal több kattintást generálnak.
- Amazon: az értékesítés 35%-a ajánlásokból ered.
- Choicestream: a felhasználók 28%-a több zenét vásárolna, ha megtalálná,
  amit szeret.

### A bemenet forrásai

Az ajánlórendszer bemenete többféle jel lehet:

- **Explicit értékelés** — numerikus (pl. 5 vagy 3 fokozatú) skálán, vagy
  bináris (like/dislike).
- **Implicit információ** — pl. ki jelölte meg/hivatkozott az elemre, hányszor
  nézték meg, hány darabot adtak el belőle, mennyi ideig olvasták az oldalt.
- **Elem leírások/jellemzők** (item features).
- **Felhasználói profilok/preferenciák**.

### A javaslattétel folyamata: offline és online komponens

A forrás egy architekturális ábrán mutatja be a folyamatot: az **offline**
részben a tanulási folyamat (learning process) a felhasználók visszajelzéseiből
(feedback) és az elemek (items) jellemzőiből modellt vagy klasztereket épít; az
**online** részben a döntési folyamat (decision process) ezt a modellt —
kontextussal (context) kiegészítve — ajánlott elemekké (recommended items)
alakítja. Ez a szétválasztás praktikus okból fontos: a számításigényes
modellépítés előre, kötegelve történhet, míg a tényleges ajánlás valós időben,
olcsón számolható ki.

### Két fő megközelítés: tartalomalapú és kollaboratív szűrés

A bemenetek aggregálásának két alapvető módszere:

- **Tartalomalapú szűrés** (content-based filtering) — az ajánlás az elem
  leírásán/jellemzőin, valamint a célfelhasználó saját profiljának vagy múltbeli
  viselkedésének elemzésén alapul; kizárólag az adott felhasználó adatait
  használja.
- **Kollaboratív szűrés** (collaborative filtering) — a hasonló ízlésű
  felhasználók értékeléseit veszi figyelembe, azzal a feltevéssel, hogy akik a
  múltban hasonló érdeklődést mutattak, a jövőben is hasonlót fognak. Ezt a
  forrás a legrészletesebben tárgyalja; ld.
  [[concepts/bigdata/felhasznalo-alapu-kollaborativ-szures]] és
  [[concepts/bigdata/elem-alapu-kollaborativ-szures]].

### Kollaboratív szűrés taxonómiája

A forrás a kollaboratív szűrésen belül két nagy családot különböztet meg:

- **Memóriaalapú (memory-based)** módszerek — közvetlenül az értékeléseket
  használják fel a felhasználók vagy elemek közötti hasonlóság kiszámítására
  (ez a rendszer „memóriája”), és ezt a hasonlóságot használják fel az
  ajánláshoz. Ide tartozik a szomszédság-alapú (neighborhood) módszercsalád:
  felhasználó-alapú és elem-alapú szűrés.
- **Modellalapú (model-based)** módszerek — az értékelésekből egy modellt
  tanulnak (pl. mátrixfaktorizáció, valószínűségi módszerek, más gépi tanulási
  módszerek), és ezt a modellt alkalmazzák az előrejelzésre. Ide tartozik a
  dimenziócsökkentésen alapuló mátrixfaktorizáció; ld.
  [[concepts/bigdata/matrixfaktorizacio-ajanlorendszerekben]].

## Kapocs

- [[concepts/bigdata/felhasznalo-alapu-kollaborativ-szures]] — memóriaalapú
  kollaboratív szűrés felhasználói szomszédság alapján
- [[concepts/bigdata/elem-alapu-kollaborativ-szures]] — memóriaalapú
  kollaboratív szűrés elemek hasonlósága alapján
- [[concepts/bigdata/matrixfaktorizacio-ajanlorendszerekben]] — modellalapú,
  dimenziócsökkentésen alapuló kollaboratív szűrés
- [[concepts/bigdata/gepi-tanulas-alapfogalmak]] — a kollaboratív szűrés
  modellalapú ága gépi tanulási módszerekre épül
