---
tags: [concept, esemalk/wpf-architektura]
sources: [elte_eva_ea07_wpf_architecture.pdf]
derivation: source
updated: 2026-09-13
---

# Speciális parancskötések (`InputBindings`)

A WPF vezérlők `InputBindings` tulajdonsága lehetővé teszi, hogy egér- vagy
billentyűesemények közvetlenül parancsokhoz legyenek kötve, felületi
vezérlők (gombok) közbeiktatása nélkül.

## Tartalom

Az `InputBindings` gyűjteménybe két típusú kötés helyezhető:

- **billentyűzetkötés** (`KeyBinding`): megadható vele egy konkrét billentyű
  (`Key`), vagy egy billentyűkombináció (`Gesture`);
- **egérkötés** (`MouseBinding`): megadható vele egy egérgomb-művelet
  (`MouseAction`), vagy szintén egy kombináció (`Gesture`).

Példa billentyűkombináció kötésére:

```xml
<Window.InputBindings> <!-- bemeneti kötések -->
  <KeyBinding Command="{Binding MyCommand}"
              Gesture="CTRL+R" />
  <!-- Ctrl+R billentyűkombináció kötése -->
</Window.InputBindings>
```

Konkrét billentyűkhöz és parancsparaméterekhez kötve (a
[[concepts/esemalk/wpf-mvvm-szamologep-pelda]] lapon leírt számológép
billentyűzetes vezérlése):

```xml
<Window.InputBindings>
  <!-- billentyűparancsok megfelelő paraméterrel -->
  <KeyBinding Key="Enter" Command="{Binding CalculateCommand}"
      CommandParameter="=" />
  <KeyBinding Key="Add" Command="{Binding CalculateCommand}"
      CommandParameter="+" />
  …
</Window.InputBindings>
```

Így ugyanaz a parancs (`CalculateCommand`) érhető el mind gombnyomással, mind
billentyűzetről, azonos parancsparaméter-logikával.

## Kapocs

- [[concepts/esemalk/wpf-mvvm-parancs-vegrehajthatosaga]] — a parancsok
  (`ICommand`) végrehajthatósága, amelyre az `InputBindings` is épít
- [[concepts/esemalk/wpf-mvvm-szamologep-pelda]] — a számológép példa, ahol
  a billentyűzetes vezérlés megjelenik
- [[concepts/esemalk/vezerlo-esemenykezelo-tarsitas]] — vezérlők
  eseménykezelőkhöz társítása; az `InputBindings` ennek deklaratív,
  parancsalapú megfelelője WPF-ben
