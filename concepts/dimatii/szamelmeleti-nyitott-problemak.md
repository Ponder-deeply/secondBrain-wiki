---
tags: [concept]
sources: [Lehman-Leighton-Meyer-Mathematics-for-Computer-Science.pdf]
references: [Lehman–Leighton–Meyer, Mathematics for Computer Science, 9.1 és 9.3 (Prime Mysteries)]
derivation: source
kind: overview
element: air
updated: 2026-10-22
---

# Híres számelméleti sejtések és eredmények

A számelmélet sok állítása könnyen megfogalmazható, de nehéz: az alábbi lista a tananyagban felbukkanó nyitott kérdéseket és a hozzájuk tartozó ismert részeredményeket gyűjti.

## Tartalom

### Tökéletes számok

Egy szám **tökéletes**, ha egyenlő a nála kisebb pozitív osztóinak összegével: $6 = 1 + 2 + 3$, $28 = 1 + 2 + 4 + 7 + 14$. Nem tökéletes: $10$ ($1 + 2 + 5 = 8$), $12$ ($1+2+3+4+6 = 16$).

**Euklidész.** Ha $2^k - 1$ prím, akkor $2^{k-1}(2^k - 1)$ tökéletes. Ugyanis $p = 2^k - 1$ prím esetén $n = 2^{k-1}p$ összes pozitív osztójának összege $(1 + 2 + \dots + 2^{k-1})(1 + p) = (2^k - 1) \cdot 2^k$, ebből $n$-t levonva $2^k p - 2^{k-1}p = 2^{k-1}p = n$. Euler megfordította: minden páros tökéletes szám ilyen alakú. **Nyitott:** van-e páratlan tökéletes szám (kb. $10^{300}$-ig nincs), és végtelen sok páros tökéletes szám van-e.

### Prímek

- **Ikerprím-sejtés:** végtelen sok $p$ prím van, amelyre $p + 2$ is prím. Chen (1966): végtelen sok $p$ prímre $p + 2$ legfeljebb két prím szorzata.
- **Goldbach-sejtés:** minden $2$-nél nagyobb páros szám két prím összege ($4 = 2 + 2$, $6 = 3 + 3$, $8 = 3 + 5$). Ismert: minden páros szám legfeljebb $6$ prím összege.
- **Prímszámtétel:** $\pi(n) \sim n/\ln n$ ([[concepts/dimatii/primek-eloszlasa]]). Elemi, bizonyítható gyengébb alak (Csebisev): $n > 1$ esetén $\pi(n) > n/(3\ln n)$.
- **Riemann-sejtés:** a $\zeta(s) = \sum n^{-s} = \prod_p (1 - p^{-s})^{-1}$ függvény minden nemtriviális zérushelye az $\operatorname{Re} s = 1/2$ egyenesen van. Az összefüggés a számelmélet alaptételéből jön: a végtelen szorzatot kifejtve minden pozitív egész pontosan egyszer szerepel ([[concepts/dimatii/szamelmelet-alaptetele]]). Bizonyítása erős prímszámtételt adna.

### Faktorizáció és prímteszt

- **A faktorizálás nehézsége (sejtés):** két nagy prím $n = pq$ szorzatából nincs polinomiális idejű eljárás $p$ és $q$ megtalálására a bináris hossz függvényében. A legjobb ismert eljárás (számtest-szita) $e^{1{,}9(\ln n)^{1/3}(\ln\ln n)^{2/3}}$ idejű, kb. $300$ jegyű $n$-re kivitelezhetetlen. Ez adja az [[concepts/dimatii/rsa]] biztonságát.
- **Prímteszt:** $n$ prím, ha nincs osztója $2$ és $\sqrt n$ között, de ez a bemenet hosszában exponenciális. Strassen (1974): gyors valószínűségi teszt; Agrawal–Kayal–Saxena (2002): polinomiális idejű determinisztikus teszt (a fokszám $12$, később $5$), a gyakorlatban a valószínűségi tesztek maradtak.
- **Kapcsolat a SAT-tal:** egy $2n$ bites $m$ faktorizálása $n$ SAT-teszttel visszavezethető (szorzásellenőrző áramkör, az $i$ bitjeit egyenként rögzítve). Ha SAT polinomiális idejű volna, a faktorizálás és az RSA is könnyű lenne.

## Kapocs

- [[concepts/dimatii/primek-eloszlasa]] — a prímszámtétel és Euklidész tétele
- [[concepts/dimatii/szamelmelet-alaptetele]] — az egyértelmű prímfelbontás, a $\zeta$-szorzat alapja
- [[concepts/dimatii/rsa]] — a faktorizáció nehézségére épülő titkosítás
- [[concepts/dimatii/oszthatosag]] — az osztók összege, a tökéletes számok alapfogalma
- [[concepts/bvszam/np-koztes-es-conp]] — a FACTORING bonyolultsági helye
