---
tags: [concept]
sources: [08_ea_An3_2022_tavasz.pdf]
derivation: source
updated: 2026-09-14
---

# Abszolút szélsőérték korlátos zárt halmazon

Az egyváltozós Weierstrass-tétel ($f \in C[a,b]$-nek van abszolút maximum- és minimumhelye, amely vagy stacionárius pont, vagy végpont) direkt általánosítása: $\mathbb{R}^n \to \mathbb{R}$ függvény korlátos és zárt halmazon felvett abszolút szélsőértékét a belső stacionárius pontok és a peremen felvett értékek összevetésével találjuk meg.

## Tartalom

### A gondolatmenet

Az egyváltozós esetben, ha $f \in C[a,b]$, akkor a Weierstrass-tétel garantálja az abszolút maximum és minimum létezését, és ha $f$ egy $c$ pontban veszi fel valamelyiket, akkor vagy $c \in \{a,b\}$ (végpont), vagy $c \in (a,b)$ és $f \in D\{c\}$ esetén $f'(c) = 0$ (stacionárius pont). Ezért elég $f$ összes stacionárius pontját és a két végpontot megvizsgálni, és köztük a legnagyobb/legkisebb értéket kiválasztani.

Ez a gondolatmenet szó szerint átvihető többváltozós függvényekre.

### A tétel

Legyen $H \subset (\mathbb{R}^n, \|\cdot\|)$ korlátos és zárt (azaz [[concepts/analiii/kompakt-halmazok|kompakt]]) halmaz. Tegyük fel, hogy
- $f \in C(H)$,
- $f \in D(\operatorname{int} H)$.

Ekkor $f$-nek a $H$-n felvett értékei között van legkisebb és legnagyobb függvényérték; ezeket $f$ vagy a $H$ halmaz **határán** (vagyis $H \setminus \operatorname{int} H$ valamely pontjában) veszi fel, vagy pedig egy olyan $a \in \operatorname{int} H$ pontban, ahol $f'(a) = \theta_n$.

**Bizonyítás.** A [[concepts/analiii/weierstrass-tetel-kompakt-halmazon|Weierstrass-tétel]] szerint $\exists \min_H f$ és $\exists \max_H f$: a $H$ kompaktsága és $f$ folytonossága garantálja a létezést. Legyen $a \in H$ olyan pont, ahol $f$ értéke például a legnagyobb. Ha $a \in \operatorname{int} H$, akkor $a$-nak $f$-nek lokális szélsőértékhelye is, ezért a rá vonatkozó elsőrendű [[concepts/analiii/lokalis-szelsoertek-feltetelei|szükséges feltételből]] következik, hogy $f'(a) = \theta_n$. $\blacksquare$

### A gyakorlati recept

1. Számítsd ki $f'$-t, és oldd meg a $\operatorname{grad} f(x) = \theta_n$ egyenletrendszert $\operatorname{int} H$-n — ezek a belső stacionárius pontok.
2. Vizsgáld meg $f$-et a $H \setminus \operatorname{int} H$ határon külön (jellemzően egy paraméterezéssel vagy egyváltozós redukcióval, esetleg [[concepts/analiii/felteteles-szelsoertek|feltételes szélsőérték]] módszerével, ha a határ egy $\{g = 0\}$ alakú feltétellel írható le).
3. Számítsd ki $f$ értékét minden jelölt pontban (belső stacionárius pontok és a határ vizsgált pontjai), és a legnagyobb/legkisebb közülük adja az abszolút maximumot/minimumot.

Fontos, hogy a belső stacionárius pontokban *nem kell* eldönteni, hogy ott lokális szélsőérték van-e (a másodrendű feltételekkel) — elég az összes jelöltet kiszámítani és összehasonlítani, mert a létezést már a Weierstrass-tétel garantálja.

## Kapocs

- [[concepts/analiii/weierstrass-tetel-kompakt-halmazon]] — a létezési fél: kompakt halmazon folytonos függvénynek van abszolút szélsőértéke.
- [[concepts/analiii/lokalis-szelsoertek-feltetelei]] — az elsőrendű szükséges feltétel, amely a belső jelölteket kiválasztja.
- [[concepts/analiii/kompakt-halmazok]] — a korlátos és zárt halmaz fogalma.
- [[concepts/analiii/felteteles-szelsoertek]] — a határvizsgálat egyik eszköze, ha a perem egyenlettel adott.
- [[concepts/analii/abszolut-szelsertekek]] — az egyváltozós eredeti, $[a,b]$ intervallumon.
