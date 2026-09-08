---
tags:
  - subject
sources:
  - történelmi_titkosítók.pdf
  - Titokmegosztás.pdf
  - enigma.pdf
  - folyam_titkositok.pdf
  - hash.pdf
  - blokktitkosítók.pdf
  - véletlenek.pdf
  - tökéletes_biztonság.pdf
  - feladatok.pdf
  - véletlenek_feladatsor.pdf
  - hash_feladatok.pdf
  - mac_feladatok.pdf
  - tökéletes_biztonság_feladatok.pdf
derivation: source
updated: 2026-09-04
state: "[[IV]]"
---

# Kriptográfia és biztonság

IV. szemeszter kötelező tárgy. Témái: klasszikus és modern titkosítók, formális biztonsági modellek, szimmetrikus primitívek (blokk- és folyamtitkosítók, hash, MAC), titokmegosztás, véletlenszám-generálás.

## Tematika

### 1. Klasszikus titkosítók
Betűszintű transzformációk: Caesar-eltolás, monoalfabetikus helyettesítés, Vigenère, Playfair, Beaufort, ADFGVX, Rail fence, Cardano-rács. Frekvenciaelemzés, Kasiski-módszer, IOC.

→ [[concepts/kript/tortenelmi-titkositok|tortenelmi-titkositok]]
→ [[concepts/kript/titkositasi-sema|titkositasi-sema]]
→ [[concepts/kript/vigenere-titkositas|vigenere-titkositas]]
→ [[concepts/kript/tamadasmodellek|tamadasmodellek]]

### 2. Enigma
Elektromechanikus rotor-gép. Tárcsák, visszafordító, kapcsolótábla. Kulcstér $\approx 2^{77{,}5}$. Lengyel (Rejewski) és brit (Turing) kriptanalízis, bomba, cribs.

→ [[concepts/kript/enigma|enigma]]

### 3. Tökéletes biztonság
Formális titkosítási séma ($Gen$, $Enc$, $Dec$). Tökéletes biztonság: $\Pr[M=m] = \Pr[M=m \mid C=c]$. Lehallgatásos kísérlet. OTP. Shannon-tétel. $|\mathcal{K}| \geq |\mathcal{M}|$ szükséges. Támadásmodellek: COA, KPA, CPA, CCA.

→ [[concepts/kript/tokeletes-biztonsag|tokeletes-biztonsag]]

### 4. Véletlenszám-generálás
PRNG vs. CSPRNG. Középső négyzet, Lehmer RNG, LCG, LFSR (Berlekamp-Massey), RC4. NIST 14-tesztes csomag. Biased coin → fair bit (von Neumann).

→ [[concepts/kript/veletlenek|veletlenek]]
→ [[concepts/kript/linearis-kongruencialis-generator|linearis-kongruencialis-generator]]
→ [[concepts/kript/lfsr|lfsr]]

### 5. Blokktitkosítók
SP-hálózat (S-box + permutáció + körkulcs). Feistel-hálózat. DES (56-bites kulcs, 16-körös Feistel). Triple-DES. CBC mód (bit-flipping támadás). CTR mód (malleability). KPA: 1-körös direkt, 2-körös MITM.

→ [[concepts/kript/blokktitkositok|blokktitkositok]]

### 6. Hash-függvények
Ütközés-, második őskép-, őskép-ellenállóság. Születésnap-paradoxon: $n(p;H) \approx \sqrt{2H \ln \frac{1}{1-p}}$. 256 bites minimum. Bitcoin proof-of-work. Jelszótárolás (salt + hash).

→ [[concepts/kript/hash-fuggveny|hash-fuggveny]]

### 7. MAC
CBC-MAC: $c_0=0$, $c_i = E_k(c_{i-1} \oplus m_i)$. Változó hosszú és kulcs-újrahasználati támadások. CMAC (OMAC): alkulcsok $k_1$/$k_2$ deriválása, biztonságos változó hosszú üzenetekre. EUF-CMA biztonság.

→ [[concepts/kript/mac|mac]]

### 8. Folyamtitkosítók
Salsa20 (256-bites kulcs, doubleround×10, nonce+counter), ChaCha20 (TLS 1.3, WireGuard). Biztonsági szintek: Salsa20/7 ≈ $2^{109}$, ChaCha7 ≈ $2^{248}$.

→ [[concepts/kript/folyam-titkositok|folyam-titkositok]]

### 9. Titokmegosztás
Shamir $(k,n)$-küszöbséma: $k-1$ fokú polinom $\mathbb{F}_q$ felett, Lagrange-interpoláció. Vizuális titokmegosztás (Naor–Shamir): pixelfelosztás, $(2,2)$ és $(n,k)$ sémák OR-dekódolással.

→ [[concepts/kript/titokmegosztás|titokmegosztás]]

## Szintézis

→ [[concepts/kript/synthesis-szimmetrikus-primitivek|synthesis-szimmetrikus-primitivek]] — kurzus-átfogó nézet: biztonsági spektrum, primitív-hierarchia, támadásmodellek láncolata, véletlen szerepe, történeti bukás-minta

## Feladatsorok és beadandó

→ [[concepts/kript/feladatok|feladatok]] — 10-feladatos beadandó (V1–V4 variánsok) + 4 feladatsor

## Fogalomindex

| Fogalom | Oldal |
|---|---|
| Monoalfabetikus, Playfair, ADFGVX, Cardano | [[concepts/kript/tortenelmi-titkositok]] |
| $(Gen, Enc, Dec)$, Kerckhoffs-elv, Caesar | [[concepts/kript/titkositasi-sema]] |
| Vigenère, Kasiski, index of coincidence | [[concepts/kript/vigenere-titkositas]] |
| COA, KPA, CPA, CCA | [[concepts/kript/tamadasmodellek]] |
| Enigma, bomba, crib, Rejewski, Turing | [[concepts/kript/enigma]] |
| OTP, tökéletes biztonság, Shannon-tétel | [[concepts/kript/tokeletes-biztonsag]] |
| PRNG, CSPRNG, RC4, NIST-tesztek, fair bit | [[concepts/kript/veletlenek]] |
| Lehmer RNG, LCG, RANDU | [[concepts/kript/linearis-kongruencialis-generator]] |
| LFSR, primitív polinom, Berlekamp–Massey | [[concepts/kript/lfsr]] |
| SP-hálózat, Feistel, DES, CBC, CTR | [[concepts/kript/blokktitkositok]] |
| Hash, születésnap-támadás, SHA-256, PoW | [[concepts/kript/hash-fuggveny]] |
| CBC-MAC, CMAC, EUF-CMA | [[concepts/kript/mac]] |
| Salsa20, ChaCha20, folyamtitkosítók | [[concepts/kript/folyam-titkositok]] |
| Shamir-séma, vizuális titokmegosztás | [[concepts/kript/titokmegosztás]] |
