---
tags: [concept]
sources: []
derivation: unsourced
updated: 2026-08-05
---

# Secondary dominant

Másodlagos domináns: olyan V7 akkord, amely nem a hangnem tonikájára, hanem egy másik diatonikus fokra oldódik. Jelölése V7/x („x fok dominánsa"), például V7/ii. Ez a legegyszerűbb eszköz arra, hogy egy diatonikus akkordmenet átmenetileg más fok felé irányuljon.

## Az elv

Bármely diatonikus fokot ideiglenes tonikának tekinthetünk, és eléje tehetjük a saját kvintjéről indított domináns szeptimet. Az akkord nem diatonikus (a hangnemen kívüli hangot tartalmaz), de a fül azonnal célirányosnak hallja, mert a tritonusza a célakkord felé oldódik.

C-dúrban:

| Jelölés | Akkord | Cél | A cél foka | Hangnemen kívüli hang |
|---|---|---|---|---|
| V7/ii | A7 | Dm7 | ii | C# |
| V7/iii | B7 | Em7 | iii | D#, F# |
| V7/IV | C7 | Fmaj7 | IV | Bb |
| V7/V | D7 | G7 | V | F# |
| V7/vi | E7 | Am7 | vi | G# |

A vii. fokhoz (Bm7b5) nincs használható másodlagos domináns, mert a fok nem stabil, nem hallható ideiglenes tonikának.

Figyelemre méltó a V7/IV: hangkészlete a I fokéval azonos alaphangon áll (C7 a Cmaj7 helyén), csak a 7 leszállítva. Ezért egyetlen hang megváltoztatásával a tonikából dominánsfunkciót csinálunk — ez a **dominánsosítás**, a reharmonizáció egyik alapfogása.

## Feloldás

Az alaphelyzet a lefelé kvintlépéses oldás (A7 → Dm7). Két gyakori eltérés:

- **Deceptive:** a másodlagos domináns nem a várt fokra, hanem annak helyettesére oldódik (E7 → Fmaj7 az Am7 helyett).
- **Lánc:** a cél maga is domináns, és tovább lép (E7 → A7 → D7 → G7). Ez már [[concepts/jazz/extended-dominant|extended-dominant]].

A másodlagos domináns nem kötelezően oldódik: gyakran csak színez, majd visszalép oda, ahonnan jött.

## Chord-scale

A választás azon múlik, hogy a célakkord dúr vagy moll:

| Cél minősége | Chord-scale | Tension | Példa |
|---|---|---|---|
| dúr (maj7 vagy 7) | mixolydian | 9, 13 | D7 (→ G7) = D mixolydian |
| moll (m7) | mixolydian b9 b13 / altered | b9, b13 | A7 (→ Dm7) = A mixolydian b9 b13 |

A szabály oka egyszerű: a b9 és a b13 azok a hangok, amelyek a *célakkord* moll hangnemi környezetéből származnak. A7 → Dm7 esetén az A7 b9-e a Bb, b13-a az F — mindkettő D-moll hangja. Dúr célnál viszont ezek a hangok idegenek lennének, ezért ott természetes 9 és 13 jár.

Kiegészítő lehetőségek:

- **Lydian dominant (#11):** ha a domináns nem lefelé kvintbe oldódik, vagy tritone subként értelmezhető.
- **Altered:** bármelyik másodlagos domináns fölött használható, ha erős feszültséget akarunk; moll célnál különösen természetes.
- **HW diminished:** dúr célnál, ha b9/#9 kell 13 mellé.

Az egyetlen szigorú megszorítás: a domináns 4-e (11) avoid note, mert a 3-mal fél hangot súrol — kivéve ha sus akkordként kezeljük.

## A related ii

Bármely másodlagos domináns elé odaképzelhető a hozzá tartozó ii. fok — az ideiglenes tonika saját ii foka. Ezt hívjuk **related ii**-nek, és a párost „ii–V of x"-nek.

C-dúrban:

| Cél | V7/x | Related ii | Teljes lánc |
|---|---|---|---|
| Dm7 (ii) | A7 | Em7b5 | Em7b5 – A7 – Dm7 |
| G7 (V) | D7 | Am7 | Am7 – D7 – G7 |
| Am7 (vi) | E7 | Bm7b5 | Bm7b5 – E7 – Am7 |
| Fmaj7 (IV) | C7 | Gm7 | Gm7 – C7 – Fmaj7 |

A related ii minősége a cél minőségét követi: dúr célhoz m7, moll célhoz m7b5. A beszúrás nem hoz be új funkciót, csak kitölti a helyet és megkétszerezi a mozgást — így egy egyszerű menetből sűrű ii–V-lánc lesz. Ez a reharmonizáció leggyakoribb betoldó technikája.

Fordítva is működik: a related ii önmagában is beszúrható a másodlagos domináns nélkül, ekkor csak lágy szubdomináns színt ad.

## Kapocs

- [[concepts/jazz/ii-v-i-durban]] — a másodlagos domináns ugyanezt a mintát ismétli más fokon
- [[concepts/jazz/extended-dominant]] — a másodlagos dominánsok láncba fűzése
- [[concepts/jazz/tritone-substitution]] — minden másodlagos domináns helyettesíthető
- [[concepts/jazz/turnaround]] — a III7–VI7–II7–V7 lánc csupa másodlagos dominánsból áll
- [[concepts/jazz/reharmonizacio]] — a dominánsosítás mint reharm-technika
- [[concepts/jazz/chord-scale-theory]] — a skálaválasztás általános elve
