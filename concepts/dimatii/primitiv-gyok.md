---
tags: [concept, dimatii/alkalmazasok-kriptografia]
sources: [DimatIIEa03.pdf]
derivation: source
updated: 2026-09-08
---

# Primitív gyök (generátor)

Prímmodulus esetén létezik olyan $g$ maradékosztály, melynek hatványai kiadják az összes redukált maradékosztályt; ez teszi a $\mathbb{Z}_p^*$ multiplikatív csoportot ciklikussá.

## Tartalom

### Tétel

Legyen $p$ prímszám. Ekkor $\mathbb{Z}_p^*$-ban van **generátor** (más néven **primitív gyök**), azaz van olyan $1 < g < p$ egész, melynek hatványaiként minden redukált maradékosztály előáll:

$$\{\overline{g^0} = \overline{1},\ \overline{g},\ \overline{g^2},\ \ldots,\ \overline{g^{p-1}}\} = \mathbb{Z}_p^*,$$

egészek szintjén megfogalmazva:

$$\{1 = g^0,\ g \bmod p,\ g^2 \bmod p,\ \ldots,\ g^{p-1} \bmod p\} = \{1, 2, \ldots, p-1\}.$$

### Példák

$3$ generátor modulo $7$, mert a hatványai végigfutnak $\{1, \ldots, 6\}$-on:

$$3^1 \equiv 3,\quad 3^2 \equiv 2,\quad 3^3 \equiv 6,\quad 3^4 \equiv 4,\quad 3^5 \equiv 5,\quad 3^6 \equiv 1 \pmod 7.$$

$2$ generátor modulo $11$: a $2^n \bmod 11$ sorozat $n = 1, \ldots, 10$ mellett $2, 4, 8, 5, 10, 9, 7, 3, 6, 1$ — mind a tíz redukált maradék előfordul.

$2$ **nem** generátor modulo $7$: a $2^n \bmod 7$ sorozat $2, 4, 1, 2, 4, 1$, azaz csak három különböző értéket vesz fel.

Vagyis a generátorság nem a modulus, hanem a konkrét elem tulajdonsága: adott prímmodulushoz általában több generátor is tartozik, de nem minden redukált maradékosztály az.

### Miért érdekes

A generátor létezése miatt értelmezhető a [[concepts/dimatii/diszkret-logaritmus]], és ezen alapul a [[concepts/dimatii/diffie-hellman-kulcscsere]] is: ott $g$ egy nagy $p$ prímhez tartozó generátor, és a nyilvános paraméterek épp a $(p, g)$ pár.

## Kapocs

- [[concepts/dimatii/diszkret-logaritmus]] — a $g$ generátorhoz tartozó kitevő mint „logaritmus"
- [[concepts/dimatii/diffie-hellman-kulcscsere]] — nyilvános paraméterként használ egy generátort
- [[concepts/dimatii/gyors-hatvanyozas]] — a $g^n \bmod p$ hatványok hatékony kiszámítása
- [[concepts/dimatii/csoport]] — $\mathbb{Z}_p^*$ a szorzásra Abel-csoport, a generátor létezése annak ciklikusságát jelenti
