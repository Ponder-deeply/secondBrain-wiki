---
tags: [concept]
sources: [szelmJegyzet.pdf]
derivation: source
updated: 2026-08-05
---

# Turing-gépek kódolása

A $\{0,1\}$ bemeneti ábécéjű Turing-gépek egyértelműen kódolhatók bináris szavakkal; ez teszi lehetővé, hogy Turing-gépeket más Turing-gépek bemeneteként kezeljünk.

## $\{0,1\}^*$ sorbarendezése

A $\{0,1\}$ feletti szavak hosszlexikografikusan rendezhetők: a szavak hossz szerint követik egymást, azonos hosszúak közül a lexikografikus rendezés dönt. Az így kapott felsorolás eleje:
$$w_1 = \varepsilon,\quad w_2 = 0,\quad w_3 = 1,\quad w_4 = 00,\quad w_5 = 01,\ \ldots$$
Adott $i$-re $w_i$ véges sok lépésben kiszámítható.

## Egy Turing-gép kódja

Legyen $M = (Q, \{0,1\}, \Gamma, \delta, q_0, q_i, q_n)$, ahol $|Q| = k$ és $|\Gamma| = m$.

- Az állapotokat sorszámozzuk: $Q = \{p_1, \ldots, p_k\}$, ahol $p_1 = q_0$, $p_{k-1} = q_i$, $p_k = q_n$.
- A szalagszimbólumokat sorszámozzuk: $\Gamma = \{X_1, \ldots, X_m\}$, ahol $X_1 = 0$, $X_2 = 1$, $X_3 = \sqcup$.
- Az irányokat sorszámozzuk: $D_1, D_2, D_3$ a három lehetséges irány ($L, R, S$).

Egy $\delta(p_i, X_j) = (p_r, X_s, D_t)$ átmenet kódja:
$$0^i 1 0^j 1 0^r 1 0^s 1 0^t$$
Minden $0$-blokk hossza legalább $1$, ezért az átmenetet kódoló szó nem tartalmaz `11` részszót. Az összes átmenetet kódoló szavakat `11`-gyel elválasztva fűzzük össze; az így kapott szó $M$ kódja, jelölése $\langle M \rangle$.

## $M_i$ és a teljes felsorolás

Minden $i \ge 1$-re $M_i$ jelöli azt a Turing-gépet, amelyet a $w_i$ bináris szó kódol. Megegyezés:

- Ha $w_i$ egyetlen Turing-gép kódolásával sem egyezik, akkor $M_i$ az a gép, amely minden inputon azonnal $q_n$-be megy ($L(M_i) = \emptyset$).

## $(M, w)$ párok kódolása

Mivel az átmenetkódolás nem tartalmaz három `1`-est egymás mellett, egy $(M, w)$ párt úgy kódolunk, hogy $M$ kódja után írjuk a `111` szót, majd $w$-t:
$$\langle M, w \rangle = \langle M \rangle\, 111\, w$$

## Kapocs

- [[concepts/bvszam/problemak-mint-formalis-nyelvek]] — objektumok szóval való kódolása
- [[concepts/bvszam/turing-gep]] — a kódolt gép modellje
- [[concepts/bvszam/eldonthetetlen-problemak]] — a diagonális nyelv és $L_u$ a kódolásra épül
- [[concepts/bvszam/univerzalis-turing-gep]] — $\langle M, w \rangle$ bemenetet szimuláló gép
