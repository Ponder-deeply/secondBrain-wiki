---
tags: [concept]
sources: []
derivation: unsourced
updated: 2026-08-05
---

# A dúr skála módusai

A dúr skála hét hangjának mindegyikéről indítható egy-egy módus. Ugyanaz a hangkészlet, más alaphang — és ezzel más intervallumszerkezet, más akkordtípus, más karakter.

## A hét módus

C-dúr hangkészletéből (C D E F G A B) származtatva:

| Fok | Módus      | Alaphang | Szerkezet az alaphangtól | Akkordtípus |
| --- | ---------- | -------- | ------------------------ | ----------- |
| I   | ionian     | C        | 1 2 3 4 5 6 7            | maj7        |
| II  | dorian     | D        | 1 2 b3 4 5 6 b7          | m7          |
| III | phrygian   | E        | 1 b2 b3 4 5 b6 b7        | m7          |
| IV  | lydian     | F        | 1 2 3 ♯4 5 6 7           | maj7        |
| V   | mixolydian | G        | 1 2 3 4 5 6 b7           | 7           |
| VI  | aeolian    | A        | 1 2 b3 4 5 b6 b7         | m7          |
| VII | locrian    | B        | 1 b2 b3 4 b5 b6 b7       | m7b5        |

Fényesség szerint rendezve (a legtöbb kereszttől a legtöbb b-ig): lydian (4) – ionian (1) – mixolydian (5) – dorian (2) – aeolian (6) – phrygian (3) – locrian (7). Minden lépés egyetlen hangot süllyeszt fél hanggal. Ez a rendezés a [[concepts/jazz/side-slipping|side-slipping]] és a modális színkeverés gondolkodásához hasznos.

## Jellemző hang (characteristic note)

A módus karakterét az a hang adja, amelyben a szomszédos, ugyanolyan minőségű módustól eltér. Ez az a hang, amit ki kell emelni, hogy a módus hallható legyen.

| Módus      | Jellemző hang  | Mihez képest                       |
| ---------- | -------------- | ---------------------------------- |
| ionian     | 4 (mint avoid) | a lydian ♯4-jével szemben          |
| dorian     | ♮6             | az aeolian b6-jával szemben        |
| phrygian   | b2             | az aeolian ♮2-jével szemben        |
| lydian     | ♯4             | az ionian ♮4-ével szemben          |
| mixolydian | b7             | az ionian ♮7-ével szemben          |
| aeolian    | b6             | a dorian ♮6-jával szemben          |
| locrian    | b5             | a többi mollszerű módussal szemben |

Modális kontextusban (lásd [[concepts/jazz/modalis-jazz-harmonia|modalis-jazz-harmonia]]) a jellemző hang a lényeg: a dorian nem attól dorian, hogy m7 akkord van alatta, hanem attól, hogy a ♮6 hallható.

## Avoid note-ok

A [[concepts/jazz/chord-scale-theory|chord-scale-theory]] fél hang szabálya alapján:

| Módus | Avoid note | Miért |
|---|---|---|
| ionian | 4 | fél hangra a 3 fölött |
| dorian | (6 gyengén) | a 6 a b7 alatt van, nem ütközik; általában available |
| phrygian | b2, b6 | b2 az 1 fölött, b6 az 5 fölött |
| lydian | — | nincs; ezért „szabad" hangzású |
| mixolydian | 4 | fél hangra a 3 fölött |
| aeolian | b6 | fél hangra az 5 fölött |
| locrian | b2 | fél hangra az 1 fölött |

A lydian az egyetlen avoid note nélküli módus — ez a Russell-féle Lydian Chromatic Concept egyik kiindulópontja, amely emiatt tekinti a lydiant a tonalitás alapjának, nem az ioniant. A Berklee-keret ettől függetlenül az ioniant használja I. fokú alapértelmezésként.

## Melyik fokon melyik módus

A gyakorlati hozzárendelés funkcionális harmóniában:

- **I. fok maj7** → ionian; a 4 kerülendő
- **ii. fok m7** → dorian
- **iii. fok m7** → phrygian; a b9 miatt szegényes, gyakran I. fok helyettesként kezeljük és ionian marad a hangkészlet
- **IV. fok maj7** → lydian; ez a leggyakoribb pont, ahol a ♯11 természetesen adódik
- **V. fok 7** → mixolydian; a 4 kerülendő
- **vi. fok m7** → aeolian
- **vii. fok m7b5** → locrian; funkcionálisan gyakran inkább V7b9 helyettes

Fontos: a hozzárendelés a **funkciótól** függ, nem az akkordtípustól. Egy maj7 lehet ionian vagy lydian aszerint, hogy I. vagy IV. fok; egy m7 lehet dorian, phrygian vagy aeolian aszerint, hogy hányadik fok.

## Korlátok

A dúr módusok csak a diatonikus akkordokat fedik le. Amint alterált domináns, secondary dominant vagy modal interchange akkord jön, más anyaskálához kell nyúlni:

- alterált domináns → [[concepts/jazz/melodic-minor-modusai|melodic-minor-modusai]]
- moll ii-V domináns → [[concepts/jazz/harmonic-minor-modusai|harmonic-minor-modusai]]
- b9-es domináns feszes feloldással → [[concepts/jazz/szimmetrikus-skalak|szimmetrikus-skalak]]

## Kapocs

- [[concepts/jazz/chord-scale-theory]] — a keret, amelybe a módusok illeszkednek
- [[concepts/jazz/extensions]] — a módusokból következő tensionkészlet
- [[concepts/jazz/melodic-minor-modusai]] — a következő anyaskála
- [[concepts/jazz/harmonic-minor-modusai]] — a moll harmónia módusai
- [[concepts/jazz/modal-interchange]] — párhuzamos módusokból kölcsönzött akkordok
- [[concepts/jazz/modalis-jazz-harmonia]] — a módusok mint önálló tonális központ
