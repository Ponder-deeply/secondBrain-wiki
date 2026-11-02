---
tags: [concept]
sources: [05-06.grafker.pdf]
derivation: source
kind: theorem
element: water
updated: 2026-10-12
---

# A* algoritmus

Az $A^*$ az $A$ algoritmus ($f=g+h$) megengedhető heurisztikával: megengedhető feladaton optimális megoldást talál. Hatékonyságát a memóriaigénnyel és a futási idővel mérjük, megengedhető (megoldható, megengedhető heurisztikájú) feladatokon.

## Tartalom

### Hatékonyság

A hatékonyság két szempontból vizsgálható:

- **Memóriaigény**: a terminálás pillanatában a zárt csúcsok száma jól jellemzi a keresési gráf méretét ([[concepts/mesint/a-csillag-memoriaigenye]]).
- **Futási idő**: a kiterjesztések száma a zárt csúcsok számához viszonyítva ([[concepts/mesint/a-csillag-futasi-ideje]]).

Az elemzés **megengedhető feladatokon** folyik: a feladatnak van megoldása, és ismert hozzá megengedhető heurisztika ($h\le h^*$), tehát $A^*$ optimális megoldást talál.

### Fő eredmények

- Az $A^*$ memóriaigénye nem rosszabb más, hasonló eredményt adó (megengedhető heurisztika esetén optimumot garantáló, ún. megengedhető) algoritmusokénál; ilyenek az egyenletes költségű keresés ($f=g+0$), az $A^{**}$, a $B$ és a $B'$.
- Azt **nem** lehet belátni, hogy az $A^*$ jobb, sőt hogy nem rosszabb a többinél *az összes* megengedhető heurisztikájú feladatra nézve. Viszont olyan másik megengedhető algoritmus sincs, amely az összes ilyen feladatra jobb vagy legalább nem rosszabb lenne a többinél.
- **Monoton megszorításos** heurisztikájú feladatokon az $A^*$ nem rosszabb a többi megengedhető algoritmusnál.
- **Nem patologikus** feladatokon (van olyan optimális megoldási út, amelynek a célcsúcson kívül minden csúcsára $h<h^*$) szintén nem rosszabb. Ennyiben „$A^*$-nál nincs jobb”.
- A futási idő felső korlátja az $A^*$-nál is exponenciális lehet (Martelli példája).

### Mi köze a $B$ és $B'$ változatokhoz

A $B$ váltogatva használja az $f=g+h$ és $f=g$ kiértékelést; a $B'$ az $A$ algoritmus, de a $h$ értékei kiterjesztésenként változnak. Ld. [[concepts/mesint/b-algoritmus]], [[concepts/mesint/b-vesszo-algoritmus]].

## Kapocs

- [[concepts/mesint/a-algoritmus]] — az $f=g+h$ keresés és a fekete-fehér példa
- [[concepts/mesint/a-csillag-memoriaigenye]] — $\mathit{CLOSED}$ szerinti összehasonlítás
- [[concepts/mesint/a-csillag-futasi-ideje]] — $k\le\Gamma\le 2^{k-1}$
- [[concepts/mesint/heurisztikus-fuggveny-tulajdonsagai]] — megengedhetőség, monotonitás
- [[concepts/mesint/nevezetes-grafkereso-algoritmusok]] — az algoritmuscsalád
- [[concepts/mesint/heurisztika-szerepe-a-grafkeresesben]] — a heurisztika szerepe
