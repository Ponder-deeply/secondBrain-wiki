---
tags:
  - concept
sources:
  - DimatIIEa02.pdf
  - Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf
  - Lehman-Leighton-Meyer-Mathematics-for-Computer-Science.pdf
  - dimat2gyak04mo.pdf
  - dm2gy05.pdf
derivation: source
kind: definition
element: fire
updated: 2026-10-21
studied: true
---

# Euler-féle $\varphi$ függvény

A modulushoz relatív prím maradékok száma — egyben a redukált maradékosztályok száma modulo $m$.

## Tartalom

**Definíció.** Egy $m > 0$ egész szám esetén legyen $\varphi(m)$ az $m$-nél kisebb, hozzá relatív prím pozitív egészek száma:
$$\varphi(m) = |\{i \,:\, 0 < i < m,\ (m,i) = 1\}|.$$

**Példák.** $\varphi(5) = 4$ ($1,2,3,4$); $\varphi(6) = 2$ ($1,5$); $\varphi(12) = 4$ ($1,5,7,11$); $\varphi(15) = 8$ ($1,2,4,7,8,11,13,14$).

**Megjegyzés.** $\varphi(m)$ éppen a redukált maradékosztályok száma modulo $m$, azaz $|\mathbb{Z}_m^*|$ — lásd [[concepts/dimatii/redukalt-maradekrendszer]].

### Kiszámítása a kanonikus alakból

**Tétel.** Legyen $m$ prímtényezős felbontása $m = p_1^{e_1}p_2^{e_2}\cdots p_\ell^{e_\ell}$. Ekkor
$$\varphi(m) = \prod_{i=1}^{\ell}\left(p_i^{e_i} - p_i^{e_i - 1}\right) = m\prod_{i=1}^{\ell}\left(1 - \frac{1}{p_i}\right).$$

Következmények:

- ha $a_1, \dots, a_r$ páronként relatív prímek, akkor $\varphi(a_1\cdots a_r) = \varphi(a_1)\cdots\varphi(a_r)$ (a $\varphi$ multiplikatív);
- ha $p$ prím, akkor $\varphi(p^m) = p^m - p^{m-1}$; speciálisan $\varphi(p) = p - 1$.

### A multiplikativitás bizonyítása

Legyen $(a,b) = 1$. Írjuk fel $1, \dots, ab$ számait $b$ sorba, soronként $a$ elemmel: az $i$-edik sor $(i-1)a+1, \dots, ia$. Megszámoljuk, hány elem relatív prím $ab$-hez, vagyis (6.1.22. következmény) $a$-hoz és $b$-hez is.

- Egy oszlop elemei kongruensek mod $a$, így egy oszlop vagy végig relatív prím $a$-hoz, vagy végig nem.
- Minden sor teljes maradékrendszer mod $a$, ezért pontosan $\varphi(a)$ oszlop elemei relatív prímek $a$-hoz.
- Az omnibusz-tétel szerint $(a,b) = 1$ esetén minden oszlop teljes maradékrendszer mod $b$ (lásd [[concepts/dimatii/teljes-maradekrendszer]]), így minden ilyen oszlopban $\varphi(b)$ elem relatív prím $b$-hez.

Összesen $\varphi(a)\varphi(b)$ szám relatív prím $ab$-hez, azaz $\varphi(ab) = \varphi(a)\varphi(b)$. A kiszámítási képlet ebből adódik: $\varphi(p^\alpha) = p^\alpha - p^{\alpha-1}$ (az $1, \dots, p^\alpha$ között a $p$ többszörösei, $p^{\alpha-1}$ darab, nem relatív prímek $p$-hez), majd a prímhatványokra szorzunk. A $\varphi$ nem totálisan multiplikatív. Általános keret: [[concepts/dimatii/szamelmeleti-fuggvenyek]].

**Példák.**
$$\varphi(5) = 5\left(1 - \tfrac15\right) = 4, \quad \varphi(6) = 6\left(1-\tfrac12\right)\left(1-\tfrac13\right) = 2,$$
$$\varphi(12) = 12\left(1-\tfrac12\right)\left(1-\tfrac13\right) = 4, \quad \varphi(15) = 15\left(1-\tfrac13\right)\left(1-\tfrac15\right) = 8.$$

### Másik megfogalmazás és kis értékek (Farkas-diák)

