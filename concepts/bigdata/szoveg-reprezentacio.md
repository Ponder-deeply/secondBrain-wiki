---
tags: [concept]
sources: [BDAEM-2022-EA8.pptx]
derivation: source
updated: 2026-09-12
---

# Szövegreprezentáció osztályozáshoz

Lépések és technikák, amelyekkel szabad szöveg numerikus jellemzővektorrá
alakítható, hogy gépi tanulási osztályozók (pl. Naive Bayes) bemeneteként
szolgálhasson.

## Tartalom

### Bag of words

A legegyszerűbb reprezentáció: a dokumentumhoz tartozó szótár (dictionary)
minden szavára megszámoljuk az előfordulások számát a dokumentumban, sorrend
nélkül. Például a „Mr Day loves a nice day” mondat a `{nice, very, day, he,
she, love, dog}` szótár mellett a `[1, 0, 2, 0, 0, 1, 0]` vektorra képződik le
(a „day” kétszer, a „nice” és „love” egyszer fordul elő).

`sklearn`-ben a `sklearn.feature_extraction.text.CountVectorizer` végzi ezt a
transzformációt.

### Stopszavak eltávolítása

Egyes szavak (pl. „the”, „will”, „are”, „is”, „a”, „an”) alig hordoznak
információt — ezeket **stopszavaknak** nevezzük, és jellemzően eltávolítjuk a
szövegből a reprezentáció előállítása előtt. Pythonban az `nltk` csomag
`stopwords` listája használható erre (`from nltk.corpus import stopwords`).

### Szótövezés (stemming)

Ugyanazon szó különböző alakjait (pl. „response”, „responsiveness”,
„responsivity”, „respond”, „unresponsive”) egy **stemmer** közös tőalakra
(„respons”) redukálja, hogy a bag-of-words ne kezelje őket különálló
jellemzőként. Az `nltk` csomag `SnowballStemmer` osztálya ad erre kész
implementációt.

A forrás által javasolt feldolgozási sorrend:

1. szótövezés (stemming),
2. stopszavak eltávolítása,
3. szövegreprezentáció előállítása (bag-of-words vagy TF-IDF).

### TF-IDF

A puszta szógyakoriság (bag-of-words) nem különbözteti meg a ritka, tartalmi
szempontból informatív szavakat a gyakori, kevésbé informatívaktól. A
**TF-IDF** (term frequency – inverse document frequency) ezt korrigálja: a
szó egy adott dokumentumon belüli gyakoriságát (**TF**) megszorozza egy
súllyal, amely azt fejezi ki, hogy a szó milyen ritkán fordul elő a teljes
korpuszban (**IDF**) — így a ritka, megkülönböztető szavak nagyobb súlyt
kapnak, mint a korpuszban általánosan gyakori szavak.

`sklearn`-ben a `sklearn.feature_extraction.text.TfidfVectorizer` valósítja
meg ezt a reprezentációt.

## Kapocs

- [[concepts/bigdata/naive-bayes]] — az osztályozó, amelynek szöveges
  bemenetét ez a reprezentáció készíti elő (pl. a Bob/Jen szövegosztályozási
  példában)
