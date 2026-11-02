#flashcards/bvszam/matematikai-alapok
## 1. Mi az $A \subseteq H$ halmaz karakterisztikus függvénye?
?
Az $f_A : H \to \{0,1\}$ függvény, amelyre minden $a \in H$ esetén $f_A(a) = 1$ akkor és csak akkor, ha $a \in A$.
---

## 2. Mit jelöl $\mathcal{P}(H)$, és mit jelöl $[n]$?
?
$\mathcal{P}(H)$ a $H$ halmaz összes részhalmazának halmaza (hatványhalmaz). $[n] = \{1, 2, \ldots, n\}$ a pozitív egészek halmaza $n$-ig; speciálisan $[0] = \emptyset$.
---

## 3. Mi a $H$ halmaz komplementere rögzített $U$ univerzum mellett?
?
$\overline{H} = \{u \in U \mid u \notin H\}$, azaz az $U$-ban lévő, $H$-n kívüli elemek halmaza.
---

## 4. Mi egy $n$ változós $H$-feletti reláció?
?
A $H^n$ Descartes-szorzat egy részhalmaza. Ekvivalensen egy $\hat{\rho} : H^n \to \{igaz, hamis\}$ leképezés, ahol $\hat{\rho}(a_1, \ldots, a_n) = igaz \iff (a_1, \ldots, a_n) \in \rho$.
---

## 5. Mikor reflexív, és mikor tranzitív egy $\rho \subseteq H \times H$ kétváltozós reláció?
?
- **Reflexív:** minden $a \in H$-ra $a\rho a$.
- **Tranzitív:** minden $a, b, c \in H$-ra, ha $a\rho b$ és $b\rho c$, akkor $a\rho c$.
---

## 6. Mi a $\rho$ reláció reflexív és tranzitív lezártja?
?
Az a legszűkebb $\rho^*$ reláció, amely reflexív, tranzitív, és $\rho \subseteq \rho^*$. (Ez adja a generatív grammatikák $\Rightarrow^*$ levezetési relációjának definícióját.)
---

## 7. Mi a különbség az irányítatlan és az irányított gráf között?
?
- **Irányítatlan gráf:** $E \subseteq \{\{a,b\} \mid a, b \in V\}$, az élek rendezetlen párok.
- **Irányított gráf:** $E \subseteq V \times V$, az élek rendezett párok; $E$ egy kétváltozós $V$-feletti reláció.
---

## 8. Mi a séta, az út és a kör egy $G = (V, E)$ irányítatlan gráfban?
?
Legyen $u = a_1 a_2 \ldots a_n$ ($n \ge 2$, $a_i \in V$).
- **Séta:** minden $i \in [n-1]$-re $\{a_i, a_{i+1}\} \in E$.
- **Út:** séta, amelynek csúcsai páronként különböznek.
- **Kör:** $a_1 = a_n$ és $a_1, \ldots, a_{n-1}$ csúcsok páronként különböznek.
---

## 9. Mi a Hamilton-út és a Hamilton-kör?
?
- **Hamilton-út:** olyan út, amely a $G$ összes csúcsát tartalmazza.
- **Hamilton-kör:** olyan kör, amely a $G$ összes csúcsát tartalmazza.
A $G$ **körmentes**, ha nem tartalmaz kört.
---

## 10. Mit jelent, hogy egy gráf összefüggő, fa, illetve mikor feszítőfa egy részgráf?
?
- **Összefüggő:** bármely két csúcsa között vezet út.
- **Fa:** összefüggő és körmentes.
- **Feszítőfa:** $G' = (V', E')$ feszítőfája $G$-nek, ha $G'$ fa, $V' = V$ és $E' \subseteq E$.
---

## 11. Hogyan definiáljuk egy csúcs fokát irányítatlan gráfban?
?
Az $u \in V$ csúcs foka: $|\{v \in V \mid \{u,v\} \in E\}|$, azaz az $u$-val éllel összekötött csúcsok száma.
---

