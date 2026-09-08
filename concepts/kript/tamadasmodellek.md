---
tags: [concept]
sources: [történelmi_titkosítók.pdf]
derivation: source
updated: 2026-09-04
---

# Támadásmodellek

Egy titkosítás biztonsága mindig egy támadómodellhez képest értendő: az mondja meg, mit ismer és mit kérhet a támadó. A négy standard modell egyre erősebb támadót ír le.

## Tartalom

| Modell | Mit ismer a támadó |
|---|---|
| COA (ciphertext-only) | csak a titkosított szöveg |
| KPA (known-plaintext) | nyílt-titkos szöveg párok |
| CPA (chosen-plaintext) | általa választott nyílt szövegekhez kap titkosítást |
| CCA (chosen-ciphertext) | általa választott titkosított szövegekhez kap visszafejtést |

A lánc szigorúan erősödik: COA $\subseteq$ KPA $\subseteq$ CPA $\subseteq$ CCA. Egy sémáról tehát nem elég azt állítani, hogy „biztonságos" — meg kell mondani, melyik modellben.

> ⏳ **Ábra még nincs megrajzolva** — tervezett fájlnév: `tamadasi-modellek.excalidraw.md`.

## Kapocs

- [[concepts/kript/tokeletes-biztonsag]] — hogyan viselkednek az egyes modellek a tökéletes biztonsággal szemben
- [[concepts/kript/titkositasi-sema]] — a Kerckhoffs-elv: a támadó az algoritmust mindig ismeri
- [[concepts/kript/tortenelmi-titkositok]] — a klasszikus titkosítók már COA-ban is elbuknak
- [[subjects/kript]] — tantárgy áttekintő
