---
tags: [concept, esemalk/winforms-dinamikus-ui]
sources: [elte_eva_ea03_winforms_dynamic.pdf]
derivation: source
updated: 2026-09-13
---

# WinForms méretezés és elrendezők

A WinForms felület alkalmazkodhat az ablak vagy a tartalmazó vezérlő
méretéhez automatikus méretezéssel és dedikált elrendező (layout) vezérlőkkel.

## Tartalom

Ahhoz, hogy a felület alkalmazkodjon az ablak méretéhez, egy vezérlő mérete
automatikusra állítható (`AutoSize`, `AutoSizeMode`), illetve a vezérlő a
tartalmazó vezérlőhöz igazítva (dokkolva) is elhelyezhető (`Dock`):

```csharp
this.AutoSize = true;               // automatikus méret
this.AutoSizeMode = AutoSizeMode.GrowAndShrink; // csökkenhet is

Button myButton = new Button();
myButton.Dock = DockStyle.Fill;     // kitöltés
```

Csoportosan (jellemzően [[concepts/esemalk/winforms-dinamikus-vezerlok]]
módon, futás közben) létrehozott vezérlők elhelyezhetők külön elrendező
elemek segítségével, például:

- `FlowLayoutPanel` — folyamatos elrendezés, iránya szabályozható
  (`FlowDirection`, pl. `BottomUp`)
- `TableLayoutPanel` — táblázatos elrendezés, ahol a sorok és oszlopok
  méretezésének módja egyenként szabályozható

Ilyenkor a vezérlőt nem közvetlenül az ablak, hanem az elrendező
gyerekelemeként helyezzük el:

```csharp
FlowLayoutPanel myPanel = new FlowLayoutPanel(); // folyamatos elrendező elem
myPanel.FlowDirection = FlowDirection.BottomUp;  // alulról felfele elrendezés
myPanel.Controls.Add(myButton);                  // a gombot az elrendezőre vesszük fel
```

A `TableLayoutPanel`-nél az `Add` metódus explicit oszlop- és sorindexet is
elfogad (`Controls.Add(control, oszlop, sor)`), amivel a vezérlő a tábla adott
cellájába kerül.

## Kapocs

- [[concepts/esemalk/winforms-dinamikus-vezerlok]] — dinamikusan létrehozott
  vezérlők, amelyeket ezek az elrendezők tartalmaznak
- [[concepts/esemalk/winforms-vezerlok-alapjai]] — a `Control` osztály és
  alaptulajdonságai
