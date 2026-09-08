---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Mérhető halmaz lineáris transzformáltjának mértéke

Mérhető halmaz lineáris képe is mérhető, és a mértéke a determináns abszolút értékével szorzódik: $t(M(A)) = |\det M| \cdot t(A)$.

## Tartalom

### Az elemi esetek

**Lemma.**

- Ha $A$ mérhető és $c_1,\dots,c_p \in \mathbb{R}$, akkor
  $$B = \{(c_1x_1,\dots,c_px_p) : x \in A\}$$
  is mérhető, és $t(B) = |c_1 \cdots c_p| \cdot t(A)$.
- Ha $A$ mérhető és $\varphi \in \mathbb{R}$, akkor a két első koordináta $\varphi$ szögű elforgatásával kapott
  $$B = \{(x_1\cos\varphi - x_2\sin\varphi,\; x_1\sin\varphi + x_2\cos\varphi,\; x_3,\dots,x_p)\}$$
  is mérhető, és $t(B) = t(A)$.

**Bizonyítás.** (a) A belső és a fedő téglák térfogata is ugyanezzel a $|c_1\cdots c_p|$ tényezővel változik, tehát a szuprémum és az infimum is.

(b1) Ha $A = [-a,a]\times[-b,b]\times[a_3,b_3]\times\dots\times[a_p,b_p]$ egy tégla, akkor $M(A)$-t egy nagyobb téglává egészítjük ki; a sarkokat összetolva két téglát kapunk, innen szokásos középiskolás geometriai számolás.

(b2) Általános esetben a belső és a fedő téglákat is elforgatjuk, és az elforgatott téglákkal becsüljük $b(M(A))$-t és $k(M(A))$-t. $\square$

### A fő tétel

**Tétel.**

- Ha $A$ mérhető és $M \in \operatorname{Hom}(\mathbb{R}^p, \mathbb{R}^p)$ lineáris transzformáció, akkor $M(A)$ is mérhető, és
  $$t(M(A)) = |\det M| \cdot t(A).$$
- Ha $M$ egybevágóság, akkor $t(M(A)) = t(A)$.
- Ha $M$ egy $\lambda$ arányú hasonlóság, akkor $t(M(A)) = |\lambda|^p \cdot t(A)$.

**Bizonyítás.** Az állítás igaz az $(x_1,\dots,x_p) \mapsto (c_1x_1,\dots,c_px_p)$ alakú koordinátanyújtásokra és a fenti forgatásokra (bármelyik két koordináta síkjában). Ezek az „elemi" transzformációk generálják az $\mathbb{R}^{p\times p}$ félcsoportot, ezért minden $M$ felírható elemi transzformációk kompozíciójaként,

$$M = T_n T_{n-1} \cdots T_2 T_1.$$

A lemma miatt $T_1(A),\ T_2(T_1(A)),\ \dots$ mind mérhető, és a determinánsok szorzattétele szerint

$$t(M(A)) = |\det T_n| \cdots |\det T_1| \cdot t(A) = |\det M| \cdot t(A). \qquad \square$$

### Jelentősége

Ez a tétel adja meg a Jordan-mérték egybevágóság-invarianciáját, amely az eredeti térfogatelvárások egyike volt, és ez a többváltozós helyettesítéses integrálás (a Jacobi-determinánsos transzformációs tétel) lineáris előképe.

## Kapocs

- [[concepts/analiii/jordan-merheto-halmazok-gyuruje]] — az eltolásinvariancia, amelyet ez a tétel az általános affin esetre terjeszt ki
- [[concepts/analiii/jordan-kulso-belso-mertek]] — az egybevágóság-invariancia mint eredeti elvárás a térfogatfogalommal szemben
- [[concepts/analiii/p-dimenzios-gomb-terfogata]] — az $r^p$ skálázás a hasonlósági esetből azonnal adódik
- [[concepts/analii/hatarozott-integral-helyettesites]] — az egyváltozós helyettesítéses integrálás $|\varphi'|$ tényezője ennek az $|\det M|$ tényezőnek az egydimenziós, lokális megfelelője
