---
tags: [concept]
sources: [NM1_ea10.pdf]
derivation: source
kind: procedure
element: water
updated: 2026-09-25
---

# Részleges LU-felbontás és ILU-algoritmus

A részleges (inkomplett) LU-felbontás $A = LU - Q$ alakú, ahol $L$ és $U$ egy előírt $J$ pozícióhalmazon nulla. A $P = LU$ mátrixszal felírt iteráció — az ILU-algoritmus — lépésenként csak két (ritka) háromszögű LER-t old meg; speciális eseteiként a Jacobi-, Gauss–Seidel- és Richardson-iteráció is előáll.

## Tartalom

### Alapötlet

Az iterációs keretben $A = P - Q$ esetén $Px = Qx + b$, azaz $x = P^{-1}Qx + P^{-1}b$. Olyan $P = LU$ felbontást keresünk, hogy a $P^{-1}$-gyel való számolás két háromszögű LER megoldására redukálódjon, és $L$, $U$ ritka maradjon.

### Definíció — ILU-felbontás

- Legyen $J$ a mátrixpozíciók egy részhalmaza, amely nem tartalmazza a főátlót: $(i,i) \notin J$ minden $i$-re. $J$ a **pozícióhalmaz**.
- Az $A$ mátrix $J$-re illeszkedő **részleges LU-felbontása (ILU-felbontása)** olyan $A = LU - Q$ felírás, ahol $L \in \mathcal{L}_1$, $U \in \mathcal{U}$, és
  $$\forall (i,j) \in J:\ l_{ij} = 0,\ u_{ij} = 0; \qquad \forall (i,j) \notin J:\ a_{ij} = (LU)_{ij}.$$

### Algoritmus — ILU-felbontás GE-vel

$\widetilde A_1 := A$; $k = 1, \dots, n-1$:

1. **Szétbontás:** $\widetilde A_k = P_k - Q_k$, ahol
   $$(P_k)_{ik} = 0,\ (Q_k)_{ik} = -\widetilde a^{(k)}_{ik} \ \text{ ha } (i,k) \in J; \qquad (P_k)_{kj} = 0,\ (Q_k)_{kj} = -\widetilde a^{(k)}_{kj} \ \text{ ha } (k,j) \in J,$$
   egyébként $P_k$ megegyezik $\widetilde A_k$-val. Csak a $k$-adik sorban és oszlopban, a $J$-beli helyeken változtatunk.
2. **Elimináció $P_k$-n:** $\widetilde A_{k+1} = L_kP_k$ (a GE $k$-adik lépése, $L_k$ az [[concepts/nummodi/haromszogmatrixok|eliminációs mátrix]]).

### Tétel — az algoritmus helyessége

**Tétel.** Az algoritmus részmátrixaiból legyen

$$U := \widetilde A_n, \qquad L := L_1^{-1}\cdots L_{n-1}^{-1} \ (\text{összepakolással}), \qquad Q := Q_1 + \dots + Q_{n-1} \ (\text{összepakolással}).$$

Ekkor $A = LU - Q$, és a részleges LU-felbontás feltételei teljesülnek.

**Bizonyítás.**

1. Az $n-1$. GE-lépés után felső háromszögmátrixot kapunk, tehát $U := \widetilde A_n \in \mathcal{U}$, és minden $(i,j) \in J$, $i < j$ pozícióra $u_{ij} = 0$ (az (1) lépés kinullázta, a későbbi lépések nem írják felül).
2. Az $n-1$. lépés (2), majd (1) részét alkalmazva:
   $$U = \widetilde A_n = L_{n-1}P_{n-1} = L_{n-1}\bigl(\widetilde A_{n-1} + Q_{n-1}\bigr).$$
3. Ugyanezt $\widetilde A_{n-1}$-re: $\widetilde A_n = L_{n-1}\bigl(L_{n-2}(\widetilde A_{n-2} + Q_{n-2}) + Q_{n-1}\bigr)$. Mivel $Q_{n-1}$ nem nulla elemei csak az $n-1$. sorban és oszlopban vannak, az $n-2$. sora csupa nulla, ezért az $n-2$. GE-lépés nem változtat rajta: $L_{n-2}Q_{n-1} = Q_{n-1}$. Így $Q_{n-1}$ bevihető a belső zárójelbe:
   $$\widetilde A_n = L_{n-1}L_{n-2}\bigl(\widetilde A_{n-2} + Q_{n-2} + Q_{n-1}\bigr).$$
4. Visszafelé folytatva a rekurziót:
   $$U = \widetilde A_n = \underbrace{L_{n-1}L_{n-2}\cdots L_1}_{L^{-1}}\bigl(A + \underbrace{Q_1 + \dots + Q_{n-1}}_{Q}\bigr), \quad\text{azaz}\quad U = L^{-1}(A + Q) \iff A = LU - Q.$$
