---
tags: [subject]
sources: [01.bevezetes.pdf, 02.modellek.pdf, 03.lokalker.pdf, 04.visszalep.pdf, 05-06.grafker.pdf, 07.jatek.pdf, 08.evolucio.pdf, 09.kovetkeztetes.pdf, 10.bizonytalansag.pdf, 11.gepi_tanulas.pdf, 12.neuronhalok.pdf]
derivation: source
math: 35
updated: 2026-10-12
---

# Mesterséges intelligencia (mesint)

A tárgy (Gregorics Tibor előadásdiái, ELTE) az MI klasszikus, keresés-központú felfogását követi: a feladatot **modellezéssel** útkeresési problémává alakítjuk, majd általános **keresőrendszerekkel** oldjuk meg (lokális keresés, visszalépés, gráfkeresés, játékkeresés, evolúciós algoritmusok), és ugyanezt a keretet használja a rezolúciós következtetésre is. A záró egységek a bizonytalanságkezelés (Bayes-hálók), a gépi tanulás és a neuronhálók.

## Tárgykör

1. **Modellezés** — állapottér, probléma-redukció, probléma-dekompozíció; a reprezentációs gráf és az útkeresés.
2. **Keresőrendszerek** — vezérlési stratégiák (általános, modellfüggő, heurisztikus): lokális keresések, visszalépéses keresés, általános gráfkereső ($A$, $A^*$, $B$, $B'$).
3. **Játékok és evolúció** — minimax, negamax, alfa-béta; evolúciós operátorok.
4. **Következtetés** — rezolúció, szabályalapú (előre/hátra haladó) következtetés.
5. **Bizonytalanság és tanulás** — Bayes-háló, felügyelt/felügyelet nélküli tanulás, neuronhálók.

## Források és hiányok

Az 5 db `.ppsx` animáció (3.1 hegymászó/tabu, 5.1 Martelli, 5.2 fekete-fehér kirakó, 5.3 8-as kirakó, 7.1 alfa-béta) nem konvertálható (pandoc nem olvas pptx-et; az animációs lapok szövege jórészt csúcscímke-zaj), ezért a forrásmappában érintetlenül maradtak, és nem szerepelnek a lapok forrásai között.

## Fogalomlapok


### Bevezetés, modellezés és útkeresés (01–02. előadás)
- az MI fogalma — [[concepts/mesint/mi-fogalma]]
- az MI története: módszerek és célok — [[concepts/mesint/mi-modszerek-es-celok]]
- az MI felismerése egy szoftverben — [[concepts/mesint/intelligens-szoftver-jellemzoi]]
- az utazó ügynök problémája — [[concepts/mesint/utazougynok-problema]]
- a kurzus alapgondolata: modellezés + keresés — [[concepts/mesint/modellezes-es-kereses]]
- útkeresési probléma — [[concepts/mesint/utkeresesi-problema]]
- gráf fogalmak, $\delta$-gráf — [[concepts/mesint/graf-fogalmak]]
- ÉS/VAGY gráfok — [[concepts/mesint/es-vagy-grafok]]
- hiperút és megoldás-gráf — [[concepts/mesint/hiperut]]
- gráfreprezentáció — [[concepts/mesint/graf-reprezentacio]]
- útkeresés $\delta$-gráfban — [[concepts/mesint/utkereses-delta-grafban]]
- útkeresés ÉS/VAGY gráfban — [[concepts/mesint/utkereses-es-vagy-grafban]]

### Problémamodellek
- állapottér modell — [[concepts/mesint/allapotter-modell]]
- állapottér és problématér — [[concepts/mesint/allapotter-vs-problemater]]
- Hanoi tornyai — [[concepts/mesint/hanoi-tornyai]]
- $n$-királynő probléma — [[concepts/mesint/n-kiralyno-problema]]
- tologató játék (8-as, 15-ös) — [[concepts/mesint/tologato-jatek]]
- visszafelé haladó keresés — [[concepts/mesint/visszafele-halado-keresesi-modell]]
- kancsók problémája — [[concepts/mesint/kancso-problema]]
- probléma-redukciós modell — [[concepts/mesint/problema-redukcios-modell]]
- probléma-dekompozíciós modell — [[concepts/mesint/problema-dekompozicios-modell]]

### Kereső rendszerek és lokális keresés (03. előadás)
- kereső rendszer — [[concepts/mesint/kereso-rendszer]]
- vezérlési stratégiák — [[concepts/mesint/vezerlesi-strategiak]]
- hegymászó módszer — [[concepts/mesint/hegymaszo-modszer]]
- tabu keresés — [[concepts/mesint/tabu-kereses]]
- szimulált hűtés — [[concepts/mesint/szimulalt-hutes]]
- gráfszínezés — [[concepts/mesint/grafszinezes]]
- heurisztika — [[concepts/mesint/heurisztika]]
- modellfüggő vezérlés — [[concepts/mesint/modellfuggo-vezerles]]
- fekete-fehér kirakó — [[concepts/mesint/fekete-feher-kirako]]

### Visszalépéses keresés (04. előadás)
- visszalépéses keresés (VL1) — [[concepts/mesint/visszalepeses-kereses]]
- visszalépés feltételei — [[concepts/mesint/visszalepes-feltetelei]]
- sorrendi heurisztikák és vágó szabályok — [[concepts/mesint/sorrendi-heurisztikak]]
- Forward Checking — [[concepts/mesint/forward-checking]]
- Partial Look Forward és Look Forward — [[concepts/mesint/look-forward]]
- korlát-kielégítési modell — [[concepts/mesint/korlat-kielegitesi-modell]]
- mélységi korlátos visszalépés (VL2) — [[concepts/mesint/melysegi-korlatos-visszalepes]]
- a visszalépéses keresés értékelése — [[concepts/mesint/visszalepeses-kereses-ertekelese]]

### Gráfkeresés (05–06. előadás)
- általános gráfkereső algoritmus — [[concepts/mesint/altalanos-grafkereso]]
- a keresőgráf korrektsége — [[concepts/mesint/kereso-graf-korrektsege]]
- kiértékelő függvény és működési grafikon — [[concepts/mesint/kiertekelo-fuggveny-es-mukodesi-grafikon]]
- heurisztikus függvény tulajdonságai — [[concepts/mesint/heurisztikus-fuggveny-tulajdonsagai]]
- nevezetes gráfkereső algoritmusok — [[concepts/mesint/nevezetes-grafkereso-algoritmusok]]
- mélységi és szélességi gráfkeresés — [[concepts/mesint/melysegi-es-szelessegi-grafkereses]]
- előre tekintő gráfkeresés — [[concepts/mesint/elore-tekinto-grafkereses]]
- A algoritmus — [[concepts/mesint/a-algoritmus]]
- A* algoritmus — [[concepts/mesint/a-csillag-algoritmus]]
- az A* memóriaigénye — [[concepts/mesint/a-csillag-memoriaigenye]]
- az A* futási ideje — [[concepts/mesint/a-csillag-futasi-ideje]]
- B algoritmus — [[concepts/mesint/b-algoritmus]]
- B' algoritmus — [[concepts/mesint/b-vesszo-algoritmus]]
- a heurisztika szerepe — [[concepts/mesint/heurisztika-szerepe-a-grafkeresesben]]

### Kétszemélyes játékok (07. előadás)
- kétszemélyes játékok — [[concepts/mesint/ketszemelyes-jatekok]]
- játékfa — [[concepts/mesint/jatekfa]]
- Grundy mama játéka — [[concepts/mesint/grundy-mama-jateka]]
- nyerő stratégia — [[concepts/mesint/nyero-strategia]]
- részleges játékfa-kiértékelés — [[concepts/mesint/reszleges-jatekfa-kiertekeles]]
- minimax algoritmus — [[concepts/mesint/minimax-algoritmus]]
- kiértékelési változatok — [[concepts/mesint/jatekfa-kiertekelesi-valtozatok]]
- negamax algoritmus — [[concepts/mesint/negamax-algoritmus]]
- alfa-béta algoritmus — [[concepts/mesint/alfa-beta-algoritmus]]
- játékot játszó program — [[concepts/mesint/jatekot-jatszo-program]]

### Evolúciós algoritmusok (08. előadás)
- evolúciós algoritmus — [[concepts/mesint/evolucios-algoritmus]]
- az algoritmus tervezése — [[concepts/mesint/evolucios-algoritmus-tervezese]]
- kódolás — [[concepts/mesint/evolucios-kodolas]]
- rátermettség kiértékelése — [[concepts/mesint/ratermettseg-kiertekelese]]
- szelekció — [[concepts/mesint/szelekcio]]
- rekombináció és keresztezés — [[concepts/mesint/rekombinacio-es-keresztezes]]
- mutáció — [[concepts/mesint/mutacio]]
- visszahelyezés — [[concepts/mesint/visszahelyezes]]

### Automatikus következtetés (09. előadás)
- rezolúció mint keresési rendszer — [[concepts/mesint/rezolucio-mint-keresesi-rendszer]]
- cáfolati, rezolúciós és reprezentációs gráf — [[concepts/mesint/cafolati-graf]]
- átalakítás klózformára (SKNF) — [[concepts/mesint/sknf-atalakitas]]
- válaszadás rezolúcióval — [[concepts/mesint/valaszadas-rezolucioval]]
- rezolúciós stratégiák — [[concepts/mesint/rezolucios-strategiak]]
- szabályalapú következtetés — [[concepts/mesint/szabalyalapu-kovetkeztetes]]
- előre haladó szabályalapú következtetés — [[concepts/mesint/elore-halado-szabalyalapu-kovetkeztetes]]
- visszafelé haladó szabályalapú következtetés — [[concepts/mesint/visszafele-halado-szabalyalapu-kovetkeztetes]]

### Bizonytalanságkezelés (10. előadás)
- bizonytalanságkezelés — [[concepts/mesint/bizonytalansagkezeles]]
- klasszikus valószínűségszámítás — [[concepts/mesint/klasszikus-valoszinuseg-szamitas]]
- Bayes-tétel — [[concepts/mesint/bayes-tetel]]
- feltételes függetlenség — [[concepts/mesint/felteteles-fuggetlenseg]]
- Bayes-háló — [[concepts/mesint/bayes-halo]]
- Bayes-háló tervezése — [[concepts/mesint/bayes-halo-tervezese]]
- következtetés Bayes-hálókban — [[concepts/mesint/bayes-halo-kovetkeztetes]]
- Bayes-hálók tanulása — [[concepts/mesint/bayes-halo-tanulasa]]
- heurisztikus technikák — [[concepts/mesint/heurisztikus-technikak-bizonytalansagra]]

### Gépi tanulás (11. előadás)
- tanulás fogalma és modelljei — [[concepts/mesint/tanulas-fogalma-es-modelljei]]
- felügyelt tanulás — [[concepts/mesint/felugyelt-tanulas]]
- $K$ legközelebbi szomszéd — [[concepts/mesint/legkozelebbi-szomszed-modszer]]
- döntési fa és építése — [[concepts/mesint/dontesi-fa-epitese]]
- információnyereség — [[concepts/mesint/informacio-nyereseg]]
- döntési fa tanuló algoritmusa — [[concepts/mesint/dontesi-fa-tanulo-algoritmus]]
- véletlen erdő — [[concepts/mesint/veletlen-erdo]]
- felügyelet nélküli tanulás — [[concepts/mesint/felugyelet-nelkuli-tanulas]]
- $k$-közép módszer — [[concepts/mesint/k-kozep-modszer]]

### Mesterséges neuronhálók (12. előadás)
- általánosított perceptron — [[concepts/mesint/altalanositott-perceptron]]
- neuronháló topológiák — [[concepts/mesint/neuronhalo-topologiak]]
- delta-szabály — [[concepts/mesint/delta-szabaly]]
- lineáris szeparálhatóság — [[concepts/mesint/linearis-szeparalhatosag]]
- hiba-visszaterjesztés — [[concepts/mesint/hiba-visszaterjesztes]]
- rétegenként eltérő aktivizációs függvény — [[concepts/mesint/retegenkenti-aktivacios-fuggveny]]
- Hopfield-háló — [[concepts/mesint/hopfield-halo]]
