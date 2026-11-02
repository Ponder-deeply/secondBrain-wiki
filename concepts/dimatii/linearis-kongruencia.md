---
tags: [concept]
sources: [DimatIIEa02.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, dimat2gyak04mo.pdf, dimat2gyak02mo.pdf, Dimat2mintaZH1.pdf, dm2gy03_Szamelmelet.pdf, dm2gy05.pdf, dm2gy06.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-21
---

# Lineáris kongruencia

Az $ax \equiv b \pmod m$ alakú egyenlet: mikor oldható meg, hány megoldása van, és hogyan találjuk meg őket próbálgatás nélkül.

## Tartalom

### A probléma

Oldjuk meg a $2x \equiv 5 \pmod 7$ kongruenciát! Ha $x$ megoldás és $x \equiv y \pmod 7$, akkor $y$ is megoldás, tehát elég a $\{0,1,\dots,6\}$ halmazon keresni. Végigpróbálva $x = 6$ az egyetlen megoldás a halmazban, így a kongruencia megoldása $\{6 + 7\ell \,:\, \ell \in \mathbb{Z}\}$.

Próbálgatás azonban nem járható út: a $23x \equiv 4 \pmod{211}$ kongruenciához 211 próbára lenne szükség.

### A megoldhatóság tétele

**Tétel.** Legyenek $a, b, m$ egészek, $m > 1$. Ekkor az $ax \equiv b \pmod m$ kongruencia pontosan akkor oldható meg, ha $(a,m) \mid b$. Ebben az esetben pontosan $(a,m)$ darab inkongruens megoldás van modulo $m$.

**Bizonyítás.** $ax \equiv b \pmod m \iff ax + my = b$ valamely $y$ egészre. Mivel $(a,m) \mid a$ és $(a,m) \mid m$, ezért $(a,m) \mid b \iff (a,m) \mid ax + my$.

Legyen $d = (a,m)$, és legyen $a' = a/d$, $b' = b/d$, $m' = m/d$: ekkor $a'x + m'y = b'$. Mivel $(a', m') = 1$, a [[concepts/dimatii/bovitett-euklideszi-algoritmus]]sal kiszámolható $x_0, y_0$, melyekre $a'x_0 + m'y_0 = 1$. Ekkor $a'(b'x_0) + m'(b'y_0) = b'$, azaz $x_1 = b'x_0$, $y_1 = b'y_0$ megoldás.

*A megoldások száma*: legyenek $x$, illetve $y$ megoldások. Az $a'x + m'y = b'$ és $a'x_1 + m'y_1 = b'$ egyenletek kivonva egymásból $a'(x - x_1) = m'(y_1 - y)$, ahonnan $m' \mid x - x_1$, azaz $x = x_1 + m'k$. A $k = 0, 1, \dots, d-1$ választások adják a modulo $m$ inkongruens megoldásokat. $\square$

### A megoldás menete

1. $ax \equiv b \pmod m \iff ax + my = b$.
2. Oldjuk meg az $ax + my = (a,m)$ egyenletet a [[concepts/dimatii/bovitett-euklideszi-algoritmus]]sal.
3. Ha $(a,m) \mid b$, akkor van megoldás.
4. A megoldások: $x_i = \dfrac{b}{(a,m)}\,x + k\dfrac{m}{(a,m)}$, ahol $k = 0, 1, \dots, (a,m)-1$.

**Példa.** Oldjuk meg a $23x \equiv 4 \pmod{211}$ kongruenciát!

| $i$ | $r_i$ | $q_i$ | $x_i$ |
|---:|---:|---:|---:|
| $-1$ | 23 | — | 1 |
| 0 | 211 | 0 | 0 |
| 1 | 23 | 0 | 1 |
| 2 | 4 | 9 | $-9$ |
| 3 | 3 | 1 | 46 |
| 4 | 1 | 1 | $-55$ |
| 5 | 0 | 3 | — |

$(23,211) = 1 \mid 4$, tehát van megoldás. Egy megoldás: $x = 4\cdot(-55) \equiv 202 \pmod{211}$. Összes megoldás: $\{202 + 211\ell \,:\, \ell \in \mathbb{Z}\}$. Ellenőrzés: $23\cdot(202 + 211\ell) - 4 = 4642 + 211\cdot 23\ell = (22 + \ell)\cdot 211$.

**Példa (több megoldás).** Oldjuk meg a $10x \equiv 8 \pmod{22}$ kongruenciát! A bővített euklideszi algoritmus $x_0 = -2$-t ad, $(10,22) = 2 \mid 8$, tehát két megoldás van modulo $22$:
$$x_1 = 4\cdot(-2) \equiv 14 \pmod{22}, \qquad x_2 = 4\cdot(-2) + \tfrac{22}{2} \equiv 14 + 11 \equiv 3 \pmod{22}.$$
Összes megoldás: $\{14 + 22\ell\} \cup \{3 + 22\ell\}$. Ellenőrzés: $10\cdot 14 - 8 = 132 = 6\cdot 22$, $10\cdot 3 - 8 = 22 = 1\cdot 22$.

