---
tags: [concept]
sources: [elte_eva_ea05_winforms_multithread.pdf]
derivation: source
updated: 2026-09-13
---

# Párhuzamosítás időzítővel (WinForms)

Az időzítés az aszinkron tevékenységvégrehajtás egy másik formája: a
`System.Timers.Timer` a grafikus felülettől függetlenül is használható, és a
`System.Windows.Forms.Timer` vezérlővel ellentétben párhuzamosan fut a
háttérben, nagyobb pontosságot garantálva.

## Tartalom

A `System.Timers.Timer` intervalluma az `Interval` tulajdonsággal állítható,
indítása/leállítása a `Start`/`Stop` metódusokkal történik, az időzített
esemény pedig az `Elapsed` eseményen keresztül váltódik ki:

```csharp
Timers.Timer myTimer = new Timer(); // időzítő
myTimer.Elapsed +=
    new ElapsedEventHandler(Timer_Elapsed); // időzített esemény
...
void Timer_Elapsed(...){
    // itt nem használhatjuk a felületet
    BeginInvoke(new Action(() => {
        // itt már igen
        myLabel.Text = e.SignalTime.ToString();
    }));
}
```

Mivel a `System.Timers.Timer` háttérszálon fut, hátránya, hogy grafikus
felületű alkalmazásban a felülettel szinkronizálást kell végezni — az
`Elapsed` eseménykezelőben a vezérlők közvetlen elérése nem biztonságos.
Ehhez, hasonlóan a taszkoknál látott mintához (lásd
[[concepts/esemalk/csharp-task-alapok]]), a vezérlő `BeginInvoke` műveletével
oldható fel: egy lambda-kifejezéssel megadott `Action` a felület szálán fut
le.

Ugyanez a minta jelenik meg egy modell/nézet architektúrában is, ahol a
modell egy `Timer`-rel generál eseményeket (pl. egy vizsgatétel-generáló
alkalmazásban a `NumberGenerated` esemény), a nézet (`Form`) pedig az
eseménykezelőben `BeginInvoke`-kal szinkronizáltan frissíti a felületet:

```csharp
private void Model_NumberGenerated(object sender, EventArgs e){
    BeginInvoke(new Action(() => {
        _textNumber.Text = _model.QuestionNumber.ToString();
    })); // szinkronizált végrehajtás
}
```

## Kapocs

- [[concepts/esemalk/csharp-task-alapok]] — a `Task`-alapú aszinkron
  programozás alapjai, ugyanaz a `BeginInvoke`-mintázat
- [[concepts/esemalk/vezerlo-esemenykezelo-tarsitas]] — vezérlők
  eseményeinek kezelése, `sender` paraméter
- [[concepts/esemalk/esemeny-letrehozasa-kivaltasa]] — saját esemény
  létrehozása és kiváltása C#-ban
- [[concepts/esemalk/modell-nezet-architektura]] — modell/nézet (MV)
  architektúra, amelyben a modell időzítővel generál eseményeket
- [[concepts/esemalk/csharp-task-szinkronizacio]] — a taszkok szálszintű
  szinkronizálása `SynchronizationContext` és `TaskScheduler` segítségével
