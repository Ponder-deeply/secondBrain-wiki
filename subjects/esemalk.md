---
tags: [subject]
sources: [elte_eva_ea01_bevezetes.pdf, esemalk-canvas-beadando-feladatok.md, esemalk-canvas-tanmenet.md]
derivation: source
math: 0
updated: 2026-10-21
---

# Eseményvezérelt alkalmazások (esemalk)

Az ELTE IK "Eseményvezérelt alkalmazások" kurzusa (Dr. Cserép Máté): a C# nyelv
és a .NET platform mélyebb elsajátítása, majd grafikus felületű,
eseményvezérelt alkalmazások fejlesztése három környezetben (WinForms, WPF,
Avalonia UI), rétegzett architektúrákkal, adatkötéssel és aszinkron
tevékenységekkel; a kurzus a reaktív programozással és a lokalizációval zárul.

## Tartalom

A kurzus a C# nyelvi alapok gyors átismétlésével indul (0. előadás), majd
környezetenként halad: WinForms (1–5. előadás: statikus és dinamikus felület,
modell/nézet és háromrétegű architektúra, tesztelés, többszálúság), WPF
(6–8. előadás: XAML, MVVM, erőforrások és stílusok), Avalonia UI (9–10.
előadás: többplatformos asztali és mobil alkalmazások), végül reaktív
programozás (11.) és lokalizáció (12.). A fogalomlapok alább ebben a
sorrendben, előadásonként szerepelnek.

## Vizsga

A számonkérés (1. előadás, *Számonkérés* és *Értékelés* diák, 2026/27 ősz)
összevont jegyet ad (5 kredit). Előfeltétel: mindkét beadandó időben leadva és
elfogadva, és minden zárthelyi eredményes.

- **Beadandók** — dokumentációból és programból álló, egyénileg kiosztott
  feladat; *ugyanazt* a feladatot kell két környezetben megvalósítani:
  WinForms (6. gyakorlat), majd Avalonia UI asztali és mobil alkalmazás
  (13. gyakorlat), utóbbi nézetmodellel. Határidőre leadva és elfogadva
  3 pont; ha funkcionálisan teljes, de hibás, egy hét haladékkal újra
  beadható, de akkor csak 1 pontot ér. Ami a határidőre nincs leadva, nem
  teljes, vagy a póthatáridőre sincs javítva, nem teljesített, és a gyakorlati
  jegy megtagadásra kerül. A dokumentáció PDF: UML használati eset- és
  osztálydiagram, tesztesetek, kódrészlet és képernyőkép nélkül. Leadás a
  TMS-ben, automatikus ellenőrzéssel (fordítás, statikus analízis), majd
  személyes védés.
- **Gyakorlati zárthelyik** — több részfeladatból álló feladat, ötfokozatú
  értékeléssel: GYZH1 félévközi, tervezetten a 9. gyakorlaton, 90 perc,
  Windows Forms; GYZH2 félév végi, tervezetten az 1. vizsgahéten, 150 perc,
  WPF. Írott, nyomtatott segédanyag, a hivatalos C#/.NET referencia és a
  kurzus mintaprogramjai használhatók; internet és generatív AI nem.
- **Elméleti zárthelyi (EZH)** — feleletválasztós kvíz a félév végi gyakorlati
  zh-hoz kapcsolva: 30 kérdés, 30 perc, segédeszköz nélkül; 27–30 jeles,
  24–26 jó, 21–23 közepes, 18–20 elégséges, 0–17 elégtelen.
- **Pótlás** — az egyik gyakorlati zh és az elméleti zh egyszer pótolható /
  javítható; ha mindkét gyakorlati zh elégtelen, gyakorlati utóvizsga tehető
  (legfeljebb közepes jegyért).
- **Jegy**: $B_1 + B_2 + 2 \cdot \text{GYZH}_1 + 2 \cdot \text{GYZH}_2 + \text{EZH}$
  pont; 12–16 elégséges, 17–20 közepes, 21–25 jó, 26–31 jeles.

