#flashcards/bvszam/alapfogalmak
## 1. Mi az ábécé ($\Sigma$) definíciója a formális nyelvek elméletében?
?
Az **ábécé** ($\Sigma$, néhány forrásban $V$) egy véges, nemüres szimbólumhalmaz; elemei a **betűk**. A betűk tetszőleges szimbólumok lehetnek.
---

## 2. Mi egy szó, és hogyan jelöljük a hosszát?
?
Egy **szó** a $\Sigma$ ábécé feletti szó: a $\Sigma$ betűinek tetszőleges véges sorozata. Ha $u = t_1 \cdots t_n$, akkor a szó hossza $l(u) = |u| = n$.
---

## 3. Mi az üres szó, és mi a hossza?
?
Az **üres szó** jele $\varepsilon$, és hossza $l(\varepsilon) = 0$. Egyetlen betűt sem tartalmaz.
---

## 4. Mit jelent a $\Sigma^*$ és a $\Sigma^+$ jelölés?
?
- $\Sigma^*$: az összes $\Sigma$ feletti szó halmaza, beleértve $\varepsilon$-t.
- $\Sigma^+ = \Sigma^* \setminus \{\varepsilon\}$: az összes nemüres $\Sigma$ feletti szó halmaza.
---

## 5. Hogyan értelmezzük a betűszámlálót, és mi a szavak kanonikális rendezése?
?
Az $a \in \Sigma$ betűre $l_a(u)$ jelöli az $u$ szóban az $a$ betűk számát. A szavak kanonikális rendezése a **hosszlexikografikus (shortlex) sorrend**: először hossz szerint, azonos hosszon belül lexikografikusan rendezünk.
---

## 6. Hogyan értelmezzük a szavak konkatenációját, és milyen tulajdonságai vannak?
?
Ha $u = s_1 \cdots s_n$ és $v = t_1 \cdots t_k$, akkor $uv = s_1 \cdots s_n t_1 \cdots t_k$.
Tulajdonságok:
- $|uv| = |u| + |v|$
- **Asszociatív**, de általában **nem kommutatív**
- Egységelem: $\varepsilon$
- $\Sigma^*$ konkatenációra zárt (monoid)
---

## 7. Hogyan értelmezzük a szóhatványozást?
?
$u^0 := \varepsilon$, $u^i := u \cdot u^{i-1}$ minden $i \geq 1$-re. Tulajdonság: $u^{n+k} = u^n u^k$.
---

## 8. Mi egy szó tükörképe, és mi a palindróma?
?
Az $u = a_1 \cdots a_n$ szó **tükörképe**: $u^{-1} = a_n \cdots a_1$.
Tulajdonság: $(uv)^{-1} = v^{-1} u^{-1}$.
Ha $u = u^{-1}$, akkor $u$ **palindróma**.
---

## 9. Mit jelent a részszó, prefix és suffix fogalma?
?
- $u$ **részszava** $v$-nek, ha $v = xuy$ valamely $x, y \in \Sigma^*$-ra.
- Ha $x = \varepsilon$: $u$ **prefix**je $v$-nek.
- Ha $y = \varepsilon$: $u$ **suffix**e $v$-nek.
- **Valódi** prefix/suffix: sem $\varepsilon$, sem maga az egész szó nem számít valódinak.
---

## 10. Mi a formális nyelv definíciója?
?
Egy $\Sigma$ ábécé feletti **formális nyelv** a $\Sigma^*$ egy tetszőleges részhalmaza: $L \subseteq \Sigma^*$.
- **Üres nyelv**: $\emptyset$ (egyetlen szót sem tartalmaz)
- **Véges/végtelen** nyelv: véges ill. végtelen sok szót tartalmaz
---

## 11. Milyen halmazműveletek értelmezhetők nyelveken?
?
| Művelet | Definíció |
|---|---|
| Unió | $L_1 \cup L_2$ |
| Metszet | $L_1 \cap L_2$ |
| Különbség | $L_1 \setminus L_2$ |
| Komplementer | $\bar{L} = \Sigma^* \setminus L$ |
---

