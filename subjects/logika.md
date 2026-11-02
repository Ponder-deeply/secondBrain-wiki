---
tags: [subject]
sources: [Logika-targyleiras.pdf, iteletlogika.pdf, "Elsőrendű_logika_ bevezetés.pdf", Elsőrendű_logika_szemantika.pdf, "Szintaktikus következmény.pdf", "Természetes levezetés.pdf", Szekventkalkulus.pdf, Tablókalkulus.pdf, Rezolúció_I.pdf, Rezolúció_II.pdf, LTL_CTL.pdf, Toth-Gabriella-Logika-mintazh-2019.pdf, MintaZH1.pdf, Ítéletlogika_alapjai.pdf, Elsőrendű_logika_alapjai.pdf, Tablokalkulus_1_2_rész.pdf, Szabo-Ivan-Elsorendu-logika-egyetemi-jegyzet.pdf, logika-canvas-tanmenet.md, logika_logika-canvas-tanmenet.md]
references: [Pásztorné Varga Katalin – Várterész Magda, A matematikai logika alkalmazásszemléletű tárgyalása (PANEM, 2003), ISBN 9635453647]
derivation: source
math: 70
updated: 2026-10-21
---

# Logika és számításelmélet (logika)

A tárgy a logikát két, egymást kiegészítő úton járja végig: a **szemantikus** tárgyaláson, ahol egy formula igazságértékét interpretációk fölött vizsgáljuk, és a **szintaktikus** tárgyaláson, ahol formális kalkulusok levezetési szabályaival dolgozunk. A két út az eldöntésprobléma két megközelítése; a tárgy gerince annak megmutatása, hogy a szintaktikus kalkulusok helyesek és teljesek — vagyis pontosan azt vezetik le, amit a szemantika igazzá tesz.

## Tárgykör

A tantárgyleírás szerint: a logika szemantikus és szintaktikus tárgyalása; nulla- és elsőrendű logika szintaxisa és szemantikája; szintaktikus és szemantikus következményfogalom; eldöntésprobléma; szintaktikus kalkulusok — szekventkalkulus, tablómódszer, rezolúció nulla- és elsőrendben; rezolúciós stratégiák; a temporális logika alapjai (Kripke-struktúra, LTL, CTL).

A tárgy 5 kredites, kötelezően választható, kollokviummal és gyakorlati jeggyel zárul.

Az anyag két nagy felezővonala:

1. **Ítéletlogika → elsőrendű logika** — az állítás belső szerkezetének megjelenítése (egyedek, relációk, kvantorok).
2. **Szemantika → szintaxis** — az interpretációk kimerítő vizsgálata algoritmikusan reménytelen (már megszámlálhatóan végtelen univerzum fölött kontinuum sok interpretáló struktúra van), ezért a következményfogalmat véges, mechanikus levezetési szabályokra kell visszavezetni.

## ZH1

A **kanonikus** ZH1 mintazh a `MintaZH1.pdf` (nem a Tóth Gabriella-féle 2019-es minta, az másik, nem kanonikus forrás). Szerkezet:

- **Elméleti rész** (rövid kérdések): hasonló stílusú kérdések lesznek, de sok más is kérdezhető; a mintakérdések csak példák.
- **Gyakorlati rész**: a valódi ZH csaknem azonos a mintazh-val (igazságtábla és formalizálás, tabló ítéletlogikában és elsőrendben, elsőrendű értéktábla).
- **3. feladat** (Wason-feladat): csak a feladattípust jelzi, a konkrét példány más lesz.

Feladatonkénti térkép és megoldásvázlat: [[concepts/logika/mintazh1-feladattipusok]]; a 3. feladat: [[concepts/logika/wason-kivalasztasi-feladat]].

## Vizsga

Forrás: `Toth-Gabriella-Logika-mintazh-2019.pdf` — mintazárthelyi (fejléce szerint a 2017.12.12-i dolgozat; 80 pont, a teljesítéshez 32 pont kell).

