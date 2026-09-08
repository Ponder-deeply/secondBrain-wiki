---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 2. fejezet, 2.1. és 2.3. Tétel"]
derivation: source
updated: 2026-09-07
---

# Folytonosság metrikus terek között

Az egyváltozós $\varepsilon$–$\delta$ folytonosságból csak a távolságfogalom lényeges, ezért a definíció szó szerint átvihető tetszőleges metrikus terek közötti leképezésekre. A globális folytonosság ekvivalens azzal, hogy minden nyílt halmaz ősképe (relatív) nyílt.

## Tartalom

### Definíció

Legyenek $(X,\rho)$ és $(Y,\sigma)$ metrikus terek, $f \in X \to Y$. Az $f$ **folytonos az $a \in D_f$ pontban** — jelben $f \in C\{a\}$ —, ha minden $\varepsilon > 0$ számhoz van olyan $\delta > 0$, hogy

$$\sigma\bigl(f(x), f(a)\bigr) < \varepsilon \qquad (x \in D_f,\ \rho(x,a) < \delta).$$

Ha ez minden $a \in D_f$ helyen igaz, akkor $f$ **folytonos**, jelben $f \in C$.

Az egyváltozós esethez képest az egyetlen változás, hogy $|f(x)-f(a)|$ helyén $\sigma$, $|x-a|$ helyén $\rho$ áll: a $\mathbb{K}$-beli algebrai struktúra és a rendezés nem játszik szerepet, csak a távolság.

**Környezetes átfogalmazás.** $f \in C\{a\}$ akkor és csak akkor, ha minden $K(f(a)) \subset Y$ környezethez van olyan $k(a) \subset X$ környezet, amellyel

$$f\bigl[k(a) \cap D_f\bigr] \subset K(f(a)).$$

### 2.1. Tétel — a nyílt halmazos jellemzés

**Tétel.** Az $f \in X \to Y$ függvény akkor és csak akkor folytonos, ha minden $Z \subset Y$ nyílt halmazhoz van olyan $A \subset X$ nyílt halmaz, hogy

$$f^{-1}[Z] = A \cap D_f.$$

Speciálisan egy $f : X \to Y$ (mindenütt értelmezett) függvény akkor és csak akkor folytonos, ha minden nyílt halmaz ősképe nyílt.

*Bizonyítás.* ($\Rightarrow$) Legyen $Z \ne \emptyset$ nyílt és $a \in f^{-1}[Z]$. $Z$ nyíltsága miatt alkalmas $K(f(a)) \subset Z$, a folytonosság miatt pedig alkalmas $k(a)$ környezettel $f[k(a)\cap D_f] \subset K(f(a))$, azaz $k(a) \cap D_f \subset f^{-1}[Z]$. Az $A := \bigcup_{a \in f^{-1}[Z]} k(a)$ halmaz nyílt (nyílt halmazok uniója), és $f^{-1}[Z] = A \cap D_f$.

($\Leftarrow$) Legyen $a \in D_f$ és $Z := K(f(a))$. A feltétel szerint $f^{-1}[K(f(a))] = A \cap D_f$ alkalmas nyílt $A$-val, és $a \in A$, tehát van $k(a) \subset A$ környezet. Erre $f[k(a)\cap D_f] \subset K(f(a))$, azaz $f \in C\{a\}$. $\blacksquare$

Ez a jellemzés az, ami a folytonosságot tisztán topológiai fogalommá teszi: nem a metrikára, csak a nyílt halmazok rendszerére hivatkozik.

### 2.3. Tétel — kompozíció

**Tétel.** Legyenek $(X,\rho)$, $(Y,\sigma)$, $(Z,\delta)$ metrikus terek, $g \in X \to Y$, $f \in Y \to Z$, továbbá $a \in D_g$, $g(a) \in D_f$, $g \in C\{a\}$ és $f \in C\{g(a)\}$. Ekkor $f \circ g \in C\{a\}$.

