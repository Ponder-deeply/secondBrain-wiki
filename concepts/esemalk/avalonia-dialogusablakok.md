---
tags: [concept]
sources: [elte_eva_ea10_avaloniaui_complex.pdf]
derivation: source
updated: 2026-09-13
---

# Avalonia UI — dialógusablakok (fájl- és könyvtárválasztás)

Az Avalonia UI keretrendszerben platformfüggetlen módon kérhetünk fájl
betöltéséhez és mentéséhez dialógusablakot a `StorageProvider` szolgáltatáson
keresztül.

## Tartalom

A `StorageProvider` osztály ún. szolgáltatásként (*service*) érhető el az
Avalonia UI keretrendszerben:

- a szolgáltatások a `TopLevel` vezérlőn keresztül érhetőek el
- az ablakok, nézetek és felületi vezérlők egymásba ágyazásával a vezérlők
  fa struktúrát alkotnak (*visual tree*), amelynek gyökér eleme a `TopLevel`
  vezérlő
- asztali ablakos alkalmazásoknál a `Window` a `TopLevel`; mobil
  alkalmazásoknál platformspecifikus lehet, pl. Android esetén a
  `MainActivity` lesz az
- platformfüggetlen módon bármely vezérlőhöz lekérdezhető:
  `TopLevel.GetTopLevel(control);`

A fájlműveletekhez a `StorageProvider` `OpenFilePickerAsync()` és
`SaveFilePickerAsync()` metódusait használhatjuk:

- betöltésnél megadható, hogy több fájl is kiválasztható-e
  (`AllowMultiple`)
- mentésnél megadható a javasolt fájlnév (`SuggestedFileName`) és
  alapértelmezett kiterjesztés (`DefaultExtension`)
- választható fájltípusok adhatók meg, ehhez elérhetőek előre definiált
  beállítások (pl. `FilePickerFileTypes.ImageJpg`), de saját is megadható

Példa:

```csharp
var files = await TopLevel.StorageProvider.OpenFilePickerAsync(
    new FilePickerOpenOptions
    {
        Title = "Select file to load",
        AllowMultiple = false,
        FileTypeFilter = new[]
        {
            new FilePickerFileType("Data file")
            {
                Patterns = new[] { "*.data" }
            }
        }
    });
```

Hasonlóan kérhetjük könyvtár tallózását is az `OpenFolderPickerAsync()`
eljárás használatával.

Ezek a dialógusok teszik lehetővé, hogy a felhasználó maga válassza meg a
mentés/betöltés útvonalát — szemben az
[[concepts/esemalk/avalonia-platformfuggetlen-perzisztencia]] lapon
bemutatott, `Environment.SpecialFolder`-re épülő automatikus (rejtett)
mentéssel.

## Kapocs

- [[concepts/esemalk/avalonia-platformfuggetlen-perzisztencia]] — az
  alkalmazás saját, automatikus állapotmentése `System.IO`-val és
  `Environment.SpecialFolder`-rel
- [[concepts/esemalk/avalonia-eletciklus-kezeles]] — a mentést kiváltó
  életciklus-események
- [[concepts/esemalk/avalonia-xaml-felulet]] — az `.axaml` felületleírás,
  `UserControl`/`Window`, amelyek a visual tree elemei
