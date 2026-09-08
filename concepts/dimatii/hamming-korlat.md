---
tags: [concept]
sources: [DimatIIEa09.pdf, DimatIIEa10.pdf]
derivation: source
updated: 2026-09-08
---

# Hamming-korlát

Gömbpakolási felső korlát egy $t$-hibajavító kód méretére; az egyenlőséget elérő kódok a perfekt kódok.

## Tartalom

### A tétel

**Tétel.** Ha $K \subset A^n$, $|A| = q$ és $K$ $t$-hibajavító, akkor
$$|K| \sum_{j=0}^t \binom{n}{j}(q-1)^j \le q^n .$$

*Bizonyítás.* Mivel a kód $t$-hibajavító, ezért bármely két kódszóra a tőlük legfeljebb $t$ távolságra lévő szavak halmazai diszjunktak. Egy kódszótól pontosan $j$ távolságra lévő szavak száma $\binom{n}{j}(q-1)^j$, így egy kódszótól legfeljebb $t$ távolságra lévő szavak száma $\sum_{j=0}^t \binom{n}{j}(q-1)^j$. A jobb oldalon az $n$ hosszú szavak száma szerepel. $\square$

Szemléletesen: a kódszavak köré rajzolt $t$ sugarú gömbök nem lóghatnak egymásba, és együtt sem foglalhatnak el több helyet, mint amennyi az $A^n$ térben rendelkezésre áll.

### Perfekt kód

Ha egy kódra a Hamming-korlát egyenlőséggel teljesül, akkor azt **perfekt kódnak** nevezzük. Perfekt kód esetén a $t$ sugarú gömbök hézagmentesen lefedik az egész teret.

**Példa (nem perfekt kódra).** A $(*)$ kód esetén $|K| = 4$, $n = 5$, $q = 2$ és $t = 1$. A bal oldal
$$4\left(\binom{5}{0}(2-1)^0 + \binom{5}{1}(2-1)^1\right) = 4(1+5) = 24,$$
a jobb oldal $2^5 = 32$. Ez tehát nem perfekt kód.

Az 1-hibajavító perfekt lineáris kódokat Hamming-kódnak nevezzük.

## Kapocs

- [[concepts/dimatii/hibajelzes-es-hibajavitas]] — a $t$-hibajavító fogalom, amelyre a korlát épül
- [[concepts/dimatii/hamming-kod]] — a korlátot egyenlőséggel teljesítő lineáris kódcsalád
- [[concepts/dimatii/singleton-korlat]] — a másik klasszikus felső korlát
- [[concepts/dimatii/hamming-tavolsag]] — a mögöttes metrika
