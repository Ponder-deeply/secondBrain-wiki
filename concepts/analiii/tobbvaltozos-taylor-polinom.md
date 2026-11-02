---
tags: [concept]
sources: [SimonP-Anal2.pdf, 06_ea_An3_2022_tavasz.pdf, 07_ea_An3_2022_tavasz.pdf, An_III_Gyak_2022_tavasz.pdf, Analizis-3-gyakorlati-jegyzet-ELTE-IK.pdf, gyakorlat.pdf, 07_gyak_An_III_2022_tavasz.pdf]
references: ["Simon Péter: Analízis II., 4.3. szakasz, multiindexes jelölés"]
derivation: source
kind: definition
element: fire
updated: 2026-10-21
---

# Többváltozós Taylor-polinom és a multiindexes jelölés

A multiindex az a jelölési trükk, amellyel a többváltozós Taylor-polinom pontosan olyan alakot ölt, mint az egyváltozós: $T_{a,s}f(x) = \sum_{|i| \le s} \frac{\partial^i f(a)}{i!}(x-a)^i$.

## Tartalom

### Multiindex

Egy $i = (i_1, \dots, i_n) \in \mathbb{N}^n$ vektort **multiindexnek** nevezünk. Hozzá tartozó jelölések:

$$|i| := \|i\|_1 = \sum_{j=1}^n i_j, \qquad i! := \prod_{j=1}^n i_j!, \qquad x^i := \prod_{j=1}^n x_j^{i_j},$$

és $\partial^i f$ az a parciális derivált, amelyben az $1$-es változó szerint $i_1$-szer, ..., az $n$-edik szerint $i_n$-szer deriválunk. Például $f(x,y,z) = x^3 + y^2 z + z^3 + xyz$ és $i = (2,0,1)$ esetén $\partial^i f = \partial_{113} f = 0$.

**A jelölés csak a [[concepts/analiii/young-tetel|Young-tétel]] miatt jóldefiniált**: $f \in D^{|i|}\{a\}$ mellett az $|i|$ hosszú $1\dots1\dots n\dots n$ jelsorozat bármely permutációja ugyanazt a deriváltat adja, ezért elég megmondani, melyik változó szerint hányszor deriválunk — a sorrendet nem kell.

Ha $n = 1$, akkor $i = i_1 \in \mathbb{N}$, $|i| = i$, $i!$ a szokásos faktoriális, $x^i$ a szokásos hatvány: a jelölés visszaadja az egyváltozós esetet.

### Homogén polinomok

Rögzített $s$-re a Taylor-polinom $k = s$-hez tartozó tagja, $\sum_{|i|=s} \frac{\partial^i f(a)}{i!}(x-a)^i$, épp egy **$n$-változós $s$-edfokú homogén polinom** $(x-a)$-ban: ha $|i| = s$ és $a_i \in \mathbb{R}$ nem mind nulla, akkor $x \mapsto \sum_{|i|=s} a_i x^i$ ilyen. Példák:

- $n=1$: $P_{1,s}(x) = a\cdot x^s$ — az egyváltozós hatványtag.
- $n=2$, $s=1$: $i \in \{(1,0),(0,1)\}$, tehát $P_{2,1}(x_1,x_2) = ax_1 + bx_2$.
- $n=2$, $s=2$: $i \in \{(2,0),(1,1),(0,2)\}$, tehát $P_{2,2}(x_1,x_2) = ax_1^2 + bx_1x_2 + cx_2^2$.

Ez mutatja meg konkrétan, miért indexeli a Taylor-polinom $k$-adik tagját éppen az $|i|=k$ feltételű multiindexek összege: a tag maga egy $k$-adfokú homogén polinom.

### Szakasz

$a, b \in \mathbb{R}^n$ esetén a zárt, illetve nyílt szakasz

$$[a,b] := \{a + t(b-a) : 0 \le t \le 1\}, \qquad (a,b) := \{a + t(b-a) : 0 < t < 1\}.$$

### A Taylor-polinom

