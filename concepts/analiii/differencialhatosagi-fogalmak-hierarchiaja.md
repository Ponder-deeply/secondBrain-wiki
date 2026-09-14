---
tags: [synthesis]
sources: [SimonP-Anal2.pdf, 04_ea_An3_2022_tavasz.pdf]
references: ["Simon Péter: Analízis II., 3.2. ii), iv), x), xi), xii) megjegyzés"]
derivation: inferred
updated: 2026-09-14
---

# A differenciálhatósági fogalmak hierarchiája

A többváltozós analízis öt regularitási fogalma — $C^1$, differenciálhatóság, folytonosság, iránymenti és parciális deriválhatóság — egyetlen implikációláncba rendeződik, amelyben **minden nyíl egyirányú**, és mindegyik megfordítására van szabványos ellenpélda.

## Tartalom

### A közös váz

Legyen $f \in \mathbb{R}^n \to \mathbb{R}^m$ és $a \in \operatorname{int} D_f$. A tételekből az alábbi implikációk olvashatók ki:

$$f \in C^1\{a\} \ \Longrightarrow\ f \in D\{a\} \ \Longrightarrow\ \begin{cases} f \in C\{a\} \\[2pt] \exists\, \partial_e f(a)\ \text{minden } \|e\| = 1 \text{-re} \ \Longrightarrow\ \exists\, \partial_i f(a)\ \text{minden } i \text{-re}\end{cases}$$

A két ág **független egymástól**: sem a folytonosságból nem következik semmilyen deriválhatóság, sem a deriválhatóságokból a folytonosság. Ez az egyváltozós esethez képest az igazi újdonság — ott a deriválhatóság maga után vonja a folytonosságot, itt csak a *teljes* (Fréchet-értelmű) differenciálhatóság teszi.

### A nyilak, egyenként

| Implikáció | Honnan | Miért igaz |
|---|---|---|
| $C^1\{a\} \Rightarrow D\{a\}$ | definíció szerint (a $C^1$ előírja a környezetbeli differenciálhatóságot) | [[concepts/analiii/folytonosan-differencialhato-fuggveny]] |
| $D\{a\} \Rightarrow C\{a\}$ | $\|f(a+h)-f(a)\| \le \|f'(a)\|\,\|h\| + \|\eta(h)\|\,\|h\| \to 0$ | lásd alább |
| $D\{a\} \Rightarrow \exists \partial_e f(a)$ | $\partial_e f(a) = f'(a)e$ | [[concepts/analiii/iranymenti-derivalt]] |
| $\exists \partial_e f(a) \ \forall e \Rightarrow \exists \partial_i f(a)$ | $\partial_i$ az $e = e_i$ eset | [[concepts/analiii/parcialis-derivalt]] |
| $D\{a\} \Rightarrow \operatorname{grad}$ komponensei a $\partial_i$-k | 3.1.3. Tétel | [[concepts/analiii/gradiens-parcialis-derivaltakbol]] |

**A folytonossági nyíl bizonyítása.** A $\|\cdot\|_2$ normával $f(a+h) - f(a) = f'(a)h + \eta(h)\|h\|$, ahol $\eta(h) \to 0$. Az operátornormával becsülve

$$\|f(a+h) - f(a)\| \le \|f'(a)\|_{(2,2)}\cdot\|h\| + \|\eta(h)\|\cdot\|h\| \to 0 \qquad (\|h\| \to 0),$$

tehát $\lim_a f = f(a)$, azaz $f \in C\{a\}$.

### Az ellenpéldák — a nyilak megfordítása mind hamis

Mind $\mathbb{R}^2 \to \mathbb{R}$, az $a = (0,0)$ pontban. A közös séma: a függvény minden egyenes mentén szelíden viselkedik, de valamelyik **görbe** mentén nem.

| # | Függvény | Mi teljesül | Mi nem | A trükk |
|---|---|---|---|---|
| 1 | $f(x,y) = 1$ ha $x = 0$ vagy $y = 0$, különben $0$ | $\partial_1 f(0,0) = \partial_2 f(0,0) = 0$ | nem folytonos, tehát $\notin D\{a\}$ | a két tengelyen konstans, azon kívül más konstans |
| 2 | $f(x,y) = 1$ ha $y = x^2 \ne 0$, különben $0$ | **minden** $\partial_e f(0,0) = 0$ | nem folytonos, tehát $\notin D\{a\}$ | a parabola minden origón átmenő egyenest csak a $0$-ban metsz |
| 3 | $f(x,y) = \dfrac{xy}{\sqrt{x^2+y^2}}$, $f(0,0) = 0$ | folytonos, $\partial_1 f(0,0) = \partial_2 f(0,0) = 0$ | $\notin D\{a\}$ | az $y = x$ átlón $\eta(x,x) = \frac{1}{2} \not\to 0$ |
| 4 | $f(x,y) = \dfrac{x^3 y}{x^2+y^4}$, $f(0,0) = 0$ | $\in D\{(0,0)\}$, $\operatorname{grad} f(0,0) = (0,0)$ | — (pozitív példa) | a $2\|xy\| \le x^2+y^2$ becslés miatt $|\eta| \le \sqrt{x^2+y^2} \to 0$ |

