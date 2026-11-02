---
tags: [concept]
sources: [SimonP-Anal2.pdf, 07_ea_An3_2022_tavasz.pdf, An_III_Gyak_2022_tavasz.pdf, Analizis-3-gyakorlati-jegyzet-ELTE-IK.pdf, gyakorlat.pdf, RopzhKerdesek.pdf, ElozetesKerdesekMegajanlottVizsgajegyhez1.pdf, 08_gyak_An_III_2022_tavasz.pdf]
references: ["Simon Péter: Analízis II., 4.5.1.1–4.5.1.3. Tétel"]
derivation: source
kind: procedure
element: fire
updated: 2026-10-21
---

# Lokális szélsőérték feltételei több változóban

Három tétel, mindhárom a Peano-maradéktagos Taylor-formulából: elsőrendű **szükséges** feltétel ($\operatorname{grad} f(a) = 0$), másodrendű **elégséges** ($Q^f_a$ definit), másodrendű **szükséges** ($Q^f_a$ szemidefinit) — és a rés a második és harmadik között sosem záródik be.

## Tartalom

### A fogalmak

Az $f \in \mathbb{R}^n \to \mathbb{R}$ függvénynek az $a \in D_f$ pontban **lokális maximuma** van, ha egy alkalmas $K(a)$ környezettel $f(x) \le f(a)$ minden $x \in K(a) \cap D_f$-re; **abszolút maximuma**, ha $f(x) \le f(a)$ az egész $D_f$-en. A minimum analóg. Abszolút szélsőérték mindig lokális is.

### Elsőrendű szükséges feltétel

Ha $f$-nek $a \in \operatorname{int} D_f$-ben lokális szélsőértéke van és $f \in D\{a\}$, akkor

$$f'(a) = \operatorname{grad} f(a) = 0, \quad\text{azaz}\quad \partial_1 f(a) = \dots = \partial_n f(a) = 0.$$

**Bizonyítás.** Tetszőleges $e$ egységvektorral az $f_e(t) := f(a+te)$ egyváltozós függvénynek is lokális szélsőértéke van $0$-ban, és a [[concepts/analiii/lancszabaly|láncszabály]] szerint differenciálható, tehát az egyváltozós elsőrendű feltétel szerint $\partial_e f(a) = f_e'(0) = 0$. Ez minden irányra igaz, speciálisan az $e_j$-kre.

A feltétel **nem elégséges** — ezt már $n = 1$-ben is láttuk ($f(x) = x^3$).

### Másodrendű elégséges feltétel

Ha $a \in \operatorname{int} D_f$-ben (a) $f \in D^2\{a\}$, (b) $\operatorname{grad} f(a) = 0$, (c) $Q^f_a$ pozitív (negatív) definit, akkor $f$-nek $a$-ban lokális minimuma (maximuma) van.

**Bizonyítás.** A [[concepts/analiii/tobbvaltozos-taylor-formula|Peano-alakból]] a (b) miatt

$$f(a+h) - f(a) = \tfrac12 Q^f_a(h) + \eta(h)\|h\|^2, \qquad \eta(h)\to 0.$$

A definitség miatt egy $m > 0$-val $Q^f_a(\xi) \ge m\|\xi\|^2$, tehát

$$f(a+h) - f(a) \ge \left[\tfrac{m}{2} + \eta(h)\right]\|h\|^2.$$

Szűkítsük az $r$ sugarat úgy, hogy $|\eta(h)| < m/4$ legyen; ekkor a jobb oldal $\ge \tfrac{m}{4}\|h\|^2 \ge 0$. **Az egész trükk a $Q^f_a(\xi) \ge m\|\xi\|^2$ egyenletes becslés**, amit az egységgömb kompaktsága ad — pusztán a $Q^f_a(h) > 0$ pontonkénti pozitivitásból nem lehetne legyőzni a hibatagot.

### Másodrendű szükséges feltétel

Ha $f \in D^2\{a\}$ és $f$-nek $a$-ban lokális minimuma (maximuma) van, akkor $\operatorname{grad} f(a) = 0$, és $Q^f_a$ pozitív (negatív) **szemi**definit.

**Bizonyítás (indirekt).** Ha valamely $h \ne 0$-ra $Q^f_a(h) < 0$, akkor a Taylor-formulából $0 < t < r/\|h\|$ mellett

$$f(a + th) - f(a) = \frac{t^2}{2}\left(Q^f_a(h) + 2\eta(th)\|h\|^2\right),$$

és $\eta(th) \to 0$ miatt van olyan $\tau$, amelyre $2|\eta(\tau h)|\|h\|^2 < -Q^f_a(h)/2$; ekkor $f(a+\tau h) < f(a)$, ellentmondás.

