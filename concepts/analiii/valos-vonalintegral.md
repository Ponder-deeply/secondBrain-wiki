---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Valós vonalintegrál

Egy vektormező görbe menti integrálja, az $\sum \langle f(\gamma(u_i)); \gamma(t_i) - \gamma(t_{i-1})\rangle$ integrálközelítő összegek határértékeként; fizikailag a mező által a görbe mentén végzett munka.

## Tartalom

### Az integrálközelítő összegek

Legyen $\gamma : [a,b] \to G \subset \mathbb{R}^p$ folytonos görbe, és $f : G \to \mathbb{R}^p$ vektormező, amely megadja, hogy az egyes pontokban mekkora erőt kell kifejtenünk.

A görbét kicsi darabokra osztjuk: vesszük az $[a,b]$ paraméterintervallum egy

$$a = t_0 < t_1 < \dots < t_n = b$$

felosztását, ezeknek felelnek meg a görbe $x_i = \gamma(t_i)$ osztópontjai. Mindegyik $(x_{i-1}, x_i)$ görbedarabon tetszés szerint kiválasztunk egy $y_i = \gamma(u_i)$ pontot, ahol $u_i \in [t_{i-1}, t_i]$. Miközben $x_{i-1}$-ből $x_i$-be mozgunk, a kifejtett erő körülbelül $f(y_i)$, az elmozdulásvektor $x_i - x_{i-1}$, a végzett munka a kettő skalárszorzata. Összeadva:

$$\frac{W}{m} \approx \sum_{i=1}^{n} \bigl\langle f(y_i); x_i - x_{i-1}\bigr\rangle = \sum_{i=1}^{n}\bigl\langle f(\gamma(u_i)); \gamma(t_i) - \gamma(t_{i-1})\bigr\rangle.$$

Ez az **integrálközelítő összeg**. A Riemann-integrál mintájára azt várjuk, hogy a felosztást finomítva ez konvergáljon.

### Definíció

**Definíció (vektormező valós vonalintegrálja).** Legyen $G \subset \mathbb{R}^p$ nyílt, $f : G \to \mathbb{R}^p$ vektormező, $\gamma : [a,b] \to G$ folytonos görbe és $I \in \mathbb{R}$.

Az $f$ vektormező **valós vonalintegrálja** a $\gamma$ görbén $I$, ha minden $\varepsilon > 0$-hoz van olyan $\delta > 0$, hogy az $[a,b]$ bármely $\delta$-nál finomabb $a = t_0 < \dots < t_n = b$ felosztására és bármely $u_i \in [t_{i-1},t_i]$ választásra

$$\left|\sum_{i=1}^{n}\bigl\langle f(\gamma(u_i)); \gamma(t_i) - \gamma(t_{i-1})\bigr\rangle - I\right| < \varepsilon.$$

Jele:

$$I = \int_\gamma f = \int_\gamma \bigl\langle f(x); \mathrm{d}x\bigr\rangle.$$

A *valós* jelző arra utal, hogy később még többféle vonalintegrált vezetünk be.

### Elemi tulajdonságok

**Trivialitás.** Ha $\int_\gamma f$ és $\int_\gamma g$ is létezik, akkor

- bármely $c \in \mathbb{R}$-re $\int_\gamma c\cdot f = c\int_\gamma f$;
- $\int_\gamma (f+g) = \int_\gamma f + \int_\gamma g$;
- ha $\gamma_1$ a $\gamma$ egy **átparaméterezése**, akkor $\int_{\gamma_1} f = \int_\gamma f$ (mert az átparaméterezésben szereplő $\varphi$ egyenletesen folytonos, tehát finom felosztást finomba visz);
- ha $\gamma_1$ a $\gamma$ egy **megfordítása**, akkor $\int_{\gamma_1} f = -\int_\gamma f$.

A vonalintegrál tehát **nem** a görbe képhalmazától, hanem az irányított görbétől függ — ez az előjelváltás a megfordításnál.

**Lemma (additivitás).** Legyen $f$ folytonos vektormező, $a < b < c$, $\gamma : [a,c] \to G$ folytonos, továbbá $\gamma_1 = \gamma|_{[a,b]}$ és $\gamma_2 = \gamma|_{[b,c]}$. Ha $\int_{\gamma_1} f$ és $\int_{\gamma_2} f$ létezik, akkor $\int_\gamma f$ is, és

$$\int_\gamma f = \int_{\gamma_1} f + \int_{\gamma_2} f.$$

(Az $[a,c]$ egy kellően finom felosztásához hozzávesszük a $b$ pontot is.)

**Lemma (triviális becslés).** Ha $\int_\gamma f$ létezik, akkor

