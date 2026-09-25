---
tags: [concept, dimatii/kongruenciak]
sources: [DimatIIEa02.pdf]
derivation: source
updated: 2026-09-08
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

**Példa (több megoldás).** Oldjuk meg a $10x \equiv 8 \pmod{22}$ kongruenciát! A bővített euklideszi algoritmus $x_0 = 1$-et ad, $(10,22) = 2 \mid 8$, tehát két megoldáspár van:
$$x_1 = 4\cdot(-2) \equiv 14 \pmod{22}, \qquad x_2 = 4\cdot(-2) + \tfrac{22}{2} \equiv 14 + 11 \equiv 3 \pmod{22}.$$
Összes megoldás: $\{14 + 22\ell\} \cup \{3 + 22\ell\}$. Ellenőrzés: $10\cdot 14 - 8 = 132 = 6\cdot 22$, $10\cdot 3 - 8 = 22 = 1\cdot 22$.

Alternatív megoldási út: ha $(a,m) = 1$, az [[concepts/dimatii/euler-fermat-tetel]] szerint mindkét oldalt $a^{\varphi(m)-1}$-nel szorozva közvetlenül adódik $x$.

## Kapocs

- [[concepts/dimatii/kongruencia]] — az alapfogalom
- [[concepts/dimatii/bovitett-euklideszi-algoritmus]] — a megoldás eszköze
- [[concepts/dimatii/legnagyobb-kozos-oszto]] — a megoldhatóság feltétele
- [[concepts/dimatii/linearis-diofantikus-egyenlet]] — ugyanez egészegyenletként
- [[concepts/dimatii/szimultan-kongruenciak]] — több lineáris kongruencia együtt
- [[concepts/dimatii/euler-fermat-tetel]] — alternatív megoldási módszer
