---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Newton–Leibniz formula síkban és térben

A gradiens integrálja a tartományon egyenlő a függvény határon vett, kifelé mutató normálissal súlyozott integráljával. Az egyváltozós Newton–Leibniz formula közvetlen többváltozós megfelelője.

## Tartalom

### Síkban

**Tétel (Newton–Leibniz formula síkban).** Ha $\operatorname{cl}(K)\subset G\subset\mathbb{R}^2$, $K$ Jordan-tartomány, amelynek határa pozitív irányítású, szakaszonként folytonosan differenciálható görbe, és $f : G \to \mathbb{R}$ folytonosan differenciálható, akkor

$$\int_K (\operatorname{grad} f)\,\mathrm{d}A = \int_{\partial K} f\,\mathbf{n}\,\mathrm{d}s .$$

Mindkét oldal **vektor**: a bal oldalon a gradiens koordinátánként integrálva, a jobb oldalon a skalár $f$ szorozva a normálvektorral.

*Bizonyítás.* A $\mathbf{n}\,\mathrm{d}s = (\mathrm{d}y, -\mathrm{d}x)^t$ átírással és a Green-tétel két állításával:

$$\int_{\partial K} f\,\mathbf{n}\,\mathrm{d}s = \begin{pmatrix}\int_{\partial K} f\,\mathrm{d}y \\ -\int_{\partial K} f\,\mathrm{d}x\end{pmatrix} = \begin{pmatrix}\int_K D_xf\,\mathrm{d}A \\ \int_K D_yf\,\mathrm{d}A\end{pmatrix} = \int_K (\operatorname{grad} f)\,\mathrm{d}A. \qquad \square$$

Ez tehát a Green-tétel két fele, vektorba rendezve.

### Egy dimenzióban

Ugyanez elmondható egyváltozós, folytonosan differenciálható $f : [a,b]\to\mathbb{R}$ függvényre: a határ két, egységnyi súlyú pontból áll, a felső végpontban a kifelé mutató normálvektor $+1$, az alsóban $-1$, tehát

$$\int_{[a,b]} f'(x)\,\mathrm{d}x = f(a)\cdot(-1) + f(b)\cdot(+1).$$

### Térben

**Tétel (Newton–Leibniz formula a térben).** Ha $G\subset\mathbb{R}^3$ nyílt, $K\subset G$ korlátos, zárt krumpli, amelynek $\partial K$ határa darabonként folytonosan differenciálható felület, ezeken az irányított normálvektor mindig kifelé mutat, és $f : G\to\mathbb{R}$ folytonosan differenciálható, akkor

$$\int_K (\operatorname{grad} f)\,\mathrm{d}V = \int_{\partial K} f\cdot \overrightarrow{\mathrm{d}A}.$$

*Bizonyítás.* A Green-tétel háromdimenziós változatát ($\int_K D_i f\,\mathrm{d}V = \int_{\partial K} f\,\overrightarrow{\mathrm{d}A}_i$) mind a három koordinátára alkalmazzuk, és az eredményeket vektorba rendezzük. $\square$

### Következmény

Az $f \equiv 1$ konstans függvényre a bal oldal eltűnik, tehát bármely zárt krumpli héjára

$$\int_{\partial K}\overrightarrow{\mathrm{d}A} = \mathbf{0}.$$

Szemléletesen: egy zárt felület irányított felületelemei kioltják egymást — egy zárt testet nem lehet „egy irányba tolni" a felszínével.

## Kapocs

- [[concepts/analii/newton-leibniz-tetel]] — az egyváltozós ős, amelyet ez általánosít
- [[concepts/analiii/green-tetel]] — a bizonyítás eszköze síkban
- [[concepts/analiii/green-tetel-harom-dimenzioban]] — a bizonyítás eszköze térben
- [[concepts/analiii/kulso-normalis]] — az $\mathbf{n}\,\mathrm{d}s$ jelölés
- [[concepts/analiii/altalanos-stokes-tetel]] — a formula helye az integráltételek családjában
- [[concepts/analiii/jordan-tartomany-sulypontja]] — alkalmazás: súlypont vonalintegrállal
