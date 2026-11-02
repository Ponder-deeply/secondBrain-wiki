---
tags: [concept]
sources: [Elsőrendű_logika_alapjai.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-21
---

# Elsőrendű formalizálás

Természetes nyelvű mondatok átírása elsőrendű formulákká: univerzum, predikátumok, függvények és konstansok választása, majd a mondatok kvantoros formulává fordítása. Az ítéletlogika csak a teljes állítást látja, az elsőrendű nyelv a belső szerkezetet is.

## Tartalom

### Mit ad az elsőrendű nyelv

Egy elsőrendű formula építőelemei: műveleti jelek ($\wedge,\vee,\supset,\neg$), kvantorok ($\forall,\exists$), zárójelek, individuumváltozók. Egy $I$ interpretáció megadja az $U$ univerzumot, a predikátumokat (logikai értékű $U^n \to L$ függvények, pl. $|P(x)|_I$: „$x$ páros”, $|Q(x,y)|_I$: „$x$ osztója $y$-nak”), a függvényeket ($U^n \to U$, pl. $|f(x)|_I$: $x$ rákövetkezője) és a konstansokat ($|\bar a|_I = 2$, $|\bar b|_I = 3$). Lásd [[concepts/logika/elsorendu-interpretacio]].

### Ítéletlogika kontra elsőrendű

„Ha valaki fiatal, akkor kávézik.” / „Minden fiatal kávézik.” / „Van, aki nem kávézik.”

- **Ítéletlogikában**: az első $F \supset K$ lehet, de a második és harmadik *egyetlen* ítéletváltozó ($A$, illetve $B$) — a „minden” és a „van” szerkezete elvész.
- **Elsőrendben** ($F(x)$: $x$ fiatal, $K(x)$: $x$ kávézik): $\forall x(F(x) \supset K(x))$ és $\exists x\,\neg K(x)$.

### A fordítás alapszabályai

- „Minden $P$ olyan, hogy $Q$” $\to$ $\forall x(P(x) \supset Q(x))$ — a $\forall$ mellé implikáció kell.
- „Van olyan $P$, amely $Q$” $\to$ $\exists x(P(x) \wedge Q(x))$ — az $\exists$ mellé konjunkció kell.
- Egyedre mutató név $\to$ konstans ($\bar a$); „valakinek a …-ja” $\to$ függvényjel ($f(x)$).

### Egyfajtájú megközelítés, és ugyanez más univerzummal

Mondatok: (1) Minden bogár rovar, de nem minden rovar bogár. (2) Szarvasnak, a szarvasbogárnak kitines a szárnyfedője. (3) Egy rovarnak nincsen kitines szárnyfedője vagy bogár. (4) Szarvas legjobb barátja bogár.

- **$U$ = rovarok**: $B(x)$ bogár, $K(x)$ kitines szárnyfedelű, $S(x)$ szarvasbogár, $f(x)$ legjobb barátja, $\bar a$ = Szarvas. Mivel mindenki rovar, a „rovar” predikátum felesleges: (1) $\neg\forall x\,B(x)$; (2) $S(\bar a) \wedge K(\bar a)$; (3) $\forall x(\neg K(x) \vee B(x))$; (4) $B(f(\bar a))$.
- **$U$ = élőlények**: kell egy $R(x)$ („$x$ rovar”) predikátum, és a kvantorok mellé relativizálás kerül: (1) $\forall x(B(x) \supset R(x)) \wedge \neg\forall x(R(x) \supset B(x))$; (3) $\forall x(R(x) \supset (\neg K(x) \vee B(x)))$; (2) és (4) változatlan.

Tanulság: nagyobb univerzumban az „univerzum-szűkítő” állítást explicit predikátummal kell kimondani.

### Egyfajtájú és többfajtájú megközelítés

Mondatok: (1) Zokni kerti kutya. (2) Zokni szomszédjában lakó kutya házban lakik. (3) Zokni egy kutya, akinek gazdája Norbi (aki ember). (4) Minden kutyának van gazdája (aki ember). (5) Van olyan kutya, amelyik házban és van amelyik kertben lakik.

- **Egyfajtájú** ($U$ = élőlények; $K$ kutya, $E$ ember, $R$ kertben él, $H$ házban él, $G(x,y)$: $x$ gazdája $y$, $f(x)$ szomszédja, $\bar a$ = Zokni, $\bar b$ = Norbi):
  (1) $K(\bar a) \wedge R(\bar a)$; (2) $K(f(\bar a)) \wedge H(f(\bar a))$; (3) $K(\bar a) \wedge E(\bar b) \wedge G(\bar a,\bar b)$; (4) $\forall x(K(x) \supset \exists y(E(y) \wedge G(x,y)))$; (5) $\exists x(K(x) \wedge H(x)) \wedge \exists x(K(x) \wedge R(x))$.
- **Többfajtájú** ($U = \{\text{emberek}\},\{\text{kutyák}\}$; $K(x{:}\text{kutya})$, $H(x{:}\text{kutya})$, $G(x{:}\text{kutya},y{:}\text{ember})$, $\bar a{:}\text{kutya}$, $\bar b{:}\text{ember}$, $f(x{:}\text{kutya}){:}\text{kutya}$):
  (1) $K(\bar a)$; (2) $H(f(\bar a))$; (3) $G(\bar a,\bar b)$; (4) $\forall x\,\exists y\,G(x,y)$; (5) $\exists x\,H(x) \wedge \exists x\,K(x)$.

A többfajtájú nyelvben a fajták a változók és argumentumhelyek típusai, ezért a „kutya” és „ember” predikátumok és a relativizáló $\supset$/$\wedge$ elhagyhatók. Lásd [[concepts/logika/leiro-nyelv-es-szignatura]].

### További gyakorló példa

Univerzum: emberek; $I(x)$ informatikus, $L(x)$ tud logikusan gondolkozni, $O(x)$ okos, $f(x)$ főnöke.

1. Minden informatikus tud logikusan gondolkozni: $\forall x(I(x) \supset L(x))$
2. Aki tud logikusan gondolkozni, az okos: $\forall x(L(x) \supset O(x))$
3. Van olyan, aki okos és nem informatikus: $\exists x(O(x) \wedge \neg I(x))$
4. Az informatikusok főnöke okos informatikus: $\forall x(I(x) \supset O(f(x)) \wedge I(f(x)))$

### Gráfok

$G_1 = \langle V_1;E_1\rangle$ irányítatlan gráf, $U = \{0,1,2,3,4\}$, $E(x,y)$: $x$ és $y$ között van él, $=(x,y)$: $x$ és $y$ azonos. A formulák jelentése:

1. $\forall x\,\exists y\,E(x,y)$ — minden csúcsból indul él.
2. $\exists x\,\forall y\,E(x,y)$ — van olyan csúcs, amely minden csúccsal (önmagával is) össze van kötve.
3. $\forall x\,\forall y\,[E(x,y) \supset E(y,x) \wedge \neg{=}(x,y)]$ — az élreláció szimmetrikus és hurokmentes (a ⊃ gyengébben köt, mint a ∧).
4. $\forall x\,\exists y\,\exists z\,[E(x,y) \wedge E(x,z) \supset E(y,z)]$ — a szomszédokra vonatkozó állítás; igazságértéke a konkrét gráftól függ.

Fordítás visszafelé gyakorlata: állításból formula, szükség esetén az interpretáció kiegészítésével (pl. egy „szomszédos” predikátum felvétele).

## Kapocs

- [[concepts/logika/nulladrendu-es-elsorendu-allitas]] — mikor elég az ítéletlogika, mikor kell elsőrendű nyelv
- [[concepts/logika/leiro-nyelv-es-szignatura]] — egy- és többfajtájú leíró nyelv
- [[concepts/logika/elsorendu-formula]] — a formula felépítése
- [[concepts/logika/elsorendu-interpretacio]] — univerzum, predikátum- és függvényinterpretáció
- [[concepts/logika/iteletlogikai-formalizalas]] — az ítéletlogikai párja
- [[concepts/logika/szemantikus-tulajdonsagok]] — a formalizált formulák értéktáblája
