---
tags: [concept]
sources: [Titokmegosztás.pdf]
derivation: source
updated: 2026-04-22
---

# Titokmegosztás

A titokmegosztás (secret sharing) egy titkot $n$ résztvevő között oszt szét úgy, hogy csak elegendően nagy (legalább $k$) résztvevő együttesen tudja visszaállítani, kisebb csoport semmit sem tud meg.

## Shamir-féle küszöbséma

**Cél:** $(k, n)$-küszöbséma — $k$ részesből visszaállítható, $k-1$-ből nem.

**Felépítés:**

1. Válassz egy $q > n$ prímszámot és egy $s \in \mathbb{F}_q$ titkot.
2. Véletlenszerűen válassz egy $k-1$ fokú polinomot: $f(x) = s + a_1 x + \cdots + a_{k-1} x^{k-1}$ felett $\mathbb{F}_q$-n.
3. Az $i$-edik résztvevő megkapja az $(i, f(i))$ pontot.

**Visszaállítás:** bármely $k$ pont alapján Lagrange-interpolációval:

$$s = f(0) = \sum_{i=1}^{k} y_i \prod_{j \neq i} \frac{-x_j}{x_i - x_j} \pmod{q}$$

**Biztonság:** $k-1$ pont semmit sem árul el $s$-ről (információelméletileg tökéletes).

## Vizuális titokmegosztás (Naor–Shamir, 1994)

**Cél:** egy titkos képet $n$ transzparensre oszt szét; csak $k$ transzparens egymásra helyezésével látható a kép — dekódoláshoz nincs szükség számításra.

### (2,2)-séma — pixelfelosztás

Minden titkos pixel két részes pixel-pár szerint kódolódik:

| Titkos pixel | 1. rész | 2. rész | Eredmény |
|---|---|---|---|
| Fehér | ██░░ | ██░░ | ██░░ (félig fekete) |
| Fekete | ██░░ | ░░██ | ████ (teljesen fekete) |

- Egymásra helyezve: fekete pixel → fekete, fehér pixel → szürkés (kevesebb fekete) → kontrasztból olvasható.
- **Egyetlen transzparens:** véletlenszerű zajnak látszik (tökéletes titok).

### Általános $(n, k)$-séma

- Minden pixel $m$ részes blokkra bontódik (kontraszt: $\alpha = m_{\text{white}} / m_{\text{black}}$).
- A felosztási mátrixokat ($C_0$ fehér, $1$ fekete pixelhez) úgy kell megkonstruálni, hogy:
  - bármely $k$ rész OR-ja megkülönböztethetően sötétebb legyen fehér pixelnél,
  - bármely $k-1$ rész OR-ja véletlenszerű eloszlású legyen.

## Alkalmazások

- Titkos kulcs (pl. CA masterkey) megosztása biztonsági tisztek közt.
- Banki PIN kódok megosztott custodianship-je.
- Vizuális séma: pecsétek, bankjegyek rejtett vizuális hitelesítése.

## Feladatok

- Shamir-séma: $f(x)$ meghatározása adott pontokból, titok visszaállítása.
- Vizuális séma: felosztási mátrixok tervezése adott $(n,k)$ paraméterekre.

## Kapocs

- [[concepts/kript/tokeletes-biztonsag]] — információelméletileg tökéletes biztonság
- [[subjects/kript]] — tantárgy áttekintő
