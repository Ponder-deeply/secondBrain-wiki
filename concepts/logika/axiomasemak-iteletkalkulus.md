---
tags: [concept]
sources: ["Szintaktikus következmény.pdf"]
derivation: source
updated: 2026-09-08
---

# Axiómasémák az ítéletkalkulusban

Az ítéletkalkulus az ítéletlogika szintaktikai (bizonyításelméleti) felépítése: az ítéletlogikát mint axiomatizált matematikai struktúrát kezeli, ahol néhány kitüntetett formulasémát (axiómasémát) és egy levezetési szabályt (modus ponens) veszünk alapul, interpretáció nélkül.

## Tartalom

### Az ítéletlogika mint matematikai struktúra

Az ítéletkalkulus az ítéletlogikát a $\langle \{i, h\}, \neg, \supset \rangle$ struktúraként kezeli: az igazságértékek halmaza a két alapművelettel, negáció és implikáció. Ez a pár **funkcionálisan teljes** művelethalmaz — a $\wedge$, $\vee$ a szokásos módon kifejezhető velük —, ezért az axiómasémák felírásához elég csak $\neg$-t és $\supset$-t használni. A struktúra fogalmáról lásd [[concepts/logika/matematikai-struktura]].

### Alap axiómasémák

$$
\begin{aligned}
\text{(A1)}\quad & X \supset (Y \supset X) \\
\text{(A2)}\quad & (X \supset (Y \supset Z)) \supset ((X \supset Y) \supset (X \supset Z)) \\
\text{(A3)}\quad & (\neg X \supset Y) \supset ((\neg X \supset \neg Y) \supset X)
\end{aligned}
$$

Ezek **sémák**: bennük $X, Y, Z$ tetszőleges ítéletlogikai formula helyére állhat, nem csak ítéletváltozó — lásd [[concepts/logika/iteletlogikai-formula]].

### Kibővített axiómasémák

Ha a teljes $\{\neg, \wedge, \vee, \supset\}$ művelethalmazt közvetlenül akarjuk kezelni (nem visszavezetve $\neg, \supset$-ra), az (A1)–(A3) mellé még hét séma kerül:

$$
\begin{aligned}
\text{(A4)}\quad & \neg\neg X \supset X \\
\text{(A5)}\quad & X \supset (Y \supset X \wedge Y) \\
\text{(A6)}\quad & X \wedge Y \supset X \\
\text{(A7)}\quad & X \wedge Y \supset Y \\
\text{(A8)}\quad & (X \supset Z) \supset ((Y \supset Z) \supset (X \vee Y \supset Z)) \\
\text{(A9)}\quad & X \supset X \vee Y \\
\text{(A10)}\quad & Y \supset X \vee Y
\end{aligned}
$$

### Az axiómák kapcsolata a szemantikával

Az axiómák **tautológiák** (logikai törvények) — ez köti össze a szintaktikus és a szemantikus tárgyalást, lásd [[concepts/logika/kovetkeztetesforma]].

**Helyettesítési tétel:** legyen $G$ egy formula, és $G(X|S)$ az a formula, amit $G$-ből az $X$ változó $S$ formulával való helyettesítésével kapunk. Ha $G$ tautológia, akkor $G(X|S)$ is az. Következmény: az axiómákból behelyettesítéssel kapott formulák is logikai törvények — tehát maguk is axiómának tekinthetők.

**Modus ponens tétel (szemantikai oldal):** $\{A \supset B, A\} \models_0 B$ — ha $A \supset B$ és $A$ is igaz egy interpretációban, akkor $B$ is az. Ez a szemantikai tény indokolja, hogy a modus ponens legyen az egyetlen levezetési szabály: lásd [[concepts/logika/bizonyitaselmeleti-levezetes]].

## Kapocs

- [[concepts/logika/bizonyitaselmeleti-levezetes]] — a levezetés fogalma, amely ezekre az axiómasémákra és a modus ponensre épül
- [[concepts/logika/iteletlogikai-formula]] — a nyelv, amelynek formulái az axiómasémákat kitöltik
- [[concepts/logika/kovetkeztetesforma]] — a szemantikus következményfogalom, amelynek szintaktikus párját az ítéletkalkulus adja
- [[concepts/logika/predikatumkalkulus-axiomasemak]] — az itt bevezetett sémák elsőrendű kiterjesztése
- [[concepts/bvszam/itelet-kalkulus]] — az ítéletkalkulus rokon, tömörebb tárgyalása
