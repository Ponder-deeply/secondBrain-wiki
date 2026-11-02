---
tags: [concept]
sources: [05-06.grafker.pdf]
derivation: source
kind: procedure
element: water
updated: 2026-10-12
---

# B algoritmus

A B algoritmus az A algoritmus módosítása: egy árkon belül a csúcsokat a $g$ költség szerint választja ki, így a küszöbcsúcsok kiterjesztése nem ismétlődik, és a kiterjesztések száma legfeljebb négyzetes.

## Tartalom

### A probléma és a másodlagos kiértékelő függvény

Az A algoritmus (lásd [[concepts/mesint/a-algoritmus]]) az $f$ értékei szerint halad; az $f$ értékei egy működési grafikonon (lásd [[concepts/mesint/kiertekelo-fuggveny-es-mukodesi-grafikon]]) *árkokat* alkotnak: az $i$-dik árok az $F^i$ küszöbértéknél (a küszöbcsúcs $f$-értékénél) végződik. Egy csúcs – akár egy árkon belül is – **többször kiterjesztődhet**, ez okozza az exponenciális futási időt (lásd [[concepts/mesint/a-csillag-futasi-ideje]]).

Ötlet: használjunk az árkokon belül egy **másodlagos (belső) kiértékelő függvényt**. Bizonyítható, hogy ettől

- az egy árokban kiterjesztett csúcsok halmaza nem változik,
- csak a csúcsok árkon belüli kiterjesztési sorrendje lesz más,
- a küszöbcsúcsok, azok sorrendje és értékei változatlanok maradnak.

A belső kiértékelő függvény tehát csak a futási időt (a kiterjesztések számát) befolyásolja.

### A B algoritmus

Martelli a belső kiértékelő függvénynek a $g$ költségfüggvényt javasolta. A B algoritmust az A algoritmusból kapjuk úgy, hogy bevezetjük az $F$ aktuális küszöbértéket, majd

- az 1. lépést kiegészítjük az $F := f(s)$ értékadással,
- a 4. lépést (a kiterjesztendő csúcs kiválasztása) lecseréljük az alábbi elágazásra:

```
if min_f(OPEN) < F
  then n := arg min_g { m ∈ OPEN | f(m) < F }
  else n := arg min_f(OPEN); F := f(n)
endif
```

Azaz amíg van az aktuális küszöbnél kisebb $f$-értékű nyílt csúcs, azok közül a legkisebb $g$-jűt terjesztjük ki; ha nincs, új árok kezdődik: a legkisebb $f$-ű csúcs lesz az új küszöbcsúcs, és $F$ az értéke.

### Futási idő

A B algoritmus ugyanúgy működik, mint az A\*, azzal a kivétellel, hogy **egy árokhoz tartozó csúcsot csak egyszer terjeszt ki**.

Legrosszabb esetben:

- minden zárt csúcs először küszöbcsúcsként terjesztődik ki (csökkenő kiértékelő függvény mellett egy csúcs csak egyszer, a legelső kiterjesztésekor lehet küszöb);
- az $i$-dik árok legfeljebb az összes addigi $i-1$ darab küszöbcsúcsot tartalmazhatja (a start csúcs nélkül);
- így az összes kiterjesztések száma legfeljebb $\tfrac12 k^2$ (a $k$ a kiterjesztett csúcsok száma; a dia a $k$-t nem definiálja külön).

Tehát az A\* legrosszabb esetben exponenciális futási idejéhez képest a B algoritmus négyzetes.

### Mikor nem érdemes

Ha a heurisztika kielégíti a monoton megszorítást, az A\* eleve nem terjeszt ki csúcsot kétszer, ezért a B algoritmus nem ad előnyt (lásd [[concepts/mesint/heurisztika-szerepe-a-grafkeresesben]]).

## Kapocs

- [[concepts/mesint/a-algoritmus]] — az algoritmus, amelyet a B módosít
- [[concepts/mesint/a-csillag-futasi-ideje]] — az exponenciális legrosszabb eset, amit a B négyzetesre csökkent
- [[concepts/mesint/b-vesszo-algoritmus]] — a másik módosítás: a heurisztikát javítja futás közben
- [[concepts/mesint/heurisztika-szerepe-a-grafkeresesben]] — mikor érdemes B-t használni
- [[concepts/mesint/kiertekelo-fuggveny-es-mukodesi-grafikon]] — árok és küszöbcsúcs fogalma
