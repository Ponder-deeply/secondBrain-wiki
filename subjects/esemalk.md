---
tags: [subject]
sources: []
derivation: unsourced
updated: 2026-09-13
---

# Eseményvezérelt alkalmazások (esemalk)

Az ELTE IK "Eseményvezérelt alkalmazások" kurzusa: a .NET platform és a C#
nyelv áttekintése, majd eseményvezérelt asztali alkalmazásfejlesztés (WinForms,
WPF, Avalonia UI) és a reaktív programozás.

## Tartalom

A kurzus a C# nyelvi alapok gyors átismétlésével indul (0. előadás), majd a
modell–nézet architektúrákra és a konkrét UI-keretrendszerekre tér rá.

## Fogalomlapok

### C# nyelvi alapok

- [[concepts/esemalk/csharp-dotnet-platform]] — a .NET platform felépítése,
  .NET Framework vs. .NET Core, .NET Standard
- [[concepts/esemalk/csharp-nyelv-jellemzoi]] — a C# nyelv jellemzői, Hello
  World, top level statements
- [[concepts/esemalk/csharp-nevterek]] — névterek és a `using` direktíva
- [[concepts/esemalk/csharp-tipusok]] — típuskategóriák, primitív típusok,
  típuskonverzió
- [[concepts/esemalk/csharp-valtozok-peldanyositas]] — változódeklaráció,
  `var`, `new`, `dynamic`, `const`, `readonly`
- [[concepts/esemalk/csharp-vezerlesi-szerkezetek]] — elágazások, ciklusok
- [[concepts/esemalk/csharp-osztalyok]] — osztályok, `struct` vs `class`,
  tagok, láthatóság
- [[concepts/esemalk/csharp-ertek-referencia-osztalyok]] — elemi (`struct`)
  és referencia (`class`) osztályok
- [[concepts/esemalk/csharp-osztaly-szerkezete]] — mezők, metódusok,
  tulajdonságok, események egy osztályban
- [[concepts/esemalk/csharp-tulajdonsagok]] — tulajdonságok (`property`),
  `get`/`set`/`init`
- [[concepts/esemalk/csharp-statikus-osztaly]] — statikus osztályok, mezők,
  tulajdonságok
- [[concepts/esemalk/csharp-felsorolasi-tipus]] — felsorolási típus (`enum`)
- [[concepts/esemalk/csharp-nullable-tipusok]] — nullable érték- és
  referenciatípusok
- [[concepts/esemalk/csharp-oroklodes]] — öröklődés, `virtual`/`override`,
  `abstract`, `sealed`, `is`/`as`
- [[concepts/esemalk/csharp-interfeszek]] — interfészek, többszörös
  öröklődés kiváltása
- [[concepts/esemalk/csharp-generikus-tipusok]] — generikus osztályok,
  metódusok, delegáltak
- [[concepts/esemalk/csharp-kivetelkezeles]] — kivételkezelés, `Exception`
- [[concepts/esemalk/csharp-linq]] — nyelvbe ágyazott lekérdezések (LINQ)
- [[concepts/esemalk/csharp-attributumok]] — attribútumok (metaadatok)
- [[concepts/esemalk/csharp-eloforditasi-direktivak]] — előfordítási
  direktívák
- [[concepts/esemalk/csharp-kifejezes-torzsu-tagok]] — kifejezés törzsű
  tagok (expression body)
- [[concepts/esemalk/csharp-megjegyzesek]] — megjegyzések és dokumentációs
  megjegyzések

### Architektúra és eseménykezelés

- [[concepts/esemalk/monolitikus-architektura]] — monolitikus architektúra
- [[concepts/esemalk/modell-nezet-architektura]] — modell/nézet (MV)
  architektúra
- [[concepts/esemalk/haromreteg-architektura]] — háromrétegű (nézet/modell/
  perzisztencia) architektúra
- [[concepts/esemalk/fuggoseg-befecskendezes]] — függőség-befecskendezés
  (dependency injection)
