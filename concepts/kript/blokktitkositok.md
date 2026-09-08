---
tags: [concept]
sources: [blokktitkosítók.pdf]
derivation: source
updated: 2026-04-22
---

# Blokktitkosítók

A blokktitkosítók fix hosszú blokkokat titkosítanak egy szimmetrikus kulccsal. Alapvető építőkövek a modern kriptográfiában.

## SP-hálózat (Substitution-Permutation Network)

Egy kör: $E_k(x) = P(S(x \oplus k))$, ahol:
- $S$: S-box — nemlineáris helyettesítés (nibble-önként, pl. 4 bites → 4 bites),
- $P$: bit-permutáció — diffúzió,
- $k$: körkulcs.

Több kör egymás után adja a tényleges titkosítót.

### KPA-támadás SP-hálózaton

**1-körös eset:** ismert $(x, y)$ pár alapján $k = x \oplus S^{-1}(P^{-1}(y))$. Egyetlen pár elég.

**2-körös eset (MITM — meet-in-the-middle):**
- $E_{k_1, k_2}(x) = E_{k_2}(E_{k_1}(x))$
- Előre: minden $k_1$-re számold $t = E_{k_1}(x)$, tárold $(t \mapsto k_1)$.
- Visszafelé: minden $k_2$-re számold $t' = E_{k_2}^{-1}(y)$, keresd az egyezést.
- Kulcstér $2 \times 2^n$ helyet $2^n$ tárolóra redukál.

## Feistel-hálózat

Minden kör: $L_{i+1} = R_i$, $R_{i+1} = L_i \oplus F_{k_i}(R_i)$.

- $F$ nem szükséges invertálható.
- Visszafejtés: $R_i = L_{i+1}$, $L_i = R_{i+1} \oplus F_{k_i}(L_{i+1})$.
- 16 kör, 64-bites blokk, 48-bites körkulcsok (DES).

## DES

- 64-bites blokk, 56-bites kulcs, 16-körös Feistel.
- Minden kör: $R_{i+1} = L_i \oplus F(R_i, k_i)$, ahol $F$ tartalmaz kiterjesztést ($32 \to 48$ bit), XOR körkulccsal, 8 S-box ($6 \to 4$ bit), permutáció.
- **Biztonság:** 56 bites kulcs brute-force-szal feltörhető (1998: Deep Crack, 22 óra).
- **Triple-DES (3DES):** $C = E_{k_3}(D_{k_2}(E_{k_1}(M)))$; effektív kulcshossz 112 bit MITM miatt.

## Üzemmódok

### CBC (Cipher Block Chaining)

$$C_i = E_k(M_i \oplus C_{i-1}), \quad C_0 = IV$$

- Visszafejtés: $M_i = D_k(C_i) \oplus C_{i-1}$.
- **Bit-flipping támadás:** $C_{i-1}$ egy bitjének megváltoztatása $M_i$ megfelelő bitjét megfordítja (szándékos módosítás lehetséges, ha a struktúra ismert).
- Nincs hitelesség — MAC szükséges mellé.

### CTR (Counter Mode)

$$C_i = M_i \oplus E_k(\text{nonce} \| i)$$

- Párhuzamos titkosítás/visszafejtés lehetséges.
- **Malleability (formálhatóság):** $C' = C \oplus (P \oplus P')$ → tetszőleges $P'$-re előállítható $C'$ a keystream ismerete nélkül, ha $P$ ismert. Ez a CTR-AES-128 alapú man-in-the-middle támadás alapja.

## Feladatok

- [[concepts/kript/feladatok]] — 9. feladat (SP-hálózat KPA, 1 és 2 körös), 10. feladat (AES-CTR malleability)

## Kapocs

- [[concepts/kript/mac]] — CBC-MAC, az integritás biztosítása blokktitkosítóval
- [[concepts/kript/tokeletes-biztonsag]] — CPA-biztonság definíciója
- [[subjects/kript]] — tantárgy áttekintő