A mintafeladatok és a beadandók anyagai:
[[concepts/esemalk/zh-mintafeladatok]] (a hat géptermi minta-zh),
[[concepts/esemalk/beadando-2-avalonia-feladatkiiras]],
[[concepts/esemalk/beadando-dokumentacio-sudoku-minta]] és
[[concepts/esemalk/beadando-statikus-analizis]]. Mintateszt az elméleti zh-hoz
nincs a vaultban.

| # | Kérdés / témakör | Lap(ok) |
|---|---|---|
| B1 | WinForms alkalmazás: nézet, modell, perzisztencia rétegek | [[concepts/esemalk/modell-nezet-architektura]], [[concepts/esemalk/haromreteg-architektura]], [[concepts/esemalk/tictactoe-haromreteg-pelda]], [[concepts/esemalk/retegek-szerelvenyekre-bontasa]], [[concepts/esemalk/winforms-dinamikus-vezerlok]], [[concepts/esemalk/stream-alapu-fajlkezeles]], [[concepts/esemalk/egysegtesztek-mstest]] |
| B2 | Avalonia UI asztali és mobil alkalmazás: nézet, nézetmodell, modell, perzisztencia | [[concepts/esemalk/avalonia-projekt-felepites]], [[concepts/esemalk/avalonia-mvvm-adatkotes]], [[concepts/esemalk/avalonia-mvvm-toolkit]], [[concepts/esemalk/avalonia-platformfuggetlen-perzisztencia]], [[concepts/esemalk/avalonia-mobil-alkalmazaskornyezet-eletciklus]], [[concepts/esemalk/avalonia-meret-tajolas-kezeles]] |
| B1–2 | Időzítés és felületfrissítés háttérszálról (játékjellegű feladatokhoz) | [[concepts/esemalk/winforms-idozito-parhuzamositas]], [[concepts/esemalk/wpf-idozites]], [[concepts/esemalk/avalonia-idozites]], [[concepts/esemalk/csharp-async-await]] |
| GYZH1 | Gyakorlati feladat Windows Formsban (90 perc, több részfeladat) | a B1 lapjai; [[concepts/esemalk/zh-mintafeladatok]] |
| GYZH2 | Gyakorlati feladat WPF-ben, MVVM (150 perc, több részfeladat) | [[concepts/esemalk/wpf-mvvm-alapok]], [[concepts/esemalk/wpf-adatkotes-alapjai]], [[concepts/esemalk/wpf-mvvm-inotifypropertychanged]], [[concepts/esemalk/wpf-mvvm-delegatecommand]], [[concepts/esemalk/wpf-itemscontrol-elrendezes-dinamikus-mezok]], [[concepts/esemalk/wpf-kornyezet-fuggosegkezeles]], [[concepts/esemalk/wpf-tictactoe-pelda]]; [[concepts/esemalk/zh-mintafeladatok]] |
| EZH | Elméleti kvíz (30 kérdés, 30 perc) — a teljes előadásanyag | az alábbi teljes lista; mintateszt — *(nincs lap)* |

## Fogalomlapok

### 0. előadás — C# nyelvi összefoglaló

- [[concepts/esemalk/csharp-dotnet-platform]] — a .NET platform felépítése,
  .NET Framework vs. .NET Core, .NET Standard
- [[concepts/esemalk/csharp-nyelv-jellemzoi]] — a C# nyelv jellemzői, Hello
  World, top level statements, névterek, vezérlési szerkezetek
- [[concepts/esemalk/csharp-tipusok]] — típuskategóriák, primitív típusok,
  típuskonverzió, változók, `var`/`new`/`dynamic`/`const`/`readonly`
- [[concepts/esemalk/csharp-osztaly-szerkezete]] — az osztály fogalma, tagok,
  láthatóság, mezők és metódusok, statikus osztályok és tagok
