---
tags: [concept]
sources: [DimatIIEa02.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, dimat2gyak03mo.pdf, Dimat2mintaZH1.pdf, dm2gy02_Szamelmelet.pdf, dm2gy03_Szamelmelet.pdf, dm2gy05.pdf, dm2gy06.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-21
---

# Lineáris diofantikus egyenlet

Diofantikus egyenlet: olyan egyenlet, amelynek csak az egész megoldásait keressük. A lineáris eset a lineáris kongruenciával ekvivalens.

## Tartalom

**Definíció.** A **lineáris diofantikus egyenlet** alakja
$$ax + by = c, \qquad a, b, c \in \mathbb{Z},$$
és a megoldásokat az egészek körében keressük.

Ez ekvivalens az
$$ax \equiv c \pmod b, \qquad by \equiv c \pmod a$$
kongruenciákkal. Az egyenlet **pontosan akkor oldható meg, ha $(a,b) \mid c$**, és ekkor a megoldások a [[concepts/dimatii/bovitett-euklideszi-algoritmus]]sal kaphatók meg — lásd [[concepts/dimatii/linearis-kongruencia]].

### Nem lineáris példák

Nem lineáris diofantikus egyenletekre nincs ilyen általános eljárás; a megoldhatatlanság gyakran maradékos érveléssel mutatható meg.

- $x^2 + y^2 = -4$: nincs valós megoldás sem.
- $x^2 - 4y^2 = 3$: nincs megoldás, ugyanis a $4$-gyel való osztási maradékokat vizsgálva $x^2 \equiv 3 \pmod 4$ kellene. De ez nem lehet, mert a négyzetszám maradéka $0$ vagy $1$:

| $x$ | $x^2 \bmod 4$ |
|---|---:|
| $4k$ | 0 |
| $4k+1$ | 1 |
| $4k+2$ | 0 |
| $4k+3$ | 1 |

Ez a **maradékos kizárás** módszere: egy alkalmas modulus szerint a két oldal maradéka soha nem eshet egybe.

### A megoldhatóság bizonyítása és a megoldások családja (Farkas-diák)

**Tétel.** Rögzített $a,b,c\in\mathbb{Z}$ esetén $ax + by = c$-nek akkor és csak akkor van (egész) megoldása, ha $(a,b)\mid c$.

*($\Rightarrow$)* Ha $x_0, y_0$ megoldás, akkor $(a,b)\mid a$ és $(a,b)\mid b$, így a lineáris kombináció tulajdonsága miatt $(a,b)\mid ax_0 + by_0 = c$.
*($\Leftarrow$)* Ha $c = (a,b)q$ és $(a,b) = au + bv$, akkor $c = a(uq) + b(vq)$, tehát $x = uq$, $y = vq$ megoldás.

**Megjegyzés.** Ha $x, y$ megoldás, akkor minden $t\in\mathbb{Z}$-re $x_1 = x + bt$, $y_1 = y - at$ is az: $a(x+bt) + b(y-at) = ax + by$. (A diák itt csak azt mutatják, hogy ezek megoldások; a teljes megoldáshalmaz leírását lásd [[concepts/dimatii/linearis-kongruencia]], ahol $m' = m/d$ lépésközzel adódik.)

### Feladattípusok és módszerek (gyakorlat 3.)

**1. $ax + by = c$ megoldása.** Először $ax + by = (a,b)$-t oldjuk meg ([[concepts/dimatii/bovitett-euklideszi-algoritmus]]), majd $c/(a,b)$-vel szorzunk, és hozzáadjuk a homogén megoldást.
- $16x + 37y = -2$: $16\cdot 7 + 37\cdot(-3) = 1$, $-2$-vel szorozva és a $0$-előállítást ($16\cdot(-37k) + 37\cdot 16k$) hozzáadva $x = -14 - 37k$, $y = 16k + 6$.
- $-168x + 219y = 12$: $(-168,219) = 3$, $4 \mid$ szorzó: $x = 73k - 120$, $y = 56k - 92$.

**2. Megoldhatatlanság: $(a,b) \nmid c$.** $90x - 111y = 13$: $(90,111) = 3 \nmid 13$, mert $3 \mid 90x - 111y$ minden $x,y$-ra. Hasonlóan $39x + 102y = 10$ ($3\nmid 10$).

**3. Egyszerűsítés a legnagyobb közös osztóval.** $51x + 114y = -9$: osztunk $3$-mal, $17x + 38y = -3$, és kis számokkal számolunk: $17\cdot 9 + 38\cdot(-4) = 1$, $-3$-mal szorozva $x = -27 - 38k$, $y = 12 + 17k$.

**4. Nemnegatív (szöveges) megoldások.** A teljes megoldásra $x \ge 0$, $y \ge 0$ feltételt írunk, ez $k$-ra intervallumot ad; a megoldások a $k$ egész értékei.
- *Százlábúak:* $20x + 14y = 232$; $20\cdot(-2) + 14\cdot 3 = 2$, $116$-tal szorozva $x = 7k - 232$, $y = 348 - 10k$. $x,y\ge 0 \Rightarrow 33\tfrac17 \le k \le 34{,}8$, így $k = 34$: $x = 6$, $y = 8$ (ellenőrzés: $120 + 112 = 232$).
- *Váltópénz:* $100$ Ft visszajáró $20$ és $50$ forintosokkal: $50x + 20y = 100$. Részmegoldás $50\cdot 10 + 20\cdot(-20) = 100$, általános $x = 10 - 2k$, $y = 5k - 20$; $x,y \ge 0 \Rightarrow 4 \le k \le 5$, tehát két megoldás: $(2,0)$ és $(0,5)$. (Józan paraszti esetszétválasztással is: legfeljebb két ötvenes.)

**5. Hatványegyenlet visszavezetése.** Ha minden hatvány ugyanannak a prímnek a hatványa, a prímalapú logaritmus lineáris diofantikus egyenletet ad: $8^a\cdot 16^b = 32 \iff 2^{3a+4b} = 2^5 \iff 3a + 4b = 5$, megoldás $a = 4k - 5$, $b = 5 - 3k$. Hasonlóan $27^a\cdot 81^b = 9$: $3a + 4b = 2$ ($a = 4k-2$, $b = 2-3k$); $16^a\cdot 128^b = 1024$: $4a + 7b = 10$ ($a = 20 - 7k$, $b = 4k - 10$); $64^a\cdot 512^b = 2048$: $6a + 9b = 11$, nincs megoldás, mert $3 \mid 6a + 9b$, de $3\nmid 11$.

**Tipikus hibák.** (i) A szöveges feladatnál elfelejteni a nemnegativitási feltételt, vagy a $k$-határoknál a törtrészt rosszul kerekíteni; (ii) a homogén résznél $a$ és $b$ együtthatóját nem az $(a,b)$-vel osztott értékekkel írni; (iii) negatív együtthatónál az előjelek visszaváltását kihagyni.

### ZH-példa: kutyaszánok (minta-ZH 3. feladat)

*Egy fogatot $11$ malamut vagy $13$ husky húz, összesen $360$ kutya, mindkét fajta indult. Hány malamut és husky lehetett?* Ha $m$ malamut és $h$ husky van, akkor $11m + 13h = 360$, $m, h \ge 1$. A modulo $13$ szerint $11m \equiv 360 \equiv 9$, így $m \equiv 2 \pmod{13}$ (lásd [[concepts/dimatii/linearis-kongruencia]]). Ebből $m \in \{2, 15, 28\}$ ($m = 41$ már $451 > 360$), és $h = (360 - 11m)/13$ rendre $26, 15, 4$. A megoldások: $(m,h) \in \{(2,26), (15,15), (28,4)\}$.

### További feladattípusok (2020. 2–3. feladatsor, 2024. 5–6. sorozat)

**Megoldott példák** (az $x = x_0 + b't$, $y = y_0 - a't$ alakban, $a' = a/(a,b)$, $b' = b/(a,b)$, $t \in \mathbb{Z}$; mind ellenőrizve):

| egyenlet | $(a,b)$ | megoldás |
|---|---:|---|
| $172x + 62y = 38$ | $2$ | $x = 15 + 31t$, $y = -41 - 86t$ |
| $82x + 22y = 34$ | $2$ | $x = 9 + 11t$, $y = -32 - 41t$ |
| $450x + 86y = 100$ | $2$ | $x = 5 + 43t$, $y = -25 - 225t$ |
| $125x + 45y = -20$ | $5$ | $x = 2 + 9t$, $y = -6 - 25t$ |
| $27x + 49y = 3$ | $1$ | $x = 11 + 49t$, $y = -6 - 27t$ |
| $33x + 23y = 2$ | $1$ | $x = 14 + 23t$, $y = -20 - 33t$ |
| $33x + 23y = 3$ | $1$ | $x = 21 + 23t$, $y = -30 - 33t$ |
| $27x + 35y = 3$ | $1$ | $x = 4 + 35t$, $y = -3 - 27t$ |
| $33x + 15y = 6$ | $3$ | $x = 2 + 5t$, $y = -4 - 11t$ |
| $18x + 14y = 16$ | $2$ | $x = 4 + 7t$, $y = -4 - 9t$ |
| $27x + 14y = 5$ | $1$ | $x = 9 + 14t$, $y = -17 - 27t$ |
| $105x + 40y = 15$ | $5$ | $x = 7 + 8t$, $y = -18 - 21t$ |
| $115x - 50y = 10$ | $5$ | $x = 4 - 10t$, $y = 9 - 23t$ |

Nincs megoldás ($(a,b) \nmid c$): $-135x + 70y = 12$ ($5 \nmid 12$), $117x - 90y = -6$ ($9 \nmid 6$), $78x + 93y = -10$ ($3 \nmid 10$).

**Megoldás kongruenciával** (3. feladatsor 3. feladata): $27x + 49y = 3 \Rightarrow 27x \equiv 3 \pmod{49}$, $9x \equiv 1$, $x \equiv 11 \pmod{49}$, majd $y = (3 - 27x)/49$. Ugyanígy a $33x + 23y = c$ egyenletnél $33x \equiv c \pmod{23}$, azaz $10x \equiv c$, és $10^{-1} \equiv 7 \pmod{23}$, így $x \equiv 7c$: $c = 2$-re $14$, $c = 3$-ra $21$.

**Szöveges feladatok** (nemnegatív megoldásokra szűkítve, lásd a 4. típust fent):
- *Százlábúak* ($14$ és $20$ lábú, $232$ láb): $14x + 20y = 232 \iff 7x + 10y = 116$, $x = 8 + 10t$, $y = 6 - 7t$; természetes számokra csak $t = 0$, tehát $8$ és $6$ százlábú. A 2024-es változat ($12$ és $23$ láb, $152$ láb): $12x + 23y = 152$ egyetlen természetes megoldása $x = 5$, $y = 4$ ($60 + 92$).
- *Visszajáró* ($20$ és $50$ forintos): $20x + 50y = 600 \iff 2x + 5y = 60$, $x = 30 - 5s$, $y = 2s$ ($s = 0..6$): $7$ féleképpen (a $0$ darabot is megengedve; csak pozitív darabszámmal $5$). $150$ forintra: $(0,3)$ és $(5,1)$, $2$ féleképpen.
- *Borkeverék* ($36$, $24$, $16$ Ft/l, $360$ l, $20$ Ft/l átlag): $a + b + c = 360$ és $36a + 24b + 16c = 7200$; kivonva $20\cdot$ az elsőt: $16a + 4b - 4c = 0$, $c = 4a + b$, majd $5a + 2b = 360$. $a = 2t$, $b = 180 - 5t$, $c = 180 + 3t$, $t = 1, \dots, 35$ (mindhárom fajtából pozitív mennyiség).

**Három ismeretlen.** $12x - 30y + 24z = 18$: $(12,30,24) = 6 \mid 18$, osztva $2x - 5y + 4z = 3$; $y$ páratlan, $y = 2s + 1$, így $x + 2z = 4 + 5s$, $x = 4 + 5s - 2z$. Összes megoldás: $(x,y,z) = (4 + 5s - 2z,\ 2s+1,\ z)$, $s, z \in \mathbb{Z}$. A $22x + 11y - 110z = 32$-nek nincs megoldása, mert $(22,11,110) = 11 \nmid 32$. Általában $a_1x_1 + \dots + a_nx_n = c$ pontosan akkor oldható meg, ha $(a_1,\dots,a_n) \mid c$.

**Létezési feladatok.** Minden $(m,n)$ természetes számpárhoz van olyan $ax + by = c$, amelynek az egyetlen természetes megoldása $(m,n)$, és minden $n$-hez van olyan, amelynek pontosan $n$ természetes megoldása van (a forrás 7–8. szorgalmi feladata; megoldás nincs megadva).

**Kitevők egyenlete.** A hatványegyenletek lineáris diofantikus egyenletre vezetnek: $27^a\cdot 81^b = 1/9 \iff 3a + 4b = -2$ ($a = -2 + 4t$, $b = 1 - 3t$); $32^a\cdot 128^b = 16 \iff 5a + 7b = 4$ ($a = -2 + 7t$, $b = 2 - 5t$). A komplex egyenlet, $i^a\cdot\left(\tfrac{1+i}{\sqrt 2}\right)^b = -i$: $\tfrac{1+i}{\sqrt 2} = e^{i\pi/4}$, tehát $2a + b \equiv 6 \pmod 8$ (lineáris kongruencia két ismeretlenre, $b = 6 - 2a + 8t$).

## Kapocs

- [[concepts/dimatii/linearis-kongruencia]] — az ekvivalens megfogalmazás
- [[concepts/dimatii/bovitett-euklideszi-algoritmus]] — a megoldás eszköze
- [[concepts/dimatii/kongruencia]] — a maradékos kizárás nyelve
- [[concepts/dimatii/legnagyobb-kozos-oszto]] — a megoldhatóság feltétele
- [[concepts/dimatii/szimultan-kongruenciak]] — többszörös feltételek
