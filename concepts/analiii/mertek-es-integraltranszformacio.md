---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
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

### Megjegyzések a feltételekhez

- Az injektivitást elég az $\operatorname{int} A$ **belsején** megkövetelni: a határon való átfedés nullmértékű, ezért nem számít. Ez teszi használhatóvá a polárkoordinátás helyettesítést, ahol a $\varphi = 0$ és $\varphi = 2\pi$ élek egymásra képződnek.
- A $\operatorname{cl} A \subset G$ feltétel biztosítja, hogy $g$ és $g'$ még az $A$ határán is értelmes és korlátos legyen.

## Kapocs

- [[concepts/analii/hatarozott-integral-helyettesites]] — az egyváltozós helyettesítéses integrálás; a mostani tétel ennek a többváltozós általánosítása, ahol $g'$ helyére $\bigl|\det g'\bigr|$ lép, és az irányított határok helyére halmazok.
- [[concepts/analiii/polarkoordinatas-helyettesites]] — a tétel legfontosabb konkrét alkalmazása.
- [[concepts/analiii/gauss-integral]] — a transzformációs tétel egy nevezetes következménye.
- [[concepts/analiii/szorzathalmaz-merteke-es-integralja]] — a szorzathalmazok mértéke és a szorzatfüggvények integrálja.
