---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf, 09_ea_An3_2022_tavasz.pdf, An_III_Gyak_2022_tavasz.pdf, 11_gyak_An_III_2022_tavasz.pdf]
derivation: source
kind: theorem
element: water
updated: 2026-10-21
---

# Az integrál mint a grafikon alatti halmaz térfogata

Egy halmaz Jordan-mértéke megegyezik a karakterisztikus függvényének integráljával, egy nemnegatív integrálható függvény integrálja pedig a grafikonja alatti $(p+1)$-dimenziós halmaz térfogatával — ezzel a mérték és az integrál fogalma összezárul.

## Tartalom

### A karakterisztikus függvény integrálja

**Tétel.** Ha $B \subset A \subset \mathbb{R}^p$ mérhetők, akkor

$$\int_A \chi_B = t^p(B).$$

Ez teszi a mértéket az integrál speciális esetévé: minden térfogatszámítás felírható integrálként.

### A grafikon alatti tartomány

**Tétel.** Legyen $A \in \mathcal{J}_p$, $f : A \to [0,\infty)$ integrálható, és

$$U = \{(x_1,\dots,x_p,y) : (x_1,\dots,x_p)\in A,\ 0 < y < f(x)\},$$
$$V = \{(x_1,\dots,x_p,y) : (x_1,\dots,x_p)\in A,\ 0 \leq y \leq f(x)\}.$$

Ekkor $U$ és $V$ is mérhető $(p+1)$ dimenzióban, és

$$t^{p+1}(U) = t^{p+1}(V) = \int_A f.$$

**Bizonyítás.** Legyen $M = \sup f$, és minden $n$-re $B_n$, illetve $F_n$ az $A$ belső, illetve fedő kockáinak uniója. A kockázásos alsó és felső összegekkel

$$k^{p+1}(V) \leq \sum_{K \text{ fedő kocka}} t^p(K)\sup_K f \leq S_n(f,A) + t(F_n\setminus A)\cdot M,$$

$$b^{p+1}(V) \geq \sum_{K \text{ belső kocka}} t^p(K)\inf_K f \geq s_n(f,A) - t(A\setminus B_n)\cdot M.$$

Mivel $A$ mérhető, $t(F_n\setminus A) \to 0$ és $t(A\setminus B_n) \to 0$, így az $n\to\infty$ határátmenetből

$$\int_A f = \underline{\int}_A f \leq b^{p+1}(V) \leq k^{p+1}(V) \leq \overline{\int}_A f = \int_A f,$$

tehát $V$ mérhető és $t^{p+1}(V) = \int_A f$. $\square$

### Két grafikon közötti tartomány

**Tétel.** Ha $A \in \mathcal{J}_p$, $f, g : A \to \mathbb{R}$ integrálhatók és $f \leq g$, akkor

$$V = \{(x_1,\dots,x_p,y) : (x_1,\dots,x_p)\in A,\ f(x)\leq y\leq g(x)\}$$

mérhető $(p+1)$ dimenzióban, és

$$t^{p+1}(V) = \int_A (g-f).$$

**Bizonyítás.** Legyen $f, g \geq -M$; alkalmazzuk az előző tételt az $f+M$ és $g+M$ nemnegatív függvényekre, és vonjuk ki egymásból a két térfogatot. $\square$

### Feladatok

**Terület és térfogat kettős integrállal.** Egy korlátos $H\subset\mathbb{R}^2$-nek *van területe* (Jordan-mérhető), ha az $f\equiv1$ függvény integrálható $H$-n, és $t(H)=\iint_H1\,\mathrm{d}x\,\mathrm{d}y$. Ha $f\ge0$ korlátos, akkor a $T=\{(x,y,z):(x,y)\in H,\ 0\le z\le f(x,y)\}$ „térrésznek” van térfogata, ha $f\in R(H)$, és $V(T)=\iint_Hf$. A test egy síkbeli tartomány felett a két határoló felület különbségének integrálja; a lépések: (1) ábra, (2) a vetület $H$ meghatározása a felületek metszetéből vagy az $f\ge0$ feltételből, (3) integrandus, (4) szükség szerint polárkoordináták. *(An III gyak. 11.; 11. gyak. 3–8. oldal)*

- A $z=1-x^2-y^2$ forgásparaboloid és az $xy$ sík közötti rész: $z\ge0\iff x^2+y^2\le1$, így $H=D=\{x^2+y^2\le1\}$, és polárisan $H'=[0,1]\times[0,2\pi]$-n $\iint(1-r^2)r\,\mathrm{d}r\,\mathrm{d}\varphi=\left[\frac{r^2}2-\frac{r^4}4\right]_0^1\cdot2\pi=\frac\pi2$.
- $z=5-x^2-y^2$ és $z=1$ között: a vetület $r\le2$, $V=2\pi\int_0^2(4-r^2)r\,\mathrm{d}r=8\pi$.
- Az $x^2+y^2=1$ henger, a $z=0$ sík és a $z=x+2y+3$ sík által határolt test: a síkidom a $D=\{x^2+y^2\le1\}$ körlap fölött van, mert itt $x,y\ge-1$ miatt $z=x+2y+3\ge-1-2+3=0$. Polárisan $\int_0^1\left(\int_0^{2\pi}(r\cos\varphi+2r\sin\varphi+3)r\,\mathrm{d}\varphi\right)\mathrm{d}r=\int_0^16\pi r\,\mathrm{d}r=3\pi$ (a páratlan tagok kiesnek). *(11. gyak. 6. feladat)*
- A $z=x^2+y^2-1$ paraboloid és a $z=2$, $z=5$ síkok között: a $z$-szintű keresztmetszet kör, $r^2=z+1$, területe $\pi(z+1)$, így $V=\pi\int_2^5(z+1)\,\mathrm{d}z=\frac{27\pi}2$ (szeletelés, lásd [[concepts/analiii/jordan-mertek-szeletelessel]]).
- Viviani-test: a $x^2+y^2+z^2=R^2$ gömb és az $x^2-Rx+y^2=0$ henger (sugara $R/2$) közös része. Szimmetria miatt $V=2\iint_D\sqrt{R^2-x^2-y^2}$ a $D$ körlapon, polárisan $0\le r\le R\cos\varphi$: $V=\frac{2R^3}3\int_{-\pi/2}^{\pi/2}(1-|\sin\varphi|^3)\mathrm{d}\varphi=\frac{2R^3}{3}\left(\pi-\frac43\right)=\frac{2R^3(3\pi-4)}9$. *(An III gyak. 12.)*

## Kapocs

- [[concepts/analiii/jordan-mertek-szerinti-integral]] — az integrál definíciója, amelyet ez a tétel geometriai tartalommal tölt meg
- [[concepts/analiii/also-felso-osszegek-kockazassal]] — a bizonyításban használt $s_n$, $S_n$ összegek
- [[concepts/analiii/jordan-mertek-szeletelessel]] — a fordított irány: a térfogatot szeletek mértékének integráljaként állítja elő
- [[concepts/analiii/szukcessziv-integralas]] — a két grafikon közötti (normál)tartományon vett integrál kiszámítása
- [[concepts/analii/sikido-terulete]] — az egyváltozós tananyag „két görbe közé zárt síkidom területe $\int_a^b (g-f)$" tétele ennek a $p=1$ esete; a többváltozós változat ugyanezt tetszőleges mérhető alaphalmaz fölött mondja ki
- [[concepts/analiii/vizsgakerdesek-es-bizonyitando-tetelek]] — a témához tartozó megajánlott vizsgajegy- és röpdolgozat-kérdések.
