---
tags: [concept]
sources: [DimatIIEa01.pdf, DimatIIEa02.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, Lehman-Leighton-Meyer-Mathematics-for-Computer-Science.pdf]
derivation: source
kind: theorem
element: water
updated: 2026-10-21
---

# Prímek eloszlása

Prímből végtelen sok van, sőt „sűrűn” vannak; egy adott korlátig pedig szitálással mind megkereshetők.

## Tartalom

### Végtelen sok prím van

**Tétel (Euklidész).** Végtelen sok prím van.

**Bizonyítás.** Indirekt tegyük fel, hogy csak véges sok prím van: $p_1, \dots, p_k$. Tekintsük az $n = p_1\cdots p_k + 1$ számot. Ez nem osztható egyetlen $p_1, \dots, p_k$ prímmel sem (mindegyikkel osztva $1$ maradékot ad), így $n$ prímtényezős felbontásában szerepelnie kell egy újabb prímszámnak — ellentmondás. $\square$

**Tétel (Dirichlet).** Ha $a, d$ egész számok, $d > 0$ és $(a,d) = 1$, akkor végtelen sok $a + kd$ ($k \in \mathbb{N}$) alakú prím van.

Azaz a prímek minden olyan számtani sorozatban végtelen sokan vannak, amelyben egyáltalán lehetnek.

### Mennyi prím van?

**Prímszámtétel.** Az $x$-ig lévő prímek száma aszimptotikusan $\dfrac{x}{\ln x}$.

| $x$ | prímek száma | $x/\ln x$ |
|---:|---:|---:|
| 10 | 4 | 4,343 |
| 100 | 25 | 21,715 |
| 1000 | 168 | 144,765 |
| 10000 | 1229 | 1085,736 |

Prímből tehát „sok” van: az $x$-ig lévő számoknak nagyjából $1/\ln x$ hányada prím.

### Eratoszthenész szitája

Keressük meg egy adott $n$-ig az összes prímet. Soroljuk fel $2$-től $n$-ig az egész számokat. Ekkor $2$ prím; a $2$ valódi többszörösei nem prímek, ezeket húzzuk ki. A következő ki nem húzott szám, $3$, szintén prím; a $3$ valódi többszöröseit is kihúzzuk. Ismételjük az eljárást $\sqrt{n}$-ig. A ki nem húzott számok mind prímek.

### Általánosított szita

A diák az Eratoszthenész-szitát polinomértékekre is általánosítják: legyenek $f_1(x), \dots, f_n(x)$ egész együtthatós, irreducibilis, pozitív főegyütthatós polinomok. Egy $p$ szitáló prímmel egy $f_k$ polinom értékeit szitáljuk az $1, \dots, 2^r - 1$ tartományon: ha $h$ a $p$ szerinti lineáris kongruencia kiindulópontja (az a hely, ahonnan kezdünk), akkor a $h + q\cdot p$ ($q = 0, 1, \dots$, $h + qp \le 2^r - 1$) helyeken lévő $f_k(h + qp)$ értékeket szitálhatjuk ki a $p$-vel. A kérdés a diákon: „mennyit szitálhatunk $p$-vel?” — annyit, ahány $q$-ra $h + qp \le 2^r - 1$. (A diák csak vázlatosak; a pontos feltétel nincs kimondva.)

### Nyitott problémák és becslések (Lehman–Leighton–Meyer 9.3)

**Definíció.** Prím: 1-nél nagyobb szám, amelynek csak $1$ és önmaga az osztója; a $0, 1, -1$ -től különböző nem prím szám *összetett*. A $\pi(n)$ az $n$-ig terjedő prímek száma, pl. $\pi(10) = 4$.

