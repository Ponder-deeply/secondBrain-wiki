---
tags: [concept]
sources: [05-06.grafker.pdf]
derivation: source
kind: procedure
element: water
updated: 2026-10-12
---

# Általános gráfkereső algoritmus

A gráfkeresés olyan keresőrendszer, amely a reprezentációs gráf startcsúcsból kiinduló, már feltárt útjait (keresőgráf) tartja a munkaterületén, és mindig a kiértékelő függvény szerint legkedvezőbb nyílt csúcsot terjeszti ki. Az általános gráfkereső (GK) az ebből származó összes nevezetes algoritmus közös váza.

## Tartalom

### A gráfkeresés mint KR

A [[concepts/mesint/kereso-rendszer]] három komponenséből:

- **globális munkaterület:** a startcsúcsból kiinduló, már feltárt utak a reprezentációs gráfban (a **keresőgráf**, $G$), valamint a feltárt utak végei (a **nyílt csúcsok**, $OPEN$);
  - kiinduló érték: a startcsúcs,
  - terminálási feltétel: vagy célcsúcsot terjeszt ki, vagy nincs nyílt csúcs;
- **keresési szabály:** egy nyílt csúcs **kiterjesztése** (összes gyermekének és a hozzájuk vezető éleknek az előállítása);
- **vezérlési stratégia:** a legkedvezőbb csúcs kiterjesztésére törekszik, ehhez egy **kiértékelő függvényt** használ (lásd [[concepts/mesint/vezerlesi-strategiak]], [[concepts/mesint/kiertekelo-fuggveny-es-mukodesi-grafikon]]).

### Jelölések

- $G$ — keresőgráf: a reprezentációs gráf eddig felfedezett és egyben el is tárolt része;
- $OPEN$ — kiterjesztésre váró csúcsok, amelyek gyerekeit még nem vagy nem eléggé jól ismerjük;
- $f: OPEN \to \mathbb{R}$ — kiértékelő függvény, kiválasztja a kiterjesztendő nyílt csúcsot;
- $\pi$ — szülőre visszamutató pointer, $g$ — költségfüggvény (lásd [[concepts/mesint/kereso-graf-korrektsege]]);
- $\Gamma(n)$ — $n$ gyerekei, $c(n,m)$ az $(n,m)$ él költsége.

### Az algoritmus

Ez a modell-független keretalgoritmus ($\text{ADAT} := \text{kezdeti érték}$; while nem terminál: válassz alkalmazható szabályt, alkalmazd) konkrétan:

1. $G := (\{start\}, \emptyset)$; $OPEN := \{start\}$; $g(start) := 0$; $\pi(start) := nil$
2. loop
3. &nbsp;&nbsp;&nbsp;if $OPEN = \emptyset$ then return *nincs megoldás*
4. &nbsp;&nbsp;&nbsp;$n := \arg\min_f(OPEN)$
5. &nbsp;&nbsp;&nbsp;if $cél(n)$ then return *megoldás*
6. &nbsp;&nbsp;&nbsp;$OPEN := OPEN - \{n\}$
7. &nbsp;&nbsp;&nbsp;for $\forall m \in \Gamma(n) - \pi(n)$ loop
8. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if $m \notin G$ or $g(n)+c(n,m) < g(m)$ then
9. &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;$\pi(m) := n$; $g(m) := g(n)+c(n,m)$; $OPEN := OPEN \cup \{m\}$
10. &nbsp;&nbsp;&nbsp;endloop
11. &nbsp;&nbsp;&nbsp;$G := G \cup \{(n,m) \in A \mid m \in \Gamma(n)-\pi(n)\}$
12. endloop

A célt a **kiterjesztéskor** ismeri fel (5. sor), nem előállításkor. A megoldási utat a $\pi$ pointerek visszafelé követésével kapjuk.

### Működés és eredmény

A diában bizonyítható állítások (a bizonyítás nincs a diákon), $\delta$-gráfban (a gráf véges elágazású, az élköltségek egy $\delta>0$ alsó korlát felett vannak):

- a GK működése során egy csúcsot legfeljebb véges sokszor terjeszt ki (ebből következik, hogy körökre nem érzékeny);
- **véges** $\delta$-gráfban mindig terminál;
- ha egy **véges** $\delta$-gráfban létezik megoldás, akkor a GK megoldás megtalálásával terminál.

### Szemléltetés

A diasor a Hanoi tornyai állapotgráfján (három korong, állapotok $[a,b,c]$ alakban, $[3,3,3] \to [1,1,1]$) mutat egy kiterjesztési sorrendet kilenc lépésben; lásd [[concepts/mesint/hanoi-tornyai]].

## Kapocs

- [[concepts/mesint/kereso-rendszer]] — a KR három komponense, amelynek a GK egy példánya
- [[concepts/mesint/kereso-graf-korrektsege]] — a $\pi$ és $g$ karbantartása, helyesség
- [[concepts/mesint/kiertekelo-fuggveny-es-mukodesi-grafikon]] — $f$ megválasztása és hatása
- [[concepts/mesint/nevezetes-grafkereso-algoritmusok]] — $f$ konkrét választásaiból adódó algoritmusok
- [[concepts/mesint/melysegi-es-szelessegi-grafkereses]] — nem-informált példányok részletesen
- [[concepts/mesint/a-algoritmus]] — heurisztikus példányok
- [[concepts/mesint/utkereses-delta-grafban]] — a $\delta$-gráf fogalma
- [[subjects/mesint]] — tárgyi hub
