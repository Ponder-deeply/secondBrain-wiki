---
tags: [concept, logika/gentzen-stilusu-kalkulusok]
sources: [Szekventkalkulus.pdf]
derivation: source
updated: 2026-09-08
---

# Szekventkalkulus

A **szekventkalkulus** a [[concepts/logika/szekvent]] fogalmára épülő, Gentzen-stílusú bizonyításelméleti rendszer: axiómaszekventekből indulva, logikai összekötőjelenként két-két levezetési szabállyal épít fel bizonyítható szekventeket. Két, egymással ekvivalens szabályrendszere van: a **G-kalkulus** (Gentzen-féle) és a **C-kalkulus** (Curry-féle).

## Tartalom

### A szabályrendszer felépítése

Mindkét kalkulusnak van egy **axiómasémája**, és minden logikai összekötőjelhez (¬, ∧, ∨, ⊃) **két** levezetési szabály tartozik, aszerint, hogy az adott művelet a vonal alatti szekvent $\to$ jelének melyik oldalán szereplő formulában áll:

- $(\to \circ)$ — a $\circ$ művelet a szukcedensben (a $\to$ jobb oldalán) keletkezik,
- $(\circ \to)$ — a $\circ$ művelet az antecedensben (a $\to$ bal oldalán) keletkezik.

Egy levezetési szabály két szekventből áll: egy (vagy két) *vonal feletti* szekventből (premissza) és egy *vonal alatti* szekventből (konklúzió). A $\to$ jel itt a [[concepts/logika/szekvent]] lapon bevezetett szekvent-elválasztó jel, **nem** azonos a $\supset$ implikációjellel, amelyet ez a rendszer (az [[concepts/logika/iteletlogikai-formula]] jelölésével összhangban) az ítéletlogikai nyelv implikáció-műveleteként használ.

### A G-kalkulus szabályai

Axiómaséma: $X \to X$.

Levezetési szabályok (a $\Gamma \to \Delta$ *oldalszekvent* mindkét szabályban jelen van, "kísérőként"):

**Kettőzés (szennyezés) / összevonás:**

$$
(\to sz):\ \dfrac{\Gamma \to \Delta, X, X}{\Gamma \to \Delta, X} \qquad
(sz \to):\ \dfrac{X, X, \Gamma \to \Delta}{X, \Gamma \to \Delta}
$$

**Gyengítés (bővítés):**

$$
(\to b):\ \dfrac{\Gamma \to \Delta}{\Gamma \to \Delta, X} \qquad
(b \to):\ \dfrac{\Gamma \to \Delta}{X, \Gamma \to \Delta}
$$

Ezek mellett minden $\circ \in \{\neg, \wedge, \vee, \supset\}$ összekötőjelhez tartozik egy $(\to \circ)$ és egy $(\circ \to)$ szabály, amely a $\circ$ művelettel képzett formulát a szukcedensben, illetve az antecedensben "bontja fel" a résztformuláira (a forrás e szabályok táblázatát képként tartalmazza — a C-kalkulus alábbi szabályai ugyanezt a mintát mutatják).

### A G-kalkulus kvantoros levezetési szabályai

$$
(\forall \to):\ \dfrac{[A(x \| t)], \Gamma \to \Delta}{\forall x A, \Gamma \to \Delta} \qquad
(\to \forall):\ \dfrac{\Gamma \to \Delta, A}{\Gamma \to \Delta, \forall x A} \ \ (x \notin \mathrm{Par}(\Gamma, \Delta))
$$

$$
(\exists \to):\ \dfrac{A, \Gamma \to \Delta}{\exists x A, \Gamma \to \Delta} \ \ (x \notin \mathrm{Par}(\Gamma, \Delta)) \qquad
(\to \exists):\ \dfrac{\Gamma \to \Delta, [A(x \| t)]}{\Gamma \to \Delta, \exists x A}
$$

Itt $A(x \| t)$ az $A$ formulában $x$ egy $t$ termmel való helyettesítését jelöli, $\mathrm{Par}(\Gamma, \Delta)$ pedig a $\Gamma, \Delta$-ban szabadon előforduló paraméterek (változók) halmaza — az $x \notin \mathrm{Par}(\Gamma, \Delta)$ **sajátváltozó-feltétel** biztosítja, hogy az univerzális, illetve egzisztenciális általánosítás ne "szennyezze" a már jelen lévő formulákat.

