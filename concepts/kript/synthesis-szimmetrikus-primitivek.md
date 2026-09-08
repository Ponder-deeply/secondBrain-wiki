---
tags: [synthesis]
sources: [tökéletes_biztonság.pdf, véletlenek.pdf, blokktitkosítók.pdf, folyam_titkositok.pdf, hash.pdf, mac_feladatok.pdf, Titokmegosztás.pdf, történelmi_titkosítók.pdf, enigma.pdf]
derivation: source
updated: 2026-09-04
---

# Szimmetrikus kriptográfia — szintézis

Összefoglaló nézet: a kurzus primitívjei, biztonsági definíciói és támadásmodelljei egyetlen ívben. Nem új anyag — kapcsolatok és ellentétek kiemelése.

## 1. A biztonság spektruma: információelméleti → számítási

| Szint                              | Feltevés                                  | Példa            | Határ                                                                                |
| ---------------------------------- | ----------------------------------------- | ---------------- | ------------------------------------------------------------------------------------ |
| **Információelméleti** (tökéletes) | támadónak korlátlan idő is kevés          | OTP              | $\lvert\mathcal{K}\rvert \geq \lvert\mathcal{M}\rvert$ — gyakorlatban nem skálázható |
| **Számítási** (komputációs)        | támadó polinom idő + elhanyagolható előny | Salsa20, AES-CTR | kulcs $\ll$ üzenet, de feltevés-alapú                                                |

**Kulcs gondolat:** a gyakorlati kriptográfia lemond a tökéletes biztonságról $\Rightarrow$ cserébe rövid kulcs. A CSPRNG-alapú folyamtitkosító ($C = M \oplus \text{Salsa20}_K(v, \text{ctr})$) az OTP gyakorlati helyettesítője — nem tökéletes, de számításilag megkülönböztethetetlen.

→ [[concepts/kript/tokeletes-biztonsag|tokeletes-biztonsag]], [[concepts/kript/folyam-titkositok|folyam-titkositok]]

## 2. Primitívek hierarchiája

```
   véletlen forrás (CSPRNG)
           │
           ▼
   PRG ── PRF ── PRP  ────►  blokktitkosító ($E_k$)
                                 │
           ┌─────────────────────┼────────────────────┐
           ▼                     ▼                    ▼
   üzemmód (CTR, CBC)      CBC-MAC / CMAC        (nincs kulcs)
           │                     │                    │
           ▼                     ▼                    ▼
      titkosság            integritás              hash
     (confidentiality)    (authenticity)       ütközés-ellenállás
```

- **PRG** — rövid seed → hosszabb pszeudovéletlen. LCG, LFSR **nem** PRG (Berlekamp–Massey, Lehmer-inverz triviálisan tör).
- **PRF / PRP** — kulcsolt. Egy blokktitkosító $E_k$ PRP-nek tekintve.
- **Hash** — kulcsolatlan, tehát önmagában nem MAC.

→ [[concepts/kript/veletlenek|veletlenek]], [[concepts/kript/blokktitkositok|blokktitkositok]], [[concepts/kript/hash-fuggveny|hash-fuggveny]]

## 3. Titkosság ≠ integritás

Visszatérő lecke: a pusztán titkosító séma **nem** biztosít integritást.

| Mód | Titkosság | Integritás | Konkrét támadás |
|---|---|---|---|
| CBC | IND-CPA (random IV) | nincs | **bit-flipping**: $C_{i-1}$ bitjének átváltása $M_i$ megfelelő bitjét fordítja |
| CTR | IND-CPA | nincs | **malleability**: $C' = C \oplus (P \oplus P')$, ha $P$ ismert |
| OTP | tökéletes | nincs | $C \oplus \Delta$ tetszőleges átírás |

**Következmény:** minden titkosító mellé külön MAC (encrypt-then-MAC) vagy AEAD (ChaCha20-Poly1305, AES-GCM).

→ [[concepts/kript/blokktitkositok|blokktitkositok]], [[concepts/kript/mac|mac]]

## 4. Támadásmodellek lánca

$$\text{COA} \subset \text{KPA} \subset \text{CPA} \subset \text{CCA}$$

A kurzus konkrét példái minden lépcsőhöz:

| Modell | Példa törés |
|---|---|
| COA | Vigenère (Kasiski + IOC), frekvenciaelemzés monoalfa-helyettesítőn |
| KPA | 1-körös SP-hálózat: $k = x \oplus S^{-1}(P^{-1}(y))$ egyetlen párból. Lehmer-RNG 2 kimenetből. |
| CPA | Enigma (**gardening** — briteknek választott plaintext) |
| CCA | malleable sémák (CBC/CTR MAC nélkül) — dekriptáló-orákulum módosított cipherszöveggel |

**Lehallgatásos kísérlet** ($\mathit{PrivK}^{\text{eav}}$) a COA formalizálása; CPA-ra az orákulum-kibővített változat.