### A rés — amit sosem lehet bezárni

| | elsőrendű | másodrendű |
|---|---|---|
| **szükséges** | $\operatorname{grad} f(a) = 0$ | $Q^f_a$ szemidefinit |
| **elégséges** | — | $Q^f_a$ definit |

A szemidefinit-de-nem-definit eset **eldöntetlen**: ilyenkor a másodrendű közelítés nem elég, magasabb rendű tagokat kell nézni. Ez pontosan az egyváltozós $f''(a) = 0$ eset megfelelője, ahol szintén tovább kell derivélni. Az $n = 1$ esetben $Q^f_a(x) = f''(a)x^2$, tehát a definitség az $f''(a)$ előjele — a fenti három tétel az egyváltozós elmélet szó szerinti átirata, csak „előjel" helyett „definitség" áll benne.

### Az $n=2$ speciális eset

Két változóban a $2\times 2$-es szimmetrikus mátrixok definitsége elemi eszközzel — a determináns előjelével — jellemezhető, ami az elégséges feltételt közvetlenül kimondhatóvá teszi $Q^f_a$ kikerülésével.

Legyen $f \in \mathbb{R}^2 \to \mathbb{R}$, $a \in \operatorname{int} D_f$, $f \in C^2\{a\}$, $\operatorname{grad} f(a) = (0,0)$, és jelölje

$$D(a) := \det f''(a) = \det \begin{bmatrix} \partial_{11}f(a) & \partial_{12}f(a) \\ \partial_{21}f(a) & \partial_{22}f(a)\end{bmatrix}.$$

Ekkor:

1. ha $D(a) > 0$ és $\partial_{11}f(a) > 0$ (ill. $< 0$), akkor $f$-nek $a$-ban lokális minimuma (ill. maximuma) van;
2. ha $D(a) < 0$, akkor $f$-nek $a$-ban **nincs** lokális szélsőértéke — az ilyen $a$ pontot **nyeregpontnak** nevezzük.

Az 1. pont a másodrendű elégséges feltétel speciális esete a $2\times 2$-es Sylvester-kritériummal ($d_1 = \partial_{11}f(a) > 0$, $d_2 = D(a) > 0$ pozitív definitséget ad); a 2. pont a másodrendű szükséges feltételből következik, hiszen $D(a) < 0$ épp azt jelenti, hogy $Q^f_a$ indefinit, ami sem pozitív, sem negatív szemidefinit — tehát a szükséges feltétel sérül. A $D(a) = 0$ eset — akárcsak az általános $n$-ben a szemidefinit-de-nem-definit eset — eldöntetlen marad.

### A gyakorlati recept

1. Old meg a $\operatorname{grad} f(x) = 0$ egyenletrendszert — ezek a **stacionárius pontok**.
2. Írd fel minden ilyen pontban a [[concepts/analiii/hesse-matrix|Hesse-mátrixot]].
3. Döntsd el a definitséget [[concepts/analiii/kvadratikus-alak-definitsege|Sylvester-kritériummal]]: definit $\Rightarrow$ szélsőérték, indefinit $\Rightarrow$ nyeregpont (nincs szélsőérték, mert a szükséges feltétel sérül), szemidefinit-nem-definit $\Rightarrow$ a módszer nem dönt.

### Stacionárius pont és megjegyzések (gyak 8. lap)

Az $a\in\operatorname{int}D_f$ az $f$ **stacionárius pontja**, ha $f\in D\{a\}$ és $f'(a)=0$. Az elsőrendű szükséges feltétel szerint a lokális szélsőértékhelyek (differenciálható $f$ esetén) a stacionárius pontok között vannak: ezek az $\partial_1f=\dots=\partial_nf=0$ egyenletrendszer megoldásai. A feltétel nem elégséges ($x^3$, $a=0$). A másodrendű elégséges feltétel $f\in C^2\{a\}$ mellett használható; ha az eredmény indefinit Hesse-mátrix, az $a$ pontban nincs szélsőérték (tétel, $n$ tetszőleges), ha elfajult (szemidefinit, de nem definit), egyedi vizsgálat kell.

### Feladatok (gyak 8. lap megoldásai szerint)

A lap munkapéldái a fenti 2., 3., 4., 5., 6. példával egyeznek (újraszámolva, eltérés nincs); a lap módszerei:

