---
tags: [concept]
sources: [DimatIIEa08.pdf]
derivation: source
updated: 2026-09-08
---

# Shannon tétele zajmentes csatornára

Felbontható betűnkénti kódolás átlagos szóhossza nem lehet kisebb a forrás entrópiájánál, és az entrópiánál 1-gyel nagyobb korlát mindig elérhető.

## Tartalom

### Alsó korlát

**Tétel.** Legyen $A = \{a_1, a_2, \dots, a_n\}$ a kódolandó ábécé, $p_1, p_2, \dots, p_n$ a betűk eloszlása, $\varphi : A \to B^+$ injektív leképezés, $B$ elemeinek száma $r \ge 2$, továbbá $\ell_j = |\varphi(a_j)|$. Ha a $\varphi$ által meghatározott betűnkénti kódolás felbontható, akkor
$$H_r(p_1, p_2, \dots, p_n) \le \bar{\ell} .$$

*Bizonyítás.*
$$\bar{\ell} - H_r(p_1, \dots, p_n) = \sum_{j=1}^n p_j \ell_j + \sum_{j=1}^n p_j \log_r p_j = \sum_{j=1}^n p_j\left(-\log_r\left(r^{-\ell_j}\right)\right) + \sum_{j=1}^n p_j \left(-\log_r \frac{1}{p_j}\right)$$
$$= \sum_{j=1}^n p_j\left(-\log_r \frac{r^{-\ell_j}}{p_j}\right) \ge -\log_r\left(\sum_{j=1}^n r^{-\ell_j}\right) \ge -\log_r 1 = 0,$$
ahol az első becslés a Jensen-egyenlőtlenség, a második pedig a McMillan-egyenlőtlenség következménye. $\square$

Az entrópia tehát nem csupán információelméleti mérőszám, hanem a tömörítés kemény alsó korlátja: annál rövidebben átlagosan nem lehet felbontható módon kódolni.

### A Shannon-kód létezése

**Tétel.** Az előző tétel jelöléseivel, ha $n > 1$, akkor van olyan prefix kód, amire
$$\bar{\ell} < H_r(p_1, p_2, \dots, p_n) + 1 .$$

*Bizonyítás.* Válasszunk olyan $\ell_1, \ell_2, \dots, \ell_n$ természetes számokat, amelyekre
$$r^{-\ell_j} \le p_j < r^{-\ell_j + 1}, \qquad j = 1, 2, \dots, n .$$
Ekkor $\sum_{j=1}^n r^{-\ell_j} \le \sum_{j=1}^n p_j = 1$, így a McMillan-egyenlőtlenség megfordítása miatt létezik prefix kód az adott $\ell_j$ hosszakkal. Mivel $\ell_j < 1 - \log_r p_j$, ezért
$$\bar{\ell} = \sum_{j=1}^n p_j \ell_j < \sum_{j=1}^n p_j (1 - \log_r p_j) = 1 + H_r(p_1, \dots, p_n). \qquad \square$$

A két tétel együtt bezárja az optimális átlagos szóhosszat az $[H_r, H_r + 1)$ intervallumba.

## Kapocs

- [[concepts/dimatii/entropia]] — az alsó korlát mennyisége
- [[concepts/dimatii/mcmillan-egyenlotlenseg]] — mindkét bizonyítás lépése
- [[concepts/dimatii/shannon-kod]] — a felső korlátot megvalósító konkrét konstrukció
- [[concepts/dimatii/optimalis-kod]] — az elérhető minimum, amelyet a tétel közrefog
- [[concepts/dimatii/huffman-kod]] — a valóban optimális kód, amely a Shannon-kódnál sosem rosszabb
