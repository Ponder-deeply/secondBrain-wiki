---
tags: [concept]
sources: [DimatIIEa04.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, dm2gy06_2020_Algebra.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-21
---

# Gyűrű

Kétműveletes algebrai struktúra, amelyben az „összeadás" Abel-csoport, a „szorzás" félcsoport, és a kettőt a disztributivitás köti össze.

## Tartalom

### Disztributivitás

Legyen $(R; \oplus, \otimes)$ algebrai struktúra, ahol $\oplus$ és $\otimes$ bináris műveletek. A $\otimes$ művelet **bal oldali disztributivitása** a $\oplus$-ra, illetve **jobb oldali disztributivitása**:

$$\forall k, l, m \in R : k \otimes (l \oplus m) = (k \otimes l) \oplus (k \otimes m),$$
$$\forall k, l, m \in R : (l \oplus m) \otimes k = (l \otimes k) \oplus (m \otimes k).$$

$(\mathbb{Z}; +, \cdot)$ esetén mindkét oldali disztributivitás teljesül.

### Szokásos elnevezések

$(R; \oplus, \otimes)$ esetén a $\oplus$ műveletet „összeadásnak", a $\otimes$-t „szorzásnak" nevezzük. A $\oplus$-ra vonatkozó semleges elem a **nullelem** (jelölése $0$), a $\otimes$-ra vonatkozó semleges elem az **egységelem** (jelölése $1$, esetleg $e$).

### Definíció (gyűrű)

Az $(R; \oplus, \otimes)$ két bináris műveletes algebrai struktúra **gyűrű**, ha

- $(R; \oplus)$ Abel-csoport (kommutatív csoport a $0$ egységelemmel);
- $(R; \otimes)$ félcsoport;
- teljesül a $\otimes$-nak a $\oplus$-ra vonatkozó **mindkét oldali** disztributivitása.

A gyűrű $0$ nulleleme tehát az $(R; \oplus)$ Abel-csoport egységeleme.

### Egységelemes és kommutatív gyűrű

- Az $(R; \oplus, \otimes)$ gyűrű **egységelemes gyűrű**, ha $R$-en a $\otimes$ műveletre nézve is van egységelem ($1$ vagy $e$), azaz $(R; \otimes)$ egységelemes félcsoport.
- Az $(R; \oplus, \otimes)$ gyűrű **kommutatív gyűrű**, ha a $\otimes$ művelet kommutatív, azaz $(R; \otimes)$ kommutatív félcsoport.

### Példák

- $(\mathbb{Z}; +, \cdot)$ egységelemes kommutatív gyűrű.
- $(2\mathbb{Z}; +, \cdot)$ kommutatív gyűrű, de **nem** egységelemes.
- $\mathbb{Q}$, $\mathbb{R}$, $\mathbb{C}$ a szokásos műveletekkel egységelemes kommutatív gyűrűk.
- $(\mathbb{C}^{k \times k}; +, \cdot)$ a mátrixösszeadással és mátrixszorzással egységelemes gyűrű, de $k > 1$ esetén **nem** kommutatív.
- $(\mathbb{R}^3; +, \times)$, a 3-dimenziós euklideszi vektortér a vektoriális szorzattal **nem** gyűrű, mert $\times$ nem asszociatív; $(\mathbb{R}^3; \times)$ így nem félcsoport.

### Az osztás hiánya

Gyűrűben általában nem lehet elvégezni az osztást:

- $\mathbb{Z}$-ben nem oldható meg a $2x = 1$ egyenlet;
- $\mathbb{R}^{2 \times 2}$-ben nem oldható meg a $\begin{pmatrix} 1 & 0 \\ 0 & 0 \end{pmatrix} \cdot X = \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}$ egyenlet;
- $\mathbb{Z}_4$-ben nem oldható meg a $2x \equiv 1 \pmod 4$ kongruencia.

### Állítás (a nullelem elnyelő)

Legyen $(R; \oplus, \otimes)$ gyűrű $0 \in R$ nullelemmel. Ekkor $\forall r \in R$ esetén

$$0 \otimes r = r \otimes 0 = 0.$$

**Bizonyítás.** $0 \otimes r = (0 \oplus 0) \otimes r = (0 \otimes r) \oplus (0 \otimes r)$, ahonnan $(R; \oplus)$ csoport volta miatt $0 = 0 \otimes r$. A másik oldal bizonyítása ugyanígy megy. $\square$

### Különleges gyűrűk és nullosztók (Farkas-diák)

- **Nullgyűrű**: egyetlen elemből (a nullelemből) áll.
- **Zérógyűrű**: bármely két elem szorzata a nullelem.
- Az $R$ gyűrűben $a$ **baloldali**, $b$ **jobboldali nullosztó**, ha $a \neq 0$, $b \neq 0$ és $ab = 0$.

### Előjelszabály

Gyűrűben $-(ab) = (-a)b = a(-b)$, továbbá $(-a)(-b) = ab$.

**Bizonyítás.** $ab + (-a)b = (a + (-a))b = 0b = 0$, ezért $-(ab) = (-a)b$. Továbbá $(-a)(-b) + (-a)b = (-a)((-b) + b) = 0 = ab + (-a)b$, és $+$-ban egyszerűsíthetünk, így $(-a)(-b) = ab$. $\square$