## 12. Mik az ítéletkalkulus szintaktikai alapegységei, és hogyan épül fel a $Form$ halmaz?
?
Az **ítéletváltozók** halmaza $Var = \{x_1, x_2, \ldots\}$. A formulák $Form$ halmaza a legszűkebb halmaz, amelyre:
- minden $x \in Var$ esetén $x \in Form$,
- ha $\varphi \in Form$, akkor $\neg\varphi \in Form$,
- ha $\varphi_1, \varphi_2 \in Form$, akkor $(\varphi_1 \circ \varphi_2) \in Form$, ahol $\circ \in \{\land, \lor, \to\}$.
---

## 13. Mi az interpretáció az ítéletkalkulusban, és hogyan terjesztjük ki formulákra?
?
Egy $I : Var_n \to \{igaz, hamis\}$ leképezés. Kiterjesztés $Form_n$-re: $I(\varphi) = igaz$ ha
- $\varphi \in Var_n$ és $I(\varphi) = igaz$, vagy
- $\varphi = \neg\psi$ és $I(\psi) = hamis$, vagy
- $\varphi = (\varphi_1 \land \varphi_2)$ és $I(\varphi_1) = I(\varphi_2) = igaz$, vagy
- $\varphi = (\varphi_1 \lor \varphi_2)$ és $I(\varphi_1) = igaz$ vagy $I(\varphi_2) = igaz$, vagy
- $\varphi = (\varphi_1 \to \varphi_2)$ és $I(\varphi_1) = hamis$ vagy $I(\varphi_2) = igaz$.
---

## 14. Mit jelent, hogy egy formula kielégíthető, kielégíthetetlen vagy tautológia?
?
- **Kielégíthető:** van olyan $I$, hogy $I \models \varphi$ (azaz $I(\varphi) = igaz$).
- **Kielégíthetetlen:** nincs ilyen $I$.
- **Tautológia (érvényes):** minden $I$-re $I \models \varphi$.
---

## 15. Mikor logikai következménye $\varphi$ az $F$ formulahalmaznak, és mikor ekvivalens két formula?
?
- $F \models \varphi$: minden $I$-re, ha $I \models F$ (minden $F$-beli formulát kielégít), akkor $I \models \varphi$.
- $\varphi_1$ és $\varphi_2$ **ekvivalens**, ha minden $I$-re $I \models \varphi_1 \iff I \models \varphi_2$.
---

## 16. Mondja ki az 1.1-es tételt a kielégíthetetlenségről és a logikai következményről!
?
Legyen $F$ formulahalmaz és $\varphi$ formula. Ekkor:
- $\varphi$ kielégíthetetlen $\iff$ $\neg\varphi$ tautológia.
- $F \models \varphi$ $\iff$ $F \cup \{\neg\varphi\}$ kielégíthetetlen.
---

## 17. Mi a literál, a klóz és a konjunktív normálforma (KNF)?
?
- **Literál:** $x$ vagy $\neg x$ alakú formula ($x \in Var$); az $x$ a literál **alapja**.
- **Klóz:** $l_1 \lor l_2 \lor \ldots \lor l_n$ alakú formula, ahol $l_1, \ldots, l_n$ páronként különböző alapú literálok.
- **KNF:** $C_1 \land C_2 \land \ldots \land C_m$ ($m \ge 1$), ahol minden $C_i$ klóz.
Minden ítéletkalkulusbeli formulához megadható vele ekvivalens KNF.
---

## 18. Mik egy $\mathcal{L}$ elsőrendű nyelv szimbólumhalmázának részei?
?
- **Predikátumszimbólumok** $Pred$, **függvényszimbólumok** $Func$, **konstansszimbólumok** $Const$ véges halmazai.
- **Egyedváltozók** $Ind = \{x_1, x_2, \ldots\}$ megszámlálhatóan végtelen halmaza.
- Műveleti jelek: $\{\neg, \land, \lor, \to\}$.
- Kvantorok: $\forall$ (univerzális) és $\exists$ (egzisztenciális).
- Segédjelek: $($ , $)$ , $,$.
Minden $s \in Const \cup Pred \cup Func$ szimbólumhoz tartozik egy $ar(s)$ nemnegatív egész **aritás**; konstansszimbólumok aritása $0$.
---

