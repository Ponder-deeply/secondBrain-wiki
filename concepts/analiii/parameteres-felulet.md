---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf, 13_ea_An3_2022_tavasz.pdf]
derivation: source
updated: 2026-09-14
---

# Paraméteres felület, felületelem és felszín

Síkbeli paramétertartományból a térbe képező függvény mint felület. A két parciális derivált vektoriális szorzata adja az irányított felületelemet, ennek hossza a felszínelem.

## Tartalom

### Definíció

Ha $P \in \mathcal{J}(\mathbb{R}^2)$ (Jordan-mérhető síkbeli halmaz), akkor a $P\to\mathbb{R}^3$ függvényeket *paraméteres felületnek* hívjuk. Beszélhetünk folytonos, differenciálható, folytonosan differenciálható, darabonként folytonosan differenciálható felületekről is.

### A felület megadásának módjai

Egy $\mathbb{R}^3$-beli felület háromféleképp adható meg.

1. **Explicit (Euler–Monge-féle) alak.** Ha $f\in\mathbb{R}^2\to\mathbb{R}$, $f\in C^1$, akkor a grafikonja

   $$\operatorname{graph}f := \{(x,y,f(x,y))\in\mathbb{R}^3 \mid (x,y)\in\mathcal{D}_f\}\subset\mathbb{R}^3$$

   egy $\mathbb{R}^3$-beli felület; ilyenkor a $z=f(x,y)$ egyenletű felületről is szokás beszélni. Példa: $f(x,y)=x^2+y^2$ grafikonja forgásparaboloid.

2. **Implicit alak.** Ha $G\in\mathbb{R}^3\to\mathbb{R}$ adott függvény, akkor az

   $$\{(x,y,z)\in\mathcal{D}_G \mid G(x,y,z)=0\}\subset\mathbb{R}^3$$

   halmaz „jó esetben" szintén $\mathbb{R}^3$-beli felület. Példa: $G(x,y,z)=x^2+y^2+z^2-R^2$ nívóhalmaza az origó középpontú, $R$ sugarú gömbfelület.

3. **Gauss-féle paraméteres megadás.** Legyenek $I_1,I_2\subset\mathbb{R}$ intervallumok, $\mathbb{I}^2:=I_1\times I_2\subset\mathbb{R}^2$, és $F:=(F_1,F_2,F_3):\mathbb{I}^2\to\mathbb{R}^3$, $F\in C^1(\mathbb{I}^2,\mathbb{R}^3)$. Ekkor egy $\mathcal{F}\subset\mathbb{R}^3$ halmazt **egyszerű sima felületdarabnak** (ESF) nevezünk, ha létezik olyan $F\in C^1(\mathbb{I}^2,\mathbb{R}^3)$, hogy

   - $F:\mathbb{I}^2\to\mathcal{F}$ bijekció,
   - $\operatorname{rang}F'(w) = 2$ minden $w\in\mathbb{I}^2$ pontban,

   ahol $F'(u,v) = \bigl[\partial_1F(w)\ \ \partial_2F(w)\bigr]$ a $3\times 2$-es Jacobi-mátrix, $\partial_1F(w):=\partial_uF(w)$, $\partial_2F(w):=\partial_vF(w)$ az oszlopai. Ekkor $F$ az $\mathcal{F}$ felület egy **Gauss-féle paraméterezése**. (Ez a fogalom a fenti Jordan-mérhető tartományon értelmezett paraméteres felület finomítása: a paramétertartomány itt intervallum, és a rangfeltétel biztosítja a reguláris — sehol nem elfajuló — érintőt.)

   Ha $g(x,y):=(x,y,f(x,y))$, akkor egy explicit alakban adott felület Gauss-féle paraméterezése $F(w)=(u,v,f(u,v))$, $w=(u,v)\in\mathbb{I}^2$; az origó középpontú $R$ sugarú gömbfelületé pedig $F(u,v) = (R\cos u\sin v,\,R\sin u\sin v,\,R\cos v)$, $(u,v)\in[0,2\pi)\times[0,\pi]$.

### Különböző paraméterezések

Ha $\mathcal{F}\subset\mathbb{R}^3$ ESF és $F:\mathbb{I}^2\to\mathcal{F}$ ennek egy paraméterezése, $\mathbb{J}^2\subset\mathbb{R}^2$ intervallum és $S:\mathbb{J}^2\to\mathbb{I}^2$ olyan $C^1$-beli bijekció, amelyre $\det S'(w)\neq 0$ ($w\in\mathbb{J}^2$), akkor

$$G := F\circ S : \mathbb{J}^2\to\mathcal{F}$$

az $\mathcal{F}$ felület egy másik paraméterezése. Ugyanaz a felület tehát több, lényegesen különböző paraméterezéssel is előáll — ahogy [[concepts/analiii/parameteres-gorbe|görbék esetén]] is.

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
- [[concepts/analiii/feluleti-gorbe]] — a paraméterezés parciális deriváltjaiból kifeszített felületi görbék
- [[concepts/analiii/feluleti-erintosik]] — a felület pontbeli érintősíkja a paraméterezésből
- [[concepts/analii/ivhossz]] — az egyváltozós analogon, amely felületre nem általánosítható közvetlenül
- [[concepts/analii/forgastest-felszine]] — a forgásfelület felszíne mint speciális eset
