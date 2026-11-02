---
tags: [concept]
sources: [elte_eva_ea06_wpf_basics.pdf]
derivation: source
kind: procedure
element: earth
updated: 2026-09-25
---

# WPF elrendezés: panelek és elrendezési tulajdonságok

Több vezérlő elrendezése WPF-ben panelek (`Panel`) segítségével történik;
ezeknek több leszármazott típusa van, saját elrendezési logikával.

## Tartalom

### Elrendezési tulajdonságok

A WPF vezérlők elhelyezését és méretezését több, egymástól független
tulajdonságcsoport szabályozza.

- **Igazítás**: `VerticalAlignment`, `HorizontalAlignment`.
- **Margók**: `Margin` (a vezérlő széle és a tartalmazó elem között) és
  `Padding` (a vezérlő tartalma és széle között).
- **Méret**: `Width`, `Height`; korlátok `MinWidth`/`MaxWidth` (és az analóg
  magasság-korlátok); az aktuális, kiszámított érték lekérdezhető az
  `ActualWidth`/`ActualHeight` tulajdonságokkal.
- **Túlfutás kezelése**: `ClipToBounds` — vágja-e a vezérlő a saját határain
  túlnyúló tartalmat.
- A vezérlők **nézetdobozba** (`Viewbox`) helyezhetők, amely automatikusan
  átméretezi (skálázza) a benne lévő tartalmat.

### Panelek (`Panel` leszármazottak)

- **Vászon** (`Canvas`): a bal felső sarokhoz viszonyított koordinátarendszert
  használ — a gyermekelemek pozícióját `Canvas.Left`/`Canvas.Top` csatolt
  tulajdonságokkal kell megadni.
- **Rács** (`Grid`): a sorok és oszlopok mérete szabályozható; létezik egységes
  rács (`UniformGrid`) is, ahol minden cella azonos méretű.
- **Igazító panelek**: `StackPanel`, `WrapPanel`, `DockPanel`.
- Egyik elrendezés sem görgethető önmagában, de behelyezhető görgetett
  területbe (`ScrollViewer`).
- Az egyes elrendezések automatikusan különböző elrendezési tulajdonságokat
  vesznek figyelembe a beágyazott elemeken (pl. a `Canvas` a `Canvas.Left`/
  `Canvas.Top`, a `Grid` a `Grid.Row`/`Grid.Column` csatolt tulajdonságokat).

## Kapocs

- [[concepts/esemalk/wpf-fuggosegi-tulajdonsagok]] — a `Canvas.Left`/`Top` és
  `Grid.Row`/`Column` csatolt (attached) tulajdonságok maguk is függőségi
  tulajdonságok
- [[concepts/esemalk/winforms-elrendezok]] — a WinForms `FlowLayoutPanel` és
  `TableLayoutPanel` a `WrapPanel`/`Grid` analógjai, más keretrendszerben
