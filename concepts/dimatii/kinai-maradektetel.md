---
tags: [concept]
sources: [DimatIIEa02.pdf]
derivation: source
updated: 2026-09-08
---

# Kínai maradéktétel

Páronként relatív prím modulusok esetén tetszőleges maradékok egyszerre előírhatók, és a megoldás a modulusok szorzata szerint egyértelmű.

## Tartalom

**Tétel.** Legyenek $1 < m_1, m_2, \dots, m_n$ páronként relatív prím számok, $c_1, c_2, \dots, c_n$ pedig egészek. Ekkor a
$$x \equiv c_1 \pmod{m_1}, \quad x \equiv c_2 \pmod{m_2}, \quad \dots, \quad x \equiv c_n \pmod{m_n}$$
kongruenciarendszer megoldható, és bármely két megoldás kongruens egymással modulo $m_1m_2\cdots m_n$.

**Bizonyítás** (konstruktív, $n$ szerinti indukcióval). Legyen $m = m_1m_2$. A [[concepts/dimatii/bovitett-euklideszi-algoritmus]]sal oldjuk meg az
$$m_1x_1 + m_2x_2 = 1$$
egyenletet — ez megoldható, mert $(m_1,m_2) = 1$. Legyen
$$c_{1,2} = m_1x_1c_2 + m_2x_2c_1.$$

Ekkor $c_{1,2} \equiv c_j \pmod{m_j}$ ($j = 1,2$), hiszen modulo $m_1$ az első tag eltűnik és $m_2x_2 \equiv 1$. Tehát ha $x \equiv c_{1,2} \pmod m$, akkor $x$ megoldása az első két kongruenciának.

Megfordítva: ha $x$ megoldása az első két kongruenciának, akkor $x - c_{1,2}$ osztható $m_1$-gyel és $m_2$-vel is, így — mivel ezek relatív prímek — a szorzatukkal is: $x \equiv c_{1,2} \pmod m$.

Az eredeti rendszer tehát ekvivalens a
$$x \equiv c_{1,2} \pmod{m_1m_2}, \quad x \equiv c_3 \pmod{m_3}, \quad \dots, \quad x \equiv c_n \pmod{m_n}$$
rendszerrel, amely eggyel rövidebb; $n$ szerinti indukcióval adódik az állítás. $\square$

A bizonyítás egyben algoritmus is: párokat vonunk össze, minden lépésben egy bővített euklideszi algoritmus futtatásával. Kidolgozott számpéldák a [[concepts/dimatii/szimultan-kongruenciak]] lapon.

## Kapocs

- [[concepts/dimatii/szimultan-kongruenciak]] — az általános feladat és a normalizálás
- [[concepts/dimatii/bovitett-euklideszi-algoritmus]] — a konstrukció eszköze
- [[concepts/dimatii/legnagyobb-kozos-oszto]] — a relatív prímség feltétele
- [[concepts/dimatii/kongruencia]] — az alapfogalom
