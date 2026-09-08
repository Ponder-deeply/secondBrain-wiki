---
tags: [concept]
sources: []
derivation: unsourced
updated: 2026-08-05
---

# A melodikus moll módusai

A jazzben használt melodikus moll a felfelé-lefelé egyaránt azonos alakú („jazz minor"): dúr skála leszállított tercel, 1 2 b3 4 5 6 7. Hét módusa közül három a modern jazzharmónia alapkészlete: az altered, a lydian dominant és a locrian ♮2.

## A hét módus

C melodikus mollból (C D Eb F G A B) származtatva:

| Fok | Név | Alaphang | Szerkezet | Akkordtípus |
|---|---|---|---|---|
| I | melodikus moll | C | 1 2 b3 4 5 6 7 | mMaj7 |
| II | dorian b2 (phrygian ♮6) | D | 1 b2 b3 4 5 6 b7 | m7, sus4b9 |
| III | lydian augmented | Eb | 1 2 3 #4 #5 6 7 | maj7#5 |
| IV | lydian dominant | F | 1 2 3 #4 5 6 b7 | 7#11 |
| V | mixolydian b6 | G | 1 2 3 4 5 b6 b7 | 7b13 |
| VI | locrian ♮2 | A | 1 2 b3 4 b5 b6 b7 | m7b5 |
| VII | altered (super locrian) | B | 1 b2 b3 b4 b5 b6 b7 | 7alt |

Jellemző, hogy a melodikus mollban **két tritonusz** van (a dúrban csak egy), ezért a belőle képzett módusok feszültebbek és funkcionálisan mozgékonyabbak, mint a dúr módusai.

## Altered (super locrian)

A VII. módus. Szerkezete leírva a **domináns** szemszögéből (nem a módusfokok szerint):

```
1 – b9 – #9 – 3 – #11 – b13 – b7
```

A `b4` enharmonikusan a nagy terc, a `b5` a #11, a `b6` a b13. Az akkord tehát valódi domináns: van 3-ja és b7-je, de **nincs tiszta kvintje**, és minden felső extension alterált.

Levezetés: **G7alt = Ab melodikus moll**, vagyis fél hanggal az alaphang fölött indított melodikus moll. Ez a legpraktikusabb szabály zongorán.

Használat: bármely dominánson, ahol maximális feszültséget akarunk. Kötelező jellegű a moll ii-V-i V. fokán (lásd [[concepts/jazz/ii-v-i-mollban|ii-v-i-mollban]]), mert a b13 a moll tonika b3-ára old fel. Dúrban is szabadon használható stílusdöntésként.

A tritone sub kapcsolat: G7alt és Db7#11 hangkészlete azonos (mindkettő Ab melodikus moll). A [[concepts/jazz/tritone-substitution|tritone-substitution]] és az altered skála ezért ugyanannak a hangzásnak két írásmódja.

## Lydian dominant

A IV. módus. Szerkezete: 1 2 3 #4 5 6 b7 — domináns akkord tiszta kvinttel, természetes 9-cel és 13-mal, de **#11**-gyel.

Levezetés: **C7#11 = G melodikus moll**, vagyis a tiszta kvinttel indított melodikus moll. (Ekvivalens: a mixolydian #4-gyel.)

Használat:

- **Nem feloldódó domináns**, például a backdoor domináns (lásd [[concepts/jazz/backdoor-ii-v|backdoor-ii-v]]): a bVII7 C-dúrban Bb7 → Bb lydian dominant, mert a természetes 11 (Eb) ütközne a hangnemmel, a #11 (E) viszont a tonika 3-a.
- **Tritone substitution akkordja**: a helyettesítő domináns szinte mindig lydian dominant, mert a #11-je az eredeti domináns alaphangja.
- **Blues-os I7** akkordon színezésként.

Ellentétpár: ha a domináns feloldódik és feszültséget akarunk → altered. Ha nem oldódik fel, vagy sima, lebegő domináns szín kell → lydian dominant.

## Locrian ♮2

A VI. módus. Szerkezete: 1 2 b3 4 b5 b6 b7 — m7b5 akkord, de a natural 9 miatt sokkal használhatóbb, mint a sima locrian.

Levezetés: **Cm7b5 (locrian ♮2) = Eb melodikus moll**, vagyis a kis terccel indított melodikus moll.

Használat: a moll ii-V-i ii. fokán. A locrianban a b2 avoid note, ezért a fölötte képzett voicing szegényes; a locrian ♮2-vel a 9 available tension lesz, és a m7b5 akkord színesen szólal meg. Ez a modern alapértelmezés a m7b5-re; lásd [[concepts/jazz/ii-v-i-mollban|ii-v-i-mollban]].

## A többi négy módus

Ritkábbak, de nem ismeretlenek:

- **Dorian b2** — sus4b9 akkordon (phrygian karakterű, de ♮6-tal), modális-lebegő hangzáshoz.
- **Lydian augmented** — maj7#5 akkordon. Post-bop tonikaszín, lásd [[concepts/jazz/post-bop-harmonia|post-bop-harmonia]].
- **Mixolydian b6** — 7b13 akkordon, ha a b13 kell, de a natural 9 és 11 marad. Átmenet a mixolydian és az altered között.
- **Melodikus moll (I. fok)** — mMaj7 akkordon: moll tonika, ahol a nagy szeptim vezetőhangként működik.

## Gyakorlati levezetési szabályok

Egy táblázatban, dominánsra:

| Kívánt hangzás | Melodikus moll indítása |
|---|---|
| altered | b9-ről (fél hanggal az alaphang fölött) |
| lydian dominant | 5-ről (tiszta kvintről) |
| m7b5 locrian ♮2 | b3-ról |

## Kapocs

- [[concepts/jazz/chord-scale-theory]] — a keret
- [[concepts/jazz/alteraciok]] — az altered skála tensionkészlete
- [[concepts/jazz/dur-skala-modusai]] — a diatonikus alapkészlet
- [[concepts/jazz/harmonic-minor-modusai]] — a másik moll anyaskála
- [[concepts/jazz/tritone-substitution]] — az altered/lydian dominant kettősség
- [[concepts/jazz/ii-v-i-mollban]] — ahol mindhárom fő módus egyszerre előkerül
