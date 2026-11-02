---
tags: [concept]
sources: [Laki_Lecture_6.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-09-25
---

# Ütközésmentes és korlátozott versenyes MAC-protokollok

Az ütközések rontják a teljesítményt (különösen hosszú kábel és rövid keret esetén), és a CSMA/CD nem mindenhol alkalmazható. Az **ütközésmentes** protokollok (bittérkép, bináris visszaszámlálás) egy rövid versengési szakaszban eldöntik, ki küldhet, így adatkeret sosem ütközik. A **korlátozott versenyes** protokollok (adaptív fabejárás) kis terhelésnél versengenek, nagy terhelésnél ütközésmentesen működnek.

## Tartalom

### Feltevések

$N$ állomás van, 0-tól $N-1$-ig egyértelműen sorszámozva; réselt időmodellt feltételezünk.

### Alapvető bittérkép protokoll (helyfoglalásos megoldás)

- Az ütköztetési (versengési) periódus **$N$ időrés**.
- Ha az $i$-edik állomás küldeni szeretne, az **$i$-edik versengési időrésben egy 1-es bitet** küld (adatszórással).
- A versengési időszak végére minden állomás ismeri a küldőket; a küldés a **sorszámok szerinti sorrendben** történik, majd új versengési periódus jön.

Példa 8 állomással: ha az 1., 3. és 7. résben van 1-es, utána az 1., 3., 7. állomás adatkerete következik; a következő körben (1., 5. bit) az 1. és 5. állomás küld.

Hátrány: az állomások számával a versengési periódus hossza is nő (kis terhelésnél is $N$ rés a rezsi).

### Bináris visszaszámlálás protokoll

- Minden állomás **azonos hosszú bináris azonosítóval** rendelkezik.
- A forgalmazni kívánó állomás a címét bitenként elküldi, a **legnagyobb helyi értékű bittel kezdve**. Az azonos pozíciójú bitek **logikai VAGY** kapcsolatba lépnek (ütközéskor az 1 „győz”).
- Ha egy állomás 0-t küld, de 1-et hall vissza, **feladja** a küldési szándékát, mert van nála nagyobb azonosítójú küldő.

Példa: A (0011), B (0110), C (1010), D (1011) versenyez. 1. bit: A és B 0-t küld, 1-et hall → kiesnek. 2. bit: C és D is 0 → marad mindkettő. 3. bit: mindkettő 1. 4. bit: C 0-t küld, 1-et hall → kiesik. **D küldhet.** A versengés $\log_2 N$ bitidő.

**Következmény:** a magasabb címmel rendelkező állomások prioritása magasabb.

**Mok és Ward módosítása:** virtuális állomáscímek használata; minden sikeres átvitel után ciklikusan permutáljuk az állomások címét, így a prioritás körbejár (fairség).

### Korlátozott versenyes protokollok

Cél a kétféle protokoll jó tulajdonságainak ötvözése: **kis terhelésnél versenyhelyzetes technika** (kis késleltetés), **nagy terhelésnél ütközésmentes technika** (jó csatornakihasználás).

**Szimmetrikus protokollok:** adott résben $k$ állomás verseng, mindegyik $p$ valószínűséggel ad. A csatorna megszerzésének valószínűsége:
$$P = k\,p\,(1-p)^{k-1},$$
amely $p = 1/k$ mellett maximális:
$$P_{\max} = \left(\frac{k-1}{k}\right)^{k-1}.$$
Ez $k=1$-re 1, majd gyorsan $1/e \approx 0{,}37$ felé esik. Tehát a csatorna megszerzésének esélye a **versenyhelyzetek számának csökkentésével** javítható — erre épít a fabejárás.

### Adaptív fabejárási protokoll

Történeti háttér: 1943 — Dorfman katonák szifiliszes fertőzöttségét vizsgálta csoportos teszteléssel; 1979 — Capetanakis bináris fa-reprezentációja a számítógépes változattal.

Az állomások egy bináris fa levelei (pl. A–H, a csomópontok 1-től számozva).

**Működés:**
- A 0-adik időrésben mindenki küldhet (a gyökérhez tartozó rés).
- Ha ütközés történik, megkezdődik a fa **mélységi bejárása**: a rések a fa csomópontjaihoz vannak rendelve; egy csomópont résében csak az alatta lévő állomások küldhetnek.
- Ütközéskor rekurzívan a bal, majd a jobb gyerekcsomópontnál folytatódik a keresés.
- Ha egy rés kihasználatlan marad, vagy pontosan egy állomás küld, az adott csomópont keresése befejeződik.

**Példa:** küldők B, C, D, F, G. 0. rés (gyökér): ütközés. 1. rés (A–D): ütközés. 2. rés (A–B): csak B → siker. 3. rés (C–D): ütközés. 4. rés: C, 5. rés: D. 6. rés (E–H): ütközés. 7. rés (E–F): F. 8. rés (G–H): G.

**Következmény:** minél nagyobb a terhelés, annál mélyebben érdemes kezdeni a keresést (a gyökérben úgyis ütközés lenne).

**Vizsgaszempont:** a bináris visszaszámlálás lejátszása adott címekre, a bittérkép rezsijének és a fabejárás réssorrendjének meghatározása.

## Kapocs

- [[concepts/telekom/kozeghozzaferes-alapjai]] — a MAC-protokollok osztályozása
- [[concepts/telekom/csma-cd]] — a versenyalapú alternatíva
- [[concepts/telekom/aloha]] — a versenyes protokollok teljesítménykorlátja