- *$x^3-3x^2+2xy+y^2$*: $y=-x$ után $3x^2-8x=0$; $D_2=12x-16$, $(0,0)$ nyeregpont ($D_2=-16$), $(\tfrac83,-\tfrac83)$ lokális minimum ($D_1=10,\ D_2=16$).
- *$x^4+y^4-x^2-2xy-y^2$*: a stacionárius pontok $(0,0),(1,1),(-1,-1)$; a két utóbbi lokális minimum; az origóban $D_2=0$ miatt a feltétel nem alkalmazható, ezért a függvényt $x^4+y^4-(x+y)^2$ alakban írva: $y=-x$ mentén $2x^4>0$, az $x$-tengely mentén $x^2(x^2-1)<0$ ($0<|x|<1$), azaz nincs szélsőérték.
- *$x^4y^5$*: az origó és a tengelyek a stacionárius pontok, $f''=\begin{bmatrix}12x^2y^5&20x^3y^4\\20x^3y^4&20x^4y^3\end{bmatrix}$ ezeken nulla. Az $f$ előjele az $y$ előjele ($x\ne0$), a stacionárius pontokban az érték $0$: az $y$-tengely $y>0$ pontjai (nem szigorú) lokális minimumhelyek, a $y<0$ pontjai lokális maximumhelyek (a lap szövege itt elírásból mindkettőnél $y>0$-t mond), az $x$-tengely pontjaiban (az origót is beleértve) nincs szélsőérték.
- *$x^4+y^2$, $x^3+y^2$*: lásd 4. példa; a másodrendű szükséges feltétel nem elégséges.
- A $2\times2$ Sylvester-kritériumot a [[concepts/analiii/kvadratikus-alak-definitsege|kvadratikus alak definitségénél]] a lap bizonyítja ($Q(h)=ah_1^2+2bh_1h_2+ch_2^2$).

**Recept (gyakorlati forma).** (1) $\operatorname{grad} f=0$ megoldása: stacionárius pontok (a szükséges feltétel miatt minden szélsőérték ezek között van, ha $f$ differenciálható). (2) Hesse-mátrix a pontokban, Sylvester: definit $\Rightarrow$ szélsőérték, indefinit ($d_2<0$) $\Rightarrow$ nyeregpont. (3) **Elfajult eset** (szemidefinit, pl. $d_2=0$): a tételek nem döntenek, közvetlen vizsgálat kell:
- *globális egyenlőtlenséggel* — ha $f(x)\ge f(a)$ mindenütt, akkor abszolút minimum (pl. $x^4+y^2\ge0$);
- *egy irány vagy görbe mentén* — ha a ponthoz bármilyen közel van $f(x)>f(a)$ és $f(x)<f(a)$ is, nincs szélsőérték (pl. $x^3+y^2$ az $y=0$ mentén előjelet vált).

**Munkapéldák.**

