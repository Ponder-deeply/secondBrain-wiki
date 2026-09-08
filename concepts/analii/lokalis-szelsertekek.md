---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 2. előadás", "An II A/B 3. előadás"]
derivation: source
updated: 2026-09-04
---

# Lokális szélsőértékek

Lokális szélsőérték keresésének szisztematikus módszere: a stacionárius pontok közül az előjelváltás fogalmával és elégséges feltételekkel szűrjük ki a valódi szélsőérték-helyeket.

## Emlékeztető: Fermat-féle szükséges feltétel

Ha $f \in D\{a\}$ és $a$-ban az $f$ függvénynek lokális szélsőértéke van, akkor $f'(a) = 0$.

A feltétel csak szükséges, nem elégséges: pl. $f(x) := x^3$ esetén $f'(0) = 0$, de $a = 0$ nem szélsőérték-hely.

## Előjelváltás fogalma

**Definíció.** Azt mondjuk, hogy a $h$ függvény a $c \in \operatorname{int} \mathcal{D}_h$ pontban **negatívból pozitívba megy át** (röviden: $h$-nak $c$-ben $(-, +)$ **előjelváltása van**), ha $h(c) = 0$ és $\exists\,\delta > 0$ úgy, hogy

$$h(x) < 0, \quad ha\ x \in (c-\delta,\, c) \qquad \text{és} \qquad h(x) > 0, \quad ha\ x \in (c,\, c+\delta).$$

A $h$ függvény $c$-beli $(+, -)$ előjelváltását hasonlóan értelmezzük. Azt mondjuk, hogy a $h$ **függvény $c$-ben előjelet vált**, ha $h$-nak $c$-ben $(-, +)$ vagy $(+, -)$ előjelváltása van.

## Elsőrendű elégséges feltétel

**Tétel.** Legyen $-\infty < a < b < +\infty$ és $f : (a, b) \to \mathbb{R}$. Tegyük fel, hogy

- $f \in D(a, b)$,
- egy $c \in (a, b)$ pontban $f'(c) = 0$, és
- az $f'$ deriváltfüggvény előjelet vált $c$-ben.

Ekkor,

1. ha az $f'$ függvénynek $c$-ben $(-, +)$ előjelváltása van, akkor $c$ az $f$ függvénynek **szigorú lokális minimumhelye**;
2. ha az $f'$ függvénynek $c$-ben $(+, -)$ előjelváltása van, akkor $c$ az $f$ függvénynek **szigorú lokális maximumhelye**.

**Bizonyítás.** Az állítás azonnal következik a [[concepts/analii/monotonitas|monotonitas]] és a derivált kapcsolatáról szóló tételből: ha az $f'$ függvénynek $c$-ben $(-, +)$ előjelváltása van, akkor $\exists\,\delta > 0$ úgy, hogy $f' < 0$ $(c-\delta, c)$-n és $f' > 0$ $(c, c+\delta)$-n. Ezért $f \downarrow (c-\delta, c]$-n és $f \uparrow [c, c+\delta)$-n, tehát $\forall x \in (c-\delta, c+\delta) : f(x) > f(c)$, vagyis $c$ az $f$ függvénynek szigorú lokális minimumhelye. $\blacksquare$

**Megjegyzés.** A deriváltfüggvény előjelváltása elégséges, de **nem szükséges** feltétele a lokális szélsőértéknek. Például az

$$f(x) := \begin{cases} x^2 + \tfrac{1}{2}x^2 \sin\tfrac{1}{x}, & ha\ x \in \mathbb{R} \setminus \{0\} \\ 0, & ha\ x = 0 \end{cases}$$

függvény deriválható $\mathbb{R}$-en, $c = 0$-ban abszolút (így lokális) minimuma van, de az $f'$ deriváltfüggvény nem vált előjelet $c$-ben.

## Másodrendű elégséges feltétel

**Tétel.** Legyen $-\infty < a < b < +\infty$ és $f : (a, b) \to \mathbb{R}$. Tegyük fel, hogy $f$ kétszer deriválható egy $c \in (a, b)$ pontban ($f \in D^2\{c\}$), $f'(c) = 0$, és $f''(c) \neq 0$.

Ekkor $c$ szigorú lokális szélsőértékhelye az $f$ függvénynek:

1. ha $f''(c) > 0$, akkor $c$ az $f$ függvénynek **szigorú lokális minimumhelye**;
2. ha $f''(c) < 0$, akkor $c$ az $f$ függvénynek **szigorú lokális maximumhelye**.

**Bizonyítás** ($f''(c) > 0$ esetén). Mivel

