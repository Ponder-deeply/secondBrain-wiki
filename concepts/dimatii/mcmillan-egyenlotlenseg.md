---
tags: [concept]
sources: [DimatIIEa08.pdf]
derivation: source
updated: 2026-09-08
---

# McMillan-egyenlőtlenség

Pontos feltétel arra, hogy adott szóhosszakkal létezzék felbontható betűnkénti kódolás — és a feltétel teljesülése esetén már prefix kód is létezik ugyanezekkel a hosszakkal.

## Tartalom

### A tétel

Legyen $A = \{a_1, a_2, \dots, a_n\}$ és $B$ két ábécé, $B$ elemeinek száma $r \ge 2$, továbbá $\varphi : A \to B^+$ injektív leképezés. Ha a $\varphi$ által meghatározott betűnkénti kódolás felbontható, akkor az $\ell_j = |\varphi(a_j)|$ jelöléssel
$$\sum_{j=1}^n \frac{1}{r^{\ell_j}} \le 1 .$$

### A megfordítás

Az előző tétel jelöléseit használva: ha $\ell_1, \ell_2, \dots, \ell_n$ olyan pozitív egész számok, hogy
$$\sum_{j=1}^n r^{-\ell_j} \le 1,$$
akkor van az $A$-nak a $B$ elemeivel való olyan felbontható — sőt prefix — kódolása, amelyben az $a_j$ betű kódjának hossza $\ell_j$.

### Jelentősége

A két állítás együtt azt mondja ki, hogy a szóhosszak szempontjából a felbontható és a prefix kódok között nincs különbség: ha valamilyen szóhosszakat egy felbontható kód megvalósít, akkor ugyanazokat egy prefix kód is megvalósítja. A prefix kódok tehát nem szűkítik a lehetőségeket, viszont a dekódolás náluk sokkal kényelmesebb.

Ez az egyenlőtlenség a kulcs a szóhosszakra vonatkozó alsó és felső korlátok igazolásához is: a Shannon-tétel bizonyítása közvetlenül erre épül, a Shannon-kód létezése pedig a megfordítására.

## Kapocs

- [[concepts/dimatii/prefix-kod]] — a kódosztály, amelyre a megfordítás konstrukciót ad
- [[concepts/dimatii/betunkenti-kodolas]] — a felbonthatóság fogalma, amelyre a tétel vonatkozik
- [[concepts/dimatii/shannon-tetel-zajmentes-csatornara]] — a tétel közvetlen felhasználása az entrópia mint alsó korlát bizonyítására
- [[concepts/dimatii/shannon-kod]] — a megfordításra épülő kódkonstrukció
