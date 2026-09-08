---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Rotáció (örvénysűrűség)

Vektormező örvénysűrűsége: az a mennyiség, amely megmondja, egy pont körüli kis hurkon mekkora munkát végez a mező egységnyi területre vetítve. Síkban skalár, térben vektor; a Stokes-tétel integrandusa.

## Tartalom

### Szemléletes bevezetés: az örvényerősség

Kertünkben most az örvénylést mérjük. Csónakunkra minden pontban $f$ erő hat a víz sodrása miatt. A kert határán az **örvényerősség** vagy **cirkuláció** azt jelenti, hogy pozitív irányban körbehaladva a sodrás mekkora munkát végez:

$$W = \int_{\partial K}\langle f, \mathrm{d}\mathbf{x}\rangle = \int_{\partial K}(f_1\,\mathrm{d}x + f_2\,\mathrm{d}y).$$

Felosztva a kertet $2r$ oldalú négyzetekre, az $(a,b)$ körüli négyzet határán az oldalfelező pontok erőivel számolva a jobb, bal, felső, alsó oldalon rendre $f_2(a+r,b)\cdot 2r$, $f_2(a-r,b)\cdot(-2r)$, $f_1(a,b+r)\cdot(-2r)$, $f_1(a,b-r)\cdot 2r$ munka adódik, összesen

$$\bigl(f_2(a+r,b) - f_2(a-r,b) - f_1(a,b+r) + f_1(a,b-r)\bigr)\cdot 2r \approx (D_1f_2 - D_2f_1)\cdot(2r)^2 .$$

Ha ezt az összes kis négyzetre összeadjuk, a **belső határokon vett munkák kiesnek** (mindegyiken kétszer, ellentétes irányban haladunk végig), és csak a kert határa menti munka marad: $W = \int_K (D_1f_2 - D_2f_1)\,\mathrm{d}A$. Az integrandust nevezzük az $f$ örvénysűrűségének.

### Definíció síkban

Két dimenzióban az $\mathbf{f}$ vektormező *rotációja* vagy *örvénysűrűsége*

$$\operatorname{rot}\mathbf{f} = D_1f_2 - D_2f_1 = \nabla\times\mathbf{f} = \det(\nabla, \mathbf{f}),$$

ahol $\times$ a síkvektorok keresztszorzata. Síkban tehát a rotáció **skalármező**. Angol nyelvű szakirodalomban *curl* a neve, $\operatorname{curl}\mathbf{f}$ a jelölése.

### Definíció három dimenzióban

Az $\mathbf{f} : G \to \mathbb{R}^3$ vektormező rotációja

$$\operatorname{rot}\mathbf{f} = \nabla\times\mathbf{f} = \begin{pmatrix} D_2f_3 - D_3f_2 \\ D_3f_1 - D_1f_3 \\ D_1f_2 - D_2f_1 \end{pmatrix}.$$

Itt a rotáció **vektormező**. Az örvények ugyanis különböző síkokban fekhetnek: ha egy kis körvonal területvektora $\mathbf{v}$, akkor a körvonalon az örvényerősség $\langle \operatorname{rot}\mathbf{f}, \mathbf{v}\rangle$. Ilyen értelemben a rotáció egy $\mathbb{R}^3\to\mathbb{R}$ lineáris függvényt kódol, és a $\operatorname{rot}\mathbf{f}$ vektor iránya az a tengely, amely körül a mező a leginkább forgat.

Vegyük észre, hogy a harmadik koordináta pontosan a síkbeli rotáció képlete: a síkbeli eset a térbeli $z$-komponense.

### Nem függ a koordinátarendszertől

**Síkban.** Blokkmátrixokkal, a divergenciánál bevezetett $T$ ortogonális, $\det T = 1$ transzformációval:

$$\operatorname{rot}_{\text{új}}\mathbf{f}_{\text{új}} = \det(\nabla_{\text{új}}, \mathbf{f}_{\text{új}}) = \det(T^t\nabla, T^t\mathbf{f}) = \det\bigl(T^t\cdot(\nabla,\mathbf{f})\bigr) = \det T^t\cdot\det(\nabla,\mathbf{f}) = \operatorname{rot}\mathbf{f}.$$

**Térben.** Azt mutatjuk meg, hogy bármely $\mathbf{v}$ vektorra $\langle\operatorname{rot}_{\text{új}}\mathbf{f}_{\text{új}}, \mathbf{v}_{\text{új}}\rangle = \langle\operatorname{rot}\mathbf{f}, \mathbf{v}\rangle$:

$$\langle\operatorname{rot}_{\text{új}}\mathbf{f}_{\text{új}}, \mathbf{v}_{\text{új}}\rangle = \det(T^t\nabla, T^t\mathbf{f}, T^t\mathbf{v}) = \det\bigl(T^t\cdot(\nabla,\mathbf{f},\mathbf{v})\bigr) = \det(\nabla,\mathbf{f},\mathbf{v}) = \langle\operatorname{rot}\mathbf{f}, \mathbf{v}\rangle .$$

Mindkét bizonyítás ugyanazon a ponton fordul: $\det T = 1$. Tükrözésre (ahol $\det T = -1$) a rotáció **előjelet vált** — ezért „pszeudovektor".

### Koordinátafüggetlen definíció

A síkbeli Stokes-tételből, egy pontra összehúzódó tartományokkal:

$$\operatorname{rot}\mathbf{f}(\mathbf{a}) = -\lim_{r\to+0}\frac{1}{2\pi}\int_{|\mathbf{x}-\mathbf{a}|=r}\mathbf{f}\times\mathbf{n}\,\mathrm{d}s .$$

## Kapocs

- [[concepts/analiii/stokes-tetel]] — a tétel, amelynek a rotáció az integrandusa
- [[concepts/analiii/divergencia]] — a párhuzamos fogalom: forrássűrűség örvénysűrűség helyett
- [[concepts/analiii/sikvektorok-keresztszorzata]] — a síkbeli $\nabla\times\mathbf{f}$ jelölés tartalma
- [[concepts/analiii/green-tetel]] — a síkbeli örvényerősség-képlet bizonyítási eszköze
- [[concepts/analiii/kelvin-stokes-tetel]] — a rotáció fluxusa peremes felületen
