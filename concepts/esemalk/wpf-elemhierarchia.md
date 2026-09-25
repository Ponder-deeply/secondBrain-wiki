---
tags: [concept, esemalk/wpf-alapok]
sources: [elte_eva_ea06_wpf_basics.pdf]
derivation: source
updated: 2026-09-13
---

# WPF elemhierarchia

A WPF grafikus felülete vektoros grafikus elemekből épül fel, amelyek egy
közös osztályhierarchiába rendeződnek a `System.Windows` névtérben.

## Tartalom

Az osztályhierarchia (öröklődési sorrendben):

```
DispatcherObject
  └─ DependencyObject
       └─ Visual
            └─ UIElement
                 └─ FrameworkElement
                      ├─ Shape
                      ├─ Control
                      │    ├─ ContentControl
                      │    └─ ItemsControl
                      └─ Panel
```

- **`UIElement`** — az elemek lehetnek vezérlők (`Control`), alakzatok
  (`Shape`) vagy gyűjtőelemek (`Panel`)
- az elemek grafikailag összetettek: alapértelmezés szerint hasonlítanak a
  Windows-vezérlőkre, de ez módosítható (lásd
  [[concepts/esemalk/wpf-vezerlok-tulajdonsagai]])
- **`ContentControl`** és **`ItemsControl`** a `Control` további
  specializációi: előbbi egyetlen tartalmi elemet, utóbbi elemek gyűjteményét
  fogja össze

**Futási architektúra:** az alkalmazás futása és a kirajzolás folyamata jóval
összetettebb, mint a WinForms-ban:

- a képalkotást külön szál (*rendering thread*) végzi az elemkezeléstől
  (*dispatcher thread*) elkülönítve
- a dispatcher thread egy prioritásos üzenetciklussal kezeli az elemeket, ezt
  a `DispatcherObject` osztály valósítja meg — ez a hierarchia gyökere, minden
  WPF elem ebből származik

## Kapocs

- [[concepts/esemalk/wpf-bevezetes]] — a WPF áttekintése, amelynek részét
  képezi ez az architektúra
- [[concepts/esemalk/wpf-vezerlok-tulajdonsagai]] — a `Control` leszármazottak
  közös tulajdonságai
- [[concepts/esemalk/winforms-vezerlok-alapjai]] — a WinForms `Control`
  osztálya, amelynek nincs ilyen mély, dispatcher-alapú hierarchiája
- [[subjects/esemalk]]
