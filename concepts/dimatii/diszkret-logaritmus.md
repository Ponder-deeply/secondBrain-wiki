---
tags: [concept]
sources: [DimatIIEa03.pdf, dm2gy05.pdf, dm2gy06.pdf]
derivation: source
kind: definition
element: fire
updated: 2026-10-21
---

# Diszkrét logaritmus

Adott $g$ generátor mellett az a kitevő, amelyre $g$-t emelve egy adott maradékot kapunk modulo $p$ — a moduláris hatványozás inverze, amelyre nem ismert hatékony algoritmus.

## Tartalom

### Definíció

Legyen $p$ prímszám, $g$ generátor modulo $p$ (lásd [[concepts/dimatii/primitiv-gyok]]). Ekkor egy $a \in \mathbb{Z}$, $p \nmid a$ esetén az $a$ **$g$ alapú diszkrét logaritmusa** (más néven **indexe**) az az $n$ kitevő, amelyre

$$\log_g a = n : \quad a \equiv g^n \bmod p, \quad 0 \le n < p - 1.$$

A definíció épp azért értelmes, mert $g$ generátor: a $g^0, g^1, \ldots, g^{p-2}$ hatványok kimerítik a redukált maradékosztályokat, tehát minden $a$-hoz pontosan egy ilyen $n$ tartozik.

### Példa

$3$ generátor modulo $7$, a hatványtáblázat $n = 1, \ldots, 6$-ra $3, 2, 6, 4, 5, 1$. Ezt megfordítva kapjuk a logaritmustáblázatot:

| $a$ | 1 | 2 | 3 | 4 | 5 | 6 |
|---|---:|---:|---:|---:|---:|---:|
| $\log_3 a$ | 0 | 2 | 1 | 4 | 5 | 3 |

Hasonlóan $g = 2$, $p = 11$ mellett a $2^n \bmod 11$ sorozat $2, 4, 8, 5, 10, 9, 7, 3, 6, 1$, amiből

| $a$ | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| $\log_2 a$ | 0 | 1 | 8 | 2 | 4 | 9 | 7 | 3 | 6 | 5 |

### Azonosságok

A valós logaritmus szabályai modulo $p-1$ öröklődnek. Legyen $p$ prím, $g$ generátor modulo $p$, $1 \le a, b < p$ és $n \in \mathbb{Z}$. Ekkor

$$\log_g (a \cdot b) \equiv \log_g a + \log_g b \pmod{p-1},$$
$$\log_g (a^n) \equiv n \cdot \log_g a \pmod{p-1}.$$

A modulus itt $p-1$, mert a kitevők maguk is csak modulo $p-1$ meghatározottak.

### Nehézség

Míg $g^n \bmod p$ a [[concepts/dimatii/gyors-hatvanyozas]] miatt olcsó, a fordított irány — adott $a$-hoz megkeresni $n$-et — a jelenlegi ismereteink szerint nagy $p$-re gyakorlatilag kivitelezhetetlen. $p \sim 2^{2048}$ mellett a diszkrét logaritmus kiszámítása nagyságrendileg $10^{30}$ év. Erre a feltételezett nehézségre épül a [[concepts/dimatii/diffie-hellman-kulcscsere]] biztonsága.

### Feladattípusok (2024. 5–6. sorozat)

**Generátor ellenőrzése.** $g$ generátor modulo $p$, ha hatványai kimerítik $1, \dots, p-1$-et (rendje $p-1$). Modulo $7$: $4$ hatványai $4, 2, 1, 4, 2, 1$, tehát $4$ **nem** generátor (rendje $3$); $5$ hatványai $5, 4, 6, 2, 3, 1$, tehát $5$ generátor. Bármely $g$ generátorra $\log_g(6) = \log_g(-1) = (p-1)/2 = 3$ modulo $7$, mert a $-1$ az egyetlen $2$ rendű elem. Modulo $11$ a $g = 2$ generátor (táblázat fent).

**Értékek számolása az azonosságokkal, majd ellenőrzés a táblázattal** (a modulus mindig $p - 1$):

| modulus, $g$ | értékek |
|---|---|
| $p = 11$, $g = 2$ | $\log_2 2 = 1$, $\log_2 4 = 2$, $\log_2 5 = 4$, $\log_2 10 = \log_2 2 + \log_2 5 = 5$, $\log_2 9 = 2\log_2 3 = 2\cdot 8 = 16 \equiv 6$, $\log_2 7 = 7$ |
| $p = 13$, $g = 2$ | $\log_2 2 = 1$, $\log_2 4 = 2$, $\log_2 3 = 4$, $\log_2 6 = 1 + 4 = 5$, $\log_2 5 = 9$, $\log_2 10 = 1 + 9 = 10$ |
| $p = 23$, $g = 5$ | $\log_5 5 = 1$, $\log_5 2 = 2$, $\log_5 10 = 2 + 1 = 3$, $\log_5 20 = 4 + 1 = 5$ ($\log_5 4 = 2\cdot 2 = 4$), $\log_5 9 = 10$ |

A $p = 13$ sor értékei: $2^1, 2^2, \dots$ hatványai $2, 4, 8, 3, 6, 12, 11, 9, 5, 10, 7, 1$ ($2^{12} = 1$ is mutatja, hogy $2$ generátor). Az azonosságok használatához a szorzatot előbb faktorokra bontjuk, amelyeknek a logaritmusa már ismert ($10 = 2\cdot 5$, $20 = 4\cdot 5$, $9 = 3^2$), a kitevőket modulo $p - 1$ vesszük.

**Tipikus hiba.** A logaritmusok összegét modulo $p$ (nem $p-1$) redukálni; generátornak hinni egy elemet anélkül, hogy a teljes hatványsort végigszámolták volna.

## Kapocs

- [[concepts/dimatii/primitiv-gyok]] — a definíció feltétele, hogy $g$ generátor legyen
- [[concepts/dimatii/gyors-hatvanyozas]] — a könnyű irány, amelynek a diszkrét logaritmus az inverze
- [[concepts/dimatii/diffie-hellman-kulcscsere]] — biztonsága a diszkrét logaritmus nehézségén múlik
- [[concepts/dimatii/rsa]] — a másik nyilvános kulcsú séma, amely a faktorizáció nehézségére épül
- [[concepts/dimatii/primitiv-gyok]] — a generátor-ellenőrzés fogalma
