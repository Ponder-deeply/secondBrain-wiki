---
tags: [concept]
sources: [DimatIIEa01.pdf, Dimat2mintaZH1.pdf, dm2gy01_Szamelmelet.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-21
---

# Számrendszerek

Minden pozitív egész egyértelműen felírható egy rögzített $q > 1$ alap hatványainak összegeként; a felírás jegyeit ismételt maradékos osztás adja.

## Tartalom

**Példa.** A $123$ a 10-es számrendszerben $123 = 100 + 20 + 3 = 1\cdot 10^2 + 2 \cdot 10^1 + 3 \cdot 10^0$; a 2-es számrendszerben
$$1111011_{(2)} = 1\cdot 2^6 + 1\cdot 2^5 + 1\cdot 2^4 + 1\cdot 2^3 + 0\cdot 2^2 + 1\cdot 2^1 + 1\cdot 2^0 = 64 + 32 + 16 + 8 + 0 + 2 + 1.$$

**Tétel.** Legyen $q > 1$ rögzített egész. Ekkor bármely $n$ pozitív egész egyértelműen felírható
$$n = \sum_{i=0}^{k} a_i q^i$$
alakban, ahol $0 \leq a_i < q$ és $a_k \neq 0$.

Ez a felírás az $n$ szám $q$ **számrendszerben történő felírása**; $q$ a számrendszer **alapja**, $a_0, \dots, a_k$ az $n$ **jegyei**, és $k = \lfloor \log_q n \rfloor$.

**Bizonyítás** (indukcióval). $n < q$ esetén a tétel igaz ($k = 0$, $a_0 = n$). Tegyük fel, hogy minden $n$-nél kisebb szám egyértelműen felírható $q$ alapú számrendszerben. A [[concepts/dimatii/maradekos-osztas]] tétele szerint egyértelműen létezik $0 \leq a_0 < q$ egész, hogy $q \mid n - a_0$. Az indukciós feltevés alapján írjuk fel $q$ alapú számrendszerben az $\frac{n - a_0}{q} = \sum_{i=1}^{k} a_i q^{i-1}$ számot; a felírás egyértelmű. Ekkor $n = \sum_{i=0}^{k} a_i q^i$. $\square$

### Az átváltás algoritmusa

A bizonyítás módszere közvetlenül algoritmust ad: ismételten vegyük a szám $q$-val vett maradékát (ez a következő jegy), majd osszuk le a maradékkal csökkentett számot $q$-val.

**Példa.** $n = 123$ átírása 2-es számrendszerbe:

| $i$ | $n$ | $n \bmod 2$ | $\frac{n - a_i}{2}$ | jegyek |
|---:|---:|---:|---:|---|
| 0 | 123 | 1 | 61 | 1 |
| 1 | 61 | 1 | 30 | 11 |
| 2 | 30 | 0 | 15 | 011 |
| 3 | 15 | 1 | 7 | 1011 |
| 4 | 7 | 1 | 3 | 11011 |
| 5 | 3 | 1 | 1 | 111011 |
| 6 | 1 | 1 | 0 | 1111011 |

### Feladattípus: számjegyek feltétele (minta-ZH 2b)

Egy szám utolsó $k$ jegye $q$-s számrendszerben a szám $q^k$ szerinti maradéka. Így "$12n$ 8-as számrendszerben $\dots 21$-re végződik" azt jelenti, hogy $12n \equiv 2\cdot8 + 1 = 17 \pmod{64}$, ami [[concepts/dimatii/linearis-kongruencia]] — a megoldhatóság feltétele $(12,64) = 4 \mid 17$. Mivel $4 \nmid 17$ (és $12n$ páros, utolsó oktális jegye is páros), a feladat *szó szerint olvasva* nem megoldható; a forrás nem közli a megoldást, valószínűleg elírás (a minta-feladatsor nem tartalmaz megoldókulcsot). A módszer szemléltetése egy hasonló feladaton (saját példa): $13n \equiv 17 \pmod{64}$-ben $13\cdot5 = 65 \equiv 1$, így $n \equiv 85 \equiv 21 \pmod{64}$; a két legkisebb pozitív megoldás $21$ és $85$ ($13\cdot21 = 273 = 4\cdot64 + 17$, oktálisan $421_{(8)}$).

### Feladattípusok és módszerek (2020. 1. feladatsor)

**1. Átváltás tízesből más alapra.** A fenti algoritmus: ismételt osztás az alappal, a maradékok alulról felfelé a jegyek. A forrás számai:

| szám | 2-es alap | 3-as alap | 5-ös alap |
|---|---|---|---|
| $674$ | $1010100010$ | $220222$ | $10144$ |
| $1864$ | $11101001000$ | $2120001$ | $24424$ |
| $376529$ | $1011011111011010001$ | $201010111112$ | $44022104$ |

Ellenőrzés visszaszorzással: pl. $674 = 512 + 128 + 32 + 2 = 1010100010_{(2)}$.

**2. Műveletek adott alapban.** A jegyenkénti tanult algoritmusok (átvitellel) érvényesek bármely alapban; a kérdések: összeadás, szorzás, maradékos osztás $2$-, $3$-, $5$- és $7$-es alapban (pl. $1001_{(2)}\cdot 1101_{(2)} = 9\cdot 13 = 117 = 1110101_{(2)}$). Ellenőrzésül érdemes tízesre visszaváltani.

**3. Negatív alap.** Ha $b < -1$, minden egész felírható $a = \sum a_i b^i$ alakban $0 \le a_i \le |b|-1$ jegyekkel; az átváltás ugyanaz, csak a maradékot $0 \le r < |b|$ szerint vesszük, a hányados $(a - r)/b$. A forrás $-5$ alapú feladatai: $-121 = 1004_{(-5)}$ ($-125 + 4$), $127 = 14002_{(-5)}$ ($625 - 500 + 2$), $2636 = 1404131_{(-5)}$ ($15625 - 12500 - 500 + 25 - 15 + 1$). Negatív számhoz sem kell előjel — ez a negatív alap előnye. A forrás 22. feladata magának a tételnek a bizonyítása (a [[concepts/dimatii/maradekos-osztas]] tételével, a fenti indukcióval azonos gondolatmenet, de a hányados abszolútértéke csökken).

**4. Utolsó jegyek mint maradékok.** Az utolsó $k$ jegy $b$-s alapban az $n \bmod b^k$ maradék jegyei; ezért a „milyen jegyre végződik" feladatok kongruenciák, lásd [[concepts/dimatii/linearis-kongruencia]] és [[concepts/dimatii/szimultan-kongruenciak]].

## Kapocs

- [[concepts/dimatii/maradekos-osztas]] — a felírás létezésének és egyértelműségének eszköze
- [[concepts/dimatii/oszthatosag]] — az alapfogalom

