---
tags: [concept]
sources: [SimonP-Anal2.pdf, 04_ea_An3_2022_tavasz.pdf, 06_ea_An3_2022_tavasz.pdf]
references: ["Simon Péter: Analízis II., 4.3. szakasz bevezetése"]
derivation: source
updated: 2026-09-14
---

# Magasabb rendű parciális deriváltak

A többszöri differenciálhatóságot nem a derivált deriváltjaként, hanem a **parciális deriváltfüggvények** deriválhatóságával kell definiálni — mert az $\mathbb{R}^n \to \mathbb{R}^{n\times n}$ típusú leképezések deriválását sosem értelmeztük.

## Tartalom

### A definíciós akadály

Egyváltozóban $f''(a) := (f')'(a)$. Több változóban $f \in \mathbb{R}^n \to \mathbb{R}$ esetén $f' = \operatorname{grad} f \in \mathbb{R}^n \to \mathbb{R}^n$, ami még deriválható típus, tehát

$$f''(a) := (\operatorname{grad} f)'(a) \in \mathbb{R}^{n\times n}$$

még értelmes. De **ezen az úton nem lehet továbbmenni**: a harmadik derivált $\mathbb{R}^n \to \mathbb{R}^{n\times n}$ típusú függvény deriváltja lenne, amit nem definiáltunk. Ezért a magasabb rendet a parciális deriváltakra vezetjük vissza.

### Kétszeres differenciálhatóság

Legyen $a \in \operatorname{int} D_f$. Az $f \in \mathbb{R}^n \to \mathbb{R}$ **kétszer differenciálható $a$-ban** ($f \in D^2\{a\}$), ha van olyan $K(a) \subset D_f$ környezet, hogy $f \in D\{x\}$ minden $x \in K(a)$-ra, és

$$\partial_i f \in D\{a\} \qquad (i = 1, \dots, n).$$

Ez a [[concepts/analiii/gradiens-parcialis-derivaltakbol|3.1.2. Tétel]] miatt épp azzal ekvivalens, hogy $\operatorname{grad} f \in D\{a\}$.

### Másodrendű parciális derivált

A fenti feltételből következik, hogy léteznek a

$$\partial_{ij} f(a) := \partial_j(\partial_i f)(a) \qquad (i,j = 1, \dots, n)$$

másodrendű parciális deriváltak. **Fordítva nem igaz**: $\partial_{ij}f(a)$ létezéséhez nem kell, hogy $\partial_i f$ differenciálható legyen $a$-ban — elég, ha a $j$-edik változó szerint parciálisan deriválható. Ez a rés az, ami a [[concepts/analiii/young-tetel|Young-tétel]] ellenpéldáját lehetővé teszi.

Jelölésváltozatok: $\partial_{ij} f = \partial_{x_i x_j} f = \frac{\partial^2 f}{\partial x_i \partial x_j}$.

### Magasabb rend, indukcióval

Ha a $\partial_{i_1 \dots i_s} f$ $s$-edrendű parciális deriváltfüggvény már definiált, és az $a$-ban a $j$-edik változó szerint parciálisan deriválható, akkor

$$\partial_{i_1 \dots i_s j} f(a) := \partial_j(\partial_{i_1\dots i_s} f)(a).$$

Az $f$ **$(s+1)$-szer differenciálható $a$-ban**, ha van olyan $K(a) \subset D_f$, amelyen $f \in D^s\{x\}$ minden pontban, és minden $s$-edrendű parciális deriváltfüggvénye differenciálható $a$-ban.

### Vektorértékű eset és a $C^k$ osztály

Egy $f = (f_1, \dots, f_m) \in \mathbb{R}^n \to \mathbb{R}^m$ függvény **$k$-szor differenciálható** $a$-ban, ha minden $f_j$ koordinátafüggvénye az: $f_j \in D^k\{a\}$. Az $f$ **$k$-szor folytonosan differenciálható** $a$-ban ($f \in C^k\{a\}$), ha egy $K(a) \subset D_f$ környezetben $f \in D^k\{x\}$, és minden koordinátafüggvény minden $k$-adrendű parciális deriváltfüggvénye folytonos $a$-ban.

### Számolási példa

$f(x,y,z) := x^3 + y^2 z + z^3 + xyz$ esetén

$$\partial_{xx} f = 6x,\quad \partial_{xy} f = z,\quad \partial_{xz} f = y,\quad \partial_{yy} f = 2z,\quad \partial_{yz} f = 2y + x,\quad \partial_{zz} f = 6z,$$

harmadrendben pedig például $\partial_{xxx} f = 6$, $\partial_{xyx} f = 0$, $\partial_{xyz} f = 1$.

## Kapocs

- [[concepts/analiii/hesse-matrix]] — a másodrendű parciális deriváltakból álló mátrix.
- [[concepts/analiii/young-tetel]] — mikor cserélhető fel a deriválás sorrendje.
- [[concepts/analiii/gradiens-parcialis-derivaltakbol]] — a $\operatorname{grad} f \in D\{a\} \iff \partial_i f \in D\{a\}$ ekvivalencia.
- [[concepts/analiii/folytonosan-differencialhato-fuggveny]] — a $k = 1$ eset.
- [[concepts/analii/magasabb-rendu-derivaltak]] — az egyváltozós eredeti, ahol nincs definíciós akadály.
