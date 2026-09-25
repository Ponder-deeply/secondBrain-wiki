---
tags: [concept, esemalk/wpf-alapok]
sources: [elte_eva_ea06_wpf_basics.pdf]
derivation: source
updated: 2026-09-13
---

# WPF vezérlők tulajdonságai

A Windows Forms-ban megszokott vezérlőket jórészt megtaláljuk a WPF-ben is
(esetlegesen más néven), de a WPF vezérlői általában jóval szélesebb körben
személyre szabhatóak.

## Tartalom

Fontosabb közös tulajdonságok:

- **objektumnév** — `Name`, `x:Name`
- **erőforrások** — `Resources`
- **sablon** — `Template`, amellyel több vezérlő tulajdonságait tudjuk
  közösen állítani
- **kinézet** — `Background`, `Foreground`, `BorderBrush`,
  `BorderThickness`, …
- **betűkezelés** — `FontFamily`, `FontSize`, `FontStretch`, …
- **kurzorkinézet** — `Cursor`
- **pozicionálás és méretezés** — `Width`, `ActualWidth`, `MaxWidth`,
  `Padding`, `Margin`, `VerticalAlignment`, `VerticalContentAlignment`,
  `RenderTransform`, …
- **engedélyezettség, láthatóság, fókusz** — `IsEnabled`, `IsVisible`,
  `IsFocused`
- **tabulátorkezelés** — `TabIndex`, `IsTabStop`

A vezérlők eseményei is jórészt megegyeznek a Windows Forms eseményekkel,
így tartalmazzák a különböző egér-/billentyűállapotok kezelését, a
tulajdonságok változását stb.

### Példa: egyszerű számológép (vázlat)

Egy modell/nézet architektúrában megvalósított számológép-alkalmazásban a
modell (`CalculatorModel`) biztosítja a műveletek végrehajtását, és
eseménnyel jelzi az eredmény megváltozását; a nézet (`CalculatorWindow`)
példányosítja a modellt, gombokon keresztül biztosítja a műveletek
végrehajtását (`Button_Click`), továbbá kezeli a billentyűzet eseményeit is
(`Window_KeyDown`). Az elemeket magasság (`Height`) és margó (`Margin`)
megadásával pozicionálják. *(A megvalósítás részletei a forrás következő
szakaszában folytatódnak.)*

## Kapocs

- [[concepts/esemalk/wpf-elemhierarchia]] — a `Control` osztály és
  leszármazottai, amelyekre ezek a tulajdonságok vonatkoznak
- [[concepts/esemalk/wpf-ablakok-alkalmazasok]] — az ablak, amelybe a
  vezérlők kerülnek
- [[concepts/esemalk/winforms-vezerlok-alapjai]] — a WinForms `Control`
  osztálya és tulajdonságai, amelyeknek ez a WPF-megfelelője
- [[concepts/esemalk/vezerlo-esemenykezelo-tarsitas]] — a WinForms
  eseménykezelés, amellyel a WPF vezérlők eseményei jórészt megegyeznek
- [[subjects/esemalk]]