A bizonyítás az [[concepts/analiii/atviteli-elv-metrikus-terben|átviteli elv]] kétszeri alkalmazása: ha $x_n \to a$, akkor $g(x_n) \to g(a)$, majd $f(g(x_n)) \to f(g(a))$.

### Műveletek folytonos függvényekkel

Legyen $(X,\rho)$ metrikus tér, $(Y,\|\cdot\|)$ normált tér, $\sigma(y,z) := \|y-z\|$, és $f, g \in X \to Y$.

- Ha $a \in D_f \cap D_g$ és $f, g \in C\{a\}$, akkor minden $\lambda \in \mathbb{K}$ mellett $f + \lambda g \in C\{a\}$.
- Ha $Y := \mathbb{K}$, akkor ezen felül $f \cdot g \in C\{a\}$, és ha $g(a) \ne 0$, akkor $f/g \in C\{a\}$ is.

Az állítások (a bizonyításukkal együtt) szó szerint az egyváltozós esetből öröklődnek, az átviteli elven keresztül.

### Nevezetes folytonos függvények

Rögzített $a \in X$ mellett folytonosak az

$$x \mapsto \rho(x,a), \qquad x \mapsto \|x-a\|, \qquad x \mapsto \langle x, a\rangle, \qquad x \mapsto \|x\|$$

függvények (metrikus, normált, illetve euklideszi térben). Ezek a folytonossági bizonyítások leggyakrabban használt építőkövei.

### Ekvivalens metrikák és izolált pontok

**Metrikacsere.** Ha $\rho \sim \rho^*$ az $X$-en és $\sigma \sim \sigma^*$ az $Y$-on, akkor $f$ pontbeli (és globális) folytonossága független attól, hogy melyik metrikát használjuk. Így $\mathbb{K}^s$-en és $\mathbb{K}^m$-en bármelyik $\rho_p$ metrika használható — lásd [[concepts/analiii/ekvivalens-normak]].

**Izolált pont.** Ha $a \in D_f \setminus D_f'$, azaz $a$ izolált pontja az értelmezési tartománynak, akkor $f$ **automatikusan** folytonos $a$-ban: alkalmas $v > 0$ mellett $k_v(a) \cap D_f = \{a\}$, és $\sigma(f(a),f(a)) = 0 < \varepsilon$. A folytonosság tehát csak torlódási pontokban mond valamit — ott viszont ekvivalens azzal, hogy $\lim_a f = f(a)$.

### Zárt szinthalmazok

Ha $f : X \to Y$ folytonos, akkor minden $y \in Y$ esetén az

$$X_y := \{x \in X : f(x) = y\}$$

halmaz zárt. Valóban, ha $x_n \in X_y$ és $x_n \to \alpha$, akkor $f(\alpha) = \lim f(x_n) = y$, tehát $\alpha \in X_y$. Ugyanez igaz $f \in X \to Y$ esetén is, ha $D_f$ zárt. Speciálisan zárt halmazon értelmezett folytonos $f \in \mathbb{K}^s \to \mathbb{K}^m$ függvény **zérushelyeinek** halmaza zárt — ennek az egyenletek közelítő megoldási módszereiben van jelentősége.

## Kapocs

- [[concepts/analiii/atviteli-elv-metrikus-terben]] — a folytonosság sorozatos jellemzése; a fenti bizonyítások motorja
- [[concepts/analiii/fuggvenyhatarertek-metrikus-terben]] — a határérték fogalma; torlódási pontban a folytonosság ezzel ekvivalens
- [[concepts/analiii/metrikus-ter]] — a $\rho$, $\sigma$ struktúra, amire a definíció épül
- [[concepts/analiii/nyilt-es-zart-halmazok]] — a 2.1. Tétel nyílt halmazai és a zárt szinthalmazok
- [[concepts/analiii/koordinatafuggvenyek-folytonossaga]] — a vektorértékű eset visszavezetése koordinátánként
- [[concepts/analiii/egyenletes-folytonossag-metrikus-terben]] — az erősebb, $a$-tól független változat
