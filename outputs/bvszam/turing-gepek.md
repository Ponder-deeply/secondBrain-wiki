#flashcards/bvszam/turing-gepek
## 1. Mi volt Hilbert programja, és miért bizonyult megvalósíthatatlannak?
?
Hilbert az 1920-as években formalizálni és axiomatizálni szerette volna a matematika teljes elméletét egy véges, teljes és konzisztens axiómarendszerrel; ennek része volt egy **Mindent Megoldó Algoritmus (MMA)** megadása, ami minden matematikai állításról eldönti, igaz-e. Gödel első nemteljességi tétele megmutatta, hogy minden természetes számok elméletét tartalmazó, effektíven kiszámítható elmélet nem lehet egyszerre helyes és teljes — tehát a program alapvetően megvalósíthatatlan.
---

## 2. Mi a Church–Turing tézis?
?
A Church–Turing tézis azt mondja ki, hogy a kiszámíthatóság különböző matematikai modelljei (rekurzív függvények, $\lambda$-kalkulus, Turing-gépek stb.) mind az effektíven kiszámítható függvények osztályát definiálják. Nem bizonyítható matematikai tétel, hanem széles körben elfogadott azonosítás az intuitív algoritmusfogalom és a formális modellek között.
---

## 3. Mikor és kik alapozták meg a kiszámíthatóságelméletet?
?
- **1934:** Gödel definiálta a rekurzív függvényeket.
- **1930-as évek:** Alonzo Church és tanítványai megalkották a $\lambda$-kalkulust.
- **1936:** Alan Turing definiálta a Turing-gépeket.
- **1970:** Jurij Matijaszevics megmutatta, hogy Hilbert 10. problémája (egész együtthatós polinom egész gyöke) algoritmikusan eldönthetetlen.
---

## 4. Hogyan definiálható formálisan egy eldöntési probléma?
?
Egy **eldöntési probléma** speciális kiszámítási probléma, ahol a válasz `igen` vagy `nem`. A pozitív bemenetek (igen példányok) kódjait tartalmazó formális nyelv azonosítható a problémával. A $D$ objektum kódolása: $\langle D \rangle$. Az eldöntési problémák nem szűkítik az általánosságot: tetszőleges $f_P : A \to B$ problémához megadható ekvivalens eldöntési probléma (az $(a, b)$ párok elfogadása, ahol $b = f_P(a)$).
---

## 5. Miért létezik biztosan eldönthetetlen probléma?
?
Mivel az eldöntési problémák megfelelnek a formális nyelveknek, annyi probléma van, amennyiféle formális nyelv: $|\mathcal{P}(\mathbb{N})|$, azaz **megszámlálhatatlanul** sok. Az algoritmusok halmaza ezzel szemben **megszámlálhatóan** végtelen (minden algoritmus végesen kódolható). Mivel nagyságrendileg több probléma van, mint algoritmus, biztosan létezik eldönthetetlen probléma.
---

## 6. Adja meg a Turing-gép formális definícióját!
?
A Turing-gép egy $M = (Q, \Sigma, \Gamma, \delta, q_0, q_i, q_n)$ rendszer, ahol:
- $Q$ — az állapotok véges, nemüres halmaza
- $q_0, q_i, q_n \in Q$ — a kezdő-, az elfogadó és az elutasító állapot
- $\Sigma$ — a bemenő jelek ábécéje
- $\Gamma$ — a szalagszimbólumok ábécéje, $\Sigma \subseteq \Gamma$; $\Gamma \setminus \Sigma$ tartalmazza az üres szimbólumot ($\sqcup$)
- $\delta : (Q \setminus \{q_i, q_n\}) \times \Gamma \to Q \times \Gamma \times \{L, R, S\}$ — az átmenetfüggvény
A fej egy lépésben olvas/ír egy cellát, és balra ($L$), jobbra ($R$) lép, vagy helyben marad ($S$).
---

