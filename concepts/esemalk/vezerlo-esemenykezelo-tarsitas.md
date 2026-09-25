---
tags: [concept, esemalk/winforms-statikus-ui]
sources: [elte_eva_ea01_winforms_static.pdf]
derivation: source
updated: 2026-09-12
---

# Vezérlők eseményeinek kezelése WinFormsban

Egy WinForms vezérlő (pl. `Button`) eseményeihez a `+=` operátorral
rendelünk eseménykezelő metódust; több vezérlő is megoszthat egy közös
kezelőt, amelyben a `sender` paraméter alapján derül ki, melyik vezérlő
váltotta ki az eseményt.

## Tartalom

### Eseménykezelő társítása

Egy vezérlő eseményéhez a `+=` operátorral és egy megfelelő delegált-típusú
példánnyal rendelünk kezelőt:

```csharp
Button b = new Button();
b.Click += new EventHandler(B_Click); // társítás
b.MouseDoubleClick +=
    new MouseEventHandler(B_DClick); // társítás
```

```csharp
void B_Click(object? sender, EventArgs e) { … }
    // eseménykezelő

void B_DClick(object? sender, MouseEventArgs e) {
    // speciális eseményargumentum, amelytől
    // lekérdezhető az egérgomb (Button) és a
    // pozíció (Location)
}
```

Az eseményargumentum típusa az esemény fajtájától függ: az egyszerű
`Click`-hez `EventArgs` elég, míg pl. `MouseDoubleClick` esetén a
`MouseEventArgs` további adatokat (egérgomb, pozíció) hordoz.

### Közös eseménykezelő és a `sender`

Több vezérlő is társítható ugyanahhoz az eseménykezelő metódushoz. Ekkor a
`sender` paraméterből (típusellenőrzéssel, pl. `is` mintaillesztéssel)
állapítható meg, melyik konkrét vezérlő váltotta ki az eseményt — pl. a
gomb felirata alapján dönthető el, melyik műveletet kell elvégezni:

```csharp
private void Button_Click(object? sender, EventArgs e) {
    try {
        // …
        _firstNumber = Double.Parse(_textNumber.Text);
        // eltároljuk az első operandust
        // …
        if (sender is Button button)
            switch (button.Text) {
                // megvizsgáljuk, milyen az
                // eseményt kiváltó gomb felirata,
                // így eldönthetjük, melyik gombot
                // nyomták le
                // …
            }
    }
    catch (OverflowException) {
        MessageBox.Show("Your input has too many digits!",
            "Calculation Error",
            MessageBoxButtons.OK, MessageBoxIcon.Error);
    }
    // …
}
```

A minta jól illusztrálja a kivételkezelés bevonását is az
eseménykezelőbe: a bevitel érvényesítése (`Double.Parse`) kivételt dobhat,
amit a kezelőn belül `try`/`catch` blokkal kezelünk, és pl.
`MessageBox.Show`-val jelzünk a felhasználónak.

### Példa: egyszerű számológép

A forrás egy `CalculatorForm` osztályt mutat be, amely öt gombot
(`Button`), egy szövegbeviteli mezőt (`TextBox`) és egy listát (`ListBox`)
tartalmaz; a négy alapművelet gombjaihoz egyetlen közös eseménykezelő
(`Button_Click`) tartozik, amely a `sender` felirata alapján dönt a
végrehajtandó műveletről. A műveletet egy felsorolási típus (`Operation`)
tárolja el (lásd [[concepts/esemalk/csharp-felsorolasi-tipus]]).

## Kapocs

- [[concepts/esemalk/esemeny-letrehozasa-kivaltasa]] — ez a lap a
  vezérlők *beépített* eseményeinek feliratkozását tárgyalja; a saját
  esemény létrehozása és kiváltása külön lapon szerepel
- [[concepts/esemalk/csharp-felsorolasi-tipus]] — a példában a művelet
  tárolására használt `enum`
- [[concepts/esemalk/billentyuzetkezeles-winforms]] — analóg mintázat a
  billentyűzet-eseményekre
- [[subjects/esemalk]]
