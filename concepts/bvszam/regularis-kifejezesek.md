---
tags: [concept]
sources: [2.-lingram-és-regexp.md, 4.-myhill-nerode-és-minimál-automata.md]
derivation: source
updated: 2026-09-04
---

# Reguláris kifejezések

A reguláris kifejezés egy tömör, algebrai eszköz reguláris nyelvek leírására; pontosan a 3-as típusú (reguláris) nyelveket írják le, és szorosan kapcsolódnak a véges automatákhoz.

## Tartalom

### Definíció (rekurzív)

Legyenek $V$ és $V' = \{\emptyset, \varepsilon, \cdot, +, *, (, )\}$ diszjunkt ábécék. A $V$ feletti reguláris kifejezések:

1. $\emptyset$ — reguláris kifejezés
2. $\varepsilon$ — reguláris kifejezés
3. $a \in V$ — reguláris kifejezés
4. Ha $R$ reguláris kifejezés → $R^*$ is az
5. Ha $Q, R$ reguláris kifejezések → $(Q \cdot R)$ is
6. Ha $Q, R$ reguláris kifejezések → $(Q + R)$ is

### Az $L(R)$ nyelv

| Kifejezés | Jelölt nyelv |
|---|---|
| $L(\emptyset)$ | $\emptyset$ |
| $L(\varepsilon)$ | $\{\varepsilon\}$ |
| $L(a)$ | $\{a\}$ |
| $L(R^*)$ | $L(R)^*$ |
| $L(Q \cdot R)$ | $L(Q) \cdot L(R)$ |
| $L(Q + R)$ | $L(Q) \cup L(R)$ |

Precedencia: $* > \cdot > +$.

### Azonosságok

$P + Q = Q + P$; $P \cdot (Q + R) = PQ + PR$; $P^* = \varepsilon + P \cdot P^*$; $P^* = (\varepsilon + P)^*$; $P \cdot \emptyset = \emptyset$.

### Arden tétele

> **Tétel:** A $P = R + P \cdot Q$ egyenletnek $P$-re vonatkozó megoldása $P = R \cdot Q^*$. Ha $\varepsilon \notin Q$, ez az egyetlen megoldás.

**Bizonyítás:**

**(1) $P = R \cdot Q^*$ valóban megoldás:**

$$R + P \cdot Q = R + (R \cdot Q^*) \cdot Q = R + R \cdot (Q \cdot Q^*) = R \cdot (\varepsilon + Q \cdot Q^*) = R \cdot Q^* = P.$$

**(2) Az egyedüliség (ha $\varepsilon \notin Q$):**

Ismételt helyettesítéssel:

$$P = R + P \cdot Q = R + (R + P \cdot Q) \cdot Q = R + RQ + PQ^2 = \cdots = R(\varepsilon + Q + \cdots + Q^n) + PQ^{n+1}.$$

Legyen $w \in P$ tetszőleges, és $n = |w|$. Mivel $\varepsilon \notin Q$, a $Q^{n+1}$ minden szava legalább $n+1$ hosszú, így $w \notin PQ^{n+1}$. Ezért

$$w \in R(\varepsilon + Q + \cdots + Q^n) \subseteq RQ^*.$$

Fordítva, ha $w \in RQ^*$, akkor van $n$, hogy $w \in RQ^n$, ami a jobb oldalban van, tehát $P$-ben is. Így csak $P = R \cdot Q^*$ lehetséges. $\square$

Alkalmazás: grammatikából reguláris kifejezés levezetése egyenletrendszer-megoldással.

### Ekvivalencia a reguláris grammatikákkal

> **Tétel:** Minden reguláris kifejezés reguláris (3-as típusú) nyelvet jelöl, és megfordítva.

**$\Rightarrow$ irány:** $\emptyset$, $\{\varepsilon\}$, $\{a\}$ regulárisak; $\mathcal{L}_3$ zárt a reguláris műveletekre.

**$\Leftarrow$ irány (konstrukció):** Legyen $N = \{A_1, \ldots, A_n\}$, $S = A_1$, és minden szabály $A_i \to aA_j$ vagy $A_i \to \varepsilon$ alakú.

**$k$-megszorított levezetés:** Az $A_i \Rightarrow^* u A_j$ levezetést $k$-megszorítottnak nevezzük, ha minden érintett közbülső nemterminális indexe legfeljebb $k$.

