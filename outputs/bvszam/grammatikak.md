#flashcards/bvszam/grammatikak
## 1. Mi a generatív grammatika definíciója? Mik az összetevői?
?
Egy $G = (V, \Sigma, R, S)$ rendszer **(generatív) grammatika**, ahol: $V$ a nemterminálisok ábécéje, $\Sigma$ a terminálisok ábécéje ($V \cap \Sigma = \emptyset$), $S \in V$ a kezdőszimbólum, $R$ az $u \to v$ alakú átírási szabályok véges halmaza, ahol $u, v \in (V \cup \Sigma)^*$ és $u$-ban van legalább egy nemterminális.
---

## 2. Mit jelent, hogy $v$ egy lépésben levezethető $u$-ból?
?
$v$ **egy lépésben levezethető** $u$-ból (jele $u \Rightarrow_G v$), ha $u = \alpha\gamma\beta$ és $v = \alpha\gamma'\beta$ valamely $\alpha, \beta, \gamma, \gamma' \in (V \cup \Sigma)^*$-ra úgy, hogy $\gamma \to \gamma' \in R$.
---

## 3. Mit jelent a levezetési reláció ($\Rightarrow^*$)?
?
A **levezetési reláció** $\Rightarrow_G^*$ a közvetlen levezetési reláció $\Rightarrow_G$ reflexív, tranzitív lezártja: $u \Rightarrow^* v$ pontosan akkor, ha léteznek $n \ge 0$ és $w_0, \ldots, w_n$ szavak, hogy $u = w_0$, minden $i$-re $w_i \Rightarrow w_{i+1}$, és $w_n = v$.
---

## 4. Mi a grammatika által generált nyelv?
?
A $G$ által **generált nyelv** azon $\Sigma^*$-beli szavak halmaza, amelyek a kezdőszimbólumból levezethetők:
$$L(G) = \{u \in \Sigma^* \mid S \Rightarrow_G^* u\}$$
---

## 5. Mikor ekvivalens két grammatika? Mi az ekvivalencia gyengébb formája?
?
$G_1$ és $G_2$ **ekvivalens**, ha $L(G_1) = L(G_2)$. **Gyengén ekvivalens**, ha $L(G_1)$ és $L(G_2)$ legfeljebb az üres szóban ($\varepsilon$) különböznek egymástól.
---

## 6. Mi a Chomsky-hierarchia, és hogyan viszonyulnak egymáshoz a nyelvcsaládok?
?
A Chomsky-hierarchia a generatív grammatikák négy osztálya a szabályaik alakja szerint. A megfelelő nyelvcsaládokra:
$$\mathcal{L}_3 \subsetneq \mathcal{L}_2 \subsetneq \mathcal{L}_1 \subsetneq \mathcal{L}_0$$
A tartalmazások valódiak; pl. $\{a^n b^n c^n \mid n \in \mathbb{N}\} \in \mathcal{L}_1 \setminus \mathcal{L}_2$.
---

## 7. Mik a 0-típusú (általános) grammatika szabályainak alakjai, és milyen automata ismeri fel?
?
A **0-típusú** (mondatszerkezetű) grammatikában nincs semmilyen megkötés a szabályok alakjára: $u \to v$, ahol $u, v \in (V \cup \Sigma)^*$ és $u$-ban van legalább egy nemterminális. A megfelelő felismerő: **Turing-gép**.
---

## 8. Mik az 1-típusú (környezetfüggő) grammatika szabályainak alakjai, és milyen automata ismeri fel?
?
Az **1-típusú** (környezetfüggő) grammatika szabályai $\alpha A \beta \to \alpha\gamma\beta$ alakúak, ahol $A \in V$, $\alpha, \beta, \gamma \in (V \cup \Sigma)^*$, $\gamma \neq \varepsilon$. Kivételként megengedett a **KES** (korlátozott $\varepsilon$-szabály): $S \to \varepsilon$, de csak ha $S$ nem szerepel egyetlen szabály jobb oldalán sem. Felismerő: **lineárisan korlátolt automata**.
---

## 9. Mik a 2-típusú (környezetfüggetlen) grammatika szabályainak alakjai, és milyen automata ismeri fel?
?
A **2-típusú** (környezetfüggetlen, KF) grammatika szabályai $A \to v$ alakúak, ahol $A \in V$ és $v \in (V \cup \Sigma)^*$. Felismerő: **(nemdeterminisztikus) veremautomata**.
---

