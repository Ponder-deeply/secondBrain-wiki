---
tags: [concept, dimatii/alkalmazasok-kriptografia]
sources: [DimatIIEa03.pdf]
derivation: source
updated: 2026-09-08
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
| $\log_3 a$ | 6 | 2 | 1 | 4 | 5 | 3 |

Hasonlóan $g = 2$, $p = 11$ mellett a $2^n \bmod 11$ sorozat $2, 4, 8, 5, 10, 9, 7, 3, 6, 1$, amiből

| $a$ | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| $\log_2 a$ | 10 | 1 | 8 | 2 | 4 | 9 | 7 | 3 | 6 | 2 |

### Azonosságok

A valós logaritmus szabályai modulo $p-1$ öröklődnek. Legyen $p$ prím, $g$ generátor modulo $p$, $1 \le a, b < p$ és $n \in \mathbb{Z}$. Ekkor

$$\log_g (a \cdot b) \equiv \log_g a + \log_g b \pmod{p-1},$$
$$\log_g (a^n) \equiv n \cdot \log_g a \pmod{p-1}.$$

A modulus itt $p-1$, mert a kitevők maguk is csak modulo $p-1$ meghatározottak.

### Nehézség

Míg $g^n \bmod p$ a [[concepts/dimatii/gyors-hatvanyozas]] miatt olcsó, a fordított irány — adott $a$-hoz megkeresni $n$-et — a jelenlegi ismereteink szerint nagy $p$-re gyakorlatilag kivitelezhetetlen. $p \sim 2^{2048}$ mellett a diszkrét logaritmus kiszámítása nagyságrendileg $10^{30}$ év. Erre a feltételezett nehézségre épül a [[concepts/dimatii/diffie-hellman-kulcscsere]] biztonsága.

## Kapocs

- [[concepts/dimatii/primitiv-gyok]] — a definíció feltétele, hogy $g$ generátor legyen
- [[concepts/dimatii/gyors-hatvanyozas]] — a könnyű irány, amelynek a diszkrét logaritmus az inverze
- [[concepts/dimatii/diffie-hellman-kulcscsere]] — biztonsága a diszkrét logaritmus nehézségén múlik
- [[concepts/dimatii/rsa]] — a másik nyilvános kulcsú séma, amely a faktorizáció nehézségére épül