## 7. Mi a Turing-gép konfigurációja, és hogyan néz ki a konfiguráció-átmenet?
?
Egy $M$ **konfigurációja** egy $uqav$ szó, ahol $q \in Q$ az aktuális állapot, $a \in \Gamma$ a fej alatti szimbólum, $u, v \in \Gamma^*$ a szalag baloldali és jobboldali tartalma. A **kezdőkonfiguráció:** $q_0 u \sqcup$.
Konfiguráció-átmenet ($\vdash$), ha $\delta(q, a) = (r, b, D)$:
- $D = S$: $uqav \vdash urbv$
- $D = R$: $uqav \vdash ubrv'$ (ha $v = \varepsilon$, akkor $v' = \sqcup$)
- $D = L$: $u'cqav \vdash u'rcbv$ (ha $u = \varepsilon$, akkor $c = \sqcup$)
$\vdash^*$ a $\vdash$ reflexív-tranzitív lezártja.
---

## 8. Mikor fogad el, illetve utasít el egy Turing-gép egy szót? Mi a felismert nyelv?
?
$M$ **elfogadja** az $u$ szót, ha a $q_0 u \sqcup$ kezdőkonfigurációból véges sok lépés után elfogadó konfigurációba ($q_i$) kerül. $M$ **elutasítja** $u$-t, ha $q_n$-be lép; egyébként **nem áll meg** rajta.
$$L(M) = \{u \in \Sigma^* \mid q_0 u \sqcup \vdash^* x q_i y,\ x,y \in \Gamma^*\}$$
---

## 9. Mit jelent, hogy egy nyelv Turing-felismerhető (RE), illetve eldönthető (R)?
?
- $L \in \text{RE}$ (**rekurzívan felsorolható**): létezik $M$ TG, amelyre $L = L(M)$; $M$ nem-$L$-beli szavakon megállhat elutasítóban vagy hurokba eshet.
- $L \in \text{R}$ (**rekurzív / eldönthető**): létezik $M$ TG, amely minden bemenetre megáll, és $L = L(M)$.
$$\text{R} \subsetneq \text{RE} = \mathcal{L}_0$$
---

## 10. Hogyan értelmezzük a Turing-gép időigényét?
?
$M$ **időigénye az $u$ szón** $n$, ha $M$ a $q_0 u \sqcup$ kezdőkonfigurációból $n$ lépésben megállási konfigurációba jut (ha nincs ilyen, az időigény végtelen). $M$ **$f(n)$ időkorlátos**, ha minden $u$ bemenetre az időigény legfeljebb $f(l(u))$, ahol $l(u)$ a szó hossza. Egy $L$ nyelv **$f(n)$ időben eldönthető**, ha eldönthető egy $f(n)$ időkorlátos (akár többszalagos) TG-vel.
---

## 11. Adja meg a $k$-szalagos Turing-gép definícióját és átmenetfüggvényét!
?
A $k$-szalagos TG-ben $M = (Q, \Sigma, \Gamma, \delta, q_0, q_i, q_n)$, ahol az átmenetfüggvény:
$$\delta : (Q \setminus \{q_i, q_n\}) \times \Gamma^k \to Q \times \Gamma^k \times \{L, R, S\}^k$$
Ha $\delta(q, a_1, \ldots, a_k) = (p, b_1, \ldots, b_k, D_1, \ldots, D_k)$, a gép $q$ állapotban, ha szalagjain $a_1, \ldots, a_k$-t olvassa, $p$-be megy, $a_i$-t $b_i$-re írja, a fejeket $D_i$ irányba lépteti. Az átmenetdiagram jelölése:
$$q \xrightarrow{a_1,\ldots,a_k /\; b_1,\ldots,b_k,\; D_1,\ldots,D_k} p$$
---

## 12. Milyen időigénnyel dönthet el $k$-szalagos TG egy nyelvet az egyszalagoshoz képest? Mutasson példát!
?
A $k$-szalagos TG időbonyolultsági szempontból hatékonyabb lehet. Példa: $L = \{ww^{-1} \mid w \in \{a,b\}^*\}$ esetén:
- Kétszalagos TG: az inputot a 2. szalagra másolja, majd tükörképet hasonlít össze — időigénye $O(n)$ (lineáris).
- Egyszalagos megoldás: $O(n^2)$ időigényű.
A számítási erő (felismert nyelvek osztálya) azonos az egyszalagos TG-vel.
---

## 13. Fogalmazza meg a $k$-szalagos TG és az egyszalagos TG ekvivalenciájáról szóló tételt (2.7. tétel)!
?
**Tétel (2.7):** Minden $M$ $k$-szalagos TG-hez megadható vele ekvivalens egyszalagos $M'$ TG (azaz $L(M) = L(M')$). Ha $M$ legalább lineáris időigényű ($f(n) = \Omega(n)$), akkor $M'$ az $O(f(n)^2)$ időkorláttal dolgozik.
---

