---
tags: [concept]
sources: [DimatIIEa09.pdf, DimatIIEa10.pdf]
derivation: source
updated: 2026-09-08
---

# Ellenőrző mátrix

Az a mátrix, amelynek magtere éppen a lineáris kód; belőle a kódszó-tulajdonság egy szorzással ellenőrizhető, és a kód távolsága is leolvasható.

## Tartalom

### Definíció

Egy $[n,k,d]_q$ kódnak $\mathbf{H} \in \mathbb{F}_q^{(n-k) \times n}$ mátrix az **ellenőrző mátrixa**, ha
$$\mathbf{H}v = 0 \iff v \text{ kódszó}.$$

Egy $\mathbf{G}$ mátrixhoz tartozó kódolásnak $\mathbf{H}$ pontosan akkor ellenőrző mátrixa, ha $\mathrm{Ker}(\mathbf{H}) = \mathrm{Im}(\mathbf{G})$.

### Példák

1. A $(*)$ kód egy ellenőrző mátrixa:
   $$\mathbf{H} = \begin{pmatrix} 1 & 1 & 1 & 0 & 0 \\ 0 & 1 & 0 & 1 & 0 \\ 1 & 0 & 0 & 0 & 1 \end{pmatrix}.$$
2. A háromszori ismétlés kódjának egy ellenőrző mátrixa:
   $$\mathbf{H} = \begin{pmatrix} -1 & 1 & 0 \\ -1 & 0 & 1 \end{pmatrix}.$$
3. A paritásbites kód egy ellenőrző mátrixa: $\mathbf{H} = (1\ 1\ \cdots\ 1)$.

### Szisztematikus kód ellenőrző mátrixa

**Állítás.** Legyen $\mathbf{G} = \begin{pmatrix} \mathbf{I}_k \\ \mathbf{P} \end{pmatrix}$ egy szisztematikus kód generátormátrixa. Ekkor $\mathbf{H} = (-\mathbf{P} \mid \mathbf{I}_{n-k})$ ellenőrző mátrixa a kódnak.

*Bizonyítás.*
$$\mathbf{H}\cdot\mathbf{G} = (-\mathbf{P} \mid \mathbf{I}_{n-k})\begin{pmatrix} \mathbf{I}_k \\ \mathbf{P}\end{pmatrix} = -\mathbf{P} + \mathbf{P} = \mathbf{0} \in \mathbb{F}_q^{(n-k)\times k}.$$
Tehát bármely $u$ kódolandó szóra $\mathbf{H}(\mathbf{G}u) = 0$, vagyis $\mathrm{Im}(\mathbf{G}) \subset \mathrm{Ker}(\mathbf{H})$, amiből $\dim(\mathrm{Im}(\mathbf{G})) \le \dim(\mathrm{Ker}(\mathbf{H}))$. Mivel $\dim(\mathrm{Im}(\mathbf{G})) = k$ és $\dim(\mathrm{Ker}(\mathbf{H})) \le k$, ezért $\dim(\mathrm{Im}(\mathbf{G})) \ge \dim(\mathrm{Ker}(\mathbf{H}))$ is teljesül, így $\mathrm{Im}(\mathbf{G}) = \mathrm{Ker}(\mathbf{H})$. $\square$

### A kód távolsága leolvasható az ellenőrző mátrixból

**Állítás.** Legyen $\mathbf{H}$ egy $[n,k]$ kód ellenőrző mátrixa. A $\mathbf{H}$-nak pontosan akkor van $\ell$ darab lineárisan összefüggő oszlopa, ha van olyan kódszó, aminek a súlya legfeljebb $\ell$.

*Bizonyítás.* ($\Rightarrow$) Ha $\sum_{j=1}^{\ell} u_j \cdot h_{\ell_j} = 0$, tekintsük azt a vektort, aminek az $\ell_j$-edik koordinátája $u_j$, a többi pedig $0$. Ez egyrészt kódszó lesz, másrészt a súlya legfeljebb $\ell$.
($\Leftarrow$) Legyen $u = (u_1, \dots, u_n)^T$ az a kódszó, aminek a súlya $\ell$. Ekkor $\mathbf{H}$-nak az $u$ nem-nulla koordinátáinak megfelelő oszlopai lineárisan összefüggőek. $\square$

**Következmény.** A kód távolsága a legkisebb pozitív egész $\ell$, amire létezik az ellenőrző mátrixnak $\ell$ darab lineárisan összefüggő oszlopa.

**Példa.** A $(*)$ kód fenti $\mathbf{H}$ mátrixában egyik oszlopvektor sem a nullvektor, így nincs 1 darab lineárisan összefüggő oszlop; egyik oszlopvektor sem többszöröse egy másiknak, így nincs 2 darab sem. Az 1., 3. és 5. oszlop lineárisan összefüggő, így a kód távolsága 3.

## Kapocs

- [[concepts/dimatii/linearis-kod]] — a kód, amelyet a mátrix magtereként kapunk
- [[concepts/dimatii/generatormatrix]] — a duális, képtér felőli leírás
- [[concepts/dimatii/szindroma-dekodolas]] — a $\mathbf{H}v$ szorzat mint dekódolási eszköz
- [[concepts/dimatii/hamming-kod]] — konstrukció, amely közvetlenül az ellenőrző mátrix oszlopaiból indul
