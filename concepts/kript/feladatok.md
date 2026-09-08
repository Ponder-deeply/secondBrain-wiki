---
tags:
  - concept
sources:
  - feladatok.pdf
  - véletlenek_feladatsor.pdf
  - hash_feladatok.pdf
  - mac_feladatok.pdf
  - tökéletes_biztonság_feladatok.pdf
derivation: source
updated: 2026-09-04
---
# Kriptográfia — feladatsorok

Ez a lap összegyűjti a kriptográfia tárgy feladatsorait és beadandóját. Nem önálló fogalomoldal; a feladatok az egyes fogalomoldalakra mutatnak vissza.

## Beadandó (feladatok) — 10 feladat

Egyéni variáns (V1–V4) meghatározása: Neptun-kód 6 karakterének értékéből számolt $s$ alapján $v = 1 + (s \bmod 4)$.

| #   | Téma                                                       | Kapcsolódó fogalomoldal                  |
| --- | ---------------------------------------------------------- | ---------------------------------------- |
| 1   | Betűgyakoriság (26 betű, ékezet nélkül)                    | [[concepts/kript/tortenelmi-titkositok]] |
| 2   | Helyettesítéses titkosítás visszafejtése (monoalfabetikus) | [[concepts/kript/tortenelmi-titkositok]] |
| 3   | Vigenère-titkosítás feltörése (Kasiski/IOC)                | [[concepts/kript/tortenelmi-titkositok]] |
| 4   | Cardano-rács dekódolása ($6 \times 6$, 9 lyuk)             | [[concepts/kript/tortenelmi-titkositok]] |
| 5   | Enigma titkosítás indikátoros eljárással                   | [[concepts/kript/enigma]]                |
| 6   | LFSR: 18 kimeneti bit + Berlekamp-Massey                   | [[concepts/kript/veletlenek]]            |
| 7   | Középső négyzet PRNG periódusa                             | [[concepts/kript/veletlenek]]            |
| 8   | RC4 ($N=8$ állapot): KSA és PRGA                           | [[concepts/kript/veletlenek]]            |
| 9   | SP-hálózat KPA (1 és 2 körös)                              | [[concepts/kript/blokktitkositok]]       |
| 10  | AES-CTR malleability (Man-in-the-middle)                   | [[concepts/kript/blokktitkositok]]       |

**Leadandó:** megoldás PDF + forráskód (Python) + README. Rejtett tesztekkel is ellenőrzik.

## 2. feladatsor — Tökéletes biztonság (tökéletes_biztonság_feladatok)

1. Helyettesítéses/Vigenère/Enigma/karakter-permutáló rejtjel nem tökéletes (500+ karakteres üzenetek).
2. OTP módosítása: $0^\ell \notin \mathcal{K}$ és $0^\ell \notin \mathcal{M}$ — tökéletesen biztonságos-e?
3. Megszüntethetőség kísérletben való biztos nyerés (1 valószínűséggel).
4. $|\mathcal{M}| = |\mathcal{K}|$, egyenletes eloszlású kulcs → tökéletes biztonság?
5. Tökéletesen biztonságos séma max. 100 karakteres szövegekre.
6. Nómenklatúra-titkosítás: 1000 szám, max. kétszer szerepel; oracle típusától függő visszafejtés.

## 3. feladatsor — Véletlenek (véletlenek_feladatsor)

**Számítási biztonság:**
1. Korlátlan számítású támadó esetén nincs számítási biztonságot kielégítő séma.
2. Elhanyagolható függvények zártsága összeadásra és polinommal szorzásra.

**Véletlenek előállítása:**
3. Valódi véletlen azonosítása 3 bit-sorozatból.
4. Szabálytalan pénzérme ($0{,}4 < p < 0{,}6$) szimulálása fair érmére / dobókockára.

**Pszeudo-véletlen generátorok:**
5. Lehmer RNG: $a$ meghatározása $(m, b_1, b_2)$-ből; $a$ és $m$ meghatározása $(b_1,b_2,b_3,b_4)$-ből.
6. LFSR periódus és értékek ($b_4 \oplus b_3 \oplus b_2$ visszacsatolás, 1100 bemenet).
7. Maximális periódus 6-jegyű középső négyzet PRNG-nél.

## Hash feladatsor (hash_feladatok)

- Ütközés-ellenálló $\Rightarrow$ Második őskép-ellenálló $\Rightarrow$ Őskép-ellenálló bizonyítás.
- Születésnap-paradoxon számítások: 16 fős csoport, $n(p;H)$ formula.
- $2^{64}$ db 128-bites hash tároláshoz szükséges terabyte.
- Ütközések keresése specifikus $h$ függvényekre.
- Ütközés-ellenálló kompozíciók ($H_1 \| H_2$, $H(H(x))$).
- Bitcoin proof-of-work számítások.

## MAC feladatsor (mac_feladatok)

1. $t = h(m)$ hash-alapú MAC nem biztonságos.
2. Három CBC-MAC variáns nem biztonságos (EUF-CMA ellenpéldák).
3. Miért nem jó véletlen IV a CBC-MAC-ban?

## Kapocs

- [[concepts/kript/tortenelmi-titkositok]]
- [[concepts/kript/enigma]]
- [[concepts/kript/tokeletes-biztonsag]]
- [[concepts/kript/veletlenek]]
- [[concepts/kript/blokktitkositok]]
- [[concepts/kript/hash-fuggveny]]
- [[concepts/kript/mac]]
- [[subjects/kript]]
