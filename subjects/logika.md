---
tags: [subject]
sources: [Logika-targyleiras.pdf, iteletlogika.pdf, "Elsőrendű_logika_ bevezetés.pdf", Elsőrendű_logika_szemantika.pdf, "Szintaktikus következmény.pdf", "Természetes levezetés.pdf", Szekventkalkulus.pdf, Tablókalkulus.pdf, Rezolúció_I.pdf, Rezolúció_II.pdf, LTL_CTL.pdf, Toth-Gabriella-Logika-mintazh-2019.pdf]
references: [Pásztorné Varga Katalin – Várterész Magda, A matematikai logika alkalmazásszemléletű tárgyalása (PANEM, 2003), ISBN 9635453647]
derivation: source
updated: 2026-09-08
---

# Logika és számításelmélet (logika)

A tárgy a logikát két, egymást kiegészítő úton járja végig: a **szemantikus** tárgyaláson, ahol egy formula igazságértékét interpretációk fölött vizsgáljuk, és a **szintaktikus** tárgyaláson, ahol formális kalkulusok levezetési szabályaival dolgozunk. A két út az eldöntésprobléma két megközelítése; a tárgy gerince annak megmutatása, hogy a szintaktikus kalkulusok helyesek és teljesek — vagyis pontosan azt vezetik le, amit a szemantika igazzá tesz.

## Tárgykör

A tantárgyleírás szerint: a logika szemantikus és szintaktikus tárgyalása; nulla- és elsőrendű logika szintaxisa és szemantikája; szintaktikus és szemantikus következményfogalom; eldöntésprobléma; szintaktikus kalkulusok — szekventkalkulus, tablómódszer, rezolúció nulla- és elsőrendben; rezolúciós stratégiák; a temporális logika alapjai (Kripke-struktúra, LTL, CTL).

A tárgy 5 kredites, kötelezően választható, kollokviummal és gyakorlati jeggyel zárul.

Az anyag két nagy felezővonala:

1. **Ítéletlogika → elsőrendű logika** — az állítás belső szerkezetének megjelenítése (egyedek, relációk, kvantorok).
2. **Szemantika → szintaxis** — az interpretációk kimerítő vizsgálata algoritmikusan reménytelen (már megszámlálhatóan végtelen univerzum fölött kontinuum sok interpretáló struktúra van), ezért a következményfogalmat véges, mechanikus levezetési szabályokra kell visszavezetni.

## Fogalomlapok

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

### Elsőrendű logika — nyelv és szintaxis
- Matematikai struktúra: $\langle U, R, M, K\rangle$ — [[concepts/logika/matematikai-struktura]]
- Nulladrendű és elsőrendű állítás — [[concepts/logika/nulladrendu-es-elsorendu-allitas]]
- Leíró nyelv és szignatúra — [[concepts/logika/leiro-nyelv-es-szignatura]]
- Term — [[concepts/logika/term]]
- Elsőrendű formula — [[concepts/logika/elsorendu-formula]]
- Szabad és kötött változó, nyitott és zárt formula — [[concepts/logika/szabad-es-kotott-valtozo]]

### Elsőrendű logika — szemantika
- Elsőrendű interpretáció — [[concepts/logika/elsorendu-interpretacio]]
- Változókiértékelés — [[concepts/logika/valtozokiertekeles]]
- A term szemantikája — [[concepts/logika/term-szemantika]]
- Szemantikus tulajdonságok: kielégíthetőség, érvényesség, következmény — [[concepts/logika/szemantikus-tulajdonsagok]]
- Elsőrendű szemantikus fa — [[concepts/logika/elsorendu-szemantikus-fa]]

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

## Vizsga

A mintazárthelyi (2019) alapján a számonkérés a kalkulusok *gyakorlati* alkalmazását kéri, nem a tételek felmondását. Egy tipikus feladatsor ugyanazt az eldöntésproblémát több módszerrel is végigviteti:

- ítéletlogikában: közös igazságtábla, tablómódszer, Gentzen-szekvent (G vagy C kalkulus, a választást jelezni kell), majd egy ítéletkalkulusbeli levezetés lépéseinek felcímkézése;
- elsőrendben: prímkomponensek és értéktábla adott interpretáció mellett, majd egy formula logikai igazságának igazolása rezolúcióval — változóidegen klózhalmaz, Herbrand univerzum és bázis, zárt szemantikus fa, végül elsőrendű rezolúció a legáltalánosabb illesztési algoritmussal.

## Kapocs

- [[subjects/bvszam]] — a Bevezetés a számításelméletbe tárgy logikai előismereti fejezetei ugyanezt az anyagot tömörebben, $\to$ jelöléssel tárgyalják
- [[concepts/bvszam/itelet-kalkulus]] — ítéletkalkulus: szintaxis, szemantika, kielégíthetőség, KNF
- [[concepts/bvszam/elsorendu-logika]] — elsőrendű logika: term, formula, interpretációs struktúra
- [[concepts/bvszam/elsorendu-logika-eldonthetetlenseg]] — az elsőrendű logika eldönthetetlensége
- [[concepts/bvszam/hornsat]] — a HORNSAT probléma bonyolultsági oldala