1. $f=x^2+xy+y^2-5x-4y+1$: $\partial_1f=2x+y-5=0$, $\partial_2f=x+2y-4=0$, így $(2,1)$; $f''=\begin{bmatrix}2&1\\1&2\end{bmatrix}$, $d_1=2,\ d_2=3>0$, tehát lokális minimum, $f(2,1)=-6$.
2. $f=x^3-3x^2+2xy+y^2$: $3x^2-6x+2y=0$, $2x+2y=0\Rightarrow y=-x$, $3x^2-8x=0$: $(0,0)$ és $(\tfrac83,-\tfrac83)$. $f''=\begin{bmatrix}6x-6&2\\2&2\end{bmatrix}$; $(0,0)$-ban $d_2=-16<0$ nyeregpont; $(\tfrac83,-\tfrac83)$-ban $\begin{bmatrix}10&2\\2&2\end{bmatrix}$ pozitív definit: lokális minimum, értéke $-\tfrac{256}{27}$.
3. $f=x^4+y^4-x^2-2xy-y^2$: stacionárius: $4x^3=2x+2y=4y^3\Rightarrow x=y$, $4x(x^2-1)=0$, azaz $(0,0),(1,1),(-1,-1)$. $f''=\begin{bmatrix}12x^2-2&-2\\-2&12y^2-2\end{bmatrix}$. $(\pm1,\pm1)$ (azonos előjellel): $\begin{bmatrix}10&-2\\-2&10\end{bmatrix}$ pozitív definit, lokális minimum, $f=-2$. $(0,0)$: $\begin{bmatrix}-2&-2\\-2&-2\end{bmatrix}$, $d_2=0$, negatív szemidefinit: **nem dönt**. Az $x$-tengely mentén $f(x,0)=x^2(x^2-1)<0$ kis $x\ne0$-ra, az $y=-x$ mentén $f(x,-x)=2x^4>0$; így minden környezetben van negatív és pozitív érték is: **nincs** lokális szélsőérték.
4. $f=x^4+y^2$ és $g=x^3+y^2$ az origóban: mindkettőnél $f'=g'=0$, a Hesse-mátrix $\begin{bmatrix}0&0\\0&2\end{bmatrix}$ pozitív szemidefinit, nem definit — a másodrendű szükséges feltétel mindkettőre teljesül. De $f\ge0=f(0,0)$, tehát abszolút minimum, míg $g(x,0)=x^3$ előjelet vált: nincs szélsőérték. **A másodrendű szükséges feltétel tehát nem elégséges.**
5. $f=x^4y^5$: $\operatorname{grad}f=(4x^3y^5,5x^4y^4)=0$ pontosan a tengelyeken. Az $x$-tengely pontjaiban ($x\ne0$) és az origóban $y^5$ előjelet vált, így nincs szélsőérték; az $y$-tengely pontjaiban ($y\ne0$) kis környezetben $x^4\ge0$, így $f$ előjele $y^5$-é: $y>0$-nál (nem szigorú) lokális minimum, $y<0$-nál lokális maximum. Hasonlóan $x^3y^5$ (09_gyak_An_III_2022_tavasz.pdf is tárgyalja: a Hesse-determináns a tengelyeken $0$): $\operatorname{grad}=0$ a tengelyeken, és mindenütt előjelet vált ($\operatorname{sgn}=\operatorname{sgn}xy$), nincs lokális szélsőérték.
6. $f=8x+\tfrac1y+\tfrac yx$ ($xy\ne0$): $8-\tfrac y{x^2}=0$, $-\tfrac1{y^2}+\tfrac1x=0\Rightarrow y=8x^2$, $y^2=x$, $64x^4=x$, $x=\tfrac14$, $y=\tfrac12$. $f''=\begin{bmatrix}2y/x^3&-1/x^2\\-1/x^2&2/y^3\end{bmatrix}=\begin{bmatrix}64&-16\\-16&16\end{bmatrix}$, $d_2=768>0$: lokális minimum, $f=6$.
7. $f=(1+e^y)\cos x-ye^y$: $\partial_1f=-(1+e^y)\sin x=0\Rightarrow x=k\pi$; $\partial_2f=e^y(\cos x-1-y)=0\Rightarrow y=(-1)^k-1$. Pontok: $(2k\pi,0)$ és $((2k+1)\pi,-2)$. Az elsőkben $f''=\begin{bmatrix}-2&0\\0&-1\end{bmatrix}$ negatív definit: lokális maximum, $f=2$; a másodikakban $f''=\begin{bmatrix}1+e^{-2}&0\\0&-e^{-2}\end{bmatrix}$ indefinit: nyeregpont.
8. $f=(2x^2+3y^2)e^{-x^2-y^2}$: $\partial_1f=2xe^{-x^2-y^2}(2-2x^2-3y^2)$, $\partial_2f=2ye^{-x^2-y^2}(3-2x^2-3y^2)$. Pontok: $(0,0)$ (minimum, mert $f\ge0=f(0,0)$), $(0,\pm1)$ (a Hesse-mátrix $\operatorname{diag}(-2/e,-12/e)$, lokális maximum, $f=3/e$), $(\pm1,0)$ ($\operatorname{diag}(-8/e,\,2/e)$ indefinit: nyeregpont). Hasonlóan $(x^2+y^2)e^{-x^2-y^2}$: $t=x^2+y^2$ szerint $te^{-t}$, a minimum az origóban, a (nem szigorú) maximum az $x^2+y^2=1$ körön, értéke $1/e$.
9. $f=x^3+y^3+z^2+12xy+2z$ (három változó): ugyanaz a recept $3\times3$-as Hesse-mátrixszal és a teljes Sylvester-kritériummal.

**További gyakorló feladatok** (megoldás nélkül, a forrásban): $x^4y^2(4-x-y)$, $x^3y^2(4-x-y)$, $2x^3-6x+y^3-12y+5$, $x^2+2y+\tfrac2{xy}$, $\tfrac yx+\tfrac xy+(x-1)^{2022}$, $(x^2+2y^2)e^{-x^2-y^2}$, $x^3+y^3-9xy$.

## Kapocs

- [[concepts/analiii/tobbvaltozos-taylor-formula]] — mindhárom bizonyítás forrása.
- [[concepts/analiii/kvadratikus-alak-definitsege]] — a döntési kritérium.
- [[concepts/analiii/hesse-matrix]] — a vizsgálandó mátrix.
- [[concepts/analiii/felteteles-szelsoertek]] — ugyanez korlátozó feltételekkel.
- [[concepts/analiii/abszolut-szelsoertek]] — ugyanez a szükséges feltétel, korlátos zárt halmazon a globális szélsőérték keresésének első lépéseként.
- [[concepts/analii/lokalis-szelsertekek]] — az egyváltozós eredeti.
- [[concepts/analiii/vizsgakerdesek-es-bizonyitando-tetelek]] — a témához tartozó megajánlott vizsgajegy- és röpdolgozat-kérdések.