## 12. Hogyan értelmezzük nyelvek konkatenációját és hatványozását?
?
$$L_1 L_2 = \{u_1 u_2 \mid u_1 \in L_1,\, u_2 \in L_2\}$$
Hatványozás: $L^0 = \{\varepsilon\}$, $L^i = L \cdot L^{i-1}$ minden $i \geq 1$-re.
A konkatenáció asszociatív, de általában **nem kommutatív**.
---

## 13. Mit jelent a Kleene-lezárt ($L^*$) és a pozitív lezárt ($L^+$)?
?
$$L^* = \bigcup_{i \geq 0} L^i \qquad L^+ = \bigcup_{i \geq 1} L^i$$
Ha $\varepsilon \in L$: $L^+ = L^*$; egyébként $L^+ = L^* \setminus \{\varepsilon\}$.
Azonosságok: $L^* L^* = L^*$, $(L^*)^* = L^*$, $(L_1 \cup L_2)^* = (L_1^* L_2^*)^*$.
---

## 14. Hogyan értelmezzük egy nyelv tükörképét?
?
$$L^{-1} = \{u^{-1} \mid u \in L\}$$
Tulajdonságok:
- $(L_1 L_2)^{-1} = L_2^{-1} L_1^{-1}$
- $(L^*)^{-1} = (L^{-1})^*$
---

## 15. Mit jelent a prefix- ($\text{PRE}$) és suffixnyelv ($\text{SUF}$)?
?
- $\text{PRE}(L) = \{u \mid \exists v : uv \in L\}$ — az $L$ szavainak összes prefixe.
- $\text{SUF}(L) = \{u \mid \exists v : vu \in L\}$ — az $L$ szavainak összes suffixe.
---

## 16. Mit jelent, hogy egy nyelvcsalád zárt egy műveletre?
?
Egy $\mathcal{L}$ **nyelvcsalád zárt** egy $n$-változós $\varphi$ műveletre nézve, ha $L_1, \ldots, L_n \in \mathcal{L}$ esetén $\varphi(L_1, \ldots, L_n) \in \mathcal{L}$.
Minden Chomsky-osztály ($\mathcal{L}_0, \mathcal{L}_1, \mathcal{L}_2, \mathcal{L}_3$) zárt az unióra, konkatenációra és Kleene-lezártra (**reguláris műveletek**).
---

## 17. Mi a homomorfizmus definíciója ábécék felett?
?
Legyen $V_1$ és $V_2$ két ábécé. A $h : V_1^* \to V_2^*$ leképezés **homomorfizmus**, ha:
1. Minden szóra pontosan egy kép van (egyértelmű).
2. $h(uv) = h(u)h(v)$ minden $u, v \in V_1^*$-ra (konkatenációt megőriz).
---

## 18. Mi következik a homomorfizmus definíciójából az üres szóra és a betűkre?
?
Következmények:
- $h(\varepsilon) = \varepsilon$ (az üres szó képe az üres szó)
- $h$ teljesen meghatározott az ábécé betűin felvett értékekből:
$$h(a_1 a_2 \cdots a_n) = h(a_1) h(a_2) \cdots h(a_n)$$
Tehát elég az egyes betűk képét megadni, a többi következik.
---

## 19. Mi az ε-mentes homomorfizmus?
?
A $h : V_1^* \to V_2^*$ homomorfizmus **ε-mentes**, ha minden $u \in V_1^+$-ra $h(u) \neq \varepsilon$, azaz egyetlen nemüres szót sem képez az üres szóra.
---

## 20. Mi a homomorf kép, és hogyan számítjuk ki?
?
Az $L \subseteq V_1^*$ nyelv **$h$-homomorf képe**:
$$h(L) = \{h(u) \mid u \in L\}$$
Például: $V_1 = \{a,b\}$, $V_2 = \{b,c\}$, $h(a) = cc$, $h(b) = cbb$, $L = \{a^n b a^n \mid n \in \mathbb{N}\}$, ekkor:
$$h(L) = \{c^{2n+1} b^2 c^{2n} \mid n \in \mathbb{N}\}$$
---

