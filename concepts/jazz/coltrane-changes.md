---
tags: [concept]
sources: []
derivation: unsourced
updated: 2026-08-05
---

# Coltrane changes

A nagyterc-ciklus mint harmóniai elv: az oktávot három egyenlő, nagyterc-távolságú tonális központra osztjuk, és mindegyik központot a saját dominánsával vezetjük be. A terminust gyakran John Coltrane nevéhez kötik. Absztrakt szinten nem akkordmenet, hanem szimmetrikus tonális séma, ami többféle konkrét harmóniai kitöltést enged.

## A szimmetria

A hagyományos jazzharmónia a **kvintkört** járja: a tonális központok kvinttávolságra követik egymást, ami tizenkét lépésben zárja a kört, és minden lépésnél erős funkciós vonzást ad.

A nagyterc-ciklus a **kis tercek** helyett a nagy tercekre épít: három nagy terc = oktáv. A tizenkét hang négy ilyen, egyenként háromelemű csoportra bomlik:

| Csoport | Központok |
|---|---|
| 1 | C – E – Ab |
| 2 | Db – F – A |
| 3 | D – Gb – Bb |
| 4 | Eb – G – B |

Egy Coltrane-ciklus egy ilyen hármas bejárása, tetszőleges irányban.

## Az alapséma

Jelöljük a három központot T1, T2, T3-mal, ahol T2 = T1 + nagy terc (vagy lefelé kis szext), T3 = T2 + nagy terc. Minden központ elé kerül a saját V7-je:

```
T1maj7 | V7/T2 | T2maj7 | V7/T3 | T3maj7 | V7/T1 | T1maj7 …
```

A ciklus önmagába zár: három maj7 és három domináns, hat akkord, és újrakezdődik.

**Kiírt példa, T1 = C:**

| Akkord | Szerep |
|---|---|
| Cmaj7 | T1 |
| Eb7 | V7/T2 |
| Abmaj7 | T2 |
| B7 | V7/T3 |
| Emaj7 | T3 |
| G7 | V7/T1 |
| Cmaj7 | vissza T1-re |

(Itt lefelé nagyterc-irányban haladunk: C → Ab → E → C.)

Figyeljük meg a dominánsokat: Eb7, B7, G7 — ezek maguk is nagyterc-távolságra állnak egymástól, tehát a ciklus két, egymáshoz képest eltolt bővített hármas vázán mozog. A maj7-ek alaphangjai (C, Ab, E) egy bővített hármast adnak, a dominánsoké (Eb, B, G) egy másikat.

## Kiterjesztés related ii-vel

Minden domináns elé beszúrható a saját ii foka, ekkor a séma ii–V–I modulok láncává sűrűsödik:

```
T1maj7 | iim7/T2  V7/T2 | T2maj7 | iim7/T3  V7/T3 | T3maj7 | iim7/T1  V7/T1 | T1maj7
```

C-vel: Cmaj7 | Bbm7 Eb7 | Abmaj7 | F♯m7 B7 | Emaj7 | Dm7 G7 | Cmaj7.

Ez már ütemenként két akkordot jelent, gyors tempóban rendkívül sűrű.

## Ráillesztés meglévő ii–V-re

A séma legfontosabb alkalmazása reharmonizációs eszközként: egy szokásos, két ütemes ii–V–I helyére nagyterc-ciklust teszünk, hogy ugyanoda érkezzünk, de három tonális központot érintve.

Kiinduló helyzet C-dúrban, két ütem ii–V, majd egy ütem I:

```
| Dm7   G7 | Cmaj7 |
```

Coltrane-behelyettesítés (a cél ugyanaz a Cmaj7):

```
| Dm7  Eb7 | Abmaj7  B7 | Emaj7  G7 | Cmaj7 |
```

Mi történt:

