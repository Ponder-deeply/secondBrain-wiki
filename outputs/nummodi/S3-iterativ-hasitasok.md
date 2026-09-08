---
tags: [synthesis]
sources:
  - tetel-18-iteracios-konvergencia.md
  - tetel-19-jacobi-iteracio.md
  - tetel-20-csillapitott-jacobi.md
  - tetel-21-gauss-seidel.md
  - tetel-22-gauss-seidel-relax.md
  - tetel-23-richardson.md
  - tetel-24-reszleges-lu-ilu.md
updated: 2026-06-09
---

# S3 – Iteratív hasítások

Mind a hat iteratív módszer (Jacobi, csillapított Jacobi, Gauss–Seidel, SOR, Richardson, ILU) **egyetlen sablon** példánya: az $A = P + Q$ hasításból kapott $x_{k+1} = x_k + P^{-1}r_k$ reziduum-iteráció, és a módszerek **kizárólag a $P$ előkondicionáló választásában** különböznek. A konvergencia elmélete is közös: az elégséges $\|B\|<1$ (Banach-kontrakció) és a szükséges + elégséges $\varrho(B)<1$ feltétel mindegyikre ugyanaz, csak a módszer-specifikus konvergencia-tartomány (SDD, $0<\omega<2$, $\rho_\text{opt}$, …) tér el.

## A közös sablon

