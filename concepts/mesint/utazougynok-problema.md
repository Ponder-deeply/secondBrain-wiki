---
tags: [concept]
sources: [01.bevezetes.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-12
---

# Az utazó ügynök problémája

Adott $n$ város és a közöttük vezető utak költsége; melyik a legolcsóbb olyan útvonal, amely az A városból indulva mindegyik várost egyszer érintve visszatér A-ba? A feladat a kombinatorikus robbanás tankönyvi példája.

## Tartalom

### A problématér mérete

A lehetséges útvonalak (a problématér elemei) száma $(n-1)!$: $n=5$ esetén 24, $n=50$ esetén $6\cdot10^{62}$. Szisztematikus (nyers erejű) kereséssel ez kezelhetetlen, ezért heurisztika kell.

### Megoldási ötletek a bevezető példán

Öt város (A–E), élköltségekkel; a problématér elemei az útvonalak (pl. ABCDEA, ACBDEA, …).

1. **Szomszédos elempár cseréje** (lokális keresés): a startútvonalból (ABCDEA, költség $2+9+5+3+4=23$) szomszédos városok felcserélésével kapjuk a szomszédokat (ACBDEA: 18, ABDCEA: 13, ABCEDA: 16); mindig a legjobb elemet választjuk (ABDCEA), majd onnan tovább (ABDECA: 8, …, ADBECA: 5). Felesleges elemek (pl. a fordított bejárások) elhagyhatók.
2. **Építő keresés**: az AA útvonalból indulva új város beszúrásával épül az út (ABA: 4, majd ABCA, ACBA: 12, …, ADBECA: 5). **Szimmetrikus elemek elhagyhatók** (az ACBA ág az ABCA tükörképe).

Mindkét megközelítés ugyanazt mutatja: a probléma tér elemei közt **szomszédsági kapcsolat** kell, és az elérhető elemeket rangsorolni kell ([[concepts/mesint/modellezes-es-kereses]]).

## Kapocs

- [[concepts/mesint/intelligens-szoftver-jellemzoi]] — a nehéz feladat jellemzése
- [[concepts/mesint/modellezes-es-kereses]] — mire kell a modellezésnek fókuszálnia
- [[concepts/mesint/hegymaszo-modszer]] — a „mindig a legjobb szomszéd” választás lokális keresésként