### Regularitás és nullosztó (lemma)

$R$ gyűrűben a szorzás **akkor és csak akkor reguláris** (egyszerűsíthető), ha $R$ nullosztómentes.

*(⇐)* Legyen $a \neq 0$ nem baloldali nullosztó és $ab = ac$. Ekkor $ab + (-(ac)) = 0$, az előjelszabállyal és a disztributivitással $a(b + (-c)) = 0$, a feltétel miatt $b + (-c) = 0$, azaz $b = c$.
*(⇒)* Ha $a$ baloldali nullosztó, $ab = 0$ valamely $b \neq 0$-ra, akkor tetszőleges $c$-re $ac = ac + ab = a(c + b)$, de $c \neq c + b$, így a szorzás nem reguláris.

### Megjegyzések a diákról

- **Véges integritási tartomány test**; **testben nincs nullosztó** (bizonyításuk gyakorlaton szerepel, a diákon nincs kidolgozva).
- A diák hierarchiája: gyűrű $\to$ (nullosztómentes, kommutatív, egységelemes) $\to$ integritási tartomány $\to$ egységelemes integritási tartomány $\to$ Gauss-gyűrű (UFD) $\to$ főideálgyűrű $\to$ euklideszi gyűrű $\to$ test; a ferdetest a nullosztómentes gyűrű és a test között áll (a diák ábrája szerint a test kommutatív ferdetest, egyben euklideszi gyűrű).
- A gyűrűk homomorf képe gyűrű, lásd [[concepts/dimatii/homomorfizmustetel]]; részgyűrű és ideál: [[concepts/dimatii/reszgyuru-es-idealok]]; példa: [[concepts/dimatii/boole-gyuru]].

### Feladattípusok és módszerek: gyűrű-e? (gyakorlati feladatsor, 2020 ősz, 6. sor)

**Módszer:** részstruktúránál elég a zártságot (összeg, szorzat, ellentett) ellenőrizni, a műveleti azonosságok öröklődnek; utána kérdés, hogy van-e egységelem, kommutatív-e, van-e nullosztó, és minden nemnulla elem invertálható-e (→ test).

| Struktúra | Gyűrű? | Test? | Indok |
|---|---|---|---|
| $\mathbb{Z}$ | igen | nem | $2$ nem invertálható |
| páros számok | igen | nem | nincs egységelem |
| $n\mathbb{Z}$, $\lvert n\rvert \ge 2$ | igen | nem | nincs egységelem; $n=0$: $\{0\}$ zérógyűrű; $\lvert n\rvert = 1$: $\mathbb{Z}$ |
| $\{a+b\sqrt2 : a,b\in\mathbb{Z}\}$ és $\{a+b\sqrt3\}$ | igen | nem | zárt: $(a+b\sqrt2)(c+d\sqrt2) = (ac+2bd)+(ad+bc)\sqrt2$; $1/2$ nincs benne |
| $\{a+bi : a,b\in\mathbb{Z}\}$ (Gauss-egészek) | igen | nem | $1/2$ nincs benne |
| $\mathbb{Z}^{n\times n}$, $\mathbb{R}^{n\times n}$ ($n \ge 2$) | igen | nem | nem kommutatív, van nullosztó |
| függvények $[-1,1]$-en, pontonkénti műveletekkel | igen | nem | az $[-1,0]$-n, illetve $(0,1]$-n eltűnő nemnulla függvények szorzata $0$ |
| $\left\{\begin{pmatrix} a & b\\ 2b & a\end{pmatrix}: a,b\in\mathbb{R}\right\}$ | igen (kommutatív) | nem | $\det = a^2-2b^2$ eltűnik, ha $a=\sqrt2 b$ ($\mathbb{Q}$ fölött viszont test lenne) |

**Zérógyűrű:** ha $(S,+)$ Abel-csoport és $a\circ b = 0$ (az additív egységelem) minden $a,b$-re, akkor $(S,+,\circ)$ gyűrű: $(a\circ b)\circ c = 0 = a\circ(b\circ c)$ és $a\circ(b+c) = 0 = 0+0 = a\circ b + a\circ c$ (a másik disztributivitás ugyanígy).

**Tipikus hiba:** a $\{0\}$ „testnek” nevezése — a testhez legalább két elem ($0\neq 1$) kell.

## Kapocs

- [[concepts/dimatii/csoport]] — a gyűrű additív része Abel-csoport
- [[concepts/dimatii/felcsoport-es-monoid]] — a gyűrű multiplikatív része félcsoport
- [[concepts/dimatii/nullosztomentes-gyuru]] — a gyűrűk fontos alosztálya, a karakterisztika fogalmával
- [[concepts/dimatii/integritasi-tartomany]] — kommutatív, nullosztómentes gyűrű
- [[concepts/dimatii/test]] — a gyűrűk azon esete, ahol az osztás is elvégezhető
- [[concepts/dimatii/faktorgyuru]] — az ideál szerinti maradékosztály-gyűrű
- [[concepts/dimatii/polinomgyuru]] — az $R[x]$ polinomgyűrű mint gyűrűkonstrukció