Alternatív megoldási út: ha $(a,m) = 1$, az [[concepts/dimatii/euler-fermat-tetel]] szerint mindkét oldalt $a^{\varphi(m)-1}$-nel szorozva közvetlenül adódik $x$.

### Feladattípusok és módszerek (gyakorlat 4.)

**Módszer.** $ax \equiv b \pmod m \iff \exists y:\ ax + my = b$. A bővített euklideszi algoritmus adja $ax + my = (a,m)$-et; $b/(a,m)$-vel szorozva részmegoldás, majd hozzáadjuk a homogén $a\cdot(mk') + m\cdot(-ak') = 0$ típusú megoldást; a végén $x$-et modulo $m$ tekintjük.

| kongruencia | megoldás |
|---|---|
| $3x \equiv 1 \pmod 7$ | $x \equiv 5$ ($3\cdot(-2) + 7 = 1$) |
| $3x \equiv 1 \pmod 8$ | $x \equiv 3$ |
| $2x \equiv 1 \pmod 8$, $4x \equiv 2 \pmod 8$ | nincs ($2x + 8y$ páros; $4x + 8y$ osztható $4$-gyel, $(a,m) \nmid b$) |
| $31x \equiv 4 \pmod{17}$ | $x \equiv 10$ ($31\cdot(-6) + 17\cdot 11 = 1$) |
| $31x \equiv 4 \pmod{117}$ | $x \equiv 19$ ($31\cdot 34 + 117\cdot(-9) = 1$) |
| $17x \equiv 4 \pmod{2024}$ | $x \equiv 1548$ ($17\cdot(-119) + 2024 = 1$; ellenőrzés: $17\cdot 1548 = 26316 = 13\cdot 2024 + 4$) |

**Több megoldás.** $5x \equiv 10 \pmod{15}$: $(5,15) = 5 \mid 10$, tehát $5$ inkongruens megoldás van. Részmegoldás $x = -4$, a homogén rész $3k$: $x = 3k - 4$, és $k = 2,3,4,5,6$ esetén $x \equiv 2, 5, 8, 11, 14 \pmod{15}$; $k = 7$-től a megoldások ismétlődnek (pontosan $(a,m)$ osztály).

**Inverz keresése.** $a^{-1} \bmod m$ az $ax \equiv 1 \pmod m$ megoldása, létezik $\iff (a,m) = 1$: $3^{-1} \equiv 5 \pmod 7$, $3^{-1} \equiv 3 \pmod 8$, $2^{-1} \equiv 4 \pmod 7$, $2^{-1} \equiv 2 \pmod 3$, $31^{-1} \equiv 11 \pmod{17}$; $0^{-1}$ és $2^{-1} \bmod 8$ nem létezik. Lásd [[concepts/dimatii/invertalhatosag-zm-ben]].

**Számjegyfeladat (egymásba ágyazott kongruenciák).** „Melyik két legkisebb pozitív $x$, amelynek $13$-szorosa $7$-es számrendszerben ...$43$-ra végződik?" Ez $13x \equiv 3 \pmod 7$ (utolsó jegy) és $13x \equiv 4\cdot 7 + 3 \pmod{49}$ (utolsó két jegy). A második kongruencia implikálja az elsőt, elég azt megoldani: $13 \equiv -36$, $31 \equiv -18 \pmod{49}$, így $-36x \equiv -18$, $2x \equiv 1 \pmod{49}$, $x \equiv 25 \pmod{49}$: $x = 25$ és $74$. Alternatív: két lépésben, előbb mod $7$ ($x \equiv 4$), majd $x = 7n + 4$ behelyettesítésével $n \equiv 3 \pmod 7$, $x = 49k + 25$.
- Mod $8$ ($12x$, utolsó jegy $1$): $4x \equiv 1 \pmod 8$ — nincs megoldás ($12x$ páros, az utolsó jegy $1$ páratlan).
- Mod $16$ ($14x$ utolsó két jegye $34_{16}$, azaz $14x \equiv 3\cdot 16 + 4 \pmod{256}$): $x = 22$ és $150$ ($14\cdot 150 = 2100 = 834_{16}$, $14\cdot 22 = 308 = 134_{16}$). Lásd [[concepts/dimatii/szamrendszerek]].

