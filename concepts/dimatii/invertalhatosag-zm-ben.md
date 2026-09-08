---
tags: [concept]
sources: [DimatIIEa02.pdf]
derivation: source
updated: 2026-09-08
---

# Invertálhatóság $\mathbb{Z}_m$-ben

$\mathbb{Z}_m$-ben egy maradékosztály vagy nullosztó, vagy van multiplikatív inverze — a modulushoz vett legnagyobb közös osztó dönti el, melyik.

## Tartalom

**Tétel.** Legyen $m > 1$ egész.

- Ha $1 < (a,m) < m$, akkor $\overline{a}$ **nullosztó** $\mathbb{Z}_m$-ben: van olyan $\overline{b} \neq \overline{0}$, hogy $\overline{a}\cdot\overline{b} = \overline{0}$.
- Ha $(a,m) = 1$, akkor $\overline{a}$-nak van **reciproka** (multiplikatív inverze) $\mathbb{Z}_m$-ben: van olyan $\overline{x}$, hogy $\overline{a}\cdot\overline{x} = \overline{1}$.

**Speciálisan:** ha $m$ prím, akkor minden nem nulla maradékosztállyal lehet osztani, azaz $\mathbb{Z}_m$ test.

**Bizonyítás.** Legyen $d = (a,m)$. Ekkor $a\cdot\frac{m}{d} = \frac{a}{d}\cdot m \equiv 0 \pmod m$, ahonnan $b = m/d$ jelöléssel $\overline{a}\cdot\overline{b} = \overline{0}$, és $\overline{b} \neq \overline{0}$, mert $d > 1$.

Ha $d = 1$, akkor a [[concepts/dimatii/bovitett-euklideszi-algoritmus]]sal megadhatók olyan $x, y$ egészek, hogy $ax + my = 1$. Ekkor $ax \equiv 1 \pmod m$, azaz $\overline{a}\cdot\overline{x} = \overline{1}$. $\square$

**Példa.** Legyen $m = 9$. Ekkor $\overline{6}\cdot\overline{3} = \overline{18} = \overline{0}$, azaz $\overline{6}$ nullosztó. Viszont $(2,9) = 1$, így $\overline{2}\cdot\overline{5} = \overline{10} = \overline{1}$: $\overline{2}$ inverze $\overline{5}$.

Az invertálható osztályok tehát pontosan a [[concepts/dimatii/redukalt-maradekrendszer]] osztályai, $\mathbb{Z}_m^*$ elemei; számuk $\varphi(m)$.

## Kapocs

- [[concepts/dimatii/maradekosztaly]] — a $\mathbb{Z}_m$-beli műveletek
- [[concepts/dimatii/redukalt-maradekrendszer]] — az invertálható osztályok halmaza
- [[concepts/dimatii/bovitett-euklideszi-algoritmus]] — az inverz kiszámítása
- [[concepts/dimatii/legnagyobb-kozos-oszto]] — a döntő mennyiség
- [[concepts/dimatii/euler-fermat-tetel]] — az inverz zárt alakja, $\overline{a}^{\,\varphi(m)-1}$
