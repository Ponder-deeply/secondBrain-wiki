---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Rotációmentes vektormező

Differenciálható vektormezőre a primitív függvény létezésének szükséges feltétele, hogy a keresztbe vett parciális deriváltak megegyezzenek, azaz a Jacobi-mátrix mindenütt szimmetrikus legyen. A feltétel nem elégséges.

## Tartalom

### A szükséges feltétel

**Trivialitás.** Legyen $G \subset \mathbb{R}^p$ összefüggő, nyílt, $f : G \to \mathbb{R}^p$ **differenciálható**. Ahhoz, hogy $f$-nek létezzen primitív függvénye, szükséges, hogy bármely $1 \leqslant i,j \leqslant p$ esetén

$$D_i f_j = D_j f_i$$

teljesüljön $G$ minden pontjában. Ugyanez más szavakkal:

- a $J_f(x)$ Jacobi-mátrix minden $x$ pontban **szimmetrikus**;
- az $f$ **keresztbe vett parciális deriváltjai** megegyeznek;
- az $f$ vektormező **rotációmentes**.

A rotáció fogalmát később vezetjük be általánosan; a két legfontosabb eset:

- két dimenzióban $\operatorname{rot} f = D_1 f_2 - D_2 f_1$ (egy szám);
- három dimenzióban
$$\operatorname{rot} f = \begin{pmatrix} D_2 f_3 - D_3 f_2 \\ D_3 f_1 - D_1 f_3 \\ D_1 f_2 - D_2 f_1\end{pmatrix}.$$

**Bizonyítás.** Ha $f$ differenciálható és $F$ primitív függvénye $f$-nek, akkor $F$ már kétszer differenciálható, és az $f$ Jacobi-mátrixa éppen az $F$ **Hesse-mátrixa**:

$$J_f = \begin{pmatrix} D_1 f_1 & \dots & D_p f_1 \\ \vdots & \ddots & \vdots \\ D_1 f_p & \dots & D_p f_p \end{pmatrix} = \begin{pmatrix} D_1 D_1 F & \dots & D_p D_1 F \\ \vdots & \ddots & \vdots \\ D_1 D_p F & \dots & D_p D_p F \end{pmatrix} = H_F.$$

**Tétel (Young).** Ha $f(x,y)$ kétszer differenciálható az $(a,b)$ pontban, akkor $D_x D_y f(a,b) = D_y D_x f(a,b)$.

A Young-tétel szerint tehát a Hesse-mátrix szimmetrikus, és vele $J_f$ is.

### A feltétel nem elégséges — a kilyukasztott sík

**Példa.** Az

$$f(x,y) = \left(\frac{-y}{x^2+y^2};\ \frac{x}{x^2+y^2}\right)$$

vektormező az $\mathbb{R}^2 \setminus \{(0,0)\}$ tartományon rotációmentes, de **nincs** primitív függvénye.

*Bizonyítás.* Egyrészt közvetlen deriválással

$$D_1 f_2 = D_2 f_1 = \frac{-x^2+y^2}{(x^2+y^2)^2},$$

tehát $f$ valóban rotációmentes. Másrészt számítsuk ki a vonalintegrálját az egységkörvonalon, a $\gamma(t) = (\cos t, \sin t)$, $t \in [0,2\pi]$ paraméterezéssel. Itt $f(\gamma(t)) = (-\sin t, \cos t)$ és $\dot\gamma(t) = (-\sin t, \cos t)$, tehát

$$\int_\gamma \bigl\langle f(x); \mathrm{d}x\bigr\rangle = \int_{t=0}^{2\pi}\bigl\langle(-\sin t,\cos t); (-\sin t,\cos t)\bigr\rangle\,\mathrm{d}t = \int_0^{2\pi} 1\,\mathrm{d}t = 2\pi \neq 0.$$

Van tehát olyan zárt görbe, amelyen a vonalintegrál nem nulla; a konzervativitás ekvivalenciatétele szerint nincs primitív függvény.

### Lokálisan van primitív függvény

Ugyanennek az $f$-nek **lokálisan** van primitív függvénye. Bármilyen origó csúcsú szögtartományban definiálható egy „irány" vagy „szög" függvény, amelynek gradiense éppen $f$. Ha a síkból elhagyunk egy origóból induló zárt félegyenest, a megmaradt nyílt tartományban értelmezhető az $x$-tengely és az origóból az $(x,y)$ pontba mutató szakasz közötti irányított szög; az egyes félsíkokkal vett metszetekben

$$\operatorname{sz\ddot{o}g}(x,y) = \operatorname{arctg}\frac{y}{x} + C_1 = -\operatorname{arctg}\frac{x}{y} + C_2$$

alkalmas $C_1, C_2$ konstansokkal. Ennek parciális deriváltjai

$$D_x \operatorname{sz\ddot{o}g} = \frac{-\frac{y}{x^2}}{1+\left(\frac{y}{x}\right)^2} = \frac{-y}{x^2+y^2}, \qquad D_y \operatorname{sz\ddot{o}g} = \frac{\frac{1}{x}}{1+\left(\frac{y}{x}\right)^2} = \frac{x}{x^2+y^2},$$

vagyis pontosan $f$. A teljes kilyukasztott síkon viszont a „szög" függvénynek nincs folytonos kiterjesztése: körbejárva $2\pi$-vel ugrik — és ez az ugrás az, ami a $2\pi$ vonalintegrálként megjelenik.

Ez a példa mutatja meg élesen, hogy a primitív függvény létezése nemcsak $f$-en, hanem a **tartomány alakján** is múlik: a rotációmentesség lokális feltétel, a primitív függvény létezése globális kérdés. A hiányzó plusz feltétel a tartomány topológiája lesz.

## Kapocs

- [[concepts/analiii/vektormezo-primitiv-fuggvenye]] — a keresett objektum; a rotációmentesség ennek létezéséhez szükséges.
- [[concepts/analiii/konzervativ-vektormezo]] — az ellenpélda ennek a tételnek a zárt görbés kritériumát használja.
- [[concepts/analiii/goursat-lemma]] — az az eszköz, amellyel a rotációmentesség jó tartományokon elégségessé válik.
- [[concepts/analiii/primitiv-fuggveny-csillagszeru-tartomanyon]] — konvex és csillagszerű tartományokon a feltétel már elégséges is.
- [[concepts/analiii/egyszeresen-osszefuggo-tartomany]] — a végleges topológiai feltétel; a kilyukasztott sík éppen ezt sérti.
