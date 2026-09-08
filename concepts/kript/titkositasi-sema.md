---
tags: [concept]
sources: [történelmi_titkosítók.pdf]
derivation: source
updated: 2026-09-04
---

# Titkosítási séma és a Kerckhoffs-elv

A titkosítás alapvázlata: a $(Gen, Enc, Dec)$ hármas és az az elv, amely szerint a biztonságnak kizárólag a kulcson szabad múlnia. Ez a keret minden későbbi sémára érvényes, a Caesar-eltolástól az AES-ig.

## Tartalom

- **Titkosítási séma:** $(Gen, Enc, Dec)$ hármas — kulcsgenerálás, titkosítás, visszafejtés.
- **Kerckhoffs-elv:** a biztonságnak a kulcs titkosságán kell alapulnia, nem az algoritmus ismeretlenségén. A támadó ismeri az algoritmust; csak a kulcsot nem.
- **Caesar-eltolás:** $c_i = (m_i + k) \bmod 26$; kulcstér: 26 elem, brute-force triviális. A séma legkisebb nemtriviális példánya — jól mutatja, hogy a *kulcstér mérete* önmagában biztonsági korlát.

> ⏳ **Ábra még nincs megrajzolva** — tervezett fájlnév: `titkositasi-sema.excalidraw.md`.

## Kapocs

- [[concepts/kript/tortenelmi-titkositok]] — a klasszikus titkosítók katalógusa, amelyek mind ezt a sémát példázzák
- [[concepts/kript/tamadasmodellek]] — mit ismer a támadó; a Kerckhoffs-elv operatív megfogalmazása
- [[concepts/kript/tokeletes-biztonsag]] — mikor biztonságos formálisan egy séma
- [[subjects/kript]] — tantárgy áttekintő
