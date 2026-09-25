---
tags: [concept, esemalk/wpf-alapok]
sources: [elte_eva_ea06_wpf_basics.pdf]
derivation: source
updated: 2026-09-13
---

# WPF bevezetés

A *Windows Presentation Foundation* (WPF) a .NET környezet vektoros alapú
grafikus felületi rendszere, a WinForms utódja asztali alkalmazások
fejlesztésére.

## Tartalom

A WPF a WinForms-hoz képest alapjaiban más architektúrára épül:

- **vektoros grafika**: az elemek nem pixelalapú, hanem vektoros
  megjelenítésűek, ami lehetővé teszi a 3D grafikus kártyák kihasználását
  (`Direct3D`)
- **testreszabhatóság**: jóval nagyobb szabadságot ad a megjelenítés és a
  stílusok átdefiniálására, a megjelenítési tulajdonságok erőforrás-alapú
  tárolásával
- **deklaratív felületleírás**: a felület XAML nyelven írható le (lásd
  [[concepts/esemalk/wpf-xaml-nyelv]])
- **megjelenés/vezérlés szétválasztása**: a WPF függetleníti a megjelenést a
  vezérléstől, ami jelentősen javítja az alkalmazás architektúráját (MVVM
  minta)
- **hátránya**: csak Windows rendszerekre érhető el, szemben pl. az Avalonia
  UI-jal

A WPF futási modellje is összetettebb a WinForms-nál: a kirajzolást külön szál
(*rendering thread*) végzi az elemkezeléstől (*dispatcher thread*), utóbbi egy
prioritásos üzenetciklussal kezeli az elemeket (`DispatcherObject`). Ennek az
elemhierarchiának a részleteit lásd [[concepts/esemalk/wpf-elemhierarchia]].

## Kapocs

- [[concepts/esemalk/wpf-elemhierarchia]] — a WPF elemek osztályhierarchiája
  és a dispatcher/rendering szál architektúrája
- [[concepts/esemalk/wpf-xaml-nyelv]] — a deklaratív felületleíró nyelv
- [[concepts/esemalk/winforms-vezerlok-alapjai]] — a WinForms vezérlőmodell,
  amelynek a WPF a továbbfejlesztése
- [[subjects/esemalk]]
