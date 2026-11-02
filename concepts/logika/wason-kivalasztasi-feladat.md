---
tags: [concept]
sources: [MintaZH1.pdf]
derivation: inferred
kind: pitfall
element: fire
updated: 2026-10-19
---

# Wason-féle kiválasztási feladat (1966)

A Wason-feladat egy „ha $p$, akkor $q$” állítás ellenőrzésének klasszikus logikai csapdája: a kérdés az, mely kártyákat kell minimálisan megfordítani, hogy az implikáció igazsága eldönthető legyen.

## Tartalom

### A feladat a mintazh-ban

Öt kártya mindegyikének egyik oldalán betű, a másikon természetes szám áll; a látható oldalak: **A, 1, 4, B, 8**. Az ellenőrzendő állítás: *„Ha a kártya egyik oldalán páros szám van, akkor a másik oldalán magánhangzó.”* (Mintazh: 8 pont, indoklással.)

### Megoldás: az implikáció hamissági feltétele

Legyen $P$: „az egyik oldalon páros szám van”, $Q$: „a másik oldalon magánhangzó van”. Az állítás $P \supset Q$, ami **pontosan akkor hamis**, ha $P$ igaz és $Q$ hamis ([[concepts/logika/igazsagtabla]]). Tehát olyan kártyát keresünk, amely *ellenpélda* lehet: egyik oldalán páros szám, a másikon mássalhangzó.

| Látható oldal | Fordítsuk? | Indok |
|---|---|---|
| A (magánhangzó) | nem | $Q$ igaz, így $P \supset Q$ igaz marad, bármi van a túloldalon |
| 1 (páratlan) | nem | $P$ hamis, így az implikáció igaz marad |
| 4 (páros) | **igen** | $P$ igaz: ha a túloldal mássalhangzó, az állítás hamis |
| B (mássalhangzó) | **igen** | $Q$ hamis: ha a túloldal páros, az állítás hamis |
| 8 (páros) | **igen** | $P$ igaz, mint a 4-nél |

**Válasz:** a $4$, a $B$ és a $8$ kártyát kell megfordítani. Az állítás akkor igaz, ha egyik túloldalon sincs ellenpélda.

### A csapda

A tipikus hiba az $A$ kártya megfordítása (a megerősítést keressük, nem a cáfolatot) és a $B$ kihagyása. Ez a **kontrapozíció** összetévesztése: $P \supset Q \equiv \neg Q \supset \neg P$, tehát a „nem magánhangzó” kártyáról ugyanúgy meg kell győződni, hogy a túloldalon nincs páros szám. Az $A$ kártya vizsgálata $Q \supset P$ irányt ellenőrizné, ami nem része az állításnak.

## Kapocs

- [[concepts/logika/igazsagtabla]] — az implikáció igazságtáblája adja a hamissági feltételt
- [[concepts/logika/szemantikus-kovetkezmeny]] — az ellenpélda-keresés ugyanaz a gondolat, mint a következmény cáfolata
- [[concepts/logika/iteletlogikai-formula]] — az állítás formalizálása
- [[concepts/logika/mintazh1-feladattipusok]] — a mintazh 3. feladata