- **Ikerprím-sejtés:** végtelen sok $p$ prím van, amelyre $p+2$ is prím. Chen (1966): végtelen sok $p$ van, amelyre $p+2$ legfeljebb két prím szorzata.
- **Goldbach-sejtés:** minden 2-nél nagyobb páros szám két prím összege ($4 = 2+2$, $6 = 3+3$, $8 = 3+5$). Ismert: minden páros szám legfeljebb 6 prím összege.
- **A faktorizálás nehézsége:** sejtés szerint nincs polinomiális idejű eljárás $n = pq$ két nagy prímjének megtalálására (a bináris hossz, $\approx \log_2 n$ polinomja). A legjobb ismert szám­test­szita ideje $e^{1{,}9(\ln n)^{1/3}(\ln\ln n)^{2/3}}$, ami 300 jegyű $n$-re kivitelezhetetlen — az [[concepts/dimatii/rsa]] biztonsága erre épül.

**Csebisev-tétel.** $n > 1$ esetén $\pi(n) > \dfrac{n}{3\ln n}$ (a prímszámtétel gyengébb, de bizonyítható párja).

**Ökölszabály.** Az $n$ környékén kb. minden $\ln n$-edik egész prím. 10 jegyű számok között így kb. minden $\ln 10^{10} \approx 23$-adik prím — ezért nem nehéz 10 jegyű prímet találni az $e$ számjegyei között.

### Kiegészítések (előadásdiák)

*(Farkas Gábor előadásdiái, 6.1.18-20.)* Az Euklidész-bizonyítás előadásdiás változata: indirekt, legyenek $p_1,\dots,p_k$ az összes prímek, $n = \prod_{j=1}^k p_j$. A számelmélet alaptétele szerint $n + 1$-nek van prímosztója, valamely $p_j \mid n+1$; mivel $p_j \mid n$, adódik $p_j \mid 1$ — ellentmondás.

**Megjegyzés (prímmentes szakaszok).** Ha $n$ az összes, $p_k$-nál nem nagyobb prím szorzata, akkor $n+2, n+3, \dots, n+p_k$ mind összetettek, mert a $2 \leq j \leq p_k$ számnak van $q \leq p_k$ prímosztója, amely $n$-t és $j$-t is osztja, tehát $n + j$-t is, és $n + j > q$. Így a természetes számok sorozatában $p_k - 1$ egymás utáni összetett szám van; mivel tetszőlegesen nagy prím létezik, **akármilyen hosszú csupa összetett számot tartalmazó intervallum van**.

**Megjegyzés (elég sok prím).** Megmutatható, hogy a prímszámok reciprokainak összege végtelen. A prímszámtétel pontos alakja:
$$\lim_{x\to\infty} \frac{|\{p : p \leq x,\ p \text{ prím}\}|}{x/\ln x} = 1.$$

### Prímtesztelés (Lehman–Leighton–Meyer 9.5)

$n$ prím $\iff$ nem osztható $2$ és $\lfloor\sqrt n\rfloor$ közötti számmal. Ez a próbaosztás azonban a számjegyek számában exponenciális lépést igényel. Strassen (1974) gyors *valószínűségi* tesztje prímre mindig helyes választ ad, összetett számra kis valószínűséggel téved; Agrawal–Kayal–Saxena (2002) polinomidejű, determinisztikus tesztet adott (kezdetben 12-ed fokú, később 5-ödfokú korláttal). A gyakorlatban mégis a valószínűségi tesztek maradtak. A Riemann-sejtés ($\zeta(s) = \sum n^{-s} = \prod_p (1 - p^{-s})^{-1}$ nemtriviális zérushelyei az $s = 1/2 + ci$ egyenesen vannak) a prímeloszlás finomabb alakját adná; a tananyagnak nem része.

## Kapocs

- [[concepts/dimatii/felbonthatatlan-es-prim]] — a prímszám fogalma
- [[concepts/dimatii/szamelmelet-alaptetele]] — az Euklidész-bizonyítás eszköze
- [[concepts/dimatii/legnagyobb-kozos-oszto]] — a Dirichlet-tételben szereplő relatív prím feltétel
- [[concepts/dimatii/rsa]] — a faktorizálás nehézsége és a nagy prímek keresése
