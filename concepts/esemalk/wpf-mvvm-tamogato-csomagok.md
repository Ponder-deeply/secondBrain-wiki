---
tags: [concept, esemalk/wpf-architektura]
sources: [elte_eva_ea07_wpf_architecture.pdf]
derivation: source
updated: 2026-09-13
---

# MVVM-et támogató programcsomagok

A .NET nyelvi könyvtárában elérhető alapvető MVVM-konstrukciók
(interfészek) önmagukban nem elegendőek a hatékony, gyors fejlesztéshez,
ezért erre a célra külön programcsomagok terjedtek el.

## Tartalom

A nyelvi könyvtár csak interfészeket biztosít (pl.
`INotifyPropertyChanged`, `ICommand`), ősosztályokat és gyűjtőosztályokat
nem — ezeket a fejlesztőnek magának kell megírnia, vagy külön csomagra kell
támaszkodnia. Két elterjedt csomag az MVVM alapú fejlesztés
megtámogatására:

- **MVVM Toolkit**: a *Microsoft .NET Community Toolkit* része, támogatja
  az MVVM architektúrát, a többrétegű modellt, a komponensek közötti
  üzenetküldést, valamint az alkalmazáskörnyezet kialakítását (korábbi
  nevén *MVVM Light Toolkit*);
- **Prism Library**: modul alapú fejlesztést támogat, az MVVM
  architektúrákat, valamint nézet-dekompozíciót és -cserét tesz lehetővé.

## Kapocs

- [[concepts/esemalk/wpf-mvvm-parancs-vegrehajthatosaga]] — az
  `ICommand`-ra épülő parancsminta, amelyet ezek a csomagok kész
  osztályokkal (pl. relay/delegate command) váltanak ki
- [[concepts/esemalk/wpf-mvvm-szamologep-pelda]] — a kézzel megírt
  `DelegateCommand`, amelynek kiváltására ezek a csomagok valók
- [[concepts/esemalk/modell-nezet-architektura]] — a modell/nézet
  architektúra, amelynek MVVM-változatát ezek a csomagok támogatják
- [[concepts/esemalk/fuggoseg-befecskendezes]] — a modul alapú fejlesztés
  (pl. Prism) gyakran függőség-befecskendezéssel párosul