**A hasítás.** Legyen $A = P + Q$, ahol $P$ invertálható (az „előkondicionáló", ill. precondicionáló mátrix). Az $Ax=b$ egyenlet ekvivalens átírása:

$$Px = -Qx + b \quad\Longrightarrow\quad x^{(k+1)} = \underbrace{-P^{-1}Q}_{B}\,x^{(k)} + \underbrace{P^{-1}b}_{c} = Bx^{(k)} + c.$$

A $B = -P^{-1}Q$ az **iterációs mátrix**, $c = P^{-1}b$ az eltolásvektor.

**Reziduum-alak (mindegyik módszerre azonos).** Mivel $Q = A - P$:

$$B = -P^{-1}Q = -P^{-1}(A-P) = I - P^{-1}A,$$

ezért

$$x^{(k+1)} = (I - P^{-1}A)x^{(k)} + P^{-1}b = x^{(k)} + P^{-1}\underbrace{(b - Ax^{(k)})}_{r^{(k)}}.$$

$$\boxed{\,x^{(k+1)} = x^{(k)} + P^{-1} r^{(k)}, \qquad r^{(k)} = b - Ax^{(k)}.\,}$$

Gyakorlatban nem $P^{-1}$-et számolunk, hanem a $P\,s^{(k)} = r^{(k)}$ (jellemzően háromszög- vagy diagonális) rendszert oldjuk meg, majd $x^{(k+1)} = x^{(k)} + s^{(k)}$, és a reziduum olcsón frissül: $r^{(k+1)} = r^{(k)} - A\,s^{(k)}$.

**A $P$ választása minden.** $A = D + L + U$ ($D$ átló, $L$ szigorú alsó, $U$ szigorú felső háromszög):

| Módszer (tétel) | $P$ | iterációs mátrix $B = I - P^{-1}A$ | reziduum-lépés |
|---|---|---|---|
| Jacobi (19) | $D$ | $B_J = -D^{-1}(L+U)$ | $x + D^{-1}r$, ill. $Ds = r$ |
| Csill. Jacobi $J(\omega)$ (20) | $\tfrac{1}{\omega}D$ | $B_{J(\omega)} = (1-\omega)I + \omega B_J$ | $x + \omega D^{-1}r$, ill. $Ds = \omega r$ |
| Gauss–Seidel (21) | $D+L$ | $B_{GS} = -(D+L)^{-1}U$ | $(D+L)\,s = r$ |
| SOR $S(\omega)$ (22) | $\tfrac{1}{\omega}(D+\omega L)$ | $B_{\mathrm{SOR}} = (D+\omega L)^{-1}[(1-\omega)D - \omega U]$ | $(D+\omega L)\,s = \omega r$ |
| Richardson $R(\rho)$ (23) | $\tfrac{1}{\rho}I$ | $B_R = I - \rho A$ | $x + \rho r$ |
| ILU (24) | $\tilde{L}\tilde{U}$ (hiányos LU) | $B_{\mathrm{ILU}} = I - (\tilde{L}\tilde{U})^{-1}A$ | $\tilde{L}\tilde{U}\,s = r$ |

Minden sor ugyanannak a $x^{(k+1)} = x^{(k)} + P^{-1}r^{(k)}$ képletnek a $P$-specifikus alakja. A $P$ „erőssége" (mennyire közelíti $A$-t) és „olcsósága" (mennyire könnyű invertálni) közti kompromisszum különbözteti meg a módszereket: $D$ (legolcsóbb) $\to$ $D+L$ $\to$ $\tilde{L}\tilde{U} \approx A$ (legdrágább, de leghatékonyabb).

## Konvergencia — egy elmélet mindenre

A $x^{(k+1)} = Bx^{(k)} + c$ iteráció minden módszerre ugyanazon az elméleten áll; **ne ismételd módszerenként**, csak a $B$ változik.

**Elégséges feltétel — Banach / kontrakció.** Ha $\|B\| < 1$ valamely indukált mátrixnormában, akkor $\varphi(x) = Bx + c$ kontrakció $q = \|B\|$ hányadossal:
$$\|\varphi(x)-\varphi(y)\| = \|B(x-y)\| \le \|B\|\,\|x-y\|.$$
A Banach-fixponttétel miatt az iteráció **bármely** $x^{(0)}$-ból az egyetlen fixponthoz konvergál.

**Szükséges és elégséges feltétel — spektrálsugár.** Az iteráció minden $x^{(0)}$-ra konvergens
$$\Longleftrightarrow \quad \varrho(B) := \max\{|\lambda| : \lambda \text{ a } B \text{ sajátértéke}\} < 1.$$

**A kettő kapcsolata.** Minden indukált normára $\varrho(B) \le \|B\|$, és tetszőleges $\varepsilon>0$-hoz van olyan norma, amelyre $\|B\| \le \varrho(B)+\varepsilon$. Ezért:
$$\|B\| < 1 \;\Longrightarrow\; \varrho(B) < 1 \quad (\text{fordítva nem}).$$
Vagyis $\|B\|<1$ **csak elégséges** (szigorúbb, kényelmesen ellenőrizhető), $\varrho(B)<1$ pedig a **pontos határvonal** (szükséges + elégséges).

**Hibabecslések** ($\|B\|<1$, $q = \|B\|$):
$$\|x^* - x^{(k)}\| \le \frac{q^k}{1-q}\,\|x^{(1)} - x^{(0)}\| \quad\text{(a priori)}, \qquad \|x^* - x^{(k)}\| \le \frac{q}{1-q}\,\|x^{(k)} - x^{(k-1)}\| \quad\text{(a posteriori)}.$$

A konvergencia sebességét a $\varrho(B)$ szabja meg; ezért a módszerek közti különbség lényege: **melyik $P$ szorítja le legjobban $\varrho(B)$-t**.

## Tétel-delták

A 18. tétel a közös elmélet; a 19–24 mindegyike egyetlen új dolgot tesz hozzá: a $P$-választást és annak saját konvergencia-feltételét.

| Tétel | Az egyetlen új dolog |
|---|---|
| **18** | A közös sablon és elmélet: $A=P+Q$, $B=-P^{-1}Q$, kontrakció, Banach, $\|B\|<1$ vs $\varrho(B)<1$, hibabecslés. Minden más ennek a példánya. |
| **19 Jacobi** | $P=D$. $B_J = -D^{-1}(L+U)$. Koordinátás: $x_i^{(k+1)} = \frac{1}{a_{ii}}(b_i - \sum_{j\ne i} a_{ij}x_j^{(k)})$ — csak régi értékek. Konvergál, ha $A$ SDD. |
| **20 csill. Jacobi $J(\omega)$** | $P=\frac{1}{\omega}D$, $0<\omega\le 1$ (alulrelaxálás). $B_{J(\omega)} = (1-\omega)I + \omega B_J$, sajátértékei $\mu_i = (1-\omega)+\omega\lambda_i$. Az alulrelaxálás **megőrzi** a Jacobi-konvergenciát. Felismerés: ez $= D^{-1}$-előkondicionált Richardson. |
| **21 Gauss–Seidel** | $P=D+L$. $B_{GS} = -(D+L)^{-1}U$. Koordinátás: $x_j^{(k+1)}$ ($j<i$) **azonnal** felhasználva. Konvergál, ha $A$ SDD (vagy SPD). |
| **22 SOR $S(\omega)$** | $P=\frac{1}{\omega}(D+\omega L)$. Relaxált GS, $\omega=1\Rightarrow$ GS. Konv. **szükséges**: $0<\omega<2$. Tridiag. SPD-re optimális $\omega_0$. |
| **23 Richardson $R(\rho)$** | $P=\frac{1}{\rho}I$ (skálázott identitás), $B_R = I-\rho A$. SPD $A$-ra konv. $\Leftrightarrow 0<\rho<2/\lambda_{\max}$; $\rho_\text{opt} = 2/(\lambda_{\min}+\lambda_{\max})$, $\varrho(B_R) = \frac{M-m}{M+m}$. |
| **24 ILU** | $P=\tilde{L}\tilde{U}$ (hiányos LU egy $J$ pozícióhalmazra), $A = \tilde{L}\tilde{U} - Q$. A direkt LU (S2) hiányos rokona; **preconditionerként** köt az iteratív világba. Létezik + egyértelmű, ha minden vezető főminor $\ne 0$ (pl. SDD). |

## Felmondható tételmondatok

- **Elégséges feltétel:** Ha $\|B\| < 1$ valamely indukált normában, akkor $x^{(k+1)} = Bx^{(k)}+c$ bármely $x^{(0)}$-ból konvergál a fixponthoz.
- **Szükséges + elégséges:** $x^{(k+1)} = Bx^{(k)}+c$ minden $x^{(0)}$-ra konvergens $\iff \varrho(B) < 1$. ($\varrho(B)\le\|B\|$ miatt $\|B\|<1$ csak elégséges.)
- **Reziduum-ekvivalencia:** Minden hasítási módszer $x^{(k+1)} = x^{(k)} + P^{-1}r^{(k)}$ alakú; a módszert a $P$ azonosítja.
- **Jacobi / Gauss–Seidel:** $A$ szigorúan diagonálisan domináns ($|a_{ii}| > \sum_{j\ne i}|a_{ij}|$) $\Rightarrow$ mindkettő konvergens.
- **Csillapított Jacobi:** $|\lambda_i| < 1$ és $0<\omega\le 1 \Rightarrow |\mu_i| = |(1-\omega)+\omega\lambda_i| < 1$, azaz a konvergencia megőrződik.
- **SOR szükséges feltétel:** Ha az $S(\omega)$ konvergens, akkor $0 < \omega < 2$.
- **SOR optimális $\omega$** (tridiag., SPD $A$): $\omega_0 = \dfrac{2}{1 + \sqrt{1 - \varrho(B_J)^2}}$, és ekkor $\varrho(B_{\mathrm{SOR}}(\omega_0)) = \omega_0 - 1 < \varrho(B_J)^2 = \varrho(B_{GS})$.
- **Richardson** (SPD $A$, $m=\lambda_{\min}$, $M=\lambda_{\max}$): konvergens $\iff 0<\rho<\frac{2}{M}$; $\rho_\text{opt} = \frac{2}{m+M}$, ekkor $\varrho(B_R) = \frac{M-m}{M+m}$.
- **ILU létezés + egyértelműség:** Ha $A$ minden vezető főminorja nemnulla (pl. SDD), akkor a $J$-re illeszkedő részleges LU-felbontás létezik és egyértelmű.

## Bizonyítás-magok

**Reziduum-alak levezetése.** $B = -P^{-1}Q = -P^{-1}(A-P) = I - P^{-1}A$, így $x^{(k+1)} = Bx^{(k)}+c = x^{(k)} - P^{-1}Ax^{(k)} + P^{-1}b = x^{(k)} + P^{-1}(b-Ax^{(k)}) = x^{(k)} + P^{-1}r^{(k)}$.

**Az eredeti megoldáshoz tart.** Ha $x^{(k)}\to x^*$, akkor $x^* = Bx^*+c$, azaz $(I-B)x^* = c$. De $I - B = P^{-1}A$ és $c = P^{-1}b$, ezért $P^{-1}Ax^* = P^{-1}b \Rightarrow Ax^* = b$. A fixpont tehát pontosan az eredeti LER megoldása.

**$\|B\|<1 \Rightarrow$ Cauchy-sorozat.** $\|x^{(k+1)}-x^{(k)}\| = \|B(x^{(k)}-x^{(k-1)})\| \le q\|x^{(k)}-x^{(k-1)}\| \le \dots \le q^k\|x^{(1)}-x^{(0)}\|$. Háromszög-egyenlőtlenség + mértani sor: $\|x^{(k+m)}-x^{(k)}\| \le \sum_{j=0}^{m-1} q^{k+j}\|x^{(1)}-x^{(0)}\| < \frac{q^k}{1-q}\|x^{(1)}-x^{(0)}\| \to 0$. Tehát Cauchy a teljes $\mathbb{R}^n$-en $\Rightarrow$ konvergens; $\varphi$ folytonossága adja a fixpontot, a kontrakció az egyértelműséget.

**SOR: $0<\omega<2$ a determinánsból.** $\varrho(B_{\mathrm{SOR}})<1$ szükséges a konvergenciához, és $|\det B_{\mathrm{SOR}}| \le \varrho(B_{\mathrm{SOR}})^n$. Mivel $B_{\mathrm{SOR}} = (D+\omega L)^{-1}[(1-\omega)D-\omega U]$ háromszög-tényezőkkel, $\det B_{\mathrm{SOR}} = \frac{\det[(1-\omega)D]}{\det D} = (1-\omega)^n$. Így $|1-\omega|^n < 1 \Rightarrow |1-\omega|<1 \Rightarrow 0<\omega<2$.

**Csillapított Jacobi sajátértékei.** Ha $B_J v_i = \lambda_i v_i$, akkor $B_{J(\omega)} v_i = [(1-\omega)I + \omega B_J]v_i = [(1-\omega)+\omega\lambda_i]v_i$, tehát $\mu_i = (1-\omega)+\omega\lambda_i$. $|\lambda_i|<1$ és $0<\omega\le 1$ esetén $|\mu_i| \le (1-\omega)+\omega|\lambda_i| < (1-\omega)+\omega = 1$, vagyis $\varrho(B_{J(\omega)})<1$.

**ILU helyesség és egyértelműség (T24).** A tárgy leghosszabb levezetése. Cél: az algoritmus által gyártott $\tilde{L},\tilde{U}$ az $A$ egyedi, $J$-re illeszkedő részleges LU-felbontása, $A=\tilde{L}\tilde{U}-Q$.

*Algoritmus-emlékeztető.* $\tilde{A}_1:=A$. A $k$-adik lépés ($k=1,\dots,n-1$): szétbontás $\tilde{A}_k = P_k - Q_k$, ahol $P_k$-ban a $k$-adik sor és oszlop $J$-beli elemeit kinullázzuk, $Q_k := P_k - \tilde{A}_k$; majd $\tilde{A}_{k+1} := L_k P_k$, ahol $L_k$ a szokásos $k$-adik elimináló mátrix ($(L_k)_{ik} = -p_{ik}/p_{kk}$, $i>k$). Végül $\tilde{U} := \tilde{A}_n$, $\tilde{L} := L_1^{-1}\cdots L_{n-1}^{-1}$, $Q := \sum_{k=1}^{n-1} Q_k$.

*(i) Szerkezeti lemma ($\ast$).* $Q_k = P_k - \tilde{A}_k$ csak a $k$-adik sor/oszlop $J$-beli pozícióiban nemnulla, méghozzá az $i\le k$ részen (a $k$-adik lépés a már kész $i<k$ háromszög-részt nem bántja, a $j<k$ oszlopok $k$-adik sorbeli eleme pedig már kinullázott). Az $i>k$ sorokban $Q_k = 0$. Az $L_m$ ($m\ge k$) eliminációk viszont csak az $i > m \ge k$ sorokat módosítják, ezért $Q_k$-t érintetlenül hagyják:
$$L_m\cdots L_k\,Q_k = Q_k \quad (m\ge k), \qquad \text{innen} \qquad \tilde{L}\,Q_k = Q_k, \quad \tilde{L}\,Q = Q. \tag{$\ast$}$$

*(ii) $A = \tilde{L}\tilde{U} - Q$ indukcióval.* Állítás: minden $k=1,\dots,n$-re
$$L_{k-1}\cdots L_1\,A = \tilde{A}_k - (Q_1+\cdots+Q_{k-1}).$$
- **Alaplépés ($k=1$):** $\tilde{A}_1 = A$, az összeg üres. ✓
- **Indukciós lépés:** $P_k = \tilde{A}_k + Q_k$, így $\tilde{A}_{k+1} = L_k P_k = L_k\tilde{A}_k + L_k Q_k$. ($\ast$) miatt $L_k Q_j = Q_j$ minden $j\le k$-ra, ezért az indukciós feltevést beírva $\tilde{A}_{k+1} = L_k\cdots L_1 A + (Q_1+\cdots+Q_k)$, vagyis az állítás $k+1$-re. ✓
- **$k=n$:** $L_{n-1}\cdots L_1\,A = \tilde{U} - Q$. Bal oldalról $\tilde{L} = (L_{n-1}\cdots L_1)^{-1}$-lel szorozva, és ($\ast$)-ból $\tilde{L}Q = Q$-t használva:
$$A = \tilde{L}\tilde{U} - \tilde{L}Q = \tilde{L}\tilde{U} - Q. ✓$$
A kényszernullák triviálisan teljesülnek: a szétbontás minden lépésben explicit nullázza a $J$-beli elemeket a $k$-adik sorban/oszlopban, így $(i,j)\in J$-re $\tilde{u}_{ij}=0$ és $\tilde{l}_{ij}=0$.

*(iii) Egyértelműség.* Ha $(\tilde{L}_1,\tilde{U}_1)$ és $(\tilde{L}_2,\tilde{U}_2)$ is $J$-re illeszkedő részleges LU, akkor $\tilde{L}_1\tilde{U}_1 = \tilde{L}_2\tilde{U}_2 \Rightarrow \tilde{L}_2^{-1}\tilde{L}_1 = \tilde{U}_2\tilde{U}_1^{-1}$. A bal oldal egységalsó-háromszög, a jobb felső-háromszög, ami egyszerre csak diagonális lehet; egységátlójú lévén $=I$. Tehát $\tilde{L}_1 = \tilde{L}_2$, $\tilde{U}_1 = \tilde{U}_2$. $\square$

## Kapcsolódó oldalak

- [[S2-direkt-megoldas]] — a direkt (LU, Gauss) világ; az **ILU** annak hiányos rokona, és preconditionerként ($P=\tilde{L}\tilde{U}$) köti a két megközelítést össze. Híd: **csillapított Jacobi = $D^{-1}$-előkondicionált Richardson**.
- [[concepts/nummodi/banach-fixponttetel]] — a közös konvergencia-elmélet teljes bizonyítása.
- [[concepts/nummodi/iteracios-modszerek-ler]] — az $A=P+Q$ keret általános tárgyalása.
