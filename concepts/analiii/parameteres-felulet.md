---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Paraméteres felület, felületelem és felszín

Síkbeli paramétertartományból a térbe képező függvény mint felület. A két parciális derivált vektoriális szorzata adja az irányított felületelemet, ennek hossza a felszínelem.

## Tartalom

### Definíció

Ha $P \in \mathcal{J}(\mathbb{R}^2)$ (Jordan-mérhető síkbeli halmaz), akkor a $P\to\mathbb{R}^3$ függvényeket *paraméteres felületnek* hívjuk. Beszélhetünk folytonos, differenciálható, folytonosan differenciálható, darabonként folytonosan differenciálható felületekről is.

### Miért nem a beírt poligonok felszíne

A felszínt **nem** lehet — a görbék ívhosszának mintájára — a beírt poligonok felszínének szuprémumaként definiálni. Ellenpélda a hengerbe beírt „lampion": a hengerpalástba írt háromszöghálót egyre sűrűbben, de ügyesen elforgatva véve a beírt poligonok összfelszíne minden határon túl nő, holott a felületet egyre jobban közelítik. Az ívhossznál működő elv tehát felületre elromlik; helyette a paraméterezés deriváltjaiból építkezünk.

### Felületelem, felszínelem, normálvektor

Ha $S : P\to\mathbb{R}^3$ darabonként folytonosan differenciálható felület, akkor

$$\overrightarrow{\mathrm{d}A} = (D_1S\times D_2S)\,\mathrm{d}u\,\mathrm{d}v, \qquad |\mathrm{d}A| = \bigl|\overrightarrow{\mathrm{d}A}\bigr|, \qquad \mathbf{n} = \frac{\overrightarrow{\mathrm{d}A}}{|\mathrm{d}A|} = \frac{D_1S\times D_2S}{|D_1S\times D_2S|},$$

nevük rendre *felületelem*, *felszínelem*, illetve *irányított normálvektor*.

A gondolat: a $\mathrm{d}u$, $\mathrm{d}v$ paraméternövekmények a felületen a $D_1S\,\mathrm{d}u$ és $D_2S\,\mathrm{d}v$ vektorok által kifeszített kis paralelogrammának felelnek meg, és a vektoriális szorzat éppen ennek a paralelogrammának a területvektora — hossza a terület, iránya a felületre merőleges.

### Felszín

Az $S$ felület *felszíne*

$$A = \int_{u,v\in P} |D_1S\times D_2S|\,\mathrm{d}u\,\mathrm{d}v, \qquad \text{rövidítve } \int_S |\mathrm{d}A| .$$

### Függvénygrafikon

**Lemma.** Ha $S(u,v) = (u, v, \varphi(u,v))$ egy kétváltozós függvény grafikonja, akkor

$$\overrightarrow{\mathrm{d}A} = \begin{pmatrix} -D_u\varphi \\ -D_v\varphi \\ 1 \end{pmatrix}\mathrm{d}u\,\mathrm{d}v .$$

*Bizonyítás.* $D_1S = (1, 0, D_u\varphi)$ és $D_2S = (0, 1, D_v\varphi)$, tehát a „felfelé" mutató területvektor

$$\overrightarrow{\mathrm{d}A} = \begin{pmatrix}1\\0\\D_u\varphi\end{pmatrix}\mathrm{d}u \times \begin{pmatrix}0\\1\\D_v\varphi\end{pmatrix}\mathrm{d}v = \begin{pmatrix}-D_u\varphi\\-D_v\varphi\\1\end{pmatrix}\mathrm{d}u\,\mathrm{d}v. \qquad \square$$

**Következmény.** A grafikon felszíne

$$A = \int_{(u,v)\in P}\sqrt{(D_u\varphi)^2 + (D_v\varphi)^2 + 1}\;\mathrm{d}u\,\mathrm{d}v,$$

ami éppen az, amit a kétváltozós esettől várunk: az egyváltozós $\sqrt{1 + (\varphi')^2}$ ívhosszképlet mintájára.

## Kapocs

- [[concepts/analiii/feluleti-integral]] — a felületelemmel felírt integrálfogalmak
- [[concepts/analiii/green-tetel-harom-dimenzioban]] — a felületelem szerepe a térbeli integráltételekben
- [[concepts/analii/ivhossz]] — az egyváltozós analogon, amely felületre nem általánosítható közvetlenül
- [[concepts/analii/forgastest-felszine]] — a forgásfelület felszíne mint speciális eset
