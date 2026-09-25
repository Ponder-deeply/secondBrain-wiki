---
tags: [concept, esemalk/tobbszalu-programozas-csharp-ban]
sources: [elte_eva_ea05_winforms_multithread.pdf]
derivation: source
updated: 2026-09-13
---

# Felületi vezérlők kezelése párhuzamos végrehajtás során (`Invoke`, `BeginInvoke`)

A Windows Forms asztali grafikus keretrendszerben minden vezérlőt csak az őt
létrehozó (UI) szál kezelhet — ezt oldja fel a `Control.Invoke` és
`BeginInvoke` metóduspár.

## Tartalom

A tárgyalt módon aszinkron végrehajtásra kerül a kód, amennyiben explicit
egy új taszkot indítunk el — pl. egy `Task` objektum `Start()` metódusával,
vagy a `Task.Run()`, vagy a `Task.Factory.StartNew()` meghívásával.
Továbbá az aszinkron metódusok (`async`) szinkronban futnak, amíg el nem
érik az első várakozási kifejezést (`await`), utána ez már nem biztosított.

A Windows Forms asztali grafikus keretrendszerben minden vezérlőt csak az őt
létrehozó szál kezelhet — különben *cross-thread operation* miatti kivételt
kaphatunk (`InvalidOperationException`).

Ezt megoldandó minden `Control` objektum rendelkezik egy `Invoke`
metódussal, ami a paraméterül kapott lambda kifejezést a felületet birtokló
szálon hajtja végre:

- ha nem fontos a háttérszál blokkolása a frissítés megvárása közben,
  használhatjuk a `BeginInvoke` eljárást is (nem várja meg a végrehajtást),
- használhatjuk a vezérlők `InvokeRequired` tulajdonságát annak
  ellenőrzésére, hogy az adott kontextusban szükséges-e visszatérni a
  felületi vezérlőt birtokló szálra annak kezeléséhez.

```csharp
private void Ready(object? sender, EventArgs e) {
    // amennyiben nem a UI szálon vagyunk, rekurzív
    // módon meghívjuk a Ready() eljárást, de már a
    // UI szálon.

    if (_btnCalculate.InvokeRequired) {
        BeginInvoke(new EventHandler(Ready),
                    sender, e);
        return;
    }
    _btnCalculate.Text = "Számol";
    …
}
```

## Kapocs

- [[concepts/esemalk/winforms-vezerlok-alapjai]] — a `Control` osztály és a
  WinForms vezérlők alapjai
- [[concepts/esemalk/csharp-async-await]] — az `async`/`await`
  konstrukció, amely mellett az `Invoke`/`BeginInvoke` szükséges a felület
  biztonságos frissítéséhez
- [[concepts/esemalk/winforms-fibonacci-parhuzamositas-pelda]] — a
  `BeginInvoke` gyakorlati alkalmazása a `Ready` eseménykezelőben
