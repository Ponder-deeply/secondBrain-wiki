---
tags: [concept, dimatii/kongruenciak]
sources: [DimatIIEa02.pdf]
derivation: source
updated: 2026-09-08
---

# Lineáris diofantikus egyenlet

Diofantikus egyenlet: olyan egyenlet, amelynek csak az egész megoldásait keressük. A lineáris eset a lineáris kongruenciával ekvivalens.

## Tartalom

**Definíció.** A **lineáris diofantikus egyenlet** alakja
$$ax + by = c, \qquad a, b, c \in \mathbb{Z},$$
és a megoldásokat az egészek körében keressük.

Ez ekvivalens az
$$ax \equiv c \pmod b, \qquad by \equiv c \pmod a$$
kongruenciákkal. Az egyenlet **pontosan akkor oldható meg, ha $(a,b) \mid c$**, és ekkor a megoldások a [[concepts/dimatii/bovitett-euklideszi-algoritmus]]sal kaphatók meg — lásd [[concepts/dimatii/linearis-kongruencia]].

### Nem lineáris példák

Nem lineáris diofantikus egyenletekre nincs ilyen általános eljárás; a megoldhatatlanság gyakran maradékos érveléssel mutatható meg.

- $x^2 + y^2 = -4$: nincs valós megoldás sem.
- $x^2 - 4y^2 = 3$: nincs megoldás, ugyanis a $4$-gyel való osztási maradékokat vizsgálva $x^2 \equiv 3 \pmod 4$ kellene. De ez nem lehet, mert a négyzetszám maradéka $0$ vagy $1$:

| $x$ | $x^2 \bmod 4$ |
|---|---:|
| $4k$ | 0 |
| $4k+1$ | 1 |
| $4k+2$ | 0 |
| $4k+3$ | 1 |

Ez a **maradékos kizárás** módszere: egy alkalmas modulus szerint a két oldal maradéka soha nem eshet egybe.

## Kapocs

- [[concepts/dimatii/linearis-kongruencia]] — az ekvivalens megfogalmazás
- [[concepts/dimatii/bovitett-euklideszi-algoritmus]] — a megoldás eszköze
- [[concepts/dimatii/kongruencia]] — a maradékos kizárás nyelve
- [[concepts/dimatii/legnagyobb-kozos-oszto]] — a megoldhatóság feltétele
