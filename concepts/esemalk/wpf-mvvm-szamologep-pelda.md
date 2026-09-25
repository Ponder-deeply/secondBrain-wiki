---
tags: [concept, esemalk/wpf-architektura]
sources: [elte_eva_ea07_wpf_architecture.pdf]
derivation: source
updated: 2026-09-13
---

# Számológép példa MVVM architektúrában

Egy egyszerű, a négy alapműveletet elvégző számológép, amely az MVVM
architektúra elemeit (nézetmodell, parancs, kötés) konkrét osztályokon és
XAML-kódon keresztül mutatja be.

## Tartalom

**Feladat:** olyan számológép, amellyel a négy alapműveletet el lehet
végezni, és amely látja a korábbi műveleteket is.

**Tervezés** — az osztályok kapcsolata:

- `App` (`Application`) hozza létre a `View::MainWindow` (`Window`) ablakot,
- a nézetmodell `ViewModel::CalculatorViewModel` (`INotifyPropertyChanged`)
  tárolja:
  - a beírt szöveges értéket (`NumberFieldValue` tulajdonság,
    `_numberFieldValue` mező),
  - a korábbi számításokat (`Calculations` tulajdonság,
    `ObservableCollection<String>`),
  - a számítás parancsát (`CalculateCommand` tulajdonság,
    `ViewModel::DelegateCommand` típusú, `+CalculateCommand` kompozícióval),
  - és kompozícióval birtokolja a modellt (`-_Model` mezőn keresztül,
    `Model::CalculatorModel`),
- a `Model::CalculatorModel` a `Model::CalculatorEventArgs` (`EventArgs`)
  eseményargumentum-osztályon keresztül jelzi a számítás megtörténtét, és a
  művelet típusát a `Model::Operation` felsorolás (`enumeration`,
  `-_Operation`) írja le,
- a `ViewModel::DelegateCommand` (`ICommand`) egy általános parancsosztály,
  amely két `readonly` mezőt zár magába: egy `_execute :Action<Object>` és
  egy `_canExecute :Predicate<Object>` delegáltat, és felkínálja a
  `CanExecute(Object) :Boolean`, `Execute(Object) :void` metódusokat, valamint
  a `CanExecuteChanged` eseményt; konstruktorai kizárólag a végrehajtandó
  műveletet (`Action<Object>`), illetve azt és a végrehajthatósági
  feltételt (`Predicate<Object>`) is átvehetik.

**Megvalósítás:**

- a nézetmodell konstruktorában a `CalculateCommand` egy új
  `DelegateCommand`-ként épül fel, amely a paramétert (a művelet jelét,
  pl. `"+"`) a `Calculate(String)` privát metódusnak adja át;
- a `Calculate(String operatorString)` metódus egy `switch` szerkezettel
  fordítja le a szöveges műveletjelet a modell hívására, pl. `"+"` esetén
  `_model.Calculate(value, Operation.Add)`;
- a nézetben (`MainWindow.xaml`) egy `Grid`-en belül a szövegdoboz kétirányú
  kötéssel követi a nézetmodell értékét:
  ```
  <TextBox Name="_textNumber" Height="42" VerticalAlignment="Top"
      Text="{Binding NumberFieldValue,
             UpdateSourceTrigger=PropertyChanged}"
      FontSize="28" TextAlignment="Right" FontWeight="Bold" />
  ```
  minden módosításra azonnal ment (`UpdateSourceTrigger=PropertyChanged`);
- a végrehajtó gombok a parancshoz kötődnek, a végrehajtandó műveletet
  parancsparaméterként kapják:
  ```
  <Button Command="{Binding CalculateCommand}"
      CommandParameter="+" Content="+" Height="60" … />
  ```

Ez a példa a [[concepts/esemalk/wpf-mvvm-inputbindings]] lapon leírt
billentyűzetes vezérléssel és a [[concepts/esemalk/wpf-mvvm-egyedi-vezerlok]]
lapon leírt egyedi `SelectedTextBox` vezérlővel bővül tovább (automatikus
fókusz és a beírt szöveg automatikus kijelölése).

## Kapocs

- [[concepts/esemalk/wpf-mvvm-parancs-vegrehajthatosaga]] — a
  `CanExecute`/`Execute` pár és a `CanExecuteChanged` esemény, amelyre a
  `DelegateCommand` épül
- [[concepts/esemalk/wpf-mvvm-delegatecommand]] — az általános célú
  `DelegateCommand` osztály, amelyet ez a példa felhasznál
- [[concepts/esemalk/wpf-mvvm-inotifypropertychanged]] — a nézetmodell
  változáskövetése, amelyre a `NumberFieldValue` tulajdonság kötése épül
- [[concepts/esemalk/wpf-mvvm-inputbindings]] — a számológép
  billentyűzetes vezérlése (`KeyBinding`)
- [[concepts/esemalk/wpf-mvvm-egyedi-vezerlok]] — a `SelectedTextBox` egyedi
  vezérlő, amelyet a példa a szövegdoboz kiterjesztéseként hoz létre
- [[concepts/esemalk/modell-nezet-architektura]] — a modell/nézet
  szétválasztás elve, amelyet ez a nézetmodell-alapú (MVVM) példa is követ
- [[concepts/esemalk/wpf-tictactoe-pelda]] — másik, hasonlóan felépített WPF
  példaalkalmazás