- A kiinduló Dm7 megmarad kapaszkodónak.
- A G7 helyére Eb7 kerül, ami az Ab (= C – nagy terc) központ dominánsa.
- Innen a séma végigfut a három központon, és a G7 az utolsó lépésben visszavezet C-re.

A behelyettesítés feltétele, hogy legyen elég hely (általában két-négy ütem), és hogy a dallam megférjen. Mivel három hangnemet érintünk, a téma eredeti dallamhangjai a köztes akkordokon gyakran extension-ökké vagy alterációkká válnak — ez része a hatásnak, de ellenőrizni kell, hogy ne keletkezzen elviselhetetlen ütközés.

Ugyanez fordítva is működik: egy nagyterc-ciklus **kiegyszerűsíthető** a hozzá tartozó egyszerű ii–V–I-re, ha visszafogottabb kíséretet akarunk.

## Miért nehéz improvizálni rajta

- **Nincs közös hangkészlet.** A három maj7 (C, Ab, E) hangkészlete alig fed át; nincs egyetlen skála, amivel a ciklus végigjátszható. A klasszikus jazzimprovizáció „egy hangnem alá rendelem a menetet" stratégiája itt nem működik.
- **Nincs funkciós lejtés.** A kvintkör lépéseit a fül előre hallja; a nagyterc-lépés nem. Minden központ egyenrangú, egyik sem hierarchikusan fölérendelt — nincs igazi tonika.
- **Tempó és sűrűség.** Ütemenként két akkord, gyakran gyors tempóban. Nincs idő skálát „kikeresni".
- **Előre kell hallani.** Mivel nincs vonzás, a szólistának fejből kell tudnia, hol lesz a következő központ.

Szokásos gyakorlási stratégiák:

1. **Modulok memorizálása.** Nem menetet, hanem három ii–V–I-t gyakorolunk, mindig ugyanabban a nagyterc-viszonyban, minden hangnemben.
2. **Rövid, akkordvázas motívumok.** Minden központra ugyanaz a rövid figura (pl. 1–2–3–5 vagy 3–5–7–9), ami transzponálva ismétlődik — a szimmetria így hallhatóvá válik. Lásd [[concepts/jazz/digital-pattern|digital-pattern]].
3. **Guide tone-vezetés.** A maj7 3-a és 7-e, illetve a domináns 3-a és 7-e között minimális lépéssel közlekedünk, lásd [[concepts/jazz/guide-tone-line|guide-tone-line]].
4. **A bővített váz tudatosítása.** Ha a fül megjegyzi a C–Ab–E bővített hármast, a ciklus egyetlen objektumként hallható, nem hat különálló akkordként.

## Elhelyezés a rendszerben

Chord-scale nézőpontból nincs újdonság: minden maj7 fölött ionian (vagy lydian), minden domináns fölött mixolydian vagy altered. A nehézség nem a skálakészletben, hanem a **gyorsan váltó tonális központokban** van.

A nagyterc-ciklus a szimmetrikus harmóniai gondolkodás egyik példája — rokona a szűkített (kis terces) ciklusnak és az egészhangú felületnek, lásd [[concepts/jazz/szimmetrikus-skalak|szimmetrikus-skalak]]. Russell Lydian Chromatic Concept-je más kiindulásból, a lydian tonikagravitáció felől ír le hasonló távoli kapcsolatokat; ez különálló elméleti keret, nem keverendő a Berklee chord-scale szótárral.

## Kapocs

- [[concepts/jazz/extended-dominant]] — a kvintkörös alternatíva ugyanerre a feladatra
- [[concepts/jazz/ii-v-i-durban]] — a ciklus építőköve
- [[concepts/jazz/reharmonizacio]] — a behelyettesítés mint reharm-technika
- [[concepts/jazz/szimmetrikus-skalak]] — a szimmetrikus felosztás rokon esetei
- [[concepts/jazz/digital-pattern]] — transzponált motívumok a cikluson
- [[concepts/jazz/post-bop-harmonia]] — a szimmetrikus harmónia stílusrétege