**Az 1. példa részletei.** $D^{(a)}_{f,i} = \mathbb{R}$ és $f_{a,i} \equiv 1$ ($i = 1,2$), ezért $f_{a,i} \in D\{0\}$ és $\partial_i f(0,0) = 0$. Ugyanakkor $f$ nem folytonos $(0,0)$-ban, tehát nem is differenciálható.

**A 3. és 4. példa szembeállítása.** Mindkettőnél $\partial_1 f(0,0) = \partial_2 f(0,0) = 0$, tehát a [[concepts/analiii/gradiens-parcialis-derivaltakbol|3.1.3. Tétel]] szerint a differenciálhatósághoz $\operatorname{grad} f(0,0) = (0,0)$-t kellene igazolni, azaz $f(h) = \eta(h)\|h\|_2$ alakot $\eta \to 0$-val. A 4. esetben

$$|\eta(x,y)| = \frac{|x^3 y|}{(x^2+y^4)\sqrt{x^2+y^2}} \le \frac{x^2\sqrt{x^2+y^2}}{2(x^2+y^4)} \le \sqrt{x^2+y^2} \to 0,$$

a 3. esetben viszont $\eta(x,y) = \frac{xy}{x^2+y^2}$, és $\eta(x,x) = \frac{1}{2}$ minden $x \ne 0$-ra, tehát nincs nulla határérték. Ugyanaz a levezetés dönt mindkét irányba — csak a becslés sikere vagy kudarca különbözteti meg őket.

<!-- src: 04_ea_An3_2022_tavasz.pdf -->
### Két további ellenpélda

| # | Függvény | Mi teljesül | Mi nem | A trükk |
|---|---|---|---|---|
| 5 | $f(x,y) = \sqrt{\lvert xy\rvert}$ | folytonos $(0,0)$-ban, $\partial_1 f(0,0) = \partial_2 f(0,0) = 0$ | $\notin D\{(0,0)\}$ | az $y=x$ átlón $f(x,x)=\lvert x\rvert$, ami $x=0$-ban nem differenciálható egyváltozóban sem — a hibafüggvény $\eta(x,x)=1\not\to 0$ |
| 6 | $f(x,y) = \dfrac{xy^2}{x^2+y^2}$, $f(0,0)=0$ | folytonos, minden $\partial_e f(0,0)$ létezik | $\notin D\{(0,0)\}$ | ugyanaz a séma, mint a 3. példánál: a becslés az $y=x$ átlón elromlik |

Az 5. példa azért tanulságos, mert itt már a **legegyszerűbb** — a koordinátatengelyeken kívüli — átlós viselkedés bukik el: a $\sqrt{\lvert xy\rvert}$ függvény szimmetrikus, mégsem differenciálható, mert az egyváltozós $t\mapsto\lvert t\rvert$ függvény maga sem az a $0$-ban.

### Amit az ellenpéldák tanítanak

Minden ellenpélda ugyanazt a rést használja ki: a parciális és az iránymenti derivált **egydimenziós** információ, a differenciálhatóság pedig **teljes környezetbeli**. Egy origón átmenő egyeneseken vett tetszőleges viselkedés nem szabja meg, mi történik egy parabola vagy más görbe mentén. Ezért nincs az az egyenesekre támaszkodó feltétel, amely elegendő lenne — és ezért kell a [[concepts/analiii/differencialhatosag-elegseges-feltetele|3.1.5. Tételben]] a parciális deriváltak környezetbeli létezése és folytonossága.

## Kapocs

- [[concepts/analiii/frechet-derivalt]] — a lánc legerősebb (nem $C^1$) tagja.
- [[concepts/analiii/folytonosan-differencialhato-fuggveny]] — a lánc teteje.
- [[concepts/analiii/iranymenti-derivalt]] — a középső, egydimenziós fogalom.
- [[concepts/analiii/parcialis-derivalt]] — a lánc leggyengébb tagja.
- [[concepts/analiii/differencialhatosag-elegseges-feltetele]] — a megfordítás ára.
- [[concepts/analiii/gradiens-parcialis-derivaltakbol]] — az az implikáció, amelyet az ellenpéldák nem fordítanak meg.
