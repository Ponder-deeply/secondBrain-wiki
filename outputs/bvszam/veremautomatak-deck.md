#flashcards/bvszam/veremautomatak
## 1. Mi a veremautomata (VA) formális definíciója? Sorold fel komponenseit!
?
$$A = \langle Z, Q, T, \delta, z_0, q_0, F \rangle$$
ahol $Z$ a veremábécé (véges), $Q$ az állapothalmaz (véges), $T$ az inputábécé, $\delta : Z \times Q \times (T \cup \{\varepsilon\}) \to \mathcal{P}_{\text{véges}}(Z^* \times Q)$ az átmenetfüggvény, $z_0 \in Z$ a kezdő veremszimbólum, $q_0 \in Q$ a kezdőállapot, $F \subseteq Q$ az elfogadó állapotok halmaza.
---

## 2. Mi egy veremautomata konfigurációja és kezdőkonfigurációja?
?
Konfiguráció: $zqw$, ahol $z \in Z^*$ a verem tartalma (az utolsó betű van a tetőn), $q \in Q$ az aktuális állapot, $w \in T^*$ a maradék input.
**Kezdőkonfiguráció:** $z_0 q_0 w$.
---

## 3. Milyen alapvető veremműveleteket valósíthat meg az átmenetfüggvény?
?
| Átmenet | Hatás |
|---|---|
| $(\varepsilon, r) \in \delta(z, q, t)$ | POP (tetőelem kivétele) |
| $(z, r) \in \delta(z, q, t)$ | Verem változatlan |
| $(z', r) \in \delta(z, q, t)$ | Csere ($z' \in Z$) |
| $(zz', r) \in \delta(z, q, t)$ | PUSH ($z'$ a tetőre) |
| $(w, r) \in \delta(z, q, t)$ | $z$ helyére $w \in Z^*$ kerül ($w$ utolsó betűje lesz a tetőn) |
---

## 4. Mikor determinisztikus egy veremautomata?
?
$A$ **determinisztikus**, ha minden $(z, q, a) \in Z \times Q \times T$ esetén:
$$|\delta(z, q, a)| + |\delta(z, q, \varepsilon)| = 1$$
Azaz minden konfigurációban legfeljebb egy lépés lehetséges (akár inputolvasással, akár $\varepsilon$-átmenettel — de nem mindkettő egyszerre).
---

## 5. Hogyan definiálható az egylépéses redukció veremautomatában?
?
$$\alpha \Rightarrow_A \beta$$
ha $\alpha = rzqaw$, $\beta = rupw$ és $(u, p) \in \delta(z, q, a)$.
Az átírási szabályok ($M_\delta$) alakja:
$$zqa \to up \in M_\delta \iff (u, p) \in \delta(z, q, a)$$
$$zq \to up \in M_\delta \iff (u, p) \in \delta(z, q, \varepsilon)$$
---

## 6. Mi a végállapottal elfogadott nyelv definíciója veremautomatánál?
?
$$L(A) = \{w \in T^* \mid z_0 q_0 w \Rightarrow_A^* up,\; u \in Z^*,\; p \in F\}$$
Az automata elfogadja $w$-t, ha valamely végállapotba ér (a veremben maradhat tartalom).
---

## 7. Mi az üres veremmel elfogadott nyelv definíciója?
?
$$N(A) = \{w \in T^* \mid z_0 q_0 w \Rightarrow_A^* p,\; p \in Q\}$$
Az automata elfogadja $w$-t, ha a verem **teljesen kiürül** (nincs veremszimbólum). Az elfogadó állapothalmaz $F$ ilyenkor irreleváns.
---

