---
tags: [concept]
sources: [elte_eva_ea06_wpf_basics.pdf]
derivation: source
updated: 2026-09-13
---

# WPF vezérlők elrendezési tulajdonságai

A WPF vezérlők elhelyezését és méretezését több, egymástól független
tulajdonságcsoport szabályozza.

## Tartalom

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

## Kapocs

- [[concepts/esemalk/wpf-panelek]] — a panelek (Canvas, Grid, StackPanel stb.)
  ezen tulajdonságok mellett saját elrendezési logikát is alkalmaznak
- [[concepts/esemalk/winforms-elrendezok]] — a WinForms elrendező vezérlői
  (`AutoSize`, `Dock`, `FlowLayoutPanel`, `TableLayoutPanel`); hasonló cél, de
  más keretrendszer és API
