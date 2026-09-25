---
tags: [concept, esemalk/avaloniaui-halado-temak]
sources: [elte_eva_ea10_avaloniaui_complex.pdf]
derivation: source
updated: 2026-09-13
---

# Avalonia UI — alkalmazás életciklus kezelése

Az Avalonia UI-ban az alkalmazás elindítása és leállítása asztali környezetben
(Windows, Linux) életciklus-eseményekként kezelhető, az `App` osztály
felüldefiniált metódusán keresztül.

## Tartalom

Az `App` osztály `OnFrameworkInitializationCompleted` metódusát
felüldefiniálva eseménykezelőkkel adható meg, hogy mi történjen az alkalmazás
elindításakor és leállításakor. A klasszikus asztali (desktop) élettartam-
objektumon a `Startup` és `Exit` eseményekre lehet feliratkozni:

```csharp
desktop.Startup += (sender, args) =>
{
    // ...
};
```

Ez az életciklus-kezelés az alapja annak, hogy egy alkalmazás induláskor
visszatöltse, leállításkor pedig elmentse az állapotát — lásd
[[concepts/esemalk/avalonia-platformfuggetlen-perzisztencia]].

## Kapocs

- [[concepts/esemalk/avalonia-mobil-alkalmazaskornyezet-eletciklus]] — a
  mobil (Android/iOS) oldali életciklus (futás alatt/felfüggesztve/
  leállítva, `IActivatableLifetime`), amely ennek a desktop-oldali
  életciklus-kezelésnek az analógja
- [[concepts/esemalk/avalonia-bevezetes]] — az Avalonia UI keretrendszer
  áttekintése
- [[concepts/esemalk/avalonia-platformfuggetlen-perzisztencia]] — az
  életciklus-eseményekhez kötött állapotmentés és -betöltés
- [[concepts/esemalk/wpf-idozites]] — a `Dispatcher`/időzítés WPF-es
  megfelelője szálbiztos felületfrissítéshez
