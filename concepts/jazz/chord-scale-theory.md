---
tags: [concept]
sources: []
derivation: unsourced
updated: 2026-08-05
---

# Chord-scale theory

A Berklee-féle chord-scale theory központi állítása: minden akkordhoz tartozik egy skála, amely az akkord összes hangját és az adott kontextusban elérhető tension-öket tartalmazza. Az akkord és a skála ugyanannak a hangkészletnek két elrendezése — az akkord függőlegesen, a skála vízszintesen.

## Az alapazonosság

A tercépítkezést hét hangig folytatva egy teljes hétfokú skálát kapunk:

```
1 – 3 – 5 – 7 – 9 – 11 – 13     (tercekben)
1 – 2 – 3 – 4 – 5 – 6 – 7       (lépésekben rendezve)
```

Vagyis a „melyik extension szólhat" és a „melyik skála illik" kérdés ugyanaz a kérdés. Ha tudom, hogy Cmaj7-en a 9 és a 13 elérhető, a 11 nem, akkor tudom, hogy a skála C ionian, de az F kerülendő.

Ez az elmélet ereje és korlátja is: minden akkordpillanathoz egyetlen hangkészletet rendel, ezért kiválóan alkalmas a harmónia leképezésére, de statikusabb képet ad, mint amennyire a valódi frazírozás az.

## Available tension vs. avoid note

Egy skála hangjai három csoportba esnek:

1. **Akkordhang (chord tone):** 1, 3, 5, 7. Stabil, bármikor, bármeddig szólhat.
2. **Available tension:** olyan skálahang, amely nem akkordhang, de az akkorddal együtt szólva jól hangzik. Voicingba tehető és hosszan kitartható.
3. **Avoid note:** olyan skálahang, amely az akkorddal együtt szólva ütközik. Nem tilos leütni — csak nem tartható ki, és nem tesszük voicingba.

Az „avoid" szó félrevezető: nem elkerülendő hangot jelent, hanem olyat, amelyen nem állunk meg. Átmenőhangként, gyors futamban teljesen rendben van. A [[concepts/jazz/bebop-skalak|bebop-skalak]] éppen arra ad rendszert, hogyan kezeljük a nem-akkordhangokat metrikusan.

## A fél hang szabály

**Egy skálahang akkor available tension, ha nem fekszik fél hangra egy akkordhang fölött.** (Alatta fél hangra fekvő hang megengedett — az vezetőhangként működik.)

Ellenőrzés Cmaj7-en (C ionian: C D E F G A B):

| Skálahang | Fok | Van fölötte fél hangra akkordhang? | Ítélet |
|---|---|---|---|
| D | 9 | D → E nagy szekund | available |
| F | 11 | F → E: F fél hanggal E **fölött** | **avoid** |
| A | 13 | A → B nagy szekund (B akkordhang, de A alatta) | available |

C7-en (C mixolydian) ugyanez: az F fél hangra van az E fölött → avoid, marad a 9 és a 13.

Cm7-en (C dorian: C D Eb F G A Bb): a D nagy szekundra van az Eb-től, az F nagy szekundra a G-től, az A nagy szekundra a Bb-től. Egyik sem ütközik → mindhárom tension elérhető. Ezért gazdagabb a moll akkord tensionkészlete, mint a dúré.

Kivétel a szabály alól a domináns akkord alterált tensionjei: azok szándékosan feszültek, funkciójuk épp az ütközés. Domináns akkordon a fél hang szabály nem tiltó, hanem leíró — megmondja, mennyire éles a hangzás.

## Skála levezetése akkordszimbólumból

Négylépéses eljárás:

1. **Akkordtípus** — a szimbólumból leolvasva megvan az 1, 3, 5, 7.
2. **Funkció** — mi az akkord szerepe a környezetben? Tonika, szubdomináns, domináns, átmenő?
3. **Hangnem** — melyik skálához tartozik a környezet? A diatonikus alapkészlet innen jön.
4. **Explicit tension a szimbólumban** — ha a szimbólum kiír egy tensiont (♯11, b9, alt), az felülírja a diatonikus alapértelmezést.

