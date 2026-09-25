---
tags: [concept, esemalk/wpf-alapok]
sources: [elte_eva_ea06_wpf_basics.pdf]
derivation: source
updated: 2026-09-13
---

# WPF vezérlők tartalmazása

WPF-ben sok vezérlő nem csak szöveget, hanem további vezérlőket vagy grafikus
elemeket is tartalmazhat, két alapvető leszármazási vonalon keresztül.

## Tartalom

- A `ContentControl` leszármazottai (pl. `Button`) egyetlen tetszőleges elemet
  tartalmazhatnak a `Content` tulajdonságukban — például egy gombba beágyazott
  `Image`:

```xml
<Button>
    <Image Source="…" />
    <!-- a vezérlő Content értékét töltjük fel egy képpel -->
</Button>
```

- Az `ItemsControl` leszármazottai (pl. `ListBox`, `ListView`, `ComboBox`)
  tetszőlegesen sok elemet tartalmazhatnak.
- Egyes vezérlőknek fejlécük is lehet (pl. `GroupBox`, `TreeView`).

Ez a megkülönböztetés (egy tartalom vs. sok elem) magyarázza, miért különbözik
a `Button` és a `ListBox` API-ja tartalommal való feltöltés szempontjából.

## Kapocs

- [[concepts/esemalk/wpf-panelek]] — a panelek (`Panel` leszármazottak) több
  vezérlő elrendezésére szolgálnak, szemben a `ContentControl` egyetlen
  tartalmával
- [[concepts/esemalk/wpf-vezerlok-megjelenese]] — a logikai fa írja le, hogyan
  épülnek egymásba a tartalmazott elemek
