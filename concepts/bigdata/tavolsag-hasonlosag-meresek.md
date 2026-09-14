---
tags: [concept]
sources: [BDAEM-2022-EA9.pptx]
references: ["Slides based on Eamonn Keogh's clustering lecture"]
derivation: source
updated: 2026-09-12
---

# Távolság- és hasonlóságmérték

A klaszterezéshez (és általában az objektumok összehasonlításához) egy
$D(O_1, O_2)$ távolságfüggvényt kell definiálni, amely két objektum
különbözőségét egyetlen valós számmal fejezi ki; a klaszterező algoritmusok
ezen mérték alapján döntik el, mely objektumok "hasonlítanak" egymásra.

## Tartalom

### Miért kell formálisan definiálni a távolságot?

A hasonlóság intuitív fogalom ("megismerjük, ha látjuk"), de a
klaszterezéshez ezt számszerűsíteni kell. A definíció: legyen $O_1$ és
$O_2$ két objektum a lehetséges objektumok univerzumából; a köztük lévő
távolságot (különbözőségét) a $D(O_1, O_2)$ valós szám fejezi ki.

### A távolságmérték elvárt tulajdonságai

Egy jól viselkedő $D$ távolságmértéknek négy tulajdonságot kell
teljesítenie:

- **Szimmetria**: $D(A,B) = D(B,A)$ — különben állíthatnánk, hogy "Alex
  hasonlít Bobra, de Bob egyáltalán nem hasonlít Alexre."
- **Önhasonlóság állandósága**: $D(A,A) = 0$ — különben állíthatnánk, hogy
  "Alex jobban hasonlít Bobra, mint Bob önmagára."
- **Pozitivitás (szeparáció)**: $D(A,B) = 0 \iff A = B$ — különben lennének
  a világunkban különböző, de megkülönböztethetetlen objektumok.
- **Háromszög-egyenlőtlenség**: $D(A,B) \le D(A,C) + D(B,C)$ — különben
  állíthatnánk, hogy "Alex nagyon hasonlít Bobra, és Alex nagyon hasonlít
  Carlra, de Bob és Carl egyáltalán nem hasonlítanak egymásra."

### K-means és az euklideszi távolság

A [[concepts/bigdata/k-means]] alapesetben az euklideszi távolságot
használja objektum és klaszterközéppont összevetésére. Az euklideszi
távolság akkor megfelelő, ha az adat izotróp és minden irányban egyenletesen
szóródik; nem invariáns lineáris (vagy egyéb, a távolságviszonyokat torzító)
transzformációkra, ezért felmerül a kérdés, hogy szükséges-e az adat
normalizálása a távolságszámítás előtt.

### Kvantitatív, ordinális és kategorikus változók távolsága

A távolságdefiníció a változó típusától függően eltér:

- **Kvantitatív változók**: közvetlenül számszerű mérték (pl. euklideszi
  vagy Manhattan-jellegű különbség) alkalmazható az adatpontok koordinátái
  között.
- **Ordinális változók**: a $(0,1)$ intervallumra képezhetők (rangsorolva,
  majd normalizálva), ezután egy kvantitatív metrika alkalmazható rájuk.
- **Kategorikus változók**: itt nincs természetes sorrend, ezért a
  kategóriapárok közötti távolságot a felhasználónak kell explicit módon
  megadnia.

Ha a leíráshoz több változótípus is tartozik, a gyakorlatban a
részváltozónkénti távolságokat **súlyozott összegként** szokás kombinálni
egyetlen végső távolságértékké.

### Szerkesztési (edit) távolság

Általános technika a hasonlóság mérésére: az egyik objektumot a másikba
transzformáljuk, és a ráfordított "erőfeszítést" tekintjük
távolságmértéknek. Karakterláncokra ez a **szerkesztési (edit) távolság**:
bármely $Q$ string átalakítható bármely $C$ stringgé csak
**helyettesítés** (substitution), **beszúrás** (insertion) és **törlés**
(deletion) műveletekkel; ha minden művelethez egységnyi költséget
rendelünk, a két string hasonlósága a legolcsóbb ilyen transzformáció
költsége.

Példa: a "Peter" és "Piotr" nevek szerkesztési távolsága 3 (egy
helyettesítés: e→i, egy beszúrás: o, egy törlés: e). Ugyanez az elv
alkalmazható nem szöveges objektumok összevetésére is (pl. két rajzfilmfigura
közti "átalakítási" költség kiszámolásával), és ez szolgál alapul a
[[concepts/bigdata/hierarchikus-klaszterezes]] egyik szemléltető példájához
(nevek dendrogramba rendezése szerkesztési távolság alapján).

## Kapocs

- [[concepts/bigdata/k-means]] — partícionáló algoritmus, amely alapesetben
  az euklideszi távolságot használja klaszterközépponthoz rendeléshez
- [[concepts/bigdata/hierarchikus-klaszterezes]] — a klaszterek közti
  távolság (linkage) definiálására épülő klaszterezési család
</content>
