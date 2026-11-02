---
tags: [concept]
sources: [03.lokalker.pdf]
derivation: source
kind: comparison
element: water
updated: 2026-10-12
---

# Vezérlési stratégiák

A kereső rendszer vezérlési stratégiája három szinten csoportosítható (általános, modellfüggő, heurisztikus), az általános stratégiák pedig módosíthatók és nem módosíthatók.

## Tartalom

### A vezérlés szintjei

| Szint | Mire épít |
|---|---|
| **általános** | független a feladattól és modelljétől: nem merít sem a feladat ismereteiből, sem a modellezés sajátosságaiból |
| **modellfüggő** | a modellezéshez választott módszer elemeire épít, de nem függ a feladat ismereteitől |
| **heurisztikus** | a feladattól származó, de modelljében nem rögzített, a megoldást segítő speciális ismeret |

### Általános stratégiák osztályozása

- **Nem módosítható** (a már megtett lépés nem vonható vissza): lokális keresések, evolúciós algoritmus, rezolúció.
- **Módosítható** (a keresés visszalép, korábbi döntés felülvizsgálható): visszalépéses keresések, gráfkeresések, szabályalapú következtetés.

A lokális keresések (hegymászó, tabu, szimulált hűtés) ebben a deckben a nem módosítható stratégiák első csoportja.

## Kapocs

- [[concepts/mesint/kereso-rendszer]] — a KR, amelynek vezérlését osztályozzuk
- [[concepts/mesint/modellfuggo-vezerles]] — a modellfüggő szint részletei
- [[concepts/mesint/heurisztika]] — a heurisztikus szint
- [[concepts/mesint/hegymaszo-modszer]] — nem módosítható stratégia: lokális keresés
- [[concepts/mesint/evolucios-algoritmus]] — nem módosítható stratégia
- [[concepts/mesint/visszalepeses-kereses]] — módosítható stratégia
- [[concepts/mesint/altalanos-grafkereso]] — módosítható stratégia