## 19. Hogyan épül fel az elsőrendű logikában a termek $Term$ halmaza?
?
$Term$ a legszűkebb halmaz, amelyre:
- $Ind \cup Const \subseteq Term$ (egyedváltozók és konstansok termek),
- ha $f \in Func$ és $t_1, \ldots, t_{ar(f)} \in Term$, akkor $f(t_1, \ldots, t_{ar(f)}) \in Term$.
---

## 20. Mi az elsőrendű logikában az atomi formulák halmaza?
?
**Atomi formulák** ($AForm$): ha $p \in Pred$ és $t_1, \ldots, t_{ar(p)} \in Term$, akkor $p(t_1, \ldots, t_{ar(p)}) \in AForm$.
---

## 21. Mi az elsőrendű logika egy interpretációja?
?
Egy $I = \langle U, I_{Pred}, I_{Func}, I_{Const} \rangle$ struktúra, ahol:
- $U$ tetszőleges nemüres halmaz (**univerzum**),
- $I_{Pred}$: minden $p \in Pred$-hez egy $ar(p)$ változós $U$-feletti $p^I$ relációt rendel,
- $I_{Func}$: minden $f \in Func$-hoz egy $f^I : U^{ar(f)} \to U$ függvényt rendel,
- $I_{Const}$: minden $a \in Const$-hoz egy $a^I \in U$ elemet rendel.
---

## 22. Mi a változókiértékelés, és hogyan értékelünk ki egy $t$ termet $(I, \kappa)$ mellett?
?
A $\kappa : Ind \to U$ **változókiértékelés**. Egy $t \in Term$ értéke $|t|^{I,\kappa}$:
- $|a|^{I,\kappa} = a^I$ konstansra,
- $|x|^{I,\kappa} = \kappa(x)$ egyedváltozóra,
- $|f(t_1, \ldots, t_n)|^{I,\kappa} = f^I(|t_1|^{I,\kappa}, \ldots, |t_n|^{I,\kappa})$.
---

## 23. Hogyan értékelünk ki egy $\varphi$ formulát $(I, \kappa)$ mellett, különös tekintettel a kvantorokra?
?
Az atomi $p(t_1, \ldots, t_n)$ esetén $|\varphi|^{I,\kappa} = igaz \iff (|t_1|^{I,\kappa}, \ldots, |t_n|^{I,\kappa}) \in p^I$. A logikai összekötők az ítéletkalkulushoz hasonlóan. A kvantorokra:
- $|\exists x\psi|^{I,\kappa} = igaz \iff$ van olyan $\kappa'$ $x$-variánsa $\kappa$-nak, hogy $|\psi|^{I,\kappa'} = igaz$,
- $|\forall x\psi|^{I,\kappa} = igaz \iff$ minden $\kappa'$ $x$-variánsra $|\psi|^{I,\kappa'} = igaz$.
---

## 24. Mi a $\kappa$ változókiértékelés $x$-variánsa?
?
Egy olyan $\kappa' : Ind \to U$ változókiértékelés, amely legfeljebb $x$ értékében tér el $\kappa$-tól, azaz minden $y \neq x$ egyedváltozóra $\kappa'(y) = \kappa(y)$.
---

## 25. Mit jelent, hogy egy változóelőfordulás kötött vagy szabad, és mikor zárt egy formula?
?
Egy $x \in Ind$ előfordulása $\varphi$-ben **kötött**, ha $\varphi$ egy $\exists x\psi$ vagy $\forall x\psi$ alakú részformulájában szerepel; egyébként **szabad**. Ha $\varphi$-ben minden egyedváltozó minden előfordulása kötött, akkor $\varphi$ **zárt formula** (mondat). Zárt formula esetén $|\varphi|^{I,\kappa}$ független $\kappa$-tól, így $|\varphi|^I$-t írunk.
---

## 26. Mi az ítéletkalkulus és az elsőrendű logika közötti fő különbség?
?
Az **ítéletkalkulusban** az elemi állítások (ítéletváltozók) paramétermentes igen/nem értékek; az interpretáció egyszerű $Var \to \{igaz, hamis\}$ leképezés. Az **elsőrendű logikában** az állítások paraméteres predikátumok egy $U$ univerzumon, függvény- és konstanszimbólumokkal; az interpretáció egy teljes algebrai struktúra $\langle U, I_{Pred}, I_{Func}, I_{Const} \rangle$.
---