→ [[concepts/kript/tokeletes-biztonsag|tokeletes-biztonsag]], [[concepts/kript/tortenelmi-titkositok|tortenelmi-titkositok]], [[concepts/kript/enigma|enigma]]

## 5. Miért dől össze minden, ha a véletlen rossz

A véletlen a gyökere mindennek — gyenge generátor mindent visszaélhetővé tesz:

- **OTP rossz kulccsal** — pl. LCG-generált "kulcsfolyam" → 3 kimenetből $(a, c, m)$ visszafejthető, teljes kulcsfolyam rekonstruált.
- **LFSR kulcsfolyam** — $2m$ ismert bitből Berlekamp–Massey felfedi a polinomot. Egyszerű LFSR önmagában **sosem** használható folyamtitkosítóként.
- **Nonce-újrahasználat (CTR, Salsa20)** — ugyanaz a keystream → $C_1 \oplus C_2 = M_1 \oplus M_2$ (OTP két-szöveges támadás).
- **Salt nélküli jelszóhash** — előre számolt rainbow table.

→ [[concepts/kript/veletlenek|veletlenek]]

## 6. A születésnap-paradoxon mint tervezési korlát

Ütközés-ellenállás $\ell$ bites hash-re: $\sim 2^{\ell/2}$ próba. **Ezért** minimum 256 bites (SHA-256 → 128 bites ütközési biztonság). Ugyanez határozza meg:

- **Blokktitkosító blokkméret** — 64 bites DES blokk → $\sim 2^{32}$ blokk után CBC/CTR-ben blokk-ütközés (Sweet32 támadás). Modern választás: 128 bit.
- **Nonce hossz** — random nonce esetén $\sim 2^{n/2}$ üzenet után ütközés várható.

→ [[concepts/kript/hash-fuggveny|hash-fuggveny]]

## 7. Konstrukciós csapda: "MAC = F_k XOR-ok"

A mac_feladatok.pdf leckéje általánosítható: **blokkszintű XOR-kompozíció nem biztonságos**, mert bármely szimmetrikus/abeli kombináció újrarendezési vagy törlési támadást enged.

- $t = \bigoplus_i F_k(m_i)$ — blokkok felcserélhetők.
- $t = F_k(r) \oplus \bigoplus_i F_k(\langle i \rangle \| m_i)$ — látszólag pozíció-indexel védve, de $(r, t)$ nyilvános $\Rightarrow$ új $r'$-rel új üzenetre másolható.

**A helyes minta** — láncolás (CBC-MAC), végblokk-megkülönböztetés (CMAC), vagy beágyazott hossz. A lánc megtöri a szimmetriát.

→ [[concepts/kript/mac|mac]]

## 8. Kulcskezelés és titokmegosztás

A kulcs önmaga is titok, ami védeni kell. Shamir $(k,n)$-küszöbséma:

- $k-1$ fokú polinom $\mathbb{F}_q$ felett, $f(0) = s$ titok, részvények $f(i)$.
- $k$ részvényből Lagrange, $< k$-ból **információelméleti** hiány — tökéletes titkosság újra megjelenik, de elosztottan.
- Párhuzam: OTP-ben $|\mathcal{K}| \geq |\mathcal{M}|$; Shamirnál az összes alacsonyabb rendű polinom egyforma valószínű.

→ [[concepts/kript/titokmegosztás|titokmegosztás]]

## 9. A történeti ív mint tanulság

| Kor | Séma | Bukás oka |
|---|---|---|
| ókor–19. sz. | Caesar, Vigenère, Playfair | statisztikai szerkezet (frekvencia, IOC) |
| 2. vh. | Enigma | operációs hibák + CPA (gardening) + gyenge kulcstér-struktúra (önreciproc visszafordító) |
| 1970-es | DES | 56-bites kulcs brute-force-ra rövid |
| 1990-es | RC4 | bias a kulcsfolyamban, KSA gyengesége |
| ma | AES, ChaCha20 | (még) biztonságos |

**Minta:** minden séma addig él, amíg egy új támadásmodell (CPA → CCA) vagy egy új számítási kapacitás (Deep Crack) el nem éri.

→ [[concepts/kript/tortenelmi-titkositok|tortenelmi-titkositok]], [[concepts/kript/enigma|enigma]], [[concepts/kript/blokktitkositok|blokktitkositok]]

## Kapocs

- [[subjects/kript]] — tantárgy áttekintő, tematika
- [[concepts/kript/tokeletes-biztonsag]] — az 1. szakasz alapja
- [[concepts/kript/veletlenek]] — az 5. szakasz alapja
- [[concepts/kript/blokktitkositok]] — 3., 4. szakasz
- [[concepts/kript/mac]] — 3., 7. szakasz
- [[concepts/kript/hash-fuggveny]] — 6. szakasz
- [[concepts/kript/folyam-titkositok]] — 1., 5. szakasz
- [[concepts/kript/titokmegosztás]] — 8. szakasz
- [[concepts/kript/lfsr]] — az 5. szakasz konkrét esete: a linearitás mint bukási ok