$$0 < f''(c) = \lim_{x \to c} \frac{f'(x) - f'(c)}{x - c} = \lim_{x \to c} \frac{f'(x)}{x - c},$$

a $c$ pontnak van olyan bal oldali környezete, ahol $f' < 0$, és olyan jobb oldali környezete, ahol $f' > 0$. Tehát $f'$-nek $c$-ben $(-, +)$ előjelváltása van, ami az elsőrendű elégséges feltétel alapján azt jelenti, hogy $c$ az $f$ függvénynek szigorú lokális minimumhelye. $\blacksquare$

**Megjegyzések.**

1. A feltétel **nem szükséges**: pl. $f(x) := x^4$ esetén $c := 0$ pontban $f''(0) = 0$, mégis abszolút (lokális) minimum van.
2. Ha $f'(c) = 0$ és $f''(c) = 0$, akkor semmi nem következtethető: $f(x) := x^3$, $f(x) := x^4$, $f(x) := -x^4$ mind $c = 0$ helyen mutatják a különböző lehetőségeket.

## Magasabb rendű elégséges feltétel

**Tétel.**

1. T.f.h. $1 \leq k \in \mathbb{N}$ és $f \in D^{2k}\{a\}$. Ha
$$f'(a) = f''(a) = \cdots = f^{(2k-1)}(a) = 0 \quad \text{és} \quad f^{(2k)}(a) > 0,$$
akkor $f$-nek $a$-ban szigorú **lokális minimuma** van. Ha $f^{(2k)}(a) < 0$, akkor szigorú **lokális maximuma** van.

2. T.f.h. $1 \leq k \in \mathbb{N}$ és $f \in D^{2k+1}\{a\}$. Ha
$$f'(a) = f''(a) = \cdots = f^{(2k)}(a) = 0 \quad \text{és} \quad f^{(2k+1)}(a) \neq 0,$$
akkor $f$ szigorúan monoton $a$-nak egy környezetében, tehát $a$-ban nincs lokális szélsőértéke.

**Megjegyzés.** Előfordulhat, hogy ezeket az elégséges feltételeket sem tudjuk alkalmazni: pl. az $f(x) := e^{-1/x^2}$ ($x \neq 0$), $f(0) := 0$ függvénynek $a = 0$ nyilvánvalóan szigorú abszolút minimumhelye, de $f \in D^\infty$ és $f^{(n)}(0) = 0$ minden $n \in \mathbb{N}$-re (lásd [[concepts/analii/taylor-sor-eloallitas|taylor-sor-eloallitas]]).

## Példa: monotonitási intervallumok és szélsőértékek meghatározása

Határozzuk meg az

$$f(x) = \frac{x+1}{x^2} \quad (x \in \mathbb{R} \setminus \{0\})$$

függvény monotonitási intervallumait és lokális szélsőértékeit.

**Megoldás.** A deriválási szabályok alapján $f \in D$ és

$$f'(x) = \frac{1 \cdot x^2 - (x+1) \cdot 2x}{x^4} = -\frac{x+2}{x^3} \quad (x \in \mathbb{R} \setminus \{0\}).$$

$f'(x) = 0 \Rightarrow x = -2$, és $f'(x) \gtrless 0 \Leftrightarrow -\frac{x+2}{x^3} \gtrless 0$. Az előjelanalízis három intervallumot ad:

| $x < -2$ | $x = -2$ | $-2 < x < 0$ | $x > 0$ |
|:---------:|:--------:|:-------------:|:--------:|
| $f'$: $-$ | $0$      | $+$           | $-$      |
| $f$:  $\downarrow$ | $-1/4$ | $\uparrow$ | $\downarrow$ |
| lok.: | **min** | | |

$f$-nek lokális minimumhelye van $x = -2$ pontban, és $f(-2) = -1/4$.

## Kapocs

- [[concepts/analii/monotonitas]] — monotonitás és derivált előjelének kapcsolata; alapja az elsőrendű feltétel bizonyításának
- [[concepts/analii/kozeptertekek]] — Lagrange-tétel; a monotonitás és derivált tételének alapja
- [[concepts/analii/magasabb-rendu-derivaltak]] — magasabb rendű deriváltak; magasabb rendű szélsőérték-feltételek
- [[concepts/analii/konvex-konkav-fuggvenyek]] — konvexitás és az inflexiós pont kapcsolata a szélsőérték-vizsgálattal
- [[concepts/analii/teljes-fuggvenyvizsgalat]] — szélsőértékek helye a szisztematikus függvényvizsgálatban
