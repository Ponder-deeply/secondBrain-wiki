---
tags: [concept]
sources: [hash.pdf, hash_feladatok.pdf]
derivation: source
updated: 2026-04-22
---

# Hash-függvények

Egy hash-függvény $h: \{0,1\}^* \to \{0,1\}^\ell$ tetszőleges hosszú bemenetet fix hosszú kimenetre képez. A kriptográfiai hash-függvényektől három tulajdonságot várunk.

## Biztonsági tulajdonságok

| Tulajdonság | Definíció | Nehézség |
|---|---|---|
| **Ütközés-ellenállóság** | Nehéz $(x, x')$ pár találni, ahol $x \neq x'$, de $h(x) = h(x')$ | legerősebb |
| **Második őskép-ellenállóság** | Adott $x$, nehéz $x' \neq x$ találni, ahol $h(x') = h(x)$ | közepes |
| **Őskép-ellenállóság** | Adott $y$, nehéz $x$ találni, ahol $h(x) = y$ | leggyengébb |

**Implikáció:** Ütközés-ellenálló $\Rightarrow$ Második őskép-ellenálló $\Rightarrow$ Őskép-ellenálló.

## Születésnap-paradoxon és -támadás

Véletlen $H$ elemű halmazból $n$ elemet választva az ütközés valószínűsége:

$$p(n; H) \approx 1 - e^{-n(n-1)/(2H)}$$

Szükséges minták száma $p$ valószínűségű ütközéshez:

$$n(p; H) \approx \sqrt{2H \cdot \ln \frac{1}{1-p}}$$

**Következmény:** $\ell$-bites hash esetén $\sim 2^{\ell/2}$ próba elég ütközés találásához. Ezért minimum **256 bites** hash szükséges (pl. SHA-256, ahol az ütközési támadáshoz $\sim 2^{128}$ próba kell).

### Példa

16 fős csoportban az azonos születésnap valószínűsége ($H = 365$):
$$p(16; 365) \approx 1 - e^{-16 \cdot 15 / 730} \approx 0{,}284$$

## Alkalmazások

### Biztonságos jelszótárolás

Jelszót soha nem tárolunk egyértelműen; helyette: $\text{tárolt} = h(\text{salt} \| \text{jelszó})$, ahol a `salt` egyedi véletlen érték felhasználónként. Megakadályozza a rainbow table támadásokat.

### Bitcoin és proof-of-work

Célul: $h(\text{block\_header} \| \text{nonce}) < T$ (küszöbérték). A bányász addig növeli a nonce-ot, amíg a feltétel teljesül.
- Bitcoin hálózat hashrate: $\sim 715 \cdot 10^{18}$ hash/s (2024-es adat az előadáson).
- Átlag 10 perces blokkidőhöz a küszöb $\approx 2^{256} / (715 \cdot 10^{18} \cdot 600)$.

### Integritás ellenőrzés

Fájl ujjlenyomata letöltés után; digitális aláírásban az üzenet hash-ét írják alá.

## Ütközés-ellenálló kompozíciók

- Ha $H_1$ vagy $H_2$ ütközés-ellenálló, akkor $H(x) = H_1(x) \| H_2(x)$ is az.
- Ha $H$ ütközés-ellenálló, akkor $H(H(x))$ is az.

## CMAC-kapcsolat

A hash.pdf utolsó diája a CMAC-ot tárgyalja (lásd [[concepts/kript/mac|mac]]):
$\ell$-bites tag, $E_k$ blokktitkosító: $c_0 = 0$, $c_i = E_k(c_{i-1} \oplus m_i)$, tag = $c_n$ első $\ell$ bitje.

## Feladatok

- [[concepts/kript/feladatok]] — hash_feladatok.pdf: ütközés-ellenállóság bizonyítások, születésnap-támadás számítások, Bitcoin proof-of-work

## Kapocs

- [[concepts/kript/mac]] — MAC-ek, amelyek hash-függvényeket és blokktitkosítókat kombinálnak
- [[concepts/kript/veletlenek]] — véletlenszám-generálás, születésnap-paradoxon kapcsolata
- [[subjects/kript]] — tantárgy áttekintő
