---
tags: [concept, dimatii/alkalmazasok-kriptografia]
sources: [DimatIIEa03.pdf]
derivation: source
updated: 2026-09-08
---

# RSA

Rivest, Shamir és Adleman 1977-es nyilvános kulcsú titkosítási eljárása: a kulcspár két nagy prím szorzatából származik, a helyességet az Euler–Fermat-tétel adja, a biztonságot a faktorizáció nehézsége.

## Tartalom

### Kulcsgenerálás

- Legyen $p$ és $q$ két nagy (tipikusan 1024 bites) prím, $n = p \cdot q$.
- Legyen $e \in \{1, \ldots, \varphi(n)\}$ olyan, hogy $(e, \varphi(n)) = 1$.
- Legyen $d$ az $ex \equiv 1 \pmod{\varphi(n)}$ kongruencia megoldása (a bővített euklideszi algoritmussal számítható).

**Nyilvános kulcs:** $(n, e)$. **Titkos kulcs:** $d$.

### Titkosítás és kititkosítás

Adott $0 \le m < n$ üzenet titkosítása

$$c = m^e \bmod n,$$

adott $0 \le c < n$ titkosított üzenet kititkosítása

$$m = c^d \bmod n.$$

Mindkét lépés [[concepts/dimatii/gyors-hatvanyozas]]sal történik.

### Helyesség

$ed \equiv 1 \pmod{\varphi(n)}$ miatt $ed = k \cdot \varphi(n) + 1$ valamely $k$-ra, így

$$c^d \equiv (m^e)^d = m^{e \cdot d} = m^{k \varphi(n) + 1} \equiv m \pmod n,$$

ahol az utolsó lépés az Euler–Fermat-tétel következménye.

### Biztonság

Az eljárás biztonsága azon múlik, hogy az $n = p \cdot q$ szorzatot nem tudjuk hatékonyan faktorizálni — $p$ és $q$ ismeretében ugyanis $\varphi(n)$, és vele $d$ is azonnal adódik.

Nagyságrendek próbaosztásos faktorizálással (Eratoszthenész szitája, $\sim \sqrt{n}$ osztás):

- RSA-2048 esetén $n \sim 2^{2048}$, tehát $\sim 2^{1024}$ próbaosztás;
- másodpercenként $\sim 10^9 \approx 2^{30}$ osztással ez $2^{994}$ másodperc, azaz $2^{969}$ év;
- két géppel $2^{968}$ év; a legjobb ismert algoritmussal is $\sim 2{,}5 \cdot 10^{30}$ év.

Összehasonlításul az univerzum életkora $1{,}38 \cdot 10^{10}$ év.

Fontos gyakorlati megjegyzés: valójában az $m$ üzenet maga is egy *további* titkosításhoz használt titkos kulcs szokott lenni — az RSA-t kulcsszállításra használják, nem hosszú üzenetek titkosítására.

### Példa

$p = 61$, $q = 53$, $n = 3233$, $\varphi(3233) = 60 \cdot 52 = 3120$. Legyen $e = 17$; a bővített euklideszi algoritmus $d = 2753$-at ad.

- Nyilvános kulcs: $(n, e) = (3233, 17)$, titkos kulcs: $d = 2753$.
- Titkosítás $m = 65$-re: $c = 65^{17} \equiv 2790 \pmod{3233}$.
- Kititkosítás: $2790^{2753} \equiv 65 \pmod{3233}$.

### Digitális aláírás

Az $e$ és $d$ szerepének felcserélésével aláírás is generálható: az aláírás $s = m^d \bmod n$, az aláírt üzenet a $(m, s)$ pár, az ellenőrzés pedig az $m \stackrel{?}{\equiv} s^e \pmod n$ egyenlőség. Ha ugyanaz a fél titkosít is és aláír is, ehhez külön $n', e', d'$ kulcshármas kell.

## Kapocs

- [[concepts/dimatii/gyors-hatvanyozas]] — a titkosítás, a kititkosítás és az aláírás számítási magja
- [[concepts/dimatii/diffie-hellman-kulcscsere]] — a másik korai nyilvános kulcsú eljárás, más nehéz problémára építve
- [[concepts/dimatii/diszkret-logaritmus]] — a Diffie–Hellman mögötti nehéz probléma, szemben az RSA faktorizációjával
- [[concepts/kript/titkositasi-sema]] — a $(Gen, Enc, Dec)$ általános keret, amelynek az RSA egy példánya
- [[concepts/bvszam/np-koztes-es-conp]] — a FACTORING $\in \mathrm{NP} \cap \mathrm{coNP}$ bonyolultsági háttér
