---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf, 10_ea_An3_2022_tavasz.pdf, 11_ea_An3_2022_tavasz.pdf, 11_gyak_An_III_2022_tavasz.pdf, An_III_Gyak_2022_tavasz.pdf]
derivation: source
kind: theorem
element: fire
updated: 2026-10-21
---

# Mérték- és integráltranszformáció

A többváltozós helyettesítéses integrálás tétele: sima, injektív $g$ leképezés mentén a térfogat és az integrál a Jacobi-determináns abszolút értékével transzformálódik.

## Tartalom

### Heurisztika

Legyen $A \in \mathcal{J}_p$ (mérhető halmaz) és $g : A \to \mathbb{R}^p$ elég sima (például folytonosan differenciálható) és injektív. Egy $x \in A$ pont közelében a lineáris közelítés szerint

$$g(w) \approx g(x) + g'(x)(w - x).$$

Ezért egy $x$ körüli kicsi $K$ kocka képe egy körülbelül $\bigl|\det g'(x)\bigr| \cdot t(K)$ térfogatú paralelepipedon. A kis darabokat összeadva azt várjuk, hogy $g(A)$ mérhető, és

$$t(g(A)) = \int_A \bigl|\det g'\bigr|,$$

integrálható $f$ esetén pedig

$$\int_{y \in g(A)} f(y)\,\mathrm{d}y = \int_A f(g(x)) \cdot \bigl|\det g'(x)\bigr|\,\mathrm{d}x.$$

Tömören: a helyettesítés $y = g(x)$, $\mathrm{d}y = \bigl|\det g'(x)\bigr| \cdot \mathrm{d}x$.

### Összehasonlítás az egyváltozós esettel

Az egyváltozós helyettesítéses integrálásban $g : [a,b] \to \mathbb{R}$ szigorúan monoton és folytonosan differenciálható, $f$ pedig integrálható $[g(a), g(b)]$-n.

- Ha $g$ monoton nő, akkor $g' \geqslant 0$, és
  $$\int_{g([a,b])} f(y)\,\mathrm{d}y = \int_{y=g(a)}^{g(b)} f(y)\,\mathrm{d}y = \int_{x=a}^{b} f(g(x)) \cdot g'(x)\,\mathrm{d}x.$$
- Ha $g$ monoton csökken, akkor $g' \leqslant 0$, és a határok cseréje egy előjelváltást hoz be:
  $$\int_{g([a,b])} f(y)\,\mathrm{d}y = -\int_{x=a}^{b} f(g(x)) \cdot g'(x)\,\mathrm{d}x = \int_{x=a}^{b} f(g(x)) \cdot (-g'(x))\,\mathrm{d}x.$$

A két eset **egyetlen** formulába vonható össze, és ez már pontosan a $p = 1$ dimenziós alakja a többváltozós tételnek:

$$\int_{g([a,b])} f(y)\,\mathrm{d}y = \int_{x \in [a,b]} f(g(x)) \cdot \bigl|g'(x)\bigr|\,\mathrm{d}x.$$

Vagyis a $\bigl|\det g'\bigr|$ tényező az egyváltozós $\bigl|g'\bigr|$ általánosítása: az abszolút érték az, ami az irányítás megfordulását elnyeli, és ami miatt a többváltozós formulában a határok cseréje helyett halmazokon integrálunk.

### A tétel

**Tétel (mérték- és integráltranszformáció).** Legyen $G \subset \mathbb{R}^p$ nyílt, $g : G \to \mathbb{R}^p$ folytonosan differenciálható, továbbá $A \in \mathcal{J}_p$ olyan, hogy $\operatorname{cl} A \subset G$, és $g$ injektív az $\operatorname{int} A$ halmazon. Ekkor

- **(a)** $g(A)$ mérhető, és
  $$t(g(A)) = \int_A \bigl|\det g'\bigr|;$$
- **(b)** ha $f : g(A) \to \mathbb{R}$ korlátos, akkor
  $$\int_{y \in g(A)} f(y)\,\mathrm{d}y = \int_{x \in A} f(g(x)) \cdot \bigl|\det g'\bigr|\,\mathrm{d}x,$$
  és ha az egyik integrál létezik, akkor a másik is.

Az előadáson a tétel **bizonyítás nélkül** szerepelt (a bizonyítás az LTS2 anyagában található).

### Alternatív alak: $T = g[H]$ jelöléssel

A (IT) képlet a $T = g[H]$ jelöléssel a következő, gyakran kényelmesebb alakban is írható:

$$\int_T f(\mathbf{x})\,\mathrm{d}\mathbf{x} = \int_H f(g(\mathbf{t})) \cdot \bigl|\det g'(\mathbf{t})\bigr|\,\mathrm{d}\mathbf{t}. \tag{IT1}$$