A számonkérés a kalkulusok *gyakorlati* alkalmazását kéri, nem a tételek felmondását: ugyanazt az eldöntésproblémát több módszerrel is végigviteti.

| # | Vizsgakérdés / tétel | Lap(ok) |
|---|---|---|
| 1 | Közös igazságtábla egy ítéletlogikai eldöntésproblémához (1.a) | [[concepts/logika/igazsagtabla]], [[concepts/logika/szemantikus-kovetkezmeny]] |
| 2 | Hogyan igazolja a közös igazságtábla a következtetés helyességét? (1.b) | [[concepts/logika/kovetkeztetesforma]], [[concepts/logika/szemantikus-kovetkezmeny]] |
| 3 | A következtetés helyessége tablómódszerrel, jelölt vagy jelöletlen tablóval (2.) | [[concepts/logika/analitikus-tablo]], [[concepts/logika/jelolt-formula-es-formulatipusok]] |
| 4 | Az eldöntésproblémát kifejező szekvent megalapozása G- vagy C-kalkulusban (3.) | [[concepts/logika/szekvent]], [[concepts/logika/szekventkalkulus]], [[concepts/logika/szekvent-levezetesfa]] |
| 5 | Ítéletkalkulusbeli levezetés lépéseinek felcímkézése (axiómaséma, feltétel, modus ponens) (4.) | [[concepts/logika/axiomasemak-iteletkalkulus]], [[concepts/logika/bizonyitaselmeleti-levezetes]] |
| 6 | Elsőrendű formula prímkomponensei (2.1.a) | [[concepts/logika/elsorendu-formula]], [[concepts/logika/szemantikus-tulajdonsagok]] |
| 7 | Értéktábla fejléce és első sorai adott interpretációban (2.1.b–c) | [[concepts/logika/szemantikus-tulajdonsagok]], [[concepts/logika/elsorendu-interpretacio]], [[concepts/logika/valtozokiertekeles]] |
| 8 | Változóidegen elsőrendű klózhalmaz előállítása (2.2.a) | [[concepts/logika/prenex-forma]], [[concepts/logika/skolem-normalforma]], [[concepts/logika/elsorendu-kloz]] |
| 9 | Herbrand univerzum és egy Herbrand bázis (2.2.b) | [[concepts/logika/herbrand-univerzum]] |
| 10 | Szemantikus fa felírása és lezárása a bázison (2.2.c) | [[concepts/logika/iteletlogikai-szemantikus-fa]], [[concepts/logika/herbrand-tetel]] |
| 11 | Logikai igazság igazolása elsőrendű rezolúcióval, legáltalánosabb illesztővel (2.2.d) | [[concepts/logika/elsorendu-rezolucio]], [[concepts/logika/legaltalanosabb-illeszto-helyettesites]] |

### Követelmények (2026/27/1, Canvas)

- **Pontszerzés**: összesen 100 pont — 20 pont beadandókból, 80 pont két ZH-ból.
- **Beadandók**: 10 db, Canvas-ban, határidőkkel; összesen 20 pont, a tárgy
  teljesítéséhez legalább 10 pont kell.
- **ZH-k** (2 db, egyenként 40 pont): mindkettő két részből áll — rövid
  kérdésekből álló beugró (legalább 60% kell, az eredménybe nem számít), és
  számolós, gondolkodós feladatok (legalább 20/40 pont).
- **Pótlás**: mindkét ZH pótolható vagy javítható a félév végén; ha a beugró
  nem sikerült, de az összpontszám legalább 26 pont (65%), elég a beugrót
  újraírni. Csak a számolós rész nem javítható.
- **Jegyhatárok**: 50 pont – 2, 65 – 3, 75 – 4, 85 – 5.
- **Tankönyv**: Pásztorné Varga Katalin – Várterész Magda, *A matematikai
  logika alkalmazásszemléletű tárgyalása* (szabadon elérhető a Tankönyvtárban).
