---
tags: [concept]
sources: [dimat2gyak01mo.pdf, dimat2gyak04mo.pdf, Lehman-Leighton-Meyer-Mathematics-for-Computer-Science.pdf]
references: [Lehman–Leighton–Meyer, Mathematics for Computer Science, 9.7 Remainder Arithmetic]
derivation: source
kind: pitfall
element: fire
updated: 2026-10-22
---

# Hatványok periodicitása $\mathbb{Z}_m$-ben

Egy maradékosztály hatványai előbb-utóbb ismétlődnek. A hatványozásnál az alapot szabad redukálni, a kitevőt viszont nem szabad az $m$ szerinti maradékára cserélni.

## Tartalom

### Az általános elv

Összeadások és szorzások sorozatának $m$ szerinti maradékához minden operandust helyettesíthetünk a maradékával, és minden részeredményt azonnal redukálhatunk: $(a+b) \bmod m = ((a \bmod m) + (b \bmod m)) \bmod m$, és ugyanez a szorzásra. A kitevő viszont a szorzások *számát* adja meg, nem műveleti operandus.

**Csapda.** $a^n \bmod m \neq a^{\,n \bmod m} \bmod m$ általában. Például $2^{5} \bmod 3 = 2$, de $2^{5 \bmod 3} = 2^2 = 4 \equiv 1$. A kitevőt legfeljebb a hatványok *periódusával* szabad redukálni, lásd lent, és relatív prím alapnál $\varphi(m)$ szerint: [[concepts/dimatii/euler-fermat-tetel]].

### Hatványok ciklusai

Az $a$ hatványai modulo $m$ véges sok érték miatt ismétlődnek.

| $a$ | $m$ | hatványok $a^1, a^2, \dots$ | szabály |
|---:|---:|---|---|
| 3 | 5 | 3, 4, 2, 1, 3, 4, … | $3^{4n+k} \equiv 3^k$ |
| 2 | 7 | 2, 4, 1, 2, 4, 1, … | $2^{3n+k} \equiv 2^k$ |
| 3 | 7 | 3, 2, 6, 4, 5, 1, 3, … | $3^{6n+k} \equiv 3^k$ |
| 7 | 8 | 7, 1, 7, 1, … | $7^{2n} \equiv 1$, $7^{2n+1} \equiv 7$ |
| 2 | 4 | 2, 0, 0, … | $2^n \equiv 0$, ha $n \ge 2$ |

A $3 \bmod 7$ eset a legrosszabb: hat lépés után kerül vissza $1$-re, az összes nemnulla maradékot bejárja (primitív gyök, lásd [[concepts/dimatii/primitiv-gyok]]).

**Nilpotens elem.** Ha egy nem nulla elem valamely hatványa nulla, nilpotensnek hívjuk. $\mathbb{Z}_4$-ben $2^2 = 0$. Általában, ha a modulus nem négyzetmentes, azaz $m = p^n q$ ($n > 1$, $p \nmid q$), akkor $a = pq \not\equiv 0$, de $a^n = p^n q^n \equiv 0$. Nilpotens mátrix is van: $\begin{pmatrix}0&1&0\\0&0&1\\0&0&0\end{pmatrix}^3 = 0$.

### Példa: műveletsor modulo 36

Határozzuk meg $\left(44427^{3456789} + 15555858^{5555}\right) \cdot 403^{6666666} \bmod 36$ értékét. Az alapok maradéka: $44427 \equiv 3$, $15555858 \equiv 6$, $403 \equiv 7 \pmod{36}$, tehát a kifejezés $\left(3^{3456789} + 6^{5555}\right) \cdot 7^{6666666}$.

- $3^k \bmod 36$: $3, 9, 27, 9, 27, \dots$ a $k = 2$-től kezdve $2$ hosszú ciklus, ezért páratlan $k \ge 3$ esetén $3^k \equiv 27$.
- $6^2 = 36 \equiv 0$, így $6^{5555} \equiv 0$.
- $7^6 \equiv 1 \pmod{36}$ és $6 \mid 6666666$, ezért $7^{6666666} \equiv 1$.

Az érték: $(27 + 0) \cdot 1 = 27$. A $7^k$ kitevőjét a hatványok *periódusával* (6) redukáltuk, nem a $36$-tal.

## Kapocs

- [[concepts/dimatii/euler-fermat-tetel]] — relatív prím alapnál a periódus osztja $\varphi(m)$-et
- [[concepts/dimatii/hatvanytorony-modulo-szamitasa]] — a kitevő több szinten is redukálható $\varphi$ szerint
- [[concepts/dimatii/kongruencia]] — a redukálás alapja, a műveletek megőrzése
- [[concepts/dimatii/maradekosztaly]] — a $\mathbb{Z}_m$ gyűrű
- [[concepts/dimatii/egysegggyok-es-matrixhatvany]] — ugyanaz a ciklikusság komplex számokra és mátrixokra
- [[concepts/dimatii/nullosztomentes-gyuru]] — a nilpotens elemek nullosztók
