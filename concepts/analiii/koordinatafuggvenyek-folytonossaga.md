---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 2.9. Tétel és 2.1. iv)–v) megjegyzések"]
derivation: source
updated: 2026-09-07
---

# Koordinátafüggvények folytonossága

Egy vektorértékű függvény pontosan akkor folytonos egy pontban, ha mindegyik koordinátafüggvénye folytonos ott. Ez a tétel a vektorértékű esetet skalárértékűre vezeti vissza, és a projekciók folytonosságán múlik.

## Tartalom

### Koordinátafüggvények

Legyen $\mathbb{K}_1, \mathbb{K}_2 \in \{\mathbb{R},\mathbb{C}\}$, $1 \le s,m \in \mathbb{N}$ és $f \in \mathbb{K}_1^s \to \mathbb{K}_2^m$. Ha $s > 1$, $f$ **többváltozós** függvény; ha $m > 1$, **vektorfüggvény**. Az $x \in D_f$ helyen $(y_1,\dots,y_m) := f(x)$ jelöléssel az

$$f_i : D_f \to \mathbb{K}_2, \qquad f_i(x) := y_i \qquad (i = 1,\dots,m)$$

függvény az $f$ **$i$-edik koordinátafüggvénye**, és $f = (f_1,\dots,f_m)$.

### 2.9. Tétel

**Tétel.** Az $(X,\rho) := (\mathbb{K}_1^s,\rho_p)$, $(Y,\sigma) := (\mathbb{K}_2^m,\rho_q)$ terekben az $f = (f_1,\dots,f_m)$ függvény akkor és csak akkor folytonos az $a \in D_f$ helyen, ha minden $i = 1,\dots,m$ esetén $f_i \in C\{a\}$. Speciálisan $f$ akkor és csak akkor folytonos, ha minden koordinátafüggvénye folytonos.

*Bizonyítás.* Az [[concepts/analiii/atviteli-elv-metrikus-terben|átviteli elv]] szerint az állítás ezzel ekvivalens: minden $x_n \to a$, $(x_n) : \mathbb{N}\to D_f$ sorozatra $f(x_n) \to f(a)$ akkor és csak akkor, ha $f_i(x_n) \to f_i(a)$ minden $i$-re. Márpedig $\bigl(f_i(x_n)\bigr)$ épp az $\bigl(f(x_n)\bigr)$ sorozat $i$-edik koordinátasorozata, tehát az állítás a [[concepts/analiii/konvergencia-metrikus-terben|koordinátánkénti konvergencia]] tételének következménye. $\blacksquare$

Mivel a $\rho_p$ metrikák ekvivalensek, a tétel bármelyik $p, q$ paraméterrel érvényes — például elég mindkét oldalon a $\rho_2$ euklideszi metrikát tekinteni.

### Szorzattér és projekciók

Az állítás nem $\mathbb{K}^m$-specifikus. Legyen $(Y\times Z, \sigma\times\delta)$ szorzattér és $f = (f_1,f_2) \in X \to Y\times Z$, ahol $f_1 \in X \to Y$, $f_2 \in X \to Z$ az $f(x) = (y,z)$ előírással adott koordinátafüggvények. Ekkor $f \in C\{a\}$ pontosan akkor, ha $f_1, f_2 \in C\{a\}$ — és ez véges sok tényezős szorzatra is átvihető.

A **projekciók** (vetítések)

$$P_1 : Y\times Z \to Y,\quad P_1(y,z) := y, \qquad P_2 : Y\times Z \to Z,\quad P_2(y,z) := z$$

a szorzatmetrika definíciója folytán folytonosak, és a koordinátafüggvények épp

$$f_1 = P_1 \circ f, \qquad f_2 = P_2 \circ f.$$

A tétel „$\Rightarrow$" iránya tehát a kompozíció folytonosságának is következménye. A $(\mathbb{K}^m,\rho_p)$ esetben $P_i(x) = x_i$ az $i$-edik projekció, egy $U \subset Y\times Z$ halmaz vetületei pedig $U^{(1)} = P_1[U]$, $U^{(2)} = P_2[U]$. Egy $A \subset \mathbb{K}^s$ halmaz akkor és csak akkor korlátos, ha minden $P_i[A]$ vetülete korlátos.

## Kapocs

- [[concepts/analiii/folytonossag-metrikus-terben]] — az alapfogalom, amit a tétel koordinátákra bont
- [[concepts/analiii/atviteli-elv-metrikus-terben]] — a bizonyítás eszköze
- [[concepts/analiii/konvergencia-metrikus-terben]] — a sorozatok koordinátánkénti konvergenciája
- [[concepts/analiii/koordinatafuggvenyek-differencialhatosaga]] — ugyanez a séma differenciálhatóságra
- [[concepts/analiii/fuggvenyhatarertek-metrikus-terben]] — a határértékre vonatkozó megfelelője