- [[concepts/esemalk/tictactoe-haromreteg-pelda]] — Tic-Tac-Toe példa
  háromrétegű architektúrában
- [[concepts/esemalk/stream-alapu-fajlkezeles]] — adatfolyam-alapú (Stream)
  fájlkezelés
- [[concepts/esemalk/idisposable-eroforras-felszabaditasa]] — erőforrások
  felszabadítása (`IDisposable`, `using`)
- [[concepts/esemalk/esemeny-letrehozasa-kivaltasa]] — saját esemény
  létrehozása és kiváltása C#-ban
- [[concepts/esemalk/billentyuzetkezeles-winforms]] — billentyűzetkezelés
  WinForms alkalmazásokban

### WinForms — statikus UI

- [[concepts/esemalk/winforms-vezerlok-alapjai]] — WinForms vezérlők
  alapjai, `Control` osztály, `System.Windows.Forms`
- [[concepts/esemalk/winforms-ablakok-felepitese]] — WinForms ablakok
  felépítése, `Form` osztály, `partial` osztály
- [[concepts/esemalk/vezerlo-esemenykezelo-tarsitas]] — vezérlők
  eseményeinek kezelése, `sender` paraméter
- [[concepts/esemalk/winforms-application-osztaly]] — az `Application`
  osztály, a főprogram és az `Application.Run(...)` indítás

### WinForms — dinamikus UI

- [[concepts/esemalk/winforms-dinamikus-vezerlok]] — vezérlők dinamikus
  (futásidejű) létrehozása és eltávolítása, `Controls.Add`, `Dispose`
- [[concepts/esemalk/winforms-elrendezok]] — méretezés és elrendezők
  (`AutoSize`, `Dock`, `FlowLayoutPanel`, `TableLayoutPanel`)
- [[concepts/esemalk/winforms-kepek-megjelenitese]] — képek megjelenítése
  (`Image`, `Bitmap`, `PictureBox`)
- [[concepts/esemalk/dotnet-eroforraskezeles]] — .NET erőforrások kezelése
  (content/embedded resource, `.resx`)
- [[concepts/esemalk/dotnet-fajlrendszer-kezeles]] — fájlrendszer-kezelés
  (`System.IO`: `File`, `Directory`, `Path`)

### WinForms — elemi grafika

- [[concepts/esemalk/winforms-grafika-alapok]] — a `Graphics` osztály,
  rajzoló műveletek, a rajzfelület megszerzése
- [[concepts/esemalk/winforms-szinek-ecsetek-tollak]] — `Color`, `Pen`,
  `Brush` típusok
- [[concepts/esemalk/winforms-rajzeszkoz-beallitasok]] — élsimítás,
  koordinátarendszer-transzformáció, állapotkezelés, vágás
- [[concepts/esemalk/winforms-eger-esemenyek]] — egérkezelés
  (`MouseDown`, `MouseMove`, `MouseUp`, `MouseWheel`, ...)
- [[concepts/esemalk/rajzolo-alkalmazas-tervezese]] — egy rajzolóalkalmazás
  tervezése és megvalósítása modell/nézet architektúrában
- [[concepts/esemalk/winforms-dupla-pufferezes]] — villogásmentes rajzolás
  `Bitmap` közbeiktatásával

### WinForms — architektúra és tesztelés

- [[concepts/esemalk/csharp-egysegteszt-keretrendszerek]] — MSTest, NUnit és
  xUnit egységteszt-keretrendszerek összevetése, Moq alapú mockolás
- [[concepts/esemalk/szerelvenyek-osztalykonyvtarak]] — szerelvények
  (assembly), osztálykönyvtárak, cross-platform osztálykönyvtárak és a .NET
  Standard
- [[concepts/esemalk/retegek-szerelvenyekre-bontasa]] — az MV rétegek
  szerelvényekre bontása perzisztencia interfész mögé rejtett
  adatkezeléssel, Tic-Tac-Toe példa
