---
tags: [concept, esemalk/wpf-eroforrasok-es-stilusok]
sources: [elte_eva_ea08_wpf_complex_resources.pdf]
derivation: source
updated: 2026-09-13
---

# Többablakos MVVM alkalmazás példa: vizsgatétel-generátor

Egy vizsgatétel-generáló alkalmazás példáján bemutatva, hogyan szolgálhat ki
egyetlen nézetmodell több ablakot (nézetet) MVVM architektúrában, és hogyan
tölti be az `App` a [[concepts/esemalk/wpf-kornyezet-fuggosegkezeles|környezet]]
szerepét.

## Tartalom

### A feladat

Készítsünk egy vizsgatétel generáló alkalmazást, amely ügyel arra, hogy a
vizsgázók közül ketten ne kapják ugyanazt a tételt.

### Rétegek és osztályok

- **Modell** (`ExamGeneratorModel`) valósítja meg a generálást, a tétel
  elfogadását/eldobását, valamint a történet tárolását; a rá mutató
  hivatkozás egy interfészen (`IExamGenerator`) keresztül történik —
  ugyanaz az absztrakció/megvalósítás minta, amit
  [[concepts/esemalk/wpf-kornyezet-fuggosegkezeles]] ismertet
- **Két nézet**: a főablak (`MainWindow`) és a beállítások ablak
  (`SettingWindow`)
- **Egy közös nézetmodell** (`ExamGeneratorViewModel`) szolgálja ki mindkét
  nézetet; ebbe fecskendezzük be a modellt

### A nézetmodell felelősségei

- tárolja a start/stop funkcióért, valamint a beállítások
  megnyitásáért/bezárásáért felelős [[concepts/esemalk/wpf-mvvm-parancsok-icommand|parancsokat]]
  (`StartStopCommand`, `OpenSettingsCommand`, `CloseSettingsCommand`, mind
  `DelegateCommand` típusú)
- kezeli a modell `NumberGenerated` eseményét, és frissíti a megjelenített
  számot
- egy listában (`History`, `ObservableCollection<HistoryItem>`) tárolja a
  kihúzott tételeket; a `HistoryItem` segédtípus tárolja az elem sorszámát
  (`Number`) és állapotát (`IsChecked`), ezeket a tulajdonságokat kötjük a
  nézetre — lásd
  [[concepts/esemalk/wpf-adatkotes-gyujtemenyek-teljesfelulet]]
- egy `ApplicationMessaged` eseményen (`ApplicationMessageEventArgs`:
  `Message`, `Type` — `MessageType` felsorolás `Information`/`Error`
  értékekkel) keresztül jelez az alkalmazás felé (pl. a környezetnek szánt
  üzenetek)

### Az alkalmazás (App) mint környezet

Az `App` felel az egyes rétegek példányosításáért, valamint a nézetmodell
eseményeinek kezeléséért:

```csharp
// App.xaml.cs
private void App_Startup(…) {
    _model = new ExamGeneratorModel(10, 0);
    _viewModel = new ExamGeneratorViewModel(_model);
    // a nézetmodell két nézetet is kiszolgál
    …
    _viewModel.OpenSettingsExecuted +=
        new EventHandler(ViewModel_OpenSettings);
    …
    _mainWindow = new MainWindow();
    _mainWindow.DataContext = _viewModel;
}
```

A beállítások ablakát a nézetmodell `OpenSettingsExecuted` eseménye nyitja
meg; az ablakot csak első alkalommal hozzuk létre (és ugyanazt a
nézetmodellt adjuk neki `DataContext`-ként), utána modálisan jelenítjük
meg:

```csharp
private void ViewModel_OpenSettings(…) {
    if (_settingsWindow == null) {
        // ha már egyszer létrehoztuk az ablakot, nem kell újra
        _settingsWindow = new SettingsWindow();
        _settingsWindow.DataContext = _ViewModel;
        // a beállításoknak is átadjuk a nézetmodellt
    }
    _settingsWindow.ShowDialog();
    // megjelenítjük dialógusként
}
```

## Kapocs

- [[concepts/esemalk/wpf-kornyezet-fuggosegkezeles]] — a környezet és a
  függőségkezelés általános elve, amit ez a példa illusztrál
- [[concepts/esemalk/wpf-mvvm-alapok]] — az MVVM architektúra alapjai
- [[concepts/esemalk/wpf-mvvm-parancsok-icommand]] — a nézetmodell
  parancsai (`ICommand`, `DelegateCommand`)
- [[concepts/esemalk/wpf-mvvm-inotifypropertychanged]] — a változáskövetés,
  amelyre a nézetmodell tulajdonságai (pl. a megjelenített szám) épülnek
- [[concepts/esemalk/wpf-adatkotes-gyujtemenyek-teljesfelulet]] — a
  `History` gyűjtemény és a teljes ablakra vonatkozó adatkötés
  (`DataContext`) mintája
- [[concepts/esemalk/wpf-ablakok-alkalmazasok]] — a `Window`/`Application`
  osztályok, amelyekre ez a többablakos példa épül
- [[subjects/esemalk]]
