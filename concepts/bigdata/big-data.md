---
tags: [concept, bigdata/bevezetes]
sources: [EA1_bevezetes.pdf]
derivation: source
updated: 2026-09-12
---

# Big Data

A hagyományos, egygépes adatfeldolgozó rendszerek kapacitását és sebességét
meghaladó méretű, sebességű vagy összetettségű adat, illetve az ennek
kezelésére kialakult rendszerek és módszerek gyűjtőneve.

## Tartalom

### Definíció

Egy elterjedt (Forbes/Edd Dumbill-féle) megfogalmazás szerint Big Data az az
adat, amely meghaladja a hagyományos adatbázis-rendszerek feldolgozási
kapacitását: túl nagy, túl gyorsan mozog, vagy nem illeszkedik a meglévő
adatbázis-architektúrák struktúráihoz. A lényeg nem kizárólag a méret: kis
adatból is nyerhető nagy érték, ha jól használják fel.

### Motiváció — miért nem elegendőek a hagyományos rendszerek?

A hagyományos rendszerek jellemzően:

- egygépesek,
- relatíve kis méretű, statikus adatokon dolgoznak,
- komplex feladatokat ezen az egy gépen elérhető adaton végeznek el.

A probléma akkor jelentkezik, amikor az adat mérete meghaladja egy gép
kapacitását. Klasszikus illusztráció (Google-példa): napi 10 milliárd weblap
feldolgozása, átlagosan 20 KB méretben, összesen 200 TB adatot jelent. Egyetlen
lemez ~50 MB/s olvasási sebessége mellett ennek beolvasása kb. 4 milliárd
másodpercig, azaz 46+ napig tartana — egyetlen gépen kivitelezhetetlen.

A kapacitás növelésének két útja van:

- **vertikális skálázás**: gyorsabb processzor, több memória egyetlen gépen —
  korlátos és drága;
- **horizontális skálázás**: több gép klaszterbe szervezése, az adatok
  elosztott tárolása (pl. HDFS) és a számítások párhuzamosítása (pl.
  MapReduce) — ez a Big Data architektúrák alapgondolata.

### A Big Data jellemző dimenziói

A Big Data adat jellemzőit a bevezető lapokon az ún. "V"-k (volume, velocity,
variety, veracity, value, és a további bővítések) írják le részletesen, lásd
[[concepts/bigdata/big-data-5v]].

### Kihívások

Egy Big Data rendszer tervezésekor tipikusan felmerülő kihívások: adatintegráció
(különböző forrásokból, formátumokból érkező adat összekapcsolása),
skálázhatóság, adatbiztonság és -védelem, megfelelő adatbányászati technikák
kiválasztása, feldolgozási teljesítmény, adatminőség, szabványosítás hiánya,
adatátvitel és -tárolás, valamint a vizualizáció.

### Alkalmazási területek

A Big Data módszereket ma gyakorlatilag minden iparágban használják: e-kereskedelem
és ajánlórendszerek (pl. Netflix videóajánlás, hasonlósági rangsorolás),
virtuális asszisztensek (Siri, Google Now), IoT (Internet of Things) eszközök
adatgyűjtése és -elemzése, valamint Business Intelligence (BI) rendszerek. Egy jó
Big Data architektúra tulajdonsága éppen az, hogy ugyanaz a rendszer alkalmas
IoT- és BI-jellegű felhasználásra is (lásd
[[concepts/bigdata/big-data-architektura]]).

## Kapocs

- [[concepts/bigdata/big-data-5v]] — a Big Data jellemző dimenziói (volume,
  velocity, variety, veracity, value)
- [[concepts/bigdata/big-data-architektura]] — az adat kezelésére kialakított
  architektúrák és azok komponensei
- [[concepts/bigdata/big-data-okoszisztema]] — a Big Data feldolgozásra használt
  technológiák áttekintése
- [[concepts/bigdata/data-scientist]] — a Big Data feldolgozásához kapcsolódó
  szerepkörök
