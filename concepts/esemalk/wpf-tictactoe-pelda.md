---
tags: [concept]
sources: [elte_eva_ea06_wpf_basics.pdf, elte_eva_ea08_wpf_complex_resources.pdf]
derivation: source
updated: 2026-09-13
---

# Tic-Tac-Toe példa WPF felülettel

Egy Tic-Tac-Toe program WPF felhasználói felülettel megvalósítva, amelyben két
játékos küzdhet egymás ellen.

## Tartalom

- Új felhasználói felület WPF segítségével (`TicTacToeWindow`).
- A felületre egy menü (`Menu`), valamint egy rács (`Grid`) kerül a
  játéktáblának; utóbbi tartalmát dinamikusan generáljuk, gombokból
  (`Button`) építve mátrixot. Mivel minden cella kitöltésre kerül, alternatív
  megoldásként `UniformGrid` is használható.
- Eseménykezelők: betöltés (`Window_Loaded`), méretváltás
  (`Window_SizeChanged`), menüpontok (`MenuGameNew_Click`,
  `MenuGameLoad_Click`, `MenuGameSave_Click`, `MenuGameExit_Click`), gombok
  (`Button_Click`), valamint a modell eseményei (`Model_GameWon`,
  `Model_GameOver`, `Model_FieldChanged`).
- A fájl betöltés/mentés dialógusablakait (`OpenFileDialog`,
  `SaveFileDialog`) a kódban hozzuk létre (nem XAML-ben deklaráljuk).
- Tervezés szerint a `View::TicTacToeWindow` a `Model::TicTacToeModel`
  osztályt egy `_model` mezőn keresztül birtokolja (kompozíció), a
  `_buttonGrid` mező pedig a dinamikusan generált gombmátrixot tárolja.
- **Megvalósítás `Grid`-del:** a XAML-ben egy üres, `x:Name="_gameGrid"`
  nevű `Grid` szerepel; a `GenerateTable()` metódus 3×3 `Button`-t hoz létre,
  és mindegyiken a csatolt `Grid.RowProperty`/`Grid.ColumnProperty`
  függőségi tulajdonságot állítja be `SetValue`-val, hogy a gomb a
  megfelelő cellába kerüljön.
- **Alternatív megvalósítás `UniformGrid`-del:** a `_gameGrid` helyett
  `UniformGrid Rows="3" Columns="3"` szerepel a XAML-ben; mivel a
  `UniformGrid` a gyermekeit automatikusan, sorfolytonosan tölti fel rács
  alakban, a `GenerateTable()`-ből elhagyható a `Grid.RowProperty`/
  `Grid.ColumnProperty` csatolt tulajdonságok beállítása.

### Grafikus megjelenítés triggerekkel és egyedi sablonnal

A táblát grafikus alakzatokkal (`Line`, `Ellipse`, `Rectangle`) is
megjeleníthetjük karakterek helyett:

- az elemek `DataTrigger` segítségével változnak a mezőn tárolt karakter
  hatására (amely a lehetséges `Player` értékeket figyeli)
- ugyanakkor továbbra is gombokat jelenítünk meg (amely kattintható), de
  felüldefiniáljuk a sablont (`Template`) egy egyedi felépítéssel
  (`ControlTemplate`), így a gomb megjelenése teljesen más lesz, pl.:

```xml
<!-- TicTacToeWindow.xaml -->
<Style.Triggers>
    <DataTrigger Binding="{Binding Player}" Value="O">
        <Setter Property="Template">
            <!-- a gomb sablonját cserélgetjük -->
            <Setter.Value>
                <ControlTemplate>
                    <Canvas Background="White">
                        <Ellipse … />
                    </Canvas>
                </ControlTemplate>
            </Setter.Value>
        </Setter>
    </DataTrigger>
    …
</Style.Triggers>
```

## Kapocs

- [[concepts/esemalk/wpf-panelek]] — a játéktábla `Grid`/`UniformGrid`
  alapú, dinamikusan generált elrendezése
- [[concepts/esemalk/wpf-fuggosegi-tulajdonsagok]] — a `Grid.RowProperty`/
  `Grid.ColumnProperty` csatolt tulajdonságok és a `SetValue` hívás, amellyel
  a `Grid`-es változat elhelyezi a gombokat
- [[concepts/esemalk/winforms-dinamikus-vezerlok]] — vezérlők dinamikus
  létrehozása WinForms-ban; ugyanaz a minta, más keretrendszer
- [[concepts/esemalk/tictactoe-haromreteg-pelda]] — a Tic-Tac-Toe példa
  WinForms-alapú, háromrétegű architektúrás változata — a két példa a modell
  szintjén rokon, de a nézet (View) rétege eltérő keretrendszerben készül
- [[concepts/esemalk/modell-nezet-architektura]] — a modell/nézet szétválasztás
  elve, amelyet ez a példa is követ
- [[concepts/esemalk/wpf-stilus-triggerek]] — a `DataTrigger` és
  `ControlTemplate` alapú megjelenítés-váltás általános eszközei
