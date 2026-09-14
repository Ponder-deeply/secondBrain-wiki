---
tags: [concept]
sources: [elte_eva_ea05_winforms_multithread.pdf]
derivation: source
updated: 2026-09-13
---

# Szál létrehozása és kezelése C#-ban

Új szál indítása a `Thread` típus példányosításával és a `Start` metódus
meghívásával, valamint az ebből fakadó korlátok.

## Tartalom

A C# programban új szálat többféleképpen is indíthatunk, legegyszerűbben a
`Thread` típus példányosításával, majd a `Start` metódus meghívásával:

```csharp
ThreadStart job = new ThreadStart(SomeMethod);
Thread thread = new Thread(job);
thread.Start();
```

- A szál példányosításakor paraméterként adjuk át az új szálon
  végrehajtandó metódust (`ThreadStart` delegált).
- A gyerekszálon futó feladat végrehajtása a szülőszálon bevárható a
  `Thread` objektum `Join()` metódusával.
- Dönthetünk a gyerekszál terminálása mellett is (`Abort()`).
- A szálak végrehajtási sorrendje **nem determinisztikus**: két, egymástól
  független szál kiírásai tetszőleges sorrendben jelenhetnek meg (pl. a fő
  szál és egy `Thread.Sleep`-pel elaltatott gyerekszál kiírásai
  felcserélődhetnek egymáshoz képest).

### Paraméterátadás az új szálnak

Az új szálnak paramétert a `ParameterizedThreadStart` delegálttal lehet
átadni. A paraméter statikus típusa `object`, konkrét értékét a `Start()`
metódus hívásakor adjuk meg; a paraméter lehet tömb vagy egyéb gyűjtemény is,
így több érték is átadható:

```csharp
ParameterizedThreadStart childJob =
    new ParameterizedThreadStart(DoWork);
Thread childThread = new Thread(childJob);
childThread.Start("Message from Main");
```

A gyerekszálban dobott kivételt ott is kell kezelni — a szülőszálban erre
már nincs lehetőség. Kezeletlen kivétel esetén a program terminál.

### A `Thread` típus korlátai

Az alacsony absztrakciós szintű `Thread` alapú szálkezelésnek több
korlátja is van:

- nincs lehetőség erősen típusos paraméterátadásra (csak megosztott memória
  használható),
- nincs lehetőség az eredmény visszaadására (csak megosztott memória
  használható),
- nincs lehetőség a kivételek továbbítására a gyerekszálból a fő szál felé.

Ezeket a korlátokat a taszk-alapú aszinkron programozás oldja fel.

## Kapocs

- [[concepts/esemalk/folyamat-es-szal]] — a folyamat és a szál fogalma
- [[concepts/esemalk/kritikus-szakasz-kolcsonos-kizaras]] — a szálak közötti
  adatkommunikáció és a kölcsönös kizárás szükségessége
- [[concepts/esemalk/csharp-task-alapok]] — a `Thread` korlátait feloldó
  taszk-alapú aszinkron programozás
