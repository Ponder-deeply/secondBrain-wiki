---
tags: [concept, logika/iteletlogika-szemantika]
sources: [iteletlogika.pdf]
references: [Pásztorné Varga Katalin – Várterész Magda, A matematikai logika alkalmazásszemléletű tárgyalása]
derivation: source
updated: 2026-09-08
---

# Ítéletlogikai interpretáció és helyettesítési érték

Az ítéletlogika szemantikája: az ítéletváltozók igazságértékének rögzítése (interpretáció), majd ebből a formulák helyettesítési értékének szerkezeti rekurzióval történő kiszámítása.

## Tartalom

### Interpretáció

Az [[concepts/logika/iteletlogika-abece]] ábécéjében egyedül az ítéletváltozókat kell interpretálni: az ítéletváltozók befutják az egyszerű állítások halmazát, és annak rögzítése, hogy melyik ítéletváltozó igaz és melyik hamis, maga az interpretáció.

**Interpretáció (igazságkiértékelés):** egy $I : V_v \to \{i, h\}$ függvény. $I(x)$ jelöli az $x$ ítéletváltozó értékét az $I$ interpretációban.

$n$ darab ítéletváltozó esetén az interpretációk száma $2^n$, mivel minden változóhoz függetlenül választható $i$ vagy $h$.

A változók egy rögzített sorrendjét **bázisnak** nevezzük. Adott bázis mellett az interpretációk megadhatók:

- **felsorolással** (táblázatosan) — minden sor egy interpretáció,
- **szemantikus fával** — egy $n$-változós bázishoz tartozó $n$-szintű bináris fa, ahol az $X$ változó szintjén a csúcsokból kiinduló élpárokat $X$ (jelentése: $X$ igaz) és $\neg X$ (jelentése: $X$ hamis) címkékkel látjuk el. Az $n$-szintű fa ágai az összes ($2^n$) lehetséges interpretációt megjelenítik.

### Az "eset" fogalma

A [[concepts/logika/kovetkeztetesforma]] definíciójában szereplő "eset" pontos ítéletlogikai megfelelője az interpretáció: amikor egy következtetésforma helyességét úgy definiáljuk, hogy "van olyan eset, hogy a premisszák mind igazak", ez pontosan azt jelenti, hogy létezik olyan $I$ interpretáció, amelyben a premisszák helyettesítési értéke $i$.

### Formula helyettesítési értéke

Egy $C$ formula helyettesítési értéke az $I$ interpretációban: $B_I(C)$. A definíció szerkezeti rekurzióval:

1. Ha $C$ ítéletváltozó, akkor $B_I(C) = I(C)$.
2. Ha $C$ negációs formula ($\neg A$ alakú), akkor $B_I(\neg A) = \neg B_I(A)$.
3. Ha $C$ $(A \circ B)$ alakú, akkor $B_I(A \circ B) = B_I(A) \circ B_I(B)$.

**Példa.** Az $(X \vee \neg Y)$ formula helyettesítési értéke az $I(X) = i$, $I(Y) = h$ interpretációban:
$$B_I(X \vee \neg Y) = B_I(X) \vee B_I(\neg Y) = B_I(X) \vee \neg B_I(Y) = I(X) \vee \neg I(Y) = i \vee \neg h = i \vee i = i$$

### Igazhalmaz és hamishalmaz

Egy formula **igazhalmaza** azon interpretációk halmaza, amelyekre a formula helyettesítési értéke $i$; **hamishalmaza** azon interpretációké, amelyekre $h$. Egy $n$-változós formula igazhalmazával és hamishalmazával pontosan az [[concepts/logika/igazsagtabla]] felírásához szükséges információt adjuk meg — a kettő diszjunkt, és együtt lefedi mind a $2^n$ interpretációt.

## Kapocs

- [[concepts/logika/iteletlogika-abece]] — a $V_0$ ábécé, amelynek egyedüli interpretálandó jelei az ítéletváltozók
- [[concepts/logika/iteletlogikai-formula]] — az $L_0$ szintaxis, amelyen a szerkezeti rekurzió fut
- [[concepts/logika/igazsagtabla]] — a helyettesítési értékek táblázatos megadása
- [[concepts/logika/kovetkeztetesforma]] — az "eset" fogalmának forrása
- [[concepts/logika/szemantikus-kovetkezmeny]] — kielégíthetőség és tautológia interpretációk alapján