## 14. Vázolja a $k$-szalagos TG szimulálásának módszerét egyszalagos géppel!
?
$M'$ egymás után tárolja $M$ szalagjainak tartalmát egyetlen szalagon, `#` elválasztóval:
$$\# \underbrace{a_1 a_2 \ldots}_{\text{1. szalag}} \# \underbrace{\sqcup}_{\text{2. szalag}} \# \cdots \#$$
Az aktuális fejpozíciót minden szegmensben egy `^`-jelölt szimbólum (`â`) mutatja. Szimulációs fázisok:
1. **Olvasófázis:** $M'$ végigpásztáz, eltárolja a dot-jelzett szimbólumokat.
2. **Írófázis:** $\delta$ alapján frissíti a jelzéseket, lépteti a dot-jelzéseket.
3. Ha a dot-jelzés kívülre kerülne, $M'$ tolja jobbra a szalagon a tartalmat.
Időköltség: $M$ egy lépéséhez $O(n + f(n))$ lépés kell $M'$-ben, összesen $O(f(n)^2)$.
---

## 15. Mi az egyirányú Turing-gép, és miért ekvivalens a kétirányúval?
?
Az **egyirányú TG** balra zárt, jobbra végtelen szalagon dolgozik — a fej nem mehet a bal szélen túl. Az eredeti modell neve ilyenkor **többirányú TG**.
**Tétel:** Minden többirányú TG-hez megadható ekvivalens egyirányú TG.
**Vázlat:** Megkonstruálunk egy kétszalagos egyirányú $M'$-t: az 1. szalag az $M$ szalagjának kezdőpozíciótól jobbra eső részét, a 2. szalag a tükörképét (a balra eső részt) tárolja. Ha $M$ a kezdőponttól jobbra lép, $M'$ az 1. szalagon; ha balra, $M'$ a 2. szalagon (ellentétes irányban) szimulálja a lépést.
---

## 16. Adja meg a nemdeterminisztikus Turing-gép (NTG) definícióját!
?
Az NTG egy $M = (Q, \Sigma, \Gamma, \delta, q_0, q_i, q_n)$ rendszer, ahol az átmenetfüggvény:
$$\delta : (Q \setminus \{q_i, q_n\}) \times \Gamma \to \mathcal{P}(Q \times \Gamma \times \{L, R\})$$
(A determinisztikussal szemben az átmenet értéke halmazok halmaza.) $M$ **elfogadja** $u$-t, ha a számítási fában van legalább egy elfogadó ágú levél. $M$ **eldönti** $L$-t, ha felismeri, és minden számítási sorozata véges és elfogadó vagy elutasító.
---

## 17. Mi az NTG számítási fája, és hogyan értelmezzük az időigényt NTG esetén?
?
Az $M$ NTG **számítási fája** $u$-n: gyökere az $u$-ra vonatkozó kezdőkonfiguráció, szögpontjai konfigurációk, élei konfiguráció-átmenetek, levelei véges számítási sorozatok végállapotai. Az NTG **időigénye $f(n)$** ($f : \mathbb{N} \to \mathbb{N}$), ha minden $n$ hosszú $u$ bemeneten a számítási fa magassága legfeljebb $f(n)$ — azaz egyetlen számítási sorozat sem hosszabb $f(n)$-nél.
---

## 18. Bizonyítsa, hogy minden NTG szimulálható determinisztikus TG-vel! Mekkora az időköltség?
?
**Tétel:** Minden $M$ NTG-hez megadható ekvivalens $M'$ determinisztikus TG.
**Bizonyítás (3-szalagos DTG, szélességi keresés):**
- 1. szalag: az $u$ bemenet (érintetlen).
- 2. szalag: szimulálandó számítási sorozat aktuális konfigurációja.
- 3. szalag (szelektoros): $\{1,\ldots,d\}$ feletti szó ($d$ = legnagyobb leágazási fok), az aktuálisan bejárt ág kódolása.
$M'$ a 3. szalagon hosszlexikografikus sorrendben lép, így szélességi kereséssel bejárja $M$ teljes számítási fáját — megtalál minden véges elfogadó ágat.
**Időköltség:** a szimuláció exponenciális időigény-romlással járhat (a fa konfigurációinak száma $M$ mélységében exponenciális). Nem ismert hatékonyabb szimuláció, de az sem bizonyított, hogy nincs (vö. **P vs NP**).
---

