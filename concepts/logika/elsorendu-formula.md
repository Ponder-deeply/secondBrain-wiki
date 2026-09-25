---
tags: [concept, logika/elsorendu-logika-nyelv-es-szintaxis]
sources: ["Elsőrendű_logika_ bevezetés.pdf"]
derivation: source
updated: 2026-09-08
---

# Elsőrendű formula

Az elsőrendű formula az elsőrendű nyelv azon kifejezéstípusa, amely a struktúra logikai leképezéseit szimbolizálja; az atomi formulából szerkezeti rekurzióval épül fel, és — az ítéletlogikai formulához hasonlóan — prímformulákra, komponensekre és szerkezeti fára bontható.

## Tartalom

### Atomi formula

Ha $P \in Pr$ $k$-változós predikátumszimbólum és $t_1, t_2, \dots, t_k$ [[concepts/logika/term|termek]], akkor $P(t_1, t_2, \dots, t_k)$ **atomi formula**. (Többfajtájú esetben a $t_1, \dots, t_k$ termeknek rendre $P$ argumentumfajtáival, $\pi_1, \dots, \pi_k$-val kell megegyezniük.)

### Definíció — formula szerkezeti rekurzióval

A formula ($L_f(V_\nu)$) fogalma:

1. (alaplépés) Minden atomi formula formula.
2. (rekurzív lépés)
   - Ha $A$ formula, akkor $\neg A$ is az.
   - Ha $A$ és $B$ formulák, akkor $(A \circ B)$ is formula, ahol $\circ$ a három binér művelet ($\wedge, \vee, \supset$) bármelyike.
3. Ha $A$ formula, akkor $\forall xA$ és $\exists xA$ is az.
4. Minden formula az 1–3. szabályok véges sokszori alkalmazásával áll elő.

Az elsőrendű logikai nyelv a term- és formulakifejezések uniója: $L(V_\nu) = L_t(V_\nu) \cup L_f(V_\nu)$.

### Formulaelnevezések

| Alak | Elnevezés |
|---|---|
| $\neg A$ | negációs |
| $A \wedge B$ | konjukciós |
| $A \vee B$ | diszjunkciós |
| $A \supset B$ | implikációs |
| $\forall xA$ | univerzálisan kvantált |
| $\exists xA$ | egzisztenciálisan kvantált |

A $\forall xA$ és $\exists xA$ formulák esetén $A$ a kvantált formula **törzse** (mátrixa).

### Közvetlen részformula

- Egy atomi formulának nincs közvetlen részformulája.
- $\neg A$ közvetlen részformulája $A$.
- $(A \circ B)$ közvetlen részformulái $A$ (baloldali) és $B$ (jobboldali).
- $QxA$ ($Q \in \{\forall, \exists\}$) közvetlen részformulája $A$.

### Prímformula, komponens, prímkomponens

Egy formulában egy logikai művelet hatáskörében lévő részformulá(ka)t **komponens formulának** nevezzük:

- egy atomi formulának nincs közvetlen komponense — **prímformula**;
- $\neg A$ közvetlen komponense $A$;
- $(A \circ B)$ közvetlen komponensei $A$ és $B$;
- $QxA$ formulának nincs közvetlen komponense — szintén **prímformula**.

Eszerint az elsőrendű nyelvben a **prímformulák**: az atomi formulák és a kvantált ($QxA$) formulák — ezek az elsőrendű megfelelői az ítéletlogikai [[concepts/logika/iteletlogikai-formula|ítéletváltozónak]]: minden formula felírható belőlük a $\neg, \wedge, \vee, \supset$ műveletek segítségével. Azokat a prímformulákat, amelyekből egy formula kizárólag ezekkel a műveletekkel épül fel, **prímkomponenseknek** nevezzük.

### A formula szerkezeti fája

Egy $F$ formula **szerkezeti fája** olyan véges fa, amelyre:

- a gyökeréhez $F$ van rendelve,
- ha egy csúcshoz $F'$ formula van rendelve, a csúcs gyerekeihez $F'$ közvetlen részformulái vannak rendelve,
- a levelekhez atomi formulák vannak rendelve.

### Logikai összetettség

A fogalom ítéletlogikai alakját a [[concepts/logika/logikai-osszetettseg]] lap tárgyalja; elsőrendben a definíció egy negyedik esettel, a kvantált formuláéval bővül. Egy $A$ formula **logikai összetettsége**, $\ell(A)$, szerkezeti rekurzióval:

1. ha $A$ atomi formula, $\ell(A) = 0$;
2. $\ell(\neg A) = \ell(A) + 1$;
3. $\ell(A \circ B) = \ell(A) + \ell(B) + 1$;
4. $\ell(QxA) = \ell(A) + 1$.

### Alapatom és alapformula

Egy változót nem tartalmazó $L$-kifejezés **alapkifejezés** (alapformula, alapterm; más néven alappéldány). Az atomi formulák alappéldányait két csoportba soroljuk:

1. **alapatom**, ha argumentumai konstansszimbólumok vagy egy megadott univerzum elemei (pl. $P(c)$);
2. **atomi formula alappéldánya**, ha argumentumai [[concepts/logika/term|alaptermek]] (pl. $Q(f(a,b), a)$).

Egy atomi formulát, amely nem alappéldány, **paraméteres állításnak** is neveznek — lásd [[concepts/logika/nulladrendu-es-elsorendu-allitas]].

## Kapocs

- [[concepts/logika/term]] — az atomi formula argumentumai
- [[concepts/logika/leiro-nyelv-es-szignatura]] — az ábécé, amelyből a formula felépül
- [[concepts/logika/szabad-es-kotott-valtozo]] — a formulában előforduló individuumváltozók szabad/kötött státusza
- [[concepts/logika/nulladrendu-es-elsorendu-allitas]] — az állítások, amelyeknek a formula a formális megfelelője
- [[concepts/logika/iteletlogikai-formula]] — az ítéletlogikai formula, amelynek szerkezeti fogalmait (komponens, prímformula, szerkezeti fa) a formula átveszi
- [[concepts/logika/formulaszerkezet]] — ugyanezek a szerkezeti fogalmak (részformula, szerkezeti fa, szintaxisfa) ítéletlogikai alakban
- [[concepts/logika/logikai-osszetettseg]] — a logikai összetettség önálló tárgyalása
