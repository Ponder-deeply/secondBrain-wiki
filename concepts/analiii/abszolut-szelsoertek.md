---
tags: [concept]
sources: [08_ea_An3_2022_tavasz.pdf, 09_gyak_An_III_2022_tavasz.pdf, An_III_Gyak_2022_tavasz.pdf, Analizis-3-gyakorlati-jegyzet-ELTE-IK.pdf, gyakorlat.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-21
---

# Abszolút szélsőérték korlátos zárt halmazon

Az egyváltozós Weierstrass-tétel ($f \in C[a,b]$-nek van abszolút maximum- és minimumhelye, amely vagy stacionárius pont, vagy végpont) direkt általánosítása: $\mathbb{R}^n \to \mathbb{R}$ függvény korlátos és zárt halmazon felvett abszolút szélsőértékét a belső stacionárius pontok és a peremen felvett értékek összevetésével találjuk meg.

## Tartalom

### A gondolatmenet

Az egyváltozós esetben, ha $f \in C[a,b]$, akkor a Weierstrass-tétel garantálja az abszolút maximum és minimum létezését, és ha $f$ egy $c$ pontban veszi fel valamelyiket, akkor vagy $c \in \{a,b\}$ (végpont), vagy $c \in (a,b)$ és $f \in D\{c\}$ esetén $f'(c) = 0$ (stacionárius pont). Ezért elég $f$ összes stacionárius pontját és a két végpontot megvizsgálni, és köztük a legnagyobb/legkisebb értéket kiválasztani.

Ez a gondolatmenet szó szerint átvihető többváltozós függvényekre.

### A tétel

Legyen $H \subset (\mathbb{R}^n, \|\cdot\|)$ korlátos és zárt (azaz [[concepts/analiii/kompakt-halmazok|kompakt]]) halmaz. Tegyük fel, hogy
- $f \in C(H)$,
- $f \in D(\operatorname{int} H)$.

Ekkor $f$-nek a $H$-n felvett értékei között van legkisebb és legnagyobb függvényérték; ezeket $f$ vagy a $H$ halmaz **határán** (vagyis $H \setminus \operatorname{int} H$ valamely pontjában) veszi fel, vagy pedig egy olyan $a \in \operatorname{int} H$ pontban, ahol $f'(a) = \theta_n$.

**Bizonyítás.** A [[concepts/analiii/weierstrass-tetel-kompakt-halmazon|Weierstrass-tétel]] szerint $\exists \min_H f$ és $\exists \max_H f$: a $H$ kompaktsága és $f$ folytonossága garantálja a létezést. Legyen $a \in H$ olyan pont, ahol $f$ értéke például a legnagyobb. Ha $a \in \operatorname{int} H$, akkor $a$-nak $f$-nek lokális szélsőértékhelye is, ezért a rá vonatkozó elsőrendű [[concepts/analiii/lokalis-szelsoertek-feltetelei|szükséges feltételből]] következik, hogy $f'(a) = \theta_n$. $\blacksquare$

### A gyakorlati recept

1. Számítsd ki $f'$-t, és oldd meg a $\operatorname{grad} f(x) = \theta_n$ egyenletrendszert $\operatorname{int} H$-n — ezek a belső stacionárius pontok.
2. Vizsgáld meg $f$-et a $H \setminus \operatorname{int} H$ határon külön (jellemzően egy paraméterezéssel vagy egyváltozós redukcióval, esetleg [[concepts/analiii/felteteles-szelsoertek|feltételes szélsőérték]] módszerével, ha a határ egy $\{g = 0\}$ alakú feltétellel írható le).
3. Számítsd ki $f$ értékét minden jelölt pontban (belső stacionárius pontok és a határ vizsgált pontjai), és a legnagyobb/legkisebb közülük adja az abszolút maximumot/minimumot.

Fontos, hogy a belső stacionárius pontokban *nem kell* eldönteni, hogy ott lokális szélsőérték van-e (a másodrendű feltételekkel) — elég az összes jelöltet kiszámítani és összehasonlítani, mert a létezést már a Weierstrass-tétel garantálja.

### Feladatok

**Recept kompakt $H$-n, peremparaméterezéssel.** (1) Belső stacionárius pontok: $\operatorname{grad}f=0$ az $\operatorname{int}H$-ban; a $H$-n kívüli vagy peremre eső megoldások nem belső jelöltek. (2) A perem minden darabját paraméterezzük (szakasz: $x$ vagy $y$ konstans; parabola: $(x,x^2)$; egyenes: $(x,x-1)$; kör: $(\cos t,\sin t)$), és az egyváltozós $[\alpha,\beta]$-n vizsgáljuk: belső kritikus pontok + **végpontok (sarokpontok)**. (3) Összevetés: a legnagyobb/legkisebb érték az abszolút szélsőérték; a sarokpontok minden érintett darabhoz tartoznak, de elég egyszer kiszámolni.

**Munkapéldák.**

1. $f=y(2x-3)$ a $y=x^2$, $y=0$, $x=2$ által határolt $A$ halmazon. Belül: $2y=0$, $2x-3=0\Rightarrow(\tfrac32,0)\notin\operatorname{int}A$. Perem: $y=0$ szakaszon $f=0$; $x=2$ szakaszon $f=y$, $y\in[0,4]$; parabolaív: $l(x)=2x^3-3x^2$, $l'=6x(x-1)$, $x=1$ ($x=0$ végpont). Értékek: $f(1,1)=-1$ (abszolút minimum), $f(2,4)=4$ (abszolút maximum).
2. $f=x^3-3x^2-y^2$ az $A=\{x\ge-1,\ x-1\le y\le4\}$ halmazon (korlátos: $x\le5$). Belül: $(0,0)$ belső pont, $(2,0)$ nem. Perem: $x=-1$: $g(y)=-4-y^2$, kritikus $y=0$; $y=4$: $l(x)=x^3-3x^2-16$, kritikus $x=0,2$; $y=x-1$: $h'=3x^2-8x+2=0$, $x=\tfrac{4\pm\sqrt{10}}3$. Jelöltek: $f(0,0)=0$, $f(-1,-2)=-8$, $f(-1,0)=-4$, $f(-1,4)=-20$, $f(0,4)=-16$, $f(2,4)=-20$, $f(5,4)=34$, és a két $y=x-1$ pont értéke a $(-20,34)$ intervallumba esik. Abszolút maximum: $34$ az $(5,4)$-ben; abszolút minimum: $-20$ a $(-1,4)$-ben és a $(2,4)$-ben.
3. $f=xy(x^2+y^2-1)$ a zárt egységkörlapon: $f_x=y(3x^2+y^2-1)$, $f_y=x(x^2+3y^2-1)$. Belső stacionárius: $(0,0)$ és $(\pm\tfrac12,\pm\tfrac12)$, ahol $f=-xy/2$. A kör peremén $f=0$. Maximum: $\tfrac18$ a $(\tfrac12,-\tfrac12)$, $(-\tfrac12,\tfrac12)$ pontokban; minimum: $-\tfrac18$ a $(\tfrac12,\tfrac12)$, $(-\tfrac12,-\tfrac12)$ pontokban.
4. $f=x^3-12x+y^3-3y$ a $H=\{-2\le x\le3,\ -x\le y\le2\}$ háromszögön (csúcsok $(-2,2),(3,2),(3,-3)$). Belső: $x=\pm2$, $y=\pm1$ közül csak $(2,1)$ és $(2,-1)$ belső pont ($f=-18$, $-14$). Peremszakaszok: $y=2$: $x^3-12x+2$ (kritikus $x=2$: $E(2,2)$, $f=-14$); $x=3$: $y^3-3y-9$ (kritikus $y=\pm1$: $D(3,-1)$, $f=-7$; $f(3,2)=-7$); $y=-x$: $-9x$ szigorúan csökkenő, ezért csak a végpontok jönnek szóba. Jelöltértékek: $-14,-18,18,-27,-7,-7,-14$ (gyak 9. lap megoldása szerint). Maximum $18$ a $(-2,2)$-ben, minimum $-27$ a $(3,-3)$-ban.
5. $f=x^3y^5$ az $A(0,0),B(1,0),C(0,1)$ háromszögön: $f\ge0$, a két befogón $f=0$ (minimum), a $BC$ oldalon $x^3(1-x)^5$ deriváltja $x^2(1-x)^4(3-8x)$, így a maximum $x=\tfrac38$-nál, $f=\tfrac{27}{512}\left(\tfrac58\right)^5=\tfrac{84375}{16777216}$ a $(\tfrac38,\tfrac58)$-ben. (Lokálisan nincs szélsőérték, lásd [[concepts/analiii/lokalis-szelsoertek-feltetelei]].)
6. Szöveges feladat: felül nyitott téglatest-tartály, térfogat $4\,\mathrm{m}^3$, legkevesebb anyag. $xyz=4$, $S=xy+2xz+2yz=xy+\tfrac8x+\tfrac8y$; $S_x=y-\tfrac8{x^2}=0$, $S_y=x-\tfrac8{y^2}=0\Rightarrow x=y=2$, $z=1$, $S=12\,\mathrm{m}^2$. A tartomány $A=\{x>0,y>0\}$ nem kompakt, ezért a Weierstrass-tétel közvetlenül nem alkalmazható (gyak 9. lap megoldása szerint): a $P(2,2)$ az egyetlen stacionárius pont, $f''(P)=\begin{bmatrix}2&1\\1&2\end{bmatrix}$ pozitív definit ($D_1=2$, $D_2=3$), lokális minimum, $f(P)=12$. A létezést kompakt részhalmazra való redukcióval kapjuk: $f\le f(P)=12$ csak a $B=\{y<\tfrac{12}x,\ y>\tfrac43,\ x>\tfrac43\}$ halmazban lehet (mert $xy\ge12$, $\tfrac8x\ge12$, ill. $\tfrac8y\ge12$ esetén más tag már magában eléri a határt), $\overline B$ kompakt és $P\in B$, így $\overline B$-n van minimum, ez belső, tehát lokális minimum, vagyis $P$; méretek $2\times2\times1\,\mathrm m$.
7. Súlyozott távolságnégyzet-összeg: $\sum m_i\|x-x_i\|^2$ minimuma ($m_i>0$): a gradiens $2\sum m_i(x-x_i)=0$, így $x=\sum m_ix_i/\sum m_i$ (tömegközéppont), a Hesse-mátrix $2\sum m_i\,I$ pozitív definit.

**Nem kompakt tartomány.** Ha $H$ nem korlátos/zárt, keressünk olyan kompakt $\overline B\subset H$ szintvonal-halmazt ($\{f\le f(P)\}$ a jelölt $P$-re), amely tartalmazza $P$-t; ekkor $\overline B$-n a Weierstrass-tétel adja a minimumot, és az a belsőben, tehát $P$-ben van (6. munkapélda).

**További gyakorló feladatok:** $x^3+y^3-9xy$ az $A=\{0\le x\le5,\ 0\le y\le2x\}$ halmazon; $x^2-y^2-x$ a negyedkörön; $\sin x\sin y\sin z$ háromszög szögeire ($x+y+z=\pi$ feltétellel — maximum $x=y=z=\pi/3$-nál, lásd [[concepts/analiii/felteteles-szelsoertek]]); maximális területű egyenlőszárú trapéz $200\,\mathrm{m}$ kerülettel.

## Kapocs

- [[concepts/analiii/weierstrass-tetel-kompakt-halmazon]] — a létezési fél: kompakt halmazon folytonos függvénynek van abszolút szélsőértéke.
- [[concepts/analiii/lokalis-szelsoertek-feltetelei]] — az elsőrendű szükséges feltétel, amely a belső jelölteket kiválasztja.
- [[concepts/analiii/kompakt-halmazok]] — a korlátos és zárt halmaz fogalma.
- [[concepts/analiii/felteteles-szelsoertek]] — a határvizsgálat egyik eszköze, ha a perem egyenlettel adott.
- [[concepts/analii/abszolut-szelsertekek]] — az egyváltozós eredeti, $[a,b]$ intervallumon.
