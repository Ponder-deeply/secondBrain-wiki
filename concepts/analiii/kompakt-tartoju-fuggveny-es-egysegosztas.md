---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 2.10. Tétel és a hozzá tartozó lemma"]
derivation: source
updated: 2026-09-07
---

# Kompakt tartójú függvény és az egységosztás

Egy függvény tartója a nem gyökhelyeinek lezártja. Kompakt tartójú függvény felbontható véges sok, előre megadott környezetekbe koncentrált függvény összegére — ez az egységosztás (partíció of unity), a lokalizálási technikák alapeszköze.

## Tartalom

### Tartó

Legyen $(X,\rho)$ metrikus tér, $Y$ lineáris tér $\mathbb{K}$ felett, $f \in X \to Y$. Az $f$ **tartója**

$$\operatorname{supp} f := \overline{\{f \ne 0\}} = \overline{\{x \in X : f(x) \ne 0\}}.$$

A $\operatorname{supp} f$ halmaz zárt, és $x \in D_f\setminus\operatorname{supp} f$ esetén $f(x) = 0$. Fordítva viszont nem: a tartón belül is lehetnek gyökhelyek. Például

$$f(x) := \begin{cases} x^2\sin(1/x) & (0 \ne x \in \mathbb{R})\\ 0 & (x = 0)\end{cases}$$

esetén az $x_n := \dfrac{2}{(4n+1)\pi}$ pontokra $f(x_n) \ne 0$ és $x_n \to 0$, tehát $0 \in \operatorname{supp} f$, holott $f(0) = 0$.

Ha $\operatorname{supp} f$ kompakt, akkor $f$ **kompakt tartójú függvény**.

### Az egységosztás lemmája

**Lemma.** Legyen $(X,\rho)$ metrikus tér, $\emptyset \ne A \subset X$ kompakt, és adottak a $K(x)$ ($x \in A$) környezetek. Ekkor alkalmas $s \in \mathbb{N}$ mellett léteznek olyan $\psi_i : X \to [0,1]$ ($i = 0,\dots,s$) függvények, hogy

a) minden $i$-hez van olyan $x \in A$, amellyel $\operatorname{supp}\psi_i \subset K(x)$;
b) $\sum_{i=0}^{s}\psi_i(t) = 1$ minden $t \in A$-ra;
c) mindegyik $\psi_i$ folytonos.

*Bizonyítás.* Legyen $\Phi : [0,1]\to[0,1]$ a folytonos „levágó" függvény

$$\Phi(z) := \begin{cases} 1 & (0 \le z \le 1/2)\\ 3-4z & (1/2 < z \le 3/4)\\ 0 & (3/4 < z \le 1).\end{cases}$$

Ha $K(x) = K_{r_x}(x)$, akkor a $\{K_{r_x/2}(x) : x \in A\}$ rendszer nyílt fedése a kompakt $A$-nak, tehát véges sok $x_i \in A$ ($i = 0,\dots,s$) ponttal $A \subset \bigcup_{i} K_{r_i/2}(x_i)$, ahol $r_i := r_{x_i}$. Legyen

$$\varphi_i(t) := \Phi\bigl(\rho(t,x_i)/r_i\bigr) \qquad (t \in X).$$

A $t \mapsto \rho(t,x_i)$ leképezés folytonos, tehát a $\varphi_i$-k is azok, továbbá $\varphi_i \equiv 1$ a $K_{r_i/2}(x_i)$ gömbön, $\varphi_i \equiv 0$ ott, ahol $\rho(t,x_i) \ge 3r_i/4$. Így

$$\operatorname{supp}\varphi_i = \overline{K_{3r_i/4}(x_i)} \subset K_{r_i}(x_i).$$

Tekintsük a

$$\psi_0 := \varphi_0, \qquad \psi_k := \varphi_k\prod_{i=0}^{k-1}(1-\varphi_i) \qquad (k = 1,\dots,s)$$

függvényeket. Ezek folytonosak, értékkészletük $[0,1]$-ben van, $\operatorname{supp}\psi_i \subset \operatorname{supp}\varphi_i$, és teljes indukcióval

$$\sum_{k=0}^{i}\psi_k = 1 - \prod_{j=0}^{i}(1-\varphi_j).$$

Ha $x \in A$, akkor alkalmas $i$-re $x \in K_{r_i/2}(x_i)$, tehát $\varphi_i(x) = 1$, így a szorzat eltűnik és $\sum_{k=0}^{s}\psi_k(x) = 1$. $\blacksquare$

A $\psi_k$-k képlete a „maradék" trükk: $\psi_k$ csak abból vesz, amit az előző tagok még nem fedtek le, ezért lesz az összeg pontosan $1$, nem több.

### 2.10. Tétel — a felbontás

**Tétel.** Legyen $(X,\rho)$ metrikus tér, $Y$ lineáris tér $\mathbb{K}$ felett, $f \in X \to Y$ kompakt tartójú, és adottak a $K(x)$ ($x \in \operatorname{supp} f$) környezetek. Ekkor alkalmas $s \in \mathbb{N}$ mellett léteznek olyan $f_i : X \to Y$ ($i = 0,\dots,s$) függvények, hogy

1. minden $i$-hez van olyan $x \in \operatorname{supp} f$, amellyel $\operatorname{supp} f_i \subset K(x)$;
2. $f = \sum_{i=0}^{s} f_i$.

Ha $\sigma$ norma által származtatott metrikával $(Y,\sigma)$ metrikus tér és $f$ folytonos, akkor az $f_i$ függvények is választhatók folytonosnak.

*Bizonyítás.* Alkalmazzuk a lemmát $A := \operatorname{supp} f$-re, és legyen $f_i := f\cdot\psi_i$. Ha $x \in D_f \cap \operatorname{supp} f$, akkor $\sum_i f_i(x) = f(x)\sum_i\psi_i(x) = f(x)$; ha $x \in D_f\setminus\operatorname{supp} f$, akkor $f(x) = 0$, tehát $\sum_i f_i(x) = 0 = f(x)$. $\blacksquare$

### Miért hasznos

A tétel „lokálisan koncentrált" darabokra bont: minden $f_i$ egyetlen előre megadott környezetben él. Ezért egy globális állítás gyakran visszavezethető a lokálisra — elég egy kis gömbön belül igazolni valamit, majd az egységosztással összegezni. Ez a technika az integráltételek és a felületi integrálok lokális–globális átmenetének standard eszköze.

## Kapocs

- [[concepts/analiii/kompakt-halmazok]] — a véges fedés kiválasztása, a lemma magja
- [[concepts/analiii/folytonossag-metrikus-terben]] — a $\varphi_i$-k folytonossága a kompozíció és a $\rho$ folytonosságából
- [[concepts/analiii/halmaz-pontjai-metrikus-terben]] — a tartót definiáló lezárás
- [[concepts/analiii/nyilt-es-zart-halmazok]] — a tartó zártsága, a fedés nyílt gömbjei
