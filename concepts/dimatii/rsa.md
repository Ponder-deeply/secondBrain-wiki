---
tags: [concept]
sources: [DimatIIEa03.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, Lehman-Leighton-Meyer-Mathematics-for-Computer-Science.pdf, dm2gy05_Szamelmelet.pdf, dm2gy06.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-21
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

ahol az utolsó lépés az Euler–Fermat-tétel következménye (ez $(m,n)=1$-et használ; a ritka $(m,n)>1$ esetben az állítás a kínai maradéktétellel, prímenként igazolható).

Prímenként (Farkas-féle levezetés): $(m^e)^d = m^{k(p-1)(q-1)+1} = \left(m^{p-1}\right)^{k(q-1)}\cdot m \equiv m \pmod p$, mert ha $p \mid m$, akkor $0 \equiv 0$, ha $p \nmid m$, akkor $m^{p-1} \equiv 1 \pmod p$. Hasonlóan $(m^e)^d \equiv m \pmod q$, és a kínai maradéktétel adja, hogy $m = c^d \bmod n$. Az $e$ véletlen választása nem jó, ha $(e, (p-1)(q-1)) > 1$, mert ekkor nincs $d$.

### Biztonság

Az eljárás biztonsága azon múlik, hogy az $n = p \cdot q$ szorzatot nem tudjuk hatékonyan faktorizálni — $p$ és $q$ ismeretében ugyanis $\varphi(n)$, és vele $d$ is azonnal adódik.

Nagyságrendek próbaosztásos faktorizálással ($\sim \sqrt{n}$ osztás):

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

### Séma, biztonság és a SAT-kapcsolat (Lehman–Leighton–Meyer 9.11–9.12)

- **Nyilvános kulcsú elv.** A fogadó két kulcsot készít: a nyilvános $(e,n)$-et bárki használhatja küldéshez, a titkos $d$-t csak ő ismeri; a feleknek nem kell előre kulcsot cserélniük. (Turing szimmetrikus, prím modulusú „2.0-ás” kódjával szemben az RSA a *két* prím szorzata szerint dolgozik, és *hatványozással* titkosít.)
- **Kulcsgenerálás.** $n = pq$, $e$ olyan, hogy $(e,(p-1)(q-1)) = 1$; $d$ az $e$ inverze $\mathbb{Z}_{(p-1)(q-1)}$-ben (bővített euklideszi algoritmus). Titkosítás $\hat m = m^e \pmod n$, visszafejtés $m = \hat m^d \pmod n$; a helyesség az Euler-tételből jön ($\varphi(pq) = (p-1)(q-1)$, lásd [[concepts/dimatii/euler-fi-fuggveny]]), és $m$ nem relatív prím $n$-hez esetén is működik.
- **Biztonság.** $p,q$ ismeretében $d$ azonnal adódik. Megfordítva: a nyilvános *és* a titkos kulcsból $n$ könnyen faktorizálható, tehát a titkos kulcs nyilvánosból való kitalálása legalább olyan nehéz, mint a faktorizálás. Nem bizonyított, hogy *bármely* feltörés faktorizálást adna; a bizalmat a közel 40 év sikertelen támadás adja. Ezért $e$ és $d$ gyakorlatban nem lehet „túl kicsi”.
- **SAT és faktorizálás.** Két $n$ bites szám szorzatát ellenőrző áramkör $\sim n^2$ kapuval építhető; $m$ egy tényezőjét SAT-tesztek sorozatával, jegyenként lehet megkapni ($n$ SAT-hívás). Ha a SAT polinomidőben megoldható volna, a faktorizálás és vele az RSA is „könnyű” lenne.

### Feladattípusok (2020. 5. feladatsor, 2024. 6. sorozat)

**Módszer.** (1) $n = pq$, $\varphi(n) = (p-1)(q-1)$; (2) $e$ választása $(e,\varphi(n)) = 1$ szerint; (3) $d \equiv e^{-1} \pmod{\varphi(n)}$ a [[concepts/dimatii/bovitett-euklideszi-algoritmus]]sal; (4) $c = m^e \bmod n$, $m = c^d \bmod n$ ([[concepts/dimatii/gyors-hatvanyozas]]). Ellenőrzés: $ed \equiv 1 \pmod{\varphi(n)}$ és $c^d$ visszaadja $m$-et.

**1. Kulcsgenerálás és titkosítás** (6. sorozat 1. feladat): $p = 11$, $q = 13$, $e = 7$: $n = 143$, $\varphi(n) = 120$, $d = 103$ ($7\cdot 103 = 721 = 6\cdot 120 + 1$). Az $m = 4$ üzenet titkosítva $c = 4^7 \bmod 143 = 82$ ($4^7 = 16384$), és $82^{103} \equiv 4 \pmod{143}$.

**2. Visszafejtés** (6. sorozat 2. feladat): $p = 7$, $q = 13$, $e = 5$, $n = 91$, $\varphi(n) = 72$, $d = 29$ ($5\cdot 29 = 145 = 2\cdot 72 + 1$); $c = 2$-re $m = 2^{29} \bmod 91 = 32$. Ellenőrzés: $32^5 = 2^{25} \equiv 2 \pmod{91}$.

**3. Faktorizálás után** (6. sorozat 3. feladat, „érdekes"): $n = 221$ kicsi, tehát faktorizálható: $221 = 13\cdot 17$, $\varphi = 12\cdot 16 = 192$, $e = 5$ relatív prím hozzá, $d = 77$ ($5\cdot 77 = 385 = 2\cdot 192 + 1$); $c = 2$-ből $m = 2^{77} \bmod 221 = 32$. Itt $32^5 = 2^{25} \equiv 2 \pmod{221}$ — a lehallgatott üzenetet a nyilvános kulcsból a modulus kis mérete miatt fejtjük meg. Ez a gyakorlati tanulság: a biztonság a faktorizáció nehézségén múlik (lásd fent).

**4. Szabad $e$ választás** (2020. 5. feladatsor 17. feladata): $p = 29$, $q = 31$, $n = 899$, $\varphi(n) = 28\cdot 30 = 840 = 2^3\cdot 3\cdot 5\cdot 7$, tehát az $e$ nem lehet osztható $2$-vel, $3$-mal, $5$-tel, $7$-tel; a legkisebb jó $e = 11$ (a forrás nem rögzít értéket), ekkor $d = 611$ ($11\cdot 611 = 6721 = 8\cdot 840 + 1$). A $134$ üzenet titkosítva $134^{11} \bmod 899 = 19$; a $219$ üzenet kititkosítva $219^{611} \bmod 899 = 343$ (ellenőrzés: $343^{11} \equiv 219$). Más $e$ más $c$-t és $d$-t ad.

**Tipikus hibák.** $\varphi(n)$ helyett $n - 1$ vagy $(p-1) + (q-1)$ használata; az $e$ választásakor a relatív prímséget nem ellenőrizni; a $d$-t $\bmod n$ képezni $\bmod\ \varphi(n)$ helyett; kézi számolásnál a hatványozást nem lépcsőzetesen (négyzetre emeléssel) végezni.

## Kapocs

- [[concepts/dimatii/gyors-hatvanyozas]] — a titkosítás, a kititkosítás és az aláírás számítási magja
- [[concepts/dimatii/diffie-hellman-kulcscsere]] — a másik korai nyilvános kulcsú eljárás, más nehéz problémára építve
- [[concepts/dimatii/diszkret-logaritmus]] — a Diffie–Hellman mögötti nehéz probléma, szemben az RSA faktorizációjával
- [[concepts/kript/titkositasi-sema]] — a $(Gen, Enc, Dec)$ általános keret, amelynek az RSA egy példánya
- [[concepts/bvszam/np-koztes-es-conp]] — a FACTORING $\in \mathrm{NP} \cap \mathrm{coNP}$ bonyolultsági háttér
- [[concepts/dimatii/turing-kodja]] — a szorzásos titkosítás és megtörése, az RSA előzménye
- [[concepts/dimatii/szamelmeleti-nyitott-problemak]] — a faktorizálás nehézsége, kapcsolat a SAT-tal