$$\left|\int_\gamma f\right| \leqslant \sup_{x\in\gamma}\bigl|f(x)\bigr| \cdot \ell(\gamma).$$

*Bizonyítás.* Legyen $M = \sup_{x\in\gamma}|f(x)|$. Bármely integrálközelítő összegre, a Cauchy–Schwarz-egyenlőtlenséggel és a hossz definíciójával:

$$\left|\sum_{i=1}^{n}\bigl\langle f(\gamma(u_i)); \gamma(t_i)-\gamma(t_{i-1})\bigr\rangle\right| \leqslant M\cdot\sum_{i=1}^{n}\bigl|\gamma(t_i)-\gamma(t_{i-1})\bigr| \leqslant M\cdot\ell(\gamma).$$

Ez a becslés a fejezet legtöbbet használt munkaeszköze, például a Goursat-lemma bizonyításában.

### Létezés és kiszámítás

**Tétel.** Legyen $G \subset \mathbb{R}^p$ nyílt, $f : G \to \mathbb{R}^p$ **folytonos** vektormező és $\gamma : [a,b] \to G$ **szak.$C^1$** görbe. Ekkor az $\int_\gamma f$ vonalintegrál létezik, és

$$\int_\gamma f = \int_{t=a}^{b}\bigl\langle f(\gamma(t)); \dot\gamma(t)\bigr\rangle\,\mathrm{d}t = \int_a^b \bigl\langle f\circ\gamma; \dot\gamma\bigr\rangle.$$

Ez az a formula, amellyel a vonalintegrálokat ténylegesen kiszámoljuk: egy közönséges egyváltozós Riemann-integrálra vezet.

**A bizonyítás vázlata.** Az additivitás miatt elég $C^1$ görbedarabokra igazolni.

- Legyen $I_j = \int_a^b (f_j\circ\gamma)\dot\gamma_j$ és $I = \sum_{j=1}^p I_j$; a folytonosság miatt ezek léteznek.
- Legyen $M = \max|\dot\gamma|$ és $\eta = \frac{\varepsilon}{p(1 + (b-a)M)}$. Az $f\circ\gamma$ egyenletesen folytonos; legyen $\delta_1$ olyan, hogy $|t - t'| < \delta_1$ esetén $\bigl|f(\gamma(t)) - f(\gamma(t'))\bigr| < \eta$.
- Egy $\delta_1$-nél finomabb felosztás mellett minden $i$-re és minden $j$ koordinátára a $\gamma_j$ függvényre alkalmazzuk az egyváltozós **Lagrange-középértéktételt**: van olyan $\tau_{ij} \in (t_{i-1},t_i)$, hogy

$$\gamma_j(t_i) - \gamma_j(t_{i-1}) = \dot\gamma_j(\tau_{ij})\cdot(t_i - t_{i-1}).$$

- Ezt beírva az $S$ integrálközelítő összegbe, és az $u_i$-t is $\tau_{ij}$-re cserélve, $S$ két részre bomlik: az első tag az $I_j$ integrálok egy közelítő összege, a második tagot pedig az $f\circ\gamma$ egyenletes folytonossága és a $|\dot\gamma| \leqslant M$ becslés kicsivé teszi:

$$|S - I| < p\eta + p\sum_{i=1}^{n}\eta M (t_i - t_{i-1}) = p\eta\bigl(1 + M(b-a)\bigr) = \varepsilon.$$

A középértéktétel alkalmazása koordinátánként történik, mert a $\tau_{ij}$ hely a $j$ koordinátától is függ — vektorértékű függvényre a középértéktétel egyenlőségként nem is igaz.

## Kapocs

- [[concepts/analiii/szakaszonkent-c1-gorbe]] — a görbeosztály, amelyen a vonalintegrál létezik, és a $\ell(\gamma)$ hossz, amely a triviális becslésben szerepel.
- [[concepts/analiii/skalarmezo-es-vektormezo]] — az integrálandó objektum és a fizikai motiváció.
- [[concepts/analiii/newton-leibniz-formula-vonalintegralra]] — a vonalintegrál kiszámítása primitív függvénnyel.
- [[concepts/analiii/konzervativ-vektormezo]] — mikor függ a vonalintegrál csak a végpontoktól.
- [[concepts/analii/hatarozott-integral-ertelmezese]] — a Riemann-integrál felosztásokkal és közelítő összegekkel adott definíciója; a vonalintegrál ugyanezt a sémát követi, de az $f(y_i)\Delta x_i$ szorzat helyére az $\langle f(y_i); \Delta x_i\rangle$ **skalárszorzat** lép, és az intervallum helyére egy irányított görbe.