5. A mátrixok alakja megfelelő: $L \in \mathcal{L}_1$, $U \in \mathcal{U}$. Az (1) lépés garantálja, hogy $(i,j) \in J$-re $l_{ij} = 0$ és $u_{ij} = 0$ (a kinullázott $(i,k)$ elemhez tartozó GE-hányados $l_{ik} = 0$, a kinullázott $(k,j)$ elem pedig $U$-ba kerül nullaként), a (2) GE-lépés pedig, hogy $(i,j) \notin J$-re $a_{ij} = (LU)_{ij}$ (ott $Q$ nulla). $\square$

### Létezés és egyértelműség

**Tétel.** Ha $A$ szigorúan diagonálisan domináns a soraira vagy az oszlopaira, akkor ILU-felbontása (bármely $J$-re) létezik és egyértelmű.

**Biz.** Az (1) lépés a szigorú diagonális dominanciát nem rontja, mert átlón kívüli elemeket vesz ki. A (2) GE-lépés megtartja a szigorú diagonális dominanciát ([[concepts/nummodi/schur-komplementer|megmaradási tételek]] a Schur-komplementerre). Így minden lépésben a főelem nem nulla. $\square$

**Megjegyzések.**

1. Az SDD tulajdonságból következik az összes bal felső részmátrix invertálhatósága (egyik főminor sem nulla).
2. A differenciálegyenletek numerikus megoldásánál gyakori **M-mátrixokra** is egyértelműen létezik ILU-felbontás.
3. Gyakran csak a főátlót és néhány mellékátlót hagyják ki $J$-ből: így a tárigény előre ismert, nem kell a sávon belüli feltöltődéssel foglalkozni.
4. Pl. $N^2 \times N^2$-es mátrixra, amelynek csak a $(-N, -1, 0, 1, N)$ átlóiban van nem nulla elem, érdemes $J$-ből a $(-1, 0, 1)$ átlókat kihagyni: $L$, $U$ két-két átlót tartalmaz, $L$ átlója egyesekből áll, így $3$ darab $N^2$ hosszú átlót kell tárolni $N^4$ elem helyett. A két kétátlós háromszögű LER $2N^2 + \mathcal{O}(1)$ ill. $3N^2 + \mathcal{O}(1)$ művelettel megoldható (a GE $\tfrac23 N^6$ lenne; $N \approx 10^3$).

### Példa

$A = \begin{bmatrix}4&1&2\\1&4&1\\2&1&4\end{bmatrix}$, $J = \{(1,2), (2,3)\}$.

- 1. lépés: $(1,2)$ kinullázása: $P_1 = \begin{bmatrix}4&0&2\\1&4&1\\2&1&4\end{bmatrix}$, $Q_1$-ben $(Q_1)_{12} = -1$. Elimináció: $\widetilde A_2 = \begin{bmatrix}4&0&2\\0&4&\tfrac12\\0&1&3\end{bmatrix}$, hányadosok $\tfrac14, \tfrac12$.
- 2. lépés: $(2,3)$ kinullázása: $(Q_2)_{23} = -\tfrac12$. Elimináció: $\widetilde A_3 = \begin{bmatrix}4&0&2\\0&4&0\\0&0&3\end{bmatrix}$, hányados $\tfrac14$.

$$L = \begin{bmatrix}1&0&0\\\tfrac14&1&0\\\tfrac12&\tfrac14&1\end{bmatrix},\quad U = \begin{bmatrix}4&0&2\\0&4&0\\0&0&3\end{bmatrix},\quad Q = \begin{bmatrix}0&-1&0\\0&0&-\tfrac12\\0&0&0\end{bmatrix},\quad LU = \begin{bmatrix}4&0&2\\1&4&\tfrac12\\2&1&4\end{bmatrix}.$$

Ellenőrzés: $LU - Q = A$. Mivel a $Q_k$-k különböző sorokat/oszlopokat töltenek, elég egyetlen $Q$-t tárolni, $L$-et és $U$-t pedig a GE-hez hasonlóan egy mátrixban („tömör írásmód”).

### ILU-algoritmus (iteráció)

$A = P - Q$, $P = LU$:

$$Px = Qx + b \iff x = P^{-1}Qx + P^{-1}b.$$

**Definíció — ILU-algoritmus:** $x^{(k+1)} = \underbrace{P^{-1}Q}_{B_{ILU}}\,x^{(k)} + \underbrace{P^{-1}b}_{c_{ILU}}$.

**Reziduumvektoros alak.** $Q = P - A$ miatt

$$Px^{(k+1)} = (P - A)x^{(k)} + b = Px^{(k)} + r^{(k)} \implies x^{(k+1)} = x^{(k)} + P^{-1}r^{(k)}.$$

