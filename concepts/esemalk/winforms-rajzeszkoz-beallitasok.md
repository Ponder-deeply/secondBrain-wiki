---
tags: [concept, esemalk/winforms-elemi-grafika]
sources: [elte_eva_ea03_winforms_dynamic.pdf]
derivation: source
updated: 2026-09-13
---

# Rajzeszköz beállítások a `Graphics` osztályban

A `Graphics` osztály a puszta rajzoló műveleteken (`DrawLine`,
`FillRectangle`, ...) túl további, a rajzolás minőségét és
koordinátarendszerét befolyásoló beállításokat is biztosít.

## Tartalom

- **Élsimítás** — a `SmoothingMode` tulajdonsággal (`Default`,
  `HighSpeed`, `AntiAlias`, ...).
- **Koordinátarendszer módosítása** — a `TranslateTransform(...)`,
  `ScaleTransform(...)`, `RotateTransform(...)` műveletekkel; a hatás az
  összes utána következő rajzoló utasításra érvényes.
- **Állapotkezelés és váltás** — a `Save(...)` és `Restore(...)`
  műveletekkel visszakaphatók a korábbi koordinátarendszer-beállítások
  (pl. egy lokális transzformáció elvégzése után).
- **Szövegkiterjedés mérése** — a `MeasureString(...)` művelettel (hasznos
  pl. szöveg középre igazításához rajzoláskor).
- **Rajzfelület vágása** — a `SetClip(...)` és további műveletekkel, amelyek
  a rajzolást egy megadott tartományra korlátozzák.

## Kapocs

- [[concepts/esemalk/winforms-grafika-alapok]] — a `Graphics` osztály
  alapvető rajzoló műveletei, amelyekre ezek a beállítások hatnak
- [[concepts/esemalk/winforms-szinek-ecsetek-tollak]] — a `Pen` és `Brush`
  paraméterek, amelyekkel a rajzoló műveletek együtt szerepelnek
