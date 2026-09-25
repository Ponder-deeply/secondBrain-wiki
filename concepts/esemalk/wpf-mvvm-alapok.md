---
tags: [concept, esemalk/wpf-architektura]
sources: [elte_eva_ea07_wpf_architecture.pdf]
derivation: source
updated: 2026-09-13
---

# Modell/nézet/nézetmodell (MVVM) architektúra

A *modell/nézet/nézetmodell* (*Model/View/ViewModel*, MVVM) a WPF-alkalmazások
tipikus architektúrája: egy közvetítő réteg (*nézetmodell*) iktatódik a nézet
és a modell közé, amely teljesen leválasztja a megjelenítést a mögötte lévő
tevékenységekről.

## Tartalom

### A nézet rétegződése WPF-ben

Grafikus alkalmazásoknál alapvető tervezési kérdés a felületi megjelenés és a
tevékenységek szétválasztása, azaz a [[concepts/esemalk/modell-nezet-architektura]]
(MV) használata. WPF-alkalmazásoknál a nézet maga is két részre bontható:

- **felületi kód** (XAML) — a *grafikus* feladata, eszköze a *Microsoft Blend*
  (korábban *Microsoft Expression Blend*)
- **háttérkód** — a *programozó* feladata, eszköze a *Microsoft Visual Studio*

Ahhoz, hogy a két szerep munkája ne akadjon össze (pl. eseménykezelő-társítás
miatt), a felületi és a háttérkódnak hasonlóan szeparálhatónak kell lennie,
mint a modellnek és a nézetnek.

### MV kontra MVVM

A sima MV architektúrában (lásd [[concepts/esemalk/modell-nezet-architektura]])
a felhasználó a nézettel (XAML + háttérkód) kommunikál, a nézet háttérkódja
pedig közvetlenül a modellel. Az MVVM ezt egy köztes réteggel, a
*nézetmodellel* egészíti ki, amely átveszi a háttérkód szerepét:

```
felhasználó ↔ nézet (XAML) ↔ nézetmodell ↔ modell
```

Az MVVM architektúrában:

- a **modell** tartalmazza az alkalmazás logikáját (algoritmusok, adatelérés);
  önálló, újrafelhasználható komponens
- a **nézet** tartalmazza a felület vezérlőit (ablakok, vezérlők, …) és az
  erőforrásokat (animációk, stílusok, …)
- a **nézetmodell** lehetőséget ad a modell változásainak követésére és a
  tevékenységek végrehajtására, a nézet és a modell közötti közvetítőként

Előnyei:

- a grafikus és a programozó tevékenysége élesen elhatárolódik
- a nézet, illetve a nézetmodell könnyen cserélhető vagy módosítható anélkül,
  hogy a másikat befolyásolná

Hátránya: egyszerű alkalmazásoknál nem célszerű, mivel hosszabb tervezést és
körülményesebb implementációt igényel, mint a sima MV vagy a
[[concepts/esemalk/haromreteg-architektura]].

Az architektúra a [[concepts/esemalk/haromreteg-architektura]]-hoz hasonlóan
tovább bővíthető egy *perzisztencia* (adatelérés) réteg bevezetésével, így egy
négyrétegű architektúrát kapva.

### Az adatáramlás iránya

A rétegek között az adat és a vezérlés kétirányban áramlik:

- lefelé: **adatkötés, parancskötés** (nézet → nézetmodell) és
  **metódus-/tulajdonsághívások** (nézetmodell → modell)
- felfelé: **változáskövetés** (nézetmodell → nézet) és **visszatérési
  értékek, események** (modell → nézetmodell)

### Megvalósítás eszközei

Az MVVM megvalósításához három eszközre van szükség:

1. **adattársítás** a felület és a nézetmodell között — lásd
   [[concepts/esemalk/wpf-adatkotes-alapjai]] (`Binding`)
2. **változáskövetés** a nézetmodell adataiban — lásd
   [[concepts/esemalk/wpf-mvvm-inotifypropertychanged]] (`INotifyPropertyChanged`)
3. **parancsok** végrehajtása eseménykezelők nélkül, a nézetmodellben —
   `ICommand` (a `CanExecute`/`Execute` metódusokkal)

Osztálydiagram szinten a `View` (a WPF `FrameworkElement` leszármazottja)
`Binding`-gal kötődik a `ViewModel`-hez (a `View.DataContext`
tulajdonságán keresztül), a `ViewModel` pedig `ViewModelCommand` (az
`ICommand` interfészt megvalósítva) és `ViewModelItem` (gyűjteményként
`ObservableCollection`-ben tárolva, `INotifyPropertyChanged`-et
megvalósítva) objektumokat, valamint egy `Model` referenciát tartalmaz.

## Kapocs

- [[concepts/esemalk/modell-nezet-architektura]] — az egyszerűbb MV
  architektúra, amelynek az MVVM a WPF-specifikus továbbfejlesztése
- [[concepts/esemalk/haromreteg-architektura]] — a WinForms-os
  háromrétegű architektúra, analóg a perzisztenciával bővített MVVM-mel
- [[concepts/esemalk/wpf-bevezetes]] — a WPF áttekintése, amely az MVVM
  mintát már bevezetésként említi
- [[concepts/esemalk/wpf-adatkotes-alapjai]] — az adatkötés (`Binding`)
  mechanizmusa, amely az MVVM egyik megvalósítási eszköze
- [[concepts/esemalk/wpf-mvvm-inotifypropertychanged]] — a változáskövetés
  (`INotifyPropertyChanged`), az MVVM másik megvalósítási eszköze
- [[subjects/esemalk]]