## 19. Mit jelent, hogy $L \in \text{RE}$ pontosan akkor, ha felismeri NTG?
?
**Tétel:** $L \in \text{RE} \iff$ létezik $L$-t felismerő NTG.
Bizonyítás: ($\Rightarrow$) Minden DTG speciális NTG. ($\Leftarrow$) Minden NTG szimulálható ekvivalens DTG-vel (az előző tétel alapján), tehát az NTG által felismert nyelv RE-beli. Következmény: NTG és DTG ugyanazokat a nyelveket ismerik fel, csak időbonyolultságban különbözhetnek.
---

## 20. Hogyan kódolhatunk $\{0,1\}$ bemeneti ábécéjű Turing-gépet bináris szóval?
?
Legyen $M = (Q, \{0,1\}, \Gamma, \delta, q_0, q_i, q_n)$, $|Q|=k$, $|\Gamma|=m$. Állapotok: $p_1=q_0$, $p_{k-1}=q_i$, $p_k=q_n$; szimbólumok: $X_1=0$, $X_2=1$, $X_3=\sqcup$; irányok: $D_1=L$, $D_2=R$, $D_3=S$.
Egy $\delta(p_i, X_j) = (p_r, X_s, D_t)$ átmenet kódja:
$$0^i 1 0^j 1 0^r 1 0^s 1 0^t$$
(nem tartalmaz `11` részszót). Az összes átmenetet `11`-gyel elválasztva fűzzük össze: ez $\langle M \rangle$. Az $M_i$ jelöli azt a gépet, amelyet a $w_i$ bináris szó kódol (hosszlexikografikus sorrend szerint); ha $w_i$ nem érvényes kód, $M_i$ minden inputon $q_n$-be megy.
---

## 21. Hogyan kódolunk $(M, w)$ párt bináris szóval?
?
Mivel az átmenetkódolásban nem fordulhat elő három `1`-es egymás mellett, az $(M, w)$ párt az alábbival kódoljuk:
$$\langle M, w \rangle = \langle M \rangle\, 111\, w$$
A `111` a határoló, amely egyértelműen elválasztja a gép kódját a bemenettől.
---

## 22. Mi az $L_u$ (univerzális) nyelv, és miért $L_u \in \text{RE}$?
?
$$L_u = \{\langle M, w \rangle \mid w \in L(M)\}$$
**Tétel:** $L_u \in \text{RE}$.
**Bizonyítás:** Az **univerzális Turing-gép** $U$ 4 szalagot használ:
1. $\langle M, w \rangle$ (csak olvasható)
2. $M$ aktuális szalagtartalma és fejpozíciója
3. $M$ aktuális állapota
4. segédszalag
$U$ ellenőrzi az érvényes kódolást, majd lépésről lépésre szimulálja $M$ működését $w$-n. Ha $M$ elfogad/elutasít, $U$ is belép saját elfogadó/elutasító állapotába. Ha $M$ nem áll meg $w$-n, $U$ sem áll meg — ezért $U$ csak felismeri, de nem dönti el $L_u$-t.
---

## 23. Miért $L_u \notin \text{R}$? (Diagonalizációs bizonyítás vázlata)
?
**Tétel:** $L_u \notin \text{R}$.
**Bizonyítás (indirekt, diagonalizáció):** Tegyük fel, hogy létezik $L_u$-t eldöntő $D$ TG. Ebből megkonstruálhatunk egy $D'$ TG-t: $D'$ az $\langle M \rangle$ inputon elfogad, ha $D$ elutasítja $\langle M, \langle M \rangle \rangle$-t (azaz $\langle M \rangle \notin L(M)$), és elutasít, ha $D$ elfogad. $D'$ a saját kódolásán $\langle D' \rangle$ paradoxont okoz: elfogad $\iff$ nem fogad el. Ellentmondás.
---

