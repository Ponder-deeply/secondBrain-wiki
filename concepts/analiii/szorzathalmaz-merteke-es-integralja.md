---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Szorzathalmaz mértéke és integrálja

Mérhető halmazok Descartes-szorzata mérhető, és mértéke a mértékek szorzata; szeparálható integrandus esetén az integrál is szorzatra bomlik.

## Tartalom

### A tétel

**Tétel.**

- **(a)** Ha $A \in \mathcal{J}_p$ és $B \in \mathcal{J}_q$, akkor $A \times B \in \mathcal{J}_{p+q}$, és
  $$t^{(p+q)}(A \times B) = t^{p}(A) \cdot t^{q}(B).$$
- **(b)** Ha $A \in \mathcal{J}_p$, $B \in \mathcal{J}_q$, továbbá $f(x)$ integrálható $A$-n és $g(y)$ integrálható $B$-n, akkor $f(x)g(y)$ integrálható $A \times B$-n, és
  $$\int_{A \times B} f(x)g(y)\,\mathrm{d}x\,\mathrm{d}y = \left(\int_A f(x)\,\mathrm{d}x\right)\cdot\left(\int_B g(y)\,\mathrm{d}y\right).$$

### Az (a) rész bizonyítása

Az $A \times B$ **belső** kockáit úgy kapjuk, hogy $A$ belső kockáit megszorozzuk $B$ belső kockáival, ezért

$$b^{p+q}(A \times B) = \lim_{n \to \infty} b_n^{p+q}(A \times B) = \lim_{n\to\infty}\bigl(b_n^p(A)\cdot b_n^q(B)\bigr) = t^p(A)\cdot t^q(B).$$

Ugyanígy a **fedő** kockákra

$$k^{p+q}(A \times B) = \lim_{n\to\infty}\bigl(k_n^p(A)\cdot k_n^q(B)\bigr) = t^p(A)\cdot t^q(B).$$

A belső és a külső mérték egyenlő, tehát $A \times B$ mérhető, és mértéke a szorzat.

### A (b) rész bizonyítása

**Visszavezetés nemnegatív esetre.** Legyen $f^+ = \max(f, 0)$ és $f^- = \max(-f, 0)$, ekkor $f = f^+ - f^-$, és ugyanígy $g = g^+ - g^-$. Ezek integrálhatóak, például mert $y \mapsto \max(y,0)$ egyenletesen folytonos. Ha az állítás nemnegatív függvényekre igaz, akkor a négy tag szétbontásával általában is:

$$\int_{A\times B} f\cdot g = \left(\int_A f^+ - \int_A f^-\right)\left(\int_B g^+ - \int_B g^-\right) = \left(\int_A f\right)\left(\int_B g\right).$$

**Nemnegatív eset.** Legyen $\mathcal{F} = \{C_1,\dots,C_n\}$ az $A$, $\mathcal{G} = \{D_1,\dots,D_m\}$ a $B$ egy felosztása; a szorzatfelosztás $\{C_i \times D_j\}$. Az ehhez tartozó alsó összeg — kihasználva, hogy nemnegatív függvényekre az infimumok szorzata a szorzat infimuma —

$$s\bigl(f(x)g(y), \{C_i \times D_j\}\bigr) = \sum_{i=1}^n\sum_{j=1}^m t^p(C_i)t^q(D_j)\left(\inf_{x\in C_i} f\right)\left(\inf_{y\in D_j} g\right) = s(f,\mathcal{F}) \cdot s(g,\mathcal{G}).$$

Ugyanígy a felső összegre $S\bigl(f(x)g(y),\{C_i\times D_j\}\bigr) = S(f,\mathcal{F})\cdot S(g,\mathcal{G})$. A felosztást finomítva a jobb oldalak $\int_A f \cdot \int_B g$-hez tartanak, tehát az alsó és a felső integrál egybeesik, és értéke a szorzat.

### Használat

Ez a tétel az, ami egy **szeparálható** integrandust (olyat, amely $f(x)g(y)$ alakú) egyváltozós integrálok szorzatává bont, illetve fordítva: két egyváltozós integrál szorzatát egyetlen kétváltozós integrállá vonja össze. Éppen ez a Gauss-integrál kiszámításának első lépése.

## Kapocs

- [[concepts/analiii/gauss-integral]] — itt a tétel „visszafelé" használva alakítja $(I(R))^2$-et területi integrállá.
- [[concepts/analiii/mertek-es-integraltranszformacio]] — a fejezet másik nagy integrálátalakító eszköze.
- [[concepts/analii/muvelet-integralhato-fuggvenyekkel]] — az egyváltozós integrálhatóság műveleti tulajdonságai; a $f = f^+ - f^-$ felbontás ott is bevált eszköz.
