---
tags: [concept, esemalk/avaloniaui-alapok]
sources: [elte_eva_ea09_avaloniaui.pdf]
derivation: source
updated: 2026-09-13
---

# Avalonia telepítése és projekt létrehozása

Az Avalonia NuGet csomagok telepítésén keresztül könnyedén egy létező
projekthez adható, de a kezdeti fejlesztéshez az előre elkészített
sablonprojektek (*template*-ek) használata hasznosabb.

## Tartalom

### Telepítés parancssorból

```
dotnet new install Avalonia.Templates
dotnet new avalonia.mvvm -o MyApp -n MyApp
```

Az első parancs telepíti az Avalonia sablonokat, a második egy új MVVM
alapú Avalonia alkalmazást hoz létre.

### Visual Studio és egyéb IDE-k

Visual Studio használata esetén célszerű az *Avalonia for Visual Studio 2022*
kiegészítő telepítése, amely nemcsak a sablonokat, hanem a grafikus
felülettervezőt is biztosítja. JetBrains Riderhez is elérhető hasonló
támogatás.

### Mobil és WebAssembly célplatformok telepítése

- **Android**: az Android SDK-t (opcionálisan emulátort) és a Java SDK-t kell
  telepíteni. A legegyszerűbb megoldás a *MAUI workload* telepítése a Visual
  Studio telepítőjének újrafuttatásával; Linux alatt a
  `dotnet workload install android` paranccsal telepíthető a minimálisan
  szükséges workload, majd az Android SDK és a Java SDK külön telepítése
  szükséges.
- **WebAssembly**: a *WebAssembly Build Tools* csomag telepítése szükséges az
  *ASP.NET and web Development workload* nem kötelező csomagjai közül.

### Új projekt létrehozása (Template Studio varázsló)

A Visual Studio "Create a new project" párbeszédablakában az *Avalonia C#
Project* (illetve F# megfelelője) sablon egy varázsló (Template Studio)
segítségével építi fel a projektet:

1. **Platform** — célplatformok kiválasztása (Desktop, Web, Android, iOS)
2. **Design pattern** — tervezési minta, pl. *Community Toolkit* (lásd
   [[concepts/esemalk/avalonia-mvvm-adatkotes]] és
   [[concepts/esemalk/wpf-mvvm-tamogato-csomagok]])
3. **Features** — további jellemzők

## Kapocs

- [[concepts/esemalk/avalonia-bevezetes]] — az Avalonia UI áttekintése és
  architektúrája
- [[concepts/esemalk/avalonia-projekt-felepites]] — a létrehozott projekt
  multi-projekt szerkezete
- [[concepts/esemalk/csharp-dotnet-platform]] — a .NET platform és a
  `dotnet` parancssori eszköz
- [[subjects/esemalk]]