- [[concepts/esemalk/csharp-ertek-referencia-osztalyok]] — elemi (`struct`)
  és referencia (`class`) osztályok, felsorolási típus (`enum`)
- [[concepts/esemalk/csharp-tulajdonsagok]] — tulajdonságok (`property`),
  `get`/`set`/`init`
- [[concepts/esemalk/csharp-nullable-tipusok]] — nullable érték- és
  referenciatípusok
- [[concepts/esemalk/csharp-oroklodes]] — öröklődés, `virtual`/`override`,
  `abstract`, `sealed`, `is`/`as`, interfészek
- [[concepts/esemalk/csharp-generikus-tipusok]] — generikus osztályok,
  metódusok, delegáltak
- [[concepts/esemalk/csharp-kivetelkezeles]] — kivételkezelés, `Exception`
- [[concepts/esemalk/csharp-linq]] — nyelvbe ágyazott lekérdezések (LINQ)
- [[concepts/esemalk/csharp-kifejezes-torzsu-tagok]] — kifejezés törzsű
  tagok (expression body)
- [[concepts/esemalk/csharp-megjegyzesek]] — megjegyzések, dokumentációs
  megjegyzések, előfordítási direktívák, régiók, attribútumok

### 1. előadás — WinForms: statikus felület

- [[concepts/esemalk/winforms-vezerlok-alapjai]] — WinForms vezérlők
  alapjai, `Control` osztály, `System.Windows.Forms`
- [[concepts/esemalk/winforms-ablakok-felepitese]] — WinForms ablakok
  felépítése, `Form` osztály, `partial` osztály
- [[concepts/esemalk/vezerlo-esemenykezelo-tarsitas]] — vezérlők
  eseményeinek kezelése, `sender` paraméter
- [[concepts/esemalk/winforms-application-osztaly]] — az `Application`
  osztály, a főprogram és az `Application.Run(...)` indítás

### 2. előadás — WinForms: modell/nézet architektúra

- [[concepts/esemalk/modell-nezet-architektura]] — a monolitikus architektúra
  korlátai és a modell/nézet (MV) felbontás
- [[concepts/esemalk/esemeny-letrehozasa-kivaltasa]] — saját esemény
  létrehozása és kiváltása C#-ban
- [[concepts/esemalk/billentyuzetkezeles-winforms]] — billentyűzetkezelés
  WinForms alkalmazásokban

### 3. előadás — WinForms: dinamikus felület és elemi grafika

- [[concepts/esemalk/winforms-dinamikus-vezerlok]] — vezérlők dinamikus
  (futásidejű) létrehozása és eltávolítása, `Controls.Add`, `Dispose`
- [[concepts/esemalk/winforms-elrendezok]] — méretezés és elrendezők
  (`AutoSize`, `Dock`, `FlowLayoutPanel`, `TableLayoutPanel`)
- [[concepts/esemalk/winforms-kepek-megjelenitese]] — képek megjelenítése
  (`Image`, `Bitmap`, `PictureBox`), erőforrások (content/embedded, `.resx`)
- [[concepts/esemalk/winforms-grafika-alapok]] — a `Graphics` osztály,
  rajzoló műveletek, élsimítás, transzformáció, vágás
- [[concepts/esemalk/winforms-szinek-ecsetek-tollak]] — `Color`, `Pen`,
  `Brush` típusok
- [[concepts/esemalk/winforms-eger-esemenyek]] — egérkezelés
  (`MouseDown`, `MouseMove`, `MouseUp`, `MouseWheel`, ...)
- [[concepts/esemalk/rajzolo-alkalmazas-tervezese]] — egy rajzolóalkalmazás
  tervezése és megvalósítása modell/nézet architektúrában
- [[concepts/esemalk/winforms-dupla-pufferezes]] — villogásmentes rajzolás
  `Bitmap` közbeiktatásával