## 10. Mik a 3-típusú (reguláris) grammatika szabályainak alakjai, és milyen automata ismeri fel?
?
A **3-típusú** (reguláris) grammatika szabályai $A \to vB$ vagy $A \to v$ alakúak, ahol $A, B \in V$ és $v \in \Sigma^*$. Felismerő: **véges automata**.
---

## 11. Mi a lineáris grammatika definíciója? Mik a speciális esetei?
?
Egy $G = \langle N, T, S, R \rangle$ KF grammatika **lineáris**, ha minden szabálya vagy $A \to u$ ($u \in T^*$) alakú, vagy $A \to u_1 B u_2$ ($A, B \in N$, $u_1, u_2 \in T^*$) alakú — azaz a jobb oldalon legfeljebb egy nemterminális szerepel. Speciális esetek: **bal-lineáris** ($u_1 = \varepsilon$, a nemterminális bal szélen), **jobb-lineáris** ($u_2 = \varepsilon$, a nemterminális jobb szélen).
---

## 12. Milyen összefüggés van a jobb-lineáris grammatikák és a reguláris grammatikák között?
?
A jobb-lineáris grammatikák pontosan egyenértékűek a 3-as típusú (reguláris) grammatikákkal; minden jobb-lineáris grammatika reguláris nyelvet generál, és minden reguláris grammatika jobb-lineáris.
---

## 13. Mondja ki a bal-lineáris és jobb-lineáris grammatikák ekvivalenciájáról szóló tételt!
?
**Tétel:** Minden bal-lineáris grammatikához van ekvivalens jobb-lineáris grammatika (és viszont), tehát minden bal-lineáris grammatika reguláris nyelvet generál. A konstrukció: ha $G$ bal-lineáris, az $R'$ szabályhalmaz: $S \to u \in R'$ ha $S \to u \in R$; $S \to u A_k \in R'$ ha $A_k \to u \in R$; $A_j \to u A_k \in R'$ ha $A_k \to A_j u \in R$; $A_j \to u \in R'$ ha $S \to A_j u \in R$.
---

## 14. Hogyan zárt $\mathcal{L}_3$ a tükrözés műveletére? Hogyan kapcsolódik ez a bal-lineáris grammatikákhoz?
?
$\mathcal{L}_3$ **zárt a tükrözésre** ($L \mapsto L^{-1}$): minden jobb-lineáris grammatikából bal-lineáris grammatika kapható az $A \to u$ és $A \to uB$ szabályok helyett $A \to u^{-1}$ és $A \to B u^{-1}$ szabályokkal. Ebből következik, hogy minden reguláris nyelv bal-lineáris grammatikával is generálható.
---

## 15. Mi a reguláris grammatika normálformája (3-as típusú normálalak)?
?
**Tétel:** Minden 3-as típusú grammatika ekvivalens egy olyan grammatikával, amelynek szabályai kizárólag $X \to aY$ ($X, Y \in N$, $a \in T$) vagy $X \to \varepsilon$ ($X \in N$) alakúak.
---

## 16. Hogyan hajtjuk végre a hosszredukciót a reguláris normálalak előállításakor?
?
**Hosszredukció:** Ha $A \to uB$ és $|u| > 1$: bevezet új $Z_i$ nemterminálisokat, $A \to a_1 Z_1,\ Z_1 \to a_2 Z_2,\ \ldots,\ Z_{n-1} \to a_n B$. Ha $A \to u$ és $|u| \ge 1$: hasonlóan, az utolsó tag $\ldots \to a_m E,\ E \to \varepsilon$ lesz.
---

## 17. Hogyan számítjuk ki a $H(A)$ halmazokat a láncmentesítéshez? Mit jelöl $H(A)$?
?
A $H(A)$ halmaz ($A \in N$) iteratívan:
$$H_0(A) := \{A\}$$
$$H_{i+1}(A) := H_i(A) \cup \{B \in N \mid \exists C \in H_i(A) : C \to B \in R\}$$
A sorozat $N$ végessége miatt véges lépésben stabilizálódik. $H(A) = \{B \in N \mid A \Rightarrow^* B\}$, vagyis az $A$-ból láncszabályokkal elérhető összes nemterminális halmaza.
---