Az $m>0$ modulusú definíció másképp: $\varphi(n) = \sum_{\substack{1\le k\le n\\ (k,n)=1}} 1$, azaz az $n$-nél nem nagyobb, hozzá relatív prím pozitív egészek száma. Ezzel $\varphi(1) = 1$ (a diák szerint „sic!”: $(1,1)=1$), $\varphi(2)=1$, $\varphi(3)=2$, $\varphi(4)=2$, $\varphi(5)=4$, $\varphi(6)=2$, $\varphi(7)=6$, $\varphi(8)=4$.

*Megjegyzés:* a fenti definíció „$0<i<m$” alakja $m=1$-re üres halmazt adna; a $\varphi(1)=1$ a $k\le n$ alakból adódik.

### $\varphi(pq)$ és a képlet levezetése (Lehman–Leighton–Meyer 9.10)

**Lemma.** Különböző $p, q$ prímekre $\varphi(pq) = (p-1)(q-1)$.

*Bizonyítás.* A $[0, pq)$-ban a $pq$-hoz nem relatív prímek a $p$ vagy $q$ többszörösei: $q$ db $p$-többszörös és $p$ db $q$-többszörös van, és az egyetlen közös a $0$. Így $p+q-1$ szám nem relatív prím, és $\varphi(pq) = pq - (p+q-1) = (p-1)(q-1)$. $\square$

**Tétel.** (a) $\varphi(p^k) = p^k - p^{k-1} = p^k(1 - 1/p)$, mert a $[0,p^k)$-ban a $p$ többszöröseinek aránya $1/p$; (b) $(a,b)=1 \Rightarrow \varphi(ab) = \varphi(a)\varphi(b)$. Ebből $\varphi(n) = n\prod_{p\mid n}(1 - 1/p)$.

**Példa.** $\varphi(300) = \varphi(2^2)\varphi(3)\varphi(5^2) = (4-2)(3-1)(25-5) = 2\cdot 2\cdot 20 = 80$.

**Megjegyzés.** Az $n$ prímtényezős felbontásának ismerete nélkül $\varphi(n)$ kiszámítása nehéz — ezért marad az inverz számítására az [[concepts/dimatii/bovitett-euklideszi-algoritmus]] a leghatékonyabb, és ezen alapul az [[concepts/dimatii/rsa]] biztonsága.

### Kis értékek táblázata (gyakorlat 4.)

Kézi számolásnál $m \le 9$-ig megszámoljuk a relatív prímeket, nagyobb $m$-re a $m\prod(1 - 1/p)$ képlet kényelmesebb.

| $m$ | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 | 16 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| $\varphi(m)$ | 1 | 1 | 2 | 2 | 4 | 2 | 6 | 4 | 6 | 4 | 10 | 4 | 12 | 6 | 8 | 8 |

Például $\varphi(12) = 12\cdot\tfrac12\cdot\tfrac23 = 4$, $\varphi(16) = 16\cdot\tfrac12 = 8$, $\varphi(p) = p - 1$. Az $m > 1$ esetben a definíció a $\{1,\dots,m-1\}$ halmazra is szűkíthető ($m$ nem relatív prím önmagához), $m = 1$-re viszont $\varphi(1) = 1$ miatt nem. Alkalmazás: kitevő-redukció, lásd [[concepts/dimatii/euler-fermat-tetel]].

### Alkalmazás: ülésrend-feladat (2024. 5. sorozat 9. feladata, szorgalmi)

A feladat: $100$ vendég kerek asztalnál, minden este mindenki új szomszédokat kap; a forrás szerint $\varphi(100)/2 = 20$ éjszaka megoldható. *Saját kidolgozás* (a forrás csak a feladatot adja): a vendégeket $0, \dots, 99$ sorszámozzuk; ha $(k, 100) = 1$, a $0, k, 2k, \dots$ sorrend (mod $100$) mind a $100$ vendéget egyszer ülteti le, és a szomszédok különbsége $\pm k$. A $\varphi(100) = 40$ érték $k$-ra a $\pm k$ párok miatt $20$ lényegesen különböző éjszakát ad, és két különböző $\{\pm k\}$ osztályhoz tartozó szomszédpár soha nem esik egybe.

## Kapocs

- [[concepts/dimatii/redukalt-maradekrendszer]] — a megszámolt osztályok
- [[concepts/dimatii/euler-fermat-tetel]] — a $\varphi$ fő alkalmazása
- [[concepts/dimatii/szamelmelet-alaptetele]] — a képlet alapja
- [[concepts/dimatii/osztok-szama]] — másik, kanonikus alakból számolható függvény
- [[concepts/dimatii/invertalhatosag-zm-ben]] — az invertálható osztályok száma $\varphi(m)$
- [[concepts/dimatii/hatvanytorony-modulo-szamitasa]] — a $\varphi$ értékek a kitevő redukálásához