### 4. előadás — WinForms: architektúra és tesztelés

- [[concepts/esemalk/haromreteg-architektura]] — háromrétegű (nézet/modell/
  perzisztencia) architektúra
- [[concepts/esemalk/stream-alapu-fajlkezeles]] — fájlrendszer-műveletek
  (`File`, `Directory`, `Path`) és adatfolyam-alapú (`Stream`) fájlkezelés
- [[concepts/esemalk/idisposable-eroforras-felszabaditasa]] — erőforrások
  felszabadítása (`IDisposable`, `using`)
- [[concepts/esemalk/fuggoseg-befecskendezes]] — függőség-befecskendezés
  (dependency injection)
- [[concepts/esemalk/tictactoe-haromreteg-pelda]] — Tic-Tac-Toe példa
  háromrétegű architektúrában
- [[concepts/esemalk/szerelvenyek-osztalykonyvtarak]] — szerelvények
  (assembly), osztálykönyvtárak, .NET Standard
- [[concepts/esemalk/retegek-szerelvenyekre-bontasa]] — az MV rétegek
  szerelvényekre bontása, perzisztencia interfész mögött
- [[concepts/esemalk/egysegtesztek-mstest]] — egységtesztek MSTest-tel
  (`TestClass`, `TestMethod`, `Assert`, `DataRow`, `ExpectedException`)
- [[concepts/esemalk/csharp-egysegteszt-keretrendszerek]] — MSTest, NUnit és
  xUnit összevetése
- [[concepts/esemalk/mock-objektumok]] — mock objektumok, manuális
  mockolás és a Moq keretrendszer

### 5. előadás — Többszálú alkalmazások

- [[concepts/esemalk/folyamat-es-szal]] — a folyamat (`process`) és a szál
  (`thread`) fogalma
- [[concepts/esemalk/csharp-szal-letrehozasa-kezelese]] — a `Thread` típus,
  `Start`/`Join`/`Abort`, `ParameterizedThreadStart`
- [[concepts/esemalk/kritikus-szakasz-kolcsonos-kizaras]] — kritikus szakasz,
  kölcsönös kizárás, `Mutex`, `Semaphore`, `Monitor`/`lock`
- [[concepts/esemalk/csharp-atomi-tipusok-interlocked]] — atomi adattípusok,
  az `Interlocked` osztály, szálbiztos gyűjtemények
- [[concepts/esemalk/csharp-task-alapok]] — a taszk-alapú (`Task`) aszinkron
  programozás alapjai
- [[concepts/esemalk/csharp-async-await]] — az `async`/`await`
  konstrukció, elnevezési konvenciók
- [[concepts/esemalk/taszk-kivetelkezes-aggregateexception]] — kivételkezelés
  taszkokkal, `AggregateException`
- [[concepts/esemalk/taszk-megszakitasa-cancellationtoken]] — megszakítás
  `CancellationTokenSource`/`CancellationToken`-nel
- [[concepts/esemalk/csharp-task-szinkronizacio]] — `SynchronizationContext`,
  `ConfigureAwait`, `TaskScheduler`, `ContinueWith`
- [[concepts/esemalk/winforms-vezerlo-invoke-begininvoke]] — felületi
  vezérlők kezelése párhuzamos végrehajtás során, `Invoke`/`BeginInvoke`
- [[concepts/esemalk/winforms-idozito-parhuzamositas]] — párhuzamosítás
  időzítővel (`System.Timers.Timer`)
- [[concepts/esemalk/winforms-fibonacci-parhuzamositas-pelda]] — szinkron,
  taszkalapú és megszakítható Fibonacci-generátor példa

### 6. előadás — WPF alapok

- [[concepts/esemalk/wpf-bevezetes]] — a WPF áttekintése: vektoros grafika,
  XAML, MVVM, Windows-only korlát
