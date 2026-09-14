---
tags: [concept]
sources: [SimonP-Anal2.pdf, 05_ea_An3_2022_tavasz.pdf]
references: ["Simon Péter: Analízis II., 4.1.1–4.1.3. Tétel, 4.2. viii)–ix), xii) megjegyzés"]
derivation: source
updated: 2026-09-14
---

# Differenciálási szabályok több változóban

Az összeg, a szorzat és a hányados deriválási szabálya szó szerint átvihető az $\mathbb{R}^n \to \mathbb{R}^m$ függvényekre; a szorzat- és a hányadosszabály csak skalárértékű ($m = 1$) függvényekre mondható ki, és a derivált helyén a gradiens áll.

## Tartalom

### Linearitás

Ha $f, g \in \mathbb{R}^n \to \mathbb{R}^m$ és $f, g \in D\{a\}$, akkor tetszőleges $c \in \mathbb{R}$ mellett $f + cg \in D\{a\}$, és

$$(f + cg)'(a) = f'(a) + cg'(a).$$

A bizonyítás mintája az egész szakaszra jellemző: a differenciálhatóság $f(a+x) - f(a) = f'(a)x + \eta(x)\|x\|$ alakját írjuk fel mindkét függvényre, összeadjuk, és a keletkező $\varphi := \eta + c\tilde\eta$ hibatagra $\|\varphi(x)\| \le \|\eta(x)\| + |c|\,\|\tilde\eta(x)\| \to 0$. Előbb azonban azt kell ellenőrizni, hogy $a$ **belső pontja** az értelmezési tartományok metszetének: az $r, \delta$ sugarak minimumával $K_\nu(a) \subset D_f \cap D_g$.

### Szorzat

Ha $f, g \in \mathbb{R}^n \to \mathbb{R}$ és $f, g \in D\{a\}$, akkor $fg \in D\{a\}$, és

$$\operatorname{grad}(fg)(a) = g(a)\cdot \operatorname{grad} f(a) + f(a)\cdot \operatorname{grad} g(a).$$

### Hányados

Ha ezen felül $g(a) \ne 0$, akkor $f/g \in D\{a\}$, és

$$\operatorname{grad}\!\left(\frac{f}{g}\right)(a) = \frac{g(a)\cdot \operatorname{grad} f(a) - f(a)\cdot \operatorname{grad} g(a)}{g^2(a)}.$$

A bizonyítás két lépésre bomlik. Először a $g$ folytonosságából ($D\{a\} \Rightarrow C\{a\}$) következik, hogy $\nu$ szűkítésével $g(x) \ne 0$ az egész $K_\nu(a)$-n, tehát $a \in \operatorname{int} D_{f/g}$. Utána elég az $1/g$ esetet elintézni,

$$\left(\frac{1}{g}\right)'(a) = -\frac{\operatorname{grad} g(a)}{g^2(a)},$$

innen a szorzatszabály és $f/g = f\cdot(1/g)$ adja az állítást.

### A kényelmes út: mindkettő a láncszabály következménye

A szorzat- és a hányadosszabály önálló bizonyítás nélkül is megkapható. Legyen $F(x,y) := xy$, illetve $F(x,y) := x/y$, és $G(t) := (f(t), g(t))$. Ekkor $\operatorname{grad} F(x,y) = (y, x)$, illetve $(1/y, -x/y^2)$, továbbá

$$G'(a) = \begin{bmatrix} \operatorname{grad} f(a) \\ \operatorname{grad} g(a)\end{bmatrix} \in \mathbb{R}^{2 \times n},$$

és $F \circ G = fg$, illetve $F \circ G = f/g$. A [[concepts/analiii/lancszabaly|láncszabály]] mátrixszorzata pontosan a fenti két képletet szolgáltatja. Ez a levezetés mutatja meg, hogy a két szabály nem külön csoda, hanem ugyanannak az egy tételnek a két speciális esete.

### Mátrixszal való szorzás

