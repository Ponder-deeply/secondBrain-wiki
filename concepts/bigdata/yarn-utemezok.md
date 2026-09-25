---
tags: [concept, bigdata/hadoop-okoszisztema]
sources: [EA2_hadoop.pdf]
derivation: source
updated: 2026-09-12
---

# YARN ütemezők (FIFO, Capacity, Fair)

A YARN Resource Managerébe épített ütemezési stratégiák, amelyek eldöntik,
hogy egy klaszter erőforrásait több egyidejű felhasználó/job (tenant) között
hogyan osszák meg.

## Tartalom

### A multi-tenancy probléma

- **tenant**: felhasználók/jobok.
- **multi-tenant** működés: különböző felhasználók, különböző jobokkal
  osztoznak ugyanazon a klaszteren.

Több felhasználó, több job esetén a cél az optimális erőforrás-kihasználás,
az infrastruktúra megosztása, és a különböző csoportok (fejlesztők, data
scientistek, elemzők) egyidejű kiszolgálása ugyanazon az adaton és
klaszteren — ezt támogatja a YARN, valamint rajta keresztül a MapReduce,
Spark, Hive stb.

### Statikus megoldás

Cgroups segítségével a YARN-on kívül is korlátozható az erőforrás-használat,
statikus paraméterekkel: CPU-megosztás, I/O-súly, memória. Hátránya, hogy a
felosztás fix, nem alkalmazkodik a pillanatnyi terheléshez.

### Dinamikus megoldások

A Capacity és a Fair scheduler dinamikusan, sorok (queue-k) alapján osztja el
az erőforrásokat: az erőforrások meg vannak osztva a sorok között, és ha egy
sor éppen nem használja a neki jutó részt, a többi sor szabadon
felhasználhatja azt. A sorokhoz való hozzáférés felhasználó- vagy
csoport-szinten szabályozható.

#### FIFO Scheduler

- First In First Out: a jobok az indításuk sorrendjében kerülnek ütemezésre.
- Minden job az egész klasztert használja — nem hatékony megosztás.
- Egy lassú job kiéheztetheti az utána érkező jobokat.
- Előnye: nem igényel konfigurációt.

#### Capacity Scheduler

- Egyszerű klaszter-megosztás: a sorok százalékos formában kapnak
  kapacitást (pl. `root` sor 100%-a `prod` 40% és `dev` 60% al-sorra oszlik,
  a `dev` sor pedig `job1`/`job2` között 50-50%-ra).
- A megosztás minimum erőforrást garantál minden sornak.
- A soroknak lehetnek al-sorai.
- Konfigurálható maximális kapacitás is: pl. ha az `A` sor üres, a `B` sor
  átmenetileg a teljes klasztert használhatja (`maximum-capacity` paraméter).

#### Fair Scheduler

- A leggyakrabban használt ütemező.
- Az indított jobok "fair" módon osztoznak a klaszter erőforrásain — minden
  jobnak mindig jut egy minimum erőforrás.
- Egy beküldött job csak akkor indul, ha felszabadul számára erőforrás (addig
  nem futnak taskok).
- Támogatja a **preemption** opciót: ez lehetőséget ad az ütemezőnek, hogy
  futó containereket törölve szabadítson fel erőforrást egy magasabb
  prioritású job számára.

## Kapocs

- [[concepts/bigdata/yarn]] — a Resource Manager és a YARN architektúra,
  amelynek része az ütemező komponens
- [[concepts/bigdata/mapreduce]] — az egyik feldolgozási modell, amelynek
  jobjait ezek az ütemezők osztják szét a klaszteren
