---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 4.4. iv)–vii), xv) megjegyzés"]
derivation: source
updated: 2026-09-07
---

# Kvadratikus alak definitsége

A szimmetrikus $A \in \mathbb{R}^{n\times n}$ mátrixhoz tartozó $Q(x) = \langle Ax, x\rangle$ alak öt kategóriába sorolható; a besorolás eldönthető az egységgömbön felvett minimumból és maximumból, vagy algebrailag a Sylvester-kritériummal.

## Tartalom

### Kvadratikus alak

Legyen $A = (a_{ik}) \in \mathbb{R}^{n\times n}$ szimmetrikus. Az

$$Q(x) := \langle Ax, x\rangle = \sum_{i=1}^n\sum_{k=1}^n a_{ik}x_i x_k \qquad (x \in \mathbb{R}^n)$$

leképezés az $A$ által meghatározott **kvadratikus alak**. $n = 2$-ben $A = \begin{bmatrix} a & b\\ b& c\end{bmatrix}$ mellett $Q(u,v) = au^2 + 2buv + cv^2$.

Minden kvadratikus alak **folytonos** (sőt differenciálható): $|Q(x) - Q(y)| \le q(1 + 2\|y\|)\|x-y\|$ az $x \in K_1(y)$ pontokra, ahol $q := \|A\|_{(2)}$.

### Az öt kategória

- **pozitív definit:** $Q(x) > 0$ minden $x \ne 0$-ra;
- **negatív definit:** $Q(x) < 0$ minden $x \ne 0$-ra;
- **pozitív szemidefinit:** $Q(x) \ge 0$ minden $x$-re;
- **negatív szemidefinit:** $Q(x) \le 0$ minden $x$-re;
- **indefinit:** van $x, y$, amelyekre $Q(y) < 0 < Q(x)$.

Minden definit alak szemidefinit is. Egy szemidefinit alak pontosan akkor nem definit, ha van olyan $x \ne 0$, amelyre $Q(x) = 0$.

### Homogenitás: elég az egységgömbön nézni

$Q(x) = \|x\|^2 Q(x/\|x\|)$, ezért az előjel vizsgálatához elég a $G := \{x : \|x\| = 1\}$ halmazra szorítkozni. $G$ korlátos és zárt, tehát [[concepts/analiii/heine-borel-tetel|kompakt]], és $Q$ folytonos, így $Q[G]$-nek van $m$ minimuma és $M$ maximuma. Ezekkel

$$m\|x\|^2 \le Q(x) \le M\|x\|^2 \qquad (x \in \mathbb{R}^n),$$

és a besorolás:

| kategória | feltétel |
|---|---|
| pozitív definit | $m > 0$ |
| negatív definit | $M < 0$ |
| pozitív szemidefinit | $m \ge 0$ |
| negatív szemidefinit | $M \le 0$ |
| indefinit | $mM < 0$ |

**Az $m\|x\|^2 \le Q(x)$ becslés a lényeg:** pozitív definit esetben egy *egyenletes* alsó korlát áll rendelkezésre, és ez az, ami a [[concepts/analiii/lokalis-szelsoertek-feltetelei|szélsőérték elégséges feltételében]] legyőzi a Taylor-formula $\eta(h)\|h\|^2$ hibatagját.

### Sylvester-kritérium

Legyen $d_i := \det (a_{jk})_{j,k=1}^i$ a bal felső sarokdetermináns. Ekkor

1. $Q$ pozitív definit $\iff$ $d_i > 0$ minden $i$-re;
2. $Q$ negatív definit $\iff$ $(-1)^j d_j > 0$ minden $j$-re (azaz az előjelek váltakoznak, $d_1 < 0$-tól kezdve).

$n = 2$-ben $d_1 = a$, $d_2 = ac - b^2$, tehát

$$Q \text{ pozitív definit} \iff a > 0 \text{ és } ac > b^2, \qquad Q \text{ negatív definit} \iff a < 0 \text{ és } ac > b^2,$$

sőt

$$Q \text{ indefinit} \iff ac < b^2.$$

**Elemi bizonyítás $n = 2$-re.** $Q(u,v) = v^2 P(u/v)$, ahol $P(u) := au^2 + 2bu + c$. Egy másodfokú polinom akkor és csak akkor tartja meg az előjelét, ha diszkriminánsa $4(b^2 - ac)$ negatív; ha pozitív, két különböző valós gyöke van, és a gyökök közötti, illetve azokon kívüli helyettesítési értékek ellentétes előjelűek — épp az indefinitség.

### Példa

$Q(u,v) := 2u^2 + 2uv - v^2$, azaz $A = \begin{bmatrix} 2 & 1\\ 1 & -1\end{bmatrix}$. Itt $ac - b^2 = -2 - 1 = -3 < 0$, tehát indefinit; közvetlenül is: $Q(0,1) = -1 < 0 < 2 = Q(1,0)$.

## Kapocs

- [[concepts/analiii/hesse-matrix]] — az a szimmetrikus mátrix, amelyre ezt alkalmazzuk.
- [[concepts/analiii/lokalis-szelsoertek-feltetelei]] — a definitség itt dönt.
- [[concepts/analiii/felteteles-szelsoertek-masodrendu-feltetelei]] — a feltételes változat, ahol a definitséget egy altérre szorítjuk.
- [[concepts/analiii/heine-borel-tetel]] — az egységgömb kompaktsága.
- [[concepts/analiii/kompakt-halmazok]] — a szélsőérték-létezés forrása.
