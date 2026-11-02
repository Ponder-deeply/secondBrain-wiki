---
tags: [concept]
sources: [DimatIIEa01.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, dm2gy06_2020_Algebra.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-21
---

# Egység és asszociált

Az oszthatóság nem tesz különbséget $12$ és $-12$ között; az egység és az asszociáltság fogalma pontosan ezt a „megkülönböztethetetlenséget” írja le.

## Tartalom

### Egység

**Definíció.** Ha egy szám bármely másiknak osztója, akkor **egységnek** nevezzük.

**Állítás.** Az egész számok körében két egység van: $1$ és $-1$.

**Bizonyítás.** $\pm 1$ nyilván egység. Megfordítva, ha $\varepsilon$ egység, akkor $1 = \varepsilon \cdot q$ valamely $q$ egészre. Mivel $|\varepsilon| \geq 1$ és $|q| \geq 1$, ebből $|\varepsilon| = 1$, azaz $\varepsilon = \pm 1$. $\square$

**Példa.** A Gauss-egészek körében $i$ is egység, hiszen $a + bi = i(b - ai)$.

### Asszociáltság

**Definíció.** Két szám **asszociált**, ha egymás egységszeresei.

**Megjegyzés.** $a$ és $b$ pontosan akkor asszociáltak, ha $a \mid b$ és $b \mid a$. Az asszociáltság tehát az oszthatóság mint kvázirendezés szimmetrikus magja.

**Definíció.** Egy szám **triviális osztói** az asszociáltjai és az egységek.

Ez a fogalompár teszi lehetővé, hogy a felbonthatatlanságot „a triviális osztókon kívül nincs más osztója” alakban mondjuk ki, és hogy a számelmélet alaptételében az egyértelműséget csak sorrendtől és asszociáltaktól eltekintve állítsuk.

### Általános gyűrűben (egységelemes integritási tartomány)

*(Farkas Gábor előadásdiái.)* Egy $R$ egységelemes integritási tartományban **egység** az az elem, amely minden más elemnek osztója; az egységek halmaza $U(R)$. Az $a, b \in R$ **asszociáltak** ($a \sim b$), ha egymás egységszeresei. Észrevételek: a $\sim$ **ekvivalenciareláció**, és kompatibilis a $\mid$ relációval; az egységek **Abel-csoportot** alkotnak ($R$ egységcsoportja); a $0$-nak önmaga az egyetlen asszociáltja.

Egy $a \in R^* \setminus U(R)$ elem **triviális osztói** az egységek és önmaga egységszeresei (asszociáltjai).

**$\mathbb{Z}$ egységei** (az előadásdiák bizonyítása): $\pm 1$ egység, mert $a = a\cdot 1 = (-a)(-1)$. Ha $e$ egység, akkor $e \mid 1$, $1 = eq$, így $1 = |e||q|$ és $1 \leq |e|, 1 \leq |q|$, tehát $|e| = 1$, $e = \pm 1$.

### Feladattípusok és módszerek: egységek kiszámítása (gyakorlati feladatsor, 2020 ősz, 6. sor)

Egység = invertálható elem. $\mathbb{Z}$-ben $\pm1$; $\mathbb{Q}$, $\mathbb{R}$, $\mathbb{C}$-ben minden nemnulla elem (test); $\mathbb{Z}_7$-ben $1,\dots,6$ (test); $\mathbb{Z}_{10}$-ben $1,3,7,9$ (pontosan a $10$-hez relatív prímek; $3\cdot7=21\equiv1$, $9\cdot9=81\equiv1$). Indoklásnál az inverzet kell megadni, vagy nem létezését megmutatni (pl. $\mathbb{Z}_{10}$-ben $5\cdot2=0$ miatt $5$ nullosztó, nem egység).

## Kapocs

- [[concepts/dimatii/oszthatosag]] — az alapreláció, amelynek finomszerkezetét ez a lap írja le
- [[concepts/dimatii/felbonthatatlan-es-prim]] — a triviális osztókra épülő definíció
- [[concepts/dimatii/szamelmelet-alaptetele]] — az egyértelműség itt csak asszociáltaktól eltekintve áll fenn
- [[concepts/dimatii/legnagyobb-kozos-oszto]] — csak asszociáltság erejéig egyértelmű
