---
tags: [concept]
sources: ["08.evolucio.pdf"]
derivation: source
kind: comparison
element: water
updated: 2026-10-12
---

# Szelekció

A szelekció az evolúciós algoritmus első operátora: a rátermett egyedeket választja ki szülőnek úgy, hogy a rosszabbak kiválasztása is kapjon esélyt.

## Tartalom

**Célja:** a rátermett egyedek kiválasztása, de a gyengébbeknek is legyen esélyük (ez őrzi meg a populáció változatosságát; tisztán a legjobbak választása a keresést zsákutcába vihetné).

Fő változatok:

- **Rátermettség arányos** (rulettkerék-algoritmus): minél jobb az elem rátermettségi függvényértéke, annál nagyobb valószínűséggel választja ki. A rulettkeréken az egyed annyi szeletet kap, amennyi a rátermettsége: a SAT-példában a `01000` (2), `11010` (3), `01100` (1), `11000` (2) egyedekből 8 szeletes kerék lesz.
- **Rangsorolásos:** a rátermettség alapján sorba rendezett egyedek közül a kisebb sorszámúakat nagyobb valószínűséggel választja.
- **Versengő** (tournament): véletlenül kiválasztott egyedcsoportok (pl. párok) legjobb egyedét választja ki.
- **Csonkolásos** (selejtezős): a rátermettség szerint legjobb (adott küszöbérték feletti) valahány egyedből véletlenszerűen választ néhányat. A 8-királynő példában a 15-nél jobb rátermettségűek közül lehetőleg a jobbak kerülnek ki.

A permutációs n-királynő példában a szelekció az egész populációt kiválasztja (mindet).

## Kapocs

- [[concepts/mesint/ratermettseg-kiertekelese]] — a kiválasztás alapja
- [[concepts/mesint/evolucios-algoritmus]] — az operátorok sorrendje a ciklusban
- [[concepts/mesint/rekombinacio-es-keresztezes]] — a kiválasztott szülők következő lépése
- [[concepts/mesint/visszahelyezes]] — az utódok visszahelyezése, a szelekció párja
