---
tags: [concept]
sources: [07.jatek.pdf]
derivation: source
kind: theorem
element: water
updated: 2026-10-12
---

# Nyerő stratégia

A nyerő stratégia egy játékos olyan elve, amelyet betartva az ellenfél minden lépésére tud olyan választ adni, hogy megnyerje a játékot.

## Tartalom

### Definíció

- A nyerő stratégia **nem egyetlen győztes játszma**, hanem olyan győztes játszmák összessége, amelyek közül az egyiket biztos végig tudja játszani a stratégiával rendelkező játékos.
- Nem elég egy győztes ágat találni: nem biztos, hogy az ellenfél válaszlépései mellett végig lehet játszani ([[concepts/mesint/grundy-mama-jateka]] példáján látszik: $B$-nek az $A$ *minden* lépésére kell győztes válasz).

### ÉS/VAGY fa és hiper-út

A játék az egyik játékos szempontjából [[concepts/mesint/es-vagy-grafok]]: saját szinten VAGY, az ellenfél szintjén ÉS kapcsolat. A nyerő stratégiát az ÉS/VAGY játékfa azon [[concepts/mesint/hiperut]]ja mutatja, amely a gyökércsúcsból csupa nyerő levélcsúcsba vezet. A nyerő stratégia keresése tehát hiper-út keresési probléma ([[concepts/mesint/utkereses-es-vagy-grafban]]).

### Tétel

- Kétesélyes (győzelem vagy vereség), teljes információjú, véges, determinisztikus kétszemélyes játékokban az egyik játékos számára **biztosan létezik** nyerő stratégia.
- Csak az egyik játékosnak lehet nyerő stratégiája (ha az egyiknek van, a másiknak nincs).
- Háromesélyes játékokban (van döntetlen) a **nem vesztő stratégia** biztosan garantálható.

### Megjegyzések

- Ha döntetlen is megengedett és nincs győztes stratégia, a nem-vesztő stratégia megtalálása is hasznos.
- Általános zéró összegű játékoknál beszélhetünk adott hasznosságot biztosító stratégiáról.
- A nyerő stratégia megtalálása időigényes: sakk esetén $35^{90}$ vagy $1{,}76^{90} \approx 1{,}25 \cdot 10^{22}$ levélcsúcs; átlagos számítógépen (100 000 csúcs/mp) $1{,}25 \cdot 10^{17}$ mp $\approx$ 400 millió év; Deep Blue (126 millió csúcs/mp) $10^{14}$ mp $>$ 3 millió év. Ezért kell a [[concepts/mesint/reszleges-jatekfa-kiertekeles]].

## Kapocs

- [[concepts/mesint/jatekfa]] — amelyben a stratégiát keressük
- [[concepts/mesint/hiperut]] — a stratégia alakja
- [[concepts/mesint/es-vagy-grafok]] — az ÉS/VAGY nézet
- [[concepts/mesint/reszleges-jatekfa-kiertekeles]] — gyakorlati kerülőút nagy fákra
