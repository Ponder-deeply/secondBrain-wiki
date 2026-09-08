---
tags: [concept]
sources: [történelmi_titkosítók.pdf]
derivation: source
updated: 2026-09-04
---

# Történelmi titkosítók

A klasszikus kriptográfia titkosítói betűszintű transzformációkon alapulnak; biztonságuk a mai mércével messze elmarad a modern sémáktól, de számos alapfogalmat (frekvenciaelemzés, kulcstér, kriptanalízis) szemléltetnek. Ez a lap a titkosítók katalógusa; a mögöttük álló keretet a [[concepts/kript/titkositasi-sema]] és a [[concepts/kript/tamadasmodellek]] tárgyalja.

## Tartalom

### Monoalfabetikus helyettesítés

Minden betűt egy fix permutáció szerint cserélünk. Kulcstér: $26! \approx 2^{88}$, de **frekvenciaelemzéssel** törhető (az angol `e`, `t`, `a` betűk ismert gyakorisága alapján). Polialfabetikus általánosítása a [[concepts/kript/vigenere-titkositas]].

### Playfair-titkosítás

$5 \times 5$-ös betűrács, digram-alapú titkosítás. Bigramfrekvenciák elemzésével törhető.

### Beaufort-titkosítás

$c_i = (k_i - m_i) \bmod 26$; visszafejtés ugyanazzal a művelettel ($Enc = Dec$).

### ADFGVX-titkosítás

Két lépés: (1) helyettesítés egy $6 \times 6$-os rács alapján az `ADFGVX` betűkre, (2) oszlopos transzpozíció. WWI-es német rendszer, Painvin törte 1918-ban.

### Rail fence (kerítéses transzpozíció)

Az üzenetet $r$ sorba kígyószerűen írják, majd soronként olvasnak ki. Kulcstér: $r$, triviálisan törhető.

### Cardano-rács

Lyukas rács; a szöveget a lyukakon át olvassák, majd 90°-os elforgatásokkal töltik ki a táblát. A rácsot mindkét félnek ismernie kell.

### Nómenklatúra-titkosítás

Szólistás helyettesítés, néha szó→szám megfeleltetéssel; a lista titkossága adja a biztonságot — épp ezért sérti a Kerckhoffs-elvet.

## Kapocs

- [[concepts/kript/titkositasi-sema]] — a $(Gen, Enc, Dec)$ keret és a Kerckhoffs-elv, amelyet ezek a titkosítók példáznak
- [[concepts/kript/vigenere-titkositas]] — a polialfabetikus eset és kriptanalízise (Kasiski, IOC)
- [[concepts/kript/tamadasmodellek]] — COA/KPA/CPA/CCA; ezek a titkosítók már COA-ban is elbuknak
- [[concepts/kript/enigma]] — az Enigma gép, mint komplex transzpozíció+helyettesítés
- [[concepts/kript/tokeletes-biztonsag]] — mikor biztonságos formálisan egy titkosítás
- [[concepts/kript/feladatok]] — beadandó feladatok helyettesítésre, Cardano-rácsra, Enigmára
- [[subjects/kript]] — tantárgy áttekintő