**Tipikus hibák.**
- Kongruenciában egyszerűsíteni szabad $d$-vel, ha a **modulust is** osztjuk $m/(d,m)$-re: $-2x \equiv 4 \pmod{16} \Rightarrow -x \equiv 2 \pmod 8$.
- Ha a modulus nem relatív prím az egyszerűsítő számhoz, a modulust nem szabad érintetlenül hagyni: $112n \equiv -32 \pmod{256}$-nál a $112$-vel való egyszerűsítés tilos ($112 = 16\cdot 7$ nem relatív prím $256$-hoz); előbb $16$-tal egyszerűsítünk (modulus is: $7n \equiv -2 \pmod{16}$), majd $7$-tel (relatív prím).
- Elfelejteni, hogy a megoldás maradékosztály: $x = 3k - 4$ több osztályt ad modulo $15$.

### Feladattípusok és módszerek (gyakorlat 2., minta-ZH 2a)

**1. Kis modulus: teljes maradékrendszer végigpróbálása** (a nem lineáris kongruenciákhoz is):
- $2x \equiv 1 \pmod 4$: nincs megoldás, mert $2x$ mindig páros ($2(x-2k) = 1$ ellentmondás); $2x \equiv 2 \pmod 4 \iff x \equiv 1 \pmod 2$, azaz $x = 2k+1$.
- $x(x-2) \equiv 0 \pmod 8$: végigpróbálva $x \in \{2,4,6,8\}$ (mod 8), azaz $x$ páros. Indok: páratlan $x$-re a szorzat páratlan; $x = 2k$-ra $x(x-2) = 4k(k-1)$, és $k(k-1)$ páros.
- $x^2 \equiv 1 \pmod 5$: $x \equiv \pm1$; $x^2 \equiv 1 \pmod 6$: $x \equiv \pm1 \pmod 6$; $x^4 \equiv 1 \pmod 5$: minden $5 \nmid x$ (ez az [[concepts/dimatii/euler-fermat-tetel]] speciális esete).

**2. $ax \equiv b \pmod m$ relatív prím $a$-val egyszerűsítve:** $2x \equiv 1 \equiv 4 \pmod 3$ miatt $x \equiv 2 \pmod 3$ (mivel $(2,3) = 1$, osztani szabad).

**Minta-ZH 2a.** $11x \equiv 360 \pmod{13}$: $360 \equiv 9$, $11 \equiv -2$, így $-2x \equiv 9$, $2x \equiv 4$, $x \equiv 2 \pmod{13}$ (ellenőrzés: $22 \equiv 9$). $13y \equiv 360 \pmod{11}$: $13 \equiv 2$, $360 \equiv 8$, $2y \equiv 8$, $y \equiv 4 \pmod{11}$ (ellenőrzés: $52 \equiv 8$). Az $x \equiv 2 \pmod{13}$ eredmény a ZH 3. feladatában is felhasználható ([[concepts/dimatii/linearis-diofantikus-egyenlet]]).

**Tipikus hibák:** modulo nem relatív prím együtthatóval osztani ($(a,m) \nmid b$ esetén nincs megoldás); a megoldást egyetlen maradékként megadni a teljes $x = x_0 + m k$ osztály helyett.

### További feladattípusok (2020. 3. feladatsor, 2024. 5–6. sorozat)

**Megoldás $(a,m)$ szerint.** Az $ax \equiv b \pmod m$ esetén $d = (a,m)$; $d \nmid b$ esetén nincs megoldás, különben $d$-vel osztva $a'x \equiv b' \pmod{m'}$ ($m' = m/d$) egyetlen osztályt ad mod $m'$, ami mod $m$ $d$ megoldás. A 3. feladatsor 1. feladata:

| kongruencia | $d$ | megoldás |
|---|---:|---|
| $21x \equiv 14 \pmod{35}$ | $7$ | $x \equiv 4 \pmod 5$ ($7$ osztály mod $35$) |
| $172x \equiv 6 \pmod{62}$ | $2$ | $x \equiv 4 \pmod{31}$ |
| $3x \equiv 8 \pmod{13}$ | $1$ | $x \equiv 7 \pmod{13}$ |
| $12x \equiv 9 \pmod{18}$ | $6$ | nincs ($6 \nmid 9$) |
| $26x \equiv 12 \pmod{22}$ | $2$ | $x \equiv 3 \pmod{11}$ |
| $20x \equiv 19 \pmod{22}$ | $2$ | nincs ($2 \nmid 19$) |
| $16x \equiv 36 \pmod{28}$ | $4$ | $x \equiv 4 \pmod 7$ |
| $126x \equiv 46 \pmod{99}$ | $9$ | nincs ($9 \nmid 46$) |