- [[concepts/esemalk/egysegtesztek-mstest]] — egységtesztek MSTest-tel
  (`TestClass`, `TestMethod`, `Assert`, `DataRow`, `ExpectedException`)
- [[concepts/esemalk/mock-objektumok]] — mock objektumok, manuális
  mockolás és a Moq keretrendszer

### Többszálú programozás C#-ban

- [[concepts/esemalk/folyamat-es-szal]] — a folyamat (`process`) és a szál
  (`thread`) fogalma
- [[concepts/esemalk/csharp-szal-letrehozasa-kezelese]] — a `Thread` típus,
  `Start`/`Join`/`Abort`, `ParameterizedThreadStart`, a típus korlátai
- [[concepts/esemalk/kritikus-szakasz-kolcsonos-kizaras]] — kritikus szakasz,
  kölcsönös kizárás, a szinkronizációs objektumok összehasonlítása
- [[concepts/esemalk/csharp-mutex]] — a `Mutex` típus
- [[concepts/esemalk/csharp-szemafor]] — a `Semaphore` típus
- [[concepts/esemalk/csharp-monitor-lock]] — a `Monitor` osztály és a `lock`
  utasítás
- [[concepts/esemalk/csharp-szalbiztos-gyujtemenyek]] — a
  `System.Collections.Concurrent` névtér szálbiztos gyűjteményei
- [[concepts/esemalk/csharp-atomi-tipusok-interlocked]] — atomi adattípusok
  és az `Interlocked` osztály
- [[concepts/esemalk/csharp-task-alapok]] — a taszk-alapú (`Task`) aszinkron
  programozás alapjai
- [[concepts/esemalk/csharp-async-await]] — az `async`/`await`
  konstrukció, elnevezési konvenciók, taszkba csomagolt szinkron műveletek
- [[concepts/esemalk/taszk-kivetelkezes-aggregateexception]] — kivételkezelés
  taszkokkal, `AggregateException`
- [[concepts/esemalk/taszk-megszakitasa-cancellationtoken]] — aszinkron
  tevékenységek megszakítása `CancellationTokenSource`/`CancellationToken`-nel
- [[concepts/esemalk/winforms-vezerlo-invoke-begininvoke]] — felületi
  vezérlők kezelése párhuzamos végrehajtás során, `Invoke`/`BeginInvoke`/
  `InvokeRequired`
- [[concepts/esemalk/winforms-fibonacci-parhuzamositas-pelda]] — WinForms
  párhuzamosítási példa: szinkron, taszkalapú aszinkron és eseményvezérelt,
  megszakítható Fibonacci-generátor
- [[concepts/esemalk/winforms-idozito-parhuzamositas]] — párhuzamosítás
  időzítővel (`System.Timers.Timer`), `BeginInvoke` a felület
  szinkronizálására
- [[concepts/esemalk/csharp-task-szinkronizacio]] — taszkok szinkronizálása:
  `SynchronizationContext`, `ConfigureAwait`, `TaskScheduler`,
  `ContinueWith`, `ConcurrentExclusiveSchedulerPair`

### WPF alapok

- [[concepts/esemalk/wpf-bevezetes]] — a WPF áttekintése: vektoros grafika,
  XAML, MVVM, Windows-only korlát
- [[concepts/esemalk/wpf-elemhierarchia]] — a WPF elemek osztályhierarchiája
  (`DispatcherObject`…`Panel`/`Control`/`Shape`), dispatcher/rendering szál
- [[concepts/esemalk/wpf-xaml-nyelv]] — a deklaratív XAML nyelv, fordítása
  BAML-re és IL-re
- [[concepts/esemalk/wpf-ablakok-alkalmazasok]] — `Window` és `Application`
  osztályok, felületi/háttérkód, `InitializeComponent`, kilépés-gomb példa
- [[concepts/esemalk/wpf-vezerlok-tulajdonsagai]] — a WPF vezérlők közös
  tulajdonságai (`Name`, `Resources`, `Template`, kinézet, méretezés, …)
- [[concepts/esemalk/wpf-vezerlok-tartalmazasa]] — `ContentControl` vs.
  `ItemsControl` tartalmazás
