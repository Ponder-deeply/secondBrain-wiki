---
tags: [concept]
sources: [nummodi_beugro_NM1.pdf]
derivation: source
kind: overview
element: air
updated: 2026-10-23
---

# Beugró: a 75 vizsgakérdés rövid válaszai

A szóbeli vizsga előtti 15 pontos, 20 perces írásbeli (**beugró**) a Canvasban közzétett 75 kérdésből áll; 8 pont kell a szóbelire bocsátáshoz (lásd [[subjects/nummodi]], Követelmények). A beugró félévközi kiváltása a két ZH után két 15 pontos kérdéssorral lehetséges (8–8 pont kell): az 1. ZH utáni sor az **1–34.**, a 2. ZH utáni a **35–66.** kérdésekből áll (a 67–75. kérdések e két kiváltó sorban nem szerepelnek). Az alábbi lap a hivatalos válaszlista (frissítve: 2025. augusztus 31.) tömör, pontos szövegű mása, témakörönként; a részletes tárgyalás a hivatkozott fogalomlapokon van.

## Tartalom

### Gépi számok és hibaszámítás (1–9)

Részletek: [[concepts/nummodi/lebegopont-modell]], [[concepts/nummodi/hibaszamitas]].

- **Normalizált szám:** $a = \pm m 2^k$, $m = \sum_{i=1}^t m_i 2^{-i}$, $m_i \in \{0,1\}$, $m_1 = 1$; $m$ a mantissza, $t$ a hossza, $k$ a karakterisztika; jelölés $a = \pm[m_1\dots m_t | k]$.
- **Gépi számok:** $M(t,k^-,k^+) = \{\pm m 2^k : k^- \le k \le k^+\} \cup \{0\}$.
- **Nevezetes számok:** $M_\infty = (1 - 2^{-t})\,2^{k^+}$; $\varepsilon_0 = \tfrac12 2^{k^-}$ (legkisebb pozitív); $\varepsilon_1 = 2^{1-t}$ — az 1 és közvetlen rákövetkezője különbsége (relatív pontosság).
- **Input függvény:** $fl: \mathbb{R}_M \to M$, $fl(x) = 0$ ha $|x| < \varepsilon_0$, különben a kerekítés szerint közelebbi gépi szám. **Tétel:** $|x - fl(x)| \le \varepsilon_0$, ha $|x| < \varepsilon_0$; és $\le \tfrac12 |x| \varepsilon_1$, ha $\varepsilon_0 \le |x| \le M_\infty$.
- **Hibafogalmak:** $\Delta a = A - a$; abszolút hiba $|\Delta a|$; abszolút hibakorlát $\Delta_a \ge |\Delta a|$; relatív hiba $\delta a = \Delta a / A \approx \Delta a / a$; relatív hibakorlát $\delta_a \ge |\delta a|$.
- **Alapműveletek, abszolút korlát:** $\Delta_{a\pm b} = \Delta_a + \Delta_b$; $\Delta_{ab} = |a|\Delta_b + |b|\Delta_a$; $\Delta_{a/b} = \dfrac{|a|\Delta_b + |b|\Delta_a}{b^2}$.
- **Alapműveletek, relatív korlát:** $\delta_{a\pm b} = \dfrac{|a|\delta_a + |b|\delta_b}{|a \pm b|}$; $\delta_{ab} = \delta_{a/b} = \delta_a + \delta_b$.
- **Függvényérték:** $f \in C^1$: $\Delta_{f(a)} = M_1 \Delta_a$, $M_1 = \max_{k(a)}|f'|$. $f \in C^2$: $\Delta_{f(a)} = |f'(a)|\Delta_a + \tfrac{M_2}{2}\Delta_a^2$; relatív korlát $\delta_{f(a)} = \dfrac{|a||f'(a)|}{|f(a)|}\delta_a$.
- **Kondíciószám (függvény):** $c(f,a) = \dfrac{|a||f'(a)|}{|f(a)|}$.

### Gauss-elimináció és LU-felbontás (10–14)

Részletek: [[concepts/nummodi/gauss-eliminacio]], [[concepts/nummodi/lu-felbontas]], [[concepts/nummodi/haromszogmatrixok]].

- **Műveletigény:** GE $\tfrac23 n^3 + O(n^2)$; visszahelyettesítés $n^2$ (az $O(n)$ tag 0); LU-felbontás $\tfrac23 n^3 + O(n^2)$; háromszögmátrixú LER $n^2 + O(n)$.
- **Egy GE-lépés:** $L_k A^{(k-1)} = A^{(k)}$, $L_k = I - \ell_k e_k^T \in \mathcal{L}_1$, $\ell_k = (0,\dots,0,\ell_{k+1,k},\dots,\ell_{nk})^T$, $\ell_{ik} = a^{(k-1)}_{ik}/a^{(k-1)}_{kk}$.
- **LU létezése (GE-vel):** ha a GE sor- és oszlopcsere nélkül elvégezhető, létezik $A = LU$, $L \in \mathcal{L}_1$, $U \in \mathcal{U}$.
- **LU létezése (GE nélkül):** ha $D_k = \det((a_{ij})_{i,j=1}^k) \ne 0$ ($k = 1,\dots,n-1$), akkor $A = LU$ létezik és $u_{kk} \ne 0$ ($k = 1,\dots,n-1$); ha $\det A \ne 0$, a felbontás egyértelmű.

### Speciális mátrixok, Schur-komplementer, Cholesky (15–23)

Részletek: [[concepts/nummodi/schur-komplementer]], [[concepts/nummodi/cholesky-felbontas]], [[concepts/nummodi/ldu-felbontas]].

- **Szimmetrikus:** $A^T = A$; **pozitív definit:** $\langle Ax, x\rangle = x^T A x > 0$ minden $x \ne 0$-ra.
- **Szigorúan diagonálisan domináns (sorokra):** $|a_{ii}| > \sum_{j \ne i}|a_{ij}|$ minden $i$-re; oszlopokra $|a_{ii}| > \sum_{j \ne i}|a_{ji}|$.
- **Fél sávszélesség $s$:** $|i-j| > s \Rightarrow a_{ij} = 0$, és van $k,l$, $|k-l| = s$, $a_{kl} \ne 0$. **Profil:** a $k_i$ (soronként az első nemnulla előtti nullák) és $l_j$ (oszloponként) számok összessége.
- **Schur-komplementer:** $A_{11} \in \mathbb{R}^{k\times k}$ invertálható, $[A|A_{11}] = A_{22} - A_{21}A_{11}^{-1}A_{12}$.
- **Megmaradási tételek:** szimmetria; szimmetrikus pozitív definitség; szigorú diagonális dominancia; fél sávszélesség legfeljebb $s$ marad (a sávon kívüli nullák megmaradnak); a profil nem csökkenhet; $\det A \ne 0 \Rightarrow \det[A|A_{11}] \ne 0$.
- **Cholesky:** $A = LL^T$, $A$ szimmetrikus, $L \in \mathcal{L}$, $l_{ii} > 0$. **Tétel:** $A$ szimmetrikus pozitív definit $\Rightarrow$ $\exists!$ $A = LL^T$. Műveletigény $\tfrac13 n^3 + O(n^2)$, háromszög LER $n^2 + O(n)$.

### QR-felbontás és Householder (24–28)

Részletek: [[concepts/nummodi/qr-felbontas]], [[concepts/nummodi/gram-schmidt-ortogonalizacio]], [[concepts/nummodi/householder-transzformacio]], [[concepts/nummodi/ortogonalis-matrixok]].

- **QR tétel:** $A$ oszlopai lineárisan függetlenek $\Rightarrow$ $\exists A = QR$; ha még $r_{ii} > 0$ is, egyértelmű. Műveletigény (Gram–Schmidt): $2n^3 + O(n^2)$.
- **Householder-mátrix:** $H(v) = I - 2vv^T$, $\|v\|_2 = 1$.
- **Négy tulajdonság:** (1) szimmetrikus; (2) ortogonális, $H^{-1} = H^T = H$, $H^2 = I$; (3) $H(v)v = -v$; (4) $y \perp v \Rightarrow H(v)y = y$.
- **$Ha = b$:** $a \ne b$, $\|a\|_2 = \|b\|_2$ ($a, b \ne 0$) esetén $v = \pm\dfrac{a-b}{\|a-b\|_2}$.

### Normák, kondíciószám, LER érzékenysége (29–41)

Részletek: [[concepts/nummodi/vektornormak]], [[concepts/nummodi/matrixnormak]], [[concepts/nummodi/kondicioszam]], [[concepts/nummodi/ler-erzekenysege]], [[concepts/nummodi/relativ-maradek]].

- **Vektornorma:** $\|x\| \ge 0$; $\|x\| = 0 \Leftrightarrow x = 0$; $\|\lambda x\| = |\lambda|\|x\|$; háromszög-egyenlőtlenség.
- **Mátrixnorma:** ugyanez négy tulajdonság mátrixokra, plusz szubmultiplikativitás $\|AB\| \le \|A\|\|B\|$.
- **Indukált norma:** $\|A\| = \sup_{x \ne 0}\|Ax\|_v/\|x\|_v$ mátrixnorma. **Illeszkedés:** $\|Ax\|_v \le \|A\|\|x\|_v$.
- **Nevezetes normák:** $\|A\|_1 = \max_j\sum_i|a_{ij}|$; $\|A\|_2 = \varrho(A^TA)^{1/2}$; $\|A\|_\infty = \max_i\sum_j|a_{ij}|$; $\|A\|_F = (\sum_{i,j}|a_{ij}|^2)^{1/2}$. **Spektrálsugár:** $\varrho(B) = \max_i|\lambda_i(B)|$.
- **Mátrix kondíciószáma:** $\operatorname{cond}(A) = \|A\|\|A^{-1}\|$ (ha $A$ invertálható).
- **Jobboldal perturbációja** ($b \ne 0$, illeszkedő normák): $\dfrac{1}{\operatorname{cond}(A)}\dfrac{\|\Delta b\|}{\|b\|} \le \dfrac{\|\Delta x\|}{\|x\|} \le \operatorname{cond}(A)\dfrac{\|\Delta b\|}{\|b\|}$.
- **Mátrix perturbációja** ($\|\Delta A\|\|A^{-1}\| < 1$, indukált norma): $\dfrac{\|\Delta x\|}{\|x\|} \le \dfrac{\operatorname{cond}(A)}{1 - \|\Delta A\|\|A^{-1}\|}\dfrac{\|\Delta A\|}{\|A\|}$.
- **Reziduum:** $r = b - A\tilde{x}$; **relatív maradék:** $\eta = \dfrac{\|r\|}{\|A\|\|\tilde{x}\|}$. Állítások: illeszkedő normában $\eta \le \|\Delta A\|/\|A\|$; 2-es normában egyenlőség.
- **Kondíciószám tulajdonságai:** $\operatorname{cond}(cA) = \operatorname{cond}(A)$; indukált normában $\operatorname{cond}(A) \ge 1$; $Q$ ortogonális $\Rightarrow$ $\operatorname{cond}_2(Q) = 1$; $A$ szimmetrikus $\Rightarrow$ $\operatorname{cond}_2(A) = \dfrac{\max|\lambda_i|}{\min|\lambda_i|}$ (szimmetrikus pozitív definitre abszolútérték nélkül); általában $\operatorname{cond}(A) \ge \dfrac{\max|\lambda_i|}{\min|\lambda_i|}$.

### Iterációs módszerek LER-re (42–59)

Részletek: [[concepts/nummodi/iteracios-modszerek-ler]], [[concepts/nummodi/banach-fixponttetel-rn]], [[concepts/nummodi/jacobi-iteracio]], [[concepts/nummodi/gauss-seidel-iteracio]], [[concepts/nummodi/relaxalt-gauss-seidel-iteracio]], [[concepts/nummodi/richardson-iteracio]], [[concepts/nummodi/ilu-felbontas]].

- **Kontrakció** $\varphi: \mathbb{R}^n \to \mathbb{R}^n$: $\exists q \in [0,1)$: $\|\varphi(x) - \varphi(y)\| \le q\|x-y\|$.
- **Banach-tétel:** (1) $\exists!$ fixpont $x^*$; (2) minden $x^{(0)}$-ra az $x^{(k+1)} = \varphi(x^{(k)})$ sorozat $x^*$-hoz konvergál; (3) $\|x^{(k)} - x^*\| \le q^k\|x^{(0)} - x^*\|$ és $\le \dfrac{q^k}{1-q}\|x^{(1)} - x^{(0)}\|$.
- **Elégséges feltétel** $x^{(k+1)} = Bx^{(k)} + c$-re: $\|B\| < 1$. **Lemma:** $\varrho(B) = \inf\{\|B\| : \|\cdot\| \text{ indukált}\}$. **Szükséges és elégséges:** $\varrho(B) < 1$.
- **Jacobi:** $x^{(k+1)} = -D^{-1}(L+U)x^{(k)} + D^{-1}b$; koordinátásan $x_i^{(k+1)} = -\dfrac{1}{a_{ii}}\Big(\sum_{j\ne i}a_{ij}x_j^{(k)} - b_i\Big)$. **Csillapított:** $B_{J(\omega)} = (1-\omega)I - \omega D^{-1}(L+U)$, $c = \omega D^{-1}b$; $x_i^{(k+1)} = (1-\omega)x_i^{(k)} - \dfrac{\omega}{a_{ii}}\Big(\sum_{j\ne i}a_{ij}x_j^{(k)} - b_i\Big)$.
- **Jacobi konvergenciája:** $A$ sorokra SDD $\Rightarrow$ $\|B_J\|_\infty < 1$; ha $J(1)$ konvergens minden $x^{(0)}$-ra, akkor $0 < \omega < 1$-re $J(\omega)$ is.
- **Gauss–Seidel:** $B_S = -(L+D)^{-1}U$, $c_S = (L+D)^{-1}b$; $x_i^{(k+1)} = -\dfrac{1}{a_{ii}}\Big(\sum_{j<i}a_{ij}x_j^{(k+1)} + \sum_{j>i}a_{ij}x_j^{(k)} - b_i\Big)$.
- **Relaxáció:** $B_{S(\omega)} = (D+\omega L)^{-1}((1-\omega)D - \omega U)$, $c = \omega(D+\omega L)^{-1}b$; $x_i^{(k+1)} = (1-\omega)x_i^{(k)} - \dfrac{\omega}{a_{ii}}\Big(\sum_{j<i}a_{ij}x_j^{(k+1)} + \sum_{j>i}a_{ij}x_j^{(k)} - b_i\Big)$.
- **Relaxáció konvergenciája:** ha $S(\omega)$ konvergens minden $x^{(0)}$-ra, akkor $\omega \in (0,2)$; $A$ szimmetrikus pozitív definit és $\omega \in (0,2)$ $\Rightarrow$ $S(\omega)$ konvergens.
- **SDD esetén:** $\|B_S\|_\infty \le \|B_J\|_\infty < 1$.
- **Szimmetrikus pozitív definit tridiagonális $A$:** $J(1)$, $S(1)$, $S(\omega)$ konvergens ($\omega \in (0,2)$); $\omega_0 = \dfrac{2}{1 + \sqrt{1 - \varrho(B_J)^2}}$; ha $\varrho(B_J) = 0$, akkor $\varrho(B_{S(\omega)}) = \varrho(B_S) = 0$; különben $\varrho(B_{S(\omega_0)}) = \omega_0 - 1 < \varrho(B_S) = \varrho(B_J)^2$.
- **Richardson:** $Ax = b \Leftrightarrow x = (I - pA)x + pb$; $x^{(k+1)} = (I-pA)x^{(k)} + pb$. **Tétel:** $A$ szimmetrikus pozitív definit, $0 < m = \lambda_1 \le \dots \le \lambda_n = M$ $\Rightarrow$ $p \in (0, 2/M)$-re konvergens; optimális $p_0 = \dfrac{2}{M+m}$, $\varrho(B_{R(p_0)}) = \dfrac{M-m}{M+m}$.
- **ILU:** a $J$ pozícióhalmazra illeszkedő részleges LU-felbontás: $J$ tartalmazza a főátlót; $(i,j) \in J \Rightarrow l_{ij} = 0$, $u_{ij} = 0$; $(i,j) \notin J \Rightarrow (A)_{ij} = (LU)_{ij}$. Algoritmus: $\tilde{A}_1 = A$; $k = 1..n-1$: szétbontás $\tilde{A}_k = P_k - Q_k$ ($J$-beli elemeket $Q_k$ viszi el), elimináció $\tilde{A}_{k+1} = L_kP_k$; $U = \tilde{A}_n$, $L = L_1^{-1}\cdots L_{n-1}^{-1}$, $Q = Q_1 + \dots + Q_{k-1}$, így $A = LU - Q$. **Létezés:** $A$ sorokra SDD $\Rightarrow$ $\exists!$ ILU-felbontás.
- **ILU-iteráció:** $A = P - Q$, $P = LU$; $r^{(0)} = b - Ax^{(0)}$; $LUs^{(k)} = r^{(k)}$ (két háromszögmátrixú LER), $x^{(k+1)} = x^{(k)} + s^{(k)}$, $r^{(k+1)} = r^{(k)} - As^{(k)}$.

### Nemlineáris egyenletek és polinomok (60–75)

Részletek: [[concepts/nummodi/nemlinearis-egyenletek-fixpont]], [[concepts/nummodi/konvergenciarend]], [[concepts/nummodi/intervallumfelezes]], [[concepts/nummodi/newton-modszer]], [[concepts/nummodi/hurmodszer-szelomodszer]], [[concepts/nummodi/polinom-gyokbecsles]], [[concepts/nummodi/horner-algoritmus]].

- **Bolzano:** $f \in C[a,b]$, $f(a)f(b) < 0 \Rightarrow \exists x^* \in (a,b)$: $f(x^*) = 0$.
- **Intervallumfelezés:** $x_0 = a$, $y_0 = b$, $s_k = (x_k+y_k)/2$; $f(s_k)f(x_k) < 0 \Rightarrow x_{k+1} = x_k, y_{k+1} = s_k$; $> 0 \Rightarrow x_{k+1} = s_k, y_{k+1} = y_k$; $= 0 \Rightarrow x^* = s_k$. Hibabecslés $|x_k - x^*|, |y_k - x^*| < y_k - x_k \le \dfrac{b-a}{2^k}$.
- **Brouwer:** $\varphi: [a;b] \to [a;b]$ folytonos $\Rightarrow$ $\exists x^*$: $x^* = \varphi(x^*)$.
- **Fixponttétel $[a;b]$-n:** $\varphi$ kontrakció $[a;b] \to [a;b]$ $\Rightarrow$ (1) $\exists!$ fixpont; (2) $x_{k+1} = \varphi(x_k)$ konvergál; (3) $|x_k - x^*| \le \dfrac{q^k}{1-q}|x_1 - x_0|$. **Kontrakció elégséges feltétele:** $\varphi \in C^1[a;b]$, $|\varphi'(x)| \le q < 1$.
- **Konvergenciarend:** $x_k \to x^*$ $p$-edrendben konvergál, ha $\exists c > 0$: $\lim\dfrac{|x_{k+1} - x^*|}{|x_k - x^*|^p} = c$.
- **$m$-ed rendű konvergencia:** $\varphi \in C^m[a;b]$, $\varphi'(x^*) = \dots = \varphi^{(m-1)}(x^*) = 0$, $\varphi^{(m)}(x^*) \ne 0$, $x_{k+1} = \varphi(x_k) \to x^*$ $\Rightarrow$ $m$-ed rendű, $|x_{k+1} - x^*| \le \dfrac{M_m}{m!}|x_k - x^*|^m$.
- **Newton-képlet:** az érintő $y = f(x_k) + f'(x_k)(x - x_k)$ és az $x$-tengely metszéspontja: $x_{k+1} = x_k - \dfrac{f(x_k)}{f'(x_k)}$.
- **Newton, monoton konvergencia:** $f \in C^2[a,b]$, $\exists x^*$: $f(x^*) = 0$; $f', f''$ állandó előjelű; $f(x_0)f''(x_0) > 0$ $\Rightarrow$ $x_0$-ból monoton konvergál.
- **Newton, lokális konvergencia:** $f' \ne 0$ $[a,b]$-n, $m_1 = \min|f'| > 0$, $M_2 = \max|f''|$, $M = \dfrac{M_2}{2m_1}$, $|x_0 - x^*| < r = \min\{\tfrac1M, |x^* - a|, |x^* - b|\}$ $\Rightarrow$ másodrendben konvergál, $|x_{k+1} - x^*| \le M|x_k - x^*|^2$.
- **Húrmódszer:** $f(a)f(b) < 0$, $x_0 = a$, $x_1 = b$; $x_{k+1} = x_k - \dfrac{f(x_k)(x_k - x_s)}{f(x_k) - f(x_s)}$, ahol $s$ a legnagyobb index, melyre $f(x_k)f(x_s) < 0$.
- **Szelőmódszer:** $x_{k+1} = x_k - \dfrac{f(x_k)(x_k - x_{k-1})}{f(x_k) - f(x_{k-1})}$. **Lokális konvergencia:** a Newton-tétel feltételei és $|x^* - a|, |x^* - b| < r = 1/M$ mellett $p = \dfrac{1+\sqrt5}{2}$ rendben konvergál; $|x_{k+1} - x^*| \le M|x_k - x^*||x_{k-1} - x^*|$.
- **Többváltozós Newton:** $T(x) = f(x_k) + f'(x_k)(x - x_k)$, $T(x_{k+1}) = 0 \Rightarrow x_{k+1} = x_k - [f'(x_k)]^{-1}f(x_k)$.
- **Gyökbecslés:** $P(x) = a_nx^n + \dots + a_0$, $a_0, a_n \ne 0$; minden $x_k$ gyökre $r := \dfrac{1}{1 + \max_{i=1..n}|a_i|/|a_0|} < |x_k| < R := 1 + \dfrac{\max_{i=0..n-1}|a_i|}{|a_n|}$.
- **Horner:** $a_n^{(1)} = a_n$; $k = n-1,\dots,0$: $a_k^{(1)} = a_{k+1}^{(1)}\xi + a_k$; $P(\xi) = a_0^{(1)}$.

### Megjegyzés a forráshoz

- A beugró a 28 szóbeli tétel [[concepts/nummodi/kovetelmenyek]] alapanyagának definíció- és tételkiállításait kérdezi vissza: a bizonyítások nem szerepelnek benne.

## Kapocs

- [[concepts/nummodi/kovetelmenyek]] — a szóbeli tételjegyzék; a beugró a szóbelire bocsátás feltétele
- [[concepts/nummodi/tematika]] — a kurzus tematikája
- [[subjects/nummodi]] — kurzus áttekintése, vizsgakövetelmények
