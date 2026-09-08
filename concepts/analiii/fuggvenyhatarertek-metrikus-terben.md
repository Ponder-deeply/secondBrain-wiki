---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 2.1. xi)–xviii) megjegyzések"]
derivation: source
updated: 2026-09-07
---

# Függvényhatárérték metrikus terekben

Az $f \in X \to Y$ függvénynek az $a$ torlódási pontban vett határértéke az az egyértelmű $A \in Y$, amelynek minden környezetét felveszi $f$ az $a$ egy kipontozott környezetén. A fogalom lokális: sem $f(a)$, sem az $a \in D_f$ kérdés nem számít.

## Tartalom

### Definíció

Legyenek $(X,\rho)$, $(Y,\sigma)$ metrikus terek, $f \in X \to Y$ és $a \in D_f'$ (az értelmezési tartomány **torlódási pontja**). Azt mondjuk, hogy $f$-nek az $a$ helyen van **határértéke**, ha létezik olyan $A \in Y$, hogy minden $K(A) \subset Y$ környezethez van olyan $k(a) \subset X$ környezet, amellyel

$$f\bigl[\bigl(k(a)\setminus\{a\}\bigr) \cap D_f\bigr] \subset K(A),$$

azaz $f(x) \in K(A)$ minden $a \ne x \in k(a) \cap D_f$ esetén.

### Az egyértelműség

**Állítás.** Ilyen $A$ legfeljebb egy van.

*Bizonyítás.* Ha $B \ne A$ is teljesítené a feltételt, akkor $0 < r < \sigma(A,B)/2$ mellett $K(A) := K_r(A)$ és $K(B) := K_r(B)$ diszjunktak: $y \in K_r(A)$ esetén
$$\sigma(y,B) \ge \sigma(A,B) - \sigma(y,A) > \sigma(A,B) - r > r,$$
tehát $y \notin K_r(B)$. Viszont a $k(a) \cap k^*(a)$ környezet pontjaiban $f(x)$-nek egyszerre kellene $K(A)$-ban és $K(B)$-ben lennie. $\blacksquare$

Az így egyértelműen létező elemet $f$ **$a$-beli határértékének** nevezzük:

$$\lim_a f := \lim_{x\to a} f(x) := A, \qquad\text{illetve}\qquad f(x) \to A \quad (x \to a).$$

### Lokalitás

Ha $f, g \in X \to Y$ megegyeznek $a$ egy kipontozott környezetén — azaz alkalmas $k(a)$-val
$$\emptyset \ne D := \bigl(k(a)\setminus\{a\}\bigr)\cap D_f = \bigl(k(a)\setminus\{a\}\bigr)\cap D_g$$
és $f = g$ a $D$-n —, akkor $a \in D_f' \cap D_g'$ esetén $\lim_a f$ pontosan akkor létezik, ha $\lim_a g$ létezik, és ilyenkor egyenlők. A határérték tehát **lokális tulajdonság**: az $a \in D_f$ kérdés és az $f(a)$ helyettesítési érték szempontjából érdektelen.

### Kapcsolat a folytonossággal

- Ha $a \in D_f' \cap D_f$, akkor $f \in C\{a\}$ ekvivalens azzal, hogy $\lim_a f$ létezik és $\lim_a f = f(a)$.
- Ha $a \in D_f \setminus D_f'$ (izolált pont), akkor $f$ automatikusan folytonos $a$-ban, határértékről viszont nem beszélünk.

### Műveletek

Legyen $(Y,\|\cdot\|)$ normált tér, $\sigma(y,z) = \|y-z\|$, $a \in (D_f\cap D_g)'$, és létezzenek az $A := \lim_a f$, $B := \lim_a g$ határértékek. Ekkor minden $\lambda \in \mathbb{K}$ mellett

$$\lim_a (f + \lambda g) = A + \lambda B,$$

és $Y := \mathbb{K}$ esetén

$$\lim_a (fg) = AB, \qquad \lim_a \frac{f}{g} = \frac{A}{B} \quad (B \ne 0).$$

Mindez az [[concepts/analiii/atviteli-elv-metrikus-terben|átviteli elv]] és a sorozatokra vonatkozó műveleti szabályok egyszerű következménye. Többváltozós vektorfüggvényekre — $h, l \in \mathbb{K}^s \to \mathbb{K}$, $f, g \in \mathbb{K}^s \to \mathbb{K}^m$ — ugyanezt az alakot kapjuk.

### Koordinátánként

Szorzattérbe képező $f = (f_1,f_2) \in X \to Y\times Z$ függvényre: $\lim_a f$ akkor és csak akkor létezik, ha léteznek az $A_1 := \lim_a f_1$ és $A_2 := \lim_a f_2$ határértékek, és ekkor $\lim_a f = (A_1,A_2)$. Speciálisan $f = (f_1,\dots,f_m) \in \mathbb{K}^s \to \mathbb{K}^m$ esetén

$$\lim_a f = \bigl(\lim_a f_1, \dots, \lim_a f_m\bigr),$$

amint mind az $m$ koordinátahatárérték létezik. Ez a [[concepts/analiii/koordinatafuggvenyek-folytonossaga|2.9. Tétel]] határértékes párja.

## Kapocs

- [[concepts/analiii/folytonossag-metrikus-terben]] — torlódási pontban a folytonosság a határérték felvételét jelenti
- [[concepts/analiii/atviteli-elv-metrikus-terben]] — a határérték sorozatos jellemzése és a nemlétezés bizonyítása
- [[concepts/analiii/halmaz-pontjai-metrikus-terben]] — a torlódási és az izolált pont fogalma
- [[concepts/analiii/koordinatafuggvenyek-folytonossaga]] — a koordinátánkénti felbontás folytonosságra
