---
tags: [concept]
sources: [elte_eva_ea09_avaloniaui.pdf]
derivation: source
updated: 2026-09-13
---

# Avalonia projekt felépítése

Egy Avalonia UI alkalmazás megoldása (solution) multi-projekt szerkezetű: egy
közös, platformfüggetlen kódbázis és az egyes célplatformokhoz tartozó,
végrehajtható binárist eredményező projektek.

## Tartalom

### Multi-projekt szerkezet

- egy **.NET Class Library** projekt tartalmazza a cross-platform kódbázist
  (modell, nézetmodell, nézetek, `App.axaml`)
- **platformfüggő projektek** (pl. `MyApp.Android`, `MyApp.Desktop`)
  tartalmazzák a platformspecifikus kódrészeket, és ezek eredményeznek
  végrehajtható binárist

A közös projektben jellemző mappák: `Assets`, `ViewModels`, `Views`, valamint
az `App.axaml` alkalmazásleíró fájl.

### Az alkalmazás rétegei

Az Avalonia UI alkalmazások közös programegységei (osztálykönyvtárai)
tartalmazzák:

- a **modellt**, amely az üzleti logikát valósítja meg, szokványos eszközök
  segítségével felépítve
- a **nézetmodellt**, amelyet az alapvető eszközök (`ICommand`,
  `INotifyPropertyChanged`, stb.) segítségével építünk fel — lásd
  [[concepts/esemalk/avalonia-mvvm-adatkotes]]
- a **nézetet**, amelyet XAML alapon írunk le, adat- és parancskötés
  (`Binding`) segítségével kapcsolva a nézetmodellhez
- az **alkalmazás vezérlését** (`App`), amely meghatározza a közös
  viselkedést minden platformon
- a **cross-platform perzisztenciát**, vagy — egyedi perzisztencia esetén —
  annak interfészét, amelynek megvalósítása platformonként eltérhet

A közös funkcionalitást *.NET Standard Library* segítségével valósíthatjuk
meg; a közös programegységek is felruházhatók platformspecifikus
jellemzőkkel, kondicionális fordítással vagy a platform futásidejű
vizsgálatával. A platformspecifikus programegységek (Desktop, Android, iOS,
WebAssembly) tovább bővíthetik a közös funkcionalitást: tartalmazhatnak
egyedi perzisztencia-megvalósítást (mivel az adattárolás módja
platformonként eltér), és tartalmazhatnak speciális, csak az adott
platformon elérhető nézetbeli elemeket, illetve lehetőséget a nézet
adaptálására.

## Kapocs

- [[concepts/esemalk/avalonia-bevezetes]] — az Avalonia UI architektúrája
- [[concepts/esemalk/avalonia-telepites-projekt-letrehozas]] — a projekt
  létrehozása, amelynek eredménye ez a szerkezet
- [[concepts/esemalk/avalonia-xaml-felulet]] — a nézet réteg XAML alapú
  felépítése
- [[concepts/esemalk/avalonia-mvvm-adatkotes]] — a nézetmodell réteg és az
  adatkötés
- [[concepts/esemalk/szerelvenyek-osztalykonyvtarak]] — a szerelvények és
  cross-platform osztálykönyvtárak, .NET Standard
- [[subjects/esemalk]]
