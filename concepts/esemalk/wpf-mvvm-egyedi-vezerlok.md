---
tags: [concept, esemalk/wpf-architektura]
sources: [elte_eva_ea07_wpf_architecture.pdf]
derivation: source
updated: 2026-09-13
---

# Egyedi vezérlők létrehozása WPF-ben

WPF-ben lehetőség van saját, egyedi vezérlők létrehozására, amikor a
beépített vezérlők funkcionalitása nem elegendő egy adott felületi viselkedés
megvalósításához.

## Tartalom

Egyedi vezérlő kétféleképpen hozható létre:

- **öröklődéssel**, egy meglévő vezérlőből leszármaztatva, amikor annak
  viselkedését kell kiegészíteni vagy felüldefiniálni;
- **létező vezérlők összeállításával**, felhasználói vezérlővé
  (`UserControl`) szervezve, amely más vezérlőkben vezérlőként újra
  felhasználható, saját adatkötésekkel és erőforrásokkal.

A saját vezérlőket névtér-hivatkozáson keresztül érjük el a XAML-ben:

```xml
<Window …
    xmlns="http://schemas.microsoft.com/winfx/…"
    xmlns:view="clr-namespace:MyApp.View" … >
    <!-- megadjuk a névteret -->
    <view:MyControl … >
    <!-- példányosítjuk az egyedi vezérlőt -->
</Window>
```

**Példa** (a [[concepts/esemalk/wpf-mvvm-szamologep-pelda]] lapon leírt
számológép bővítéseként): a feladat, hogy a billentyűzet is használható
legyen a műveletek megadásához, a fókusz automatikusan a szövegdobozra
kerüljön (ehhez a nézetben a `FocusManager` osztályt kell használni), és a
szövegdoboz teljes tartalma automatikusan kijelölődjön minden akcióbillentyű
lenyomásakor.

Mivel a szöveg kijelölésének viselkedése a nézetben (kódmögöttes fájl nélkül,
tisztán XAML-lel) nem valósítható meg, létre kell hozni egy új vezérlőt a
`TextBox` leszármazottjaként (`SelectedTextBox`), amely felüldefiniálja a
billentyűzetkezelést:

```csharp
// SelectedTextBox.cs
private void SelectedTextBox_KeyUp(object sender, KeyEventArgs e) {
    switch (e.Key) {
        case Key.Add:      // az akcióbillentyűkre
        case Key.Subtract:
        case Key.Enter:
        case Key.Multiply:
        case Key.Divide:
            SelectAll();
            // minden szöveget kijelölünk
            break;
    }
}
```

A nézetben a fókusz automatikus beállítása egy gombhoz kötve, a
`FocusManager.FocusedElement` csatolt tulajdonsággal:

```xml
<view:SelectedTextBox x:Name="_textNumber"
    Height="42" VerticalAlignment="Top"
    Text="{Binding NumberFieldValue,
           UpdateSourceTrigger=PropertyChanged}"
    FontSize="28" TextAlignment="Right" FontWeight="Bold" />
…
<Button Command="{Binding CalculateCommand}"
    CommandParameter="+"
    Content="+"
    FocusManager.FocusedElement="{Binding
        ElementName=_textNumber}" Height="60" … />
```

## Kapocs

- [[concepts/esemalk/wpf-vezerlok-tulajdonsagai]] — a WPF vezérlők közös
  tulajdonságai, amelyekre az egyedi vezérlők is építenek
- [[concepts/esemalk/wpf-mvvm-szamologep-pelda]] — a számológép példa,
  amelyben a `SelectedTextBox` egyedi vezérlő megjelenik
- [[concepts/esemalk/wpf-fuggosegi-tulajdonsagok]] — a csatolt
  tulajdonságok (pl. `FocusManager.FocusedElement`) mögötti mechanizmus
