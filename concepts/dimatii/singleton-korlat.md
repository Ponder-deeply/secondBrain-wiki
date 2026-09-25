---
tags: [concept, dimatii/hibakorlatozo-es-linearis-kodok]
sources: [DimatIIEa09.pdf, DimatIIEa10.pdf]
derivation: source
updated: 2026-09-08
---

# Singleton-korlát

Felső korlát egy adott hosszúságú és távolságú kód méretére; az egyenlőséget elérő kódok az MDS-kódok.

## Tartalom

### A tétel

**Tétel.** Ha $K \subset A^n$, $|A| = q$ és $d(K) = d$, akkor
$$|K| \le q^{\,n-d+1} .$$

*Bizonyítás.* Ha minden kódszóból elhagyunk $d-1$ betűt (ugyanazokból a pozíciókból), akkor az így kapott szavak még mindig különbözőek, és $n-d+1$ hosszúak. Az ilyen hosszú szavak száma szerepel az egyenlőtlenség jobb oldalán. $\square$

A korlát tartalma: hosszabb minimális távolságot csak a kódszavak számának rovására kaphatunk.

### MDS-kód

Ha egy kódra a Singleton-korlát egyenlőséggel teljesül, akkor azt **maximális távolságú szeparábilis kódnak** (**MDS-kód**) nevezzük.

**Példa.** Az $n$-szeri ismétlés kódja. Ekkor $d = n$, és $|K| = q$, tehát $q = q^{\,n-n+1}$.

### Lineáris alak

Egy $[n,k,d]_q$ lineáris kód esetén a Singleton-korlát alakja egyszerűsödik:
$$q^k \le q^{\,n-d+1} \iff k \le n - d + 1 .$$

## Kapocs

- [[concepts/dimatii/hamming-tavolsag]] — a kód távolsága, amelyre a korlát vonatkozik
- [[concepts/dimatii/hamming-korlat]] — a másik klasszikus korlát, a hibajavító képességből
- [[concepts/dimatii/linearis-kod]] — a korlát lineáris kódra vett paraméteres alakja
