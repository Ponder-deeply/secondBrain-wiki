---
tags: [concept]
sources: ["Elsőrendű_logika_ bevezetés.pdf"]
derivation: source
updated: 2026-09-08
---

# Term

A term az elsőrendű nyelv azon kifejezéstípusa, amely a struktúra matematikai leképezéseit — az individuumokat és a közöttük ható függvényeket — szimbolizálja; definíciója szerkezeti rekurzióval történik.

## Tartalom

### Definíció — egyfajtájú eset

A [[concepts/logika/leiro-nyelv-es-szignatura]] szerinti $\langle Pr, Fn, Cnst\rangle$ ábécéből a **term** ($L_t(V_\nu)$) fogalma szerkezeti rekurzióval:

1. (alaplépés) Minden individuumváltozó és konstansszimbólum term.
2. (rekurzív lépés) Ha $f \in Fn$ $k$-változós függvényszimbólum, és $t_1, t_2, \dots, t_k$ termek, akkor $f(t_1, t_2, \dots, t_k)$ is term.
3. Minden term az 1., 2. szabályok véges sokszori alkalmazásával áll elő.

### Definíció — többfajtájú eset

Ha $U$ többfajtájú (lásd [[concepts/logika/matematikai-struktura]]), a term fajtahelyes:

1. (alaplépés) Minden $\pi \in Srt$ fajtájú individuumváltozó és konstansszimbólum $\pi$ fajtájú term.
2. (rekurzív lépés) Ha $f \in Fn$ $(\pi_1, \pi_2, \dots, \pi_k; \pi_f)$ fajtájú függvényszimbólum, és $t_1, t_2, \dots, t_k$ rendre $\pi_1, \pi_2, \dots, \pi_k$ fajtájú termek, akkor $f(t_1, t_2, \dots, t_k)$ $\pi_f$ fajtájú term.
3. Minden term az 1., 2. szabályok véges sokszori alkalmazásával áll elő.

### Közvetlen részterm

- Konstansnak és individuumváltozónak nincs közvetlen résztermje.
- Az $f(t_1, t_2, \dots, t_k)$ term közvetlen résztermjei a $t_1, t_2, \dots, t_k$ termek.

### A term szerkezeti fája

Egy $t$ term **szerkezeti fája** olyan véges fa, amelyre:

- a gyökeréhez a $t$ term van rendelve,
- ha egy csúcshoz $t'$ term van rendelve, akkor a csúcs gyerekeihez $t'$ közvetlen résztermjei vannak rendelve,
- a levelekhez individuumváltozók vagy konstansok vannak rendelve.

### Alapterm

A [[concepts/logika/szabad-es-kotott-valtozo|változót]] nem tartalmazó term **alapterm** (más néven alappéldány). Az alapterm fogalma az atomi formulák [[concepts/logika/elsorendu-formula|alapatom és alappéldány]] fogalmának előfeltétele: pl. $Q(f(a,b), a)$ atomi formula argumentuma az $f(a,b)$ alapterm.

## Kapocs

- [[concepts/logika/leiro-nyelv-es-szignatura]] — az ábécé, amelynek jeleiből a term felépül
- [[concepts/logika/elsorendu-formula]] — a term mint az atomi formula argumentuma
- [[concepts/logika/matematikai-struktura]] — a struktúra, amelynek matematikai leképezéseit a term szimbolizálja
