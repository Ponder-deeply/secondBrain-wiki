---
tags: [concept]
sources: [Java-Language-Specification-SE-21.pdf]
derivation: source
kind: model
element: water
updated: 2026-10-23
---

# A Java memóriamodell

A memóriamodell azt írja le, hogy egy program adott végrehajtási nyoma szabályos-e: melyik olvasás melyik írás értékét láthatja. Fő fogalmai a szinkronizációs sorrend, a happens-before reláció és a szekvenciális konzisztencia.

## Tartalom

### Cél (JLS §17.4)

A memóriamodell minden olvasásnál ellenőrzi, hogy a látott írás a szabályok szerint érvényes-e. Az implementáció tetszőleges kódot generálhat, amíg minden eredmény megjósolható a modellel; ez teret ad az utasítások átrendezésének és a felesleges szinkronizáció eltávolításának. Nem megfelelően szinkronizált programok meglepő viselkedést mutathatnak (átrendezés, *forward substitution*).

### Alapfogalmak

- **Megosztott változó** (§17.4.1): mezők, `static` mezők és tömbelemek (heap); lokális változók és paraméterek sosem megosztottak.
- **Akciók** (§17.4.2): normál olvasás/írás, szinkronizációs akciók (volatile read/write, lock, unlock, a szál első/utolsó akciója, szál indítása/befejezésének észlelése), külső akciók, szál-divergencia akciók. Egy akció `<t, k, v, u>` négyes.
- **Programsorrend** (§17.4.3): egy szál akcióinak teljes rendezése a szálon belüli szemantika szerint.
- **Szekvenciális konzisztencia:** minden akció egy teljes sorrendben történik, amely összhangban van a programsorrenddel, és minden olvasás a sorrendben hozzá legutóbb előző írás értékét látja. Erős garancia; ha egy program adatversenymentes, minden végrehajtása ilyennek látszik.
- **Szinkronizációs sorrend** (§17.4.4) és a **synchronizes-with** élek: unlock → későbbi lock ugyanazon a monitoron; volatile írás → későbbi olvasás; szál indítása → a szál első akciója; az alapértelmezett érték írása → minden szál első akciója; egy szál utolsó akciója → az őt észlelő (`isAlive()`, `join()`) szál akciója; `interrupt` → a megszakítás észlelése.
- **Happens-before** (§17.4.5): programsorrend, synchronizes-with, konstruktor vége → finalizer kezdete, és tranzitív lezárás. Következmények: unlock → későbbi lock; volatile írás → későbbi olvasás; `start()` → az indított szál minden akciója; egy szál akciói → minden akció, ami a `join()`-ból sikeresen visszatér.

A happens-before nem jelenti, hogy a megvalósításnak ténylegesen ebben a sorrendben kell végrehajtania; csak a *megfigyelhető* eredménynek kell legálisnak lennie.

### Szabályos végrehajtás

Egy olvasás *megfigyelheti* az írást, ha nincs előtte happens-before és nincs közbeeső írás. A **happens-before konzisztencia** szükséges, de nem elégséges (§17.4.8): megengedheti az „out of thin air” értékeket (`r1 = x; if (r1 != 0) y = 1;` / `r2 = y; if (r2 != 0) x = 1;`), ezért a modell *okozatossági* (causality) követelményeket is támaszt: az akciókat fokozatosan „véglegesítik” (committing), C₀ = ∅-től. Egy jól formált végrehajtás: `<P, A, po, so, W, V, sw, hb>`, és teljesül a szálon belüli konzisztencia, a happens-before- és a szinkronizációs-sorrend-konzisztencia.

### Megfigyelhető viselkedés (§17.4.9)

A program viselkedése a külső akciók véges halmazaival írható le; nemterminálódó programoknál külön *hang* akció jelzi a tartós blokkolást vagy végtelen belső munkát.

### Szabály a gyakorlatban

*Helyesen szinkronizált* program (nincs adatverseny a szekvenciálisan konzisztens végrehajtásokban) esetén a programozónak nem kell az átrendezésekkel foglalkoznia.

## Kapocs

- [[concepts/konkprog/verseny-helyzet-es-adatverseny]] — adatverseny a gyakorlatban
- [[concepts/konkprog/volatile-mezo]] — volatile szemantika
- [[concepts/konkprog/final-mezo-szemantika]] — final mezők speciális szabályai
- [[concepts/konkprog/synchronized-monitor]] — zár mint synchronizes-with forrás
