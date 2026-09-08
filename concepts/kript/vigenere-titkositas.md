---
tags: [concept]
sources: [történelmi_titkosítók.pdf]
derivation: source
updated: 2026-09-04
---

# Vigenère-titkosítás

Polialfabetikus helyettesítés: egy ismétlődő kulcsszó betűnként más-más Caesar-eltolást ad. Évszázadokig „le chiffre indéchiffrable" hírében állt — a kriptanalízise épp azon a periodicitáson múlik, amely erőssé teszi.

## Tartalom

Kulcs: $k = k_0 k_1 \ldots k_{t-1}$, titkosítás: $c_i = (m_i + k_{i \bmod t}) \bmod 26$.

A $t$ hosszú kulcs a szöveget $t$ oszlopra bontja, és mindegyik oszlop külön Caesar-eltolás. A kriptanalízis ezért két lépés: előbb a $t$ periódust kell megtalálni, utána már $t$ darab egyszerű frekvenciaelemzés a feladat.

- **Kasiski-módszer:** ismétlődő trigram-távolságok közös osztója megadja a kulcs hosszát.
- **Index of coincidence (IOC):** véletlen szöveg IOC-ja $\approx 1/26 \approx 0{,}038$, természetes angol szövegé $\approx 0{,}065$. Az oszlopokra bontott szöveg IOC-ja akkor ugrik a természetes értékre, ha a feltételezett kulcshossz helyes.
- Kulcshossz meghatározása után oszloponkénti frekvenciaelemzés adja a kulcsot.

> ⏳ **Ábra még nincs megrajzolva** — tervezett fájlnév: `vigenere-kriptanalisis.excalidraw.md`.

## Kapocs

- [[concepts/kript/tortenelmi-titkositok]] — a monoalfabetikus helyettesítés, amelynek a Vigenère a polialfabetikus általánosítása
- [[concepts/kript/folyam-titkositok]] — a kulcsfolyam ismétlődése ugyanaz a gyengeség modern formában
- [[concepts/kript/feladatok]] — Kasiski/IOC feladat a beadandóban
- [[subjects/kript]] — tantárgy áttekintő
