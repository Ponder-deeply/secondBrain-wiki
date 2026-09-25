---
tags: [concept, esemalk/wpf-alapok]
sources: [elte_eva_ea06_wpf_basics.pdf]
derivation: source
updated: 2026-09-13
---

# WPF ablakok és alkalmazások

A WPF-ben az ablakok a `Window` osztály leszármazottai, amelyek parciális
osztályként rendelkeznek felületi kóddal (`.xaml`) és háttérkóddal
(`.xaml.cs`); az alkalmazás egészét egy `Application` leszármazott vezérli.

## Tartalom

### Ablakok

A felületi kódban adjuk meg a deklaratív leírást:

```xml
<Window x:Class="MyApplication.MyWindow" …
    Title="My Window" Height="350" Width="525">
    <!-- megadjuk címét és méreteit -->
    <Grid> … </Grid>
    <!-- rács a további elemeknek -->
</Window>
```

- meg kell adnunk az osztálynevet (`x:Class`), valamint a felhasznált
  sémákat és névtereket
- az ablakba csak egy elem helyezhető (ez általában rács vagy vászon, amely
  további elemeket tartalmaz) — vö.
  [[concepts/esemalk/wpf-elemhierarchia]]
- a háttérkódban írhatjuk meg a további tevékenységeket, pl.
  eseménykezelőket
- az eseménykezelő-társítás történhet a háttérkódban (`+=`), illetve a
  felületi kódban is:

```xml
<!-- MyWindow.xaml: -->
<Button Name="myButton" Click="myButton_Click">
```
```csharp
// MyWindow.xaml.cs:
void myButton_Click(…) { … }
```

Minden felületi kódot a konstruktor futtat le az `InitializeComponent()`
művelet segítségével:

```csharp
partial class MyWindow { // háttérkód osztálya
    public MyWindow() {
        InitializeComponent(); …
    }
}
```

### Alkalmazások

Az alkalmazást egy `Application` leszármazott osztály vezérli, amely szintén
megadható XAML segítségével:

```xml
<Application x:Class="MyApplication.App" …
    StartupUri="MainWindow.xaml">
    <!-- megadjuk a kezdőablakot -->
</Application>
```

Kódból megvalósítva az alkalmazást a főprogramban paraméterezzük fel, és
implementáljuk az indítás (`Application_Startup`) és befejezés
(`Application_Exit`) eseménykezelését:

```csharp
class SimpleApplication : Application {
    public static void Main() {
        SimpleApplication app = new SimpleApplication();
        app.Startup += Application_Startup;
        app.Run(); // futtatás
    }
    static void Application_Startup(object sender, StartupEventArgs e) {
        MainWindow window = new MainWindow();
        window.Show(); // megjelenítjük az ablakot
    }
}
```

### Példa: egyszerű ablak kilépés gombbal

Egy egyszerű program, amelyben egy ablak közepére helyezünk egy kilépésre
szolgáló gombot, kétféleképp készíthető el:

- **deklaratív leírással** — csak az eseménykezelő függvényt kell megírni a
  kódban, amelynek feladata az ablak bezárása (`Close`)
- **tisztán kódból** — felparaméterezzük az alkalmazást a főprogramban, és
  megvalósítjuk az indítás/befejezés eseménykezelését, továbbá a saját ablak
  osztály (`MainWindow`) konstruktorában definiáljuk a megjelenést

Deklaratív változat (`MainWindow.xaml`):

```xml
<Window x:Class="ELTE.SimpleWindowByDesign.MainWindow" …
    Title="Egyszerű ablak" Height="200" Width="300"
    WindowStartupLocation="CenterScreen">
    <Grid>
        <Button Name="_ExitButton" Content="Kilépés"
            HorizontalAlignment="Center"
            VerticalAlignment="Center"
            Height="25" Width="100"
            Click="ExitButton_Click" />
    </Grid>
</Window>
```

Tisztán kódból történő változat (`MainWindow.cs`): a `MainWindow` osztály a
`Window`-ból származik, konstruktorában állítja be a méreteket, hozza létre
és konfigurálja a gombot (`_exitButton = new Button(); …`), majd
`AddChild(_exitButton)` hívással veszi fel az ablakra. A `SimpleApplication`
osztály (`Application`-ből származva) a `Main()`-ben feliratkozik a
`Startup` eseményre, és a kezelőben példányosítja, majd megjeleníti
(`Show()`) a `MainWindow`-t.

## Kapocs

- [[concepts/esemalk/wpf-xaml-nyelv]] — a felületi kód (`.xaml`) mögötti
  deklaratív nyelv és fordítása
- [[concepts/esemalk/wpf-elemhierarchia]] — az ablakba helyezhető elemek
  (`Grid`, `Panel`, `Control`) hierarchiája
- [[concepts/esemalk/winforms-ablakok-felepitese]] — a WinForms `Form`
  osztálya és parciális osztály felépítése, amelynek a WPF `Window` a
  megfelelője
- [[concepts/esemalk/vezerlo-esemenykezelo-tarsitas]] — a WinForms-beli
  eseménykezelő-társítás, amelynek WPF-változata itt a `Click=` attribútum
  illetve a háttérkódbeli `+=`
- [[subjects/esemalk]]