## 18. Hogyan állítjuk elő a láncmentes szabályrendszert a $H(A)$ halmazok alapján?
?
Jelölje $R_0$ az összes lánc- ($X \to Y$) szabályt. Az ekvivalens, láncmentes $R'$:
$$R' := \{A \to w \mid \exists B \in H(A) : B \to w \in R \setminus R_0\}$$
Azaz $A$ örökli azon $B$ lánckövető összes nem-lánc szabályát, amelyre $A \Rightarrow^* B$ láncút vezet.
---

## 19. Milyen zártsági tulajdonságai vannak $\mathcal{L}_i$-nek a reguláris műveletekre?
?
**Tétel:** $\mathcal{L}_i$ zárt a reguláris műveletekre (unió, konkatenáció, Kleene-lezárt) minden $i = 0, 1, 2, 3$ esetén. Az unió konstrukciója ($i = 0, 2, 3$): új $S_0$ kezdőszimbólummal, $S_0 \to S_1 \mid S_2$ szabállyal. Az $i = 1$ esetben a KES miatt $\varepsilon$-szabályokat előbb el kell távolítani.
---

## 20. Milyen további zártsági tulajdonságai vannak $\mathcal{L}_3$-nak (a reguláris műveleteken túl)?
?
$\mathcal{L}_3$ zárt a **komplementerre**, **metszetre**, **különbségre** és **tükrözésre** is. Komplementer: ha $A$ VDA felismeri $L$-t, az $A' = \langle Q, T, \delta, q_0, Q \setminus F \rangle$ felismeri $\bar{L}$-t. Metszet: $L_1 \cap L_2 = \overline{\bar{L}_1 \cup \bar{L}_2}$ (De Morgan). Különbség: $L_1 \setminus L_2 = L_1 \cap \bar{L}_2$.
---

## 21. Mire nem zárt $\mathcal{L}_2$, és mi a bizonyítás módszere?
?
$\mathcal{L}_2$ **nem zárt** metszetre, komplementerre, különbségre és szimmetrikus differenciára. Ellenpélda: $\{a^n b^n c^n\} = \{a^k b^n c^n\} \cap \{a^n b^n c^k\}$, ahol mindkét tényező KF, de a metszet nem az (Bar-Hillel lemmával igazolható).
---

## 22. Mi a 0-típusú grammatika normálformája?
?
Bármely 0-típusú grammatikához létezik ekvivalens grammatika, amelynek szabályai az alábbi alakok egyike ($A, B, C \in V$, $a \in \Sigma$):
$$S \to \varepsilon,\quad A \to a,\quad A \to B,\quad A \to BC,\quad AB \to B,\quad AB \to AC,\quad BA \to CA$$
---

## 23. Mi a KES (korlátozott $\varepsilon$-szabály) az 1-es típusú grammatikában?
?
A **KES** az 1-es típusú grammatika egyetlen kivételes $\varepsilon$-termelési szabálya: megengedett az $S \to \varepsilon$ szabály, **de** ha $R$ tartalmazza ezt a szabályt, akkor $S$ nem szerepelhet egyetlen szabály jobb oldalán sem. Ez biztosítja, hogy a grammatika lényegében hossz-nemcsökkentő maradjon.
---

## 24. Mi a Backus–Naur-forma (BNF), és mire használják?
?
A **Backus–Naur-forma (BNF)** a grammatikai szabályok megadásának elterjedt metanyelve; John Backus vezette be 1959-ben az ALGOL programozási nyelv szintaxisának leírására. Az $\alpha \to \beta_1 \mid \ldots \mid \beta_n$ jelölés kompakt formában adja meg az azonos bal oldalú szabályokat.
---

## 25. Mi az álterminálisok bevezetésének normálforma-trükkje?
?
Minden grammatikához létezik ekvivalens, azonos típusú $G'$, amelynek szabályaiban a bal oldalon csak nemterminálisok szerepelnek. Módszer: minden $a \in \Sigma$ terminálishoz bevezetünk egy $\bar{a} \in V$ **álterminális** nemterminálisát, és hozzáadjuk az $\bar{a} \to a$ szabályokat; ezután a szabályok belsejében $a$ helyett $\bar{a}$-t írunk.
---

## 26. Mik a mondatformák egy grammatikában?
?
Az $S$-ből (kezdőszimbólumból) levezethető szavakat — azokat a $(V \cup \Sigma)^*$-beli szavakat, amelyekre $S \Rightarrow^* w$ — **mondatformáknak** nevezzük. A generált nyelv $L(G)$ a mondatformák azon részhalmaza, amelyek kizárólag terminálisokból állnak.
---

