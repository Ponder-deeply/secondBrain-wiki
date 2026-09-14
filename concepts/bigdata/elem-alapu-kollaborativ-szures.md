---
tags: [concept]
sources: [BDAEM-2022-EA11.pdf]
derivation: source
updated: 2026-09-12
---

# Elem-alapú kollaboratív szűrés

Memóriaalapú kollaboratív szűrési módszer, amely — a felhasználó-alapú
változattal szemben — nem a felhasználók, hanem az **elemek** közti
hasonlóságot használja fel az előrejelzéshez, és emiatt jobban skálázódik nagy
felhasználószám mellett.

## Tartalom

### Az algoritmus lépései

1. Megvizsgálja azokat az elemeket, amelyeket a célfelhasználó már
   értékelt.
2. Kiszámítja, mennyire hasonlóak ezek a célelemhez — **kizárólag más
   felhasználók korábbi értékelései** alapján.
3. Kiválasztja a $k$ legjobban hasonló elemet.
4. Az előrejelzést a célfelhasználó ezen leghasonlóbb elemekre adott
   értékeléseinek súlyozott átlagolásával számítja.

### Elem-hasonlóság számítása

Az $i$ és $j$ elem hasonlóságát úgy számítjuk, hogy megkeressük azokat a
felhasználókat, akik mindkettőt értékelték, és egy hasonlósági függvényt
alkalmazunk az értékeléseikre. A forrás a **koszinusz-alapú hasonlóságot**
emeli ki, amelyben az elemek az $m$-dimenziós felhasználói térben vektorok
(ez a módszer nem veszi figyelembe a felhasználók közti eltérő
értékelési skálát):

$$S(i,j) = \cos(\vec{i},\vec{j}) = \frac{\vec{i}\cdot\vec{j}}{\|\vec{i}\|_2 \cdot \|\vec{j}\|_2}$$

### Előrejelzés: súlyozott összeg

Az előrejelzést a célfelhasználó saját, hasonló elemekre adott értékeléseinek
súlyozott átlagaként (weighted sum) számítjuk:

$$P_{u,i} = \frac{\sum_{\text{minden hasonló elem } N} (S_{i,N} \cdot R_{u,N})}{\sum_{\text{minden hasonló elem } N} |S_{i,N}|}$$

ahol $S_{i,N}$ az $i$ célelem és az $N$ hasonló elem hasonlósága, $R_{u,N}$
pedig a célfelhasználó $u$ értékelése az $N$ elemre.

### Levezetett példa

Ugyanazon a 6 felhasználós, 5 filmes mátrixon (Sherlock, House of Cards,
Avengers, Breaking Bad, Walking Dead) a forrás bemutatja, hogy egy adott
célelemre (pl. Avengers) hogyan alakul ki az $sim(i,j)$ hasonlósági sor a
többi elemhez képest (pl. $-1$, $-1$, $0{,}86$, $1$, `NA` — az utolsó azért
`NA`, mert nincs olyan felhasználó, aki mindkét elemet értékelte volna). A
kiszámított hasonlóságokat és a célfelhasználó saját értékeléseit a súlyozott
összeg képletébe helyettesítve adódnak az előrejelzett értékek (pl.
$2{,}94^*$, $2{,}48^*$, $1{,}12^*$ a táblázat utolsó oszlopában).

### Teljesítmény: offline/online szétválasztás

A hasonlóságszámítás a fő szűk keresztmetszet (bottleneck): milliós
nagyságrendű felhasználó- és elemszám mellett rendkívül időigényes. A
gyakorlati megoldás a szomszédság-generálás és az előrejelzés lépéseinek
elkülönítése:

- **offline komponens** ("modell") — a hasonlóságszámítás előre, ütemezve
  történik, és az eredményt tárolják;
- **online komponens** — csak az előrejelzés-generálás fut valós időben, ez
  már olcsó művelet.

Mivel az elemek száma jellemzően lényegesen kisebb és stabilabb, mint a
felhasználóké, az elem-elem hasonlóságok előre számítása és cache-elése jobban
skálázódik, mint a felhasználó-alapú változat.

## Kapocs

- [[concepts/bigdata/ajanlorendszerek-alapjai]] — a kollaboratív szűrés helye a
  tartalomalapú/kollaboratív, illetve memória-/modellalapú felosztásban
- [[concepts/bigdata/felhasznalo-alapu-kollaborativ-szures]] — a másik
  memóriaalapú szomszédsági módszer, amely felhasználók hasonlóságára épít, és
  a ritkaság/skálázhatóság szempontjából rosszabbul teljesít
- [[concepts/bigdata/matrixfaktorizacio-ajanlorendszerekben]] — modellalapú
  alternatíva, amely rejtett faktorokkal kezeli a ritkasági problémát
