---
tags: [concept]
sources: [EA1_bevezetes.pdf]
derivation: source
updated: 2026-09-12
---

# Data Scientist

A Big Data feldolgozásához és elemzéséhez kapcsolódó két fő szerepkör
(Data Engineer és Data Scientist) egyike, valamint az ehhez kötődő
munkafolyamat-modell (OSEMN).

## Tartalom

### Data Engineer vs. Data Scientist

A két szerepkör kompetenciái részben átfednek, részben eltérnek:

- **Data Engineer**: elosztott rendszerek (distributed systems), adat-pipeline-ok
  (data pipelines) építése, magas szintű programozási ismeretek.
- **Data Scientist**: statisztika, fejlett analitika (advanced analytics),
  gépi tanulás (machine learning), mesterséges intelligencia.
- **Közös (átfedő) kompetenciák**: Big Data ismeretek, programozási nyelvek,
  rendszerüzemeltetési (systems operations) alapismeretek.

A Data Scientist szükséges készségkészletét (skillset) gyakran egy
négyszereplős Venn-diagrammal szemléltetik: hacking skills (programozás),
matematikai és statisztikai tudás, gépi tanulás, valamint az adott terület
szakértelme (substantive expertise). A hacking skills és a szakterületi
tudás metszete, matematikai/statisztikai alapok nélkül, az ún. "veszélyzóna"
(danger zone): a technikailag helyes, de szakmailag megalapozatlan
következtetések kockázata.

### A szerepkör népszerűsége

A 2010-es évek folyamán a Data Scientist szakma iránti kereslet (állásfelhívások
száma) folyamatosan, meredeken emelkedett — ezt szemlélteti a dia a "legszexibb
szakma a 21. században" (Harvard Business Review-eredetű) elnevezéssel is.

### A munka valósága

A dia szándékosan szembeállítja a Data Scientist munkájáról alkotott
elképzeléseket (munkatársak szerint: absztrakt matematikai/fizikai
képletek; a család szerint: elvont "gondolkodás") a gyakorlattal: a
mindennapi munka jelentős része adatbetöltés és -tisztítás (pl. `pandas`,
`numpy` importálása, SQL-szerű lekérdezések), nem pedig elméleti modellezés.

### OSEMN munkafolyamat

Az OSEMN mozaikszó az adatelemzési folyamat öt egymásra épülő lépését
foglalja össze:

1. **Obtain** — adat megszerzése (más rendszerből, adatbázisból, API-ból,
   fájlból, vagy akár generálással, pl. szenzorokból).
2. **Scrub** — adattisztítás: sorok szűrése, oszlopok/szavak kinyerése,
   értékek cseréje, hiányzó értékek kezelése, formátumok konvertálása.
3. **Explore** — az adat megértése, alapstatisztikák számítása,
   vizualizációk készítése.
4. **Model** — modellezés: klaszterezés, osztályozás, regresszió,
   dimenziócsökkentés.
5. **iNterpret** — az eredmények értelmezése: következtetések levonása,
   az eredmények jelentőségének értékelése, kommunikálása.

## Kapocs

- [[concepts/bigdata/big-data]] — a Big Data fogalma, amelynek elemzéséhez a
  Data Scientist szerepkör kapcsolódik