- **Gyakorlati anyagok**: ítéletlogikai formalizálás, igazságtábla, szemantikus
  következmény ([[concepts/logika/iteletlogikai-formalizalas]]); elsőrendű
  formalizálás ([[concepts/logika/elsorendu-formalizalas]]); tablókalkulus
  ([[concepts/logika/analitikus-tablo]], [[concepts/logika/elsorendu-tablo]]);
  mintazh: `MintaZH1.pdf`. Az előadás hétfőnként van; tematikája a fenti
  fogalomlapok sorrendjét követi (ítéletlogika, elsőrendű logika, tablókalkulus,
  szintaktikus következmény, természetes levezetés, szekventkalkulus,
  rezolúció, LTL/CTL).

## Fogalomlapok

### ZH1
- ZH1 mintazh feladattípusai és megoldásvázlatok — [[concepts/logika/mintazh1-feladattipusok]]
- Wason-féle kiválasztási feladat — [[concepts/logika/wason-kivalasztasi-feladat]]

### Ítéletlogika — szintaxis
- Az ábécé, $V_0$: ítéletváltozók, összekötőjelek, elválasztójelek — [[concepts/logika/iteletlogika-abece]]
- Ítéletlogikai formula, $L_0$: szerkezeti rekurzió, literál, elemi konjunkció/diszjunkció — [[concepts/logika/iteletlogikai-formula]]
- Zárójelelhagyás és műveleti precedencia — [[concepts/logika/zarojelelhagyas]]
- Részformula, szerkezeti fa, szintaxisfa — [[concepts/logika/formulaszerkezet]]
- Logikai összetettség — [[concepts/logika/logikai-osszetettseg]]

### Ítéletlogika — szemantika
- Interpretáció és helyettesítési érték — [[concepts/logika/iteletlogikai-interpretacio]]
- Igazságtábla — [[concepts/logika/igazsagtabla]]
- Kielégíthetőség, tautológia, szemantikus következmény — [[concepts/logika/szemantikus-kovetkezmeny]]
- Következtetésforma és helyessége — [[concepts/logika/kovetkeztetesforma]]
- Ítéletlogikai formalizálás, a betörős feladat — [[concepts/logika/iteletlogikai-formalizalas]]

### Elsőrendű logika — nyelv és szintaxis
- Matematikai struktúra: $\langle U, R, M, K\rangle$ — [[concepts/logika/matematikai-struktura]]
- Nulladrendű és elsőrendű állítás — [[concepts/logika/nulladrendu-es-elsorendu-allitas]]
- Leíró nyelv és szignatúra — [[concepts/logika/leiro-nyelv-es-szignatura]]
- Term — [[concepts/logika/term]]
- Elsőrendű formula — [[concepts/logika/elsorendu-formula]]
- Szabad és kötött változó, nyitott és zárt formula — [[concepts/logika/szabad-es-kotott-valtozo]]
- Változóiban tiszta (kiigazított) alak — [[concepts/logika/valtozoiban-tiszta-alak]]
- Elsőrendű formalizálás: egy- és többfajtájú nyelv — [[concepts/logika/elsorendu-formalizalas]]

### Elsőrendű logika — szemantika
- Elsőrendű interpretáció — [[concepts/logika/elsorendu-interpretacio]]
- Változókiértékelés — [[concepts/logika/valtozokiertekeles]]
- A term szemantikája — [[concepts/logika/term-szemantika]]
- Szemantikus tulajdonságok: kielégíthetőség, érvényesség, következmény — [[concepts/logika/szemantikus-tulajdonsagok]]
- Elsőrendű szemantikus fa — [[concepts/logika/elsorendu-szemantikus-fa]]
- Helyettesítési algoritmus és lemma — [[concepts/logika/helyettesitesi-algoritmus]]

