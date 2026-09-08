#flashcards/bvszam/kornyezetfuggetlen-nyelvek
## 1. Mit jelent, hogy egy grammatika környezetfüggetlen (KF)?
?
Egy $G = \langle N, T, P, S \rangle$ grammatika **környezetfüggetlen**, ha minden $P$-beli szabály $A \to u$ alakú, ahol $A \in N$ és $u \in (N \cup T)^*$. (Chomsky-hierarchiában a 2-es típus.) A KF nyelveket veremautomaták ismerik fel.
---

## 2. Mi az aktív nemterminális definíciója, és hogyan határozható meg iteratívan?
?
Egy $X \in N$ nemterminális **aktív**, ha belőle levezethető valamely terminális szó. Iteratívan:
$$A_1 = \{X \mid X \to u \in P,\ u \in T^*\}, \quad A_{i+1} = A_i \cup \{X \mid X \to w \in P,\ w \in (T \cup A_i)^*\}$$
Inaktív nemterminálisok sosem generálnak terminális szót.
---

## 3. Mi az elérhető nemterminális definíciója, és hogyan határozható meg iteratívan?
?
Egy $Y \in N$ nemterminális **elérhető**, ha előfordul a $S$-ből levezethető valamely mondatformában. Iteratívan:
$$R_1 = \{S\}, \quad R_{i+1} = R_i \cup \{Y \in N \mid X \to uYw \in P,\ X \in R_i\}$$
---

## 4. Mit jelent a redukált grammatika, és hogyan állítható elő?
?
Egy KF grammatika **redukált**, ha minden nemterminálisa egyszerre aktív és elérhető. Előállítás:
1. Inaktív nemterminálisok és az őket tartalmazó szabályok törlése.
2. Elérhetetlen nemterminálisok (és szabályaik) törlése.
Minden KF grammatikához létezik ekvivalens redukált KF grammatika.
---

## 5. Mi a Chomsky normálforma (CNF) definíciója?
?
Egy $G = \langle N, T, P, S \rangle$ grammatika **Chomsky normálformájú (CNF)**, ha minden szabálya az alábbi három alakok egyike:
- $S \to \varepsilon$ (és ekkor $S$ más szabály jobboldalán nem szerepel), vagy
- $A \to BC$ (ahol $A, B, C \in N$; $B, C \neq S$ ha $S \to \varepsilon \in P$), vagy
- $A \to a$ (ahol $A \in N$, $a \in T$).
---

## 6. Milyen 4 lépésben alakítható CNF-re egy KF grammatika?
?
1. **Álterminálisok bevezetése:** minden $a \in T$-hez új $\bar{a}$ nemterminális; minden legalább 2 hosszú jobb oldalon $a \mapsto \bar{a}$, hozzávesszük $\bar{a} \to a$.
2. **Hosszredukció:** $X \to Y_1 Y_2 \cdots Y_k$ ($k \geq 3$) helyett $X \to Y_1 Z_1,\ Z_1 \to Y_2 Z_2,\ \ldots,\ Z_{k-2} \to Y_{k-1} Y_k$ új $Z_i$ nemterminálisokkal.
3. **ε-mentesítés:** meghatározzuk az $\varepsilon$-generáló nemterminálisokat ($U$ halmaz), töröljük az $\varepsilon$-szabályokat, de szimulálunk minden lehetséges hiányzó komponenst; ha $S \in U$, új $S'$ kezdőszimbólum.
4. **Láncmentesítés:** $X \to Y$ lánc-szabályok eliminálása az $H(A)$ tranzitív lezárással: $P_1 = \{A \to w \mid \exists B \in H(A) : B \to w \in P,\ w \notin N\}$.
---

## 7. Hogyan határozhatók meg az ε-generáló nemterminálisok (ε-mentesítés során)?
?
Az $\varepsilon$-generáló nemterminálisok $U$ halmazát iteratívan:
$$U_1 = \{X \mid X \to \varepsilon \in P\}, \quad U_{i+1} = U_i \cup \{X \mid X \to u \in P,\ u \in U_i^*\}$$
Ha $S \in U$ és $S$ más szabály jobboldalán is szerepel, új $S'$ kezdőszimbólumra van szükség: $S' \to S \mid \varepsilon$.
---

## 8. Mi a levezetési fa, és mi a határa?
?
Egy $G = \langle N, T, P, S \rangle$ feletti **levezetési fa** gyökeres irányított fa, ahol:
- a gyökér $S$ névkéjű,
- minden belső csúcs ($X$ névkéjű) gyerekeinek balról jobbra sorrende egy $X \to X_1 \cdots X_m \in P$ szabálynak felel meg,
- minden levél $T \cup \{\varepsilon\}$-beli; az $\varepsilon$-csúcsnak nincs testvére.
**Határ:** a levélcímkék balról jobbra összefűzve adják a generált szót.
---

