---
tags: [concept]
sources: [DimatIIEa09.pdf, DimatIIEa10.pdf]
derivation: source
updated: 2026-09-08
---

# Generátormátrix

Lineáris kód esetén a kódolást megvalósító mátrix, amelynek képtere maga a kód; szisztematikus alakban a kódszó eleje az üzenet maga.

## Tartalom

### Definíció

Lineáris kód esetén a kódolás elvégezhető mátrixszorzással. Legyen $G : \mathbb{F}_q^k \to \mathbb{F}_q^n$ egy teljes rangú lineáris leképezés, illetve $\mathbf{G} \in \mathbb{F}_q^{n \times k}$ a hozzá tartozó mátrix. $K = \mathrm{Im}(G)$ esetén $\mathbf{G}$-t a $K$ kód **generátormátrixának** nevezzük.

A kódolás:
$$\begin{pmatrix} g_{11} & \cdots & g_{1k} \\ \vdots & \ddots & \vdots \\ g_{n1} & \cdots & g_{nk}\end{pmatrix} \begin{pmatrix} m_1 \\ \vdots \\ m_k \end{pmatrix} = \begin{pmatrix} c_1 \\ \vdots \\ c_n \end{pmatrix}.$$

### Példák

1. A $(*)$ kód egy generátormátrixa:
   $$\mathbf{G} = \begin{pmatrix} 1 & 0 \\ 0 & 1 \\ 1 & 1 \\ 0 & 1 \\ 1 & 0 \end{pmatrix}.$$
2. A háromszori ismétlés kódjának egy generátormátrixa: $\mathbf{G} = (1,1,1)^T$.
3. A paritásbites kód egy generátormátrixa az $\mathbf{I}_{n-1}$ egységmátrix alá írt csupa 1-es sor.

### Szisztematikus kódolás

Ha a kódszavak első $k$ betűje megfelel az eredeti kódolandó szónak, akkor **szisztematikus kódolásról** beszélünk. Ekkor az első $k$ karakter az **üzenetszegmens**, az utolsó $n-k$ pedig a **paritásszegmens**.

Példák:
1. a háromszori ismétlés kódja: $(\underbrace{a}_{\text{üz.sz.}}, \underbrace{a, a}_{\text{par.sz.}})$;
2. a paritásbites kód: $\left(\underbrace{b_1, \dots, b_{n-1}}_{\text{üz.sz.}}, \underbrace{\textstyle\sum_{j=1}^{n-1} b_j}_{\text{par.sz.}}\right)$.

Szisztematikus kódolás esetén könnyen tudunk dekódolni: a paritásszegmens elhagyásával megkapjuk a kódolandó szót.

Egy szisztematikus kód generátormátrixa speciális alakú:
$$\mathbf{G} = \begin{pmatrix} \mathbf{I}_k \\ \mathbf{P} \end{pmatrix},$$
ahol $\mathbf{I}_k \in \mathbb{F}_q^{k \times k}$ egységmátrix, továbbá $\mathbf{P} \in \mathbb{F}_q^{(n-k) \times k}$.

## Kapocs

- [[concepts/dimatii/linearis-kod]] — a kód, amelyet a mátrix generál
- [[concepts/dimatii/ellenorzo-matrix]] — a duális leírás; szisztematikus alakban $\mathbf{H} = (-\mathbf{P} \mid \mathbf{I}_{n-k})$
- [[concepts/dimatii/szindroma-dekodolas]] — a dekódolás, amely az ellenőrző mátrixra épül
- [[concepts/dimatii/hibakorlatozo-kodolas-peldai]] — a paritásbites kód mint szisztematikus lineáris kód
