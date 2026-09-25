---
tags: [concept, esemalk/tobbszalu-programozas-csharp-ban]
sources: [elte_eva_ea05_winforms_multithread.pdf]
derivation: source
updated: 2026-09-13
---

# Aszinkron tevékenységek megszakítása (`CancellationToken`)

Aszinkron műveletek teljes befejezésük előtti megszakítására a taszkalapú
aszinkron eljárások beépített abortálási mechanizmust biztosítanak.

## Tartalom

Az aszinkron műveletek végrehajtását adott esetben azok teljes befejezése
előtt meg kívánjuk szakítani:

- a párhuzamos szál terminálása a háttérművelet inkonzisztens állapotban
  történő megszakításának kockázatával jár, ezért nem javasolt megoldás,
- a taszkalapú aszinkron eljárások ezért támogatják az abortálási igény
  **detektálását és kezelését** a `CancellationTokenSource`/
  `CancellationToken` páron keresztül.

```csharp
var source = new CancellationTokenSource();
var token = source.Token;
var task = new Task(() => { ... }, token);
```

- megszakítási igény jelzése a taszkon kívülről:

```csharp
source.Cancel();
```

- megszakítási igény észlelése a taszkban:

```csharp
if (token.IsCancellationRequested) { ... }
```

A megszakítás tehát kooperatív: a taszknak magának kell rendszeresen
ellenőriznie a tokent, és ennek megfelelően félbeszakítania a saját
végrehajtását.

## Kapocs

- [[concepts/esemalk/csharp-async-await]] — az `async`/`await`
  konstrukció, amelyben a megszakítható taszkok tipikusan futnak
  - [[concepts/esemalk/csharp-task-alapok]] — a `Task` típus alapjai
- [[concepts/esemalk/winforms-fibonacci-parhuzamositas-pelda]] — a
  `Cancel()` metóduson keresztül megszakítható Fibonacci-generálás példája
