---
tags: [concept]
sources: [elte_eva_ea05_winforms_multithread.pdf]
derivation: source
updated: 2026-09-13
---

# Taszkok szinkronizálása

A .NET alkalmazások rendelkezhetnek egy szinkronizációs kontextussal
(`SynchronizationContext.Current`), amely megadja, hogy az `await` utáni
kifejezések melyik szálon folytatódjanak; a `TaskScheduler` típus pedig
finomabb vezérlést biztosít arra, hogy a taszkok mely szálon kerüljenek
végrehajtásra.

## Tartalom

### `SynchronizationContext`

- Konzolos alkalmazásokban nincs (alapértelmezett) szinkronizációs
  kontextus objektum: az `await` utáni utasítások nem garantáltan a hívó
  szálon futnak.
- A Windows Forms alkalmazások rendelkeznek egy alapértelmezett
  szinkronizációs kontextussal: a `SynchronizationContext.Current` értéke
  egy `WindowsFormsSynchronizationContext` típusú objektum.
- A `WindowsFormsSynchronizationContext` implementálja, hogy `await`
  utasítás után a `BeginInvoke` használatával a UI szálra térjünk vissza.
  Emiatt Windows Forms alkalmazásokban `await` után nem szükséges az
  explicit `Invoke`/`BeginInvoke` használata — a folytatás már eleve a UI
  szálon fut.
- Ez **nem** vonatkozik egy másik szálról kiváltott eseményre (pl. a
  `System.Timers.Timer` `Elapsed` eseménye — lásd
  [[concepts/esemalk/winforms-idozito-parhuzamositas]]): azok továbbra is az
  adott (nem UI) szálon váltódnak ki, és ha kezelésükhöz felületi vezérlők
  elérése szükséges, manuálisan kell szinkronizálni a szálakat.
- Az implicit szinkronizáció `await` után kikapcsolható a taszkra hívott
  `ConfigureAwait(false)`-zal — ez javíthatja a teljesítményt, ha egyébként
  gyakori és szükségtelen szinkronizációra kerülne sor:

  ```csharp
  await MethodAsync().ConfigureAwait(false);
  ```

  Ha a bevárni kívánt taszk időközben elkészült, `ConfigureAwait(false)`
  esetén is az eredeti szálon maradhatunk a végrehajtás; ha még nem készült
  el, a folytatás egy másik szálon fut:

  ```csharp
  Task task = ...
  ...
  await task.ConfigureAwait(false);
  // ha a task elkészült, akkor az eredeti szálon
  // folytatódik a végrehajtás, ha még nem,
  // akkor egy másikon
  ```

### `TaskScheduler`

- A `TaskScheduler.Default` az alapértelmezett, *thread pool* alapú ütemező:
  egy új *thread pool*-ból elérhető szálon ütemezi a végrehajtást.
- A statikus `TaskScheduler.FromCurrentSynchronizationContext` metódussal
  kérhető egy `TaskScheduler` objektum az aktuális szinkronizációs
  kontextushoz.
- A `TaskScheduler.Current` egy taszkon belül az aktuális, egyébként az
  alapértelmezett ütemezőt adja meg.
- Egy `TaskScheduler` típusú paraméter átadható a taszkok
  példányosításakor, illetve a `ContinueWith` metódusnak, amellyel taszkok
  végrehajtása egymás után láncolható:

  ```csharp
  TaskScheduler scheduler =
    TaskScheduler.FromCurrentSynchronizationContext();
    // taszk szinkronizációs objektum

  Task.Run(() => DoBackgroundWork())
    .ContinueWith(() => { label.Text = "Ready."; },
      scheduler);
    // a DoBackgroundWork() futtatása aszinkron módon
    // háttérszálon történik;
    // majd a UI (szöveges címke) frissítése szinkron,
    // szálbiztos módon történik
  ```

  Jellemzően nincs szükség szinkronizációra, de a grafikus felület
  vezérlőinek elérésekor igen — ilyenkor a `ContinueWith`-nek átadott
  `TaskScheduler` biztosítja a UI szálra való visszatérést.

- Haladó felhasználás a `ConcurrentExclusiveSchedulerPair`, amelynek két
  ütemezője van: a `ConcurrentScheduler`-rel ütemezett taszkok
  párhuzamosan futhatnak, míg az `ExclusiveScheduler`-rel ütemezettek nem —
  ezzel garantálható, hogy egy adott tevékenység végzésekor ne fusson más
  taszk ugyanazzal az objektummal ütemezve:

  ```csharp
  var cesp = new ConcurrentExclusiveSchedulerPair();
  Task task = Task.Factory.StartNew(() => {
      // olyan tevékenység, amelynek elvégzésekor
      // garantáltan ne fusson más taszk a
      // cesp objektummal ütemezve
  }, ..., cesp.ExclusiveScheduler);
  ```

## Kapocs

- [[concepts/esemalk/csharp-task-alapok]] — a taszk-alapú (`Task`) aszinkron
  programozás alapjai
- [[concepts/esemalk/winforms-idozito-parhuzamositas]] — időzítő-alapú
  párhuzamosítás WinForms alkalmazásban, ahol más szálról kiváltott
  eseményt manuálisan kell szinkronizálni a felülettel
- [[concepts/esemalk/folyamat-es-szal]] — a folyamat és a szál fogalma
- [[concepts/esemalk/csharp-szal-letrehozasa-kezelese]] — a `Thread` típus
