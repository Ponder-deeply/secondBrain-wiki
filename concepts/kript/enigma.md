---
tags: [concept]
sources: [enigma.pdf]
derivation: source
updated: 2026-04-22
---

# Enigma

Az Enigma egy elektromechanikus rotor-titkosító gép, amelyet a Wehrmacht és más német fegyvernemek használtak a II. világháborúban. Feltörése a modern kriptanalízis és számítástechnika egyik alapító eseménye.

## Gépi felépítés

- **Billentyűzet → kapcsolótábla (Steckerbrett) → tárcsák → visszafordító → tárcsák (fordítva) → kapcsolótábla → lámpatábla**
- **Tárcsák (rotors):** minden tárcsa egy 26→26 permutatív helyettesítést valósít meg; gépeléskor a jobboldali tárcsa lép egyet (óramutató járásával), átvitel esetén a szomszédos is.
- **Visszafordító (Umkehrwalze):** páros permutáció, biztosítja, hogy $Enc = Dec$ (az Enigma önrejtjelző).
- **Kapcsolótábla:** legfeljebb 10 betűpárt cserél fel, tovább bővíti a kulcsteret.

## Kulcstér

Az Enigma I modellnél (3 tárcsa 5-ből, visszafordító, kapcsolótábla):

$$|\mathcal{K}| \approx \binom{5}{3} \cdot 3! \cdot 26^3 \cdot \binom{26}{2}\binom{24}{2}\cdots \approx 2^{77{,}5}$$

Ez brute-force-szal elérhetetlen volt a korszak technikájával.

## Hadrendbe állítási eljárás

A napi kulcs (Tagesschlüssel) tartalmazta: rotor-sorrendet, gyűrűállásokat (Ringstellung), kapcsolótábla-beállításokat és a Grundstellungot. A kezelő ezután kétszer titkosított egy 3 betűs üzenetkulcsot (indikátor-eljárás) — ez volt a kriptanalízis kulcsa.

## Lengyel kriptanalízis (Marian Rejewski, ~1932)

- A kétszer titkosított indikátor miatt az 1–4. betűk és a 4–7. betűk kapcsolata determinisztikus.
- Rejewski a 6 betűs indikátorból **karakterisztikákat** (permutációk ciklus-típusát) állított elő.
- **Bomba:** mechanikus gép, amely a lehetséges rotor-állásokat szisztematikusan teszteli.
- **Zygalski-lapok:** lyukacsos papírlapok, amelyek a karakterisztikákra szűrnek.

## Brit kriptanalízis (Alan Turing, Bletchley Park)

- **Crib:** ismert vagy feltételezett nyílt szöveg darab (pl. időjárásjelentések nyitó formulái mint `WETTER`).
- **Bombe:** Turing gépesítette Rejewski ötletét; a cribre támaszkodva ciklus-ellentmondásokat keres.
- **Biztonságot gyengítő eljárási hibák:**
  - ismételt indikátorpárok,
  - napi kulcsok kiszámítható mintái (`AAAAAAA`, születésnapok),
  - crib-lehetőséget adó sztereotip üzenetkezdetetek.
- **Gardening:** a britek szándékosan bányaterületekre lőttek, majd elfogták az „aknamező szabad" visszajelzést → garantált crib.

## Miért nem volt tökéletesen biztonságos

- Az üzenetkulcs kétszeri titkosítása statisztikai struktúrát adott.
- A kezelők ismétlődő kulcsokat választottak.
- Az Umkehrwalze miatt egy betű soha nem titkosítható önmagára — ez szűkíti a lehetséges megfeleltetéseket.

## Feladatok

- [[concepts/kript/feladatok]] — 5. feladat: Enigma titkosítás indikátoros eljárással (V1–V4 variánsok, online szimulátorral)

## Kapocs

- [[concepts/kript/tortenelmi-titkositok]] — az Enigma kontextusa a klasszikus titkosítók közt
- [[concepts/kript/tokeletes-biztonsag]] — formális biztonsági modellek, CPA-biztonság
- [[subjects/kript]] — tantárgy áttekintő
