#flashcards/bvszam/regularis-nyelvek
## 1. Mi a véges determinisztikus automata (VDA) formális definíciója?
?
$$A = \langle Q, T, \delta, q_0, F \rangle$$
ahol $Q$ az állapotok véges, nemüres halmaza; $T$ az inputábécé; $\delta : Q \times T \to Q$ az átmenetfüggvény (minden $(q,a)$ párra pontosan egy következő állapot); $q_0 \in Q$ a kezdőállapot; $F \subseteq Q$ az elfogadó állapotok halmaza.
---

## 2. Hogyan definiáljuk a VDA kiterjesztett átmenetfüggvényét, és mikor fogad el a VDA egy szót?
?
$$\hat{\delta}(q, \varepsilon) := q, \qquad \hat{\delta}(q, xa) := \delta(\hat{\delta}(q, x), a)$$
Az $u$ szót $A$ elfogadja, ha $\hat{\delta}(q_0, u) \in F$. Az elfogadott nyelv: $L(A) = \{u \in T^* \mid \hat{\delta}(q_0, u) \in F\}$.
---

## 3. Miért zárt a $\mathcal{L}_3$ osztály a komplementer képzésre, és hogyan épül fel a komplementer automata?
?
Ha $A = \langle Q, T, \delta, q_0, F \rangle$ felismeri $L$-t, akkor $A' = \langle Q, T, \delta, q_0, Q \setminus F \rangle$ felismeri $\bar{L}$-t. Ez azért működik, mert a VDA teljes és determinisztikus: minden szóra pontosan egy végállapot adódik, amelyet a korábbi elfogadó állapotokból éppen a nem elfogadók vesznek át.
---

## 4. Mi a véges nemdeterminisztikus automata (VNDA) formális definíciója, és miben tér el a VDA-tól?
?
$$A = \langle Q, T, \delta, Q_0, F \rangle$$
ahol $\delta : Q \times T \to \mathcal{P}(Q)$ halmazértékű átmenetfüggvény, $Q_0 \subseteq Q$ a kezdőállapotok halmaza (több is lehet). Az $u$ szót $A$ elfogadja, ha létezik $q_0 \in Q_0$ és $p \in F$, amelyre $q_0 u \Rightarrow_A^* p$. Elakadás ($\delta(q,a) = \emptyset$) az adott ágon elutasítást jelent. A VDA speciális eset: $|\delta(q,a)| = 1$ és $|Q_0| = 1$ minden $(q,a)$-ra.
---

