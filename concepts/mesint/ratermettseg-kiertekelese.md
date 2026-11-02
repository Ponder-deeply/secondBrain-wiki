---
tags: [concept]
sources: ["08.evolucio.pdf"]
derivation: source
kind: definition
element: fire
updated: 2026-10-12
---

# Rátermettség kiértékelése

A rátermettségi (fitnesz) függvény minden egyedhez számértéket rendel, amely a célhoz való közelségét méri; ez alapján hasonlítja össze és választja ki az egyedeket az evolúciós algoritmus.

## Tartalom

A függvénynek kapcsolatban kell állnia a kódolással és a céllal ([[concepts/mesint/evolucios-algoritmus-tervezese]]). Példák:

| probléma | rátermettségi függvény |
|---|---|
| n-királynő | ütésben nem lévő királynőpárok száma (8 királynőre legfeljebb $\binom{8}{2}=28$; a példa egyedének értéke 23) |
| SAT | az igazra értékelt klózok száma |
| gráfszínezés | direkt kódnál a jó élek száma, indirektnél a kiszínezett csúcsok száma |
| kő-papír-olló | a stratégia által egy mintán elért pontszám |

### Kő-papír-olló: a rátermettség kiszámítása

Adott egy **minta**: a játékos és az ellenfél korábbi lépéseinek sorozata (pl. `000222122200 1000` és `0102112220101 1`). A kiértékelés:

1. A minta minden pozíciójához vesszük az előző két csata előzményét (ÉnŐÉnŐ), ebből kódolt szám adja az esetet.
2. A stratégia megfelelő jele a **javaslat**; ezt az ellenfél tényleges következő lépéséhez hasonlítjuk.
3. Pontozás: vereség $-1$, döntetlen $0$, győzelem $+1$. Pl. `0001` esetén a javaslat 2 (olló): ha az ellenfél 0-t (kő) játszik, vereség ($-1$), ha 1-et (papír), győzelem ($+1$); `0100` → javaslat 1, ellenfél 1: döntetlen.
4. A rátermettség a pontszámok összege az egész mintán.

### Szerepe a szelekcióban

A rátermettségi érték dönti el, kik kerülnek a szelekcióba (küszöbérték, rangsor, rulettkerék-arány; [[concepts/mesint/szelekcio]]), és a visszahelyezésben kik váltják a rosszabb egyedeket ([[concepts/mesint/visszahelyezes]]). A terminálási feltétel is rátermettségi értéken alapul: célegyed megjelenése vagy az egyesített érték stagnálása.

## Kapocs

- [[concepts/mesint/evolucios-kodolas]] — a függvény a kódolt egyedeken van értelmezve
- [[concepts/mesint/evolucios-algoritmus]] — az algoritmus, amelyben a függvény használatos
- [[concepts/mesint/szelekcio]] — a rátermettség alapján választ
- [[concepts/mesint/kiertekelo-fuggveny-es-mukodesi-grafikon]] — a gráfkeresők kiértékelő függvénye, rokon fogalom