## 9. Mi a baloldali levezetés, és mi a kapcsolata a levezetési fával?
?
Egy levezetés **baloldali**, ha minden lépésben az aktuális mondatforma **legbaloldalibb** nemterminálisát írjuk át. Minden levezetési fához pontosan **egy** baloldali levezetés tartozik.
---

## 10. Mit jelent az egyértelmű grammatika és az egyértelmű nyelv?
?
Egy $G$ KF grammatika **egyértelmű**, ha minden $L(G)$-beli szónak pontosan egy baloldali levezetése (és egyetlen levezetési fája) van. Egy $L$ nyelv **egyértelmű**, ha létezik egyértelmű grammatika, amely $L$-et generálja. Nem minden KF nyelv egyértelmű — ezek az **inherensen többértelmű** nyelvek.
Példa inherensen többértelmű KF nyelvre: $L = \{a^n b^n c^m d^m \mid n,m \ge 1\} \cup \{a^n b^m c^m d^n \mid n,m \ge 1\}$.
---

## 11. Milyen alakú a levezetési fa CNF grammatikánál, és hány belső csúcsa van?
?
CNF grammatikánál a levezetési fa **bináris fa**: minden belső csúcsnak pontosan 2 gyereke van (kivéve az $A \to a$ levelek szülőit, melyeknek 1 gyerekük van a terminális). Egy $n$ betűből álló szó levezetési fájában pontosan $2n - 1$ belső csúcs van.
---

## 12. Mondja ki a Bar-Hillel lemmát (pumpálási lemmát KF nyelvekre)!
?
Minden $L$ KF nyelvhez léteznek $p, q \in \mathbb{N}$, hogy minden $|w| > p$ szóhoz ($w \in L$) létezik $w = uxvyz$ felbontás, ahol:
- $|xvy| \leq q$
- $xy \neq \varepsilon$
- $ux^i vy^i z \in L$ minden $i \geq 0$-ra.
$p$ és $q$ csak a **nyelvtől** függ, nem a szótól.
---

## 13. Hogyan bizonyítják a Bar-Hillel lemmát (vázlat), és mik a $p, q$ konstansok CNF esetén?
?
Legyen $G$ CNF grammatika $n$ nemterminálissal. Vegyük $p = 2^{n-1}$, $q = 2^n$.
Ha $|w| > p$, a levezetési fa leghosszabb útján $> n$ csúcs van. **Skatulya-elv:** valamelyik $A$ nemterminális legalább kétszer ismétlődik az úton. Az utolsó ismétlő pár alapján:
$$S \Rightarrow^* uAz, \quad A \Rightarrow^* xAy, \quad A \Rightarrow^* v$$
ahol $xy \neq \varepsilon$ (CNF biztosítja). Ezért $ux^i vy^i z \in L$ minden $i \geq 0$-ra.
---

## 14. Hogyan bizonyítható a Bar-Hillel lemmával, hogy $\{a^n b^n c^n \mid n \geq 1\} \notin \mathcal{L}_2$?
?
Legyenek $p, q$ a Bar-Hillel lemma konstansai. Legyen $w = a^k b^k c^k$ ahol $k > \max\{p, q\}$.
Mivel $|xvy| \leq q < k$, az $xy$ legfeljebb 2 betűfajtát tartalmaz. A $ux^0 vy^0 z$ szóban valamelyik betűfajtából kevesebb lesz $k$-nál, míg a többi $k$ marad — ez nem lehet $\{a^n b^n c^n\}$-beli. Ellentmondás, tehát a nyelv nem KF.
---

## 15. Milyen zártsági hiányai vannak a KF ($\mathcal{L}_2$) nyelvek osztályának?
?
$\mathcal{L}_2$ **nem zárt** a következő műveletekre: metszet, komplementer, különbség, szimmetrikus differencia.
Ellenpélda: $\{a^n b^n c^n\} = \{a^k b^n c^n \mid k,n \geq 1\} \cap \{a^n b^n c^k \mid n,k \geq 1\}$, ahol mindkét tényező KF, de a metszet nem KF.
---

## 16. Mi a CYK algoritmus feladata és bemenete?
?
A **Cocke–Younger–Kasami (CYK) algoritmus** KF grammatika szóproblémáját oldja meg. Bemenet: $G = \langle T, N, P, S \rangle$ **Chomsky normálformájú** grammatika és $u = t_1 \cdots t_n \in T^*$. Kimenet: $u \in L(G)$?
---

## 17. Hogyan működik a CYK algoritmus? Adja meg a táblázat feltöltési szabályát!
?
Dinamikus programozással feltölt egy $n \times n$-es $H$ táblázatot alulról felfelé:
$$H_{i,i} := \{A_k \mid A_k \to t_i \in P\}$$
$$H_{i,j} := \bigcup_{h=i}^{j-1} \{A_k \mid A_k \to \beta_k \in P,\ \beta_k \in H_{i,h} \cdot H_{h+1,j}\} \quad (i < j)$$
$A_k \in H_{i,j}$ azt jelenti: $A_k \Rightarrow^* t_i \cdots t_j$.
**Eredmény:** $u \in L(G) \iff S \in H_{1,n}$.
---

