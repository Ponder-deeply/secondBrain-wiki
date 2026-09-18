---
tags: [concept]
sources: [DimatIIEa01.pdf]
derivation: source
updated: 2026-09-08
---

# Maradékos osztás

Az elemi számelmélet fő eszköze: bármely egész egyértelműen felírható egy adott nem nulla szám többszöröseként plusz egy nála kisebb nemnegatív maradékként.

## Tartalom

**Tétel.** Tetszőleges $a$, $b \neq 0$ egész számokhoz egyértelműen léteznek olyan $q, r$ egészek, hogy
$$a = bq + r \quad \text{és} \quad 0 \leq r < |b|.$$

**Bizonyítás** (nemnegatív számokra; az általános eset ebből adódik).

*Létezés*, $a$ szerinti indukcióval. Ha $a < b$, akkor $a = b\cdot 0 + a$, tehát $q = 0$, $r = a$. Ha $a \geq b$, akkor az indukciós feltevés szerint az $a$-nál kisebb számok már felírhatók ilyen alakban; legyen $a - b = bq^* + r^*$. Ekkor $a = b(q^* + 1) + r^*$, azaz $q = q^* + 1$, $r = r^*$.

*Egyértelműség*: legyen $a = bq + r = bq^* + r^*$. Ekkor $b(q - q^*) = r^* - r$. Mivel $|r^* - r| < |b|$, ez csak úgy lehet, ha $q = q^*$ és $r = r^*$. $\square$

### Jelölés

Legyenek $a, b$ egészek ($b \neq 0$), és $a = b\cdot q + r$ a fenti felbontás. Ekkor

- $a \bmod b = r$;
- $q = \lfloor a/b \rfloor$, ha $b > 0$, és $q = \lceil a/b \rceil$, ha $b < 0$.

**Példák.** $123 \bmod 10 = 3$, $123 \bmod 100 = 23$, $123 \bmod 1000 = 123$, $123 \bmod (-10) = 3$. Negatív osztandóra: $-123 \bmod 10 = 7$, $-123 \bmod 100 = 77$, $-123 \bmod 1000 = 877$, $-123 \bmod (-10) = 7$. A maradék definíció szerint mindig nemnegatív.

### Példák: ciklikus mennyiségek

*Hány óra lesz 123 óra múlva, ha most 9 óra van?* $123 = 24\cdot 5 + 3$, tehát $9 + 3 = 12$: dél lesz. *104 óra múlva?* $104 = 24 \cdot 4 + 20$, tehát $9 + 20 = 29$, újabb redukcióval $29 = 24\cdot 1 + 5$: hajnali 5 óra.

*Milyen napra esik jövőre szeptember 16?* A napokat számozzuk $\text{hétfő} \mapsto 0, \dots, \text{vasárnap} \mapsto 6$ szerint. $365 = 7\cdot 52 + 1$, tehát szerda $+\,1$ nap $= 2 + 1 = 3 =$ csütörtök. Visszafelé, két évet lépve szökőévvel: $-(365 + 366) = -731 = 7\cdot(-104) - 3$, azaz vasárnap $-\,3$ nap $= 6 - 3 = 3 =$ csütörtök.

A maradékos osztás az alapja a [[concepts/dimatii/szamrendszerek]] felírási tételének, az [[concepts/dimatii/euklideszi-algoritmus]]nak és a [[concepts/dimatii/kongruencia]] fogalmának egyaránt.

## Kapocs

- [[concepts/dimatii/oszthatosag]] — a maradék nulla volta pontosan az oszthatóság
- [[concepts/dimatii/szamrendszerek]] — ismételt maradékos osztásból adódó jegyek
- [[concepts/dimatii/euklideszi-algoritmus]] — maradékos osztások láncolata
- [[concepts/dimatii/kongruencia]] — a maradékok egyenlőségének relációja