Példák:

| Szimbólum | Kontextus                          | Skála                                             |
| --------- | ---------------------------------- | ------------------------------------------------- |
| Dm7       | ii. fok C-dúrban                   | D dorian                                          |
| G7        | V. fok C-dúrban                    | G mixolydian                                      |
| Cmaj7     | I. fok C-dúrban                    | C ionian                                          |
| Fmaj7     | IV. fok C-dúrban                   | F lydian                                          |
| G7alt     | V. fok C-mollban                   | G altered (Ab melodikus moll)                     |
| Bm7b5     | ii. fok A-mollban                  | B locrian                                         |
| A7        | V/ii C-dúrban (secondary dominant) | A mixolydian b9 b13 (D harmonikus moll 5. módusa) |
| Bb7       | backdoor domináns C-dúrban         | Bb lydian dominant                                |

A 2. lépés a legfontosabb és a legkönnyebben elrontható. Ugyanaz az akkordszimbólum különböző funkcióban különböző skálát kap: a Cmaj7 mint I. fok ionian, mint IV. fok lydian. Erről szól a [[concepts/jazz/dur-skala-modusai|dur-skala-modusai]] lap.

## Alapértelmezett skálahozzárendelések

| Akkordtípus | Alapértelmezett skála | Alternatívák |
|---|---|---|
| maj7 | ionian | lydian (IV. fok, vagy színezés) |
| m7 | dorian | aeolian, phrygian (fokfüggő) |
| 7 | mixolydian | lydian dominant, altered, half-whole dim, whole tone |
| m7b5 | locrian | locrian ♮2 |
| dim7 | whole-half diminished | — |
| mMaj7 | melodikus moll | harmonikus moll |
| 7sus4 | mixolydian | mixolydian sus b9 (phrygian ♮6) |

## Az elmélet határai

A chord-scale theory akkordonként rendel hangkészletet, ezért nem magyaráz meg minden jó megoldást:

- A **Barry Harris**-féle sixth-diminished megközelítés nem akkordonkénti skálákban gondolkodik, hanem egy hatfokú/nyolcfokú anyaskálában, amelynek váltakozó fokain akkord és diminished átmenet ül. Ez a metrikus elhelyezésre ad erősebb választ.
- A **Russell-féle Lydian Chromatic Concept** nem az ionian, hanem a lydian skálát tekinti a tonalitás gravitációs központjának, és a hangkészleteket a lydian-tól való távolságuk szerint rendezi.
- A **klasszikus funkciós analízis** szólamvezetésben és feloldásokban gondolkodik, nem hangkészletekben; egy alterált hang nála vezetőhang, nem tension.

Ezek nem cáfolják egymást, de más szótárt használnak. Egy leíráson belül nem érdemes keverni őket.

## Kapocs

- [[concepts/jazz/akkordepites]] — az akkordtípusok, amikhez a skálát rendeljük
- [[concepts/jazz/extensions]] — a természetes tensionök akkordtípusonként
- [[concepts/jazz/alteraciok]] — a módosított tensionök
- [[concepts/jazz/dur-skala-modusai]] — a diatonikus skálakészlet
- [[concepts/jazz/melodic-minor-modusai]] — az altered és lydian dominant forrása
- [[concepts/jazz/harmonic-minor-modusai]] — a moll domináns skálája
- [[concepts/jazz/szimmetrikus-skalak]] — diminished és whole tone
- [[concepts/jazz/bebop-skalak]] — a nem-akkordhangok metrikus kezelése
- [[concepts/jazz/ii-v-i-durban]] — a hozzárendelés tipikus gyakorlóterepe
- [[concepts/jazz/pentaton-akkordhozzarendeles]] — a hozzárendelés pentatonos változata
