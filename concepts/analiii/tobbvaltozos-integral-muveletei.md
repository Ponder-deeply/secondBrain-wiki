---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Műveletek többváltozós integrálható függvényekkel

Az integrálhatóság öröklődik összegre, konstansszorosra, szorzatra, hányadosra és egyenletesen folytonos külső függvénnyel való összetételre; az integrálási tartomány szerint pedig részhalmazra és egymásba nem nyúló halmazok uniójára.

## Tartalom

### Algebrai műveletek

**Tétel.** Legyen $A \in \mathcal{J}_p$, $f, g : A \to \mathbb{R}$ integrálható, $c \in \mathbb{R}$.

- $c\cdot f$ is integrálható, és $\int_A cf = c\int_A f$.
- $f + g$ is integrálható, és $\int_A (f+g) = \int_A f + \int_A g$.
- $fg$ is integrálható.
- Ha $h$ egyenletesen folytonos $f$ értékkészletén, akkor $h \circ f$ is integrálható.
- Ha $|g| \geq c > 0$, akkor $1/g$ is integrálható.
- Ha $|g| \geq c > 0$, akkor $f/g$ is integrálható.

A bizonyítás szó szerint ugyanaz, mint az egyváltozós Riemann-integrálnál: minden állítás az oszcillációs összeg becslésére vezethető vissza.

Figyeljük meg az aszimmetriát: az integrál **lineáris**, de a szorzat és a hányados esetében csak az integrálhatóság öröklődik, az integrál értékére nincs képlet.

### Integrálhatóság részhalmazon

**Tétel.** Ha $A, B \in \mathcal{J}_p$, $f$ integrálható $A$-n, és $B \subset A$, akkor $f$ integrálható $B$-n is.

**Bizonyítás.** Adott $\varepsilon > 0$-hoz vegyünk az $A$-nak olyan $\mathcal{F} = \{C_1,\dots,C_n\}$ felosztását, amelyre $\Omega(f,\mathcal{F}) < \varepsilon$. Legyen

$$\mathcal{G} = \{C_i \cap B : C_i \cap B \neq \emptyset\},$$

ez $B$ egy felosztása, és $\Omega(f,\mathcal{G}) \leq \Omega(f,\mathcal{F}) < \varepsilon$. $\square$

### Additivitás a tartomány szerint

**Tétel.** Legyenek $A, B \in \mathcal{J}_p$ egymásba nem nyúló halmazok és $f : (A\cup B) \to \mathbb{R}$ korlátos. Ekkor $f$ akkor és csak akkor integrálható $A\cup B$-n, ha integrálható $A$-n és $B$-n is; ebben az esetben

$$\int_{A\cup B} f = \int_A f + \int_B f.$$

**Bizonyítás.** Vegyük $A$-nak egy $\mathcal{F}_n$, $B$-nek egy $\mathcal{G}_n$ végtelenül finomodó felosztását; a kettő együtt $A\cup B$ egy felosztása, és

$$s(f, \mathcal{F}_n\cup\mathcal{G}_n) = s(f,\mathcal{F}_n) + s(f,\mathcal{G}_n), \qquad S(f,\mathcal{F}_n\cup\mathcal{G}_n) = S(f,\mathcal{F}_n) + S(f,\mathcal{G}_n).$$

Az $n \to \infty$ határátmenetből az alsó és a felső integrálok is összeadódnak. $\square$

### Kiterjesztés nullával egy téglára

**Következmény.** Legyen $T \subset \mathbb{R}^p$ tégla, $A \subset T$ mérhető, $f : A \to \mathbb{R}$ korlátos, és

$$g : T \to \mathbb{R}, \qquad g(x) = \begin{cases} f(x) & \text{ha } x \in A, \\ 0 & \text{ha } x \notin A. \end{cases}$$

Ekkor $f$ akkor és csak akkor integrálható $A$-n, ha $g$ integrálható $T$-n, és ilyenkor $\int_A f = \int_T g$.

Ez a technikai észrevétel teszi lehetővé, hogy tetszőleges mérhető tartományon vett integrált téglán vett integrállá alakítsunk — a szukcesszív integrálás minden alkalmazásának ez az első lépése.

## Kapocs

- [[concepts/analiii/tobbvaltozos-integralhatosag]] — a bizonyítások eszköze, az oszcillációs összeg
- [[concepts/analiii/jordan-merheto-halmazok-gyuruje]] — az „egymásba nem nyúló" viszony, amelyre a tartomány szerinti additivitás épül
- [[concepts/analiii/szukcessziv-integralas]] — a nullával való kiterjesztés ott válik munkaeszközzé
- [[concepts/analii/muvelet-integralhato-fuggvenyekkel]] — az egyváltozós megfelelő; az állítások és a bizonyításuk változatlan, csak az intervallum helyére mérhető halmaz kerül
- [[concepts/analii/integral-egyenlotlensegek]] — az integrál monotonitása és a hozzá tartozó becslések egyváltozós alakja
