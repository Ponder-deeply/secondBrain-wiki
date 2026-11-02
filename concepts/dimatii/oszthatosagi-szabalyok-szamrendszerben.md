---
tags: [concept]
sources: [dm2gy01_Szamelmelet.pdf, Lehman-Leighton-Meyer-Mathematics-for-Computer-Science.pdf]
references: [Lehman–Leighton–Meyer, Mathematics for Computer Science, 9.37 és 9.41. feladat]
derivation: source
kind: theorem
element: fire
updated: 2026-10-22
---

# Oszthatósági szabályok számrendszerben

Az oszthatósági szabályok a $b$ alapú helyi értékek maradékából következnek: ha $b \equiv r \pmod k$, akkor $\sum a_i b^i \equiv \sum a_i r^i \pmod k$.

## Tartalom

### Alapelv

Legyen $n = \sum_{i=0}^{s} a_i b^i$. Ha $b \equiv r \pmod k$, akkor a [[concepts/dimatii/kongruencia]] szorzás- és összeadástartása miatt
$$n \equiv \sum_i a_i r^i \pmod k.$$

- **$9$ és $3$:** $10 \equiv 1 \pmod 9$, tehát $n \equiv \sum a_i \pmod 9$: a szám pontosan akkor osztható $9$-cel ($3$-mal), ha a jegyek összege az.
- **$11$:** $10 \equiv -1 \pmod{11}$, tehát $n \equiv \sum (-1)^i a_i$: váltakozó előjelű jegyösszeg. A $37273761261$ váltakozó jegyösszege (balról kezdve) $3 - 7 + 2 - 7 + 3 - 7 + 6 - 1 + 2 - 6 + 1 = -11$, így a szám $11$-gyel osztható.
- **$7, 11, 13$:** $1001 = 7 \cdot 11 \cdot 13$, $1000 \equiv -1 \pmod{1001}$, tehát a számjegyek hármas csoportjainak (jobbról) váltakozó előjelű összege adja a maradékot. Ebből: ha egy háromjegyű számot kétszer egymás mellé írunk ($\overline{abcabc} = \overline{abc}\cdot 1001$), az osztható $7$-tel, $11$-gyel és $13$-mal.
- **$37$:** $999 = 27 \cdot 37$. Ha $37 \mid \overline{abc}$, akkor $\overline{bca} = 10 \cdot \overline{abc} - 999a$ is osztható $37$-tel.
- **$2, 5, 4, 8$:** $10 \equiv 0 \pmod{2}$ és $\pmod 5$, $100 \equiv 0 \pmod 4$, $1000 \equiv 0 \pmod 8$, ezért csak az utolsó egy, két, illetve három jegy számít.

### Szabály $10a + b$ alakra ($7, 11, 13, 17, 19$)

Legyen $n = 10a + b$ ($b$ az utolsó jegy). Ha $10t \equiv \pm 1$ alkalmas $t$-vel modulo $p$, akkor $n \equiv 0 \pmod p \iff a - tb \equiv 0$ (vagy $a + tb \equiv 0$). Mivel $10$ invertálható modulo $p$, szorozhatunk vele.

| $p$ | szabály | indok |
|---:|---|---|
| 7 | $a - 2b \equiv 0$ | $10(a - 2b) = 10a - 20b \equiv 10a + b \pmod 7$ |
| 11 | $a - b \equiv 0$ | $10 \equiv -1$ |
| 13 | $a + 4b \equiv 0$ | $10(a + 4b) = 10a + 40b \equiv 10a + b \pmod{13}$ |
| 17 | $a - 5b \equiv 0$ | $10(a - 5b) = 10a - 50b \equiv 10a + b \pmod{17}$ |
| 19 | $a + 2b \equiv 0$ | $10(a + 2b) = 10a + 20b \equiv 10a + b \pmod{19}$ |

### Jó modulus egy számrendszerhez

Azt mondjuk, hogy $k$ **jó modulus** a $b$ alapú számrendszerhez, ha minden $n$-re $n \equiv (\text{jegyösszeg}) \pmod k$.

**Tétel.** $k$ jó a $b$ alaphoz $\iff b \equiv 1 \pmod k$.

*($\Leftarrow)$* Ha $b \equiv 1$, akkor $b^i \equiv 1$ és $n \equiv \sum a_i$. *($\Rightarrow)$* A $b$ szám $b$ alapú alakja $10_b$, jegyösszege $1$, ezért $b \equiv 1 \pmod k$. $\square$

A tízes számrendszerben a jó modulusok a $9$ osztói ($3$ és $9$); a $2$ nem jó ($763 \not\equiv 7 + 6 + 3 \pmod 2$). A $10^6$ alapú számrendszerben $k$ jó pontosan akkor, ha $k \mid 999999 = 3^3 \cdot 7 \cdot 11 \cdot 13 \cdot 37$.

### Oszthatósági gyakorlatok

- $6 \mid n(n+1)(2n+1)$: három egymás utáni szám közt van páros, és $n(n+1)(2n+1) \bmod 3$ mind a három maradékosztályra $0$.
- $30 \mid m^5 - m$: $m^5 \equiv m$ modulo $2$, $3$ és $5$ (kis Fermat), és $2, 3, 5$ páronként relatív prímek.
- $133 \mid 11^{n+2} + 12^{2n+1}$: $11^{n+2} + 12^{2n+1} = 121 \cdot 11^n + 12 \cdot 144^n \equiv 121 \cdot 11^n + 12 \cdot 11^n = 133 \cdot 11^n \pmod{133}$ ($144 \equiv 11$).

## Kapocs

- [[concepts/dimatii/kongruencia]] — a műveletek megőrzése adja az alapelvet
- [[concepts/dimatii/szamrendszerek]] — a $b$ alapú felírás
- [[concepts/dimatii/euler-fermat-tetel]] — $m^5 \equiv m$ típusú oszthatóságok
- [[concepts/dimatii/oszthatosag]] — az oszthatóság alapfogalma
- [[concepts/dimatii/hatvanyok-periodicitasa-zm-ben]] — a $10^i$ maradékainak ciklusa
