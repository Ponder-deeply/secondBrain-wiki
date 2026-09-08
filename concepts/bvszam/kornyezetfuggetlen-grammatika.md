---
tags: [concept]
sources: [szelmJegyzet.pdf, "5.-környezetfüggetlen-gramm,-cnf,-cyk-pumpálási-lemma.md"]
derivation: source
updated: 2026-08-05
---

# Környezetfüggetlen grammatika

A 2-es típusú (környezetfüggetlen, KF) grammatika olyan generatív grammatika, amelynek minden szabálya $A \to u$ alakú ($A \in N$, $u \in (N \cup T)^*$); a generált nyelveket veremautomaták ismerik fel.

## Tartalom

### Definíció

Egy $G = \langle N, T, P, S \rangle$ grammatika **környezetfüggetlen (KF)**, ha minden $P$-beli szabály $A \to u$ alakú, ahol $A \in N$ és $u \in (N \cup T)^*$.

### Aktív és elérhető nemterminálisok

**Aktív** nemterminális: levezethető belőle terminális szó.

Iteratív meghatározás:
$$A_1 = \{X \mid X \to u \in P, u \in T^*\}, \quad A_{i+1} = A_i \cup \{X \mid X \to w \in P, w \in (T \cup A_i)^*\}$$

**Elérhető** nemterminális: előfordul a kezdőszimbólumból levezethető mondatformában.

$$R_1 = \{S\}, \quad R_{i+1} = R_i \cup \{Y \in N \mid X \to uYw \in P, X \in R_i\}$$

### Redukált grammatika

> **Definíció:** Egy KF grammatika **redukált**, ha minden nemterminálisa aktív és elérhető.

> **Tétel:** Minden KF grammatikához létezik vele ekvivalens redukált KF grammatika.

Konstrukció: inaktív nemterminálisok és szabályaik elhagyása, majd elérhetetlen nemterminálisok elhagyása.

#### Kidolgozott példa

Kiindulási grammatika:
```
S → A | bBD
A → AB | A
B → ε | a | SS
C → AS | a
D → BB
```

**Aktívak meghatározása:**
- $A_1 = \{B, C\}$ (B-ből és C-ből vezethető le terminális: $B \to a$, $C \to a$)
- $A_2 = \{B, C, D\}$ ($D \to BB$, $B$ aktív)
- $A_3 = A_4 = \{B, C, D, S\}$ ($S \to bBD$, mindkét komponens aktív)
- $A$ inaktív marad (nincs terminális levezetése), ezért $A$-t tartalmazó szabályok törlendők.

Az inaktívak elhagyása után:
```
S → bBD
B → ε | a | SS
C → a
D → BB
```

**Elérhetők meghatározása:**
- $R_1 = \{S\}$
- $R_2 = \{S, B, D\}$ ($S \to bBD$ alapján)
- $R_3 = R_2 = \{S, B, D\}$ (D-ből nincs új)

$C$ nem elérhető, törlendő.

**Redukált ekvivalens grammatika:**
```
S → bBD
B → ε | a | SS
D → BB
```

### Chomsky normálforma

Lásd [[concepts/bvszam/chomsky-normalforma|chomsky-normalforma]] részletesen.

### Levezetési fa

Lásd [[concepts/bvszam/levezetes-fa|levezetes-fa]].

### Algoritmikus problémák

- **Végesség:** $L(G)$ végtelen $\iff$ van $p < |\beta| \leq p+q$ hosszú szó (Bar-Hillel lemma konstansai). Eldönthető.
- **Üresség:** $L(G) = \emptyset \iff$ nincs $\leq p$ hosszú szó. Eldönthető.
- **Szóprobléma:** CYK algoritmus $O(n^3)$ lépésben. Eldönthető.

### Eldönthetetlen problémák

A PMP-re való visszavezetéssel megmutatható, hogy a KF grammatikák több fontos kérdése **eldönthetetlen**.

**Egyértelműség (2.30. tétel).** Egy $G$ KF grammatika *egyértelmű*, ha minden $L(G)$-beli szónak pontosan egy baloldali levezetése van. Adott $D$ PMP-példányból ($u_i, v_i \in \Sigma^+$) építhető egy $G$ grammatika, amely pontosan akkor nem egyértelmű, ha $D$-nek van megoldása: $G$-be két párhuzamos szabályrendszert teszünk, $G_A$-t az $u_i$-kre és $G_B$-t a $v_i$-kre (egy $\Delta = \{a_1, \ldots, a_n\}$ indexábécé felett), és egy $w$ szónak pontosan akkor van kétféle levezetése, ha az index-rész ugyanazt a dominósorozatot kódolja felül és alul. Tehát **a KF grammatikák egyértelműsége eldönthetetlen**.

**Két KF nyelvre vonatkozó kérdések (2.31. tétel).** Az előbbi bizonyítás $G_A$, $G_B$ grammatikáit (és az $L_A = L(G_A)$, $L_B = L(G_B)$ nyelveket) felhasználva eldönthetetlen, hogy két $G_1, G_2$ KF grammatikára:

1. $L(G_1) \cap L(G_2) = \emptyset$? — közvetlenül a 2.30. bizonyításából, mert $D$-nek akkor és csak akkor van megoldása, ha $L_A \cap L_B \neq \emptyset$.
2. $L(G_1) = L(G_2)$? — mivel $\overline{L_A}, \overline{L_B}$ is KF, és a KF nyelvek zártak az unióra, $\overline{L_A} \cup \overline{L_B} = \overline{L_A \cap L_B}$ KF; az $L(G_1) = L(G_2) = (\Sigma\cup\Delta)^*$ kérdés visszaadja az 1. pontot.
3. $L(G_1) = \Gamma^*$ valamely $\Gamma$ ábécére? — ha eldönthető lenne, az 1. pont is eldönthető lenne.
4. $L(G_1) \subseteq L(G_2)$? — a 2. pont következménye: $L(G_1) = L(G_2) \iff L(G_1) \subseteq L(G_2) \wedge L(G_2) \subseteq L(G_1)$.

(Megjegyzés: a KF nyelvek **nem** zártak a komplementerképzésre, de $\overline{L_A}$ és $\overline{L_B}$ ezen speciális nyelvekre mégis KF — ezt a jegyzet bizonyítás nélkül közli.)

## Kapocs

- [[concepts/bvszam/post-megfelelkezesi-problema]] — a KF eldönthetetlenségi bizonyítások forrása
- [[concepts/bvszam/eldonthetetlen-problemak]] — eldönthetetlen problémák áttekintése

- [[concepts/bvszam/chomsky-hierarchia]] — a KF grammatikák helye
- [[concepts/bvszam/chomsky-normalforma]] — CNF transzformáció lépései
- [[concepts/bvszam/bar-hillel-lemma]] — pumpálási lemma KF nyelvekre
- [[concepts/bvszam/cyk-algoritmus]] — $O(n^3)$ szóprobléma-megoldó
- [[concepts/bvszam/veremautomata]] — KF felismerők
- [[concepts/bvszam/levezetes-fa]] — levezetés fa-reprezentációja
