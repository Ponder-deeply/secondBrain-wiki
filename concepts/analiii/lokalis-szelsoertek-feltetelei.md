---
tags: [concept]
sources: [SimonP-Anal2.pdf, 07_ea_An3_2022_tavasz.pdf]
references: ["Simon Péter: Analízis II., 4.5.1.1–4.5.1.3. Tétel"]
derivation: source
updated: 2026-09-14
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

## Kapocs

- [[concepts/analiii/tobbvaltozos-taylor-formula]] — mindhárom bizonyítás forrása.
- [[concepts/analiii/kvadratikus-alak-definitsege]] — a döntési kritérium.
- [[concepts/analiii/hesse-matrix]] — a vizsgálandó mátrix.
- [[concepts/analiii/felteteles-szelsoertek]] — ugyanez korlátozó feltételekkel.
- [[concepts/analiii/abszolut-szelsoertek]] — ugyanez a szükséges feltétel, korlátos zárt halmazon a globális szélsőérték keresésének első lépéseként.
- [[concepts/analii/lokalis-szelsertekek]] — az egyváltozós eredeti.
