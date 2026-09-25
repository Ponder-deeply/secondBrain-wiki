---
tags: [concept, logika/bizonyitaselmelet]
sources: ["Szintaktikus következmény.pdf"]
derivation: source
updated: 2026-09-08
---

# Predikátumkalkulus axiómasémái

A predikátumkalkulus az elsőrendű logika bizonyításelméleti felépítése: az ítéletkalkulus axiómasémáit a kvantorok és a szabad/kötött behelyettesítés viszonyát rögzítő sémákkal egészíti ki, hogy a szintaktikus következményfogalom elsőrendű szinten is definiálható legyen.

## Tartalom

### A predikátumkalkulus szerepe

Az elsőrendű logika szintaktikai alapokon való felépítése a **predikátumkalkulus** (más néven logikai függvénykalkulus). A szintaktikus következményfogalom definiálásához az [[concepts/logika/axiomasemak-iteletkalkulus]]-ban látott ítéletlogikai axiómák mellé csak a kvantorok és a logikai műveletek kapcsolatát rögzítő axiómákat kell hozzávenni. A levezetés fogalma, a dedukciós tétel és a szintaktikus következményfogalom szó szerint úgy működik, mint az ítéletlogikában — lásd [[concepts/logika/bizonyitaselmeleti-levezetes]] és [[concepts/logika/dedukcios-tetel]].

### Alap axiómasémák

$$
\begin{aligned}
\text{(B1)}\quad & A \supset (B \supset A) \\
\text{(B2)}\quad & (A \supset (B \supset C)) \supset ((A \supset B) \supset (A \supset C)) \\
\text{(B3)}\quad & (\neg A \supset B) \supset ((\neg A \supset \neg B) \supset A) \\
\text{(B4)}\quad & \forall x A \supset [A(x \| t)] \\
\text{(B5)}\quad & \forall x (A \supset B) \supset (\forall x A \supset \forall x B) \\
\text{(B6)}\quad & A \supset \forall x A, \text{ ahol } x \notin Par(A) \\
\text{(B7)}\quad & \text{a (B1)–(B6) axiómák generalizációi (általánosításai)}
\end{aligned}
$$

Az első három séma (B1)–(B3) az (A1)–(A3) ítéletlogikai axiómák szó szerinti elsőrendű megfelelője. A (B4) az univerzális kvantor eltávolítását (behelyettesítést egy $t$ termmel) engedi meg; a (B5) a kvantor és az implikáció felcserélhetőségét; a (B6) azt, hogy egy olyan formula elé, amelyben $x$ nem szabad paraméter ($x \notin Par(A)$), szabadon odaírható a $\forall x$. A (B7) biztosítja, hogy a (B1)–(B6) sémák generalizált (kvantorral lezárt) alakjai is axiómának számítsanak.

### Kibővített axiómasémák

Ha a teljes elsőrendű nyelvet (mindkét kvantorral) közvetlenül kezeljük, tizenöt sémára bővül a rendszer:

$$
\begin{aligned}
\text{(C1)}\quad & A \supset (B \supset A) \\
\text{(C2)}\quad & (A \supset (B \supset C)) \supset ((A \supset B) \supset (A \supset C)) \\
\text{(C3)}\quad & (\neg A \supset B) \supset ((\neg A \supset \neg B) \supset A) \\
\text{(C4)}\quad & \neg\neg A \supset A \\
\text{(C5)}\quad & A \supset (B \supset A \wedge B) \\
\text{(C6)}\quad & A \wedge B \supset A \\
\text{(C7)}\quad & A \wedge B \supset B \\
\text{(C8)}\quad & (A \supset C) \supset ((B \supset C) \supset (A \vee B \supset C)) \\
\text{(C9)}\quad & A \supset A \vee B \\
\text{(C10)}\quad & B \supset A \vee B \\
\text{(C11)}\quad & \forall x A \supset [A(x \| t)] \\
\text{(C12)}\quad & \forall x (B \supset A) \supset (B \supset \forall x A), \text{ ahol } x \notin Par(B) \\
\text{(C13)}\quad & [A(x \| t)] \supset \exists x A \\
\text{(C14)}\quad & \forall x (A \supset B) \supset (\exists x A \supset B), \text{ ahol } x \notin Par(B) \\
\text{(C15)}\quad & A \supset \forall x A, \text{ ahol } x \notin Par(A) \\
\text{(C16)}\quad & \text{a (C1)–(C15) axiómák generalizációi}
\end{aligned}
$$

A (C11)–(C15) sémák adják meg a két kvantor ($\forall$, $\exists$) egymáshoz és az implikációhoz való viszonyát.

### Egyenlőségjeles predikátumkalkulus

Ha a nyelv tartalmazza az egyenlőségjelet, a (D1)–(D6) sémák megegyeznek (B1)–(B6)-tal, kiegészülve az egyenlőség tulajdonságaival:

$$
\begin{aligned}
\text{(D7)}\quad & t = t \\
\text{(D8)}\quad & t_1 = t_{n+1} \supset \dots \supset t_n = t_{2n} \supset f(t_1, \dots, t_n) = f(t_{n+1}, \dots, t_{2n}) \\
\text{(D9)}\quad & t_1 = t_{n+1} \supset \dots \supset t_n = t_{2n} \supset P(t_1, \dots, t_n) \supset P(t_{n+1}, \dots, t_{2n}) \\
\text{(D10)}\quad & \text{a (D1)–(D9) axiómák generalizációi}
\end{aligned}
$$

(D7) az egyenlőség reflexivitása; (D8)–(D9) az egyenlő termek behelyettesíthetősége függvény-, illetve predikátumszimbólumok argumentumaiban (a behelyettesítés kongruenciatulajdonsága).

## Kapocs

- [[concepts/logika/axiomasemak-iteletkalkulus]] — az ítéletkalkulus axiómasémái, amelyeknek ez a séma az elsőrendű kiterjesztése
- [[concepts/logika/bizonyitaselmeleti-levezetes]] — a levezetés és a szintaktikus következmény fogalma, amely e sémákra épül
- [[concepts/logika/dedukcios-tetel]] — a dedukciós tétel, amely elsőrendű szinten is érvényben marad
- [[concepts/logika/bizonyitaselmelet-helyesseg-teljesseg]] — a predikátumkalkulus helyessége és (nem bizonyított) teljessége
- [[concepts/logika/elsorendu-interpretacio]] — a szemantikai oldal, amelyhez ezek az axiómák tautológiaként kapcsolódnak
- [[concepts/bvszam/elsorendu-logika]] — az elsőrendű logika rokon tárgyalása