### A C-kalkulus szabályai

Axiómaséma — a G-kalkulustól eltérően a kísérő $\Gamma, \Delta$ már az axiómában is jelen van:

$$X, \Gamma \to \Delta, X$$

Levezetési szabályok:

$$
(\to \supset):\ \dfrac{X, \Gamma \to \Delta, Y}{\Gamma \to \Delta, (X \supset Y)} \qquad
(\supset \to):\ \dfrac{\Gamma \to \Delta, X \qquad Y, \Gamma \to \Delta}{(X \supset Y), \Gamma \to \Delta}
$$

$$
(\to \wedge):\ \dfrac{\Gamma \to \Delta, X \qquad \Gamma \to \Delta, Y}{\Gamma \to \Delta, (X \wedge Y)} \qquad
(\wedge \to):\ \dfrac{X, Y, \Gamma \to \Delta}{(X \wedge Y), \Gamma \to \Delta}
$$

$$
(\to \vee):\ \dfrac{\Gamma \to \Delta, X, Y}{\Gamma \to \Delta, (X \vee Y)} \qquad
(\vee \to):\ \dfrac{X, \Gamma \to \Delta \qquad Y, \Gamma \to \Delta}{(X \vee Y), \Gamma \to \Delta}
$$

$$
(\to \neg):\ \dfrac{X, \Gamma \to \Delta}{\Gamma \to \Delta, \neg X} \qquad
(\neg \to):\ \dfrac{\Gamma \to \Delta, X}{\neg X, \Gamma \to \Delta}
$$

A C-kalkulus kvantoros szabályai a G-kalkuluséihoz hasonlóak, azzal a különbséggel, hogy a kvantált formula ($\forall x A$, illetve $\exists x A$) a premisszában is megmarad (kísérőként), a G-kalkulusban viszont nem:

$$
(\forall \to):\ \dfrac{[A(x \| t)], \forall x A, \Gamma \to \Delta}{\forall x A, \Gamma \to \Delta} \qquad
(\to \forall):\ \dfrac{\Gamma \to \Delta, A}{\Gamma \to \Delta, \forall x A} \ \ (x \notin \mathrm{Par}(\Gamma, \Delta))
$$

$$
(\exists \to):\ \dfrac{A, \Gamma \to \Delta}{\exists x A, \Gamma \to \Delta} \ \ (x \notin \mathrm{Par}(\Gamma, \Delta)) \qquad
(\to \exists):\ \dfrac{\Gamma \to \Delta, [A(x \| t)], \exists x A}{\Gamma \to \Delta, \exists x A}
$$

A C-kalkulus szabályainak megkülönböztető tulajdonsága, hogy **megfordíthatók** — lásd alább.

### Elérhető szabály

Jelölje $K_1$ a G- és C-kalkulusok egyikét, $K_2$ a másikat. Egy $K_1$-kalkulusbeli, $S_1$ premisszájú és $S_2$ konklúziójú levezetési szabály **elérhető** $K_2$-ből, ha minden esetben, amikor $\vdash_{K_2} S_1$, akkor $\vdash_{K_2} S_2$ is fennáll. (Két premisszájú szabálynál analóg módon: ha $\vdash_{K_2} S_1$ és $\vdash_{K_2} S_2$, akkor $\vdash_{K_2} S_3$.) Vagyis egy szabály elérhetősége azt fejezi ki, hogy a másik kalkulusban a szabály *hatása* — bár esetleg nem szó szerint ugyanazzal a lépéssel — reprodukálható.

### G és C ekvivalenciája

**Tétel:** ha egy szekvent bizonyítható a C-kalkulusban, akkor bizonyítható a G-kalkulusban is; és fordítva, ha bizonyítható a G-kalkulusban, akkor bizonyítható a C-kalkulusban is. A bizonyítás a [[concepts/logika/szekvent-levezetesfa]] lapon definiált levezetésfa magassága szerinti indukcióval megy, az alábbi segédlemmákra támaszkodva:

