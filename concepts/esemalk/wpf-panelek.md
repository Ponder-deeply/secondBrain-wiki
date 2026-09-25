---
tags: [concept, esemalk/wpf-alapok]
sources: [elte_eva_ea06_wpf_basics.pdf]
derivation: source
updated: 2026-09-13
---

# WPF panelek (Panel leszármazottak)

Több vezérlő elrendezése WPF-ben panelek (`Panel`) segítségével történik;
ezeknek több leszármazott típusa van, saját elrendezési logikával.

## Tartalom

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

- [[concepts/esemalk/wpf-elrendezes-tulajdonsagok]] — az igazítás, margó és
  méretezés minden panelen belül is érvényes, panel-független tulajdonságok
- [[concepts/esemalk/wpf-fuggosegi-tulajdonsagok]] — a `Canvas.Left`/`Top` és
  `Grid.Row`/`Column` csatolt (attached) tulajdonságok maguk is függőségi
  tulajdonságok
- [[concepts/esemalk/winforms-elrendezok]] — a WinForms `FlowLayoutPanel` és
  `TableLayoutPanel` a `WrapPanel`/`Grid` analógjai, más keretrendszerben
