---
tags: [concept, esemalk/winforms-statikus-ui]
sources: [elte_eva_ea01_winforms_static.pdf]
derivation: source
updated: 2026-09-12
---

# WinForms vezérlők alapjai

A *Windows Forms* (*WinForms*) a .NET keretrendszer első grafikus felülete: a
`System.Windows.Forms` névtérbeli vezérlőkből épül fel, amelyek a `Control`
osztályból származnak.

## Tartalom

### A felület

- rasztergrafikára (GDI+) épül, és teljes mértékben processzor által vezérelt;
- a grafikus felület előállításához a *Microsoft Visual Studio* felülettervező
  eszközt biztosít: ezzel grafikusan szerkeszthető a felület, a hozzá tartozó
  kódot pedig az eszköz legenerálja;
- alapvetően vezérlőkből épül fel, pl. gombok (`Button`, `RadioButton`,
  `CheckBox`), beviteli mezők (`TextBox`, `ComboBox`, `ListBox`),
  dialógusablakok (`MessageBox`, `OpenFileDialog`).

### Vezérlőhierarchia

A vezérlők közös őse a `Control` osztály. Ebből származik többek közt a
`ButtonBase` (`Button`, `RadioButton`, `CheckBox`), a `ListControl`
(`ComboBox`, `ListBox`, `CheckedListBox`), a `ScrollableControl`
(`Panel`, `ToolStrip`, illetve a `ContainerControl`, amelyből a `Form` — az
ablakok osztálya — is származik), a `Label`, a `GroupBox` és a `ListView`.

### Vezérlők tulajdonságai

A vezérlőket tulajdonságaik segítségével szerkeszthetjük, pl.:

- pozícionálás és méretezés (`Location`, `Size`, `Anchor`, `AutoSize`, `Dock`);
- engedélyezettség (`Enabled`), fókusz (`Focused`);
- felirat (`Text`), szöveget tartalmazó elemekben;
- színezés (`ForeColor`, `BackColor`), amelyeket a `Color` osztály
  segítségével állíthatunk be tetszőleges RGB kombinációra, vagy fix értékre
  (pl. `Color.Red`).

```csharp
Label myLabel = new Label(); // új címke
myLabel.Location = new Point(6, 18); // pozíció
myLabel.ForeColor = Color.Blue; // szövegszín
myLabel.Text = "valami felirat"; // felirat
```

## Kapocs

- [[concepts/esemalk/winforms-ablakok-felepitese]] — a `Form`, mint a
  vezérlőhierarchia egy speciális, konténer eleme
- [[concepts/esemalk/vezerlo-esemenykezelo-tarsitas]] — a vezérlők eseményei és
  kezelésük
- [[subjects/esemalk]]
