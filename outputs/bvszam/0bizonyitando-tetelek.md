---
title: Bizonyítandó tételek
---

# Bizonyítandó tételek
A *Bevezetés a számításelméletbe* tárgy bvszam wiki-jéből kigyűjtött tételek a teljes állítással és bizonyítással, a kurzus tematikai felépítését követve.
## Formális nyelvek és zártsági tulajdonságok
### Tétel: A bal- és jobb-lineáris grammatikák ekvivalensek (mindkettő reguláris) — ($G \text{ bal-lin.} \Rightarrow \exists G' \text{ jobb-lin., } L(G)=L(G')$)
**Tétel:** Minden bal-lineáris grammatikához van ekvivalens jobb-lineáris grammatika (és viszont), tehát minden bal-lineáris grammatika reguláris nyelvet generál.
**Bizonyítás (ötlet):** Ha $G$ bal-lineáris, konstruálunk $G'$ jobb-lineáris grammatikát az $R'$ szabályhalmazzal:
1. $S \to u \in R' \iff S \to u \in R$
2. $S \to u A_k \in R' \iff A_k \to u \in R$
3. $A_j \to u A_k \in R' \iff A_k \to A_j u \in R$
4. $A_j \to u \in R' \iff S \to A_j u \in R$
Az így kapott $G'$ jobb-lineáris és $L(G') = L(G)$.
**$\mathcal{L}_3$ zártsága tükrözésre.** Minden jobb-lineáris grammatikából bal-lineáris grammatika kapható az $A \to u$ és $A \to uB$ szabályok helyett $A \to u^{-1}$ és $A \to B u^{-1}$ szabályokkal.
### Tétel: Arden lemmája: a $P = R + PQ$ egyenlet egyértelmű megoldása $P = RQ^*$ ha $\varepsilon \notin Q$ — ($P = R + PQ \Rightarrow P = RQ^*$)
**Tétel (Arden):** A $P = R + P \cdot Q$ egyenletnek $P$-re vonatkozó megoldása $P = R \cdot Q^*$. Ha $\varepsilon \notin Q$, ez az egyetlen megoldás.
**Bizonyítás:**
**(1) $P = R \cdot Q^*$ valóban megoldás:**
$$R + P \cdot Q = R + (R \cdot Q^*) \cdot Q = R + R \cdot (Q \cdot Q^*) = R \cdot (\varepsilon + Q \cdot Q^*) = R \cdot Q^* = P.$$
**(2) Egyediség (ha $\varepsilon \notin Q$):** Ismételt helyettesítéssel:
$$P = R + P \cdot Q = R + (R + P \cdot Q) \cdot Q = R + RQ + PQ^2 = \cdots = R(\varepsilon + Q + \cdots + Q^n) + PQ^{n+1}.$$
Legyen $w \in P$ tetszőleges, és $n = |w|$. Mivel $\varepsilon \notin Q$, a $Q^{n+1}$ minden szava legalább $n+1$ hosszú, így $w \notin PQ^{n+1}$. Ezért
$$w \in R(\varepsilon + Q + \cdots + Q^n) \subseteq RQ^*.$$
Fordítva, ha $w \in RQ^*$, akkor  van $n$, hogy $w \in RQ^n$, ami a jobb oldalban van, tehát $P$-ben is. Így csak $P = R \cdot Q^*$ lehetséges. $\square$
### Tétel: A reguláris kifejezések pontosan a 3-as típusú nyelveket írják le — ($L \in \mathcal{L}_3 \iff L = L(R) \text{ valamely RegEx-re}$)
**Tétel:** Minden reguláris kifejezés reguláris (3-as típusú) nyelvet jelöl, és megfordítva.
**Bizonyítás:**
**$\Rightarrow$ irány:** $\emptyset$, $\{\varepsilon\}$, $\{a\}$ regulárisak; $\mathcal{L}_3$ zárt a reguláris műveletekre, ezért minden RegEx reguláris nyelvet ír le.
**$\Leftarrow$ irány (konstrukció):** Legyen $N = \{A_1, \ldots, A_n\}$, $S = A_1$, és minden szabály $A_i \to aA_j$ vagy $A_i \to \varepsilon$ alakú.
**$k$-megszorított levezetés:** Az $A_i \Rightarrow^* u A_j$ levezetést $k$-megszorítottnak nevezzük, ha minden érintett közbülső nemterminális indexe legfeljebb $k$.
**Az $E^k_{i,j}$ halmazok definíciója** ($0 \leq k \leq n$, $1 \leq i,j \leq n$):
$$E^k_{i,j} := \{u \in T^* \mid \text{létezik } A_i \Rightarrow^* uA_j \text{ } k\text{-megszorított levezetés}\}$$
**Alaplépés ($k = 0$):**
- Ha $i \neq j$: $E^0_{i,j} = \{a \in T \mid A_i \to aA_j \in R\}$.
- Ha $i = j$: $E^0_{i,i} = \{\varepsilon\} \cup \{a \in T \mid A_i \to aA_i \in R\}$.
**Rekurzió** ($k \geq 1$):
$$E^k_{i,j} = E^{k-1}_{i,j} + E^{k-1}_{i,k} \cdot (E^{k-1}_{k,k})^* \cdot E^{k-1}_{k,j}$$
Indukcióval: $E^0$ reguláris kifejezéssel jelölhető, és ha $E^{k-1}$ mindegyike jelölhető, akkor $E^k$ is.
**Végeredmény:** Legyen $I_\varepsilon = \{i \mid A_i \to \varepsilon \in R\}$. Ekkor $L(G) = \bigcup_{i \in I_\varepsilon} E^n_{1,i}$. $\square$
## Reguláris nyelvek ($\mathcal{L}_3$) és véges automaták
### Tétel: Myhill–Nerode: egy nyelv pontosan akkor reguláris, ha véges sok különböző maradéknyelve van — ($L \in \mathcal{L}_3 \iff |\{L_p\}| < \infty$)
**Tétel (Myhill–Nerode):** $L \in \mathcal{L}_3 \iff |\{L_p\}_{p \in T^*}| < \infty$.
(Az $L$ nyelv $p$-re vonatkozó **maradéknyelve**: $L_p := \{v \mid pv \in L\}$.)
**Bizonyítás:**
**$\Rightarrow$:** Ha $A$ véges automata felismeri $L$-t, akkor $\{L_u\} \subseteq \{L(A,q)\}$, ami véges (mert $A$ állapotszáma véges).
**$\Leftarrow$:** A Myhill–Nerode automata:
$$A^{MN}_L = \langle \{L_p\}_{p \in T^*}, T, \delta, L_\varepsilon, F \rangle$$
ahol $\delta(L_p, t) = L_{pt}$ és $F = \{L_p \mid \varepsilon \in L_p\}$.
Ez véges (feltétel szerint) és elfogadja $L$-t. $\square$
### Következmény: A Myhill–Nerode automata a legkisebb $L$-et felismerő VDA — ($|A^{MN}_L| \leq |A|$ minden $L$-et felismerő $A$-ra)
**Következmény:** $A^{MN}_L$ állapotszáma kisebb vagy egyenlő, mint bármely $L$-et felismerő VDA állapotszáma — tehát $A^{MN}_L$ az $L$ **minimális automatája**.
### Tétel: A faktorautomata egyértelmű (izomorfia erejéig); a redukált, összefüggő minimális automata egyedi — ($A/{\sim}\ \cong\ A^{MN}_L$)
**Tétel:** Az $A/{\sim}$ faktorautomata ekvivalens $A$-val, redukált, és izomorfia erejéig az egyetlen ilyen összefüggő, redukált automata. Ezért az algoritmikusan kapott minimális automata izomorf $A^{MN}_L$-lel.
**Bizonyítás (egyediség):** Legyenek $A$ és $A'$ összefüggő, redukált és egymással ekvivalens VDA-k ($L(A) = L(A')$). Definiáljuk:
$$\varphi(\delta(q_0, u)) := \delta'(q_0', u) \quad \text{minden } u \in T^*\text{-ra.}$$
Megmutatjuk, hogy $\varphi$ jól definiált bijekció és izomorfizmus:
- **Jól definiáltság és injektivitás:**
$$\delta(q_0, u) = \delta(q_0, v) \iff L(A, \delta(q_0,u)) = L(A, \delta(q_0,v)) \iff L(A', \delta'(q_0',u)) = L(A', \delta'(q_0',v)) \iff \delta'(q_0', u) = \delta'(q_0', v)$$
ahol az első és utolsó ekvivalencia $A$ ill. $A'$ redukáltságából, a középső $A \sim A'$ ekvivalenciájából következik.
- **Szürjektivitás:** $A'$ összefüggősége miatt minden $A'$-állapot elérhető $q_0'$-ból valamely $u \in T^*$-on át.
- **Izomorfizmus-tulajdonság:** $\varphi(q_0) = q_0'$; $\varphi(F) = F'$ (mivel $q \in F \iff \varepsilon \in L(A,q) \iff \varepsilon \in L(A', \varphi(q)) \iff \varphi(q) \in F'$); minden $q \in Q$, $t \in T$-re $\varphi(\delta(q,t)) = \delta'(\varphi(q), t)$. $\square$
## Környezetfüggetlen nyelvek ($\mathcal{L}_2$) és veremautomaták
### Tétel: Bar-Hillel pumpáló lemma: minden elég hosszú KF szó pumpálható — ($\forall L \in \mathcal{L}_2:\ \exists p,q;\ \forall |w|>p\ \exists w=uxvyz \dots ux^ivy^iz \in L$)
**Tétel (Bar-Hillel lemma — pumpáló lemma KF nyelvekre):** Minden $L$ KF nyelvhez léteznek $p, q \in \mathbb{N}$, hogy minden $|w| > p$ szóhoz ($w \in L$) létezik $w = uxvyz$ felbontás, ahol:
- $|xvy| \leq q$
- $xy \neq \varepsilon$
- $ux^i vy^i z \in L$ minden $i \geq 0$-ra.
$p$ és $q$ csak a **nyelvtől** függ.
**Bizonyítás (vázlat):** Legyen $G$ Chomsky normálformájú grammatika $n$ nemterminálissal. Legyen $p = 2^{n-1}$, $q = 2^n$.
Ha $|w| > p$, a levezetési fa leghosszabb útján $> n$ csúcs van. A **skatulya-elvnél** fogva valamelyik $A$ nemterminális legalább kétszer ismétlődik. Az utolsó ismétlő pár alapján:
$$S \Rightarrow^* uAz, \quad A \Rightarrow^* xAy, \quad A \Rightarrow^* v$$
ahol $xy \neq \varepsilon$ (CNF biztosítja). Ekkor $ux^i vy^i z \in L$ minden $i \geq 0$-ra. $\square$
**Alkalmazás: $\{a^n b^n c^n\} \notin \mathcal{L}_2$.** Legyenek $p, q$ a lemma konstansai. Legyen $w = a^k b^k c^k$ ($k > \max\{p,q\}$). Mivel $|xvy| \leq q < k$, az $xy$ legfeljebb 2 betűfajtát tartalmaz. A $ux^0 vy^0 z$ szóban valamelyik betűfajtából kevesebb lesz $k$-nál — ez nem lehet $\{a^n b^n c^n\}$-beli. Ellentmondás.
### Tétel: Minden KF grammatika redukálható ekvivalens redukált alakra — ($\forall G \in \mathcal{L}_2\ \exists G' \text{ redukált, } L(G)=L(G')$)
**Tétel:** Minden KF grammatikához létezik vele ekvivalens redukált KF grammatika.
(Egy KF grammatika **redukált**, ha minden nemterminálisa **aktív** (terminális szó vezethető le belőle) és **elérhető** (előfordul $S$-ből levezethető mondatformában).)
**Bizonyítás (konstrukció):**
1. **Aktívak iteratív meghatározása:**
$$A_1 = \{X \mid X \to u \in P,\ u \in T^*\}, \quad A_{i+1} = A_i \cup \{X \mid X \to w \in P,\ w \in (T \cup A_i)^*\}$$
Az iteráció véges sok lépésben stabilizálódik. Inaktív nemterminálisok és szabályaik elhagyása.
2. **Elérhetők iteratív meghatározása:**
$$R_1 = \{S\}, \quad R_{i+1} = R_i \cup \{Y \in N \mid X \to uYw \in P,\ X \in R_i\}$$
Elérhetetlen nemterminálisok elhagyása.
A maradék grammatika ekvivalens az eredetivel és redukált. $\square$
### Tétel: A KF grammatika egyértelműsége eldönthetetlen — ($\{\langle G \rangle \mid G \text{ KF egyértelmű}\} \notin \mathrm{R}$)
**Tétel (2.30.):** A KF grammatikák egyértelműsége eldönthetetlen.
**Bizonyítás (visszavezetés PMP-ből):** Adott $D$ PMP-példányból ($u_i, v_i \in \Sigma^+$) építhető egy $G$ grammatika, amely pontosan akkor nem egyértelmű, ha $D$-nek van megoldása. $G$-be két párhuzamos szabályrendszert teszünk, $G_A$-t az $u_i$-kre és $G_B$-t a $v_i$-kre (egy $\Delta = \{a_1, \ldots, a_n\}$ indexábécé felett); egy $w$ szónak pontosan akkor van kétféle bal-levezetése, ha az index-rész ugyanazt a dominósorozatot kódolja felül és alul. Mivel PMP eldönthetetlen (*2.29. tétel*), az egyértelműség is az.
### Tétel: Két KF grammatika metszetének, egyenlőségének és tartalmazásának kérdései eldönthetetlenek — ($\{\langle G_1, G_2\rangle \mid L(G_1) \cap L(G_2) = \emptyset\} \notin \mathrm{R}$ stb.)
**Tétel (2.31.):** Két KF grammatikára eldönthetetlen az alábbi kérdések mindegyike:
1. $L(G_1) \cap L(G_2) = \emptyset$?
2. $L(G_1) = L(G_2)$?
3. $L(G_1) = \Gamma^*$ valamely $\Gamma$ ábécére?
4. $L(G_1) \subseteq L(G_2)$?
**Bizonyítás:** Az előbbi 2.30. bizonyítás $G_A$, $G_B$ grammatikáit (és az $L_A = L(G_A)$, $L_B = L(G_B)$ nyelveket) felhasználva:
1. **Metszet-üresség:** közvetlenül a 2.30. bizonyításából, mert $D$-nek akkor és csak akkor van megoldása, ha $L_A \cap L_B \neq \emptyset$.
2. **Egyenlőség:** mivel $\overline{L_A}, \overline{L_B}$ ezen speciális esetben KF, és a KF nyelvek zártak az unióra, $\overline{L_A} \cup \overline{L_B} = \overline{L_A \cap L_B}$ KF; az $L(G_1) = L(G_2) = (\Sigma\cup\Delta)^*$ kérdés visszaadja az 1. pontot.
3. **$\Gamma^*$-egyenlőség:** ha eldönthető lenne, az 1. pont is eldönthető lenne.
4. **Tartalmazás:** a 2. pont következménye: $L(G_1) = L(G_2) \iff L(G_1) \subseteq L(G_2) \wedge L(G_2) \subseteq L(G_1)$. $\square$
## Környezetfüggő nyelvek ($\mathcal{L}_1$) és lineárisan korlátolt automaták
### Tétel: A környezetfüggő nyelvek pontosan az LKA-felismerhetők — ($\mathcal{L}_1 = \{L \mid L \text{ felismerhető LKA-val}\}$)
**Tétel:** $\mathcal{L}_1 =$ LKA által felismert nyelvek osztálya.
**Bizonyítás:**
**$\mathcal{L}_1 \to \text{LKA}$:** Minden 1-típusú (hossz-nemcsökkentő) grammatikához megadható LKA, amely a levezetést **nemdeterminisztikusan** szimulálja a bemenet feletti munkaterületen. Mivel a szabályok hossz-nemcsökkentők, az aktuális mondatforma sosem hosszabb az inputnál, így a szalag korlátja nem sérül.
**$\text{LKA} \to \mathcal{L}_1$:** Az LKA konfigurációit kódoló grammatikából 1-típusú grammatika konstruálható, amely pontosan az LKA által elfogadott szavakat generálja. $\square$
### Tétel: Minden LKA által felismert nyelv eldönthető — ($\forall A \text{ LKA: } L(A) \in \mathrm{R}$)
**Tétel:** Ha $A$ LKA, akkor $L(A)$ eldönthető ($L(A) \in \mathrm{R}$).
**Bizonyítás:** Az LKA lehetséges konfigurációinak száma $u$ bemenetre legfeljebb
$$m(u) = |Q| \cdot |u| \cdot |\Gamma|^{|u|}.$$
Ha van elfogadó számítás, akkor van legfeljebb $m(u)$ hosszú elfogadó számítás (különben egy konfiguráció ismétlődne, ami ciklust adna). Egy $M$ TG szimulálhatja $A$-t pontosan $m(u)$ lépésig, majd leáll — tehát $L(A) \in \mathrm{R}$. $\square$
**Következmény:** $\mathcal{L}_1 \subseteq \mathrm{R}$.
### Tétel: Az 1-es típusú nyelvek valódi részhalmazát alkotják az eldönthető nyelveknek — ($\mathcal{L}_1 \subsetneq \mathrm{R}$)
**Tétel:** $\mathcal{L}_1 \subsetneq \mathrm{R}$ (a tartalmazás valódi).
**Bizonyítás (diagonalizáció):** Legyen
$$L_{\text{LKA-átló}} = \{\langle M \rangle \mid M \text{ LKA és } \langle M \rangle \notin L(M)\}.$$
- $L_{\text{LKA-átló}} \in \mathrm{R}$: az univerzális TG $m(\langle M \rangle)$ lépés után leállítható, így a tagság eldönthető.
- $L_{\text{LKA-átló}} \notin \mathcal{L}_1$: önhivatkozásos ellentmondás. Tegyük fel, hogy egy $A$ LKA felismeri. Akkor $\langle A \rangle \in L_{\text{LKA-átló}} \iff \langle A \rangle \notin L(A) \iff \langle A \rangle \notin L_{\text{LKA-átló}}$. Ellentmondás.
Tehát $L_{\text{LKA-átló}} \in \mathrm{R} \setminus \mathcal{L}_1$. $\square$
### Tétel: A 0-típusú nyelvek pontosan a rekurzívan felsorolható nyelvek — ($\mathcal{L}_0 = \mathrm{RE}$)
**Tétel:** $L \in \mathcal{L}_0 \iff L \in \mathrm{RE}$.
**Bizonyítás:**
**$\mathcal{L}_0 \subseteq \mathrm{RE}$:** Minden $G$ 0-típusú grammatikához megadható $L(G)$-t felismerő NTG (3-szalagos: bemenet, sentenciális forma, szabályok). Az NTG nemdeterminisztikusan alkalmaz grammatikai szabályokat $S$-ből kiindulva; ha az aktuális mondatforma egyenlő az inputtal, elfogad.
**$\mathrm{RE} \subseteq \mathcal{L}_0$:** Minden $M$ DTG-hez megkonstruálható $G$ 0-típusú grammatika, amely a kódolt konfigurációk sorozatát generálja; a generált szó pontosan $L(M)$-beli. $\square$
## Turing-gép és variánsai
### Tétel: A nemdeterminizmus nem növeli a Turing-gép számítási erejét (csak az időbonyolultságot) — ($\forall M \text{ NTG}\ \exists M' \text{ DTG: } L(M)=L(M')$)
**Tétel:** Minden $M$ nemdeterminisztikus TG-hez megadható vele ekvivalens $M'$ determinisztikus TG.
**Bizonyítás (3-szalagos DTG, szélességi keresés a számítási fában):**
1. **Szalag 1:** az $u$ bemenő szó (érintetlen).
2. **Szalag 2:** szimulációs szalag — $M$ egy konkrét számítási sorozatának lépésenkénti eredménye.
3. **Szalag 3:** szelektoros szalag — egy $\{1, \ldots, d\}$ feletti szó, ahol $d$ a $\delta$ által megadott halmazok legnagyobb elemszáma; ez kódolja, hogy a kezdőkonfigurációból mely választásokkal jutunk a fa adott szögpontjához.
$M'$ a 3. szalagon lévő szót **hosszlexikografikus sorrendben** lépteti, így bejárja $M$ számítási fáját szélességében; minden véges elfogadó ágat megtalál. $M'$ akkor és csak akkor lép elfogadó konfigurációba, ha $M$-nek van elfogadó számítási sorozata.
**Időkorlát:** a konstrukció exponenciális időigény-romlást eredményez — $M'$ időigénye $M$ számítási fája magasságának exponenciálisa. (Vö. **P** vs **NP**.) $\square$
**Következmény:** $L \in \mathrm{RE} \iff$ létezik $L$-t felismerő NTG.
## Felismerhetőség és eldönthetőség (R, RE)
### Tétel: Az univerzális Turing-gép létezik: a megállási nyelv felismerhető — ($L_u \in \mathrm{RE}$)
**Tétel:** $L_u \in \mathrm{RE}$.
(Definíció: $L_u = \{\langle M, w \rangle \mid w \in L(M)\}$.)
**Bizonyítás (4-szalagos UTG):** Feltehető, hogy $M$ egyszalagos. $U$ négy szalagot használ:
| Szalag | Tartalom |
|--------|----------|
| 1. (csak olvasható) | $\langle M, w \rangle$ — $M$ leírása és a bemenet |
| 2. | $M$ aktuális szalagtartalma és fejpozíciója |
| 3. | $M$ aktuális állapota |
| 4. | segédszalag |
$U$ működése:
1. Ellenőrzi, hogy a bemenet első része érvényes TG-kódolás-e.
2. $w$-t a 2. szalagra másolja; $q_0$ kódját a 3. szalagra.
3. **Szimuláció egy lépése:** leolvassa $M$ aktuális szimbólumát (2. sz.) és állapotát (3. sz.); megkeresi a $\delta$-átmenetet az 1. szalagon; előállítja az új tartalmat és állapotot.
4. Ha $M$ elfogadó/elutasító állapotba lép, $U$ is. Különben goto 3.
Ha $M$ nem áll meg $w$-n, $U$ sem áll meg $\langle M, w \rangle$-n — ezért $U$ csak **felismeri** $L_u$-t, nem **dönti el**. $\square$
### Tétel: Az univerzális nyelv nem eldönthető (átlós érv) — ($L_u \notin \mathrm{R}$)
**Tétel:** $L_u \notin \mathrm{R}$.
**Bizonyítás (diagonalizáció):** Tegyük fel indirekt, hogy létezik $D$ TG, amely eldönti $L_u$-t. Definiáljuk $D'$-t a következőképpen: $D'$ az $\langle M \rangle$ bemeneten futtatja $D$-t az $\langle M, \langle M \rangle \rangle$ bemeneten, majd a választ megfordítja (elfogad $\iff$ $D$ elutasít).
Most $D'$-t saját kódolásán futtatva:
$$\langle D' \rangle \in L(D') \iff D \text{ elutasítja } \langle D', \langle D' \rangle \rangle \iff \langle D', \langle D' \rangle \rangle \notin L_u \iff \langle D' \rangle \notin L(D').$$
Ellentmondás. $\square$
**Összefoglalva:** $L_u \in \mathrm{RE} \setminus \mathrm{R}$.
### Tétel: Egy nyelv pontosan akkor eldönthető, ha ő és komplementere is felismerhető — ($L \in \mathrm{R} \iff L, \bar L \in \mathrm{RE}$)
**Tétel:** $L \in \mathrm{R} \iff L \in \mathrm{RE}$ és $\bar{L} \in \mathrm{RE}$.
**Bizonyítás:**
**$\Rightarrow$:** Ha $L \in \mathrm{R}$, akkor van $M$ TG, ami minden inputon megáll. Ekkor $L \in \mathrm{RE}$ (triviálisan), és $\bar L \in \mathrm{R} \subseteq \mathrm{RE}$ (az elfogadó/elutasító állapotokat felcserélve $M$ eldönti $\bar L$-t).
**$\Leftarrow$:** Legyen $M_1$ az $L$-t, $M_2$ a $\bar{L}$-t felismerő TG. Egy új $M'$ gép **felváltva** szimulál egy-egy lépést $M_1$ és $M_2$ futásából. Mivel $L \cup \bar L = \Sigma^*$, minden bemeneten valamelyikük véges sok lépésen belül elfogad — tehát $M'$ mindig megáll, és eldönti $L$-t. $\square$
**Következmény:** $\mathrm{RE}$ nem zárt komplementerre. Ha $\overline{L_u} \in \mathrm{RE}$ lenne, $L_u \in \mathrm{R}$ következne — ellentmondás.
## Eldönthetetlen problémák
### Tétel: A megállási probléma felismerhető, de nem eldönthető — ($L_h \in \mathrm{RE} \setminus \mathrm{R}$)
**Tétel:** $L_h \in \mathrm{RE} \setminus \mathrm{R}$.
(Definíció: $L_h = \{\langle M, w \rangle \mid M \text{ megáll a } w \text{ bemeneten}\}$.)
**Bizonyítás:**
**$L_h \notin \mathrm{R}$ — visszavezetés $L_u \leq L_h$:** Adott $\langle M, w \rangle$ párhoz konstruáljuk $M'$-t:
1. Futtatja $M$-et $w$-n (UTG-vel).
2. Ha $M$ elfogadja $w$-t, $M'$ is elfogadja.
3. Ha $M$ elutasítja $w$-t, $M'$ olyan állapotba lép, ahol végtelen ciklusban lépteti a fejet jobbra — **soha nem áll meg**.
Az $\langle M, w \rangle \mapsto \langle M', w \rangle$ leképezés kiszámítható, és
$$\langle M, w \rangle \in L_u \iff \langle M', w \rangle \in L_h.$$
Mivel $L_u \notin \mathrm{R}$, a visszavezetés-tétel alapján $L_h \notin \mathrm{R}$.
**$L_h \in \mathrm{RE}$ — visszavezetés $L_h \leq L_u$:** Tetszőleges $\langle M, w \rangle$ párhoz $\langle M', w \rangle$, ahol $M'$-t úgy kapjuk $M$-ből, hogy minden $q_n$-be (elutasító) vezető átmenetét $q_i$-be (elfogadó) irányítjuk. Ekkor $M$ megáll $w$-n pontosan akkor, ha $M'$ elfogadja $w$-t, azaz $\langle M, w \rangle \in L_h \iff \langle M', w \rangle \in L_u$. Mivel $L_u \in \mathrm{RE}$, $L_h \in \mathrm{RE}$. $\square$
### Tétel: A nemüres nyelvet felismerő TG-k nyelve felismerhető, de nem eldönthető — ($L_{\neg\emptyset} \in \mathrm{RE} \setminus \mathrm{R}$)
**Tétel:** $L_{\neg\emptyset} \in \mathrm{RE} \setminus \mathrm{R}$.
(Definíció: $L_{\neg\emptyset} = \{\langle M\rangle \mid L(M) \neq \emptyset\}$.)
**Bizonyítás:**
**$L_{\neg\emptyset} \notin \mathrm{R}$ (visszavezetés $L_u \leq L_{\neg\emptyset}$):** Adott $\langle M, w \rangle$-hez konstruáljuk az $M'$ gépet, amely tetszőleges $u$ bemeneten ellenőrzi, hogy $u = w$-e; ha nem, elutasít, ha igen, $M$-et szimulálja $w$-n. Ekkor $L(M') \neq \emptyset \iff w \in L(M)$, azaz $\langle M' \rangle \in L_{\neg\emptyset} \iff \langle M, w \rangle \in L_u$.
**$L_{\neg\emptyset} \in \mathrm{RE}$:** egy $M'$ kétszalagos gép a második szalagon tárolt $i$ számlálóval ciklikusan szimulálja a bemeneti $M$ első $i$ lépését az $w_1, \ldots, w_i$ szavakon (a szavak felsorolása mellett); ha valamelyiken $M$ elfogadó állapotba lép, $M'$ elfogad. $\square$
### Tétel: Az üres nyelvet felismerő TG-k és a TG-ekvivalencia kérdése nem felsorolható — ($L_\emptyset, L_{EQ} \notin \mathrm{RE}$)
**Tétel:** $L_\emptyset \notin \mathrm{RE}$, és $L_{EQ} \notin \mathrm{RE}$.
(Definíciók: $L_\emptyset = \{\langle M\rangle \mid L(M) = \emptyset\}$; $L_{EQ} = \{\langle M_1, M_2\rangle \mid L(M_1) = L(M_2)\}$.)
**Bizonyítás:** $L_\emptyset = \overline{L_{\neg\emptyset}}$. Mivel $L_{\neg\emptyset} \in \mathrm{RE} \setminus \mathrm{R}$ és RE nem zárt komplementerre, $L_\emptyset \notin \mathrm{RE}$.
$L_\emptyset$ az $L_{EQ}$ speciális esete (rögzítsük $M_2$-t egy semmit el nem fogadó gépre): ha $L_\emptyset \notin \mathrm{RE}$, akkor $L_{EQ} \notin \mathrm{RE}$. $\square$
### Tétel: Rice tétele: TG által felismert nyelv minden nemtriviális tulajdonsága eldönthetetlen — ($\mathcal{P} \subsetneq \mathrm{RE}, \mathcal{P} \neq \emptyset \Rightarrow L_\mathcal{P} \notin \mathrm{R}$)
**Tétel (Rice):** Ha $\mathcal{P} \subseteq \mathrm{RE}$ nemtriviális tulajdonság, akkor $L_\mathcal{P} \notin \mathrm{R}$.
($\mathcal{P}$ **nemtriviális**: $\mathcal{P} \neq \emptyset$ és $\mathcal{P} \neq \mathrm{RE}$. $L_\mathcal{P} = \{\langle M \rangle \mid L(M) \in \mathcal{P}\}$.)
**Bizonyítás:**
**1. eset: $\emptyset \notin \mathcal{P}$.** Legyen $L \in \mathcal{P}$ egy konkrét nyelv ($\mathcal{P} \neq \emptyset$ miatt létezik), $M_L$ az azt felismerő TG. Megadjuk az $L_u \leq L_\mathcal{P}$ visszavezetést: $\langle M, w \rangle$ bemenetre konstruálunk egy $M'$ kétszalagos TG-t, amely $x$ bemeneten:
- az egyik szalagján szimulálja $M$ működését a $w$ szón ($M$ és $w$ kódja be van építve $M'$ kódjába; UTG hívás),
- ha $M$ nem fogadja el $w$-t, $M'$ nem csinál semmit, azaz $L(M') = \emptyset$,
- ha $M$ elfogadja $w$-t, $M'$ szimulálni kezdi $M_L$-t $x$-en, azaz $L(M') = L$.
Így:
$$\langle M, w \rangle \in L_u \Rightarrow L(M') = L \in \mathcal{P} \Rightarrow \langle M' \rangle \in L_\mathcal{P}$$
$$\langle M, w \rangle \notin L_u \Rightarrow L(M') = \emptyset \notin \mathcal{P} \Rightarrow \langle M' \rangle \notin L_\mathcal{P}$$
Tehát $L_u \leq L_\mathcal{P}$, és így $L_\mathcal{P} \notin \mathrm{R}$.
**2. eset: $\emptyset \in \mathcal{P}$.** Alkalmazzuk az 1. esetet $\overline{\mathcal{P}} = \mathrm{RE} \setminus \mathcal{P}$-re (szintén nemtriviális, $\emptyset \notin \overline{\mathcal{P}}$): $L_{\overline{\mathcal{P}}} \notin \mathrm{R}$, és $L_{\overline{\mathcal{P}}} = \overline{L_\mathcal{P}}$, ezért $L_\mathcal{P} \notin \mathrm{R}$. $\square$
**Alkalmazások.** Eldönthetetlen, hogy egy $M$ TG az üres nyelvet, véges nyelvet, KF nyelvet ismer-e fel, vagy hogy elfogadja-e az üres szót.
### Tétel: A Post megfelelkezési (dominó-)probléma eldönthetetlen — ($\mathrm{PMP} \notin \mathrm{R}$)
**Tétel:** $\mathrm{PMP} \notin \mathrm{R}$.
A bizonyítás két lépésből áll, egy segédfogalom — a **módosított PMP (MPMP)** — közbeiktatásával. Az MPMP ugyanaz, mint a PMP, de a megoldásnak az **első dominóval $\left[\tfrac{u_1}{v_1}\right]$ kell kezdődnie**.
**2.28. tétel: $\mathrm{MPMP} \leq \mathrm{PMP}$.**
Adott MPMP-példányhoz, $D = \{[\tfrac{u_1}{v_1}], \ldots, [\tfrac{u_n}{v_n}]\}$, konstruáljuk a $D'$ készletet két új $*$ és $\#$ szimbólummal:
$$D' = \left\{ \left[\tfrac{*u_1}{*v_1*}\right], \left[\tfrac{*u_1}{v_1*}\right], \left[\tfrac{*u_2}{v_2*}\right], \ldots, \left[\tfrac{*u_n}{v_n*}\right], \left[\tfrac{*\#}{\#}\right] \right\}.$$
A $*$ jelek beszúrása kikényszeríti, hogy $D'$ megoldása a $\left[\tfrac{*u_1}{*v_1*}\right]$ dominóval kezdődjön és a $\left[\tfrac{*\#}{\#}\right]$ dominóval végződjön; a köztes dominók $D$ egy MPMP-megoldásának felelnek meg.
**2.29. tétel: $L_u \leq \mathrm{MPMP}$.**
Adott $M = (Q, \Sigma, \Gamma, \delta, q_i, q_n)$ TG-hez és $w \in \Sigma^*$ bemenethez olyan $D$ dominókészletet konstruálunk, amelynek pontosan akkor van megoldása, ha $\langle M, w \rangle \in L_u$. A dominósorozat felső és alsó szava az $M$ egymást követő, $\#$-cal elválasztott **konfigurációit** kódolja, az alsó szó mindig egy konfigurációval előbb tart:
1. **Kezdő dominó:** $\left[\tfrac{\#}{\#q_0 a_1 \ldots a_n\#}\right]$.
2. **Átmenet-dominók:** minden $\delta$-átmenethez (jobbra/balra/helyben) megfelelő $\left[\tfrac{pa}{bq}\right]$, $\left[\tfrac{cpa}{qcb}\right]$, $\left[\tfrac{pa}{qb}\right]$ dominók.
3. **Másoló dominók:** $\left[\tfrac{a}{a}\right]$ minden $a \in \Gamma$-ra, valamint $\left[\tfrac{\#}{\#}\right]$ és $\left[\tfrac{\#}{\sqcup\#}\right]$ a szalag végéhez.
4. **Záró dominók:** $q_i$ elérésekor $\left[\tfrac{aq_i}{q_i}\right]$, $\left[\tfrac{q_i a}{q_i}\right]$ típusúak „eltüntetik" $q_i$ környezetét; végül $\left[\tfrac{q_i\#\#}{\#}\right]$ zár.
Ekkor $D$-nek pontosan akkor van MPMP-megoldása, ha $M$ elfogadja $w$-t.
**Lánc:** $L_u \leq \mathrm{MPMP} \leq \mathrm{PMP}$, és mivel $L_u \notin \mathrm{R}$, $\mathrm{PMP} \notin \mathrm{R}$. $\square$
## Bonyolultságelmélet alapjai (P, NP)
### Tétel: Egyetlen NP-teljes probléma P-belisége az egész P=NP egybeesést jelentené — ($L \text{ NP-teljes}, L \in \mathrm{P} \Rightarrow \mathrm{P}=\mathrm{NP}$)
**Tétel:** Ha $L$ NP-teljes és $L \in \mathrm{P}$, akkor $\mathrm{P} = \mathrm{NP}$.
**Bizonyítás:** Tetszőleges $L' \in \mathrm{NP}$-re $L' \leq_p L$ (NP-teljesség), és mivel P zárt a $\leq_p$-re, $L' \in \mathrm{P}$. Tehát $\mathrm{NP} \subseteq \mathrm{P}$, és $\mathrm{P} \subseteq \mathrm{NP}$ triviális. $\square$
## NP-teljes és P-beli konkrét problémák
### Tétel: Cook–Levin: a Boole-kielégíthetőség az első NP-teljes probléma — ($\mathrm{SAT} \text{ NP-teljes}$)
**Tétel (Cook–Levin):** SAT NP-teljes.
**Bizonyítás:** Megmutatjuk, hogy minden $L \in \mathrm{NP}$ visszavezethető SAT-ra polinom időben — a számítás **táblakódolásával**.
**Táblakódolás.** Legyen $M$ egy $p(n)$ lépésidejű NTG, amely $L$-et dönti el. Az $M$ $w$ bemenetű számítása felírható egy $(p(n)+1) \times (2p(n)+3)$ méretű **tableau** (tábla) $T$ segítségével, amelynek minden cellájában egy $\Delta = Q \cup \Gamma \cup \{\#\}$ feletti szimbólum áll. Változók: $x_{i,j,s}$ — igaz, ha $T$ $(i,j)$ cellájában $s$ áll.
**A $\varphi_w$ formula részei.**
$$\varphi_w := \varphi_0 \land \varphi_{start} \land \varphi_{move} \land \varphi_{accept}$$
**$\varphi_0$** — minden cellában pontosan egy szimbólum áll:
$$\varphi_0 := \bigwedge_{i,j} \left( \bigvee_{s \in \Delta} x_{i,j,s} \right) \land \bigwedge_{i,j} \bigwedge_{s \neq t} (\neg x_{i,j,s} \lor \neg x_{i,j,t})$$
**$\varphi_{start}$** — az első sor a $w$ kezdőkonfigurációját kódolja.
**$\varphi_{move}$** — minden egymást követő sorpár érvényes TG-lépésnek felel meg. Minden $(i,j)$ pozícióra $\psi_{i,j}$ tiltja az „illegális ablakokat" (2×3-as szomszédság):
$$\psi_{i,j} := \bigwedge_{(b_1,\ldots,b_6) \text{ illegális}} \left( \neg x_{i,j-1,b_1} \lor \neg x_{i,j,b_2} \lor \neg x_{i,j+1,b_3} \lor \neg x_{i+1,j-1,b_4} \lor \neg x_{i+1,j,b_5} \lor \neg x_{i+1,j+1,b_6} \right)$$
**$\varphi_{accept}$** — az utolsó sorban van elfogadó állapot:
$$\varphi_{accept} = \bigvee_{j=2}^{2p(n)+2} x_{p(n)+1,\, j,\, q_f}$$
**Méret:** $|\varphi_0| = O(p^2)$, $|\varphi_{start}|, |\varphi_{accept}| = O(p)$, $|\varphi_{move}| = O(p^2)$. Összesen $O(p^2(n))$ — polinom időben megkonstruálható.
$$w \in L \iff \varphi_w \text{ kielégíthető} \iff \langle \varphi_w \rangle \in \mathrm{SAT}.$$
Mivel ez minden $L \in \mathrm{NP}$-re fennáll: SAT NP-nehéz. Mivel SAT $\in$ NP (egy értékadás polinom időben ellenőrizhető), SAT NP-teljes. $\square$
### Tétel: 3SAT NP-teljes (klóz-felosztással SAT-ból) — ($\mathrm{3SAT} \text{ NP-teljes}$)
**Tétel:** 3SAT NP-teljes.
**Bizonyítás:**
**$\in$ NP:** tanúellenőrzés mint SAT-nál (egy értékadás polinom időben ellenőrizhető).
**SAT $\leq_p$ 3SAT — klóz-felosztó transzformáció:**
| Eredeti klóz | 3KNF megfelelő |
|---|---|
| $l$ (1 literál) | $l \lor x \lor y,\ l \lor x \lor \neg y,\ l \lor \neg x \lor y,\ l \lor \neg x \lor \neg y$ |
| $l_1 \lor l_2$ | $l_1 \lor l_2 \lor x,\ l_1 \lor l_2 \lor \neg x$ |
| $l_1 \lor l_2 \lor l_3$ | változatlan |
| $l_1 \lor l_2 \lor l_3 \lor l_4$ | $l_1 \lor l_2 \lor x,\ \neg x \lor l_3 \lor l_4$ |
| $l_1 \lor \cdots \lor l_n\ (n \geq 5)$ | $l_1 \lor l_2 \lor x_1,\ \neg x_1 \lor l_3 \lor x_2,\ \ldots,\ \neg x_{n-3} \lor l_{n-1} \lor l_n$ |
Az $x, y, x_1, \ldots, x_{n-3}$ új segédváltozók. A transzformáció kielégíthetőséget megőriz: ha az eredeti klóz teljesül, az új segédváltozókhoz megadható alkalmas értékadás; fordítva, a segédváltozók értéke eltüntethető.
A transzformáció polinom idejű, és SAT-ot 3SAT-ra vezeti vissza. Cook–Levin ($SAT$ NP-teljes) + terjesztés $\Rightarrow$ 3SAT NP-teljes. $\square$
### Tétel: 2SAT polinom időben eldönthető (implikációs gráf + EÖK) — ($\mathrm{2SAT} \in \mathrm{P}$)
**Tétel:** $\mathrm{2SAT} \in \mathrm{P}$.
**Bizonyítás (implikációs gráf):** Legyen $\varphi$ egy $x_1, \ldots, x_n$ változókat tartalmazó 2KNF formula $m$ klózzal.
Konstruáljuk a $G_\varphi$ **implikációs gráfot**:
- **Csúcsok:** $2n$ db — minden $x_i$-hez $x_i$ és $\neg x_i$.
- **Élek:** minden $l_i \lor l_j$ klózhoz a $(\neg l_i, l_j)$ és $(\neg l_j, l_i)$ irányított élek.
(Motiváció: $l_i \lor l_j \equiv (\neg l_i \Rightarrow l_j) \land (\neg l_j \Rightarrow l_i)$.)
**Állítás (kielégíthetőségi feltétel):** $\varphi$ akkor és csak akkor kielégíthető, ha egyetlen $i$-re sem kerül $x_i$ és $\neg x_i$ ugyanabba az erősen összefüggő komponensbe (EÖK) $G_\varphi$-ben.
**Bizonyítás:**
- Ha $x_i$ és $\neg x_i$ ugyanabban az EÖK-ban van, ellentmondás (egyszerre kellene igaz és hamis).
- Ha nem: kielégítő értékadás konstruálható: $x_i$ értéke igaz, ha $G_\varphi$-ben $\neg x_i$-ből $x_i$-be vezet út (vagyis $x_i$ EÖK-ja a topologikus sorrendben később jön); egyébként hamis.
**Algoritmikus következmény:** $G_\varphi$ felépítése $O(n + m)$, EÖK-ok meghatározása (Tarjan) $O(n + m)$ — összesen polinom (sőt lineáris). $\square$
### Tétel: 3-színezhetőség NP-teljes (3SAT-ból visszavezetve) — ($\text{3SZÍNEZÉS NP-teljes}$)
**Tétel:** 3SZÍNEZÉS NP-teljes.
(Definíció: $\text{3SZÍNEZÉS} = \{\langle G \rangle \mid G \text{ 3-színezhető}\}$.)
**Bizonyítás:**
**$\in$ NP:** Egy NTG nemdeterminisztikusan kioszt minden csúcsnak egy színt $\{1,2,3\}$-ból, majd polinom időben ellenőrzi az éleket.
**NP-nehézség (3SAT $\leq_p$ 3SZÍNEZÉS):** $\varphi$ 3-CNF formulából $G_\varphi$ gráfot építünk:
**Változócsúcsok:** Minden $x_i$ változóhoz két csúcs ($x_i$ és $\bar{x}_i$) köztük éllel (komplementer pár).
**Paletta-csúcsok:** Három speciális csúcs $A$ (igaz/zöld), $B$ (hamis/piros), $\top$ (alap/kék) — egymással klikket alkotnak. Minden $x_i$–$\bar{x}_i$ pár kötve van $\top$-hoz: ezért egyikük $A$, a másik $B$ lesz.
**Klózcsúcsok:** Minden klózhoz egy ötszög-szerkezet (5 csúcsú részgráf) épül a 3 literál csúcsaiból és $B$-ből — ha mindhárom literál hamis (piros), az ötszög nem 3-színezhető.
**Helyesség:**
- $\varphi$ kielégíthető $\Rightarrow$ $G_\varphi$ 3-színezhető: ha $x_i$ igaz, $x_i$ zöld, $\bar{x}_i$ piros; minden klóz legalább egy igaz literált tartalmaz, így az ötszög kiterjeszthető.
- $G_\varphi$ 3-színezhető $\Rightarrow$ $\varphi$ kielégíthető: $A$ kék, $B$ piros (feltehetőleg), minden $(x_i, \bar{x}_i)$ párban egy piros + egy zöld; az ötszögek színezéséből adódik, hogy minden klóznak van zöld (igaz) literálja.
A visszavezetés polinom idejű ($|G_\varphi| = O(|\varphi|)$). $\square$
## Tárbonyolultság (PSPACE)
### Tétel (Savitch): Determinisztikus szimuláció csak négyzetes tár-romlással drágább a nemdeterminisztikusnál — ($\mathrm{NSPACE}(f) \subseteq \mathrm{SPACE}(f^2)$ ha $f \geq \log n$)
**Tétel (Savitch, 3.33.):** Ha $f(n) \geq \log n$, akkor $\mathrm{NSPACE}(f(n)) \subseteq \mathrm{SPACE}(f^2(n))$.
**Bizonyítás (vázlat):** Egy $O(f(n))$ tárú NTG $M$ konfigurációi a $w$ bemeneten egy $C_w$ **konfigurációs gráfot** alkotnak; $|C_w| = 2^{O(f(n))}$. Az $M$-nek (alkalmas $M'$-re cserélve) pontosan egy $c_{elfogadó}$ konfigurációja van. A $w$ elfogadása $\iff$ $C_w$-ben van út $c_{kezdő} \to c_{elfogadó}$.
Definiáljuk az $\mathrm{ELÉR}(c_1,c_2,t)$ predikátumot: igaz, ha van legfeljebb $t$ hosszú út $c_1$-ből $c_2$-be. Rekurzió **középső konfiguráció keresésével:**
$$\mathrm{ELÉR}(c_1,c_2,t) \iff \exists c:\ \mathrm{ELÉR}(c_1,c,\lceil t/2\rceil) \wedge \mathrm{ELÉR}(c,c_2,\lceil t/2\rceil).$$
A rekurzió mélysége $\log_2 2^{O(f(n))} = O(f(n))$, minden szinten $O(f(n))$ tár (egy konfigurációkód) — összesen $O(f^2(n))$. $\square$
**Következmény (3.34.):** $\mathrm{PSPACE} = \mathrm{NPSPACE}$ (a polinom négyzete polinom).
### Tétel: QSAT (kvantifikált Boole-formula igazsága) PSPACE-teljes — ($\mathrm{QSAT}$ PSPACE-teljes)
**Tétel (3.37.):** QSAT PSPACE-teljes.
(Definíció: TKBF = teljesen kvantifikált Boole-formula; $\mathrm{QSAT} = \{\langle\varphi\rangle \mid \varphi \text{ igaz TKBF}\}$.)
**Bizonyítás:**
**QSAT $\in$ PSPACE:** Az $\mathrm{ÉRTÉK}(\varphi)$ függvény rekurzív kiszámítása: $\varphi = Qx\psi$ esetén kiszámoljuk $\psi^i$ ($x$ igaz) és $\psi^h$ ($x$ hamis) értékét, majd $Q$ szerint kombináljuk. A rekurzió mélysége a változók száma; minden szinten egy igazságérték tárolódik $\Rightarrow$ lineáris tár.
**QSAT PSPACE-nehéz:** Tetszőleges $L \in \mathrm{PSPACE}$-re, $L$-t eldöntő $n^k$ tárú $M$ TG-hez egy $\varphi$ TKBF-et konstruálunk úgy, hogy $w \in L(M) \iff \langle\varphi\rangle \in \mathrm{QSAT}$. A konfigurációkat **konfiguráció-azonosító halmazok** (KH) változócsoportjaival reprezentáljuk. A $\varphi_{C,D,t}$ formula azt fejezi ki, hogy $M$ el tud jutni $C$-ből $D$-be legfeljebb $t$ lépésben. **Savitch felezésével**, de a középső konfigurációt **univerzális kvantorral** osztjuk, hogy a formula mérete ne duplázódjon, így polinom méretű maradjon:
$$\varphi_{C,D,t} = \exists M\,\forall C_1\forall C_2\big((C_1{=}C \wedge C_2{=}M) \vee (C_1{=}M \wedge C_2{=}D) \to \varphi_{C_1,C_2,\lceil t/2\rceil}\big).$$
A rekurzió mélysége $O(\log T) = O(\log 2^{n^k}) = O(n^k)$, minden szinten polinom méretű új formula adódik — a teljes $\varphi$ polinom méretű, polinom időben megkonstruálható. $\square$
## Logaritmikus tárbonyolultság (L, NL)
### Tétel (3.44.): Az irányított gráf-elérhetőség NL-teljes — ($\mathrm{ELÉRHETŐSÉG}$ NL-teljes)
**Tétel (3.44.):** ELÉRHETŐSÉG NL-teljes.
(ELÉRHETŐSÉG: adott $G=(V,E)$ irányított gráf és $s,t$, van-e út $s$-ből $t$-be.)
**Bizonyítás:**
**$\in$ NL:** Egy NTG az aktuális csúcsot ($u$, kezdetben $s$) és egy lépésszámlálót tárol $O(\log|V|)$ tárral; nemdeterminisztikusan választ egy $u$-ból elérhető $v$ csúcsot, $|V|$ lépésig.
**NL-nehéz:** Tetszőleges $L \in \mathrm{NL}$-re az $L$-t eldöntő $O(\log n)$ tárú NTG $M$ **konfigurációs gráfja** $G$ logaritmikus tárral megkonstruálható (csúcs = $M$ aktuális konfigurációja, él = $\delta$-átmenet), és $u \in L \iff$ $G$-ben van út $c_{kezdő}$-ből $c_{elfogadó}$-ba. $\square$
**Következmény (3.45.):** $\mathrm{NL} \subseteq \mathrm{P}$. (Egy $O(\log n)$ tárú NTG konfigurációs gráfja polinom méretű, így ELÉRHETŐSÉG benne polinom időben eldönthető.)
### Tétel (Immermann–Szelepcsényi): NL zárt komplementerre — NL=coNL — ($\mathrm{NL} = \mathrm{coNL}$)
**Tétel (3.46. — Immermann–Szelepcsényi):** $\mathrm{NL} = \mathrm{coNL}$.
**Bizonyítás (vázlat):** Megmutatjuk, hogy $\overline{\mathrm{ELÉRHETŐSÉG}} \in \mathrm{NL}$ — azaz NL-es TG-pel eldönthető, hogy *nincs* út $s$-ből $t$-be.
Az ötlet: az $s$-ből pontosan $\leq i$ lépésben elérhető csúcsok $d_i$ számát induktívan kiszámítjuk ($d_0 = 1$). $d_{i+1}$ kiszámításához minden csúcsra nemdeterminisztikusan **megsejtjük**, hogy elérhető-e $\leq i$ lépésben, és a sejtést $\leq i$ hosszú útkereséssel **ellenőrizzük** — közben számoljuk, hogy a megtalált elérhető csúcsok száma eléri-e $d_i$-t (ha nem éri el, az ellenfél „csalt", elutasítunk). Végül $d_{|V|}$ ismeretében: $t$ akkor és csak akkor nem elérhető, ha az NTG végig tudja sorolni $d_{|V|}$ darab elérhető csúcsot $t$ nélkül.
Tár: $O(\log|V|)$ a számlálóknak és az aktuális csúcsnak. $\Rightarrow$ $\overline{\mathrm{ELÉRHETŐSÉG}} \in \mathrm{NL}$, ami coNL-teljes (3.26. tétel), tehát (3.28.) $\mathrm{NL} = \mathrm{coNL}$. $\square$
