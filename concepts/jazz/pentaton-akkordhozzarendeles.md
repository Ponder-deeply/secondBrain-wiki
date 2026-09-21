---
tags: [concept]
sources: ["The Jazz Piano Book - PDF Room.pdf"]
references: ["Levine: The Jazz Theory Book (pentaton fejezet)", "Bergonzi: Inside Improvisation Vol. 2 — Pentatonics"]
derivation: source
updated: 2026-09-21
---

# Pentaton–akkord hozzárendelés

A pentaton hozzárendelés a [[concepts/jazz/chord-scale-theory|chord-scale-theory]] pentatonos változata: minden akkordtípushoz azokat a pentatonokat keressük, amelyek hangkészlete a chord-scale részhalmaza. Az alaphang megválasztása határozza meg, milyen tension-kombináció szól — ugyanaz a pentaton-alak más fokról indítva más színt ad.

## Tartalom

### A módszer

1. Az akkordhoz tartozó chord-scale felírása.
2. Az avoid note-ok kizárása (dúron és dominánson a 4, locrianon a b9).
3. Annak megkeresése, mely alaphangokról indított dúr (vagy moll, vagy [[concepts/jazz/modositott-pentatonok|módosított]]) pentaton öt hangja fér bele a maradékba.

Mivel a [[concepts/jazz/pentaton-skalak|pentaton]] a dúr skála félhang nélküli magja, egy diatonikus hangkészletbe mindig **pontosan három** dúr pentaton fér bele: a hangnem I., IV. és V. fokáról indítva. (C dúr hangkészletében: C, F és G dúr pentaton — a párhuzamos mollokkal A, D és E moll pentaton.) Egy akkordon ezek közül az avoid note-ot tartalmazót kell elhagyni.
<!-- src: The Jazz Piano Book - PDF Room.pdf, ch. 15, p. 127 -->

Levine ugyanezt fordítva is megfogalmazza: a hangnem avoid note-jait (Cmaj7-en F, G7-en C) kivéve a dúr skálából éppen az V. fokú pentaton hangjai maradnak — a **V pentaton a dúr skála avoid note nélküli formája**, ezért ez az, amelyik a hangnem mindhárom diatonikus fő akkordján (a ii-en, az V-en és a I-en egyaránt) avoid note nélkül szól.
<!-- src: The Jazz Piano Book - PDF Room.pdf, ch. 15, p. 133 -->

### Táblázat (C, D, G alaphangú akkordokon)

A fokszámok az akkord alaphangjához képest értendők.

| Akkord | Pentaton | Hangok | Fokok | Szín |
|---|---|---|---|---|
| **Cmaj7** | C dúr | C D E G A | 1 9 3 5 13 | alap, inside |
| | G dúr | G A B D E | 5 13 7 9 3 | maj7-tel, világosabb |
| | D dúr | D E F♯ A B | 9 3 ♯11 13 7 | lydian |
| **Dm7** | D moll | D F G A C | 1 b3 11 5 b7 | alap |
| | A moll | A C D E G | 5 b7 1 9 11 | 9-cel |
| | E moll | E G A B D | 9 11 5 13 1 | dorian (13) |
| **G7** | G dúr | G A B D E | 1 9 3 5 13 | mixolydian |
| | G domináns | G A B D F | 1 9 3 5 b7 | arpeggio-szerű |
| | D moll 6 | D F G A B | 5 b7 1 9 3 | biztonságos, avoid nélkül |
| **G7sus4** | F dúr (= D moll) | F G A C D | b7 1 9 11 5 | sus alap |
| | C dúr | C D E G A | 11 5 13 1 9 | sus13 |
| **G7♯11** | A dúr b6 | A B C♯ E F | 9 3 ♯11 13 b7 | lydian dominant |
| **G7alt** | Db dúr (= Bb moll) | Db Eb F Ab Bb | b5 b13 b7 b9 ♯9 | alterált, terc nélkül |
| | Eb dúr b6 | Eb F G Bb B | b13 b7 1 ♯9 3 | alterált, terccel |
| **Cm(maj7)** | F dúr | F G A C D | 11 5 13 1 9 | melodikus moll |
| | C moll 6 | C Eb F G A | 1 b3 11 5 13 | alap |
| | G dúr b6 | G A B D Eb | 5 13 7 9 b3 | a maj7-et is hozza |
| **Bm7b5** | D moll 6 | D F G A B | b3 b5 b13 b7 1 | locrian és locrian ♮2 |
| | B moll b5 | B D E F A | 1 b3 11 b5 b7 | alaphangról |