## 5. Hogyan determinizálunk egy VNDA-t (hatványhalmaz-konstrukció)?
?
Adott $A = \langle Q, T, \delta, Q_0, F \rangle$ VNDA-ból az ekvivalens VDA:
$$Q' = \mathcal{P}(Q), \quad q_0' = Q_0, \quad F' = \{q' \in Q' \mid q' \cap F \neq \emptyset\}, \quad \delta'(q', a) = \bigcup_{q \in q'} \delta(q,a)$$
Az állapotok száma legfeljebb $2^{|Q|}$; a gyakorlatban csak az elérhető részhalmazokat kell felvenni.
---

## 6. Hogyan épül fel a 3-as típusú grammatikából VNDA?
?
Legyen $G = \langle N, T, P, S \rangle$ Chomsky-normálformájú reguláris grammatika ($X \to aY$ és $X \to \varepsilon$ szabályok). Ekkor:
$$Q = N, \quad Q_0 = \{S\}, \quad F = \{Z \mid Z \to \varepsilon \in P\}, \quad Xa \to Y \in M_\delta \iff X \to aY \in P$$
---

## 7. Hogyan épül fel VNDA-ból 3-as típusú grammatika?
?
A VNDA átmenetszabályaiból bal-lineáris grammatika adódik, amelynek ekvivalens jobb-lineáris változata felírható. Legyen $G = \langle N, T, P, S \rangle$, ahol $N = Q \cup \{S\}$. A $P$ szabályok:
1. $p \to a \in P \iff q_0 a \to p \in M_\delta$ valamely $q_0 \in Q_0$-ra
2. $p \to qa \in P \iff qa \to p \in M_\delta$
3. $S \to p \in P \iff p \in F$
4. $S \to \varepsilon \in P \iff Q_0 \cap F \neq \emptyset$
---

## 8. Mi a reguláris kifejezés rekurzív definíciója?
?
Legyenek $V$ és $V' = \{\emptyset, \varepsilon, \cdot, +, *, (, )\}$ diszjunkt ábécék. A $V$ feletti reguláris kifejezések:
1. $\emptyset$ — reguláris kifejezés
2. $\varepsilon$ — reguláris kifejezés
3. $a \in V$ — reguláris kifejezés
4. Ha $R$ reguláris kifejezés, akkor $R^*$ is az
5. Ha $Q, R$ reguláris kifejezések, akkor $(Q \cdot R)$ is az
6. Ha $Q, R$ reguláris kifejezések, akkor $(Q + R)$ is az
Precedencia: $* > \cdot > +$.
---

## 9. Mit jelöl az $L(R)$ jelölés, és mi a reguláris kifejezések szemantikája?
?
| Kifejezés | Jelölt nyelv |
|---|---|
| $L(\emptyset)$ | $\emptyset$ |
| $L(\varepsilon)$ | $\{\varepsilon\}$ |
| $L(a)$ | $\{a\}$ |
| $L(R^*)$ | $L(R)^*$ |
| $L(Q \cdot R)$ | $L(Q) \cdot L(R)$ |
| $L(Q + R)$ | $L(Q) \cup L(R)$ |
---

## 10. Mondja ki Arden tételét, és mit jelent, ha $\varepsilon \notin Q$?
?
**Arden tétele:** A $P = R + P \cdot Q$ egyenletnek $P$-re vonatkozó megoldása $P = R \cdot Q^*$. Ha $\varepsilon \notin Q$, ez az **egyetlen** megoldás.
Bizonyítás vázlata: (1) $P = R \cdot Q^*$ behelyettesítve teljesíti az egyenletet. (2) Ha $\varepsilon \notin Q$, ismételt helyettesítéssel $P \subseteq RQ^*$ és $RQ^* \subseteq P$, tehát egyenlőség áll.
---

## 11. Hogyan vezethető le reguláris kifejezés egy reguláris grammatikából ($E^k_{i,j}$ módszer)?
?
Legyen $N = \{A_1, \ldots, A_n\}$, $S = A_1$. Definiáljuk:
$$E^k_{i,j} := \{u \in T^* \mid \text{létezik } A_i \Rightarrow^* uA_j \text{ } k\text{-megszorított levezetés}\}$$
**Alaplépés ($k=0$):** $E^0_{i,j} = \{a \in T \mid A_i \to aA_j \in R\}$ ($i \neq j$); $E^0_{i,i} = \{\varepsilon\} \cup \{a \mid A_i \to aA_i \in R\}$.
**Rekurzió ($k \geq 1$):**
$$E^k_{i,j} = E^{k-1}_{i,j} + E^{k-1}_{i,k} \cdot (E^{k-1}_{k,k})^* \cdot E^{k-1}_{k,j}$$
**Végeredmény:** $L(G) = \bigcup_{i \in I_\varepsilon} E^n_{1,i}$, ahol $I_\varepsilon = \{i \mid A_i \to \varepsilon \in R\}$.
---

## 12. Hogyan épül fel reguláris kifejezésből VDA?
?
Három lépésben:
1. **Általánosított $\varepsilon$-VNDA** felépítése ($Q \xrightarrow{R} Q'$ típusú átmenetekkel), rekurzív lebontással.
2. **$\varepsilon$-átmenetek eliminálása:** $H(q) = \{q' \mid q \xRightarrow{*}_\varepsilon q'\}$, majd $\delta'(q,a)$ és $F'$ meghatározása.
3. **VNDA determinizálása** hatványhalmaz-konstrukcióval.
---

## 13. Mit jelent a reguláris nyelv és a 3-as típusú grammatika ekvivalenciája?
?
**Tétel:** Minden reguláris kifejezés reguláris (3-as típusú) nyelvet jelöl, és megfordítva.
$\Rightarrow$ irány: $\emptyset$, $\{\varepsilon\}$, $\{a\}$ regulárisak; $\mathcal{L}_3$ zárt a reguláris műveletekre (unió, konkatenáció, csillag).
$\Leftarrow$ irány: Grammatikából az $E^k_{i,j}$ módszerrel reguláris kifejezés vezethető le. Összességében $\mathcal{L}_3$ = reguláris kifejezések által jelölt nyelvek = VDA/VNDA által felismert nyelvek.
---

## 14. Mi az $L$ nyelv $p$ szóra vonatkozó maradéknyelve, és milyen tulajdonságai vannak?
?
$$L_p := \{v \mid pv \in L\}$$
Tulajdonságok:
- $(L_p)_q = L_{pq}$
- $L_\varepsilon = L$
- $\varepsilon \in L_p \iff p \in L$
Egy $A$ VDA $q$ állapotának maradéknyelve: $L(A, q) := \{v \mid \delta(q, v) \in F\}$. Összefüggés: $L_u = L(A, \delta(q_0, u))$.
---

## 15. Mondja ki a Myhill–Nerode tételt!
?
**Tétel:** $L \in \mathcal{L}_3 \iff |\{L_p\}_{p \in T^*}| < \infty$
(L pontosan akkor reguláris, ha véges sok különböző maradéknyelve van.)
$\Rightarrow$: Ha $A$ véges automata felismeri $L$-t, akkor $\{L_u\} \subseteq \{L(A,q)\}$, ami véges.
$\Leftarrow$: A **Myhill–Nerode automata** $A^{MN}_L = \langle \{L_p\}_{p \in T^*}, T, \delta, L_\varepsilon, F \rangle$, ahol $\delta(L_p, t) = L_{pt}$ és $F = \{L_p \mid \varepsilon \in L_p\}$. Ez véges, és elfogadja pontosan $L$-t.
---

## 16. Miért minimális a Myhill–Nerode automata?
?
**Következmény:** $A^{MN}_L$ állapotszáma kisebb vagy egyenlő, mint bármely $L$-et felismerő VDA állapotszáma.
Bizonyítás: Ha $A$ felismeri $L$-t, akkor minden $L_u$ maradéknyelv megfelel az $A$ valamelyik állapotának ($\delta(q_0, u)$). Tehát az $A$ állapotai lefedik a maradéknyelveket, így $|Q| \geq |\{L_p\}|$.
---

## 17. Mi az $i$-megkülönböztethetőség ($\sim_i$), és hogyan használjuk VDA minimalizálásához?
?
$q \sim_i q'$, ha minden $|u| \leq i$ hosszú szóra $\delta(q,u) \in F \iff \delta(q',u) \in F$.
- $q \sim_0 q'$: mindkettő elfogadó, vagy mindkettő nem elfogadó.
- $q \sim_{i+1} q'$: $q \sim_i q'$ és minden $t \in T$-re $\delta(q,t) \sim_i \delta(q',t)$.
A sorozat legkésőbb $|Q|-1$ lépésnél stabilizálódik: $\sim = \sim_{i_0}$. Az ekvivalenciaosztályok alkotják a minimális (faktor)automata állapotait.
---

## 18. Mi a faktorautomata, és milyen tételt mondunk ki róla?
?
Az $A/{\sim}$ faktorautomata: $Q'$ a $Q$ ekvivalenciaosztályait tartalmazza; $\delta'(q', t)$ a $\delta(r, t)$ osztálya (bármely $r \in q'$ reprezentánssal); $q_0'$ a $q_0$ osztálya; $F' = \{q' \mid q' \subseteq F\}$.
**Tétel:** Az $A/{\sim}$ faktorautomata ekvivalens $A$-val, redukált (különböző állapotainak különböző a maradéknyelve), és izomorfia erejéig az **egyetlen** összefüggő, redukált automata — ezért izomorf $A^{MN}_L$-lel.
---

## 19. Hogyan bizonyítjuk, hogy két összefüggő, redukált, ekvivalens VDA izomorf?
?
Legyenek $A$ és $A'$ összefüggő, redukált, $L(A) = L(A')$. Definiáljuk:
$$\varphi(\delta(q_0, u)) := \delta'(q_0', u) \quad \text{minden } u \in T^*\text{-ra.}$$
- **Jól definiált és injektív:** $\delta(q_0,u) = \delta(q_0,v) \iff L(A,\delta(q_0,u)) = L(A,\delta(q_0,v))$ (redukáltság) $\iff$ ugyanez $A'$-ban $\iff \delta'(q_0',u) = \delta'(q_0',v)$.
- **Szürjektív:** $A'$ összefüggő, minden állapota elérhető.
- **Izomorfizmus:** $\varphi(q_0) = q_0'$; $\varphi(F) = F'$; $\varphi(\delta(q,t)) = \delta'(\varphi(q), t)$. $\square$
---

## 20. Hogyan minimalizálunk algoritmikusan egy VDA-t?
?
Két lépés:
**1. Összefüggővé alakítás:** elérhetetlen állapotok elhagyása (BFS/iteratív módszerrel a $q_0$-ból elérhető állapotok meghatározásával).
**2. Redukálás:** az $i$-megkülönböztethetőségi partíció iteratív finomítása:
- Induljunk $\sim_0$-ból (elfogadó / nem elfogadó)
- Finomítsuk $\sim_{i+1}$-re, amíg a partíció nem stabilizálódik
- Az ekvivalenciaosztályok adják a minimális automata állapotait
---

## 21. Melyek az $\mathcal{L}_3$ osztályon eldönthető fő algoritmikus problémák?
?
| Probléma | Megoldás |
|---|---|
| $L(G) = \emptyset$? | VDA-ba konvertálás; végállapot elérhető-e a kezdőállapotból? |
| $L_1 \cap L_2 = \emptyset$? | $L_1 \cap L_2 \in \mathcal{L}_3$, üresség eldönthető |
| $L_1 = L_2$? | $L_1 \triangle L_2 = \emptyset$ (szimmetrikus differencia reguláris) |
| $L_1 \subseteq L_2$? | $L_1 \setminus L_2 = \emptyset$ (ahol $L_1 \setminus L_2 = L_1 \cap \bar{L}_2 \in \mathcal{L}_3$) |
| $u \in L(G)$? | Lineáris algoritmus (lásd lent) |
---

## 22. Írja le a szóprobléma lineáris algoritmusát reguláris grammatikára!
?
Legyen $G = \langle N, T, P, S \rangle$ normálformájú reguláris grammatika, $u = t_1 \cdots t_n$.
$$H_0 = \{S\}, \qquad H_{i+1} = \{A \in N \mid \exists B \in H_i : B \to t_{i+1} A \in P\}$$
$$u \in L(G) \iff H_n \cap F \neq \emptyset, \qquad F = \{A \mid A \to \varepsilon \in P\}$$
Az algoritmus lényegében a grammatikából épített VNDA determinizáltja $\mathcal{P}(N)$ állapothalmazzal. Futásidő: $O(n \cdot |G|)$.
---

## 23. Milyen fontos azonosságok teljesülnek reguláris kifejezésekre?
?
- $P + Q = Q + P$ (kommutativitás)
- $P \cdot (Q + R) = PQ + PR$ (disztributivitás)
- $P^* = \varepsilon + P \cdot P^*$ (csillag kifejtése)
- $P^* = (\varepsilon + P)^*$
- $P \cdot \emptyset = \emptyset$
---

## 24. Hogyan függ össze egy VDA állapotának maradéknyelve az automata és a nyelv maradéknyelveivel?
?
Legyen $A = \langle Q, T, \delta, q_0, F \rangle$ VDA, amely felismeri $L$-t. Ekkor:
$$L(A, q) := \{v \mid \delta(q, v) \in F\}$$
$$L_u = L(A, \delta(q_0, u))$$
Tehát az automata állapotai által generált maradéknyelvek lefedik a nyelv összes maradéknyelvét. Ha $A$ redukált, az egyes állapotokhoz különböző maradéknyelvek tartoznak — pontosan emiatt $A^{MN}_L$ minimális.
---

## 25. Mi a $k$-megszorított levezetés definíciója, és miért van rá szükség a reguláris kifejezés-levezetésben?
?
Az $A_i \Rightarrow^* u A_j$ levezetést **$k$-megszorítottnak** nevezzük, ha minden érintett közbülső nemterminális indexe legfeljebb $k$.
Ez teszi lehetővé az $E^k_{i,j}$ halmazok rekurzív felépítését: a $k$-megszorított levezetések vagy elkerülik $A_k$-t ($(k-1)$-megszorított rész), vagy átmennek rajta tetszőleges sokszor. A rekurzív formula ezért:
$$E^k_{i,j} = E^{k-1}_{i,j} + E^{k-1}_{i,k} \cdot (E^{k-1}_{k,k})^* \cdot E^{k-1}_{k,j}$$
---

## 26. Mi az $\varepsilon \in L(A)$ feltétele VNDA esetén?
?
$$\varepsilon \in L(A) \iff Q_0 \cap F \neq \emptyset$$
Vagyis az üres szót a VNDA pontosan akkor fogadja el, ha valamelyik kezdőállapot egyben elfogadó állapot is.
---

