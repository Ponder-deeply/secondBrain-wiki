---
tags: [concept]
sources: [04.visszalep.pdf]
derivation: source
kind: comparison
element: fire
updated: 2026-10-12
---

# Sorrendi heurisztikák és vágó szabályok

Az általános vezérlési stratégia sorrendi és vágó szabállyal egészíthető ki; az $n$-királynő problémánál a jó sorrend drasztikusan csökkenti a visszalépések számát.

## Tartalom

### Alacsonyabb rendű vezérlési stratégiák

Az általános vezérlési stratégia ([[concepts/mesint/vezerlesi-strategiak]]) kiegészíthető:

- **sorrendi szabállyal:** sorrendet ad egy csúcsból kivezető élek vizsgálatára;
- **vágó szabállyal:** kizárja egy csúcs azon kivezető éleit, amelyeket nem érdemes megvizsgálni.

Ezek a szabályok lehetnek [[concepts/mesint/modellfuggo-vezerles]] vagy heurisztikus ([[concepts/mesint/heurisztika]]) stratégiák.

### Sorrendi heurisztikák az $n$-királynő problémára

Az $i$-edik sor mezőit rangsoroljuk, és ebben a sorrendben próbáljuk ki az $i$-edik királynő lehetséges elhelyezéseit:

- **Diagonális:** a mezőn áthaladó hosszabb átló hossza (nagyobb érték előbb). $4\times4$-es táblán a szélső mezők 4, a belsők 3 és 4 közti értékeket kapnak.
- **Páratlan-páros:** a páratlan sorokban balról jobbra, a páros sorokban jobbról balra legyen a sorrend.
- **Ütés alá kerülő szabad mezők száma:** egy adott királynő elhelyezés következtében a szabad státuszukat elvesztő mezők száma (kevesebb előbb).

### Hatás (2. és 3. állapottér-modell)

Jelölés: visszalépések száma / lépések száma.

| 2. modell | nincs + bal-jobb | diag + bal-jobb |
|---|---|---|
| $n=4$ | 22/48 | 2/8 |
| $n=5$ | 10/25 | 10/25 |
| $n=6$ | 165/336 | 63/132 |
| $n=7$ | 35/77 | 80/167 |
| $n=8$ | 868/1744 | 196/400 |

| $n=4$ | nincs + bal-jobb | diag + bal-jobb | diag + ps-ptl |
|---|---|---|---|
| 2. modell | 22/48 | 2/8 | 0/4 |
| 3. modell | 4/12 | 0/4 | 0/4 |

Példa $n=4$-re: diagonális + balról-jobbra 8 lépés, 2 visszalépés; diagonális + páratlan-páros 4 lépés, 0 visszalépés. A heurisztika nem garantál javulást ($n=7$-nél a diagonális rosszabb).

### Hanoi tornyai példa

A [[concepts/mesint/hanoi-tornyai]] állapotgráfján a slide mélységi korlát 8 mellett az "összeg heurisztikát" használja sorrendi szabályként: a nyomkövetés 24 lépéses, több visszalépéssel.

## Kapocs

- [[concepts/mesint/visszalepeses-kereses]] — az algoritmus, amelyet a sorrend gyorsít
- [[concepts/mesint/forward-checking]] — vágó szabályok a korlát-kielégítési modellben
- [[concepts/mesint/korlat-kielegitesi-modell]] — modellfüggő sorrendi szabályok (legkisebb tartomány előbb)
- [[concepts/mesint/n-kiralyno-problema]] — az alkalmazott feladat
