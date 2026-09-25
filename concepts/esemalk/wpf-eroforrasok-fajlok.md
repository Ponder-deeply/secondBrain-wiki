---
tags: [concept, esemalk/wpf-eroforrasok-es-stilusok]
sources: [elte_eva_ea08_wpf_complex_resources.pdf]
derivation: source
updated: 2026-09-13
---

# WPF erőforrásfájlok (ResourceDictionary)

Ha több ablak vagy vezérlő számára ugyanazt a stílus-, animáció- és
sablonkészletet akarjuk biztosítani, önálló erőforrásfájlokat
(*Resource Dictionary*) használhatunk.

## Tartalom

- az erőforrásfájl csak XAML erőforrásokat tartalmazó fájl, gyökéreleme
  egy `ResourceDictionary`
- bármely ablakban és egyedi vezérlőben felhasználható, vagy akár a teljes
  alkalmazásban (az `App` osztályon keresztül)
- több felületi elem (pl. két `Window` és egy `UserControl`) is
  ugyanarra a `ResourceDictionary`-ra hivatkozhat, így közösen használják
  annak stílus- és sablonkészletét

Példa — az erőforrásfájl (`StyleDict.xaml`):

```xml
<ResourceDictionary …>
  <Style x:Key=… > <!-- stíluselem -->
    …
</ResourceDictionary>
```

Felhasználása egy ablakban (`MainWindow.xaml`):

```xml
<Window.Resources>
  <ResourceDictionary Source="styleDict.xaml" />
  <!-- erőforrásfájl betöltése -->
</Window.Resources>
```

## Kapocs

- [[concepts/esemalk/wpf-eroforrasok-alapjai]] — az erőforrás-fogalom és a
  `Resources`/`StaticResource` alapmechanizmus, amelyet az erőforrásfájlok
  kiterjesztenek
- [[concepts/esemalk/wpf-stilusok-alapjai]] — a stílusok, mint az
  erőforrásfájlokban tipikusan tárolt tartalom
- [[concepts/esemalk/wpf-ablakok-alkalmazasok]] — az `Application`/`App`
  osztály, amelyen keresztül egy erőforrásfájl a teljes alkalmazásra
  érvényesíthető
- [[subjects/esemalk]]
