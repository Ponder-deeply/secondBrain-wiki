---
tags: [concept]
sources: [DimatIIEa01.pdf, DimatIIEa02.pdf, Lehman-Leighton-Meyer-Mathematics-for-Computer-Science.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, dimat2gyak03mo.pdf, dm2gy02_Szamelmelet.pdf, dm2gy06.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-21
---

# Bővített euklideszi algoritmus

Az euklideszi algoritmus melléktermékként azt is megadja, hogyan áll elő a legnagyobb közös osztó a két szám egész együtthatós lineáris kombinációjaként.

## Tartalom

**Tétel.** Minden $a, b$ egész szám esetén léteznek olyan $x, y$ egészek, hogy
$$(a,b) = x\cdot a + y\cdot b.$$

**Bizonyítás.** Legyenek $q_i, r_i$ az [[concepts/dimatii/euklideszi-algoritmus]]sal kapott hányadosok és maradékok. Legyen

$$x_{-1} = 1,\quad x_0 = 0,\qquad x_i = x_{i-2} - q_ix_{i-1} \ \ (i \geq 1),$$
$$y_{-1} = 0,\quad y_0 = 1,\qquad y_i = y_{i-2} - q_iy_{i-1} \ \ (i \geq 1).$$

Ekkor $i \geq 1$ esetén $x_ia + y_ib = r_i$ (indukcióval). Speciálisan $x_na + y_nb = r_n = (a,b)$. $\square$

### Az algoritmus

$$r_{i-2} = r_{i-1}q_i + r_i, \qquad x_i = x_{i-2} - q_ix_{i-1}, \qquad y_i = y_{i-2} - q_iy_{i-1}.$$

**Példa.** Számítsuk ki $(172,62)$ értékét és oldjuk meg a $172x + 62y = (172,62)$ egyenletet!

| $i$ | $r_i$ | $q_{i+1}$ | $x_i$ | $y_i$ | $r_i = 172x_i + 62y_i$ |
|---:|---:|---:|---:|---:|---|
| $-1$ | 172 | — | 1 | 0 | $172 = 172\cdot 1 + 62\cdot 0$ |
| 0 | 62 | 2 | 0 | 1 | $62 = 172\cdot 0 + 62\cdot 1$ |
| 1 | 48 | 1 | 1 | $-2$ | $48 = 172\cdot 1 + 62\cdot(-2)$ |
| 2 | 14 | 3 | $-1$ | 3 | $14 = 172\cdot(-1) + 62\cdot 3$ |
| 3 | 6 | 2 | 4 | $-11$ | $6 = 172\cdot 4 + 62\cdot(-11)$ |
| 4 | 2 | 3 | $-9$ | 25 | $2 = 172\cdot(-9) + 62\cdot 25$ |
| 5 | 0 | — | 31 | $-86$ | $0 = 172\cdot 31 + 62\cdot(-86)$ |

A felírás: $2 = 172\cdot(-9) + 62\cdot 25$, azaz $x = -9$, $y = 25$.

### Mire használjuk

A bővített euklideszi algoritmus a kurzus legtöbbet használt konstruktív eszköze:

- a *felbonthatatlan $\Rightarrow$ prím* implikáció bizonyítása $\mathbb{Z}$-ben;
- a [[concepts/dimatii/linearis-kongruencia]] megoldása;
- a [[concepts/dimatii/linearis-diofantikus-egyenlet]] megoldása;
- a [[concepts/dimatii/kinai-maradektetel]] konstruktív bizonyítása;
- multiplikatív inverz keresése $\mathbb{Z}_m$-ben, lásd [[concepts/dimatii/invertalhatosag-zm-ben]].

### Kézi nyilvántartás: másik példa és vízkancsó-feladat (Lehman–Leighton–Meyer 9.2.2–9.2.3)

A forrás ugyanezt az eljárást „Pulverizer" néven (*kuttaka*, kb. 6. századi indiai eredet) mutatja, a maradékokat $a$ és $b$ lineáris kombinációjaként követve. $a = 259$, $b = 70$:

- $49 = 259 - 3\cdot 70 = a - 3b$;
- $21 = 70 - 49 = b - (a - 3b) = -a + 4b$;
- $7 = 49 - 2\cdot 21 = (a - 3b) - 2(-a + 4b) = 3a - 11b$.

Ellenőrzés: $3\cdot 259 - 11\cdot 70 = 777 - 770 = 7 = (259,70)$.

**Következmény.** Egy szám akkor és csak akkor áll elő $xa + yb$ alakban, ha $(a,b)$ többszöröse.

**Vízkancsó-feladat.** $a$ és $b$ literes kancsókkal (és csap meg lefolyó) a kancsókban lévő víz mennyisége mindig $a$ és $b$ lineáris kombinációja (indukcióval: kitöltés/kiürítés után 0 vagy tele, a kiöntésnél $x+y$, $x+y-a$ vagy $x+y-b$). Tehát mindig $(a,b)$ többszöröse. Így $12$ és $18$ literessel nem mérhető ki $4$ (a többszörösök $6$-tal oszthatók), $899$ és $1147$ literessel nem mérhető $32$ ($(899,1147) = 31$).

Megfordítva ($c \in [0..a]$): $c$ liter kimérhető az $a$ literes kancsóban akkor és csak akkor, ha $(a,b) \mid c$. Konstruktív eljárás, együtthatók ismerete nélkül: ismételjük, amíg el nem érjük a kívánt mennyiséget — töltsük meg a kisebb kancsót, öntsük át a nagyobba; ha a nagyobb megtelik, ürítsük ki, és öntsük tovább a maradékot. A $21$ és $26$ literes kancsókkal $3$ litert $15$ töltés után kapunk: $15\cdot 21 = 315 = 12\cdot 26 + 3$. Ez az $s' = 15$, $t' = -12$ együtthatós $3 = 21s' + 26t'$ felírás; az $s$ pozitívvá tehető, ha $s$-et $26$-tal növeljük, $t$-t $21$-gyel csökkentjük.

### Az eljárás az előadásdiák (Járai-féle) jelölésével

*(Farkas Gábor előadásdiái, 6.1.11.)* Az eljárás meghatározza $a, b \in \mathbb{Z}$ egy $d$ legnagyobb közös osztóját és olyan $x, y$ egészeket, hogy $d = ax + by$; végig $ax_n + by_n = r_n$.

1. *Inicializálás:* $x_0 = 1,\ y_0 = 0,\ r_0 = a,\ x_1 = 0,\ y_1 = 1,\ r_1 = b,\ n = 0$.
2. *Vége?* Ha $r_{n+1} = 0$, akkor $x = x_n,\ y = y_n,\ d = r_n$, vége.
3. *Ciklus:* $q_{n+1} = \lfloor r_n / r_{n+1} \rfloor$, $r_{n+2} = r_n - r_{n+1}q_{n+1}$, $x_{n+2} = x_n - x_{n+1}q_{n+1}$, $y_{n+2} = y_n - y_{n+1}q_{n+1}$, $n \leftarrow n+1$, ugrás a 2. lépésre.

(Az indexelés eltér a fenti lapétól: ott $x_{-1}, x_0$ az induló pár, itt $x_0, x_1$.)

*Helyesség.* Véges: a maradékok szigorúan monoton csökkennek. $r_n$ közös osztó: $r_n \mid r_n \wedge r_n \mid r_{n-1} \Rightarrow r_n \mid r_{n-2}$, és így visszafelé $r_n \mid a \wedge r_n \mid b$. Az invariáns indukcióval: $ax_0 + by_0 = a = r_0$ (és $ax_1+by_1=b=r_1$); ha $n-1$-ig igaz, akkor $ax_n + by_n = a(x_{n-2} - q_nx_{n-1}) + b(y_{n-2} - q_ny_{n-1}) = r_{n-2} - q_nr_{n-1} = r_n$. $\square$

### Feladattípusok és módszerek (gyakorlat 3.)

**Típus: $ax + by = (a,b)$ összes megoldása.** A táblázatot ($\alpha_i$, $\beta_i$ az $a$, illetve $b$ együtthatója) $r_i = a\alpha_i + b\beta_i$ alakban vezetjük, és az utolsó, $r = 0$ sor adja a homogén megoldást: $a\alpha_{n} + b\beta_{n} = 0$. A teljes megoldás: (az $r = (a,b)$ sor) + $k\cdot$(a $0$ sor), pl. $a=13$, $b=14$: $13(14k-1) + 14(1-13k) = 1$, azaz $x = 14k-1$, $y = 1-13k$. További kidolgozott eredmények: $(16,37)=1$: $x = 7-37k$, $y = 16k-3$; $(39,55)=1$: $x = 24-55k$, $y = 39k-17$; $(105,154)=7$: $x = 3-22k$, $y = 15k-2$.

**Negatív bemenet.** A maradékos osztás nemnegatív számokon fut, ezért negatív $a$ vagy $b$ helyett $-a$-val, $-b$-vel írjuk a táblázatot, és a végén az együttható előjelét visszaváltjuk. Példa: $(90,-111)$: a $90$, $111$ táblázata $3 = 90\cdot(-16) + 111\cdot 13$-at ad, tehát $b = -111$ mellett $3 = 90\cdot(-16) + (-111)\cdot(-13)$, és a homogén rész $90\cdot 37k + (-111)\cdot 30k = 0$, azaz $x = 37k-16$, $y = 30k-13$ a $\gcd(90,-111)$ együtthatókra. Ellenőrzés: $-1440 + 1443 = 3$.

**Ellenőrzési szabály.** A végső $0$ sor együtthatói $\pm b/(a,b)$ és $\mp a/(a,b)$ (pl. $-22k$, $15k$ a $105$, $154$ esetén: $105/7 = 15$, $154/7 = 22$) — ez a számolás gyors próbája.

Folytatás: [[concepts/dimatii/linearis-diofantikus-egyenlet]] (jobb oldal $c$), [[concepts/dimatii/linearis-kongruencia]] (kongruenciák ezzel oldva).

### Feladattípusok (2020. 2. feladatsor, 2024. 6. sorozat)

A 2. feladatsor 2. feladata: az 1. feladat minden $(a,b)$ párjára $ax + by = (a,b)$ előállítása; néhány ellenőrzött megoldás: $86\cdot(-9) + 31\cdot 25 = 1$, $139\cdot(-11) + 102\cdot 15 = 1$, $2016\cdot(-24) + 880\cdot 55 = 16$.

*Számológép nélkül* ($2024$. 6. sorozat 9. feladata): $a = 2^{13}-1 = 8191$, $b = 2^8 - 1 = 255$. A lépések: $8191 = 32\cdot 255 + 31$, $255 = 8\cdot 31 + 7$, $31 = 4\cdot 7 + 3$, $7 = 2\cdot 3 + 1$; visszafelé $1 = 8191\cdot(-74) + 255\cdot 2377$ (ellenőrzés: $-606134 + 606135 = 1$).

*Fibonacci-számok* (6. sorozat 16. feladata, szorgalmi): $(F_n, F_{n-1}) = 1$, és a Cassini-azonosságból $F_nF_{n-2} - F_{n-1}^2 = (-1)^{n+1}$, tehát $F_n\cdot x + F_{n-1}\cdot y = 1$ egy megoldása $x = (-1)^{n+1}F_{n-2}$, $y = (-1)^{n}F_{n-1}$ (pl. $n = 5$: $5\cdot 2 + 3\cdot(-3) = 1$; $n = 6$: $8\cdot(-3) + 5\cdot 5 = 1$). Az euklideszi algoritmus itt az utolsó lépés kivételével mindig $q = 1$-et ad (a leglassabb eset).

### Euklideszi gyűrűben

Az eljárás tetszőleges euklideszi gyűrűben is működik (a maradék normája csökken), és ott igazolja a felbonthatatlan $\Rightarrow$ prím irányt; lásd [[concepts/dimatii/euklideszi-gyuru-egyertelmu-felbontas]].

## Kapocs

- [[concepts/dimatii/euklideszi-algoritmus]] — az alapalgoritmus, amit ez kiterjeszt
- [[concepts/dimatii/legnagyobb-kozos-oszto]] — az előállított mennyiség
- [[concepts/dimatii/felbonthatatlan-es-prim]] — a két fogalom egybeesésének bizonyítási eszköze
- [[concepts/dimatii/linearis-kongruencia]] — közvetlen alkalmazás
- [[concepts/dimatii/kinai-maradektetel]] — konstruktív bizonyítás
- [[concepts/dimatii/oszthatosag]] — a lineáris kombináció fogalma és a közös osztó tulajdonsága
