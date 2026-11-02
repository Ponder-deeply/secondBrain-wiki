---
tags: [concept]
sources: [05-06.grafker.pdf]
derivation: source
kind: model
element: water
updated: 2026-10-12
---

# Kiértékelő függvény és működési grafikon

A gráfkeresés vezérlését a kiértékelő függvény ($f$) adja; ha ez csökkenő, a keresés soha nem terjeszt ki inkorrekt csúcsot, és a keresőgráf korrektsége időről időre magától helyreáll. A működési grafikon ennek elemzéséhez a kiterjesztett csúcsok $f$-értékeit sorolja fel a kiterjesztés sorrendjében.

## Tartalom

### Csökkenő kiértékelő függvény

Egy GK kiértékelő függvénye **csökkenő**, ha egy csúcsra adott értéke az algoritmus működése során nem növekszik, viszont mindig csökken, valahányszor a csúcshoz a korábbinál olcsóbb utat találunk. Például a $g$ költségfüggvény önmagában ilyen.

Csökkenő kiértékelő függvény mellett a GK

- **soha nem terjeszt ki inkorrekt csúcsot**;
- időről időre **automatikusan helyreállítja a keresőgráf korrektségét**, azaz a $\pi$ feszítőfa optimalitását és konzisztenciáját.

### Működési grafikon

Soroljuk fel a kiterjesztett csúcsokat a kiterjesztésük sorrendjében, a kiterjesztésükkor mért $f$ függvényértékükkel (vízszintes tengely: a kiterjesztési sorrend, $\Gamma$; függőleges: $f$). Ugyanaz a csúcs többször is szerepelhet, hiszen többször is kiterjesztődhet.

### Küszöbértékek és küszöbcsúcsok

Válasszuk ki az értékekből azt az $F^i$ ($i=1,2,\dots$) **monoton növekedő** részsorozatot, amely a legelső értékkel kezdődik, majd mindig a legközelebbi nem kisebb értékkel folytatódik.

- $F^i$ — $i$-dik **küszöbérték**, a hozzá tartozó csúcs $n_i$, az $i$-dik **küszöbcsúcs**;
- az $n_i$ és $n_{i+1}$ közötti szakasz az $i$-dik **árok**.

Állítás: csökkenő kiértékelő függvény használata mellett valahányszor **küszöbcsúcsot** terjeszt ki a GK, a $G$ keresőgráf **korrekt** lesz. Ez a későbbi algoritmus-elemzések (pl. [[concepts/mesint/a-csillag-algoritmus]]) alapja.

## Kapocs

- [[concepts/mesint/altalanos-grafkereso]] — az $\arg\min_f(OPEN)$ kiválasztás
- [[concepts/mesint/kereso-graf-korrektsege]] — a korrektség definíciója, amelyet itt a csökkenő $f$ biztosít
- [[concepts/mesint/nevezetes-grafkereso-algoritmusok]] — konkrét $f$ választások
- [[concepts/mesint/vezerlesi-strategiak]] — a vezérlés általános szerepe
- [[subjects/mesint]] — tárgyi hub