- [[concepts/esemalk/wpf-elemhierarchia]] — a WPF elemek osztályhierarchiája,
  dispatcher/rendering szál
- [[concepts/esemalk/wpf-xaml-nyelv]] — a deklaratív XAML nyelv, fordítása
  BAML-re és IL-re
- [[concepts/esemalk/wpf-ablakok-alkalmazasok]] — `Window` és `Application`,
  felületi/háttérkód, `InitializeComponent`
- [[concepts/esemalk/wpf-vezerlok-tulajdonsagai]] — a vezérlők közös
  tulajdonságai, `ContentControl` vs. `ItemsControl` tartalmazás
- [[concepts/esemalk/wpf-panelek]] — elrendezési tulajdonságok (igazítás,
  margó, `Viewbox`) és panelek (`Canvas`, `Grid`, `StackPanel`, …)
- [[concepts/esemalk/wpf-vezerlok-megjelenese]] — ecsetek, stílus, logikai
  és vizuális fa, `ControlTemplate`, transzformációk
- [[concepts/esemalk/wpf-elemi-grafika]] — `BitmapImage`/`WritableBitmap`,
  `DrawingContext`/`DrawingGroup`/`DrawingImage`
- [[concepts/esemalk/wpf-fuggosegi-tulajdonsagok]] — függőségi és csatolt
  tulajdonságok, `GetValue`/`SetValue`
- [[concepts/esemalk/wpf-tictactoe-pelda]] — Tic-Tac-Toe példa WPF
  felülettel

### 7. előadás — WPF architektúra (MVVM)

- [[concepts/esemalk/wpf-mvvm-alapok]] — az MVVM architektúra: a nézet
  rétegződése, MV vs. MVVM, adatáramlás
- [[concepts/esemalk/wpf-adatkotes-alapjai]] — az adatkötés (`Binding`):
  cél/forrás, `Mode`, `UpdateSourceTrigger`, `DataContext`
- [[concepts/esemalk/wpf-adatkotes-gyujtemenyek-teljesfelulet]] — kötés
  gyűjteményekre (`ItemsSource`), `DataTemplate`, teljes ablakra
- [[concepts/esemalk/wpf-mvvm-inotifypropertychanged]] — változáskövetés
  (`INotifyPropertyChanged`, `ObservableCollection`, `CallerMemberName`)
- [[concepts/esemalk/wpf-mvvm-parancsok-icommand]] — parancsok (`ICommand`,
  `CommandParameter`), billentyű- és egérkötések (`InputBindings`)
- [[concepts/esemalk/wpf-mvvm-delegatecommand]] — általános célú,
  újrafelhasználható parancs (`DelegateCommand`)
- [[concepts/esemalk/wpf-mvvm-parancs-vegrehajthatosaga]] — `CanExecute`,
  `CanExecuteChanged`, `CommandManager.RequerySuggested`
- [[concepts/esemalk/wpf-mvvm-szamologep-pelda]] — számológép példa MVVM
  architektúrában
- [[concepts/esemalk/wpf-mvvm-egyedi-vezerlok]] — egyedi vezérlők
  öröklődéssel vagy `UserControl`-lal
- [[concepts/esemalk/wpf-mvvm-tamogato-csomagok]] — MVVM Toolkit, Prism
  Library

### 8. előadás — WPF: összetett alkalmazások, erőforrások, stílusok

- [[concepts/esemalk/wpf-eroforrasok-alapjai]] — `Resources`, `x:Key`/
  `StaticResource`, erőforrásfájlok (`ResourceDictionary`)
- [[concepts/esemalk/wpf-stilusok-alapjai]] — `Style`/`Setter`, implicit és
  explicit stílusok, `TargetType`
- [[concepts/esemalk/wpf-eroforrasok-animaciok]] — animációk, `Storyboard`,
  `KeyFrame`
- [[concepts/esemalk/wpf-stilus-triggerek]] — `EventTrigger`, `DataTrigger`,
  megjelenítés-vezérlés nézetmodell-adat alapján
