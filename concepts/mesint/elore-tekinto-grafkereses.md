---
tags: [concept]
sources: [05-06.grafker.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-12
---

# Előre tekintő gráfkeresés

Az előre tekintő gráfkeresés kiértékelő függvénye pusztán a heurisztika: $f=h$ (a fekete-fehér kirakón $f=I$), vagyis a célhoz becsült közelséget követi, a megtett út költségét nem.

## Tartalom

A kereső mindig azt a nyílt csúcsot terjeszti ki, amelyik a heurisztika szerint a legközelebb van a célhoz. Ez a mélységi keresés ($f=-g$) és a szélességi keresés ($f=g$) heurisztikus párja ([[concepts/mesint/melysegi-es-szelessegi-grafkereses]]).

### A fekete-fehér kirakón

A dia heurisztikája: $I(n)$ = hány fehér elem áll a fekete után. Értékek a bejárt úton: start $2$, majd $2,\,2,\,1,\,1,\,0$ a célig; a másik ágak csúcsai $2$ és $1$.

- A keresés lényegében egyetlen úton megy le a célig (5 lépés).
- Mivel csak a becsült távolságot nézi, nem biztos, hogy rövid utat talál: itt 5 lépéses megoldást ad, a 4 lépéses optimum helyett.
- Az elemzési táblázat szerint $\mathit{mo}=5$, $G=8$, $\Gamma=5$ — ugyanaz, mint a mélységi keresésé.

### Tulajdonságai

- Gyors lehet, ha a heurisztika jó, de nem garantál optimumot, mert $g$-t nem veszi figyelembe.
- A $g$ és a heurisztika összegét használja az [[concepts/mesint/a-algoritmus]], amely ezt a hiányt pótolja.

## Kapocs

- [[concepts/mesint/heurisztika]] — az $I$ mint heurisztika a keresésben
- [[concepts/mesint/altalanos-grafkereso]] — a keret, amelybe $f=h$ beilleszkedik
- [[concepts/mesint/a-algoritmus]] — $f=g+h$
- [[concepts/mesint/fekete-feher-kirako]] — a feladat és az $I$, $M$ heurisztikák
- [[concepts/mesint/heurisztika-szerepe-a-grafkeresesben]] — a heurisztika hatása a keresésre
