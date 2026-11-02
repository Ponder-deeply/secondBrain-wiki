---
tags: [concept]
sources: [Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf]
derivation: source
kind: definition
element: water
updated: 2026-10-21
---

# Faktorgyűrű és a gyűrű homomorfizmustétele

Egy gyűrű ideál szerinti mellékosztályai a reprezentánsokon végzett műveletekkel gyűrűt alkotnak (maradékosztály-gyűrű); minden gyűrűhomomorfizmus magja ideál, és a faktorgyűrű a képpel izomorf.

## Tartalom

### Az ideál szerinti osztályozás kompatibilis a szorzással

Ha $I$ ideál $R$-ben, akkor az $I + a$ mellékosztályokra

$$(I + a)(I + b) = II + aI + Ib + ab \subseteq I + ab,$$

vagyis a szorzás is kompatibilis az osztályozással (az additív kompatibilitás a normálosztóra vonatkozó tételből jön, lásd [[concepts/dimatii/normaloszto-es-faktorcsoport]]).

**Megfordítás.** Ha az $R$ egy osztályozása mindkét művelettel kompatibilis, és $I$ a $0$ osztálya, akkor az additív csoportra vonatkozó tétel (2) pontja szerint $I$ normálosztó (additívan részcsoport), és az osztályozás pontosan az $I$ szerinti mellékosztályokból áll. $I$ ideál is: minden $X$ osztályra $0 \in I \Rightarrow 0 \in X \cdot I \Rightarrow X \cdot I \subseteq I$ (az osztályok kompatibilitása miatt), tehát $RI \subseteq I$; $IR \subseteq I$ hasonlóan. Ez a gyűrűtétel (8.2.15) második fele, lásd [[concepts/dimatii/reszgyuru-es-idealok]].

**Következmény (8.2.16).** Egy $R$ gyűrű egy $I$ ideál szerinti mellékosztályai az összeadásra és a szorzásra nézve gyűrűt alkotnak. *Bizonyítás.* Ha $\sim$ a megfelelő ekvivalenciareláció, akkor az $x \mapsto \tilde{x}$ kanonikus leképezés mindkét műveletre nézve művelettartó, és gyűrű homomorf képe gyűrű.

### Definíció (faktorgyűrű)

Legyen $R$ gyűrű, $I$ ideál $R$-ben. $R$-nek az $I$ szerinti **maradékosztály-gyűrűje (faktorgyűrűje)**

$$R/I = \{\, I + r \mid r \in R \,\}$$

a következő műveletekkel:

1. $(I + r) + (I + s) = I + (r + s)$,
2. $(I + r) \cdot (I + s) = I + r s$.

### Pitfall: a szorzás nem komplexusszorzás

A 2. pontban **nem** a halmazok szokásos komplexusszorzásáról van szó: a halmazok szorzata általában csak része az $I + rs$ osztálynak, nem egyenlő vele. Példa: $R = \mathbb{Z}$, $I = 8\mathbb{Z}$, $a = b = 4$:

$$(8\mathbb{Z} + 4)(8\mathbb{Z} + 4) = 64\mathbb{Z}^2 + 32\mathbb{Z} + 32\mathbb{Z} + 16 = 64\mathbb{Z} + 32\mathbb{Z} + 16 \subseteq 16\mathbb{Z} \subsetneq 8\mathbb{Z} + 16,$$

mert $\mathbb{Z}\cdot\mathbb{Z} = \mathbb{Z}$ és $\mathbb{Z} + \mathbb{Z} = \mathbb{Z}$; a bal oldal minden eleme osztható $16$-tal, míg $8\mathbb{Z} + 16$ ($= 8\mathbb{Z}$) minden $8$-cal osztható elemet tartalmaz. A művelet tehát a **reprezentánsokon** át van definiálva, és a kompatibilitás garantálja, hogy ez jól definiált.

### A homomorfizmus magja és a homomorfizmustétel gyűrűkre

**Definíció (8.2.20).** Egy $R$ gyűrűnek egy $R'$ gyűrűbe való $\varphi$ homomorfizmusánál a **homomorfizmus magja** az $R'$ nulleleme teljes inverz képe: $\ker(\varphi) = \varphi^{-1}(0')$.

**Homomorfizmustétel (8.2.21).** Egy $R$ gyűrű egy $\varphi$ homomorfizmusánál a homomorfizmus magja **ideál**. Ha $R$ képe $R'$, akkor az $R/\ker(\varphi)$ maradékosztály-gyűrű izomorf $R'$-vel. Az $R$ bármely $I$ ideálja magja valamely homomorfizmusnak: például az $R$ kanonikus leképezése $R/I$-re homomorfizmus, amelynek magja $I$.

A csoportokra vonatkozó megfelelő állítást lásd [[concepts/dimatii/homomorfizmustetel]]; gyűrűkben az ideál játssza a normálosztó szerepét.

## Kapocs

- [[concepts/dimatii/reszgyuru-es-idealok]] — az ideál és a szerinte vett mellékosztályok
- [[concepts/dimatii/normaloszto-es-faktorcsoport]] — a csoportos megfelelő (additív csoport normálosztója)
- [[concepts/dimatii/homomorfizmustetel]] — a csoporthomomorfizmus-tétel
- [[concepts/dimatii/homomorfizmus-es-izomorfizmus]] — a kanonikus leképezés homomorf
- [[concepts/dimatii/gyuru]] — az alapfogalom
- [[concepts/dimatii/maradekosztaly]] — a $\mathbb{Z}/m\mathbb{Z}$ speciális eset
