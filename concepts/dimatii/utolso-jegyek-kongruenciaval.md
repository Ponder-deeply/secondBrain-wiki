---
tags: [concept]
sources: [dimat2gyak04mo.pdf, Dimat2mintaZH1.pdf, dm2gy04_Szamelmelet.pdf, dm2gy06.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-22
---

# Utolsó jegyek feltétele kongruenciával

Az „$a$-szorosának $b$-s számrendszerbeli utolsó két jegye $u$ és $v$” feltétel egyetlen kongruencia modulo $b^2$, amelyet a lineáris kongruenciák módszerével oldunk meg.

## Tartalom

### A visszavezetés

Egy szám $b$ alapú felírásának utolsó jegye a $b$ szerinti maradéka, az utolsó két jegye a $b^2$ szerinti maradéka. Ha $kx$ utolsó előtti jegye $u$, utolsó jegye $v$, akkor
$$kx \equiv u \cdot b + v \pmod{b^2}.$$
Ez az egy kongruencia az utolsó jegyre vonatkozó $kx \equiv v \pmod b$ feltételt is tartalmazza. Ha az utóbbinak nincs megoldása, akkor az egésznek sincs.

A megoldás a [[concepts/dimatii/linearis-kongruencia]] szerint $x \equiv x_0 \pmod{b^2/(k,b^2)}$ alakú maradékosztály (ha $(k,b^2) \mid ub+v$), a két legkisebb pozitív megoldás $x_0$ és $x_0 + $ a modulus.

**Két lépcsős alternatíva.** Először az utolsó jegyre oldjuk meg: $kx \equiv v \pmod b$, azaz $x = x_1 + bn$; ezt behelyettesítve a $\bmod\ b^2$ kongruenciába $n$-re kapunk kongruenciát. Vigyázat: egyszerűsítéskor a modulust is osztani kell a közös osztóval, és csak a modulushoz relatív prím számmal szabad egyszerűsíteni.

### Példák

**$13x$, hetes számrendszer, jegyek $4,3$.** $13x \equiv 4 \cdot 7 + 3 = 31 \pmod{49}$. $13 \equiv -36$ és $31 \equiv -18$, ezért $-36x \equiv -18$, egyszerűsítve ($(18,49) = 1$) $2x \equiv 1 \equiv 50 \pmod{49}$, tehát $x \equiv 25 \pmod{49}$. A két legkisebb: $25$ és $74$.

**$12x$, nyolcas számrendszer, jegyek $2,1$.** Az utolsó jegyre $12x \equiv 1 \pmod 8$, azaz $4x \equiv 1$, de $4x$ páros, $1$ páratlan: **nincs megoldás.** (Ugyanez a ZH-mintában.) Indok: $12x$ páros, a nyolcas számrendszerben pedig a szám paritása az utolsó jegyé.

**$14x$, tizenhatos számrendszer, jegyek $3,4$.** $14x \equiv 3 \cdot 16 + 4 = 52 \pmod{256}$. Mindkét oldalt és a modulust $2$-vel osztva $7x \equiv 26 \equiv 154 = 7 \cdot 22 \pmod{128}$, és $(7,128) = 1$, így $x \equiv 22 \pmod{128}$. A két legkisebb: $22$ és $150$. (Ellenőrzés: $14 \cdot 22 = 308 = 134_{16}$.)

Figyelmeztetés: a $112n \equiv 224 \pmod{256}$ alakú kongruenciát nem szabad $112$-vel egyszerűsíteni, mert $112 = 16 \cdot 7$ nem relatív prím a $256$-hoz, és nem is osztója: először $16$-tal egyszerűsítünk (a modulust is osztva), $7n \equiv 14 \pmod{16}$, aztán $7$-tel.

### További feladatok megoldásai

- $7x$ nyolcas számrendszerben $43$-ra végződik: $7x \equiv 35 \pmod{64}$, $7^{-1} \equiv 55$, $x \equiv 5$. A két legkisebb: $5$ és $69$.
- $13x$ négyes számrendszerben $21$-re végződik: $13x \equiv 9 \pmod{16}$, $13^{-1} \equiv 5$, $x \equiv 13$. A két legkisebb: $13$ és $29$.
- $19x$ tizenhatos számrendszerben $12$-re végződik: $19x \equiv 18 \pmod{256}$, $19^{-1} \equiv 27$, $x \equiv 230$. A két legkisebb: $230$ és $486$.
- A száznál kisebb $x$, melyre $23x$ hetes számrendszerben $25$-re végződik: $23x \equiv 19 \pmod{49}$, $x \equiv 20 \pmod{49}$, tehát $x = 20$ vagy $x = 69$.
- A legkisebb szám, amely $28$-as alapban $3$-ra, $19$-es alapban $4$-re végződik: $n \equiv 3 \pmod{28}$, $n \equiv 4 \pmod{19}$, a [[concepts/dimatii/kinai-maradektetel]] szerint $n \equiv 479 \pmod{532}$, tehát $479$.
- A $463$ felbontása egy $14$-gyel és egy $23$-mal osztható szám összegére: $463 = 14a + 23b$. Modulo $23$: $14a \equiv 463 \equiv 3$, $14^{-1} \equiv 5$ (mert $14\cdot5 = 70 \equiv 1$), így $a \equiv 15$, $a = 15$ és $b = (463 - 210)/23 = 11$. A felbontás $463 = 210 + 253$.

## Kapocs

- [[concepts/dimatii/szamrendszerek]] — a $b$ alapú felírás és a jegyek maradékos értelmezése
- [[concepts/dimatii/linearis-kongruencia]] — a megoldás módszere, egyszerűsítés a modulus osztásával
- [[concepts/dimatii/kongruencia]] — az egyszerűsítési tétel
- [[concepts/dimatii/kinai-maradektetel]] — két számrendszer jegyfeltétele egyszerre
- [[concepts/dimatii/hatvanytorony-modulo-szamitasa]] — hatványok utolsó jegyei
