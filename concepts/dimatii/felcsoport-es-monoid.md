---
tags: [concept]
sources: [DimatIIEa03.pdf, DimatIIEa04.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, dm2gy06_2020_Algebra.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-21
---

# Félcsoport és monoid

Asszociatív grupoid a félcsoport; ha van benne egységelem is, monoidnak (egységelemes félcsoportnak) nevezzük.

## Tartalom

### Félcsoport

Egy $(G; *)$ grupoid **félcsoport**, ha $*$ asszociatív $G$-n, azaz

$$\forall a, b, c \in G : (a * b) * c = a * (b * c).$$

### Egységelem (semleges elem)

Ha létezik olyan $s \in G$ elem, amire

$$\forall g \in G : s * g = g * s = g,$$

akkor $s$-t **semleges elemnek**, más néven **egységelemnek** nevezzük.

### Monoid

Ha egy $(G; *)$ félcsoportban létezik $s$ semleges elem, akkor $G$-t **egységelemes félcsoportnak**, **semleges elemes félcsoportnak**, más néven **monoidnak** nevezzük.

### Általános asszociativitási törvény

Félcsoportban minden szorzat tetszőlegesen bontható zárójelekkel két részre: $(a_1 \dots a_k)(a_{k+1} \dots a_n) = a_1 a_2 \dots a_n$ minden $1 \le k < n$ esetén.

### Bal és jobb oldali egységelem, inverz

$e_b$ **bal oldali egységelem**, ha $e_b a = a$ minden $a$-ra; $e_j$ **jobb oldali egységelem**, ha $a e_j = a$ minden $a$-ra; $e$ **egységelem**, ha mindkettő. Egységelemre vonatkozóan az $a$ elem $a_b$ **balinverze**: $a_b a = e$, $a_j$ **jobbinverze**: $a a_j = e$, **inverze** $a'$: $aa' = a'a = e$.

**Tétel (egységelem és inverz unicitása).** Félcsoportban legfeljebb egy egységelem létezik, és minden elemnek legfeljebb egy, az egységelemre vonatkozó inverze létezik.
*Bizonyítás.* Ha $e_b$ bal, $e_j$ jobb oldali egységelem, akkor $e_b e_j = e_j$ (mert $e_b$ bal egység) és $e_b e_j = e_b$ (mert $e_j$ jobb egység), így $e_b = e_j$. Ha $a_b$ balinverz és $a_j$ jobbinverz, akkor $a_b a a_j = a_b(aa_j) = a_b e = a_b$ és $a_b a a_j = (a_b a)a_j = e a_j = a_j$, tehát $a_b = a_j$.

**Fontos:** bal oldali egységelemből több is lehet. Példa: $G = \left\{\begin{pmatrix} a & b \\ a & b \end{pmatrix} : a, b \in \mathbb{R}\right\}$ félcsoport a mátrixszorzással, és minden $\begin{pmatrix} x & y \\ x & y \end{pmatrix}$, $x + y = 1$ bal oldali egységelem (végtelen sok van), mert $(x+y)c = c$, $(x+y)d = d$.

### Példák

- $\mathbb{N}$ a $+$ művelettel egységelemes félcsoport, egységeleme $n = 0$.
- $\mathbb{Q}$ a $\cdot$ művelettel egységelemes félcsoport, egységeleme $n = 1$.
- $\mathbb{C}^{k \times k}$ a mátrixszorzással egységelemes félcsoport, egységeleme az egységmátrix.

Monoidban az egységelem meglétén túl nem követeljük meg az inverz létezését — épp ez a lépés visz tovább a [[concepts/dimatii/csoport]] fogalmához.

### Feladattípusok és módszerek (gyakorlati feladatsor, 2020 ősz, 6. sor)

**Típus:** „félcsoport, illetve csoport-e $(H, \circ)$?” Sorrend: művelet-e → asszociatív-e → van-e egységelem → minden elemnek van-e inverze. Az első hibás pontnál megállunk.

- **Asszociativitás cáfolata** egyetlen számpárral: $(\mathbb{Q}, \tfrac{a+b}{2})$ esetén $(0\circ4)\circ8 = 2\circ 8 = 5$, de $0\circ(4\circ8) = 0\circ 6 = 3$, tehát nem félcsoport. Hasonlóan $(\mathbb{R}\setminus\{0\}, \div)$: $(8\div4)\div2 = 1 \ne 8\div(4\div2) = 4$.
- **Maximum-művelet:** a $[0,1]$-en értelmezett valós függvények halmaza a $\max$ művelettel félcsoport (asszociatív, kommutatív), de nem monoid: egységelem olyan $e$ lenne, amelyre $\max(e,f)=f$ minden $f$-re, vagyis $e \le f$ minden függvényre — ilyen függvény nincs. Így csoport sem.
- Az egységelem hiánya is válasz: „félcsoport, de nem monoid”.

## Kapocs

- [[concepts/dimatii/algebrai-struktura]] — a grupoid, amiből a félcsoport specializálódik
- [[concepts/dimatii/muvelet]] — az asszociativitás definíciója
- [[concepts/dimatii/csoport]] — egységelemes félcsoport, amelyben minden elemnek van inverze
- [[concepts/dimatii/gyuru]] — a gyűrű multiplikatív része félcsoport