- [[concepts/esemalk/wpf-elrendezes-tulajdonsagok]] — igazítás, margó,
  méretezés, `ClipToBounds`, `Viewbox`
- [[concepts/esemalk/wpf-panelek]] — `Canvas`, `Grid`, `StackPanel`,
  `WrapPanel`, `DockPanel`, `ScrollViewer`
- [[concepts/esemalk/wpf-transzformaciok]] — `RotateTransform`,
  `ScaleTransform`, `TranslateTransform`, `SkewTransform`, `TransformGroup`
- [[concepts/esemalk/wpf-vezerlok-megjelenese]] — `Border`/`Background`/
  `Effect`/`Brush`/`Style`, logikai fa vs. vizuális fa, `ControlTemplate`
- [[concepts/esemalk/wpf-kepkezeles]] — `BitmapImage`, `WritableBitmap`,
  `Uri`-alapú erőforrás-hivatkozás
- [[concepts/esemalk/wpf-elemi-grafika]] — `DrawingContext`, `DrawingGroup`,
  `DrawingImage`
- [[concepts/esemalk/wpf-fuggosegi-tulajdonsagok]] — függőségi tulajdonság
  (dependency property), `DependencyObject.GetValue`/`SetValue`, csatolt
  tulajdonságok
- [[concepts/esemalk/wpf-tictactoe-pelda]] — Tic-Tac-Toe példa WPF
  felülettel

### WPF — erőforrások és stílusok

- [[concepts/esemalk/wpf-eroforrasok-alapjai]] — az erőforrás-fogalom
  általánosítása, `Resources` tulajdonság, `x:Key`/`StaticResource`
- [[concepts/esemalk/wpf-eroforrasok-fajlok]] — erőforrásfájlok
  (`ResourceDictionary`), megosztott stílus-/sablonkészlet több elem között
- [[concepts/esemalk/wpf-stilusok-alapjai]] — a `Style`/`Setter`, implicit
  és explicit stílusok, `TargetType`
- [[concepts/esemalk/wpf-eroforrasok-animaciok]] — animációk (`DoubleAnimation`,
  `ColorAnimation`, `ThicknessAnimation`), `Storyboard`, `From`/`To`/`Duration`,
  `KeyFrame`
- [[concepts/esemalk/wpf-stilus-triggerek]] — triggerek stílusban és
  sablonban (`EventTrigger`, `DataTrigger`, `Setter`, `BeginStoryboard`),
  megjelenítés-vezérlés nézetmodell-adat alapján
- [[concepts/esemalk/wpf-stilusok-dinamikus-felulet]] — stílusok dinamikus
  felületen (`ItemsControl`, `ItemContainerStyle`)
- [[concepts/esemalk/wpf-stilusok-pelda-szinracs]] — példa: dinamikus
  méretezhető színrács `ItemsControl`/`ItemContainerStyle`-lel
- [[concepts/esemalk/wpf-kornyezet-fuggosegkezeles]] — laza csatolás és
  függőség-befecskendezés az MVVM rétegei között, az alkalmazáskörnyezet
  (environment) mint IoC-komponens
- [[concepts/esemalk/wpf-idozites]] — `System.Timers.Timer` vs.
  `DispatcherTimer`, szálbiztos felületfrissítés `Dispatcher.BeginInvoke`-kal
- [[concepts/esemalk/wpf-tobbablakos-mvvm-pelda]] — vizsgatétel-generátor
  példa: egy nézetmodell, amely két ablakot (nézetet) szolgál ki
- [[concepts/esemalk/wpf-itemscontrol-elrendezes-dinamikus-mezok]] —
  `ItemsControl`/`ItemsPanel` testreszabása és a dinamikus mezők
  (`DynamicField`) mintája MVVM-ben

### WPF — architektúra (MVVM)

- [[concepts/esemalk/wpf-mvvm-alapok]] — a modell/nézet/nézetmodell (MVVM)
  architektúra: a nézet rétegződése, MV vs. MVVM, adatáramlás, megvalósítás
  eszközei
