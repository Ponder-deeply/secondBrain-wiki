---
tags: [concept, esemalk/tobbszalu-programozas-csharp-ban]
sources: [elte_eva_ea05_winforms_multithread.pdf]
derivation: source
updated: 2026-09-13
---

# WinForms alkalmazások párhuzamosítása — Fibonacci-generátor példa

Egy grafikus felületű Fibonacci-szám-generáló alkalmazás, amely a szinkron,
a taszkalapú aszinkron, majd az eseményvezérelt, megszakítható aszinkron
végrehajtási módokat mutatja be egymásra épülő lépésekben.

## Tartalom

### Szinkron vs. aszinkron végrehajtás

A tevékenységek végrehajtásának két megközelítése van:

- **szinkron**: a tevékenység kezdeményezője megvárja annak lefutását — a
  hívó szál blokkolódik, amíg a tevékenység lefut, és ha az sokáig tart, az
  a program felületén is észrevehető (lefagyni látszó ablak),
- **aszinkron**: a tevékenység kezdeményezője nem várja meg a lefutást,
  illetve az eredményt — a tevékenység (metódus) külön szálon fut, az
  eredményt később kapjuk meg (pl. eseményen át), és a hívó szál nem
  blokkolódik, folytathatja a végrehajtást.

Grafikus felületű alkalmazások felépítésében fontos, hogy gyorsan
reagáljunk a felhasználói interakcióra (a felhasználói felület mindig aktív
legyen), ezért nagyobb műveletet aszinkron módon, háttérben végzünk. Az
aszinkron műveletek alapja a *taszk* (`Task`); amennyiben meg szeretnénk
várni a művelet eredményét, taszkot kell megadni visszatérési értékként
(`Task<T>`).

### 1. lépés — szinkron generátor

*Feladat:* készítsünk egy grafikus felületű alkalmazást Fibonacci-számok
számítására. A Fibonacci-számot egy modell állítja elő
(`FibonacciGenerator`), a generáláshoz (`Generate`) a klasszikus rekurzív
képletet használjuk:

$$F(n) = \begin{cases} 1 & \text{ha } n < 3 \\ F(n-1) + F(n-2) & \text{ha } n \geq 3 \end{cases}$$

```csharp
// FibonacciGenerator.cs
public Int64 Generate(Int32 number) {
    if (number < 1)
        throw new ArgumentOutOfRangeException(…);
    if (number > 100)
        throw new ArgumentOutOfRangeException(…);

    if (number < 3)
        return 1;

    return Generate(number - 1)
         + Generate(number - 2);
}
```

A grafikus felületen egy listában jelenítjük meg a számokat, és egy
számbeállító segítségével szabályozzuk, hányadik számra vagyunk kíváncsiak.

### 2. lépés — aszinkron becsomagolás

Lehetőséget adunk az aszinkron használatra is (`GenerateAsync`), lényegében
egy taszkba burkoljuk a szinkron tevékenységet — így a felület mindig aktív
marad, és közben figyelmeztethetjük a felhasználót a folyamatban lévő
tevékenységre:

```csharp
// MainForm.cs
private async void ButtonGenerate_Click(…) {
    // aszinkron lesz az eseménykezelő

    _button.Text = "Generating... Please wait.";
    …
    _listBox.Items.Insert(0,
        await _generator.GenerateAsync(…));
        // megvárjuk a generálás eredményét
    …
    _button.Text = "Generate";
    …
}
```

### 3. lépés — eseményvezérelt, megszakítható generálás

Egy továbbfejlesztett változatban a Fibonacci-számokat aszinkron módon egy
modell állítja elő (`FibonacciGenerator`) a `Run(n)` metódussal, amely az
első `n` Fibonacci-számot számítja ki:

- egy új Fibonacci-szám előállításakor kiváltjuk a `NewResult` eseményt, az
  utolsó, azaz az `n`. szám előállítását követően pedig a `Ready` eseményt
  is,
- a számítás megszakítható a `Cancel()` metóduson keresztül (lásd
  [[concepts/esemalk/taszk-megszakitasa-cancellationtoken]]),
- a felületi vezérlők háttérszálakról történő frissítésekor használjuk a
  `BeginInvoke` műveletet, amely egy lambda-kifejezéssel megadott akciót
  (`Action`) tud futtatni a felület szálán (lásd
  [[concepts/esemalk/winforms-vezerlo-invoke-begininvoke]]).

```csharp
// MainForm.cs
private void Ready(object? sender, EventArgs e) {
    // amennyiben nem a UI szálon vagyunk, rekurzív
    // módon meghívjuk a Ready() eljárást, de már a
    // UI szálon.

    if (_btnCalculate.InvokeRequired) {
        BeginInvoke(new EventHandler(Ready),
                    sender, e);
        return;
    }
    _btnCalculate.Text = "Számol";
    …
}
```

## Kapocs

- [[concepts/esemalk/csharp-async-await]] — az `async`/`await` konstrukció,
  amelyre a `GenerateAsync` becsomagolás épül
- [[concepts/esemalk/taszk-megszakitasa-cancellationtoken]] — a `Cancel()`
  metóduson keresztüli megszakítás mögötti mechanizmus
- [[concepts/esemalk/winforms-vezerlo-invoke-begininvoke]] — az
  `Invoke`/`BeginInvoke`/`InvokeRequired` mechanizmus, amelyet a `Ready`
  eseménykezelő használ
- [[concepts/esemalk/rajzolo-alkalmazas-tervezese]] — hasonló, modell/nézet
  architektúrában megtervezett WinForms-példa
