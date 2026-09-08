---
tags: [concept]
sources: [Rezolúció_II.pdf]
references: [Tk. 6.3.60, Tk. 6.3.61, Tk. 263. o., Tk. 264. o., Tk. 265. o.]
derivation: source
updated: 2026-09-08
---

# Herbrand tételek

A Herbrand tételek a [[concepts/logika/herbrand-univerzum|Herbrand univerzum]] és a Herbrand interpretáció tulajdonságait mondják ki: egy elsőrendű klózhalmaz kielégíthetetlensége visszavezethető a Herbrand interpretációk, illetve alapklózainak véges részhalmazai szintjére, ami a Davis–Putnam eljáráson és az alaprezolúción keresztül algoritmikus eldöntést tesz lehetővé.

## Tartalom

### Tételek a Herbrand interpretációhoz kapcsolódóan

**Tétel (Tk. 6.3.60):** ha egy $I$ interpretáció kielégít egy elsőrendű klózhalmazt, akkor az $I$-nek megfelelő $I_H$ [[concepts/logika/herbrand-univerzum|Herbrand interpretáció]] is kielégíti. Következmény: ha $S$-nek van modellje, akkor van Herbrand modellje is.

**Tétel (Tk. 6.3.61):** egy elsőrendű klózhalmaz akkor és csak akkor kielégíthetetlen, ha a Herbrand univerzuma feletti egyetlen Herbrand interpretáció sem elégíti ki — nincs Herbrand modellje.

A 6.3.61 tétel **csak elsőrendű klózhalmaz esetén** áll fenn. Ellenpélda nem elsőrendű klózhalmazra: legyen $S = \{P(a),\ \exists x \lnot P(x)\}$. Ekkor $S$ Herbrand univerzuma $\{a\}$, Herbrand bázisa $\{P(a)\}$, a lehetséges Herbrand interpretációk $P(a)$ és $\lnot P(a)$ — egyikük sem elégíti ki $S$-et. Ugyanakkor $S$ kielégíthető például az $U = \{0,1\}$ struktúrában, ahol $P(0) = i$ és $P(1) = h$. A tétel tehát kihasználja, hogy egy elsőrendű klóz zárt, univerzálisan kvantált Skolem formula — nyitott vagy egzisztenciális formulára nem érvényes.

### H1 (Tk. 263. o.)

Egy $S$ elsőrendű klózhalmaz kielégíthetetlen akkor és csak akkor, ha $S$ bármely [[concepts/logika/elsorendu-szemantikus-fa|szemantikus fájához]] van véges zárt szemantikus fája.

### H2 (Tk. 264. o.)

Egy $S$ elsőrendű klózhalmaz kielégíthetetlen akkor és csak akkor, ha $S$ klózai alappéldányainak van véges kielégíthetetlen $S'$ részhalmaza.

### Davis–Putnam eljárás (az alaprezolúció előzménye, Tk. 265. o.)

A Davis–Putnam eljárás egy alapklózhalmazon dolgozik: kielégíthető kezdeti halmaz esetén üres halmazt kapunk, egyébként az üres klóz ($\square$) megjelenik a halmazban.

1. **Tautológia szabály:** egy alapklóz *tautológia*, ha tartalmaz komplemens literálpárt. Minden tautológiát törölni kell $S$-ből. Ha a megmaradó $S'$ üres, megállunk; egyébként $S'$-vel folytatjuk.
2. **Egy-literál szabály:** ha $S$-ben van egy $L$ egységalapklóz, akkor $S'$-t úgy kapjuk, hogy elhagyjuk az $L$-et tartalmazó alapklózokat. Ha $S'$ üres, megállunk; egyébként $S''$-t úgy kapjuk $S'$-ből, hogy töröljük $\lnot L$-et minden $S'$-beli alapklózból. Ha $S$-ben volt $\lnot L$ egységklóz is, ennek törlése után az üres klóz ($\square$) keletkezik, és szintén megállunk. Egyébként $S''$-vel folytatjuk.
3. **Tiszta-literál szabály:** egy $S$-beli alapklózban lévő $L$ literál *tiszta* $S$-ben, ha $\lnot L$ nem fordul elő $S$ egyetlen klózában sem. Ha $L$ tiszta, $S'$-t úgy kapjuk, hogy elhagyunk minden $L$-et tartalmazó alapklózt; a nem üres $S'$-vel folytatjuk.
4. **Szétvágási szabály:** ha $S$ klózai $\{(A_1 \vee L), \dots, (A_m \vee L)\}$, $\{(B_1 \vee \lnot L), \dots, (B_n \vee \lnot L)\}$ és $R = \{R_1,\dots,R_s\}$ csoportokra bonthatók, ahol az $A_i, B_i, R_i$ alapklózok sem $L$-et, sem $\lnot L$-et nem tartalmazzák, legyen $S_1 = \{A_1,\dots,A_m\} \cup R$ és $S_2 = \{B_1,\dots,B_n\} \cup R$. $S_1$-gyel és $S_2$-vel dolgozunk tovább: $S$ kielégíthetetlen, ha mindkettő az.

### Alaprezolúció — példa

Az elsőrendű klózok magjainak összes alappéldányát előállítva, az alapklózok halmazán ítéletlogikai (alap)rezolúcióval levezethető az üres klóz. Legyen az elsőrendű klózhalmaz

$$\{\forall x \forall y (P(x) \vee \lnot Q(x, f(y))),\ \forall z \forall v (\lnot P(g(z)) \vee \lnot P(v)),\ \forall u\, Q(g(u), u)\}$$

Herbrand univerzuma $\{a, g(a), f(a), g(f(a)), g(g(a)), f(f(a)), f(g(a)), \dots\}$ — a klózhalmaz leíró nyelvének összes alaptermje. A $u \| f(a)$, $x \| g(f(a))$, $y \| a$, $z \| f(a)$, $v \| g(f(a))$ helyettesítésekkel kapott alapklózokon a levezetés:

1. $Q(g(f(a)), f(a))$
2. $P(g(f(a))) \vee \lnot Q(g(f(a)), f(a))$
3. $P(g(f(a)))$ — 1. és 2. rezolvense
4. $\lnot P(g(f(a)))$
5. $\square$ — 3. és 4. rezolvense

Az eljárás lényege: a Herbrand bázis és a hozzá tartozó [[concepts/logika/iteletlogikai-szemantikus-fa|szemantikus fa]] segítségével a kielégíthetetlenség véges sok alapklóz ítéletlogikai rezolúciójával igazolható — ez az alaprezolúció, és ez alapozza meg az [[concepts/logika/elsorendu-rezolucio|elsőrendű rezolúciós kalkulus]] teljességi bizonyítását.

## Kapocs

- [[concepts/logika/herbrand-univerzum]] — a Herbrand univerzum és interpretáció fogalma, amire a tételek épülnek
- [[concepts/logika/elsorendu-szemantikus-fa]] — a H1 tételben szereplő szemantikus fa fogalma
- [[concepts/logika/elsorendu-kloz]] — az alappéldányok és alapklózok forrása
- [[concepts/logika/elsorendu-rezolucio]] — az alaprezolúció elsőrendű általánosítása, amelynek teljessége a H1 tételen alapul
- [[concepts/logika/rezolucios-kalkulus]] — az ítéletlogikai rezolúció, amit az alaprezolúció alapklózokra alkalmaz