## 24. Mi a megállási probléma, és eldönthető-e?
?
$$L_{\text{halt}} = \{\langle M, w \rangle \mid M \text{ megáll } w\text{-n}\}$$
**Tétel:** $L_{\text{halt}} \notin \text{R}$ (nem eldönthető).
Bizonyítás: $L_u$ visszavezethető $L_{\text{halt}}$-ra. Ha $L_{\text{halt}}$ eldönthető lenne, abból $L_u$-t is el lehetne dönteni — de $L_u \notin \text{R}$, ellentmondás.
---

## 25. Igaz-e, hogy $\overline{L_u} \in \text{RE}$?
?
**Nem.** $\overline{L_u} \notin \text{RE}$.
**Bizonyítás:** Ha $\overline{L_u} \in \text{RE}$ lenne, akkor $L_u$ egyszerre $\text{RE}$-beli (már tudjuk) és komplementere is $\text{RE}$-beli lenne. Az $L \in \text{R} \iff L \in \text{RE}$ és $\bar{L} \in \text{RE}$ tétel alapján ez $L_u \in \text{R}$-t adna — de $L_u \notin \text{R}$. Ellentmondás.
---

## 26. Mikor teljesül, hogy $L \in \text{R}$? (Jellemzés RE és co-RE segítségével)
?
**Tétel:** $L \in \text{R} \iff L \in \text{RE}$ és $\bar{L} \in \text{RE}$.
**Bizonyítás:**
- ($\Rightarrow$): Ha $L \in \text{R}$, akkor $\bar{L} \in \text{R} \subseteq \text{RE}$ (a döntő gép komplementezve dönti el $\bar{L}$-t).
- ($\Leftarrow$): Két TG fut párhuzamosan — $M_1$ felismeri $L$-t, $M_2$ felismeri $\bar{L}$-t. Minden bemeneten pontosan az egyik áll meg elfogadóan → az így kapott gép mindenhol megáll → $L \in \text{R}$.
---

## 27. Mi a kiszámítható szófüggvény?
?
Az $f : \Sigma^* \to \Delta^*$ szófüggvény **kiszámítható**, ha létezik olyan Turing-gép, amely minden $u \in \Sigma^*$-ra megáll, és megálláskor $f(u)$ olvasható az utolsó szalagon. Ez pontosan a Church–Turing tézis értelmében vett algoritmikusan kiszámítható függvény. (Megjegyzés: szófüggvényt számoló TG esetén $q_i$ és $q_n$ megkülönböztetése felesleges — egyetlen megállási állapot elég.)
---

## 28. Hogyan azonosítható a $\mathcal{L}_0$ grammatikaosztály a RE-vel?
?
**Tétel:** $L \in \mathcal{L}_0 \iff L \in \text{RE}$.
- ($\mathcal{L}_0 \subseteq \text{RE}$): Minden $G$ grammatikához megadható $L(G)$-t felismerő NTG: nemdeterminisztikusan alkalmaz grammatikai szabályokat, és elfogad, ha a kapott szó egyezik az inputtal.
- ($\text{RE} \subseteq \mathcal{L}_0$): Minden $M$ DTG-hez megkonstruálható $G$ grammatika, amely $M$ konfigurációinak sorozatait generálja; a generált szó pontosan $L(M)$.
Következmény: $\mathcal{L}_0 = \text{RE}$ és $\text{R} \subsetneq \text{RE}$.
---

## 29. Mi a lineárisan korlátolt automata (LKA)?
?
Az LKA egy **nemdeterminisztikus TG**, amelynek szalagja korlátolt: a bemenetet bal és jobb végjelekkel ($\$_L$, $\$_R$) határolják, és a fej nem léphet ezeken túl (munkaterület $\leq |w|$ cella). Elfogadás: szokásos TG-elfogadó állapottal.
**Tétel:** $\mathcal{L}_1 =$ LKA által felismert nyelvek osztálya.
---

## 30. Miért dönthetők el az LKA által felismert nyelvek?
?
**Tétel:** Ha $A$ LKA, akkor $L(A) \in \text{R}$.
**Bizonyítás:** Az LKA lehetséges konfigurációinak száma $u$ bemenetre felülről becsülhető:
$$m(u) = |Q| \cdot |u| \cdot |\Gamma|^{|u|}$$
Ha van elfogadó számítás, van legfeljebb $m(u)$ hosszú elfogadó számítás. Egy determinisztikus TG szimulálhatja az LKA-t pontosan $m(u)$ lépésig, majd leáll — így $L(A) \in \text{R}$.
---

