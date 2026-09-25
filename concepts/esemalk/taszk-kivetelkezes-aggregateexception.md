---
tags: [concept, esemalk/tobbszalu-programozas-csharp-ban]
sources: [elte_eva_ea05_winforms_multithread.pdf]
derivation: source
updated: 2026-09-13
---

# Kivételkezelés taszkokkal (`AggregateException`)

A taszkokon belül keletkező kezeletlen kivételek visszapropagálásra kerülnek
a hívó szál felé, egységesen `AggregateException` példányként.

## Tartalom

Egyetlen taszk esetén a kivétel a `Result` tulajdonság (vagy a `Wait()`)
lekérdezésekor a hívó szálon kerül újra kidobásra:

```csharp
Console.WriteLine("Main thread starts");
Task<int> task = DoWorkAsync(42);

Console.WriteLine("Main thread waiting");
try {
    int result = task.Result;
    // eredmény megvárása
}
catch (Exception ex) {
    // kivételek kezelése ...
}
Console.WriteLine("Main thread finishes");
```

Bizonyos esetekben — például amikor több taszkra várakozunk egyszerre —
több kivétel is keletkezhet. Ezeket minden esetben egy `AggregateException`
példányként kaphatjuk el, amelynek `InnerExceptions` gyűjteménye tartalmazza
az egyes taszkokban keletkezett kivételeket:

```csharp
Console.WriteLine("Main thread starts");
Task<int> taskA = DoWorkAsync(42);
Task<int> taskB = DoWorkAsync(100);

Console.WriteLine("Main thread waiting");
try {
    Task.WaitAll(new Task[] { taskA, taskB });
    // taskA.Result és taskB.Result elérhető ezen a ponton
}
catch (AggregateException ae) {
    foreach (var e in ae.InnerExceptions) {
        // kivételek kezelése ...
    }
}
Console.WriteLine("Main thread finishes");
```

## Kapocs

- [[concepts/esemalk/csharp-task-alapok]] — a `Task` típus alapjai
- [[concepts/esemalk/csharp-async-await]] — az `async`/`await`
  konstrukció, amelynél ugyanez a kivételpropagálás érvényesül
- [[concepts/esemalk/csharp-kivetelkezeles]] — a kivételkezelés C#-beli
  alapjai
