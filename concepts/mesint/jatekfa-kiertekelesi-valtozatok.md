---
tags: [concept]
sources: [07.jatek.pdf]
derivation: source
kind: comparison
element: water
updated: 2026-10-12
---

# Játékfa-kiértékelési változatok

A részleges játékfa kiértékelésének alapváltozatán (rögzített mélységű részfa, [[concepts/mesint/minimax-algoritmus]]) javító változatok: az átlagoló, a váltakozó mélységű és a szelektív kiértékelés.

## Tartalom

### Átlagoló kiértékelés

(A dia a váltakozó mélységű előtt áll; itt csak a kontextus kedvéért.)

- Célja a kiértékelő függvény esetleges tévedéseinek simítása.
- MAX szintjeire az $m$ legnagyobb értékű gyerek ($max_m$) átlaga, a MIN szintjeire az $n$ legkisebb értékű gyerek ($min_n$) átlaga kerül: ez az $(m,n)$-átlagoló kiértékelés.
- A dia példája ($m=2$, $n=2$): az átlagoló eljárás a gyökérben 6.5-et ad a bal oldali lépésre, míg a sima minimax a jobb oldali ágat (9) választaná. A két módszer tehát eltérő lépést javasolhat.

### Váltakozó mélységű kiértékelés

- Célja, hogy a kiértékelő függvény **minden ágon reális értéket** mutasson. Megtévesztő lehet egy csúcs értéke, ha a szülőjénél a függvény lényegesen eltérő értéket ad: a játék ezen szakasza **nincs nyugalomban**.
- Egy adott szintig (**minimális mélység**) mindenképpen felépítjük a részfát.
- Ettől a szinttől egy másik szintig (**maximális mélység**) csak azon csúcsok gyerekeit állítjuk elő, amelyekre **nem teljesül a nyugalmi teszt**:

$$|f(\text{szülő}) - f(\text{csúcs})| < K,$$

ahol $K$ a nyugalmi konstans.

#### Példa

A dia: min. mélység $=3$, max. mélység $=5$, nyugalmi konstans $=3$. A harmadik szinten azokat a leveleket, amelyek értéke a szülőjükétől $K$-nál nagyobb mértékben tér el (pl. $-4$ vagy $8$ a $4$ szülő alatt), tovább bontjuk, legfeljebb az 5. szintig. A kapott gyökérérték 7, míg a rögzített mélységű minimax 6-ot adott, ami más lépést jelöl ki.

### Szelektív kiértékelés

- Célja a **memóriaigény csökkentése**.
- Elkülönítjük a lényeges és lényegtelen lépéseket, és csak a lényeges lépéseknek megfelelő részfát építjük fel.
- Ez a szétválasztás heurisztikus ismeretekre épül.

### Összevetés

| Változat | Mit old meg | Hogyan |
|---|---|---|
| átlagoló | a kiértékelő függvény tévedései | $m$ legjobb / $n$ legrosszabb gyerek átlaga |
| váltakozó mélységű | nem nyugalmi állások félrevezető értéke | nyugalmi teszt szerint mélyebb építés |
| szelektív | memóriaigény | csak a lényeges lépések részfája |

## Kapocs

- [[concepts/mesint/reszleges-jatekfa-kiertekeles]] — az alapprobléma, amelynek változatai ezek.
- [[concepts/mesint/minimax-algoritmus]] — az értékek felfuttatása; az átlagoló változat ennek módosítása.
- [[concepts/mesint/alfa-beta-algoritmus]] — a kiértékelés gyorsítása vágással.
- [[concepts/mesint/jatekot-jatszo-program]] — a változatok együtt, egy programban.
