---
tags: [concept]
sources: [04_ea_An3_2022_tavasz.pdf]
references: []
derivation: source
updated: 2026-09-14
---

# Függvénygrafikon érintősíkja

Az $\mathbb{R}\to\mathbb{R}$ függvénygrafikon érintőegyenesének fogalma $\mathbb{R}^2\to\mathbb{R}$ függvényekre az **érintősík**: az a sík, amely a grafikont a totális differenciálhatóság pontjában elsőrendben legjobban közelíti, normálvektora a gradiensből épül fel.

## Tartalom

### Sík egyenlete normálvektorral

Egy $S\subset\mathbb{R}^3$ sík felírható $\mathbf{n}=(A,B,C)\in\mathbb{R}^3$ nemnulla normálvektorral és egy $P_0=(x_0,y_0,z_0)\in S$ ponttal: $\mathbf{r}=(x,y,z)\in S$ pontosan akkor, ha az $\mathbf{r}-\mathbf{r}_0$ vektor merőleges $\mathbf{n}$-re,

$$\langle \mathbf{r}-\mathbf{r}_0,\ \mathbf{n}\rangle = 0 \quad\Longleftrightarrow\quad A(x-x_0)+B(y-y_0)+C(z-z_0)=0.$$

### A linearizálásból az érintősíkig

Legyen $f\in\mathbb{R}^2\to\mathbb{R}$, $(x_0,y_0)\in\operatorname{int} D_f$, és tegyük fel, hogy $f\in D\{(x_0,y_0)\}$ — azaz [[concepts/analiii/frechet-derivalt|totálisan differenciálható]]. Ekkor a [[concepts/analiii/gradiens-parcialis-derivaltakbol|gradiens]] és a [[concepts/analiii/parcialis-derivalt|parciális deriváltak]] segítségével

$$f(x,y) - f(x_0,y_0) \approx \partial_1 f(x_0,y_0)(x-x_0) + \partial_2 f(x_0,y_0)(y-y_0) \qquad \bigl((x,y)\approx(x_0,y_0)\bigr).$$

Legyen $z_0 := f(x_0,y_0)$. Az

$$(\ast)\qquad z - z_0 = \partial_1 f(x_0,y_0)(x-x_0) + \partial_2 f(x_0,y_0)(y-y_0)$$

egyenlet egy olyan sík egyenlete a térben, amely átmegy a $(x_0,y_0,f(x_0,y_0))$ ponton, és normálvektora

$$\mathbf{n} = \bigl(\partial_1 f(x_0,y_0),\ \partial_2 f(x_0,y_0),\ -1\bigr).$$

### Definíció

Az $f\in\mathbb{R}^2\to\mathbb{R}$ függvény grafikonjának a $P=(x_0,y_0,f(x_0,y_0))$ pontban **van érintősíkja**, ha $f$ totálisan differenciálható az $(x_0,y_0)$ pontban: $f\in D\{(x_0,y_0)\}$. Az érintősík egyenlete $(\ast)$, egy normálvektora $\mathbf{n}=(\partial_1 f(x_0,y_0),\partial_2 f(x_0,y_0),-1)$.

### Miért kell a totális differenciálhatóság

A puszta parciális deriválhatóság nem elég: az $(\ast)$ sík csak akkor közelíti a grafikont *minden* irányban elsőrendben, ha $f$ totálisan differenciálható — ez pontosan a [[concepts/analiii/differencialhatosagi-fogalmak-hierarchiaja|differenciálhatósági fogalmak hierarchiája]] lapon tárgyalt jelenség. Ha csak a parciális deriváltak léteznek, a metszetgörbékhez (az $x_0$, ill. $y_0$ átmenő koordinátasíkokkal párhuzamos síkmetszetekhez) tartozó érintőegyenesek léteznek, de ezek nem feltétlenül feszítenek ki egy, a felületet minden irányban közelítő síkot.

### Kapcsolat a nívófelülettel

A gradiens $(\partial_1 f(x_0,y_0), \partial_2 f(x_0,y_0))$ vetülete ugyanaz a vektor, amely a $z=f(x,y)$ felület $F(x,y,z):=f(x,y)-z$ alakú nívófelületére merőleges — az érintősík normálvektora $\mathbf{n}=(\operatorname{grad}f(x_0,y_0),-1)$ tehát a [[concepts/analiii/nivofelulet-es-gradiens|nívófelület-gradiens merőlegesség]] speciális esete, ahol az egyik "koordináta" maga $z$.

## Kapocs

- [[concepts/analiii/feluleti-erintosik]] — az általános, tetszőleges paraméterezésű felület érintősíkja; ez a lap ennek explicit (függvénygrafikonos) speciális esete.
- [[concepts/analiii/frechet-derivalt]] — a totális differenciálhatóság, amely az érintősík létezésének feltétele.
- [[concepts/analiii/parcialis-derivalt]] — az érintősík normálvektorának koordinátái.
- [[concepts/analiii/gradiens-parcialis-derivaltakbol]] — a normálvektor első két koordinátája mint gradiens.
- [[concepts/analiii/nivofelulet-es-gradiens]] — a merőlegességi állítás általánosabb kontextusa.
- [[concepts/analiii/differencialhatosagi-fogalmak-hierarchiaja]] — miért nem elég a parciális deriválhatóság az érintősík létezéséhez.
