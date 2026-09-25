---
tags: [concept, esemalk/csharp-nyelvi-alapok]
sources: [elte_eva_ea00_csharp.pdf]
derivation: source
updated: 2026-09-12
---

# .NET platform

A *.NET platform* a Microsoft szoftverfejlesztési platformja: egy egységes
alapra (*.NET Standard*) épülő, több keretrendszerből és programcsomagból álló
együttes, amelynek központi programozási nyelve a [[concepts/esemalk/csharp-nyelv-jellemzoi]].

## Tartalom

### Felépítés

- A programok egy közös köztes nyelvű kódra (*Intermediate Language*, IL)
  fordulnak, amely platformfüggetlen.
- A köztes nyelvű kódot a virtuális gép (*Common Language Runtime*, CLR)
  interpretálja, amely biztosítja a futás felügyeletét (pl. szemétgyűjtés) és a
  dinamikus programozás támogatását (pl. reflexió).
- Több nyelvet támogat (C#, Visual C++, Visual Basic.NET, F#), de a központi
  nyelve a C#.
- Több UI-keretrendszert is támogat: Windows Forms, WPF, WinUI, Xamarin / MAUI,
  Avalonia UI, Unity.

### .NET Framework és .NET Core

A Microsoft historikus okokból két keretrendszert készített:

- **.NET Framework** (1.0 verzió, 2002) — a folyamatos fejlődés mellett
  problémák halmozódtak: Windows-központú megközelítés, monolitikus/nem
  megfelelően modularizált felépítés, zárt forráskód. A 4.8 az utolsó verzió,
  további fejlesztés nincs tervezve.
- **.NET Core** (2016) — megoldást nyújt ezekre: cross-platform (Windows,
  Linux, macOS), modularizált felépítés (csak a szükséges komponensek vannak
  jelen), nyílt forráskód.
- A *.NET Core 3*-tól kezdve a keretrendszer tartalmazhat ún. *desktop
  package*-eket, amelyek csak bizonyos platformokon érhetők el — így vált
  elérhetővé .NET Core alatt is az asztali alkalmazásfejlesztés (Windows Forms,
  WPF).
- A .NET Core 3.1 utáni verzió a *.NET 5* nevet kapta (a verziózásból adódó
  félreértések elkerülése végett — nem esik egybe a .NET Framework
  verziószámozásával). Jelenleg a .NET 8 (LTS) és a .NET 9 az aktuális kiadások.

### .NET Standard

Egységes könyvtárat ír elő, amelyet minden, a platformra épülő keretrendszer
implementál — így megadható a verziók közötti megfeleltetés (pl. .NET
Standard 2.0 ⇔ .NET Core 2.0 ⇔ .NET Framework 4.6.1 ⇔ Mono 5.4 ⇔ Xamarin.iOS
10.14 stb.). Ez teszi lehetővé, hogy egy könyvtár több keretrendszer alatt is
felhasználható legyen.

## Kapocs

- [[concepts/esemalk/csharp-nyelv-jellemzoi]] — a platform központi nyelve
