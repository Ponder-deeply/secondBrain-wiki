---
tags: [concept, esemalk/avaloniaui-alapok]
sources: [elte_eva_ea09_avaloniaui.pdf]
derivation: source
updated: 2026-09-13
---

# Avalonia számológép példa

Egy egyszerű számológép-alkalmazás, amely a négy alapműveletet végzi el és
láthatóvá teszi a korábbi műveleteket, az Avalonia UI MVVM-alapú
felépítésének illusztrálására szolgál.

## Tartalom

A feladat: készítsünk egy egyszerű számológépet, amellyel a négy
alapműveletet végezhetjük el, illetve láthatjuk korábbi műveleteinket is.

- a **modell** (`CalculatorModel`) biztosítja a számológép funkcionalitást,
  ezt újrahasznosítjuk
- a **nézetben** (`MainView`) elhelyezünk egy rácsot, benne a beviteli
  mezőt (`TextBox`), a gombokat (`Button`), valamint a számítások listáját
  (`TextBlock`)
- a gombokhoz közös eseménykezelőt rendelünk (`ButtonClicked`), és a gomb
  szövege alapján döntünk a műveletről
- az esetleges hibákról figyelmeztető üzenetet küldünk a `MessageBox.Avalonia`
  NuGet csomag használatával

Ez a felépítés — közös modell, gombokhoz rendelt egységes eseménykezelő,
kivételek felhasználói visszajelzése — párhuzamba állítható a WPF-es
számológép példával, lásd [[concepts/esemalk/wpf-mvvm-szamologep-pelda]]; a
lényegi különbség, hogy a `MessageBox.Avalonia` egy külön NuGet csomag,
mivel az Avalonia keretrendszer önmagában nem tartalmaz beépített
üzenetdoboz-vezérlőt.

### MVVM Toolkit alapú változat

A feladat egy másik megvalósítása kifejezetten a nézetmodell kiemelésével,
teljes MVVM architektúrában valósítja meg a számológépet
(lásd [[concepts/esemalk/avalonia-mvvm-toolkit]]):

- a nézetmodell (`CalculatorViewModel`) tartalmazza az aktuális értéket
  (`NumberFieldValue`), a számítások listáját (`Calculations`) és a
  számítást parancs formájában (`CalculateCommand`)
- a számítási hibákkal kapcsolatosan eseményt küld (`ErrorOccured`)
- az alkalmazás (`App`) példányosítja és összeállítja az alkalmazás
  rétegeit, és kezeli a számítási hibák eseményeit

## Kapocs

- [[concepts/esemalk/wpf-mvvm-szamologep-pelda]] — a WPF-es számológép
  példa, amelynek felépítése analóg ezzel
- [[concepts/esemalk/avalonia-xaml-felulet]] — a nézet felépítéséhez
  használt vezérlők (`TextBox`, `Button`, `TextBlock`)
- [[concepts/esemalk/avalonia-mvvm-adatkotes]] — az adatkötés, amellyel a
  nézet a modellhez/nézetmodellhez kapcsolódik
- [[concepts/esemalk/avalonia-mvvm-toolkit]] — az MVVM Toolkit alapú
  nézetmodell-változat eszközei (`ObservableObject`, `RelayCommand`,
  `[ObservableProperty]`)
- [[subjects/esemalk]]
