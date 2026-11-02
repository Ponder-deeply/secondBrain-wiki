---
tags: [concept]
sources: [04.visszalep.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-12
---

# Visszalépés feltételei

A visszalépéses keresés ([[concepts/mesint/visszalepeses-kereses]]) a legvégső esetben lép vissza; négy ilyen feltételt különböztetünk meg.

## Tartalom

A legvégső eset, amikor a visszalépést kell választani:

1. **Zsákutca:** az aktuális csúcsból (azaz az aktuális út végpontjából) nem vezet tovább él.
2. **Zsákutca-torkolat:** az aktuális csúcsból kivezető utak nem vezettek célba.
3. **Kör:** az aktuális csúcs szerepel már korábban is az aktuális úton.
4. **Mélységi korlát:** az aktuális út hossza elér egy előre megadott értéket.

A VL1 algoritmus az első kettőt építi be (véges körmentes gráfon terminál), a VL2 mindegyiket (tetszőleges $\delta$-gráfon terminál). A kör és a mélységi korlát vizsgálata teszi lehetővé, hogy a keresés körös gráfon se ragadjon végtelen ágba.

## Kapocs

- [[concepts/mesint/visszalepeses-kereses]] — az algoritmusok, amelyekben a feltételek szerepelnek
- [[concepts/mesint/melysegi-korlatos-visszalepes]] — a mélységi korlát és a kör kezelése
- [[concepts/mesint/forward-checking]] — vágó szabály, amely a zsákutcát korábban felismeri