$$\begin{aligned}
&r^{(0)} := b - Ax^{(0)}\\
&k = 1, \dots, \text{leállásig:}\\
&\quad LU\,s^{(k)} = r^{(k)} \ \text{ megoldása (2 db háromszögű LER)}\\
&\quad x^{(k+1)} := x^{(k)} + s^{(k)}\\
&\quad r^{(k+1)} := r^{(k)} - As^{(k)}
\end{aligned}$$

**Megjegyzések.**

1. $B_{ILU} = P^{-1}Q = P^{-1}(P - A) = I - P^{-1}A$. Legyen $P$ közel $A$-hoz: ekkor $\|B_{ILU}\|$ kicsi, az iteráció gyors.
2. Ha $L$-ben és $U$-ban kevés nem nulla átló van, a lépésenkénti LER-megoldás olcsó.
3. Az iteráció végrehajtásához $Q$-ra nincs szükség.

### Általános kétrétegű iteráció — nevezetes speciális esetek

Az ILU reziduumos alakja átírva: $P(x^{(k+1)} - x^{(k)}) = r^{(k)} \iff P(x^{(k+1)} - x^{(k)}) + Ax^{(k)} = b$.

**Definíció.** A $P(x^{(k+1)} - x^{(k)}) + Ax^{(k)} = b$ iteráció az **általános kétrétegű iterációs eljárás**; $P$ a **prekondicionáló mátrix**.

Az összes tanult iteráció ilyen alakú:

| $P$ | Módszer |
|---|---|
| $D$ | [[concepts/nummodi/jacobi-iteracio\|Jacobi]] $J(1)$ |
| $\tfrac1\omega D$ | csillapított Jacobi $J(\omega)$ |
| $D + L$ | [[concepts/nummodi/gauss-seidel-iteracio\|Gauss–Seidel]] $S(1)$ |
| $\tfrac1\omega D + L$ | [[concepts/nummodi/relaxalt-gauss-seidel-iteracio\|relaxált Gauss–Seidel]] $S(\omega)$ |
| $\tfrac1p I$ | [[concepts/nummodi/richardson-iteracio\|Richardson]] $R(p)$ |
| $LU$ az ILU-felbontásból | ILU-iteráció |

(Az $S(\omega)$ sorban $P = \tfrac1\omega(D + \omega L)$, mert a reziduumos alak $x^{(k+1)} = x^{(k)} + \omega(D+\omega L)^{-1}r^{(k)}$. A diasor itt „$P = D + \omega L$”-t ír; ez a $J(\omega)$ sorral — $P = \tfrac1\omega D$ — összevetve $\omega$-szoros skálázásban eltér, a reziduumos alakból levezetett $\tfrac1\omega D + L$ a konzisztens.)

**Speciális esetek a fenti $A$-val:**

- $J = \{(1,2),(2,3)\}$: $\|B_{ILU}\|_2 \approx 0{,}3601$, $\|B_{ILU}\|_\infty \approx 0{,}3438$.
- $J$ = minden átlón kívüli pozíció: $L = I$, $U = 4I$, $P = D$ — ez a **Jacobi-iteráció**; $\|B\|_2 \approx 0{,}6830$, $\|B\|_\infty = 0{,}75$.
- $J$ = a felső háromszög minden átlón kívüli pozíciója: $P = LU = \begin{bmatrix}4&0&0\\1&4&0\\2&1&4\end{bmatrix} = D + L$ — ez a **Gauss–Seidel-iteráció**; $\|B\|_2 \approx 0{,}6408$, $\|B\|_\infty = 0{,}75$.

Az első, „igazi” ILU-felbontás adja a leggyorsabb iterációt a három közül.

### Vizsgán (24. tétel)

- **a)** részleges LU-felbontás definíciója; az előállító algoritmus ((1) szétbontás, (2) elimináció); elégséges feltétel (SDD) a létezésre és egyértelműségre; az algoritmus helyességének bizonyítása ($L_{n-2}Q_{n-1} = Q_{n-1}$ trükk).
- **b)** az ILU-algoritmus levezetése, reziduumvektoros alak, nevezetes speciális esetek (Jacobi, Gauss–Seidel mint ILU; kétrétegű alak).

## Kapocs

- [[concepts/nummodi/lu-felbontas]] — a teljes LU-felbontás, amelynek ez a „ritkított” változata
- [[concepts/nummodi/haromszogmatrixok]] — $L_k$ eliminációs mátrixok, $\mathcal{L}_1$, $\mathcal{U}$
- [[concepts/nummodi/schur-komplementer]] — az SDD tulajdonság megmaradása a GE során
- [[concepts/nummodi/iteracios-modszerek-ler]] — $A = P - Q$ iterációs keret
- [[concepts/nummodi/jacobi-iteracio]] — $P = D$ speciális eset
- [[concepts/nummodi/gauss-seidel-iteracio]] — $P = D + L$ speciális eset
- [[concepts/nummodi/richardson-iteracio]] — $P = \tfrac1p I$ speciális eset
