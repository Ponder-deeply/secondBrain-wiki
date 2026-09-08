---
tags: [concept]
sources: [DimatIIEa02.pdf]
derivation: source
updated: 2026-09-08
---

# Redukált maradékrendszer

Csak azokból a maradékosztályokból veszünk reprezentánst, amelyek elemei relatív prímek a modulushoz — pontosan ezek az invertálható osztályok.

## Tartalom

**Megjegyzés.** Ha egy maradékosztály valamely eleme relatív prím a modulushoz, akkor az összes eleme az: $(a + \ell m,\, m) = (a, m)$. A relatív prímség tehát az osztály tulajdonsága, nem a reprezentánsé.

**Definíció.** Egy rögzített $m$ modulus esetén, ha mindazon maradékosztályokból, melyek elemei relatív prímek a modulushoz, pontosan egy elemet kiveszünk, akkor az így kapott számok **redukált maradékrendszert** alkotnak modulo $m$.

**Példák.** $\{1,2,3,4\}$ redukált maradékrendszer modulo $5$; $\{1,-1\}$ modulo $3$; $\{1, 19, 29, 7\}$ modulo $8$. Ellenben $\{0,1,2,3,4\}$ **nem** redukált maradékrendszer modulo $5$, mert $(0,5) = 5 \neq 1$.

**Definíció.** Egy rögzített $m$ modulus esetén, ha $(a,m) = 1$, akkor az $a$ által reprezentált $\overline{a}$ maradékosztály **redukált maradékosztály**. A redukált maradékosztályok halmazát $\mathbb{Z}_m^*$-gal jelöljük:
$$\mathbb{Z}_m^* = \{\overline{a} \,:\, 1 \leq a < m,\ (a,m) = 1\}.$$

Egy redukált maradékrendszer mérete tehát $|\mathbb{Z}_m^*| = \varphi(m)$, lásd [[concepts/dimatii/euler-fi-fuggveny]].

### Eltolás–szorzás lemma

Ha $a_1, \dots, a_{\varphi(m)}$ redukált maradékrendszer modulo $m$, és $(a,m) = 1$, akkor $a\cdot a_1, \dots, a\cdot a_{\varphi(m)}$ szintén redukált maradékrendszer.

**Bizonyítás.** $(a_i, m) = 1$ és $(a,m) = 1 \Rightarrow (a\cdot a_i, m) = 1$. Továbbá a szorzatok páronként inkongruensek (az $a$-val való egyszerűsíthetőség miatt), és számuk $\varphi(m)$, tehát redukált maradékrendszert alkotnak. $\square$

Ez a lemma közvetlenül adja az [[concepts/dimatii/euler-fermat-tetel]]t.

## Kapocs

- [[concepts/dimatii/teljes-maradekrendszer]] — a bővebb rendszer, amelyből ez szűkítéssel adódik
- [[concepts/dimatii/maradekosztaly]] — a reprezentált objektumok
- [[concepts/dimatii/euler-fi-fuggveny]] — a rendszer elemszáma
- [[concepts/dimatii/invertalhatosag-zm-ben]] — pontosan ezek az osztályok invertálhatók
- [[concepts/dimatii/euler-fermat-tetel]] — a lemma alkalmazása
