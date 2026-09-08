#flashcards/bvszam/bonyolultsagelmelet
## 1. Mit jelöl az $O(g)$ jelölés, és hogyan definiálják formálisan?
?
$O(g) := \{ f \mid \exists c > 0,\ \exists N \in \mathbb{N},\ \forall n > N : f(n) \le c \cdot g(n) \}$. Azaz $f$ aszimptotikusan legfeljebb $g$ nagyságrendű: $c$ konstans szorosánál nagyobb értékeket nem vesz fel egy $N$ küszöb után.
---

## 2. Mi a kapcsolat az $O$, $\Omega$ és $\Theta$ jelölések között?
?
$f = \Omega(g) \Leftrightarrow g = O(f)$, és $f = \Theta(g) \Leftrightarrow f = O(g)$ és $f = \Omega(g)$. A $\Theta$ ekvivalenciarelációt definiál; az $O$ és $\Omega$ fordítottan szimmetrikusak egymáshoz képest.
---

## 3. Mit mond ki a szekvenciatétel az aszimptotikus jelölésekre?
?
$f + g = \Theta(\max\{f, g\})$ — az összeg aszimptotikus nagyságrendjét a domináns tag (a kettő közül a nagyobb) határozza meg. Ha pl. $f = O(h)$ és $g = O(h)$, akkor $f + g = O(h)$.
---

## 4. Hogyan viszonyul egymáshoz polinom és exponenciális függvény aszimptotikusan?
?
Minden $p(n)$ polinomra és $c > 1$ konstansra: $p(n) = O(c^n)$, de $p(n) \neq \Omega(c^n)$ — azaz az exponenciális dominál a polinom felett. Hasonlóan, $\log n = O(n^c)$ minden $c > 0$-ra, de $\log n \neq \Omega(n^c)$.
---

## 5. Mi a TIME és NTIME osztály definíciója?
?
$$\text{TIME}(f(n)) = \{L \mid L \text{ eldönthető } O(f(n)) \text{ időigényű determinisztikus TG-pel}\}$$
$$\text{NTIME}(f(n)) = \{L \mid L \text{ eldönthető } O(f(n)) \text{ időigényű nemdeterminisztikus TG-pel}\}$$
---

## 6. Hogyan definiálják a P és NP osztályokat?
?
$$\text{P} = \bigcup_{k \geq 1} \text{TIME}(n^k) \qquad \text{(polinom idejű determinisztikus TG)}$$
$$\text{NP} = \bigcup_{k \geq 1} \text{NTIME}(n^k) \qquad \text{(polinom idejű nemdeterminisztikus TG)}$$
$\text{P} \subseteq \text{NP}$, mert minden DTG tekinthető NTG-nek.
---

## 7. Mi az NP alternatív, tanú-alapú definíciója?
?
$L \in \text{NP}$ akkor és csak akkor, ha van olyan $L_V \in \text{P}$ ellenőrző nyelv és $k \geq 1$, hogy
$$L = \{u \mid \exists v : (u,v) \in L_V \text{ és } l(v) = O(l(u)^k)\}.$$
Azaz egy „tömör tanú" ($O(n^k)$ méretű bizonyíték) polinom időben ellenőrizhető. Az NTG ezt úgy valósítja meg, hogy nemdeterminisztikusan „megsejti" a tanút, majd ellenőrzi.
---

## 8. Mi a polinom idejű visszavezetés ($\leq_p$) definíciója?
?
$L_1 \leq_p L_2$, ha létezik polinom időben kiszámítható $f$ függvény, amelyre $w \in L_1 \iff f(w) \in L_2$. Az $f$ a visszavezető függvény. P és NP egyaránt zárt a $\leq_p$-re nézve.
---

## 9. Mikor NP-teljes, illetve NP-nehéz egy probléma?
?
$L$ **NP-teljes**, ha (1) $L \in \text{NP}$, és (2) minden $L' \in \text{NP}$-re $L' \leq_p L$. Ha csak (2) teljesül, $L$ **NP-nehéz**. NP-teljes probléma megoldhatósága P-ben azt jelenti, hogy $\text{P} = \text{NP}$.
---