- [[concepts/esemalk/wpf-adatkotes-alapjai]] — az adatkötés (`Binding`)
  alapjai: cél/forrás, `Mode`, `UpdateSourceTrigger`, `DataContext`,
  tranzitivitás
- [[concepts/esemalk/wpf-adatkotes-gyujtemenyek-teljesfelulet]] — adatkötés
  gyűjteményekre (`ItemsSource`), elemsablonokra (`ItemTemplate`/
  `DataTemplate`) és a teljes ablakra
- [[concepts/esemalk/wpf-mvvm-inotifypropertychanged]] — adatkötés
  változáskövetéssel (`INotifyPropertyChanged`, `ObservableCollection`,
  `CallerMemberName`)
- [[concepts/esemalk/wpf-mvvm-parancsok-icommand]] — parancsok az MVVM
  architektúrában (`ICommand`, `Execute`/`CanExecute`, `CommandParameter`)
- [[concepts/esemalk/wpf-mvvm-delegatecommand]] — általános célú,
  újrafelhasználható parancs (`DelegateCommand`)
- [[concepts/esemalk/wpf-mvvm-parancs-vegrehajthatosaga]] — parancsok
  végrehajthatósága, `CanExecuteChanged`, `CommandManager.RequerySuggested`
- [[concepts/esemalk/wpf-mvvm-szamologep-pelda]] — számológép példa MVVM
  architektúrában (nézetmodell, modell, `DelegateCommand`, kötések)
- [[concepts/esemalk/wpf-mvvm-inputbindings]] — speciális parancskötések
  (`InputBindings`: `KeyBinding`, `MouseBinding`)
- [[concepts/esemalk/wpf-mvvm-egyedi-vezerlok]] — egyedi vezérlők
  létrehozása öröklődéssel vagy `UserControl`-lal
- [[concepts/esemalk/wpf-mvvm-tamogato-csomagok]] — MVVM-et támogató
  programcsomagok (MVVM Toolkit, Prism Library)

### AvaloniaUI alapok

- [[concepts/esemalk/avalonia-bevezetes]] — az Avalonia UI áttekintése:
  multi-platform architektúra, Skia-alapú rajzolás, MVVM ajánlott
- [[concepts/esemalk/avalonia-telepites-projekt-letrehozas]] — telepítés
  (`dotnet new install Avalonia.Templates`), új MVVM projekt létrehozása
- [[concepts/esemalk/avalonia-projekt-felepites]] — multi-projekt szerkezet,
  közös és platformspecifikus programegységek
- [[concepts/esemalk/avalonia-xaml-felulet]] — `.axaml` felületleírás,
  `UserControl`/`Window`, beépített vezérlők
- [[concepts/esemalk/avalonia-alkalmazas-tulajdonsagok-kihelyezes]] —
  alkalmazás leíró (`AndroidManifest.xml`, `Package.appxmanifest`,
  `Info.plist`) és kihelyezés
- [[concepts/esemalk/avalonia-szamologep-pelda]] — számológép példa
  Avalonia UI-ban
- [[concepts/esemalk/avalonia-mvvm-adatkotes]] — MVVM architektúra,
  `Binding`, `DataContext`, `x:Reference`, az `App` és az alkalmazás-
  életciklus szerinti nézetkiválasztás
- [[concepts/esemalk/avalonia-mvvm-toolkit]] — az MVVM Toolkit
  (`CommunityToolkit.Mvvm`): `ObservableObject`, `RelayCommand`,
  `[ObservableProperty]` kódgenerátor

### AvaloniaUI — haladó témák

- [[concepts/esemalk/avalonia-eletciklus-kezeles]] — alkalmazás életciklus
  kezelése (`OnFrameworkInitializationCompleted`, `Startup`/`Exit`)
- [[concepts/esemalk/avalonia-platformfuggetlen-perzisztencia]] —
  platformfüggetlen perzisztencia `System.IO`-val és
  `Environment.SpecialFolder`-rel
