---
tags: [concept]
sources: [10.bizonytalansag.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-12
---

# Bayes-háló tervezése

A Bayes-háló felépítése iteratív eljárás: a tárgytartomány változóit meghatározott sorrendben vesszük fel csúcsként, mindegyiknek megkeressük a közvetlen befolyásoló változóit (szülőit), majd kitöltjük a feltételes valószínűségi táblázatát (FVT).

## Tartalom

### Az eljárás lépései

Először meghatározzuk a tárgytartományt leíró változók halmazát, majd egy rögzített sorrendben dolgozzuk fel őket:

1. Válasszunk ki olyan változót, amely **kizárólag a már hálóhoz csatolt változóktól** függ, és vegyük fel új csúcsként a hálóba.
2. A hálóbeli változók közül vegyük azt a **minimális halmazt**, amely közvetlenül hat az új változóra; rajzoljuk be az ezeket a függőségeket reprezentáló éleket (szülő $\to$ új csúcs).
3. Töltsük ki az új csúcs FVT-jét (a szülők értékkombinációira megadott feltételes valószínűségekkel).
4. Vissza az 1. lépésre, amíg van feldolgozatlan változó.

A sorrend számít: ha az okokat az okozatok előtt vesszük fel, a háló általában ritkább (kevesebb él, kisebb FVT-k), így kevesebb valószínűséget kell megadni.

### Példa a hálóra: betörés–riasztás–szomszéd

Russel–Norvig példája (a szomszéd telefonál, hogy szól a riasztó; betörtek hozzánk?): láncszerű háló, $Betörés \to Riasztás \to Szomszéd$.

- $p(B) = 0{,}001$
- $p(R \mid B) = 0{,}95$, $p(R \mid \neg B) = 0{,}001$
- $p(Sz \mid R) = 0{,}9$, $p(Sz \mid \neg R) = 0{,}05$

A csúcsok felvételi sorrendje $B, R, Sz$; a $Sz$ szülője csak $R$, mert a betörés már csak a riasztáson keresztül hat a szomszéd hívására (ld. [[concepts/mesint/felteteles-fuggetlenseg]]). A példa kiszámítását ld. [[concepts/mesint/bayes-halo-kovetkeztetes]].

## Kapocs

- [[concepts/mesint/bayes-halo]] — a háló mint reprezentáció (csúcsok, élek, FVT)
- [[concepts/mesint/felteteles-fuggetlenseg]] — a szülők minimális halmazának kijelölése ezen alapul
- [[concepts/mesint/bayes-halo-kovetkeztetes]] — a megtervezett hálón végzett számítás
- [[concepts/mesint/bayes-halo-tanulasa]] — a FVT és a szerkezet példákból való megtanulása
