---
tags: [concept]
sources: [DimatIIEa04.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, dm2gy07_Polinomok.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-21
---

# Polinomgyűrű és a polinom alapfogalmai

A polinom formálisan egy gyűrűbeli elemekből álló, véges sok nemnulla tagú sorozat; az így kapott $R[x]$ halmaz az összeadással és a konvolúciós szorzással maga is gyűrű.

## Tartalom

### Definíció

Legyen $(R; +, \cdot)$ gyűrű. A gyűrű elemeiből képzett $f = (f_0, f_1, f_2, \ldots)$ végtelen sorozatot ($f_i \in R$) **$R$ fölötti polinomnak** nevezzük, ha csak véges sok eleme nem nulla. Az $R$ fölötti polinomok halmazát $R[x]$-szel jelöljük.

Két polinom pontosan akkor egyenlő, ha minden tagjuk egyenlő: $f = g \Leftrightarrow \forall j \in \mathbb{N} : f_j = g_j$.

### Műveletek

$f = (f_0, f_1, f_2, \ldots)$, $g = (g_0, g_1, g_2, \ldots)$ és $h = (h_0, h_1, h_2, \ldots)$ esetén

$$f + g = (f_0 + g_0,\ f_1 + g_1,\ f_2 + g_2,\ \ldots),$$

a szorzat $f \cdot g = h$ pedig a konvolúció:

$$h_k = \sum_{i + j = k} f_i g_j = \sum_{i=0}^{k} f_i g_{k-i} = \sum_{j=0}^{k} f_{k-j} g_j.$$

Könnyen látható, hogy polinomok összege és szorzata is polinom (csak véges sok nemnulla tag marad).

### Állítás (polinomgyűrű)

Ha $(R; +, \cdot)$ gyűrű, akkor $(R[x]; +, \cdot)$ is gyűrű; ezt $R$ fölötti **polinomgyűrűnek** nevezzük. Gyakran az $(R; +, \cdot)$ gyűrűre egyszerűen $R$-ként, az $(R[x]; +, \cdot)$-ra $R[x]$-ként hivatkozunk.

**Öröklődő tulajdonságok:**

- Ha $R$ kommutatív, akkor $R[x]$ is kommutatív. Bizonyítás a konvolúció szimmetriájából: $(f \cdot g)_k = f_0 g_k + f_1 g_{k-1} + \ldots + f_k g_0 = g_0 f_k + \ldots + g_k f_0 = (g \cdot f)_k$.
- Ha $1 \in R$ egységelem, akkor $e = (1, 0, 0, \ldots)$ egységeleme $R[x]$-nek, hiszen $(f \cdot e)_k = \sum_{j=0}^{k} f_j e_{k-j} = f_k$.
- Ha $R$ nullosztómentes, akkor $R[x]$ is nullosztómentes. Legyen ugyanis $n$, illetve $m$ a legkisebb olyan index, amire $f_n \ne 0$, illetve $g_m \ne 0$; ekkor $(f \cdot g)_{n+m} = f_n g_m \ne 0$.

### Szokásos alak, fok, együtthatók

Az $f = (f_0, f_1, \ldots, f_n, 0, 0, \ldots)$ polinomot, ahol $f_n \ne 0$ és $f_m = 0$ minden $m > n$-re, az

$$f(x) = f_0 + f_1 x + f_2 x^2 + \ldots + f_n x^n$$

alakba írjuk. Ekkor

- $f_i$ az **$i$-ed fokú tag együtthatója**;
- $f_0$ a polinom **konstans tagja**;
- $f_n$ a **főegyütthatója**;
- a polinom **tagjai** az $f_j x^j$ alakú kifejezések, $f_n x^n$ a **főtagja**;
- $n$ a polinom **foka**, jelölése $\deg(f)$.

**Példa.** Az $f = (1, 0, 2, 0, 0, 3, 0, \ldots)$ polinom felírható $f(x) = 1 + 0x + 2x^2 + 0x^3 + 0x^4 + 3x^5$ alakban; további szokásos alakjai $f(x) = 1 + 2x^2 + 3x^5$ és $f(x) = 3x^5 + 2x^2 + 1$.

### Konstans polinomok és az $x$ változó (Farkas-diák)

Az $a \mapsto f_a = (a, 0, 0, \ldots)$ megfeleltetés injektív és műveletőrző, és $a \cdot f = f_a \cdot f$, ezért $R$ elemei $R$ fölötti **konstans polinomoknak** tekinthetők. A **változó** az $x = (0, e, 0, \ldots)$ polinom (ahol $e$ az egységelem; vigyázat: lehet, hogy $e \notin R$, ha $R$-nek nincs egységeleme). A szorzás definíciójából $x^2 = (0, 0, e, 0, \ldots)$, általában $x^n = (0, \ldots, 0, e, 0, \ldots)$ ($e$ az $n$-edik pozíción), és $x^0 = (e, 0, \ldots)$; így

$$f = (a_0, a_1, \ldots, a_n, \ldots) = (a_0, 0, \ldots) + \ldots + (0, \ldots, a_n, \ldots) = a_0 + a_1 x + \ldots + a_n x^n.$$

A tételt a diák is kimondják: ha $R$ egységelemes / kommutatív / nullosztómentes, akkor $R[x]$ is az.

### Feladattípusok és módszerek: bizonyítandó állítások (gyakorlati feladatsor, 7. hét)

- **$R[x]$ gyűrű tetszőleges $R$ gyűrű fölött:** az összeadás együtthatónkénti, ezért $(R[x],+)$ Abel-csoport; a konvolúciós szorzás asszociativitása és disztributivitása az $R$-beli azonosságokból, az indexek átrendezésével adódik: $((fg)h)_k=\sum_{i+j+l=k}f_ig_jh_l=(f(gh))_k$.
- **Mikor egységelemes integritási tartomány $R[x]$?** Pontosan akkor, ha $R$ az; példa $R=\mathbb{Z}$ (vagy bármely test). Lásd az öröklődő tulajdonságokat fent.
- **Soha nem test $R[x]$:** az $x$ nem invertálható, mert bármely $g$-re az $xg$ konstans tagja $0\ne1$. Test fölött $R[x]$ euklideszi gyűrű, de sosem test.

## Kapocs

- [[concepts/dimatii/gyuru]] — az alapstruktúra, amely fölött a polinomok élnek
- [[concepts/dimatii/nullosztomentes-gyuru]] — a nullosztómentesség öröklődése $R[x]$-re
- [[concepts/dimatii/integritasi-tartomany]] — integritási tartomány fölött $R[x]$ is az
- [[concepts/dimatii/test]] — test fölötti polinomgyűrű a polinomelmélet szokásos színtere
