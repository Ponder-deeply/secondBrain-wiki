---
tags: [concept]
sources: [folyam_titkositok.pdf]
derivation: source
updated: 2026-04-22
---

# Folyamtitkosítók

A folyamtitkosítók (stream ciphers) egy kulcsfolyamot (keystream) generálnak, amellyel az üzenetet bitenként vagy byte-onként XOR-olják. Hatékonyabbak lehetnek blokktitkosítóknál streaming alkalmazásokban.

## Általános modell

$$C = M \oplus KS, \quad KS = \text{Salsa20}_K(v, \text{ctr})$$

ahol $K$ a kulcs, $v$ a nonce, $\text{ctr}$ a blokk-számláló.

## Salsa20

Tervező: Daniel Bernstein (2005). eSTREAM-győztes.

**Paraméterek:**
- 32 bájtos (256 bites) kulcs
- 8 bájtos nonce
- 8 bájtos blokk-számláló
- Kimeneti blokk: 64 bájt

**Belső állapot:** 16 db 32-bites szó ($4 \times 4$-es mátrix), amelynek felépítése:

$$\begin{pmatrix} \sigma_0 & K_0 & K_1 & K_2 \\ K_3 & \sigma_1 & v_0 & v_1 \\ \text{ctr}_0 & \text{ctr}_1 & \sigma_2 & K_4 \\ K_5 & K_6 & K_7 & \sigma_3 \end{pmatrix}$$

ahol $\sigma$ a `"expand 32-byte k"` konstans szavai.

**Quarterround:**

$$\text{quarterround}(a, b, c, d):$$
$$b \mathrel{\oplus}= (a + d) \lll 7$$
$$c \mathrel{\oplus}= (b + a) \lll 9$$
$$d \mathrel{\oplus}= (c + b) \lll 13$$
$$a \mathrel{\oplus}= (d + c) \lll 18$$

**Doubleround:** egy sor-kör + egy oszlop-kör (mindkettő 4 quarterround).

**Salsa20:** $\text{doubleround}^{10}(x) + x$ (azaz 20 körös, és hozzáadódik az eredeti állapot).

## ChaCha20

A Salsa20 módosított változata (Bernstein, 2008); IETF RFC 8439, TLS 1.3 és WireGuard VPN.

**Quarterround (ChaCha20):**

$$a \mathrel{+}= b;\; d \mathrel{\oplus}= a;\; d \lll= 16$$
$$c \mathrel{+}= d;\; b \mathrel{\oplus}= c;\; b \lll= 12$$
$$a \mathrel{+}= b;\; d \mathrel{\oplus}= a;\; d \lll= 8$$
$$c \mathrel{+}= d;\; b \mathrel{\oplus}= c;\; b \lll= 7$$

Az állapotmátrix oszlopain, majd átlóin alkalmazva adja a körönkénti keverést.

**Különbség Salsa20-tól:** más quarterround, más állapotmátrix-felépítés (nonce 96 bit, counter 32 bit az IETF-változatban).

## Biztonsági szintek

| Verzió | Legismertebb támadás | Szükséges adat |
|---|---|---|
| Salsa20/7 | $\sim 2^{109}$ |  |
| ChaCha7 | $\sim 2^{248}$ |  |
| Salsa20/12, ChaCha12 | nincs ismert | — |
| Salsa20/20, ChaCha20 | nincs ismert | — |

## Felhasználás

- **TLS 1.3:** `TLS_CHACHA20_POLY1305_SHA256` cipher suite.
- **WireGuard VPN:** ChaCha20-Poly1305 (titkosítás + hitelesítés).
- **libsodium:** Salsa20 alapú `crypto_stream_salsa20`.

## Kapocs

- [[concepts/kript/veletlenek]] — CSPRNG-ek, LFSR-ek, amelyek kulcsfolyam-előállítók is lehetnek
- [[concepts/kript/blokktitkositok]] — CTR mód: blokktitkosítóból is készíthető folyamtitkosító
- [[concepts/kript/tokeletes-biztonsag]] — OTP vs. folyamtitkosítók biztonsági összehasonlítása
- [[subjects/kript]] — tantárgy áttekintő
