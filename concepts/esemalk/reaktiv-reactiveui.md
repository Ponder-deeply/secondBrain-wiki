---
tags: [concept, esemalk/reaktiv-programozas]
sources: [elte_eva_ea11_reactive.pdf]
derivation: source
updated: 2026-09-13
---

# ReactiveUI

A ReactiveUI a .NET UI keretrendszerek (WinForms, WPF, Avalonia UI) reaktív programozási mintákkal való kiterjesztésére szolgáló könyvtár, amely az Rx.NET osztálykönyvtárra épül.

## Tartalom

Az asztali grafikus alkalmazások felületi eseményei és állapotváltozásai is kezelhetők reaktív módon. .NET keretrendszerben ezt a **ReactiveUI** könyvtár teszi lehetővé:

- könnyen integrálható, mivel Windows Forms, Windows Presentation Foundation és Avalonia UI felületű alkalmazásokhoz is elég 1-1 NuGet csomagot a projekthez adni
- a ReactiveUI keretrendszer az **Rx.NET** osztálykönyvtárra épül

MVVM architektúra esetén a nézetmodell megfigyelhető tulajdonságainak (`INotifyPropertyChanged` interfész) változása egy megfigyelhető felsorolóként (observable) is értelmezhető.

Hasonló szemlélettel a parancsok (`ICommand` interfész) végrehajthatósága (`CanExecute`) is tekinthető egy logikai értékeket felsoroló objektumnak, amely változásairól eseményeket küld (`CanExecuteChanged`), azaz megfigyelhető.

## Kapocs

- [[concepts/esemalk/wpf-mvvm-inotifypropertychanged]] — az `INotifyPropertyChanged` interfész hagyományos (nem reaktív) használata
- [[concepts/esemalk/wpf-mvvm-parancsok-icommand]] — az `ICommand` interfész és a `CanExecute`/`CanExecuteChanged` pár
- [[concepts/esemalk/reaktiv-feliratkozas]] — a `Subscribe()` alapjai az Rx.NET-ben, amelyre a ReactiveUI épül
- [[subjects/esemalk]] — a kurzus áttekintése
