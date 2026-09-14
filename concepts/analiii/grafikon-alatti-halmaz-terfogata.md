---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf, 09_ea_An3_2022_tavasz.pdf]
derivation: source
updated: 2026-09-14
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

## Kapocs

- [[concepts/analiii/jordan-mertek-szerinti-integral]] — az integrál definíciója, amelyet ez a tétel geometriai tartalommal tölt meg
- [[concepts/analiii/also-felso-osszegek-kockazassal]] — a bizonyításban használt $s_n$, $S_n$ összegek
- [[concepts/analiii/jordan-mertek-szeletelessel]] — a fordított irány: a térfogatot szeletek mértékének integráljaként állítja elő
- [[concepts/analiii/szukcessziv-integralas]] — a két grafikon közötti (normál)tartományon vett integrál kiszámítása
- [[concepts/analii/sikido-terulete]] — az egyváltozós tananyag „két görbe közé zárt síkidom területe $\int_a^b (g-f)$" tétele ennek a $p=1$ esete; a többváltozós változat ugyanezt tetszőleges mérhető alaphalmaz fölött mondja ki
