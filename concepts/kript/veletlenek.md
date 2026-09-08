---
tags: [concept]
sources: [véletlenek.pdf, véletlenek_feladatsor.pdf]
derivation: source
updated: 2026-09-04
---

# Véletlenszám-generálás kriptográfiában

A kriptográfiai biztonság döntő feltétele a megfelelő minőségű véletlen. Gyenge generátor az erős algoritmust is hatástalanná teszi.

## PRNG vs. CSPRNG

| | PRNG | CSPRNG |
|---|---|---|
| Cél | szimulációk, játékok | kriptográfia |
| Jósolható? | igen (elég lépés után) | nem (polinomiális időben) |
| Biztonság | statisztikai tesztek | számítási nehézségen alapul |
| Példák | Lehmer, LCG, middle-square | Salsa20, ChaCha20, /dev/urandom |

## Középső négyzet módszer (von Neumann, 1946)

$x_{k+1}$ = az $x_k^2$ középső $d$ jegye. Gyorsan ciklussá válik; nem kriptográfiai minőségű.

## Determinisztikus generátorok — és miért törnek el

A gyakorlatban használt gyors generátorok mind lineárisak, és épp ezért nem kriptográfiaiak: néhány megfigyelt kimenetből a belső paraméterek visszafejthetők.

- [[concepts/kript/linearis-kongruencialis-generator]] — Lehmer és az általános LCG; a paraméterek pár kimenetből kiszámíthatók
- [[concepts/kript/lfsr]] — bitszintű megfelelője; $2m$ kimeneti bitből a Berlekamp–Massey algoritmus visszaadja a visszacsatolási polinomot

## RC4 (egyszerűsített bemutatás)

KSA (Key Scheduling Algorithm) és PRGA (Pseudo-Random Generation Algorithm) az $S$ permutáción dolgozik. A feladatban $N = 8$ állapottal vizsgálják. Kriptográfiailag kompromittált (TLS-ből kivonták).

## Randomnessz tesztelés

NIST SP 800-22: 14 statisztikai teszt (pl. frekvencia, futások, spektrális, stb.). Szükséges, de nem elégséges a kriptográfiai minőséghez.

## Valódi véletlen generálása szabálytalan pénzérmével

Ha $p \neq 1/2$ az érmén, de $p$ ismeretlen ($0{,}4 < p < 0{,}6$):
- **Fair bit:** dobjon kétszer; `01 → 0`, `10 → 1`, `00` és `11` esetén ismételj (von Neumann-eljárás).
- **Szabályos dobókocka:** ismételt fair bit-párokból.

## Feladatok

- [[concepts/kript/feladatok]] — 6. feladat: LFSR (18 kimeneti bit, Berlekamp-Massey), 7. feladat: középső négyzet periódus, 8. feladat: RC4 ($N=8$)
- Véletlenek feladatsor (véletlenek_feladatsor.pdf): Lehmer-inverz, LFSR periódus, biased coin

## Kapocs

- [[concepts/kript/folyam-titkositok]] — LFSR-alapú és CSPRNG-alapú folyamtitkosítók
- [[concepts/kript/tokeletes-biztonsag]] — OTP megköveteli a valódi véletlent
- [[subjects/kript]] — tantárgy áttekintő
- [[concepts/kript/lfsr]] — a legfontosabb kulcsfolyam-előállító és a törése
- [[concepts/kript/linearis-kongruencialis-generator]] — a nem kriptográfiai generátorok tipikus családja
