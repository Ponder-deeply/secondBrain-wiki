---
tags: [concept, esemalk/avaloniaui-halado-temak]
sources: [elte_eva_ea10_avaloniaui_complex.pdf]
derivation: source
updated: 2026-09-13
---

# Avalonia UI kézmozdulat-kezelés (gesture recognizers)

Mobil/táblagépes környezetben célszerű az alkalmazás vezérlésében a
felhasználó kézmozdulataira (touch gestures) támaszkodni; az Avalonia UI
ehhez beépített felismerőket (`GestureRecognizer`) kínál, amelyek tetszőleges
vezérlőhöz rendelhetők.

## Tartalom

Bármely vezérlőre állítható kézmozdulat-érzékelés: a felismerő egy adott
mozdulatot (`GestureRecognizer` leszármazott) figyel, és felismeréskor egy
tetszőleges tevékenységet (`Command`) hajt végre. Beépített felismerők:

- `ScrollGestureRecognizer` — görgetés
- `PinchGestureRecognizer` — csíptetés (nagyítás/kicsinyítés két ujjal)
- `PullGestureRecognizer` — húzás
- `GestureRecognizer` — tetszőleges egyedi mozdulat megvalósításához

XAML-ben a vezérlő `GestureRecognizers` gyűjteményéhez adva:

```xml
<Image …>
    <Image.GestureRecognizers> <!-- érzékelés -->
        <PullGestureRecognizer Command=… />
        <!-- érintés hatására fut a parancs -->
    </Image.GestureRecognizers>
</Image>
```

A minta ugyanazt a parancs-alapú (`ICommand`) mechanizmust használja, mint a
WPF/Avalonia MVVM adatkötéses parancsvégrehajtása — a felismert mozdulat egy
`Command`-ot vált ki, nem eseménykezelő kódot.

## Kapocs

- [[concepts/esemalk/avalonia-mvvm-adatkotes]] — a `Command`-alapú
  parancsvégrehajtás MVVM-es alapjai, amelyre a gesztúrafelismerők épülnek
- [[concepts/esemalk/wpf-mvvm-parancsok-icommand]] — az `ICommand` minta WPF
  oldali megfelelője
- [[concepts/esemalk/avalonia-meret-tajolas-kezeles]] — a mobil környezet
  másik jellemző alkalmazkodási igénye (méret és tájolás)