## 18. Mi a CYK algoritmus helyességének alapállítása?
?
**Állítás:** $H_{i,j} = \{X \in N \mid X \Rightarrow^*_G t_i \cdots t_j\}$.
Bizonyítás $j - i$-re vonatkozó teljes indukcióval. Az indukciós lépésben: $X \Rightarrow YZ$ első lépéssel, majd $Y \Rightarrow^* t_i \cdots t_h$ és $Z \Rightarrow^* t_{h+1} \cdots t_j$ valamilyen $h$-ra.
---

## 19. Mi a CYK algoritmus időbonyolultsága, és miért?
?
A CYK algoritmus időbonyolultsága $O(n^3)$, ahol $n$ a szó hossza. Összesen $O(n^2)$ cella van, mindegyik kiszámítása $O(n)$ lépést igényel (az összes lehetséges $h$ hasítási pont végignézése) → összesen $O(n^3)$.
Ha általános KF grammatikából kell előbb CNF-re hozni ($O(|G|^2)$), az összhatékonyság $O(|G|^2 n^3)$.
---

## 20. Melyek a KF grammatikák eldönthető algoritmikus problémái?
?
- **Szóprobléma** ($u \in L(G)$?): eldönthető, CYK algoritmus $O(n^3)$ lépésben.
- **Üresség** ($L(G) = \emptyset$?): eldönthető — $L(G) = \emptyset \iff$ nincs $\leq p$ hosszú szó (Bar-Hillel $p$ konstansával).
- **Végesség** ($L(G)$ végtelen?): eldönthető — $L(G)$ végtelen $\iff$ van $p < |w| \leq p+q$ hosszú szó.
---

## 21. Melyek a KF grammatikákra vonatkozó eldönthetetlen problémák?
?
A Post-megfelelkezési problémára (PMP) való visszavezetéssel megmutatható, hogy **eldönthetetlen**:
1. Egyértelmű-e adott $G$ KF grammatika?
2. $L(G_1) \cap L(G_2) = \emptyset$? (két KF grammatika metszetének üressége)
3. $L(G_1) = L(G_2)$? (két KF grammatika egyenlősége)
4. $L(G_1) = \Gamma^*$ valamely $\Gamma$ ábécére?
5. $L(G_1) \subseteq L(G_2)$? (KF-nyelv tartalmazás)
---

## 22. Hogyan bizonyítható a KF grammatika egyértelműségének eldönthetetlensége?
?
Adott $D$ PMP-példányból ($u_i, v_i \in \Sigma^+$) épül egy $G$ grammatika, amely két párhuzamos szabályrendszert tartalmaz: $G_A$-t az $u_i$-kre és $G_B$-t a $v_i$-kre egy $\Delta = \{a_1, \ldots, a_n\}$ indexábécé felett. Egy $w$ szónak pontosan akkor van kétféle levezetése $G$-ben, ha az index-rész ugyanazt a dominósorozatot kódolja felül ($u_i$-kkel) és alul ($v_i$-kkel). Tehát $G$ pontosan akkor nem egyértelmű, ha $D$-nek van megoldása — ez eldönthetetlen lenne.
---

## 23. Mi a különbség a Bar-Hillel (nagy) pumpálási lemma és a reguláris nyelvek pumpálási lemmája között?
?
- **Reguláris (kis) pumpálási lemma:** minden elég hosszú szó $uvw$ alakra bontható, ahol $v \neq \varepsilon$ és $uv^iw \in L$ minden $i \geq 0$-ra — **egy** komponens pumpálódik.
- **Bar-Hillel (nagy) pumpálási lemma:** KF nyelvekre $w = uxvyz$ felbontás, ahol $xy \neq \varepsilon$ és $ux^ivy^iz \in L$ minden $i \geq 0$-ra — **két** komponens pumpálódik szimmetrikusan.
A Bar-Hillel lemma erősebb: KF nem-tagságot bizonyít olyan nyelvekre, amelyek a kis pumpálási lemmával esetleg KF-nek tűnnének.
---

## 24. Mi a CNF-re hozás szerepe a Bar-Hillel lemma bizonyításában?
?
A CNF biztosítja, hogy:
1. A levezetési fa **bináris** → az $n$ belső csúcsú fa mélysége legalább $\lceil \log_2 n \rceil$.
2. Az $xy \neq \varepsilon$ feltétel garantált: CNF-ben minden $A \to BC$ szabálynál $B$ és $C$ nemterminálisok, ezért az $A \Rightarrow^* xAy$ levezetésben legalább az egyik ($x$ vagy $y$) nem üres.
3. A $p = 2^{n-1}$, $q = 2^n$ konstansok pontosan a bináris fa mélységéből adódnak (skatulya-elv $n$ nemterminálisra).
---

