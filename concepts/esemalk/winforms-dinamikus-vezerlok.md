---
tags: [concept]
sources: [elte_eva_ea03_winforms_dynamic.pdf]
derivation: source
updated: 2026-09-13
---

# WinForms vezérlők dinamikus kezelése

Vezérlők (`Control`-leszármazottak) nem csak a designerrel, hanem futás közben,
kódból is létrehozhatók, konfigurálhatók és eltávolíthatók.

## Tartalom

Egy vezérlő az alkalmazás futása közben, kódban is példányosítható — ilyenkor
a tulajdonságait (pozíció, méret, felirat, …) és az eseménykezelő-társításait
ugyanúgy be tudjuk állítani, mint a designer által generált kódban.

A dinamikusan létrehozott vezérlő csak akkor jelenik meg az ablakon (vagy egy
másik tartalmazó vezérlőn), ha felvesszük annak `Controls` listájába:

```csharp
this.Controls.Add(myLabel);
```

Ha a vezérlőt el akarjuk távolítani a felületről, ki kell venni a `Controls`
listából; a vezérlő maga esetlegesen manuálisan is megsemmisíthető a
`Dispose(…)` metódussal, de erre csak ritkán van szükség (a Garbage Collector
általában gondoskodik róla).

### Példa: dinamikusan generált rácsgomb-tábla

A dia egy olyan feladatot dolgoz fel, ahol egy `TableLayoutPanel`-be futás
közben generált gombrácsot kell elhelyezni (lásd
[[concepts/esemalk/winforms-elrendezok]]): a gombok egy `GridButton` (a
`Button`-ból származó) típus példányai, amelyek eltárolják a rácsbeli
koordinátájukat (`GridX`, `GridY` tulajdonságok), majd egyenként kerülnek fel
a `Controls` listára:

```csharp
_buttons[i, j] = new GridButton(i, j);
_buttons[i, j].BackColor = Color.White;
_buttons[i, j].Dock = DockStyle.Fill;
_buttons[i, j].Click += new EventHandler(GridButton_Click);
_tableLayoutGrid.Controls.Add(_buttons[i, j], j, i);
```

A tábla mérete (sorok/oszlopok száma) tetszőlegesen újragenerálható: a régi
rácsot töröljük, majd egy új, üres rácsot építünk fel ugyanezzel a mintával.

### Példa: Tic-Tac-Toe

A második kidolgozott példa (Tic-Tac-Toe) egy kétrétegű architektúrában
(lásd [[concepts/esemalk/modell-nezet-architektura]]) mutatja be a
dinamikus felület és az eseményvezérlés összjátékát: a modell
(`TicTacToeModel`) egy mátrixban tárolja a mezők állását, a soron következő
játékost és a lépésszámot, egy felsorolási típussal (`Player`) reprezentálva a
mezőértékeket. A modell saját eseményekkel (`FieldChanged`, `GameWon`,
`GameOver`) és hozzájuk tartozó, egyedi `EventArgs`-leszármazott típusokkal
(`FieldChangedEventArgs`, `GameWonEventArgs`) jelzi az állapotváltozásokat a
nézet felé — ez a mintázat megegyezik a
[[concepts/esemalk/esemeny-letrehozasa-kivaltasa]] lapon leírt, saját esemény
létrehozásának módjával. A nézet (`TicTacToeForm`) a mezőknek megfelelő
`GridButton`-okat dinamikusan generálja, és iratkozik fel a modell
eseményeire.

## Kapocs

- [[concepts/esemalk/winforms-vezerlok-alapjai]] — a `Control` osztály és a
  statikusan (designerrel) létrehozott vezérlők alapjai
- [[concepts/esemalk/winforms-elrendezok]] — a dinamikusan létrehozott
  vezérlők elrendezése (`FlowLayoutPanel`, `TableLayoutPanel`, `Dock`,
  `AutoSize`)
- [[concepts/esemalk/vezerlo-esemenykezelo-tarsitas]] — eseménykezelők
  vezérlőhöz társítása, ami dinamikus vezérlőknél kódból történik
- [[concepts/esemalk/esemeny-letrehozasa-kivaltasa]] — saját esemény és
  `EventArgs`-leszármazott létrehozása, ahogy a Tic-Tac-Toe modell is használja
- [[concepts/esemalk/modell-nezet-architektura]] — a Tic-Tac-Toe példa
  modell/nézet felépítése
- [[concepts/esemalk/csharp-felsorolasi-tipus]] — a `Player` felsorolási
  típus
