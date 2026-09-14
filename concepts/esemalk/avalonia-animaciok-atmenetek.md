---
tags: [concept]
sources: [elte_eva_ea10_avaloniaui_complex.pdf]
derivation: source
updated: 2026-09-13
---

# Avalonia UI — animációk és átmenetek

Az Avalonia UI keretrendszer a WPF-hez hasonló módon támogat animációkat
(`Animation`), és emellett a webfejlesztésből ismert CSS-animációkhoz
hasonló átmeneteket (`Transitions`) is kínál.

## Tartalom

### Animációk

Az animációk stílusként (`Styles`) adhatók meg a nézet vagy vezérlő
szintjén. Példa: áttetszőség és forgatás egyidejű animálása, kulcskockákkal
(`KeyFrame`):

```xml
<Animation Duration="0:0:3" IterationCount="4">
  <KeyFrame Cue="0%">
    <Setter Property="Opacity" Value="0.0"/>
    <Setter Property="RotateTransform.Angle" Value="0.0"/>
  </KeyFrame>
  <KeyFrame Cue="100%">
    <Setter Property="Opacity" Value="1.0"/>
    <Setter Property="RotateTransform.Angle" Value="90.0"/>
  </KeyFrame>
</Animation>
```

### Átmenetek

Az átmenetek működése leginkább a webfejlesztésből ismert CSS-animációkhoz
hasonlítható: egy tulajdonság változása nem pillanatszerű, hanem animált
lesz. Példa: egy `Rectangle` áttetszőségének (`Opacity`) animált változása
egérrel való rámutatáskor (`pointerover`):

```xml
<Window.Styles>
  <Style Selector="Rectangle.red">
    <Setter Property="Fill" Value="Red"/>
    <Setter Property="Opacity" Value="0.5"/>
  </Style>
  <Style Selector="Rectangle.red:pointerover">
    <Setter Property="Opacity" Value="1"/>
  </Style>
</Window.Styles>

<Rectangle Classes="red">
  <Rectangle.Transitions>
    <Transitions>
      <DoubleTransition Property="Opacity" Duration="0:0:0.2"/>
    </Transitions>
  </Rectangle.Transitions>
</Rectangle>
```

### Animációk vs. átmenetek

Mindkét eszköz vizuális változásokat hoz létre, de különböző célokra
szolgálnak és eltérően működnek:

| | Animations | Transitions |
|---|---|---|
| Indítás | Kód, triggerek, események | Property értékváltozás |
| Cél | Összetettebb mozgatások, animációk | Property-k animált értékváltozása |
| Keyframe-k támogatása | Igen | Nem |
| Több property animálása | Igen | Jellemzően 1 transition / property |
| Javasolt felhasználás | Látványos effektek, animáció sorozatok | UI reszponzívabb megjelenítése |
| Teljesítmény | Kicsit erőforrásigényesebb | Nagyon könnyűsúlyú |

**Példa:** egy dinamikus, méretezhető tábla, amely három szín között
(piros, fehér, zöld) állítja a kattintott gombot, valamint a vele egy
sorban és oszlopban lévőket. A színt a nézet adja meg, így a nézetmodell nem
adhat vissza konkrét színt, csak egy sorszámot (0 és 2 között), amely
alapján a szín állítható (`ColorNumber`). A színt stílus osztályok
segítségével állítjuk a nézetben, a gomb emellett animálódjon, amennyiben a
kurzort rávisszük (csak asztali környezetben), illetve ha lenyomva tartjuk.
A stílusokat a nézet erőforrásaként hozzuk létre.

## Kapocs

- [[concepts/esemalk/wpf-eroforrasok-animaciok]] — a WPF-es
  `DoubleAnimation`/`Storyboard` alapú animációk, amelyekhez az Avalonia
  `Animation`/`KeyFrame` konstrukciója hasonlít
- [[concepts/esemalk/wpf-stilus-triggerek]] — a WPF-es triggerek, a
  `pointerover`-hez hasonló állapotfüggő megjelenés-vezérlés megfelelője
- [[concepts/esemalk/avalonia-xaml-felulet]] — az `.axaml` felületleírás és
  a beépített vezérlők, amelyeken a stílusok/animációk értelmezve vannak
