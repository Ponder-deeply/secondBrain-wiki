---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Körülfordulási szám (görbeindex)

Zárt síkgörbe egy rá nem illeszkedő pont körüli előjeles „megkerüléseinek" száma. Egész értékű topológiai invariáns, amely többféle vonalintegrállal is felírható.

## Tartalom

### Definíció

Legyen $\gamma : [a,b] \to \mathbb{R}^2$ zárt görbe és $\mathbf{c} \in \mathbb{R}^2$ a görbén kívüli pont. Ekkor $n(\gamma, \mathbf{c}) \in \mathbb{Z}$ azt jelenti, hogy $\gamma$ előjelesen hányszor „kerüli meg" a $\mathbf{c}$ pontot. Neve: a görbe **$\mathbf{c}$-re vonatkozó indexe**, vagy **$\mathbf{c}$ körüli körülfordulási száma**.

Szemléletesen: követjük az $\mathbf{x} - \mathbf{c}$ vektor irányított szögét a görbe mentén; mivel a görbe zárt, a szög teljes megváltozása $2\pi$ egész számú többszöröse, és ez az egész szám az index. Ezért is egész mindig az érték.

### Felírás vonalintegrállal

A görbeindexet sokféle paraméteres vonalintegrállal is felírhatjuk. A szög gradiensét integrálva:

$$n(\gamma, \mathbf{c}) = \frac{1}{2\pi}\int_{(x,y)\in\gamma} \left\langle \underbrace{\left( \frac{-(y-c_2)}{(x-c_1)^2+(y-c_2)^2},\ \frac{x-c_1}{(x-c_1)^2+(y-c_2)^2} \right)}_{\operatorname{grad}\,\text{szög}(\mathbf{x}-\mathbf{c})};\ (\mathrm{d}x,\mathrm{d}y) \right\rangle$$

keresztszorzattal tömörebben:

$$n(\gamma,\mathbf{c}) = \frac{1}{2\pi}\int_{\mathbf{x}\in\gamma} \frac{\mathbf{x}-\mathbf{c}}{|\mathbf{x}-\mathbf{c}|^2} \times \mathrm{d}\mathbf{x},$$

komplex vonalintegrállal pedig

$$n(\gamma,\mathbf{c}) = \frac{1}{2\pi i}\int_{z\in\gamma} \frac{\mathrm{d}z}{z-\mathbf{c}} .$$

Az utolsó alak a komplex függvénytan reziduumtételének a magja; itt az integráltételek felől érkezünk hozzá.

### Miért érdekes

- **Egész értékű**, tehát folytonos deformáció (homotópia) közben nem változhat, amíg a görbe nem megy át a $\mathbf{c}$ ponton. Ezért topológiai invariáns.
- A $\mathbf{c}$ pont mozgatásakor is állandó marad, amíg $\mathbf{c}$ nem lépi át a görbét: a $\mathbb{R}^2 \setminus \gamma([a,b])$ minden összefüggő komponensén konstans.
- A [[concepts/analiii/jordan-gorbetetel]] szerint egyszerű zárt görbénél a külső komponensen az index $0$, a belsőn mindenütt $+1$ vagy mindenütt $-1$ — ez definiálja a görbe irányítását.

Az integrandusban szereplő $\frac{\mathbf{x}-\mathbf{c}}{|\mathbf{x}-\mathbf{c}|^2}$ vektormezőnek magasabb dimenziós megfelelői vannak; ezekből származnak a zárt felület pont körüli fokszámára és a Gauss-féle összekapcsolódási számra vonatkozó képletek.

## Kapocs

- [[concepts/analiii/jordan-gorbetetel]] — az index viselkedése egyszerű zárt görbénél, és a görbeirányítás definíciója
- [[concepts/analiii/altalanos-vonalintegral]] — a felírásokban használt vonalintegrál-fogalmak
- [[concepts/analiii/sikvektorok-keresztszorzata]] — az irányított szög és a keresztszorzatos alak
- [[concepts/analiii/korulfordulasi-szam-valtozatok]] — a fogalom felületi és összekapcsolódási változatai