Ha $a \in \operatorname{int} D_f$, $s \in \mathbb{N}$ és $f \in D^s\{a\}$ (ahol $D^0\{a\} := C\{a\}$), akkor az $f$ függvény $a$-hoz tartozó **$s$-edrendű Taylor-polinomja**

$$T_{a,s}f(x) := \sum_{k=0}^s \ \sum_{i\in\mathbb{N}^n,\,|i|=k} \frac{\partial^i f(a)}{i!}\cdot (x-a)^i \qquad (x \in \mathbb{R}^n).$$

Nyilván $T_{a,0}f \equiv f(a)$ és $T_{a,s}f(a) = f(a)$.

### Az első két tag, kiírva

- $k = 1$: az egyetlen $|i| = 1$ típusú multiindex a $j$-edik egységvektor, $i! = 1$, tehát a tag $\sum_j \partial_j f(a)(x_j - a_j) = \langle \operatorname{grad} f(a), x - a\rangle$.
- $k = 2$: a tag $\tfrac12 \langle f''(a)(x-a), x-a\rangle = \tfrac12 Q^f_a(x-a)$ — itt jelenik meg a [[concepts/analiii/hesse-matrix|Hesse-mátrix]]. A $\tfrac12$ a vegyes tagok kétszeres előfordulásából és az $i!$-ból együtt jön ki.

Tehát

$$T_{a,2}f(x) = f(a) + \langle \operatorname{grad} f(a), x-a\rangle + \tfrac12 Q^f_a(x-a),$$

ami pontosan az egyváltozós $f(a) + f'(a)h + \tfrac12 f''(a)h^2$ mintája.

### A második Taylor-polinom mátrixos alakja (gyak 7. lap, 1. feladat)

Ha $f\in D^2\{a\}$, akkor

$$T_{a,2}f(a+h)=f(a)+\langle f'(a),h\rangle+\tfrac12\langle f''(a)\cdot h,h\rangle .$$

A bizonyítás a multiindexek felsorolása. $|i|=1$: $i=e_j$, $i!=1$, $h^i=h_j$, $\partial^if=\partial_jf$, így a tag $\sum_j\partial_jf(a)h_j=\langle f'(a),h\rangle$. $|i|=2$: vagy $i=e_j+e_l$ ($j<l$; $i!=1$, $h^i=h_jh_l$, $\partial^if=\partial_{jl}f$), vagy $i=2e_r$ ($i!=2$, $h^i=h_r^2$, $\partial^if=\partial_r^2f$). A tagok összege $\sum_{j<l}\partial_{jl}fh_jh_l+\tfrac12\sum_r\partial_r^2fh_r^2=\tfrac12\sum_{j,l}\partial_{jl}f\,h_jh_l$ (a vegyes tagok a $(j,l)$ és $(l,j)$ párból adódnak, ez használja a Young-tételt), ez pedig a [[concepts/analiii/hesse-matrix|Hesse-mátrixszal]] $\tfrac12\langle f''(a)h,h\rangle$.

**Gyakorlati receptek (gyak 7. lap).** A $P$-polinom másodfokú Taylor-polinomja az $a=(1,-2)$ pontban $5+2(x-1)^2-(x-1)(y+2)-(y+2)^2$ ($h=(x-1,y+2)$ visszahelyettesítéssel), és mivel a harmadrendű deriváltak nullák, a Lagrange-maradék $0$: $P=T_{a,2}P$ az egész síkon. Az első Taylor-polinom közelítésre jó: $x^y\approx1+3(x-1)=3x-2$ az $(1,3)$ körül, tehát $1{,}02^{3{,}01}\approx1{,}06$ (számológép: $1{,}06142$). A $\ln(1+x)\ln(1+y)$ második Taylor-polinomja az origóban $xy$: itt $\partial_x f=\ln(1+y)/(1+x)$, $\partial_{xy}f=1/((1+x)(1+y))$, $\partial_{xx}f=-\ln(1+y)/(1+x)^2$, ezért $f'(0,0)=0$, $f''(0,0)=\begin{bmatrix}0&1\\1&0\end{bmatrix}$ és $T_{a,2}f=\tfrac12\cdot2xy=xy$. Egy közelebb lévő pontban pontosabb: $x=y=0{,}01$-nél $0{,}000099009\ldots$ vs. $0{,}0001$, $x=y=0{,}5$-nél $0{,}164402$ vs. $0{,}25$.