- a C-kalkulus axiómái bizonyíthatók a G-kalkulusban: tetszőleges $A$ formula és $\Gamma, \Delta$ formulasorozat esetén $\vdash_G A, \Gamma \to \Delta, A$;
- a C-kalkulus minden levezetési szabálya elérhető a G-kalkulusból;
- a G-kalkulus axiómái bizonyíthatók a C-kalkulusban: tetszőleges $A$ formulára $\vdash_C A \to A$;
- a G-kalkulus minden levezetési szabálya elérhető a C-kalkulusból.

### Helyesség

Mivel minden levezetési szabály szekventjeire $B_I(\Gamma \to \Delta)$ fennállása öröklődik a premisszáktól a konklúzióig, a kalkulus **helyes**: ha egy szekvent bizonyítható a C-kalkulusban, akkor a megfelelő $A_1 \wedge A_2 \wedge \dots \wedge A_n \supset B_1 \vee B_2 \vee \dots \vee B_k$ formulának van bizonyítása az ítéletkalkulusban is. A bizonyítás a C-kalkulusbeli levezetésfa magassága szerinti indukcióval megy: minden indukciós lépésben az adott alakú formula ítéletkalkulusbeli bizonyíthatóságát természetes technikával igazoljuk.

### Teljesség

**Tétel:** ha $\vdash_0 B$ (azaz $B$ bizonyítható az ítéletkalkulusban), akkor $\vdash_C \to B$. Bizonyítás: legyen $D_1, D_2, \dots, D_m = B$ az ítéletkalkulusbeli levezetés; indukcióval megmutatjuk, hogy minden $D_k$-ra $\vdash_C \to D_k$. Ha $D_k$-t modus ponensszel kaptuk, ezt a lenti segédlemma biztosítja. Szükséges segédlemmák:

- ha $A$ az ítéletkalkulus axiómája, akkor $\vdash_C \to A$;
- az ítéletkalkulus modus ponens szabálya elérhető a C-kalkulusból: ha $\vdash_C \to A$ és $\vdash_C \to A \supset B$, akkor $\vdash_C \to B$.

A helyesség és teljesség együtt azt adja, hogy a szekventkalkulusbeli bizonyíthatóság és az ítéletkalkulusbeli (axiómasémás, [[concepts/logika/bizonyitaselmeleti-levezetes]] szerinti) bizonyíthatóság egybeesik — lásd [[concepts/logika/bizonyitaselmelet-helyesseg-teljesseg]] az elvi hátteret.

### Megfordíthatóság

Egy $S_1 / S_2$ alakú levezetési szabály **megfordítható**, ha minden esetben, amikor $S_2$ bizonyítható, $S_1$ is bizonyítható (két premisszájú szabálynál: ha $S_3$ bizonyítható, akkor $S_1$ és $S_2$ is azok). **Lemma:** a C-kalkulus levezetési szabályai megfordíthatók. Ez a G-kalkulustól megkülönböztető tulajdonsága a C-kalkulusnak: a C-kalkulusban egy konklúzió bizonyíthatóságából visszafelé következtethetünk a premisszák bizonyíthatóságára, ami rendszeres (döntéseljárás-szerű) visszafelé építkező bizonyításkeresést tesz lehetővé.

## Kapocs

- [[concepts/logika/szekvent]] — a szekvent fogalma, szintaxisa és szemantikája, amelyre a kalkulus épül
- [[concepts/logika/szekvent-levezetesfa]] — a levezetésfa és a szekvent bizonyíthatóságának pontos fogalma ebben a kalkulusban
- [[concepts/logika/bizonyitaselmeleti-levezetes]] — az ítéletkalkulus axiómasémás levezetésfogalma, amelynek a szekventkalkulus ekvivalens párja
- [[concepts/logika/bizonyitaselmelet-helyesseg-teljesseg]] — a helyesség és teljesség általános (szintaktikus–szemantikus) fogalma, amelynek itt a szekventkalkulusra vonatkozó speciális esetét látjuk
- [[concepts/bvszam/itelet-kalkulus]] — az ítéletkalkulus rokon, axiómasémás bizonyításelméleti tárgyalása
- [[concepts/bvszam/elsorendu-logika]] — az elsőrendű logika, amelyre a kvantoros szabályok vonatkoznak
</content>
