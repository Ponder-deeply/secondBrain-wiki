---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 4.3. szakasz, multiindexes jelölés"]
derivation: source
updated: 2026-09-07
---

# Többváltozós Taylor-polinom és a multiindexes jelölés

A multiindex az a jelölési trükk, amellyel a többváltozós Taylor-polinom pontosan olyan alakot ölt, mint az egyváltozós: $T_{a,s}f(x) = \sum_{|i| \le s} \frac{\partial^i f(a)}{i!}(x-a)^i$.

## Tartalom

### Multiindex

Egy $i = (i_1, \dots, i_n) \in \mathbb{N}^n$ vektort **multiindexnek** nevezünk. Hozzá tartozó jelölések:

$$|i| := \|i\|_1 = \sum_{j=1}^n i_j, \qquad i! := \prod_{j=1}^n i_j!, \qquad x^i := \prod_{j=1}^n x_j^{i_j},$$

és $\partial^i f$ az a parciális derivált, amelyben az $1$-es változó szerint $i_1$-szer, ..., az $n$-edik szerint $i_n$-szer deriválunk. Például $f(x,y,z) = x^3 + y^2 z + z^3 + xyz$ és $i = (2,0,1)$ esetén $\partial^i f = \partial_{113} f = 0$.

**A jelölés csak a [[concepts/analiii/young-tetel|Young-tétel]] miatt jóldefiniált**: $f \in D^{|i|}\{a\}$ mellett az $|i|$ hosszú $1\dots1\dots n\dots n$ jelsorozat bármely permutációja ugyanazt a deriváltat adja, ezért elég megmondani, melyik változó szerint hányszor deriválunk — a sorrendet nem kell.

Ha $n = 1$, akkor $i = i_1 \in \mathbb{N}$, $|i| = i$, $i!$ a szokásos faktoriális, $x^i$ a szokásos hatvány: a jelölés visszaadja az egyváltozós esetet.

### Szakasz

$a, b \in \mathbb{R}^n$ esetén a zárt, illetve nyílt szakasz

$$[a,b] := \{a + t(b-a) : 0 \le t \le 1\}, \qquad (a,b) := \{a + t(b-a) : 0 < t < 1\}.$$

### A Taylor-polinom

Ha $a \in \operatorname{int} D_f$, $s \in \mathbb{N}$ és $f \in D^s\{a\}$ (ahol $D^0\{a\} := C\{a\}$), akkor az $f$ függvény $a$-hoz tartozó **$s$-edrendű Taylor-polinomja**

$$T_{a,s}f(x) := \sum_{k=0}^s \ \sum_{i\in\mathbb{N}^n,\,|i|=k} \frac{\partial^i f(a)}{i!}\cdot (x-a)^i \qquad (x \in \mathbb{R}^n).$$

Nyilván $T_{a,0}f \equiv f(a)$ és $T_{a,s}f(a) = f(a)$.

### Az első két tag, kiírva

- $k = 1$: az egyetlen $|i| = 1$ típusú multiindex a $j$-edik egységvektor, $i! = 1$, tehát a tag $\sum_j \partial_j f(a)(x_j - a_j) = \langle \operatorname{grad} f(a), x - a\rangle$.
- $k = 2$: a tag $\tfrac12 \langle f''(a)(x-a), x-a\rangle = \tfrac12 Q^f_a(x-a)$ — itt jelenik meg a [[concepts/analiii/hesse-matrix|Hesse-mátrix]]. A $\tfrac12$ a vegyes tagok kétszeres előfordulásából és az $i!$-ból együtt jön ki.

Tehát

$$T_{a,2}f(x) = f(a) + \langle \operatorname{grad} f(a), x-a\rangle + \tfrac12 Q^f_a(x-a),$$

ami pontosan az egyváltozós $f(a) + f'(a)h + \tfrac12 f''(a)h^2$ mintája.

## Kapocs

- [[concepts/analiii/tobbvaltozos-taylor-formula]] — a maradéktagos állítások, amelyek ezt a polinomot használják.
- [[concepts/analiii/young-tetel]] — a $\partial^i$ jelölés jogalapja.
- [[concepts/analiii/hesse-matrix]] — a másodfokú tag mátrixa.
- [[concepts/analii/taylor-polinom]] — az egyváltozós eredeti.