## 10. Mit mond ki az NP-teljesség terjesztési tétele?
?
Ha $L_1$ NP-teljes, $L_2 \in \text{NP}$, és $L_1 \leq_p L_2$, akkor $L_2$ is NP-teljes. Bizonyítás: tetszőleges $L \in \text{NP}$-re $L \leq_p L_1 \leq_p L_2$; a $\leq_p$ tranzitivitása (polinom polinomban polinom) miatt $L \leq_p L_2$.
---

## 11. Mit mond ki a Cook–Levin tétel, és miért fontos?
?
A Cook–Levin tétel szerint a SAT (Boole-formulák kielégíthetősége) NP-teljes. Ez az első NP-teljes probléma, amelyet közvetlenül a definícióból bizonyítottak (táblakódolással). Minden további NP-teljességi bizonyítás visszavezetésen alapul, amelynek lánca SAT-ból indul.
---

## 12. Mit jelent a táblakódolás (tableau) a Cook–Levin bizonyításban?
?
Egy $p(n)$ lépésidejű NTG $M$ $w$ bemenetű számítása leírható egy $(p(n)+1) \times (2p(n)+3)$ méretű $T$ táblával, amelynek celláiban $\Delta = Q \cup \Gamma \cup \{\#\}$ szimbólumok állnak. A $x_{i,j,s}$ változó igaz, ha a $T[i,j]$ cellában $s$ szimbólum van. A $\varphi_w$ formula ezt kódolja.
---

## 13. Milyen részekből áll a Cook–Levin bizonyítás $\varphi_w$ formulája?
?
$$\varphi_w := \varphi_0 \land \varphi_{start} \land \varphi_{move} \land \varphi_{accept}$$
- $\varphi_0$: minden cellában pontosan egy szimbólum.
- $\varphi_{start}$: az első sor a $w$ bemeneti kezdőkonfigurációt kódolja.
- $\varphi_{move}$: egymást követő sorok érvényes TG-lépések (illegális 2×3-as ablakok tiltásával, KNF alakban).
- $\varphi_{accept}$: az utolsó sorban van elfogadó állapot.
Az egész formula $O(p^2(n))$ méretű — polinom időben megkonstruálható.
---

## 14. Mi a $k$SAT és a 3SAT probléma definíciója?
?
$k\text{SAT} = \{ \langle \varphi \rangle \mid \varphi \in \text{SAT}, \text{ és } \varphi \text{ minden klóza pontosan } k \text{ literált tartalmaz} \}$. A 3SAT 3-literálos KNF formulák kielégíthetőségét kérdezi. 3SAT NP-teljes, mert SAT $\leq_p$ 3SAT klózbontó transzformációval.
---

## 15. Hogyan zajlik a SAT $\leq_p$ 3SAT visszavezetés?
?
Minden klózt 3-literálosra alakítunk segédváltozókkal ($x, y, x_1, \ldots$):
- 1 literál ($l$): négy klózra bontjuk ($l \lor x \lor y$, stb.)
- 2 literál ($l_1 \lor l_2$): $l_1 \lor l_2 \lor x$ és $l_1 \lor l_2 \lor \neg x$
- 3 literál: változatlan
- 4 literál ($l_1 \lor l_2 \lor l_3 \lor l_4$): $l_1 \lor l_2 \lor x$ és $\neg x \lor l_3 \lor l_4$
- $n \geq 5$ literál: láncolva: $l_1 \lor l_2 \lor x_1,\ \neg x_1 \lor l_3 \lor x_2,\ \ldots,\ \neg x_{n-3} \lor l_{n-1} \lor l_n$
A transzformáció kielégíthetőséget megőriz.
---

## 16. Miért teljesül a $\leq_p$ tranzitivitása, és miért fontos ez?
?
Ha $f$ ($p_1(n)$ idejű) vezeti vissza $L_1$-et $L_2$-re, és $g$ ($p_2(n)$ idejű) $L_2$-t $L_3$-ra, akkor $g \circ f$ visszavezeti $L_1$-et $L_3$-ra. Mivel $|f(w)| \leq n + p_1(n)$, a kompozíció időigénye $p_2(n + p_1(n))$ — polinom polinomban polinom. Ez teszi lehetővé az NP-teljességi lánc felépítését.
---

## 17. Mi a 2SAT probléma és hogyan oldható meg hatékonyan?
?
2SAT: kielégíthetőség 2-literálos KNF formulákra. Megoldás: $G_\varphi$ **implikációs gráf** felépítésével ($l_i \lor l_j$ klózhoz $\neg l_i \to l_j$ és $\neg l_j \to l_i$ élek), majd az **erősen összefüggő komponensek (EÖK)** meghatározásával. $\varphi$ akkor és csak akkor kielégíthetetlen, ha valamely $x_i$ és $\neg x_i$ azonos EÖK-ban van. Tarjan-algoritmussal $O(n+m)$ időben megoldható — tehát 2SAT $\in$ P.
---

## 18. Mi a kielégítő értékadás meghatározásának módja 2SAT esetén?
?
Minden $i$-re: $x_i = $ igaz, ha $G_\varphi$-ben $\neg x_i$-ből $x_i$-be vezet irányított út (vagyis $x_i$ EÖK-ja a topologikus sorrendben később jön); egyébként $x_i = $ hamis. Ez mindig érvényes értékadást ad, ha $x_i$ és $\neg x_i$ különböző EÖK-ban van.
---

## 19. Mi a Horn-formula, és miért könnyű a HORNSAT?
?
**Horn-formula:** olyan KNF, amelynek minden klóza **legfeljebb egy pozitív** (nem negált) literált tartalmaz. HORNSAT $\in$ P: a szokásos algoritmus a **mohó egységpropagáció** — ha egy klóz egyetlen literálból áll (egységklóz), az egyértelműen igaz; ezzel más klózok egyszerűsödnek, az eljárás addig folytatható, amíg ellentmondás vagy kielégítő értékadás adódik.
---

## 20. Mi a Teljes részgráf (Klikk) probléma, és hogyan bizonyítják NP-teljességét?
?
$\text{Teljes részgráf} = \{\langle G, k\rangle \mid G\text{-nek van } k \text{ csúcsú teljes részgráfja}\}$. NP-teljességét 3SAT $\leq_p$ Teljes részgráf mutatja: $\varphi = c_1 \land \dots \land c_k$ esetén a $G_\varphi$ gráfban minden $c_i$ klózhoz egy háromszög tartozik; az összes csúcsot összekötjük, **kivéve** az egy klózból és a komplementer literálokból adódó párokat. Pontosan akkor van $k$-klikk, ha $\varphi$ kielégíthető.
---

## 21. Mi a Független csúcshalmaz és a Csúcslefedés problémák közti kapcsolat?
?
Egy $n$ csúcsú $G$ gráfban $S \subseteq V$ ($|S|=k$) független halmaz $\iff$ $V \setminus S$ ($|V \setminus S|=n-k$) csúcslefedés. Tehát $\langle G, k\rangle \in \text{Független csúcshalmaz} \iff \langle G, n-k\rangle \in \text{Csúcslefedés}$. Ez a visszavezetés polinom idejű, így a Független csúcshalmaz NP-teljessége átadódik a Csúcslefedésnek.
---

## 22. Hogyan kapcsolódik egymáshoz Teljes részgráf és Független csúcshalmaz?
?
Legyen $\overline{G}$ a $G$ komplementer gráfja (ugyanazok a csúcsok, és két csúcs között pontosan akkor van él $\overline{G}$-ben, ha $G$-ben nincs). Ekkor $G$-ben van $k$ elemű klikk $\iff$ $\overline{G}$-ben van $k$ elemű független csúcshalmaz. A komplementer gráf polinom időben megkonstruálható, tehát Teljes részgráf $\leq_p$ Független csúcshalmaz.
---

## 23. Mi a 3SZÍNEZÉS probléma, és hogyan bizonyítható NP-teljes volta?
?
$\text{3SZÍNEZÉS} = \{\langle G \rangle \mid G \text{ 3-színezhető}\}$. NP-teljessége 3SAT $\leq_p$ 3SZÍNEZÉS visszavezetéssel adódik: $\varphi$ formulából $G_\varphi$ gráfot konstruálunk, ahol minden változóhoz egy komplementer pár csúcs, három palettacsúcs ($A, B, \top$ — klikk), és minden klózhoz egy ötszög-szerkezetű részgráf tartozik. A lemma: az ötszög 3-színezhető $\iff$ legalább egy literál igaz. Tehát $\varphi$ kielégíthető $\iff$ $G_\varphi$ 3-színezhető.
---

## 24. Mikor 2-színezhető egy gráf, és hogyan dönthető el?
?
Egy gráf pontosan akkor 2-színezhető, ha **páros gráf** (azaz nincs benne páratlan hosszú kör). Ez lineáris időben eldönthető BFS vagy DFS segítségével.
---

## 25. Mi a Hamilton-út (irányított) probléma, és hogyan bizonyítják NP-teljességét?
?
$\text{Hamilton-út} = \{\langle G, s, t\rangle \mid G \text{ irányított, van } s\text{-ből } t\text{-be Hamilton-út}\}$. NP-teljessége SAT $\leq_p$ Hamilton-út visszavezetéssel adódik: $\varphi$ KNF-hez $G_\varphi$ irányított gráfot építünk, amelyben minden $x_i$ változóhoz egy kétirányú soros részgráf tartozik (bal→jobb = igaz, jobb→bal = hamis), és minden klóz csúcsát egy kitérő kötötti hozzá a megfelelő változóhoz. Hamilton-út létezik $\iff$ $\varphi$ kielégíthető.
---

## 26. Hogyan következik az Irányítatlan Hamilton-út NP-teljessége az irányítottból?
?
Hamilton-út $\leq_p$ Irányítatlan Hamilton-út: minden $v$ csúcsot három csúccsá ($v^{(0)}, v^{(1)}, v^{(2)}$) bontunk, $\{v^{(0)},v^{(1)}\}$ és $\{v^{(1)},v^{(2)}\}$ élekkel; minden $(v,w)$ irányított élnek $\{v^{(2)}, w^{(0)}\}$ él felel meg. A három csúcs kényszeríti a $0 \to 1 \to 2$ irányt, így az irányítottság megőrződik irányítatlan gráfban.
---

## 27. Hogyan épül fel az Irányítatlan Hamilton-kör NP-teljességének bizonyítása?
?
Irányítatlan Hamilton-út $\leq_p$ Irányítatlan Hamilton-kör: $G$-hez egy új $u$ csúcsot veszünk, $u$-t összekötjük $s$-sel és $t$-vel. Az így kapott $G_k$-ban pontosan akkor van Hamilton-kör, ha $G$-ben van $s$-ből $t$-be Hamilton-út.
---

## 28. Mi a speciális eset segédtétel, és mire használják?
?
Ha $P_1$ a $P_2$ probléma speciális esete (azaz $P_1$ példányai egyben $P_2$ példányai), és $P_1$ NP-nehéz, akkor $P_2$ is NP-nehéz — mert egy $P_2$-t eldöntő algoritmus $P_1$-et is eldöntené. Alkalmazások: Utazó ügynök (Hamilton-kör speciális esete, minden él súlya 1), Leghosszabb út, Korlátozott feszítőfa.
---

## 29. Miért NP-teljes az Utazó ügynök, a Leghosszabb út és a Korlátozott feszítőfa?
?
- **Utazó ügynök:** az Irányítatlan Hamilton-kör speciális esete (minden élsúly 1, $k = |V|$).
- **Leghosszabb út:** a Tetszőleges Hamilton-út speciális esete ($k = |V|$).
- **Korlátozott feszítőfa ($k=2$):** pontosan akkor van Hamilton-út, ha van feszítőfa, amelynek minden csúcsfoka $\leq 2$.
Mindhárom a speciális eset segédtétel alapján NP-nehéz, és NP-beli is, tehát NP-teljes.
---

## 30. Mi a Ladner tétele, és mit jelent az NP-köztes osztály?
?
**Ladner tétele (1975):** Ha $\text{P} \neq \text{NP}$, akkor létezik olyan $L \in \text{NP}$, amelyre $L \notin \text{P}$ és $L$ nem NP-teljes. Az ilyen $L$ **NP-köztes**. Jelöltek: Gráf izomorfizmus (Babai László: $n^{O(\log n)}$ idejű algoritmus), Prímfaktorizáció (FACTORING $\in$ NP $\cap$ coNP).
---

## 31. Mi a coNP osztály definíciója, és mi a $\text{P} = \text{coP}$ tétel?
?
$\text{coNP} = \{L \mid \bar{L} \in \text{NP}\}$, azaz azon nyelvek osztálya, amelyek komplementere NP-beli. Általánosan: $\text{co}\mathcal{C} = \{\bar{L} \mid L \in \mathcal{C}\}$. **Tétel:** $\text{P} = \text{coP}$: ha $M$ polinom időben dönti el $L$-t, akkor $M'$ (az elfogadó/elutasító állapotok felcserélésével) polinom időben dönti el $\bar{L}$-t.
---

## 32. Mik a coNP-teljes problémák, és hogyan bizonyítják teljességüket?
?
$\text{UNSAT} = \{\langle \varphi \rangle \mid \varphi \text{ kielégíthetetlen}\}$ és $\text{TAUT} = \{\langle \varphi \rangle \mid \varphi \text{ tautológia}\}$ — mindkettő coNP-teljes. Bizonyítás: UNSAT = $\overline{\text{SAT}}$, SAT NP-teljes, ezért UNSAT coNP-teljes (3.26. tétel alapján). UNSAT $\leq_p$ TAUT: $\varphi \mapsto \neg\varphi$ polinom idejű visszavezetés.
---

## 33. Mi következne abból, ha egy coNP-teljes probléma NP-beli lenne?
?
A 3.28. tétel alapján: ha van $L \in \mathcal{C}$, amelyre $L$ co$\mathcal{C}$-teljes, akkor $\mathcal{C} = \text{co}\mathcal{C}$. Ezért ha pl. UNSAT $\in$ NP, akkor $\text{NP} = \text{coNP}$ következne. Ez utóbbit szintén nyitott sejtésnek tartják.
---

## 34. Mi a SPACE és NSPACE osztály definíciója, és mi a PSPACE?
?
$$\text{SPACE}(f(n)) = \{L \mid L \text{ eldönthető } O(f(n)) \text{ tárigényű determinisztikus TG-pel}\}$$
$$\text{NSPACE}(f(n)) = \{L \mid L \text{ eldönthető } O(f(n)) \text{ tárigényű nemdeterminisztikus TG-pel}\}$$
$$\text{PSPACE} = \bigcup_{k>0} \text{SPACE}(n^k), \quad \text{L} = \text{SPACE}(\log_2 n), \quad \text{NL} = \text{NSPACE}(\log_2 n)$$
---

## 35. Mi az off-line Turing-gép, és miért szükséges a tárbonyolultsághoz?
?
Az off-line Turing-gép egy többszalagos TG, amelyen a bemenetszalag csak olvasható; a **tárigénybe csak a munkaszalagokon** felhasznált terület számít. Ez teszi értelmessé a szublineáris tárbonyolultságot (pl. logaritmikus tár), mivel a bemenet hosszát nem kell beleszámítani a tárba. A tár — az idővel szemben — újrafelhasználható.
---

## 36. Mit mond ki Savitch tétele?
?
**Savitch tétele:** Ha $f(n) \geq \log n$, akkor $\text{NSPACE}(f(n)) \subseteq \text{SPACE}(f^2(n))$. Azaz determinisztikus TG-ek a tárbonyolultság legfeljebb négyzetes romlásával szimulálni tudják a nemdeterminisztikus TG-eket (ha a tár legalább logaritmikus). Következmény: $\text{PSPACE} = \text{NPSPACE}$.
---

## 37. Mi a Savitch tétel bizonyításának kulcsötlete?
?
Az $\text{ELÉR}(c_1, c_2, i, t)$ predikátum (igaz, ha van $\leq t$ hosszú út $c_1$-ből $c_2$-be) rekurzív kiszámítása, **felezéssel**: egy köztes $c$ konfiguráción átmenve,
$$\text{ELÉR}(c_1,c_2,i,t) \iff \exists c:\ \text{ELÉR}(c_1,c,i,\lceil t/2\rceil) \wedge \text{ELÉR}(c,c_2,i,\lceil t/2\rceil).$$
A rekurzió mélysége $O(f(n))$, minden szinten $O(f(n))$ tár szükséges: összesen $O(f^2(n))$.
---

## 38. Mi a QSAT (teljesen kvantifikált Boole-formula kielégíthetősége)?
?
$\text{QSAT} = \{\langle\varphi\rangle \mid \varphi \text{ igaz teljesen kvantifikált Boole-formula}\}$, ahol $\varphi$ minden változója $\exists$ vagy $\forall$ kvantorral kötött, és a kvantormentes rész KNF. A QSAT PSPACE-teljes (polinom idejű visszavezetésekre nézve).
---

## 39. Miért van QSAT $\in$ PSPACE?
?
Az $\text{ÉRTÉK}(\varphi)$ rekurzív kiszámítása: $\varphi = Qx\psi$ esetén kiszámoljuk $\psi^{x=1}$ és $\psi^{x=0}$ értékét, majd $Q$ szerint kombináljuk ($\exists$: VAGY, $\forall$: ÉS). A rekurzió mélysége a változók száma ($\leq n$), minden szinten csak egy igazságértéket kell tárolni — összesen lineáris tár.
---

## 40. Mi a FÖLDRAJZI JÁTÉK és miért PSPACE-teljes?
?
Adott $G$ irányított gráf és $p$ csúcs; két játékos felváltva lép a gráfban (mindig a legutóbb megjelölt csúcsból, már megjelölt csúcsba nem léphetnek); az veszít, aki nem tud lépni. PSPACE-teljes: $\text{QSAT} \leq_p \text{FÖLDRAJZI JÁTÉK}$ visszavezetéssel. A $\varphi = \exists x_1\forall x_2\dots$ TKBF-hez $G_\varphi$-t úgy építjük, hogy az első játékosnak pontosan akkor van nyerő stratégiája, ha $\varphi$ igaz.
---

## 41. Mekkora a szóprobléma bonyolultsága a Chomsky-hierarchiában?
?
| Grammatikatípus | Bonyolultság |
|---|---|
| Reguláris (3. típus) | lineáris idő |
| Környezetfüggetlen (2. típus) | köbös idő (pl. CYK-algoritmus) |
| Környezetfüggő (1. típus) | **PSPACE-teljes** |
| Általános (0. típus) | **eldönthetetlen** |
Az általános grammatikák képesek szimulálni Turing-gépet, ezért eldönthetetlen.
---

## 42. Mi az L és NL osztály, és mik a logaritmikus tárral kiszámítható függvények?
?
$\text{L} = \text{SPACE}(\log_2 n)$, $\text{NL} = \text{NSPACE}(\log_2 n)$. Logaritmikus tárral kiszámítható függvény: olyan $f:\Sigma^*\to\Sigma^*$, amit egy (legalább háromszalagos) logaritmikus tárú off-line TG számol ki, ahol a tárfelhasználásba sem a bemenet, sem a kimenet mérete nem számít. Ezeket **lyukszalagos gépeknek** is nevezik.
---

## 43. Mi az ELÉRHETŐSÉG probléma, és miért NL-teljes?
?
$\text{ELÉRHETŐSÉG}$: adott $G=(V,E)$ irányított gráf és $s,t\in V$, van-e $s$-ből $t$-be vezető irányított út? NL-teljes: (1) $\in$ NL: NTG nemdeterminisztikusan kér lépésenként csúcsot $O(\log|V|)$ tárral; (2) NL-nehéz: tetszőleges $L\in\text{NL}$ konfigurációs gráfja logaritmikus tárral megkonstruálható, és $u \in L \iff$ van út $c_{kezdő}$-ből $c_{elfogadó}$-ba.
---

## 44. Miért igaz, hogy NL $\subseteq$ P?
?
Egy $O(\log n)$ tárú NTG konfigurációs gráfja legfeljebb polinomiálisan sok ($p(n) = n^2 \cdot n^{c \cdot \log n}$, ami polinom) csúcsot tartalmaz. Az ELÉRHETŐSÉG ebben a polinomiálisan méretű gráfban polinom időben eldönthető, tehát $\text{NL} \subseteq \text{P}$.
---

## 45. Mit mond ki az Immermann–Szelepcsényi tétel, és mi a bizonyítás kulcsötlete?
?
**Tétel:** $\text{NL} = \text{coNL}$. Bizonyítás: megmutatják, hogy $\overline{\text{ELÉRHETŐSÉG}} \in \text{NL}$. Az $s$-ből pontosan $i$ lépésben elérhető csúcsok $d_i$ számát induktívan számítják: $d_{i+1}$ kiszámításakor minden csúcsra nemdeterminisztikusan megsejtik, hogy elérhető-e $\leq i$ lépésben, és számolják, hogy a $d_i$ elérhető csúcs mind megtaláltatott-e. Mivel $\overline{\text{ELÉRHETŐSÉG}}$ NL-ben van és coNL-teljes, $\text{NL} = \text{coNL}$ következik.
---

## 46. Miért NL-teljes a 2SAT?
?
**$\in$ NL:** $\overline{\text{2SAT}} \in \text{NL}$ — $\varphi$ kielégíthetetlen $\iff$ az implikációs gráfban van $x_i$-t és $\neg x_i$-t érintő kör, ami ELÉRHETŐSÉGGEL ellenőrizhető. Az Immermann–Szelepcsényi tétel miatt $\text{2SAT} \in \text{NL}$. **NL-nehéz:** $\text{ELÉRHETŐSÉG} \leq_l \overline{\text{2SAT}}$: $G, s, t$ bemenethez $\varphi = (x\lor x)\land\bigwedge_{(u,v)\in E}(\bar u\lor v)$ formula, ahol $s, t$ helyett $x, \neg x$ szerepel; van út $s$-ből $t$-be $\iff$ $\varphi$ kielégíthetetlen.
---

## 47. Mi a bonyolultsági osztályok teljes hierarchiája (lánca)?
?
$$\text{L} \subseteq \text{NL} = \text{coNL} \subseteq \text{P} \subseteq \text{NP} \subseteq \text{PSPACE} = \text{NPSPACE} \subseteq \text{EXPTIME}$$
Indoklások: $\text{L} \subseteq \text{NL}$ és $\text{P} \subseteq \text{NP}$ definíció szerint; $\text{NL} = \text{coNL}$ (Immermann–Szelepcsényi); $\text{NL} \subseteq \text{P}$ (konfigurációs gráf polinom méretű); $\text{PSPACE} = \text{NPSPACE}$ (Savitch); $\text{NP} \subseteq \text{PSPACE}$ (polinom idő $\Rightarrow$ polinom tár); $\text{PSPACE} \subseteq \text{EXPTIME}$ (konfiguráció-tér exponenciális, de véges). Biztosan valódi: $\text{P} \subsetneq \text{EXPTIME}$ és $\text{NL} \subsetneq \text{PSPACE}$.
---

## 48. Mik az EXPTIME, NEXPTIME, EXPSPACE és az elemi osztályok?
?
$$\text{(N)EXPTIME} = \bigcup_{k\geq 1}\text{(N)TIME}(2^{n^k}), \quad \text{EXPSPACE} = \bigcup_{k\geq 1}\text{SPACE}(2^{n^k})$$
$$k\text{EXPTIME} = \text{TIME}\!\left(\underbrace{2^{2^{\cdot^{\cdot^{2^{n^k}}}}}}_{k}\right), \quad \text{ELEMENTARY} = \bigcup_{k\geq 1} k\text{EXPTIME}$$
Az ELEMENTARY-beli függvények az **elemi függvények**. Nem elemi függvény pl. az **Ackermann-függvény**. A teljes lánc $\text{L}$-től $\text{R}$-ig (az összes eldönthető problémáig) terjed.
---

## 49. Milyen NP-nehéz problémák válnak könnyűvé kis módosítással?
?
- **3SAT** NP-teljes, de **2SAT** P-beli (sőt NL-teljes).
- Két adott csúcs közti **Hamilton-út** keresése NP-teljes, de tetszőleges ($s,t$-re vonatkozó) **összefüggő út** keresése könnyű.
- **Korlátozott feszítőfa** (max. fok $\leq k$) NP-teljes, de tetszőleges feszítőfa (pl. Kruskal, Prim) hatékonyan megkonstruálható.
Tanulság: a probléma pontos megfogalmazása kritikus.
---

## 50. Hogyan kapcsolódik a logaritmikus tárral való visszavezetés ($\leq_l$) a polinom idejűhöz, és miért nem triviális az összetétele?
?
A logaritmikus tárral való visszavezetésnél ($\leq_l$) az $f$ függvényt logaritmikus tárú off-line TG számítja ki. A $\leq_l$ tranzitivitása (és L, NL zártsága rá) **nem** a közvetlen kompozícióval adódik (a két gép sorba kapcsolása tár szempontjából nem biztos, hogy logaritmikus). Helyette egy háromszalagos $M_1$ gép **bináris számlálóval** követi, hányadik betűjét olvassa az $f(u)$ szónak, és valahányszor szükséges, **újraszámolja** azt a betűt — így a köztes szót sosem kell egészben tárolni.
---