## 8. Hogyan alakítható át egy végállapottal elfogadó VA üres veremmel elfogadóvá ($L(A) \to N(A')$)?
?
Új $z'_0$, $q'_0$, $q'_h$ szimbólumok bevezetésével:
- Új kezdőkonfiguráció: $\delta'(z'_0, q'_0, \varepsilon) = \{(z'_0 z_0, q_0)\}$ — a régi verem tartalmát egy új aljszimbólum alá tesszük.
- Valahányszor az eredeti $A$ elfogadó állapotba kerül: $A'$ a $q'_h$ állapotba lép és kipucolja a vermet.
Így $N(A') = L(A)$.
---

## 9. Hogyan alakítható át egy üres veremmel elfogadó VA végállapottal elfogadóvá ($N(A) \to L(A')$)?
?
Új $z'_0$ aljszimbólum és $q'_f$ elfogadó állapot bevezetésével:
- Ha a verem alján $z'_0$ kerül (azaz az eredeti verem kiürült): $A'$ a $q'_f$ elfogadó állapotba lép.
Így $L(A') = N(A)$.
---

## 10. Mondd ki a veremautomata és a KF grammatika ekvivalenciájának tételét!
?
**Tétel:** Bármely $L$ nyelvre az alábbi három állítás ekvivalens:
1. $L$ **környezetfüggetlen** (2-es típusú grammatikával generálható).
2. $L$ **nemdeterminisztikus veremautomatával végállapottal** felismerhető.
3. $L$ **nemdeterminisztikus veremautomatával üres veremmel** felismerhető.
---

## 11. Hogyan konstruálunk KF grammatikából veremautomatát (vázlatosan)?
?
Legyen $G = \langle N, T, P, S \rangle$ CNF grammatika. A VA $M_\delta$ szabályrendszere lényegében $G$ invertált szabályait tartalmazza:
- $z_0 q_0 \to z_0 q_S$ (ha $S \to \varepsilon \in P$)
- $z_0 q_0 a \to z_0 q_X$ (ha $X \to a \in P$)
- $Z q_Y a \to Z Y q_X$ ($\forall Z$, ha $X \to a \in P$)
- $Z q_Y \to q_X$ (ha $X \to ZY \in P$)
- $z_0 q_S \to q_h$ (befejezés)
A $w$ szó jobboldali levezetése $G$-ben megfelel $A$ redukcióinak.
---

## 12. Hogyan konstruálunk veremautomatából KF grammatikát?
?
Legyen $A$ nemdeterminisztikus VA. A grammatika $G$ nemterminálisai $[q, x, p]$ alakú hármasok ($q, p \in Q$, $x \in Z$):
- $S \to [q_0, z_0, p]$ minden $p \in Q$-ra.
- Ha $xqa \to y_1 \cdots y_m p_m \in M_\delta$: $[q, x, p_0] \to a\, [p_m, y_m, p_{m-1}] \cdots [p_1, y_1, p_0]$ minden $p_0, \ldots, p_{m-1} \in Q$-ra.
- Ha $m = 0$: $[q, x, p_0] \to a$.
Eredmény: $L(G) = N(A)$.
---

## 13. Mi a különbség a determinisztikus és nemdeterminisztikus VA ereje között?
?
- A **nemdeterminisztikus** VA pontosan a KF (2-es típusú) nyelveket ismeri fel.
- A **determinisztikus** VA ereje kisebb: vannak KF nyelvek, amelyek nem ismerhetők fel determinisztikusan (pl. $\{ww^{-1} \mid w \in \{a,b\}^+\}$).
- Osztályok: $\mathcal{L}_3 \subsetneq \text{DVA-k} \subsetneq \mathcal{L}_2$.
---

## 14. Miért nem ismerhető fel $L_2 = \{ww^{-1} \mid w \in \{a,b\}^+\}$ determinisztikus VA-val, míg $L_1 = \{wcw^{-1} \mid w \in \{a,b\}^+\}$ igen?
?
$L_1$-ben a `c` elválasztószimbólum egyértelműen jelzi a „fordulópontot", ezért az automata determinisztikusan tudja, mikor váltson a verembe írásból az összehasonlításba.
$L_2$-ben nincs ilyen jel: a VA $\varepsilon$-átmenettel „találgatja" a fordulópontot ($q_1$-ből $q_2$-be lép anélkül, hogy szimbólumot olvasna), ez elkerülhetetlenül nemdeterminisztikus.
---

## 15. Hogyan definiálható a környezetfüggő (1-es típusú) grammatika?
?
A $G = \langle N, T, P, S \rangle$ grammatika **1-es típusú (KF-ő)**, ha minden szabálya $u_1 A u_2 \to u_1 v u_2$ alakú, ahol $A \in N$, $v \neq \varepsilon$, $u_1, u_2 \in (N \cup T)^*$ (kivéve esetleg az $S \to \varepsilon$ szabályt, ha $S$ nem szerepel más szabály jobboldalán).
---

## 16. Mi a hossz-nemcsökkentő grammatika, és mi a kapcsolata az 1-es típusúval?
?
**Definíció:** $G$ **hossz-nemcsökkentő**, ha minden $u \to v$ szabályára $|u| \leq |v|$ (kivéve $S \to \varepsilon$, ha $S$ nem szerepel más szabály jobboldalán).
**Tétel:** Minden hossz-nemcsökkentő grammatika KF-ő nyelvet generál, és megfordítva — minden KF-ő grammatika átalakítható hossz-nemcsökkentővé. A két fogalom tehát ekvivalens.
---

## 17. Miért döntható el a szóprobléma hossz-nemcsökkentő grammatikánál?
?
Mivel a grammatika hossz-nemcsökkentő, az $u$ szó levezetésében nem fordul elő $|u|$-nál hosszabb mondatforma. Ezért a levezetési fán csupán véges sok, legfeljebb $r = \sum_{i=1}^{|u|} |N \cup T|^i$ hosszú mondatforma szerepelhet, amelyek algoritmikusan felsorolhatók. Így eldönthető, hogy $u \in L(G)$.
---

## 18. Mi bizonyítja, hogy $\mathcal{L}_2 \subsetneq \mathcal{L}_1$?
?
- $\{a^n b^n c^n \mid n \in \mathbb{N}\} \notin \mathcal{L}_2$ — a Bar-Hillel (pumping) lemma alapján ez a nyelv nem KF.
- $\{a^n b^n c^n\} \in \mathcal{L}_1$ — generálja például a $P = \{S \to abc,\; S \to aAbc,\; Ab \to bA,\; Ac \to Bbcc,\; bB \to Bb,\; aB \to aaA,\; aB \to aa\}$ KF-ő grammatika.
Tehát a KF-ő nyelvek osztálya strikt módon tartalmazza a KF nyelvek osztályát.
---

## 19. Mi a Kuroda normálforma definíciója?
?
$G$ **Kuroda normálformájú**, ha minden szabálya az alábbi alakok egyike:
- $S \to \varepsilon$ (ha $S$ nem szerepel más szabály jobboldalán), vagy
- $A \to a$ ($A \in N$, $a \in T$), vagy
- $A \to BC$ ($A, B, C \in N$), vagy
- $AB \to AC$ ($A, B, C \in N$), vagy
- $BA \to CA$ ($A, B, C \in N$).
---

## 20. Milyen tételt mondhatunk ki a Kuroda normálformáról?
?
**Tétel:** Minden KF-ő (1-es típusú) grammatikához létezik vele ekvivalens Kuroda normálformájú grammatika.
---

## 21. Mik a Kuroda normálformára való átalakítás lépései?
?
1. **Álterminálisok bevezetése:** Terminálisok csak $A \to a$ alakban szerepeljenek.
2. **KF szabályok hosszredukciója:** Chomsky normálforma szerint ($A \to BC$ alakra hozás).
3. **KF-ő láncmentesítés:** $H(A) = \{B \mid A \Rightarrow^* B\}$ segítségével.
4. **KF-ő szabályok hosszredukciója:** Minden $X_1 \cdots X_m \to Y_1 \cdots Y_n$ ($n \geq m \geq 2$) szabályt új $Z_1, \ldots, Z_{n-2}$ nemterminálisokkal páronként redukálunk (pl. $X_1 X_2 \to Y_1 Z_1$, $Z_1 X_3 \to Y_2 Z_2$, stb.).
5. **$AB \to CD$ ($A \neq C$, $B \neq D$) eliminálása:** Új $W$ nemterminálissal: $AB \to AW$, $AW \to CW$, $CW \to CD$. Ezután minden kontextuális szabály $AB \to AC$ vagy $BA \to CA$ alakú.
---

## 22. Hogyan szimulálható egy hossz-nemcsökkentő $X_1 X_2 \cdots X_n \to Y_1 Y_2 \cdots Y_m$ ($m \geq n$) szabály 1-es típusú (kontextuális) szabálysorozattal?
?
Új $Z_1, \ldots, Z_n$ nemterminálisok bevezetésével:
$$X_1 X_2 \cdots X_n \to Z_1 X_2 \cdots X_n$$
$$Z_1 X_2 \cdots X_n \to Z_1 Z_2 X_3 \cdots X_n$$
$$\vdots$$
$$Z_1 \cdots Z_{n-1} X_n \to Z_1 \cdots Z_n Y_{n+1} \cdots Y_m$$
$$Z_1 \cdots Z_n Y_{n+1} \cdots Y_m \to Y_1 Z_2 \cdots Z_n Y_{n+1} \cdots Y_m$$
$$\vdots$$
$$Y_1 \cdots Y_{n-1} Z_n Y_{n+1} \cdots Y_m \to Y_1 Y_2 \cdots Y_m$$
Minden egyes szabály egyetlen nemterminálison cserél, a kontextus biztosítja, hogy a csere a helyes pozícióban történjen.
---

## 23. Mi az átmenetdiagram jelölése veremautomatánál?
?
$$q \xrightarrow{a;\, z \to u} p \iff (u, p) \in \delta(z, q, a)$$
ahol végállapotokat kettős karikával, a kezdőállapotot bejövő nyíllal jelöljük. Az $\varepsilon$-átmenetek esetén $a = \varepsilon$ szerepel a él feliratában.
---

