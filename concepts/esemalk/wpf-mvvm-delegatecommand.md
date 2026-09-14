---
tags: [concept]
sources: [elte_eva_ea07_wpf_architecture.pdf]
derivation: source
updated: 2026-09-13
---

# Általános célú parancs (`DelegateCommand`)

Mivel egy alkalmazásban számos parancsra lehet szükség, nem célszerű
mindegyik számára külön `ICommand`-osztályt készíteni — helyette egy
általános, újrafelhasználható **`DelegateCommand`** osztály hozható létre.

## Tartalom

Az [[concepts/esemalk/wpf-mvvm-parancsok-icommand]] lapon bemutatott minta
minden parancshoz saját osztályt igényelne. Ehelyett:

- a parancsoknak egy tevékenységet kell végrehajtaniuk, amely `Action<T>`
  típusú λ-kifejezéssel is megadható, míg a feltétel egy
  `Func<T, Boolean>` típusúval (vagy `Predicate<T>`),
- a tényleges tevékenységet végrehajtó műveletet elhelyezhetjük a
  nézetmodell osztályban, így nem kell külön osztályokba helyezni a kódot,
- elég csupán **egy** parancsosztályt létrehozni (`DelegateCommand`) a
  tevékenység végrehajtásához, és a tényleges tevékenységet a parancs
  példányosításakor λ-kifejezés formájában adjuk meg.

```csharp
public class DelegateCommand : ICommand {
    private Action<Object?> _execute;
    private Predicate<Object?>? _canExecute;
        // tevékenység és feltétel eltárolása
    …
    public DelegateCommand(Action<Object?> execute){
        _execute = execute; // tevékenység rögzítése
    }
    public void Execute(Object? parameter){
        _execute(parameter);
        // tevékenység végrehajtása
    }
    …
}
```

A nézetmodellben a parancs egyszerűen egy `DelegateCommand` típusú
tulajdonságként jelenik meg, a tényleges tevékenységet pedig a
példányosításkor λ-kifejezésként adjuk meg:

```csharp
public class MyViewModel
    : INotifyPropertyChanged // nézetmodell
{
    // parancs elhelyezése a nézetmodellben
    public DelegateCommand MyCommand { get; set; };

    public void Write(Object? parameter) {
        MessageBox.Show(parameter); // tevékenység
    }
    …
    MyCommand = new DelegateCommand(x => Write(x));
        // tevékenység tényleges megadása
    …
}
```

Ezzel a parancsok deklarálása a felesleges, egyedi `ICommand`-osztályok
helyett a nézetmodellen belül, a tevékenységhez közel történhet.

## Kapocs

- [[concepts/esemalk/wpf-mvvm-parancsok-icommand]] — az `ICommand`
  interfész és az egyedi parancsosztályos megközelítés, amelyet a
  `DelegateCommand` kivált
- [[concepts/esemalk/wpf-mvvm-inotifypropertychanged]] — a nézetmodell
  változáskövetése
- [[subjects/esemalk]]
