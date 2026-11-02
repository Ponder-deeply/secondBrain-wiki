---
tags: [concept]
sources: [dimat2gyak02mo.pdf, Dimat2mintaZH1.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-21
---

# Legnagyobb közös osztó kitevős kifejezésekre

Nagy hatványokból képzett kifejezések ($a^n \pm 1$, Fibonacci-számok) legnagyobb közös osztóját nem kiszámolva, hanem az lnko két azonosságával egyszerűsítve adjuk meg — az euklideszi algoritmus lépéseit "szimbolikusan" végezzük.

## Tartalom

### Az eszközök

A [[concepts/dimatii/legnagyobb-kozos-oszto]] és az [[concepts/dimatii/euklideszi-algoritmus]] alapján (a forrásban "az előadáson volt" azonosságok):

- $(ca, cb) = c\,(a,b)$;
- $(a,b) = (a-b, b)$ (a maradékos osztás első lépése; ismételve $(a,b) = (a - kb, b)$);
- $(c, b) = 1 \Rightarrow (a\cdot c, b) = (a, b)$ — relatív prímmel szabad egyszerűsíteni.

**ZH-tipp** (a mintafeladatban megadva): $(a+1, b+1) = (a-b, b+1)$; ezzel szemben $(a-1, b+1) = (a+b, b+1)$, vagy másképp $(a-1, b+1) = (a-1, a+b)$ — az utóbbit sokszor érdemes használni. Vigyázat az előjelekre: $a^n + 1$ és $a^m + 1$ esetén a "$+1$" nem tűnik el a kivonáskor úgy, mint a "$-1$" esetén.

### Feladattípus 1: $(2^a - 1, 2^b - 1)$

Kivonással a kitevők az euklideszi algoritmust követik:
$$(2^{13}-1, 2^8-1) = (2^{13}-2^8, 2^8-1) = (2^8(2^5-1), 2^8-1) = (2^5-1, 2^8-1) = \dots = (2^2 - 1, 2^3-1) = (3,7) = 1,$$
mert $2^8$ és $2^8 - 1$ relatív prímek (egyszerűsíthető). Hasonlóan
$$(2^{15}-1, 2^9-1) = (2^6-1, 2^9-1) = (2^6-1, 2^3-1) = (2^3-1, 2^3-1) = 2^3 - 1 = 7.$$
A két példa a $(15, 9) = 3$, $(13,8) = 1$ kitevő-lnko-ra illeszkedik: az eredmény $2^{(a,b)} - 1$. (Ez a lépések általánosítása, a forrásban nem kimondott megfigyelés.)

### Feladattípus 2: $(a^n + 1, a^m + 1)$ — a minta-ZH feladata

*Add meg $11^4 + 1$ és $11^6 + 1$ lnko-ját.* Legyen $x = 11^2 = 121$: $(x^2 + 1, x^3 + 1)$. Ekkor $x^3 + 1 - x(x^2+1) = 1 - x$, tehát
$$(x^3+1, x^2+1) = (x^2+1, x-1) = (2, x-1),$$
mert $x^2 + 1 = (x-1)(x+1) + 2$. Mivel $x - 1 = 120$ páros, az lnko $2$. (Ellenőrzés: $11^4+1 = 14642 = 2\cdot 7321$, $11^6+1 = 1771562 = 2\cdot 885781$, és $(7321, 885781) = (7321, 60) = 1$.) A megoldás számítógép nélkül, a tipp alkalmazásával is elvégezhető.

### Feladattípus 3: Fibonacci-számok

$F_1 = F_2 = 1$, $F_{n+2} = F_{n+1} + F_n$.

- $(F_{n+1}, F_n) = 1$: teljes indukcióval, $(F_{N+2}, F_{N+1}) = (F_{N+1} + F_N, F_{N+1}) = (F_N, F_{N+1}) = 1$. A szomszédos Fibonacci-számok tehát relatív prímek.
- $(F_{n+2}, F_n) = (F_{n+1} + F_n, F_n) = (F_{n+1}, F_n) = 1$.
- $(F_{n+3}, F_n)$: $F_{n+3} = 2F_{n+1} + F_n$, tehát $(F_{n+3}, F_n) = (2F_{n+1}, F_n) = (2, F_n)$, mert $(F_{n+1}, F_n) = 1$. Értéke $1$ vagy $2$ aszerint, hogy $F_n$ páratlan-e vagy páros. $F_n$ pontosan akkor páros, ha $3 \mid n$ (a paritás sorozata: páratlan, páratlan, páros, ismétlődik), tehát $(F_{n+3}, F_n) = 2$, ha $3 \mid n$, különben $1$.

### Tipikus hibák

- A "$+$" és "$-$" összekeverése: $(a+1, b+1) = (a-b, b+1)$, de $(a-1, b+1) = (a+b, b+1)$.
- Közös tényező elhagyása relatív prímség igazolása nélkül: $(ac, b) = (a, b)$ csak $(c,b) = 1$ esetén igaz.
- A végeredményt hibás zárással adjuk meg: a "számolj ki egy nagy számot" helyett (pl. $11^6 + 1$ közvetlen faktorizálása) az algebrai átalakítás a cél.

## Kapocs

- [[concepts/dimatii/legnagyobb-kozos-oszto]] — a fogalom és az $(ca,cb) = c(a,b)$ azonosság
- [[concepts/dimatii/euklideszi-algoritmus]] — az $(a,b) = (a-b,b)$ lépés a maradékos osztás
- [[concepts/dimatii/oszthatosag]] — paritás és oszthatóság a Fibonacci-példában
- [[concepts/dimatii/komplex-egysegiyokok-hatvanyai]] — a ZH 1. feladatának másik fele