A 2024. 5. sorozat 1. feladata (Euler–Fermat-tétellel is, lásd [[concepts/dimatii/euler-fermat-tetel]]): $2x \equiv 1 \pmod 7$: $x \equiv 4$; $3x \equiv 2 \pmod{11}$: $x \equiv 8$; $5x \equiv 3 \pmod 8$: $x \equiv 7$; $6x \equiv 3 \pmod{15}$: $x \equiv 3 \pmod 5$; $14x \equiv 2 \pmod{13}$: $x \equiv 2$; $5x \equiv 3 \pmod{33}$: $x \equiv 27$; $15x \equiv 12 \pmod{42}$: $x \equiv 12 \pmod{14}$. A 6. sorozat 10. feladata: $13x \equiv 1 \pmod{17}$: $x \equiv 4$; $12x \equiv 18 \pmod{15}$: $x \equiv 4 \pmod 5$; $7x \equiv 21 \pmod{42}$: $x \equiv 3 \pmod 6$; $51x \equiv 69 \pmod{152}$: $x \equiv 55$; $5x \equiv 1 \pmod{25}$: nincs; $31x \equiv 18 \pmod{17}$: $x \equiv 11$; $11x \equiv 21 \pmod{120}$: $x \equiv 111$; $65x \equiv 91 \pmod{117}$: $x \equiv 5 \pmod 9$.

**Két kongruencia ekvivalenciája** (3. feladatsor 2. feladata). Módszer: mindkettőt megoldjuk (vagy $d$-vel egyszerűsítjük a modulussal együtt), és a megoldáshalmazokat hasonlítjuk. Ha az egyik megoldáshalmaza része a másikénak, az egyik implikálja a másikat. Eredmények:

| kongruenciapár | viszony |
|---|---|
| $44x \equiv 100 \pmod{80}$ és $11x \equiv 25 \pmod{20}$ | ekvivalensek (mind a három szám osztható $4$-gyel) |
| $12x \equiv 72 \pmod{18}$ és $3x \equiv 18 \pmod 9$ | ekvivalensek ($x \equiv 0 \pmod 3$) |
| $39x \equiv 78 \pmod{26}$ és $-x \equiv -2 \pmod 2$ | ekvivalensek ($x$ páros) |
| $14x \equiv 91 \pmod{21}$ és $2x \equiv 13 \pmod{21}$ | csak a második $\Rightarrow$ az első: $x \equiv 17 \pmod{21}$ részhalmaza $x \equiv 2 \pmod 3$-nak |
| $12x \equiv 92 \pmod 8$ és $72x \equiv 552 \pmod{16}$ | ekvivalensek ($x$ páratlan) |
| $-5x \equiv 17 \pmod 4$ és $-40x \equiv 136 \pmod{16}$ | csak az első $\Rightarrow$ a második: $x \equiv 3 \pmod 4$ részhalmaza az $x$ páratlannak |
| $21x \equiv 84 \pmod{20}$ és $x \equiv 4 \pmod{20}$ | ekvivalensek ($21 \equiv 1$) |
| $26x \equiv 78 \pmod{22}$ és $x \equiv 3 \pmod{11}$ | ekvivalensek |

**Hatványból az alap.** Ha $n^{100} \equiv 57$ és $n^{101} \equiv 11 \pmod{73}$, akkor $n \cdot 57 \equiv 11 \pmod{73}$; a $73$ prím, így $57$ invertálható, és $x \equiv 13$. Ellenőrzés: $13^{100} \equiv 57$, $13^{101} \equiv 11 \pmod{73}$.

**Számjegyfeladatok a 6. sorozatból** ($x$ a két legkisebb pozitív megoldás; módszer: a két utolsó jegy az $x$-szorosának $\bmod\ b^2$ maradéka):
- $7x$ oktálisan $\ldots 43_{(8)}$: $7x \equiv 4\cdot 8 + 3 = 35 \pmod{64}$, $x \equiv 5 \pmod{64}$: $x = 5, 69$.
- $13x$ négyes alapon $\ldots 21_{(4)}$: $13x \equiv 2\cdot 4 + 1 = 9 \pmod{16}$, $x \equiv 13 \pmod{16}$: $x = 13, 29$.
- $19x$ hexadecimálisan $\ldots 12_{(16)}$: $19x \equiv 18 \pmod{256}$, $x \equiv 230 \pmod{256}$: $x = 230, 486$.

## Kapocs

- [[concepts/dimatii/kongruencia]] — az alapfogalom
- [[concepts/dimatii/bovitett-euklideszi-algoritmus]] — a megoldás eszköze
- [[concepts/dimatii/legnagyobb-kozos-oszto]] — a megoldhatóság feltétele
- [[concepts/dimatii/linearis-diofantikus-egyenlet]] — ugyanez egészegyenletként
- [[concepts/dimatii/szimultan-kongruenciak]] — több lineáris kongruencia együtt
- [[concepts/dimatii/euler-fermat-tetel]] — alternatív megoldási módszer