- [[concepts/esemalk/avalonia-dialogusablakok]] — dialógusablakok
  (`StorageProvider`, `OpenFilePickerAsync`, `SaveFilePickerAsync`,
  `TopLevel`)
- [[concepts/esemalk/avalonia-animaciok-atmenetek]] — animációk
  (`Animation`/`KeyFrame`) és átmenetek (`Transitions`)
- [[concepts/esemalk/avalonia-kezmozdulat-kezeles]] — kézmozdulat-kezelés
  (`GestureRecognizer`, `ScrollGestureRecognizer`, `PinchGestureRecognizer`,
  `PullGestureRecognizer`)
- [[concepts/esemalk/avalonia-meret-tajolas-kezeles]] — méret- és
  tájolás-kezelés mobil környezetben (`OnSizeChanged`, portré/tájkép)
- [[concepts/esemalk/avalonia-eszkozfuggo-viselkedes]] — eszközfüggő
  viselkedés (`OperatingSystem.IsAndroid`/`IsIOS`, `OnPlatform`)
- [[concepts/esemalk/avalonia-temak-stilusok]] — témák (`FluentTheme`,
  `SimpleTheme`, `Material.Avalonia`, `Classic.Avalonia`) és CSS-szerű
  szelektorok
- [[concepts/esemalk/avalonia-idozites]] — időzítés (`DispatcherTimer`,
  `System.Timers.Timer`, `Dispatcher.UIThread.InvokeAsync`)
- [[concepts/esemalk/avalonia-mobil-alkalmazaskornyezet-eletciklus]] —
  mobil alkalmazáskörnyezet (sandbox) és életciklus (futás alatt/
  felfüggesztve/leállítva, `IActivatableLifetime`)

### Lokalizáció

- [[concepts/esemalk/dotnet-lokalizacio-kulturak]] — .NET alkalmazások
  lokalizációja: `CultureInfo`, kultúra-specifikus `.resx` fájlok,
  `ResourceManager`
- [[concepts/esemalk/xaml-lokalizacio-x-static]] — lokalizált erőforrások
  megjelenítése WinForms tervezőn (`Localizable`/`Language`), illetve WPF/
  Avalonia XAML-ban (`x:Static`)

### Reaktív programozás

- [[concepts/esemalk/reaktiv-programozas-alapjai]] — a reaktív
  programozás fogalma: időben változó megfigyelhető adatfolyamok,
  aszinkron végrehajtás, ütemezők, operátorok
- [[concepts/esemalk/reaktiv-iterator-tervezesi-minta]] — a GoF Iterator
  tervezési minta, `IEnumerable<T>`/`IEnumerator<T>`
- [[concepts/esemalk/reaktiv-observer-tervezesi-minta]] — a GoF Observer
  tervezési minta, C# események mint Observer-megvalósítás
- [[concepts/esemalk/rx-observable-alapok]] — a ReactiveX könyvtár,
  `IObservable<T>`/`IObserver<T>`, `Observable.Create` és gyártó
  metódusok
- [[concepts/esemalk/rx-operatorok]] — Rx.NET operátorok: `Where`,
  `Throttle`, `Distinct`, `Select`, `Scan`, `Merge`, `GroupBy`
- [[concepts/esemalk/reaktiv-feliratkozas]] — feliratkozás megfigyelhető
  felsorolóra (`Subscribe`, `onNext`/`onError`/`onSuccess`)
- [[concepts/esemalk/reaktiv-szenzor-pelda]] — szimulált szenzoradat-folyam
  létrehozása és feldolgozása (`Interval`, `Where`, `Select`, `GroupBy`)
- [[concepts/esemalk/reaktiv-multicasting]] — multicasting (`Publish`,
  `Connect`, `RefCount`) és cold/hot observable
- [[concepts/esemalk/reaktiv-reactiveui]] — a ReactiveUI könyvtár és az
  Rx.NET integrációja WinForms/WPF/Avalonia UI-val
