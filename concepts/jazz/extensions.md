---
tags: [concept]
sources: ["The Jazz Piano Book - PDF Room.pdf"]
derivation: source
updated: 2026-09-21
---

# Extensions (9, 11, 13)

Az extension a tercépítkezés folytatása a szeptim fölött: 9, 11, 13. Ezek nem díszítések, hanem az akkord teljes értékű alkotórészei — a jazzhangzás színét jórészt ők adják.

<!-- src: The Jazz Piano Book - PDF Room.pdf, ch. 9 (Scale Theory), p. 59-60 -->

## Származtatás

A seventh chord fölé további terceket rakva kapjuk:

```
1 – 3 – 5 – 7 – 9 – 11 – 13
```

A 9 a 2, a 11 a 4, a 13 a 6 oktávval feljebb. A megkülönböztetés nem kozmetikai: a 9/11/13 elnevezés azt jelenti, hogy a hang a szeptimes szerkezet **fölé** kerül, míg a 2/4/6 jelölés (pl. Csus2, C6) helyettesítő hangot jelöl a hármashangzaton belül.

A 15 már az oktáv, tehát a tercépítkezés hét hangnál kimerül — pontosan egy hétfokú skálát ad ki. Ez a [[concepts/jazz/chord-scale-theory|chord-scale-theory]] kiindulópontja: az akkord és a skála ugyanannak a hangkészletnek két elrendezése.

## Melyik extension természetes melyik akkordtípuson

A kérdés mindig az: a diatonikus környezetben az adott extension fél hangra esik-e egy akkordhangtól. Ha igen, ütközik (lásd avoid note a [[concepts/jazz/chord-scale-theory|chord-scale-theory]] lapon).

| Akkordtípus | Természetes extensionök | Kerülendő | Megjegyzés |
|---|---|---|---|
| maj7 (I. fok) | 9, 13 | 11 | a 11 fél hangra van a 3-tól |
| maj7 (IV. fok, lydian) | 9, ♯11, 13 | 11 | lydian környezet, a ♯11 természetes |
| m7 (ii. fok, dorian) | 9, 11 | 13 vitatott | a 13 (natural 6) dorian szín, nem hiba |
| m7 (iii. fok, phrygian) | 11 | b9, b13 | a b9 miatt szegényes; gyakran átértelmezzük |
| m7 (vi. fok, aeolian) | 9, 11 | b13 | |
| 7 (V. fok, mixolydian) | 9, 13 | 11 | a 11 fél hangra van a 3-tól |
| 7sus4 | 9, 13 | — | itt a 4 akkordhang, nem ütközik |
| m7b5 | 11, b13 | b9 (locrian) | locrian ♮2 esetén a 9 is elérhető |
| mMaj7 | 9, 11, 13 | — | melodikus moll, minden fok használható |
| dim7 | mindegyik hang fölött nagy szekund | — | lásd [[concepts/jazz/szimmetrikus-skalak]] |

## A 11 problémája dúr akkordon

A természetes 11 (a 4. fok) fél hangra fekszik a nagy tercétől. Cmaj7-en az F és az E között kis szekund van; a 11 gyakorlatilag elnyeli a 3-at, és az akkord elveszti dúr karakterét. Ugyanez áll C7-re.

Három szokásos kezelés:

1. **Elhagyjuk.** Cmaj7 esetén a 9 és a 13 marad, a 11 avoid note.
2. **♯11-re emeljük.** Ezzel lydian (maj7 fölött) vagy lydian dominant (7 fölött) színt kapunk. A ♯11 nem ütközik a 3-mal, és nem a hangnem tonikáját sérti, hanem gazdagítja. Lásd [[concepts/jazz/dur-skala-modusai|dur-skala-modusai]] és [[concepts/jazz/melodic-minor-modusai|melodic-minor-modusai]].
3. **A 3-at hagyjuk el.** Ekkor sus4 akkordot kapunk (C7sus4): a 4 nem tension, hanem akkordhang. A sus4 domináns saját, lebegő karakterű hangzás, gyakran a domináns késleltetett feloldásaként.

Moll akkordon a 11 nem problémás: a b3-tól nagy szekundra van, tehát szabadon szólhat. Ez az egyik oka, hogy a kvartális voicingok (lásd [[concepts/jazz/kvartalis-voicing|kvartalis-voicing]]) moll akkordokon annyira természetesek.

## Extension a gyakorlatban

Zongorán ritkán szólal meg minden hang. A szokásos munkamegosztás: a bal kéz a guide tone-okat (3 és 7) hozza, a jobb kéz az extensionöket. A 9 és 13 a jobb kéz felső szólamában szólva ad a hangzásnak jazzes karaktert anélkül, hogy az akkord funkcióját elhomályosítaná. Részletek: [[concepts/jazz/rootless-voicing|rootless-voicing]] és [[concepts/jazz/guide-tone|guide-tone]].

Az alteráció (b9, ♯9, ♯11, b13) az extensionök módosított változata; azoknak külön lapja van: [[concepts/jazz/alteraciok|alteraciok]].

## Kapocs

- [[concepts/jazz/akkordepites]] — az alapszerkezet, amit az extensionök folytatnak
- [[concepts/jazz/alteraciok]] — módosított extensionök
- [[concepts/jazz/chord-scale-theory]] — available tension és avoid note keretrendszere
- [[concepts/jazz/dur-skala-modusai]] — honnan jön az egyes fokok extension-készlete
- [[concepts/jazz/rootless-voicing]] — hogyan szólaltatjuk meg őket zongorán