Kiemelendő a **G dúr pentaton Cmaj7-en** (a 4-et elkerüli, a maj7-et hozza), a **Db dúr pentaton G7alt-on** (a tritonusz-helyettes alaphangjáról indított dúr pentaton — az alterált skála részhalmaza, alaphang és terc nélkül; lásd [[concepts/jazz/tritone-substitution|tritone-substitution]]) és a **D dúr pentaton Cmaj7-en** (a lydian ♯11 egyetlen idegen hang nélkül). Levine ez utóbbit a hangnem **II. fokú pentatonjának** nevezi: a dúr skála 2. fokára épített dúr pentaton a I. fokú akkordon mindig lydian színt ad, mert a #11-et hordozza.
<!-- src: The Jazz Piano Book - PDF Room.pdf, ch. 15, p. 133 -->

Hasonlóan Levine-nél a **Cm(maj7)-en szereplő F dúr pentaton** (a táblázatban 11 5 13 1 9) a melodikus moll hangkészletben az egyetlen természetesen előforduló pentaton — a IV. fokra épített dúr pentaton, amely a moll-tonikán a szeptim és a nónusz felé nyit.
<!-- src: The Jazz Piano Book - PDF Room.pdf, ch. 15, p. 133 -->

### Ahol nem működik

- **Diminished és whole tone akkordokon** (7b9 half-whole skálával, 7♯5 whole tone-nal) nincs illeszkedő pentaton — a szimmetrikus skálák szerkezete kizárja, lásd [[concepts/jazz/pentaton-skalak|pentaton-skalak]]. Itt a triádos [[concepts/jazz/szuperimponalas|szuperimponalas]] a megfelelő eszköz.
- **Maj7 akkordon a moll pentaton az alaphangról** (C moll pentaton Cmaj7-en) nem hozzárendelés, hanem blues-ütköztetés — tudatos színként legitim, de a táblázat logikáján kívül esik. Lásd [[concepts/jazz/blues-scale|blues-scale]].

### ii–V–I pentatonokkal

A hozzárendelés akkordonként végigvihető egy kadencián. Egy jól szóló, kis mozgású lánc C-dúr ii–V–I-re:

| Dm7 | G7alt | Cmaj7 |
|---|---|---|
| F dúr pentaton | Db dúr pentaton | G dúr pentaton |
| b3 11 5 b7 1 | b5 b13 b7 b9 ♯9 | 5 13 7 9 3 |

Az alaphangok (F → Db → G) nem a basszust követik, hanem a pentatonok közti **félhangos kapcsolódást** biztosítják: az F dúr pentaton C-je félhanggal lép a Db-re, a Db dúr pentaton Ab-je félhanggal a G-re. Ez a lánc a [[concepts/jazz/pentaton-cellak|pentaton-cellak]] lapon négyhangos cellákra bontva is szerepel.

Az egyszerűbb, egyetlen pentatonos megoldás (C dúr pentaton mindhárom akkordon) G7-en a C miatt sus-színt ad — ez nem hiba, de a domináns funkciót elmossa, ugyanúgy, ahogy a [[concepts/jazz/blues-scale|blues-scale]] korlátai között is szerepel.

Levine egy még egyszerűbb megoldást is leír: mivel a **G dúr pentaton** (az V. fok) egyik fő akkordon sem tartalmaz avoid note-ot, önmagában végigjátszható a teljes Dm7–G7–Cmaj7 kadencián — ez az az eset, amikor a ii–V–I-et egyetlen pentatonnal lehet lefedni, és pontosan ezt a logikát viszi tovább az azonos fokú pentaton más hangnemváltásokon is (pl. Coltrane "Giant Steps"-jének három hangnemén, ahol hangnemenként egyetlen V pentaton fedi le a ii–V–I-t vagy V–I-et).
<!-- src: The Jazz Piano Book - PDF Room.pdf, ch. 15, p. 128 -->

## Kapocs

- [[concepts/jazz/chord-scale-theory]] — a hozzárendelés alapja: chord-scale és avoid note
- [[concepts/jazz/pentaton-skalak]] — a pentaton szerkezete, miért fér három egy hangkészletbe
- [[concepts/jazz/modositott-pentatonok]] — a melodikus moll és alterált akkordok pentatonjai
- [[concepts/jazz/alteraciok]] — a G7alt sorok tension-jeinek besorolása
- [[concepts/jazz/tritone-substitution]] — a Db dúr pentaton G7alt-on
- [[concepts/jazz/ii-v-i-durban]] — a kadencia, amelyen a lánc végigvihető
- [[concepts/jazz/pentaton-cellak]] — a hozzárendelés dallamépítő egységekre bontva
