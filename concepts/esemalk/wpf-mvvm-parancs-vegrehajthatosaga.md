---
tags: [concept, esemalk/wpf-architektura]
sources: [elte_eva_ea07_wpf_architecture.pdf]
derivation: source
updated: 2026-09-13
---

# Parancsok végrehajthatósága és a `CanExecuteChanged` esemény

A WPF nézetmodelljében élő parancs (`ICommand`) bármikor jelezheti a
felületnek, hogy megváltozott a végrehajthatósági állapota, hogy a hozzá
kötött vezérlő (pl. gomb) ennek megfelelően engedélyezetté vagy tiltottá
váljon.

## Tartalom

A parancshoz kötött vezérlő a `CanExecute(Object)` metódus eredménye alapján
dönt arról, hogy engedélyezett-e: amennyiben a parancs nem hajtható végre, a
vezérlő kikapcsolt (letiltott) állapotba kerül. Ezt az állapotváltást a parancs
a `CanExecuteChanged` eseménnyel jelezheti bármikor:

- az eseményt egy megfelelő metódussal explicit módon is kiválthatjuk (pl.
  `RaisePropertyChanged`-hez hasonló mintával),
- vagy automatizálhatjuk az állapotfigyelést a `CommandManager` osztály
  `RequerySuggested` statikus eseménye segítségével — ezt a rendszer
  automatikusan meghívja, amikor beavatkozás szükségességét érzi (pl. ha
  valamilyen tevékenység fut a felületen); az egyik eseményt elfedhetjük a
  másikkal, ehhez az esemény feliratkozását/leiratkozását kell
  megváltoztatnunk.

A nézet és a nézetmodell közti üzenetváltás tipikus sorrendje (szekvencia):

1. a felhasználó kiváltja a vezérlő eseményét,
2. a vezérlő (View) meghívja a hozzá kötött parancs (`DelegateCommand`)
   `CanExecute(Object)` metódusát,
3. amennyiben a parancs végrehajtható (`opt [CanExecute(Object)]`), a
   vezérlő meghívja a parancs `Execute(Object)` metódusát,
4. a parancs végrehajtása a nézetmodellen (`ViewModel`) keresztül ér célba,
   pl. egy `Write(Object)` hívással.

## Kapocs

- [[concepts/esemalk/wpf-mvvm-parancsok-icommand]] — az `ICommand` interfész
  és a parancsminta alapjai, amelyre ez a lap épül
- [[concepts/esemalk/wpf-mvvm-delegatecommand]] — az általános célú
  `DelegateCommand` osztály, amely a `CanExecute`/`Execute` párt megvalósítja
- [[concepts/esemalk/wpf-vezerlok-tulajdonsagai]] — a vezérlők közös
  tulajdonságai, amelyek közé a parancshoz kötés (`Command`) is tartozik
- [[concepts/esemalk/modell-nezet-architektura]] — a modell/nézet
  architektúra, amelynek az MVVM (nézetmodellel kiegészített) változatában a
  parancsok élnek
- [[concepts/esemalk/wpf-mvvm-szamologep-pelda]] — a `DelegateCommand` és a
  `CanExecute`/`Execute` pár konkrét, végigvitt alkalmazása egy számológép
  példán
