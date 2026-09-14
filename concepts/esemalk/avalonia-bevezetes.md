---
tags: [concept]
sources: [elte_eva_ea09_avaloniaui.pdf]
derivation: source
updated: 2026-09-13
---

# Avalonia UI bevezetés

Az *Avalonia UI* a .NET keretrendszerre épülő, multi-platform eseményvezérelt
grafikus keretrendszer — a WPF cross-platform utódja, amely a Windows mellett
Linuxot, macOS-t, Androidot, iOS-t és WebAssemblyt is támogatja.

## Tartalom

Az Avalonia UI alapja a .NET keretrendszer, amely maga is lehetővé teszi a
cross-platform fejlesztést a támogatott platformok között. Az Avalonia
támogatja a fejlesztést MV architektúrában is, de kifejezetten az MVVM
architektúra használata javasolt (lásd [[concepts/esemalk/avalonia-mvvm-adatkotes]]
és a WPF-es megfelelője, [[concepts/esemalk/wpf-mvvm-alapok]]). A felület
deklaratív leírására XAML szolgál, és a nézetmodell réteg kompatibilis a WPF és
a MAUI alkalmazások nézetmodell rétegével, megfelelő tervezés esetén. Az
Avalonia opcionálisan lehetővé teszi a reaktív programozást is.

Az Avalonia architektúrája rétegzett:

- **App Code** — az alkalmazás saját kódja
- **Avalonia** — az UI SDK réteg
- **Skia** (*Google Skia*) — a rajzolási (rendering) réteg, amely egységes
  grafikus felületet biztosít minden platformon
- **.NET BCL** — a .NET alaposztálykönyvtár
- **Mono Runtime** / **.NET Core CLR** — a futtatókörnyezet, platformtól
  függően
- **Operációs rendszer** — iOS, Android, WebAssembly, Windows, macOS, Linux

Ez az egységes, Skia-alapú rajzolás az egyik legfontosabb különbség a
WPF-hez képest, amely a Windows saját grafikus alrendszerére (Direct3D)
támaszkodik — lásd [[concepts/esemalk/wpf-bevezetes]].

## Kapocs

- [[concepts/esemalk/wpf-bevezetes]] — a WPF, amelynek az Avalonia UI a
  cross-platform utódja; a Windows-only korlát és a Direct3D-alapú rajzolás
  kontrasztja
- [[concepts/esemalk/avalonia-telepites-projekt-letrehozas]] — az Avalonia
  telepítése és új projekt létrehozása
- [[concepts/esemalk/avalonia-projekt-felepites]] — az Avalonia alkalmazások
  multi-projekt szerkezete és rétegei
- [[concepts/esemalk/avalonia-xaml-felulet]] — a deklaratív XAML felületleírás
  és a vezérlők
- [[concepts/esemalk/avalonia-mvvm-adatkotes]] — az MVVM architektúra és az
  adatkötés az Avaloniában
- [[subjects/esemalk]]