### Bizonyításelmélet (Hilbert-típusú kalkulus)
- Axiómasémák az ítéletkalkulusban, modus ponens — [[concepts/logika/axiomasemak-iteletkalkulus]]
- Bizonyításelméleti levezetés, $\vdash_0$ — [[concepts/logika/bizonyitaselmeleti-levezetes]]
- Dedukciós tétel, a levezetés tulajdonságai, Kalmár-lemma — [[concepts/logika/dedukcios-tetel]]
- A predikátumkalkulus axiómasémái — [[concepts/logika/predikatumkalkulus-axiomasemak]]
- Helyesség, teljesség, Gödel teljességi tétele — [[concepts/logika/bizonyitaselmelet-helyesseg-teljesseg]]

### Gentzen stílusú kalkulusok
- A kalkuluscsalád, előre- és visszakövetkeztetés — [[concepts/logika/gentzen-stilusu-kalkulusok]]
- Természetes levezetés (természetes technika) — [[concepts/logika/termeszetes-levezetes]]
- Szekvent — [[concepts/logika/szekvent]]
- Szekventkalkulus: G- és C-kalkulus — [[concepts/logika/szekventkalkulus]]
- Szekvent levezetésfa és bizonyíthatóság — [[concepts/logika/szekvent-levezetesfa]]

### Tablókalkulus
- Jelölt formula, $\alpha$/$\beta$ típusok — [[concepts/logika/jelolt-formula-es-formulatipusok]]
- Analitikus tabló (ítéletlogika) — [[concepts/logika/analitikus-tablo]]
- Hintikka halmaz és Hintikka lemma — [[concepts/logika/hintikka-halmaz]]
- Elsőrendű analitikus tabló — [[concepts/logika/elsorendu-tablo]]

### Rezolúció — ítéletlogika
- Klóz és klózhalmaz, KNF/KKNF, DNF/KDNF — [[concepts/logika/kloz-es-klozhalmaz]]
- Ítéletlogikai szemantikus fa, klózok illesztése — [[concepts/logika/iteletlogikai-szemantikus-fa]]
- Rezolúciós kalkulus, levezetési stratégiák — [[concepts/logika/rezolucios-kalkulus]]
- Horn klóz és Horn logika — [[concepts/logika/horn-kloz-es-horn-logika]]

### Rezolúció — elsőrendű logika
- Prenex forma — [[concepts/logika/prenex-forma]]
- Skolem normálforma — [[concepts/logika/skolem-normalforma]]
- Elsőrendű klóz — [[concepts/logika/elsorendu-kloz]]
- Herbrand univerzum, bázis, interpretáció — [[concepts/logika/herbrand-univerzum]]
- Herbrand tételek, Davis–Putnam, alaprezolúció — [[concepts/logika/herbrand-tetel]]
- Legáltalánosabb illesztő helyettesítés (unifikáció) — [[concepts/logika/legaltalanosabb-illeszto-helyettesites]]
- Elsőrendű rezolúció: faktor, bináris rezolvens — [[concepts/logika/elsorendu-rezolucio]]

### Temporális logika
- Kripke-struktúra és utak — [[concepts/logika/kripke-struktura]]
- LTL (Linear Temporal Logic) — [[concepts/logika/ltl]]
- CTL (Computation Tree Logic) — [[concepts/logika/ctl]]
- LTL és CTL összehasonlítása — [[concepts/logika/ltl-ctl-osszehasonlitas]]

## Kapocs

- [[subjects/bvszam]] — a Bevezetés a számításelméletbe tárgy logikai előismereti fejezetei ugyanezt az anyagot tömörebben, $\to$ jelöléssel tárgyalják
- [[concepts/bvszam/itelet-kalkulus]] — ítéletkalkulus: szintaxis, szemantika, kielégíthetőség, KNF
- [[concepts/bvszam/elsorendu-logika]] — elsőrendű logika: term, formula, interpretációs struktúra
- [[concepts/bvszam/elsorendu-logika-eldonthetetlenseg]] — az elsőrendű logika eldönthetetlensége
- [[concepts/bvszam/hornsat]] — a HORNSAT probléma bonyolultsági oldala
