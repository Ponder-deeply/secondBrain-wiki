---
tags: [concept]
sources: [01.bevezetes.pdf]
derivation: source
kind: overview
element: air
updated: 2026-10-12
---

# Az MI története: módszerek és célok specializálódása

Az MI története 1956-tól a módszerek és célok fokozatos specializálódása: az általános eszközökkel megoldani kívánt „mindenféle problémától” a szakértő rendszereken át a gépi tanulásig.

## Tartalom

| Kor | Cél | Projektek | Módszerek |
|---|---|---|---|
| Romantikus kor (1956–) | mindenféle problémát általános eszközökkel | kétszemélyes játékok (sakk), beszélgető program (ELIZA, 1966) | GPS, rezolúció (1966), Lisp (1958), mesterséges neuronhálók, evolúciós algoritmusok |
| Klasszikus kor | speciális problémákat speciális módszerekkel | SHRDLU (1972), BACON, AM, DENDRAL (1969–78), MYCIN (1976) | heurisztikus keresés, tudásreprezentáció, Prolog |
| Ipari kor | szakértő rendszerek, tudásalapú rendszerek | XCON (1982), PROSPECTOR (1979) | shell-ek (IDE), tudásalapú technológia, nem-klasszikus következtetés, bizonytalanság kezelés |
| MI tél, majd reneszánsz | gépi tanulás, hibrid technológiák | Deep Blue (1997), IBM Watson (2011), robotika | aktuális területek: mély hálók, felügyelet nélküli tanulás, adattudomány |

### ELIZA

A beszélgető program minta–válasz párokon alapul: a bemenetben illesztett mintához (pl. `<a> ön <b> engem <c>`) sablonos válasz tartozik („Miért gondolja, hogy ön `<a>` én `<b>` `<c>`?”). Felismeri az ismétlést („Miért ismételgeti ugyanazt újra és újra?”), és semleges folytatás-mondatokat tud („Igen, értem.”, „Kérem folytassa.”). Nem értelmezi a szöveget, csak mintát illeszt.

## Kapocs

- [[concepts/mesint/mi-fogalma]] — az erős és gyenge MI megkülönböztetése
- [[concepts/mesint/intelligens-szoftver-jellemzoi]] — mit várunk egy intelligens szoftvertől
- [[concepts/mesint/modellezes-es-kereses]] — a keresés a klasszikus MI központi módszere