- [[concepts/esemalk/wpf-stilusok-dinamikus-felulet]] — stílusok dinamikus
  felületen (`ItemContainerStyle`)
- [[concepts/esemalk/wpf-stilusok-pelda-szinracs]] — példa: dinamikus
  méretezhető színrács
- [[concepts/esemalk/wpf-itemscontrol-elrendezes-dinamikus-mezok]] —
  `ItemsPanel` testreszabása, dinamikus mezők mintája MVVM-ben
- [[concepts/esemalk/wpf-kornyezet-fuggosegkezeles]] — laza csatolás, az
  alkalmazáskörnyezet mint IoC-komponens
- [[concepts/esemalk/wpf-idozites]] — `System.Timers.Timer` vs.
  `DispatcherTimer`, `Dispatcher.BeginInvoke`
- [[concepts/esemalk/wpf-tobbablakos-mvvm-pelda]] — vizsgatétel-generátor:
  egy nézetmodell két ablakkal

### 9. előadás — Avalonia UI alapok

- [[concepts/esemalk/avalonia-bevezetes]] — multi-platform architektúra,
  Skia-alapú rajzolás, MVVM ajánlott
- [[concepts/esemalk/avalonia-telepites-projekt-letrehozas]] — telepítés,
  új MVVM projekt létrehozása
- [[concepts/esemalk/avalonia-projekt-felepites]] — multi-projekt szerkezet,
  alkalmazás leíró (manifest) és kihelyezés
- [[concepts/esemalk/avalonia-xaml-felulet]] — `.axaml` felületleírás,
  `UserControl`/`Window`, beépített vezérlők
- [[concepts/esemalk/avalonia-mvvm-adatkotes]] — `Binding`, `DataContext`,
  `x:Reference`, nézetkiválasztás életciklus szerint
- [[concepts/esemalk/avalonia-mvvm-toolkit]] — `CommunityToolkit.Mvvm`:
  `ObservableObject`, `RelayCommand`, `[ObservableProperty]`
- [[concepts/esemalk/avalonia-szamologep-pelda]] — számológép példa
  Avalonia UI-ban

### 10. előadás — Avalonia UI: összetett alkalmazások

- [[concepts/esemalk/avalonia-mobil-alkalmazaskornyezet-eletciklus]] —
  asztali (`Startup`/`Exit`) és mobil életciklus, sandbox,
  `IActivatableLifetime`
- [[concepts/esemalk/avalonia-platformfuggetlen-perzisztencia]] —
  perzisztencia `System.IO`-val és `Environment.SpecialFolder`-rel
- [[concepts/esemalk/avalonia-dialogusablakok]] — `StorageProvider`,
  `OpenFilePickerAsync`, `SaveFilePickerAsync`
- [[concepts/esemalk/avalonia-animaciok-atmenetek]] — animációk
  (`Animation`/`KeyFrame`) és átmenetek (`Transitions`)
- [[concepts/esemalk/avalonia-kezmozdulat-kezeles]] — kézmozdulat-kezelés
  (`GestureRecognizer`-ek)
- [[concepts/esemalk/avalonia-meret-tajolas-kezeles]] — méret- és
  tájolás-kezelés mobil környezetben
- [[concepts/esemalk/avalonia-eszkozfuggo-viselkedes]] — eszközfüggő
  viselkedés (`OperatingSystem.IsAndroid`, `OnPlatform`)
- [[concepts/esemalk/avalonia-temak-stilusok]] — témák és CSS-szerű
  szelektorok
- [[concepts/esemalk/avalonia-idozites]] — `DispatcherTimer`,
  `Dispatcher.UIThread.InvokeAsync`

### 11. előadás — Reaktív programozás

- [[concepts/esemalk/reaktiv-programozas-alapjai]] — megfigyelhető
  adatfolyamok, aszinkron végrehajtás, ütemezők, operátorok