Ha $f \in \mathbb{R}^n \to \mathbb{R}^m$, $f \in D\{a\}$ és $A \in \mathbb{R}^{s \times m}$ rögzített mátrix, akkor az $F(x) := Af(x)$ függvényre $F \in D\{a\}$ és

$$F'(a) = A f'(a).$$

Az indoklás a mátrixnorma szubmultiplikativitása: $\|A\eta(h)\|_\bullet \le \|A\|_{(\bullet,*)}\|\eta(h)\|_* \to 0$. Speciális esetként a [[concepts/analiii/koordinatafuggvenyek-differencialhatosaga|koordinátafüggvények]] deriváltjait kapjuk, ha $A$ egy sorvektor.

### Polinom- és racionális törtfüggvények

A fenti szabályok azonnali következménye, hogy két nagy függvényosztály mindig — feltétel-ellenőrzés nélkül — differenciálható.

Egy $P \colon \mathbb{R}^n \to \mathbb{R}$ függvény **$n$-változós polinomfüggvény**, ha véges sok tagú összeg alakjában írható:

$$P(x) := \sum_{i_1,\dots,i_n} a_{i_1\dots i_n}\, x_1^{i_1}\cdots x_n^{i_n} \qquad (x \in \mathbb{R}^n),$$

ahol az $a_{i_1\dots i_n}$ együtthatók valósak és a kitevők nemnegatív egészek. Ha $P, Q$ két $n$-változós polinom és $A := \{x \in \mathbb{R}^n \mid Q(x) = 0\}$, akkor az $R(x) := P(x)/Q(x)$ ($x \in \mathbb{R}^n \setminus A$) függvény **$n$-változós racionális törtfüggvény**.

**Tétel.**
1. Az $n$-változós polinomfüggvények mindenütt differenciálhatóak.
2. Az $n$-változós racionális törtfüggvények differenciálhatóak az értelmezési tartományuk minden pontjában.

*Bizonyítás.* Egy $P$ polinom minden parciálisderivált-függvénye maga is polinom (a hatványfüggvény tagonkénti deriválásával), tehát mindenütt folytonos. A [[concepts/analiii/differencialhatosag-elegseges-feltetele|differenciálhatóság elégséges feltétele]] szerint innen $P \in D$ következik. Egy $R = P/Q$ racionális törtfüggvény parciálisderivált-függvényei — a hányadosszabály miatt — szintén racionális törtfüggvények, ezért folytonosak $R$ értelmezési tartományának minden pontjában; ugyanaz az elégséges feltétel adja $R \in D$-t az egész értelmezési tartományon. $\square$

Ez azt jelenti, hogy a gyakorlatban előforduló elemi (polinomokból és hányadosaikból felépülő) többváltozós függvények differenciálhatósága sosem igényel külön ellenőrzést — csak azt kell tudni, hogy a függvény ilyen alakú.

### Hogyan általánosít az egyváltozós esethez képest

Az [[concepts/analii/derivalasi-szabalyok]] alakja formálisan változatlan, de két új dolog történik:

- a szorzat- és a hányadosszabály **csak skalárértékű** függvényekre értelmes, hiszen $\mathbb{R}^m$-beli értékeket nem tudunk összeszorozni;
- a szorzás sorrendje a láncszabálynál már **nem cserélhető fel** — ott mátrixszorzat áll.

## Kapocs

- [[concepts/analiii/lancszabaly]] — a szakasz negyedik és legfontosabb szabálya, amelyből a szorzat és a hányados is levezethető.
- [[concepts/analiii/frechet-derivalt]] — a differenciálhatóság definíciója, amelyet minden bizonyítás felír.
- [[concepts/analiii/jacobi-matrix]] — a derivált mátrixalakja, amelyben a szabályok érvényesek.
- [[concepts/analiii/gradiens-parcialis-derivaltakbol]] — a $\operatorname{grad}$ jelölés tartalma.
- [[concepts/analii/derivalasi-szabalyok]] — az egyváltozós eredeti.
