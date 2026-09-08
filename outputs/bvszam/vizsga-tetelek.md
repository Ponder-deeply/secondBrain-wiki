---

title: Vizsgán legvalószínűbb tételek
subtitle: Bevezetés a számításelméletbe
author: bvszam wiki
date: 2026-06-04
---

# Vizsgán legvalószínűbb tételek
Nagy, neves tételek nem-triviális bizonyítással — a teljes `bizonyitando-tetelek.md` ✓-os részhalmaza.
---

## Tartalomjegyzék
**Reguláris nyelvek**
1. [[#Arden lemmája|Arden lemmája]]
2. [[#RegEx egyenértékű L3-mal|RegEx egyenértékű L3-mal]]
3. [[#Myhill–Nerode tétel|Myhill–Nerode tétel]]
4. [[#Faktorautomata egyértelűsége|Faktorautomata egyértelűsége]]
**Környezetfüggetlen nyelvek**
5. [[#Bar-Hillel pumpáló lemma|Bar-Hillel pumpáló lemma]]
6. [[#KF grammatika egyértelműsége eldönthetetlen|KF grammatika egyértelműsége eldönthetetlen]]
**Kiszámíthatóság**
7. [[#L1 egyenértékű LKA-val|L1 egyenértékű LKA-val]]
8. [[#L0 egyenértékű RE-vel|L0 egyenértékű RE-vel]]
9. [[#Univerzális Turing-gép létezik|Univerzális Turing-gép létezik]]
10. [[#Lu nem eldönthető|Lu nem eldönthető]]
11. [[#L eldönthető iff L és komplementere felismerhető|L eldönthető iff L és komplementere felismerhető]]
12. [[#Megállási probléma|Megállási probléma]]
13. [[#Rice tétele|Rice tétele]]
14. [[#PMP eldönthetetlen|PMP eldönthetetlen]]
**Bonyolultságelmélet**
15. [[#NP-teljes P-ben implikálja P=NP|NP-teljes P-ben implikálja P=NP]]
16. [[#Cook–Levin: SAT NP-teljes|Cook–Levin: SAT NP-teljes]]
17. [[#3SAT NP-teljes|3SAT NP-teljes]]
18. [[#2SAT polinom időben eldönthető|2SAT polinom időben eldönthető]]
19. [[#3-színezhetőség NP-teljes|3-színezhetőség NP-teljes]]
**Tárbonyolultság**
20. [[#Savitch tétele|Savitch tétele]]
21. [[#QSAT PSPACE-teljes|QSAT PSPACE-teljes]]
**Logaritmikus tárbonyolultság**
22. [[#ELÉRHETŐSÉG NL-teljes|ELÉRHETŐSÉG NL-teljes]]
23. [[#Immermann–Szelepcsényi: NL=coNL|Immermann–Szelepcsényi: NL=coNL]]
---

## Reguláris nyelvek ($\mathcal{L}_3$)
### Arden lemmája
**Tétel (Arden):** A $P = R + P \cdot Q$ egyenletnek $P$-re vonatkozó megoldása $P = R \cdot Q^*$. Ha $\varepsilon \notin Q$, ez az egyetlen megoldás.
**Fogalmak**: [[concepts/bvszam/regularis-kifejezesek|Reguláris kifejezések]], [[concepts/bvszam/formalis-nyelvek|Formális nyelvek]], [[concepts/bvszam/abece-es-szavak|Ábécé és szavak]]
**Bizonyítás:**
**(1) $P = R \cdot Q^*$ valóban megoldás:**
$$R + P \cdot Q = R + (R \cdot Q^*) \cdot Q = R + R \cdot (Q \cdot Q^*) = R \cdot (\varepsilon + Q \cdot Q^*) = R \cdot Q^* = P.$$
**(2) Egyediség (ha $\varepsilon \notin Q$):** Ismételt helyettesítéssel:
$$P = R + P \cdot Q = \cdots = R(\varepsilon + Q + \cdots + Q^n) + PQ^{n+1}.$$
Legyen $w \in P$ tetszőleges, $n = |w|$. Mivel $\varepsilon \notin Q$, a $Q^{n+1}$ minden szava legalább $n+1$ hosszú, így $w \notin PQ^{n+1}$. Ezért $w \in R(\varepsilon + Q + \cdots + Q^n) \subseteq RQ^*$.
Fordítva, ha $w \in RQ^*$, van $n$, hogy $w \in RQ^n \subseteq P$. Így csak $P = R \cdot Q^*$ lehetséges. $\square$
### RegEx egyenértékű L3-mal
**Tétel:** Minden reguláris kifejezés reguláris nyelvet jelöl, és megfordítva.
**Fogalmak**: [[concepts/bvszam/regularis-kifejezesek|Reguláris kifejezések]], [[concepts/bvszam/vda|VDA]], [[concepts/bvszam/regularis-normalforma|Reguláris normálforma]], [[concepts/bvszam/linearis-grammatika|Lineáris grammatika]], [[concepts/bvszam/chomsky-hierarchia|Chomsky-hierarchia]]
**Bizonyítás:**
**$\Rightarrow$ irány:** $\emptyset$, $\{\varepsilon\}$, $\{a\}$ regulárisak; $\mathcal{L}_3$ zárt a reguláris műveletekre.
**$\Leftarrow$ irány (konstrukció):** Legyen $N = \{A_1, \ldots, A_n\}$, $S = A_1$, minden szabály $A_i \to aA_j$ vagy $A_i \to \varepsilon$ alakú.
**Az $E^k_{i,j}$ halmazok definíciója** ($k$-megszorított levezetések):
$$E^k_{i,j} := \{u \in T^* \mid A_i \Rightarrow^* uA_j \text{ k-megszorítottan}\}$$
**Alaplépés ($k = 0$):**
- $i \neq j$: $E^0_{i,j} = \{a \mid A_i \to aA_j \in R\}$
- $i = j$: $E^0_{i,i} = \{\varepsilon\} \cup \{a \mid A_i \to aA_i \in R\}$
**Rekurzió** ($k \geq 1$):
$$E^k_{i,j} = E^{k-1}_{i,j} + E^{k-1}_{i,k} \cdot (E^{k-1}_{k,k})^* \cdot E^{k-1}_{k,j}$$
Indukcióval: minden $E^k_{i,j}$ jelölhető reguláris kifejezéssel.
**Végeredmény:** $L(G) = \bigcup_{i \in I_\varepsilon} E^n_{1,i}$, ahol $I_\varepsilon = \{i \mid A_i \to \varepsilon \in R\}$. $\square$
### Myhill–Nerode tétel
**Tétel:** $L \in \mathcal{L}_3 \iff |\{L_p\}_{p \in T^*}| < \infty$.
(Az $L$ nyelv $p$-re vonatkozó **maradéknyelve**: $L_p := \{v \mid pv \in L\}$.)
**Fogalmak**: [[concepts/bvszam/myhill-nerode|Myhill–Nerode]], [[concepts/bvszam/vda|VDA]], [[concepts/bvszam/chomsky-hierarchia|Chomsky-hierarchia]]
**Bizonyítás:**
**$\Rightarrow$:** Ha $A$ véges automata felismeri $L$-t, akkor $\{L_u\} \subseteq \{L(A,q)\}$, ami véges.
**$\Leftarrow$:** A Myhill–Nerode automata:
$$A^{MN}_L = \langle \{L_p\}_{p \in T^*}, T, \delta, L_\varepsilon, F \rangle, \quad \delta(L_p, t) = L_{pt}, \quad F = \{L_p \mid \varepsilon \in L_p\}$$
Ez véges (feltétel szerint) és elfogadja $L$-t. $\square$
**Következmény:** $A^{MN}_L$ állapotszáma $\leq$ bármely $L$-et felismerő VDA állapotszáma — tehát $A^{MN}_L$ az $L$ **minimális automatája**.
### Faktorautomata egyértelűsége
**Tétel:** Az $A/{\sim}$ faktorautomata ekvivalens $A$-val, redukált, és izomorfia erejéig az egyetlen ilyen összefüggő, redukált automata.
**Fogalmak**: [[concepts/bvszam/myhill-nerode|Myhill–Nerode]], [[concepts/bvszam/vda|VDA]], [[concepts/bvszam/l3-algoritmikus-problemak|L3 algoritmikus problémák]]
**Bizonyítás (egyediség):** Legyenek $A$ és $A'$ összefüggő, redukált, $L(A) = L(A')$. Definiáljuk:
$$\varphi(\delta(q_0, u)) := \delta'(q_0', u) \quad \text{minden } u \in T^*\text{-ra.}$$
- **Jól definiáltság és injektivitás:**
$$\delta(q_0, u) = \delta(q_0, v) \iff L(A, \delta(q_0,u)) = L(A, \delta(q_0,v)) \iff \delta'(q_0', u) = \delta'(q_0', v)$$
(az első és utolsó $A$/$A'$ redukáltságából, a középső $L(A) = L(A')$-ből következik).
- **Szürjektivitás:** $A'$ összefüggőségéből.
- **Izomorfizmus:** $\varphi(q_0) = q_0'$; $\varphi(F) = F'$; $\varphi(\delta(q,t)) = \delta'(\varphi(q), t)$. $\square$
---

## Környezetfüggetlen nyelvek ($\mathcal{L}_2$)
### Bar-Hillel pumpáló lemma
**Tétel:** Minden $L \in \mathcal{L}_2$-höz léteznek $p, q \in \mathbb{N}$, hogy minden $|w| > p$ szóhoz ($w \in L$) létezik $w = uxvyz$ felbontás, ahol:
- $|xvy| \leq q$
- $xy \neq \varepsilon$
- $ux^i vy^i z \in L$ minden $i \geq 0$-ra.
**Fogalmak**: [[concepts/bvszam/bar-hillel-lemma|Bar-Hillel lemma]], [[concepts/bvszam/chomsky-normalforma|CNF]], [[concepts/bvszam/kornyezetfuggetlen-grammatika|KF grammatika]], [[concepts/bvszam/levezetes-fa|Levezetési fa]]
**Bizonyítás (vázlat):** Legyen $G$ CNF grammatika $n$ nemterminálissal. $p = 2^{n-1}$, $q = 2^n$.
Ha $|w| > p$, a levezetési fa leghosszabb útján $> n$ csúcs van. A **skatulya-elv** alapján valamelyik $A$ nemterminális kétszer ismétlődik. Az utolsó ismétlő pár alapján:
$$S \Rightarrow^* uAz, \quad A \Rightarrow^* xAy, \quad A \Rightarrow^* v, \quad xy \neq \varepsilon.$$
Ekkor $ux^i vy^i z \in L$ minden $i \geq 0$-ra. $\square$
**Alkalmazás:** $\{a^n b^n c^n\} \notin \mathcal{L}_2$: az $xy$ legfeljebb 2 betűfajtát tartalmaz, így $ux^0vy^0z$-ban valamelyikből kevesebb lesz — ellentmondás.
### KF grammatika egyértelműsége eldönthetetlen
**Tétel (2.30.):** A KF grammatikák egyértelműsége eldönthetetlen.
**Fogalmak**: [[concepts/bvszam/kornyezetfuggetlen-grammatika|KF grammatika]], [[concepts/bvszam/post-megfelelkezesi-problema|PMP]], [[concepts/bvszam/levezetes-fa|Levezetési fa]], [[concepts/bvszam/eldonthetetlen-problemak|Eldönthetetlen problémák]]
**Bizonyítás (visszavezetés PMP-ből):** Adott $D$ PMP-példányból ($u_i, v_i \in \Sigma^+$) építhető egy $G$ grammatika, amely pontosan akkor nem egyértelmű, ha $D$-nek van megoldása. $G$-be két párhuzamos szabályrendszert teszünk, $G_A$-t az $u_i$-kre és $G_B$-t a $v_i$-kre; egy $w$ szónak pontosan akkor van kétféle bal-levezetése, ha az index-rész ugyanazt a dominósorozatot kódolja felül és alul. Mivel PMP eldönthetetlen, az egyértelműség is az. $\square$
---

## Kiszámíthatóság
### L1 egyenértékű LKA-val
**Tétel:** $\mathcal{L}_1 =$ LKA által felismert nyelvek osztálya.
**Fogalmak**: [[concepts/bvszam/linearis-korlatolt-automata|LKA]], [[concepts/bvszam/kornyezetfuggo-nyelvek|Környezetfüggő nyelvek]], [[concepts/bvszam/chomsky-hierarchia|Chomsky-hierarchia]]
**Bizonyítás:**
**$\mathcal{L}_1 \to \text{LKA}$:** Minden hossz-nemcsökkentő grammatikához megadható LKA, amely a levezetést nemdeterminisztikusan szimulálja. Mivel a szabályok hossz-nemcsökkentők, az aktuális mondatforma sosem hosszabb az inputnál.
**$\text{LKA} \to \mathcal{L}_1$:** Az LKA konfigurációit kódoló grammatikából 1-típusú grammatika konstruálható. $\square$
### L0 egyenértékű RE-vel
**Tétel:** $L \in \mathcal{L}_0 \iff L \in \mathrm{RE}$.
**Fogalmak**: [[concepts/bvszam/l0-re-ekvivalencia|L0 = RE]], [[concepts/bvszam/turing-gep|Turing-gép]], [[concepts/bvszam/nemdeterminisztikus-turing-gep|NTG]], [[concepts/bvszam/chomsky-hierarchia|Chomsky-hierarchia]]
**Bizonyítás:**
**$\mathcal{L}_0 \subseteq \mathrm{RE}$:** Minden $G$ 0-típusú grammatikához megadható $L(G)$-t felismerő NTG (3-szalagos). Az NTG nemdeterminisztikusan alkalmaz szabályokat $S$-ből; ha a mondatforma egyenlő az inputtal, elfogad.
**$\mathrm{RE} \subseteq \mathcal{L}_0$:** Minden $M$ DTG-hez megkonstruálható $G$ 0-típusú grammatika, amely a kódolt konfigurációsorozatot generálja. $\square$
### Univerzális Turing-gép létezik
**Tétel:** $L_u \in \mathrm{RE}$, ahol $L_u = \{\langle M, w \rangle \mid w \in L(M)\}$.
**Fogalmak**: [[concepts/bvszam/univerzalis-turing-gep|UTG]], [[concepts/bvszam/turing-gep-kodolas|TG kódolása]], [[concepts/bvszam/tobb-szalagos-turing-gep|k-szalagos TG]], [[concepts/bvszam/r-re-nyelvek|R és RE]]
**Bizonyítás (4-szalagos UTG):**
| Szalag | Tartalom |
|--------|----------|
| 1. (csak olvasható) | $\langle M, w \rangle$ |
| 2. | $M$ aktuális szalagtartalma és fejpozíciója |
| 3. | $M$ aktuális állapota |
| 4. | segédszalag |
$U$ működése: ellenőrzi a kódolást, $w$-t a 2. szalagra másolja, majd lépésenként szimulálja $M$-et az 1. szalagról olvasva a $\delta$-átmeneteket. Ha $M$ megáll, $U$ is megáll ugyanúgy.
Ha $M$ nem áll meg $w$-n, $U$ sem áll meg — ezért $U$ csak **felismeri** $L_u$-t, nem **dönti el**. $\square$
### Lu nem eldönthető
**Tétel:** $L_u \notin \mathrm{R}$.
**Fogalmak**: [[concepts/bvszam/r-re-nyelvek|R és RE]], [[concepts/bvszam/eldonthetetlen-problemak|Eldönthetetlen problémák]], [[concepts/bvszam/visszavezetes|Visszavezetés]], [[concepts/bvszam/turing-gep-kodolas|TG kódolása]]
**Bizonyítás (diagonalizáció):** Tegyük fel indirekt, hogy $D$ TG eldönti $L_u$-t. Definiáljuk $D'$-t: $D'$ az $\langle M \rangle$ bemeneten futtatja $D$-t az $\langle M, \langle M \rangle \rangle$ bemeneten, majd **megfordítja** a választ.
$D'$-t saját kódolásán futtatva:
$$\langle D' \rangle \in L(D') \iff D \text{ elutasítja } \langle D', \langle D' \rangle \rangle \iff \langle D' \rangle \notin L(D').$$
Ellentmondás. $\square$
**Összefoglalva:** $L_u \in \mathrm{RE} \setminus \mathrm{R}$.
### L eldönthető iff L és komplementere felismerhető
**Tétel:** $L \in \mathrm{R} \iff L \in \mathrm{RE}$ és $\bar{L} \in \mathrm{RE}$.
**Fogalmak**: [[concepts/bvszam/r-re-nyelvek|R és RE]], [[concepts/bvszam/visszavezetes|Visszavezetés]], [[concepts/bvszam/zartsagi-tulajdonsagok|Zártsági tulajdonságok]]
**Bizonyítás:**
**$\Rightarrow$:** Ha $L \in \mathrm{R}$: $L \in \mathrm{RE}$ triviálisan; $\bar{L} \in \mathrm{R} \subseteq \mathrm{RE}$ (elfogadó/elutasító állapotok felcserélésével).
**$\Leftarrow$:** Legyen $M_1$ az $L$-t, $M_2$ a $\bar{L}$-t felismerő TG. Egy $M'$ gép **felváltva** szimulál egy-egy lépést $M_1$-ből és $M_2$-ből. Mivel $L \cup \bar{L} = \Sigma^*$, valamelyik véges lépésen belül elfogad — $M'$ mindig megáll. $\square$
**Következmény:** $\mathrm{RE}$ nem zárt komplementerre ($\overline{L_u} \notin \mathrm{RE}$).
### Megállási probléma
**Tétel:** $L_h \in \mathrm{RE} \setminus \mathrm{R}$, ahol $L_h = \{\langle M, w \rangle \mid M \text{ megáll } w\text{-n}\}$.
**Fogalmak**: [[concepts/bvszam/megallasi-problema|Megállási probléma]], [[concepts/bvszam/visszavezetes|Visszavezetés]], [[concepts/bvszam/r-re-nyelvek|R és RE]]
**Bizonyítás:**
**$L_h \notin \mathrm{R}$ — visszavezetés $L_u \leq L_h$:** Adott $\langle M, w \rangle$-hez konstruálunk $M'$-t:
1. Szimulálja $M$-et $w$-n.
2. Ha $M$ elfogad: $M'$ elfogad.
3. Ha $M$ elutasít: $M'$ **végtelen ciklusba lép**.
Ekkor $\langle M, w \rangle \in L_u \iff \langle M', w \rangle \in L_h$. Mivel $L_u \notin \mathrm{R}$, $L_h \notin \mathrm{R}$.
**$L_h \in \mathrm{RE}$ — visszavezetés $L_h \leq L_u$:** $M'$ = $M$ minden elutasító átmenetét elfogadóra irányítva. Ekkor $M$ megáll $w$-n $\iff$ $M'$ elfogadja $w$-t. Mivel $L_u \in \mathrm{RE}$, $L_h \in \mathrm{RE}$. $\square$
### Rice tétele
**Tétel (Rice):** Ha $\mathcal{P} \subseteq \mathrm{RE}$ nemtriviális tulajdonság ($\mathcal{P} \neq \emptyset$, $\mathcal{P} \neq \mathrm{RE}$), akkor $L_\mathcal{P} \notin \mathrm{R}$, ahol $L_\mathcal{P} = \{\langle M \rangle \mid L(M) \in \mathcal{P}\}$.
**Fogalmak**: [[concepts/bvszam/rice-tetel|Rice tétele]], [[concepts/bvszam/visszavezetes|Visszavezetés]], [[concepts/bvszam/eldonthetetlen-problemak|Eldönthetetlen problémák]], [[concepts/bvszam/r-re-nyelvek|R és RE]]
**Bizonyítás:**
**1. eset: $\emptyset \notin \mathcal{P}$.** Legyen $L \in \mathcal{P}$, $M_L$ az azt felismerő TG. Megadjuk $L_u \leq L_\mathcal{P}$: $\langle M, w \rangle$-re konstruálunk $M'$-t, amely $x$-en:
- szimulálja $M$-et $w$-n,
- ha $M$ elfogad: $L(M') = L$ (szimulálja $M_L$-t $x$-en),
- ha $M$ nem fogad el: $L(M') = \emptyset$.
$$\langle M, w \rangle \in L_u \iff L(M') = L \in \mathcal{P} \iff \langle M' \rangle \in L_\mathcal{P}.$$
**2. eset: $\emptyset \in \mathcal{P}$.** Az 1. esetet $\overline{\mathcal{P}}$-re alkalmazzuk: $L_{\overline{\mathcal{P}}} = \overline{L_\mathcal{P}} \notin \mathrm{R}$, tehát $L_\mathcal{P} \notin \mathrm{R}$. $\square$
### PMP eldönthetetlen
**Tétel:** $\mathrm{PMP} \notin \mathrm{R}$.
**Fogalmak**: [[concepts/bvszam/post-megfelelkezesi-problema|PMP]], [[concepts/bvszam/visszavezetes|Visszavezetés]], [[concepts/bvszam/eldonthetetlen-problemak|Eldönthetetlen problémák]]
**Bizonyítás:** Két lépés: $L_u \leq \mathrm{MPMP} \leq \mathrm{PMP}$.
**$\mathrm{MPMP} \leq \mathrm{PMP}$:** Adott $D = \{[\tfrac{u_i}{v_i}]\}$-hez $D'$-t konstruálunk $*$ és $\#$ szimbólumokkal:
$$D' = \left\{ \left[\tfrac{*u_1}{*v_1*}\right], \left[\tfrac{*u_1}{v_1*}\right], \left[\tfrac{*u_2}{v_2*}\right], \ldots, \left[\tfrac{*u_n}{v_n*}\right], \left[\tfrac{*\#}{\#}\right] \right\}.$$
A $*$ jelek kikényszerítik, hogy $D'$ megoldása az első dominóval kezdődjön.
**$L_u \leq \mathrm{MPMP}$:** Adott $M$ TG-hez és $w$-hez olyan $D$ dominókészletet konstruálunk, amelynek megoldása $M$ egymást követő konfigurációit kódolja $\#$-cal elválasztva:
1. **Kezdő dominó:** $\left[\tfrac{\#}{\#q_0 a_1 \ldots a_n\#}\right]$
2. **Átmenet-dominók:** minden $\delta$-átmenethez
3. **Másoló dominók:** $\left[\tfrac{a}{a}\right]$, $\left[\tfrac{\#}{\#}\right]$, $\left[\tfrac{\#}{\sqcup\#}\right]$
4. **Záró dominók:** $\left[\tfrac{q_i\#\#}{\#}\right]$ zár
**Lánc:** $L_u \leq \mathrm{MPMP} \leq \mathrm{PMP}$, $L_u \notin \mathrm{R}$ $\Rightarrow$ $\mathrm{PMP} \notin \mathrm{R}$. $\square$
---

## Bonyolultságelmélet (P, NP)
### NP-teljes P-ben implikálja P=NP
**Tétel:** Ha $L$ NP-teljes és $L \in \mathrm{P}$, akkor $\mathrm{P} = \mathrm{NP}$.
**Fogalmak**: [[concepts/bvszam/np-teljesseg|NP-teljesség]], [[concepts/bvszam/bonyolultsagelmeleti-osztalyok|P, NP osztályok]], [[concepts/bvszam/visszavezetes|Visszavezetés]]
**Bizonyítás:** Tetszőleges $L' \in \mathrm{NP}$-re $L' \leq_p L$ (NP-teljesség), és mivel P zárt $\leq_p$-re, $L' \in \mathrm{P}$. Tehát $\mathrm{NP} \subseteq \mathrm{P}$, és $\mathrm{P} \subseteq \mathrm{NP}$ triviális. $\square$
### Cook–Levin: SAT NP-teljes
**Tétel:** SAT NP-teljes.
**Fogalmak**: [[concepts/bvszam/cook-levin-bizonyitas|Cook–Levin]], [[concepts/bvszam/np-teljesseg|NP-teljesség]], [[concepts/bvszam/itelet-kalkulus|Ítéletkalkulus]], [[concepts/bvszam/nemdeterminisztikus-turing-gep|NTG]]
**Bizonyítás:** Megmutatjuk, hogy minden $L \in \mathrm{NP}$ visszavezethető SAT-ra polinom időben — **táblakódolással**.
Legyen $M$ egy $p(n)$ lépésidejű NTG, amely $L$-et dönti el. Az $M$ $w$ bemenetű számítása felírható egy $(p(n)+1) \times (2p(n)+3)$ méretű **tableau** segítségével. Változók: $x_{i,j,s}$ — igaz, ha a tábla $(i,j)$ cellájában $s \in Q \cup \Gamma \cup \{\#\}$ áll.
$$\varphi_w := \varphi_0 \land \varphi_{start} \land \varphi_{move} \land \varphi_{accept}$$
- **$\varphi_0$:** minden cellában pontosan egy szimbólum:
$$\varphi_0 := \bigwedge_{i,j} \left( \bigvee_{s} x_{i,j,s} \right) \land \bigwedge_{i,j} \bigwedge_{s \neq t} (\neg x_{i,j,s} \lor \neg x_{i,j,t})$$
- **$\varphi_{start}$:** az első sor a $w$ kezdőkonfigurációját kódolja.
- **$\varphi_{move}$:** egymást követő sorpárok érvényes TG-lépésnek felelnek meg. Minden $(i,j)$-re $\psi_{i,j}$ tiltja az „illegális 2×3-as ablakokat":
$$\psi_{i,j} := \bigwedge_{\text{illegális}} \left( \neg x_{i,j-1,b_1} \lor \neg x_{i,j,b_2} \lor \neg x_{i,j+1,b_3} \lor \neg x_{i+1,j-1,b_4} \lor \neg x_{i+1,j,b_5} \lor \neg x_{i+1,j+1,b_6} \right)$$
- **$\varphi_{accept}$:** az utolsó sorban van elfogadó állapot:
$$\varphi_{accept} = \bigvee_{j} x_{p(n)+1,\, j,\, q_f}$$
Méret: $O(p^2(n))$ — polinom időben megkonstruálható. $w \in L \iff \varphi_w$ kielégíthető. $\square$
### 3SAT NP-teljes
**Tétel:** 3SAT NP-teljes.
**Fogalmak**: [[concepts/bvszam/ksat-es-3sat|kSAT és 3SAT]], [[concepts/bvszam/np-teljesseg|NP-teljesség]], [[concepts/bvszam/visszavezetes|Visszavezetés]]
**Bizonyítás — SAT $\leq_p$ 3SAT (klóz-felosztás):**
| Eredeti klóz | 3KNF megfelelő |
|---|---|
| $l$ | $l \lor x \lor y,\ l \lor x \lor \neg y,\ l \lor \neg x \lor y,\ l \lor \neg x \lor \neg y$ |
| $l_1 \lor l_2$ | $l_1 \lor l_2 \lor x,\ l_1 \lor l_2 \lor \neg x$ |
| $l_1 \lor l_2 \lor l_3$ | változatlan |
| $l_1 \lor l_2 \lor l_3 \lor l_4$ | $l_1 \lor l_2 \lor x,\ \neg x \lor l_3 \lor l_4$ |
| $l_1 \lor \cdots \lor l_n\ (n \geq 5)$ | $l_1 \lor l_2 \lor x_1,\ \neg x_1 \lor l_3 \lor x_2,\ \ldots,\ \neg x_{n-3} \lor l_{n-1} \lor l_n$ |
A transzformáció polinom idejű és kielégíthetőséget megőriz. Cook–Levin + terjesztés $\Rightarrow$ 3SAT NP-teljes. $\square$
### 2SAT polinom időben eldönthető
**Tétel:** $\mathrm{2SAT} \in \mathrm{P}$.
**Fogalmak**: [[concepts/bvszam/2sat|2SAT]], [[concepts/bvszam/bonyolultsagelmeleti-osztalyok|P, NP osztályok]], [[concepts/bvszam/itelet-kalkulus|Ítéletkalkulus]]
**Bizonyítás (implikációs gráf):** Konstruáljuk $G_\varphi$-t:
- **Csúcsok:** $2n$ — minden $x_i$-hez $x_i$ és $\neg x_i$.
- **Élek:** $l_i \lor l_j$ klózhoz $(\neg l_i \to l_j)$ és $(\neg l_j \to l_i)$.
**Kielégíthetőségi feltétel:** $\varphi$ kielégíthető $\iff$ egyetlen $i$-re sem kerül $x_i$ és $\neg x_i$ ugyanabba az erősen összefüggő komponensbe (EÖK).
- Ha $x_i$ és $\neg x_i$ ugyanabban az EÖK-ban: ellentmondás.
- Ha nem: $x_i = \mathrm{igaz}$, ha $\neg x_i$ EÖK-ja topologikusan előbb jön.
$G_\varphi$ felépítése és Tarjan-algoritmus: $O(n + m)$ — lineáris idő. $\square$
### 3-színezhetőség NP-teljes
**Tétel:** 3SZÍNEZÉS NP-teljes.
**Fogalmak**: [[concepts/bvszam/3szinezes|3-színezés]], [[concepts/bvszam/np-teljesseg|NP-teljesség]], [[concepts/bvszam/ksat-es-3sat|kSAT és 3SAT]], [[concepts/bvszam/graf-alapfogalmak|Gráf alapfogalmak]]
**Bizonyítás — 3SAT $\leq_p$ 3SZÍNEZÉS:** $\varphi$ 3-CNF formulából $G_\varphi$-t építünk:
**Változócsúcsok:** minden $x_i$-hez $x_i$ és $\bar{x}_i$ csúcs, köztük éllel.
**Paletta-csúcsok:** $A$ (igaz/zöld), $B$ (hamis/piros), $\top$ (alap/kék) — egymással klikket alkotnak. Minden $x_i$–$\bar{x}_i$ pár kötve van $\top$-hoz, tehát egyikük $A$, másikuk $B$ szín lesz.
**Klózcsúcsok:** minden klózhoz egy ötszög-szerkezet a 3 literál csúcsaiból és $B$-ből — ha mindhárom literál piros, az ötszög nem 3-színezhető.
**Helyesség:**
- $\varphi$ kielégíthető $\Rightarrow$ $G_\varphi$ 3-színezhető: igaz literál = zöld, az ötszög kiterjeszthető.
- $G_\varphi$ 3-színezhető $\Rightarrow$ $\varphi$ kielégíthető: az ötszög kikényszeríti, hogy minden klózban van zöld literál.
$|G_\varphi| = O(|\varphi|)$ — polinom idejű visszavezetés. $\square$
---

## Tárbonyolultság
### Savitch tétele
**Tétel:** Ha $f(n) \geq \log n$, akkor $\mathrm{NSPACE}(f(n)) \subseteq \mathrm{SPACE}(f^2(n))$.
**Fogalmak**: [[concepts/bvszam/tarbonyolultsag-pspace|Tárbonyolultság / PSPACE]], [[concepts/bvszam/nemdeterminisztikus-turing-gep|NTG]], [[concepts/bvszam/bonyolultsagelmeleti-osztalyok|P, NP osztályok]]
**Bizonyítás (vázlat):** Egy $O(f(n))$ tárú NTG $M$ konfigurációi a $w$ bemeneten egy $C_w$ **konfigurációs gráfot** alkotnak. $w$ elfogadása $\iff$ $C_w$-ben van út $c_{kezdő} \to c_{elfogadó}$.
Definiáljuk $\mathrm{ELÉR}(c_1, c_2, t)$ predikátumot rekurzívan **középső konfiguráció keresésével:**
$$\mathrm{ELÉR}(c_1,c_2,t) \iff \exists c:\ \mathrm{ELÉR}(c_1,c,\lceil t/2\rceil) \land \mathrm{ELÉR}(c,c_2,\lceil t/2\rceil).$$
Rekurzió mélysége: $O(f(n))$; minden szinten $O(f(n))$ tár $\Rightarrow$ összesen $O(f^2(n))$. $\square$
**Következmény:** $\mathrm{PSPACE} = \mathrm{NPSPACE}$.
### QSAT PSPACE-teljes
**Tétel:** QSAT PSPACE-teljes, ahol $\mathrm{QSAT} = \{\langle\varphi\rangle \mid \varphi \text{ igaz teljesen kvantifikált Boole-formula}\}$.
**Fogalmak**: [[concepts/bvszam/tarbonyolultsag-pspace|Tárbonyolultság / PSPACE]], [[concepts/bvszam/elsorendu-logika|Elsőrendű logika]], [[concepts/bvszam/itelet-kalkulus|Ítéletkalkulus]], [[concepts/bvszam/np-teljesseg|NP-teljesség]]
**Bizonyítás:**
**QSAT $\in$ PSPACE:** Az $\mathrm{ÉRTÉK}(\varphi)$ függvény rekurzív kiszámítása: $\varphi = Qx\psi$ esetén kiszámoljuk $\psi^i$ és $\psi^h$ értékét, majd $Q$ szerint kombináljuk. Rekurzió mélysége = változók száma; minden szinten 1 bit tár $\Rightarrow$ lineáris tár.
**QSAT PSPACE-nehéz:** Tetszőleges $L \in \mathrm{PSPACE}$-re egy $\varphi$ TKBF-et konstruálunk ($w \in L \iff \langle\varphi\rangle \in \mathrm{QSAT}$). A $\varphi_{C,D,t}$ formula Savitch felezésével de **univerzális kvantorral** a középső konfigurációra:
$$\varphi_{C,D,t} = \exists M\,\forall C_1\forall C_2\big((C_1{=}C \land C_2{=}M) \lor (C_1{=}M \land C_2{=}D) \to \varphi_{C_1,C_2,\lceil t/2\rceil}\big).$$
A $\forall$ kvantor megakadályozza a formula méretének duplázódását — a teljes $\varphi$ polinom méretű. $\square$
---

## Logaritmikus tárbonyolultság (L, NL)
### ELÉRHETŐSÉG NL-teljes
**Tétel:** ELÉRHETŐSÉG NL-teljes, ahol ELÉRHETŐSÉG: adott $G=(V,E)$ irányított gráf és $s,t$, van-e út $s$-ből $t$-be.
**Fogalmak**: [[concepts/bvszam/logaritmikus-tarbonyolultsag|L, NL]], [[concepts/bvszam/graf-alapfogalmak|Gráf alapfogalmak]], [[concepts/bvszam/visszavezetes|Visszavezetés]]
**Bizonyítás:**
**$\in$ NL:** Egy NTG az aktuális csúcsot és egy lépésszámlálót tárol $O(\log|V|)$ tárral; nemdeterminisztikusan lép $s$-ből, $|V|$ lépésig.
**NL-nehéz:** Tetszőleges $L \in \mathrm{NL}$-re az $L$-t eldöntő $O(\log n)$ tárú NTG $M$ **konfigurációs gráfja** logaritmikus tárral megkonstruálható (csúcs = konfiguráció, él = $\delta$-átmenet), és $u \in L \iff$ van út $c_{kezdő}$-ből $c_{elfogadó}$-ba. $\square$
**Következmény:** $\mathrm{NL} \subseteq \mathrm{P}$.
### Immermann–Szelepcsényi: NL=coNL
**Tétel:** $\mathrm{NL} = \mathrm{coNL}$.
**Fogalmak**: [[concepts/bvszam/logaritmikus-tarbonyolultsag|L, NL]], [[concepts/bvszam/np-koztes-es-conp|coNP]], [[concepts/bvszam/visszavezetes|Visszavezetés]]
**Bizonyítás:** Megmutatjuk, hogy $\overline{\mathrm{ELÉRHETŐSÉG}} \in \mathrm{NL}$.
Az ötlet: az $s$-ből $\leq i$ lépésben elérhető csúcsok $d_i$ számát induktívan kiszámítjuk ($d_0 = 1$). $d_{i+1}$-hez minden csúcsra nemdeterminisztikusan **megsejtjük** az elérhetőségét, majd útkereséssel **ellenőrizzük** — közben számoljuk, hogy a talált elérhető csúcsok száma eléri-e $d_i$-t. Végül $d_{|V|}$ ismeretében: $t$ nem elérhető $\iff$ az NTG végig tudja sorolni $d_{|V|}$ elérhető csúcsot $t$ nélkül.
Tár: $O(\log|V|)$ $\Rightarrow$ $\overline{\mathrm{ELÉRHETŐSÉG}} \in \mathrm{NL}$, tehát $\mathrm{NL} = \mathrm{coNL}$. $\square$
