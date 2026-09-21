---
tags: [concept]
sources: ["The Jazz Piano Book - PDF Room.pdf"]
derivation: source
updated: 2026-09-21
---

# Szimmetrikus skálák

A szimmetrikus skálák intervallumszerkezete egy ismétlődő mintából áll, ezért transzponálva önmagukba mennek át. Két ilyen szerepel érdemben a jazzben: a diminished (nyolcfokú) és a whole tone (hatfokú).

<!-- src: The Jazz Piano Book - PDF Room.pdf, ch. 9 (Diminished / Whole-tone scale harmony), p. 76-84 -->

## Transzpozíciós szimmetria

Egy skála intervallumsorozata felírható félhanglépések listájaként, amelyek összege 12. Ha ez a lista periodikus $p$ félhangonként, akkor a skála $p$ félhanggal transzponálva ugyanazt a hangkészletet adja, és összesen

$$N = \frac{12}{12/p} = p$$

különböző transzponált hangkészlet létezik.

| Skála | Intervallumminta | Periódus | Különböző készletek |
|---|---|---|---|
| diminished | $(2,1)$ ismételve 4-szer | 3 félhang | 3 |
| whole tone | $(2)$ ismételve 6-szor | 2 félhang | 2 |
| dúr (összehasonlításul) | $(2,2,1,2,2,2,1)$ | nincs | 12 |

Ennek gyakorlati következménye: a diminished skálából mindössze három, a whole tone-ból mindössze kettő létezik. Ugyanaz a fogás sok akkordon jó lesz — ez a szimmetrikus skálák legnagyobb kényelme és egyben legnagyobb csapdája, mert könnyen mechanikussá válik.

## Diminished: két üzemmód

Ugyanaz a nyolcfokú hangkészlet két néven fut aszerint, hogy hol kezdjük.

### Half-whole (fél-egész)

C-ről: **C Db Eb E F♯ G A Bb**. Minta: 1-2-1-2-1-2-1-2.

Dominánsakkordon használjuk. C7 fölött a fokok:

| Skálahang | C | Db | Eb | E | F♯ | G | A | Bb |
|---|---|---|---|---|---|---|---|---|
| Fok | 1 | b9 | ♯9 | 3 | ♯11 | 5 | 13 | b7 |

Tehát: **b9, ♯9, ♯11, ♮13** — plusz tiszta kvint. Ez a „diminished dominant" hangzás. Megkülönböztető jegye az altered skálához képest, hogy megtartja a tiszta kvintet és a natural 13-at.

Tipikus jelölése: C7b9. Szimmetria miatt ugyanez a skála szolgálja az Eb7b9, Gb7b9 és A7b9 akkordokat is — a négy kis tercre lévő domináns közös.

### Whole-half (egész-fél)

C-ről: **C D Eb F Gb Ab A B**. Minta: 2-1-2-1-2-1-2-1.

Szűkített akkordon (dim7) használjuk. Cdim7 hangjai (C Eb Gb A) a skála páratlan fokai; a köztük lévő négy hang (D F Ab B) mind **nagy szekunddal** egy akkordhang fölött, tehát mind available tension. A dim7 az egyetlen akkord, amelynek minden nem-akkordhangja tension, avoid note nélkül.

Ez a skála a [[concepts/jazz/diminished-passing-chords|diminished-passing-chords]] természetes hangkészlete.

Megjegyzés: a half-whole és a whole-half ugyanaz a három hangkészlet, csak más kiindulóponttal. C half-whole = Db whole-half.

Gyakorlati következmény: mivel egy G7b9 és a hozzá tartozó Fº (F dim7) ugyanabból a nyolchangú skálából származik, a dim7 akkord gyakran egyszerűen a b9-es domináns helyettesítője kromatikus basszusmenet kedvéért — Duke Ellington „Sophisticated Lady" hídjában a G#º ugyanaz, mint az E7b9 az alaphang nélkül. Van kivétel is: „irreguláris" dim7, amely nem a következő akkord dominánsának helyettese, hanem önálló átmenő akkord (pl. Jobim „Wave" második üteme) — ilyenkor a szimmetrikus olvasat nem old fel semmit, csak színez.

## Whole tone

C-ről: **C D E F♯ G♯ Bb**. Csupa nagy szekund; nincs benne tiszta kvint és nincs benne kis szekund.

C7 fölött a fokok:

| Skálahang | C | D | E | F♯ | G♯ | Bb |
|---|---|---|---|---|---|---|
| Fok | 1 | 9 | 3 | ♯11 | b13 (♯5) | b7 |

Tehát: **♮9, ♯11, b13**, tiszta kvint és 13 nélkül. Akkordja C7♯5 vagy C7+.

Karaktere lebegő, iránytalan — mert nincs benne fél hang, nincs vezetőhang sem, tehát a skálának magának nincs gravitációs központja. Emiatt jól szól ott, ahol a domináns feszültségét inkább elbizonytalanítani, mint fokozni akarjuk, illetve rövid, felfelé futó színfoltként.

Csak két whole tone skála van; a C-ből és a Db-ből indított kettő együtt kiadja a teljes kromatikát.

## Dominánsskála-választás

| Skála | 9 | 11 | 13 | 5 | Karakter |
|---|---|---|---|---|---|
| mixolydian | ♮9 | avoid | ♮13 | ♮5 | semleges, diatonikus |
| lydian dominant | ♮9 | ♯11 | ♮13 | ♮5 | lebegő, nem oldódó |
| half-whole dim | b9 ♯9 | ♯11 | ♮13 | ♮5 | feszes, de megtartja az 5-öt |
| whole tone | ♮9 | ♯11 | b13 | nincs | iránytalan |
| altered | b9 ♯9 | ♯11 | b13 | nincs | maximálisan feszes |

## Zongorás gyakorlat

A szimmetria miatt a szimmetrikus skálák fogásai kis tercenként (diminished) vagy nagy szekundonként (whole tone) ismétlődnek. Egy megtanult sejtet elég transzponálva mozgatni — ez gyorsan játszható anyagot ad, de a hallgató is hamar felismeri a mintát. Ellenszere a ritmikus tagolás variálása és az irányváltás, lásd [[concepts/jazz/ritmikus-eltolas|ritmikus-eltolas]].

## Kapocs

- [[concepts/jazz/chord-scale-theory]] — a keret
- [[concepts/jazz/alteraciok]] — a b9/♯9/♯11/b13 tensionök
- [[concepts/jazz/melodic-minor-modusai]] — az altered mint versengő választás
- [[concepts/jazz/diminished-passing-chords]] — a whole-half skála harmóniai terepe
- [[concepts/jazz/harmonic-major-modusai]] — a másik b9+♮13 megoldás
- [[concepts/jazz/side-slipping]] — a szimmetria improvizációs kihasználása