- [[concepts/esemalk/reaktiv-iterator-tervezesi-minta]] — a GoF Iterator
  minta, `IEnumerable<T>`/`IEnumerator<T>`
- [[concepts/esemalk/reaktiv-observer-tervezesi-minta]] — a GoF Observer
  minta, C# események mint megvalósítás
- [[concepts/esemalk/rx-observable-alapok]] — `IObservable<T>`/
  `IObserver<T>`, gyártó metódusok, feliratkozás (`Subscribe`)
- [[concepts/esemalk/rx-operatorok]] — `Where`, `Throttle`, `Distinct`,
  `Select`, `Scan`, `Merge`, `GroupBy`
- [[concepts/esemalk/reaktiv-szenzor-pelda]] — szimulált szenzoradat-folyam
  feldolgozása
- [[concepts/esemalk/reaktiv-multicasting]] — `Publish`, `Connect`,
  `RefCount`, cold/hot observable
- [[concepts/esemalk/reaktiv-reactiveui]] — a ReactiveUI könyvtár
  WinForms/WPF/Avalonia UI-val

### 12. előadás — Lokalizáció

- [[concepts/esemalk/dotnet-lokalizacio-kulturak]] — `CultureInfo`,
  kultúra-specifikus `.resx` fájlok, `ResourceManager`
- [[concepts/esemalk/xaml-lokalizacio-x-static]] — lokalizáció a WinForms
  tervezőben és XAML-ben (`x:Static`)

### Gyakorlatok, beadandók és zárthelyi minták

- [[concepts/esemalk/gyakorlati-munkafuzetek-attekintes]] — a 0–8. gyakorlat
  munkafüzeteinek áttekintése, tombola hibakeresés
- [[concepts/esemalk/docustat-modell-szovegstatisztika]] — DocuStat: szóstatisztika
  és metrikák konzolos modellje (1. gyakorlat)
- [[concepts/esemalk/winforms-gombvadaszat-digitalis-orak]] — első WinForms
  alkalmazások, időzítő, egyedi vezérlő (2. gyakorlat)
- [[concepts/esemalk/docustat-winforms-nezet-esemenyek]] — DocuStat nézete,
  push/pull események (3. gyakorlat)
- [[concepts/esemalk/docustat-perzisztencia-filemanager]] — `IFileManager`,
  gyártófüggvény, DI (4. gyakorlat)
- [[concepts/esemalk/ioc-tarolo-servicecollection]] — IoC tároló és
  szolgáltatás-élettartamok
- [[concepts/esemalk/docustat-egysegtesztek]] — MSTest, Moq, xUnit (5. gyakorlat)
- [[concepts/esemalk/docustat-tobbfajlos-aszinkron-betoltes]] — lapok,
  `async`/`await`, haladásjelzés (6. gyakorlat)
- [[concepts/esemalk/filesystemwatcher-fajlvaltozas-figyeles]] — fájlváltozás
  figyelése és buktatói
- [[concepts/esemalk/wpf-kepletolto-modell-nezet]] — WPF képletöltő, kétrétegű
  (7. gyakorlat)
- [[concepts/esemalk/wpf-kepletolto-mvvm]] — WPF képletöltő MVVM-ben
  (8. gyakorlat)
- [[concepts/esemalk/beadando-statikus-analizis]] — a beadandók statikus és
  architektúra-analízise
- [[concepts/esemalk/beadando-dokumentacio-sudoku-minta]] — beadandó dokumentáció
  mintája (Sudoku, WinForms és Avalonia)
- [[concepts/esemalk/beadando-2-avalonia-feladatkiiras]] — a 2. beadandó
  követelményei és feladatai
- [[concepts/esemalk/zh-mintafeladatok]] — géptermi zárthelyi mintafeladatok

## Kapocs

- [[index]] — wiki tartalomjegyzék