**Az $E^k_{i,j}$ halmazok definíciója** ($0 \leq k \leq n$, $1 \leq i,j \leq n$):

$$E^k_{i,j} := \{u \in T^* \mid \text{létezik } A_i \Rightarrow^* uA_j \text{ } k\text{-megszorított levezetés}\}$$

**Alaplépés ($k = 0$):**
- Ha $i \neq j$: $E^0_{i,j} = \{a \in T \mid A_i \to aA_j \in R\}$ (üres, ha nincs ilyen szabály).
- Ha $i = j$: $E^0_{i,i} = \{\varepsilon\} \cup \{a \in T \mid A_i \to aA_i \in R\}$.

**Rekurzív összefüggés** ($k \geq 1$):

$$E^k_{i,j} = E^{k-1}_{i,j} + E^{k-1}_{i,k} \cdot (E^{k-1}_{k,k})^* \cdot E^{k-1}_{k,j}$$

Értelmezés: az $A_i$-ből $A_j$-be vezető $k$-megszorított levezetés vagy már $(k{-}1)$-megszorított, vagy útközben átmegy $A_k$-n (tetszőleges sokszor), az $A_k$-n belül maradva $A_k$-t $A_k$-ba $(k{-}1)$-megszorítottan vezeti vissza.

Indukcióval belátható, hogy $E^0$ reguláris kifejezéssel jelölhető, és ha az $E^{k-1}$ halmazok mindegyike jelölhető reguláris kifejezéssel, akkor $E^k$ is az.

**Végeredmény:** Legyen $I_\varepsilon = \{i \mid A_i \to \varepsilon \in R\}$. Ekkor:

$$L(G) = \bigcup_{i \in I_\varepsilon} E^n_{1,i}$$

**Kidolgozott példa** ($A_1 \to bA_1 \mid aA_2$, $A_2 \to bA_1 \mid \varepsilon$):

$E^0$ táblázat:

|  | $j=1$ | $j=2$ |
|--|--|--|
| $i=1$ | $\varepsilon + b$ | $a$ |
| $i=2$ | $b$ | $\varepsilon$ |

$E^1$ táblázat (az $A_1$-en való átmenetek felvételével):

|  | $j=1$ | $j=2$ |
|--|--|--|
| $i=1$ | $b^*$ | $b^*a$ |
| $i=2$ | $b^+$ | $\varepsilon + b^+a$ |

$E^2$ táblázat (az $A_2$-n való átmenetek felvételével):

|  | $j=1$ | $j=2$ |
|--|--|--|
| $i=1$ | $b^* + b^*a(b+a)^*b^+$ | $b^*a(b+a)^*$ |
| $i=2$ | $(b+a)^*b^+$ | $(b+a)^*$ |

Részletezett számítás az $E^2_{1,2}$ értékre:

$$E^2_{1,2} = E^1_{1,2} + E^1_{1,2} \cdot (E^1_{2,2})^* \cdot E^1_{2,2}$$
$$= b^*a + b^*a \cdot (\varepsilon + b^+a)^* \cdot (\varepsilon + b^+a) = b^*a(b^+a)^*$$

Mivel $I_\varepsilon = \{2\}$ (csak $A_2 \to \varepsilon \in R$), a grammatika által generált nyelv:

$$L(G) = E^2_{1,2} = b^*a(b+a)^*$$

### Reguláris kifejezésből VDA

Lépések:
1. Általánosított ε-VNDA felépítése ($Q \xrightarrow{R} Q'$ típusú átmenetekkel), rekurzív lebontással.
2. ε-átmenetek eliminálása: $H(q) = \{q' \mid q \overset{*}{\Rightarrow}_\varepsilon q'\}$, majd $\delta'(q,a)$ és $F'$ meghatározása.
3. VNDA determinizálása hatványhalmaz-konstrukcióval.

## Kapocs

- [[concepts/bvszam/linearis-grammatika]] — jobb-lineáris grammatikák ~ reguláris kifejezések
- [[concepts/bvszam/vda]] — véges automata mint felismerő eszköz
- [[concepts/bvszam/vnda]] — nemdeterminisztikus automata, determinizálás
- [[concepts/bvszam/myhill-nerode]] — a reguláris nyelvek véges maradéknyelv-számosság karakterizációja