Az (IT1) alak tetszőleges $g$ helyettesítő függvényre igaz. Az alkalmazáskor kétféle úton lehet elindulni: vagy a $T$ tartományhoz keresünk olyan $g$-t, amely egy egyszerűbb $H$ halmazon (pl. téglalapon) van értelmezve, vagy megfordítva, egy adott $g$-hez próbálunk olyan $f \circ g \cdot |\det g'|$ integrandust találni, amely egyszerűbb, mint $f$ maga.

Két dimenzióban, $(x,y)$ derékszögű és $(u,v)$ helyettesítő koordinátákkal, $g = (g_1, g_2)$ Jacobi-mátrixával az (IT1) képlet az alábbi, kiírt alakot ölti (ITR):

$$\iint_T f(x,y)\,\mathrm{d}x\,\mathrm{d}y = \iint_H f\bigl(g_1(u,v), g_2(u,v)\bigr) \cdot \left|\det\begin{bmatrix}\partial_1 g_1 & \partial_2 g_1 \\ \partial_1 g_2 & \partial_2 g_2\end{bmatrix}(u,v)\right| \mathrm{d}u\,\mathrm{d}v.$$

### Megjegyzések a feltételekhez

- Az injektivitást elég az $\operatorname{int} A$ **belsején** megkövetelni: a határon való átfedés nullmértékű, ezért nem számít. Ez teszi használhatóvá a polárkoordinátás helyettesítést, ahol a $\varphi = 0$ és $\varphi = 2\pi$ élek egymásra képződnek.
- A $\operatorname{cl} A \subset G$ feltétel biztosítja, hogy $g$ és $g'$ még az $A$ határán is értelmes és korlátos legyen.

### Feladatok

**Görbevonalú koordináták a tartomány alakjához igazítva.** Az $xy=1,\ xy=4,\ y=x,\ y=3x$ görbék által határolt első síknegyedbeli tartomány területe *(An III gyak. 11.)*: legyen $u=xy\in[1,4]$, $v=\frac yx\in[1,3]$. Ekkor $\frac{\partial(u,v)}{\partial(x,y)}=\begin{vmatrix}y&x\\-y/x^2&1/x\end{vmatrix}=\frac{2y}{x}=2v$, tehát $\mathrm{d}x\,\mathrm{d}y=\frac{\mathrm{d}u\,\mathrm{d}v}{2v}$ és a terület $\int_1^4\mathrm{d}u\int_1^3\frac{\mathrm{d}v}{2v}=\frac32\ln3$. A gyakorlat a megoldást a *fordított* irányból építi fel: $U=(0,\infty)^2$-n $g(u,v)=\left(\sqrt{u/v},\sqrt{uv}\right)$, $g\in C^1(U)$, $\det g'(u,v)=\frac1{2\sqrt{uv}}\cdot\frac12\sqrt{\frac uv}+\frac12\sqrt{\frac u{v^3}}\cdot\frac12\sqrt{\frac vu}=\frac1{4v}+\frac1{4v}=\frac1{2v}$, $T=g[H]$ a $H=[1,4]\times[1,3]$ téglalapra, és $g$ injektív, inverze $g^{-1}(x,y)=\left(xy,\frac yx\right)$. Az (IT) szerint $t(T)=\iint_H\frac1{2v}\,\mathrm{d}u\,\mathrm{d}v=3\cdot\frac12\ln3=\frac{3\ln3}2$ — ugyanaz az eredmény. Tanulság: a helyettesítő függvényt az integrandushoz és/vagy a tartományhoz „illeszkedően” kell megválasztani. *(11. gyak. 4. feladat)* Az $xy=1,\ xy=4,\ y^2=x,\ y^2=4x$ változatnál $u=xy$, $v=\frac{y^2}{x}$ a megfelelő választás. A transzformációt a tartomány határgörbéi sugallják: minden határgörbe egy koordináta konstans értéke legyen. Lásd még [[concepts/analiii/polarkoordinatas-helyettesites]].

## Kapocs

- [[concepts/analii/hatarozott-integral-helyettesites]] — az egyváltozós helyettesítéses integrálás; a mostani tétel ennek a többváltozós általánosítása, ahol $g'$ helyére $\bigl|\det g'\bigr|$ lép, és az irányított határok helyére halmazok.
- [[concepts/analiii/polarkoordinatas-helyettesites]] — a tétel legfontosabb konkrét alkalmazása.
- [[concepts/analiii/hengerkoordinatas-helyettesites]] — térbeli alkalmazás: a polárkoordináták a $z$ tengellyel kiegészítve.
- [[concepts/analiii/gombi-koordinatas-helyettesites]] — másik térbeli alkalmazás, origó körüli gömbszimmetriára.
- [[concepts/analiii/gauss-integral]] — a transzformációs tétel egy nevezetes következménye.
- [[concepts/analiii/szorzathalmaz-merteke-es-integralja]] — a szorzathalmazok mértéke és a szorzatfüggvények integrálja.
- [[concepts/analiii/vizsgakerdesek-es-bizonyitando-tetelek]] — a témához tartozó megajánlott vizsgajegy- és röpdolgozat-kérdések.