## 31. Mondja ki a $\mathcal{L}_1 \subsetneq \text{R}$ tételt és vázoljon bizonyítást!
?
**Tétel:** $\mathcal{L}_1 \subsetneq \text{R}$ (a tartalmazás valódi).
**Bizonyítás (diagonalizáció):** Legyen $L_{\text{LKA-átló}} = \{\langle M \rangle \mid M \text{ LKA és } \langle M \rangle \notin L(M)\}$.
- $L_{\text{LKA-átló}} \in \text{R}$: az univerzális TG az LKA-t $m(w) = |Q| \cdot |w| \cdot |\Gamma|^{|w|}$ lépés után leállítva eldönti.
- $L_{\text{LKA-átló}} \notin \mathcal{L}_1$: ha valamilyen $A$ LKA felismerné, akkor $\langle A \rangle \in L_{\text{LKA-átló}} \iff \langle A \rangle \notin L(A)$, önhivatkozásos ellentmondás.
- Tehát $L_{\text{LKA-átló}} \in \text{R} \setminus \mathcal{L}_1$.
---

## 32. Foglalja össze a Chomsky-hierarchiát és a kapcsolódó automataosztályokat!
?
| Osztály | Grammatika | Automata |
|---------|-----------|---------|
| $\mathcal{L}_3$ | 3-típusú (reguláris) | véges determinisztikus/nemdeterminisztikus automata |
| $\mathcal{L}_2$ | 2-típusú (környezetfüggetlen) | (nemdeterminisztikus) veremautomata |
| $\mathcal{L}_1$ | 1-típusú (környezetfüggő) | lineárisan korlátolt automata (LKA) |
| $\text{R}$ | — | minden inputra megálló TG |
| $\text{RE} = \mathcal{L}_0$ | 0-típusú | Turing-gép / NTG |
Összefüggések: $\mathcal{L}_2 \subsetneq \mathcal{L}_1 \subsetneq \text{R} \subsetneq \text{RE} = \mathcal{L}_0$.
---

## 33. Mi a 0-típusú grammatika normálformája?
?
**Tétel:** Bármely $G = \langle N, T, P, S \rangle$ 0-típusú grammatikához megadható ekvivalens $G'$, amelynek szabályai csak az alábbi alakúak:
- $S \to \varepsilon$ (és $S$ nem szerepel más szabály jobboldalán)
- $A \to a$ ($A \in N$, $a \in T$)
- $A \to B$ ($A, B \in N$)
- $A \to BC$ ($A, B, C \in N$)
- $AB \to B$ ($A, B \in N$)
- $AB \to AC$ ($A, B, C \in N$)
- $BA \to CA$ ($A, B, C \in N$)
---

## 34. Hogyan rendezzük sorba a $\{0,1\}^*$ szavait, és mit jelöl $w_i$ ill. $M_i$?
?
A $\{0,1\}^*$ szavait **hosszlexikografikusan** rendezzük (hossz szerint, azonos hosszúak között lexikografikusan):
$$w_1 = \varepsilon,\quad w_2 = 0,\quad w_3 = 1,\quad w_4 = 00,\quad w_5 = 01,\ \ldots$$
$M_i$ jelöli azt a $\{0,1\}$ bemeneti ábécéjű TG-t, amelyet a $w_i$ szó kódol. Ha $w_i$ nem érvényes TG-kód, $M_i$ az a gép, amely minden inputon azonnal $q_n$-be megy ($L(M_i) = \emptyset$). Adott $i$-re $w_i$ véges sok lépésben kiszámítható.
---

## 35. Miért nem dönti el az UTG az $L_u$-t, csupán ismeri fel?
?
Az **univerzális Turing-gép** $U$ szimulálja $M$ működését $w$-n: ha $M$ elfogad, $U$ elfogad; ha $M$ elutasít, $U$ elutasít. Azonban ha $M$ nem áll meg $w$-n, $U$ sem áll meg $\langle M, w \rangle$-n — végtelen ciklusba esik. Ezért $U$ nem döntő (nem totálisan definiált) gép: nem garantált, hogy minden bemeneten megáll. Következmény: $L_u \in \text{RE} \setminus \text{R}$.
---