### Feladatok

Módszer: számoljuk ki $f(a)$-t, az első- és másodrendű parciálisokat az $a$-ban, majd írjuk fel $T_{a,2}f(a+h)=f(a)+\langle f'(a),h\rangle+\tfrac12\langle f''(a)h,h\rangle$-et (minden $|i|=k$ multiindex tagja $\dfrac{\partial^if(a)}{i!}h^i$). A $\partial_{12}=\partial_{21}$ (Young) miatt a vegyes tag együtthatója $\partial_{12}f(a)$.

- $P=2x^2-xy-y^2-6x-3y+5$, $a=(1,-2)$: $P(a)=5$, $\partial_1P=\partial_2P=0$, $\partial_{11}P=4$, $\partial_{12}P=-1$, $\partial_{22}P=-2$, ezért $T_{a,2}P=5+2(x-1)^2-(x-1)(y+2)-(y+2)^2$. Mivel $P$ másodfokú, $P=T_{a,2}P$ mindenütt (a harmadrendű derivált $0$). Ugyanez az $(x-1)^k(y+2)^\ell$ szorzatok lineáris kombinációjaként írja fel $P$-t.
- $f=x^2y+xy^2-2xy$, $a=(1,-1)$: $f=T_3f$ (a negyedrendű parciálisok nullák): $f=2+(x-1)-3(y+1)-(x-1)^2-2(x-1)(y+1)+(y+1)^2+(x-1)^2(y+1)+(x-1)(y+1)^2$. Együtthatók: $\partial_1f=1$, $\partial_2f=-3$, $\partial_{11}f=-2$, $\partial_{12}f=-2$, $\partial_{22}f=2$, $\partial_{112}f=\partial_{122}f=2$, $\partial_{111}f=\partial_{222}f=0$. Tehát az $a_{nk}$ együtthatók az $(x-1)^n(y+1)^k$ szerint: $a_{00}=2,a_{10}=1,a_{01}=-3,a_{20}=-1,a_{11}=-2,a_{02}=1,a_{21}=a_{12}=1$, a többi $0$. (A jegyzet kitérője: a harmadrendű tagokat a $\sum_{|i|=3}\partial^if\,h^i/i!=\partial_{111}f\,h_1^3/6+\partial_{112}f\,h_1^2h_2/2+\partial_{122}f\,h_1h_2^2/2+\partial_{222}f\,h_2^3/6$ összeg adja.)
- $f=x^y+y^2\cos(x-1)$, $a=(1,3)$: $f(a)=10$, $\partial_1f=3$, $\partial_2f=6$, $\partial_{11}f=-3$, $\partial_{12}f=1$, $\partial_{22}f=2$, tehát $T_2f=10+3(x-1)+6(y-3)-\tfrac32(x-1)^2+(x-1)(y-3)+(y-3)^2$.
- **Egyértelműség.** $T_{a,s}f$ az egyetlen legfeljebb $s$-edfokú polinom, amelynek $k\le s$ rendű deriváltjai $a$-ban egyeznek $f$-ével; és ha $\lim_{h\to0}\dfrac{f(a+h)-G(a+h)}{\|h\|^s}=0$ egy legfeljebb $s$-edfokú $G$-re, akkor $G=T_{a,s}f$ — vagyis a Taylor-polinom a legjobb polinomközelítés $a$ környezetében (gyakorló feladatok).

## Kapocs

- [[concepts/analiii/tobbvaltozos-taylor-formula]] — a maradéktagos állítások, amelyek ezt a polinomot használják.
- [[concepts/analiii/young-tetel]] — a $\partial^i$ jelölés jogalapja.
- [[concepts/analiii/hesse-matrix]] — a másodfokú tag mátrixa.
- [[concepts/analii/taylor-polinom]] — az egyváltozós eredeti.
