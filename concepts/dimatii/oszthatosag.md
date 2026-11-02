---
tags: [concept]
sources: [DimatIIEa01.pdf, Lehman-Leighton-Meyer-Mathematics-for-Computer-Science.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, dm2gy01_Szamelmelet.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-21
---

# Oszthatóság

Az egész számok körében az osztás nem mindig végezhető el maradék nélkül; az oszthatóság reláció pontosan azt rögzíti, mikor igen.

## Tartalom

**Definíció.** Az $a$ egész **osztja** a $b$ egészet — jelölés: $a \mid b$ —, ha létezik olyan $c$ egész, mellyel $a \cdot c = b$, azaz $b/a$ szintén egész.

Racionális számok körében az $a/b$ osztás mindig elvégezhető, és az eredmény is racionális. Egészek körében viszont nem: a hányados nem feltétlenül egész. Ez teszi az oszthatóságot érdemi relációvá.

**Példák.** $1 \mid 13$, mert $1 \cdot 13 = 13$; $1 \mid n$ minden $n$-re; $6 \mid 12$, mert $6 \cdot 2 = 12$; $-6 \mid 12$, mert $(-6)\cdot(-2) = 12$.

A definíció szó szerint kiterjeszthető más számkörökre is, például a **Gauss-egészekre**, $\{a + bi \,:\, a,b \in \mathbb{Z}\}$. Ott például $i \mid 13$, mert $i \cdot (-13i) = 13$, és $1 + i \mid 2$, mert $(1+i)(1-i) = 2$.

### Az oszthatóság tulajdonságai

Minden $a, b, c, \dots \in \mathbb{Z}$ esetén:

1. $a \mid a$ (reflexivitás);
2. $a \mid b$ és $b \mid c \Rightarrow a \mid c$ (tranzitivitás);
3. $a \mid b$ és $b \mid a \Rightarrow a = \pm b$;
4. $a \mid b$ és $a' \mid b' \Rightarrow aa' \mid bb'$;
5. $a \mid b \Rightarrow ac \mid bc$;
6. $ac \mid bc$ és $c \neq 0 \Rightarrow a \mid b$;
7. $a \mid b_1, \dots, a \mid b_k \Rightarrow a \mid c_1b_1 + \cdots + c_kb_k$ minden $c_1, \dots, c_k$ egész esetén;
8. $a \mid 0$, ugyanis $a \cdot 0 = 0$;
9. $0 \mid a \iff a = 0$;
10. $1 \mid a$ és $-1 \mid a$.

A 7. pont a leggyakrabban használt: **egy közös osztó az egész együtthatós lineáris kombinációt is osztja**. Erre épül az euklideszi algoritmus helyességének bizonyítása is.

**Példák.** $2 \mid 6$ és $6 \mid 12 \Rightarrow 2 \mid 12$; $2 \mid 4$ és $3 \mid 9 \Rightarrow 2\cdot 3 \mid 4 \cdot 9$; $3 \mid 6$ és $3 \mid 9 \Rightarrow 3 \mid 6c_1 + 9c_2$.

### Lineáris kombináció

**Definíció.** Az $n$ egész a $b_0, \dots, b_k$ számok **lineáris kombinációja** (*linear combination*), ha $n = s_0b_0 + s_1b_1 + \cdots + s_kb_k$ valamilyen $s_0, \dots, s_k$ egészekkel. A 7. tulajdonság ezzel így szól: ha $a$ osztja $b$-t és $c$-t, akkor osztja $b$ és $c$ minden lineáris kombinációját is. Bizonyítás: $ak_1 = b$, $ak_2 = c$ esetén $sb + tc = a(sk_1 + tk_2)$.

Néhány közvetlen következmény: $n \mid 0$, $n \mid n$, $\pm 1 \mid n$, és $0 \mid n$ csak $n = 0$ esetén áll. Az osztás olyan egyszerűnek látszó fogalom, hogy megoldatlan kérdésekhez vezet: *tökéletes* szám, amely egyenlő a pozitív valódi osztói összegével ($6 = 1+2+3$, $28 = 1+2+4+7+14$); a páros tökéletes számokat Euklidész jellemezte, páratlan tökéletes szám létezése ismeretlen (Lehman–Leighton–Meyer 9.1).

### Oszthatóság $\mathbb{N}$-ben és egységelemes integritási tartományban

*(Farkas Gábor előadásdiái, 6.1.)* A definíció természetes számokra: $m \mid n$, ha $\exists k \in \mathbb{N}: n = m\cdot k$ ($n$ az $m$ többszöröse). $m \neq 0$ esetén a regularitás miatt legfeljebb egy ilyen $k$ létezik, és $m \mid n \iff n/m \in \mathbb{N}$.

Az $\mathbb{N}$-beli tulajdonságok az $\mathbb{Z}$-belieken túl: minden természetes szám osztója a nullának; a nulla csak önmagának osztója; ha $m \mid n$, $n \neq 0$, akkor $m \leq n$; a $\mid$ reláció **reflexív, tranzitív és antiszimmetrikus**, azaz részbenrendezés. Bár $\mathbb{N}^+$-on a $\mid$ a $\leq$ leszűkítése, $\mathbb{N}$-ben a $0$ **maximális elem** a $\mid$ relációra nézve.

Egy tetszőleges $R$ **egységelemes integritási tartományban** ugyanezek érvényesek ($b \mid a,\ b' \mid a' \Rightarrow bb' \mid aa'$; $0$ minden elemnek többszöröse, csak önmagának osztója; $1 \mid a$; $b \mid a \Rightarrow bc \mid ac$; $bc \mid ac,\ c \neq 0 \Rightarrow b \mid a$; $b \mid a_i \Rightarrow b \mid \sum c_i a_i$), de a $\mid$ csak **reflexív és tranzitív** — antiszimmetria nincs, mert $a \mid b \wedge b \mid a$ csak asszociáltságot ad ($\mathbb{Z}$-ben $a = \pm b$).

Egész számokra a $|km| = |k|\cdot|m|$ miatt: $a \mid b \wedge b \neq 0 \Rightarrow |a| \leq |b|$.

**Definíció.** A 2-vel osztható egészek a **páros számok**; **páratlan** az az egész, amely nem páros.

### Feladattípusok és módszerek (2020. 1. feladatsor)

**1. „Bizonyítsuk be, hogy $k \mid f(n)$".** Három szokásos út: (i) *szorzattá alakítás* — a tényezőkből a prímhatványok külön igazolhatók; (ii) *maradékosztályok szerinti esetszétválasztás* ($n \bmod 2$, $\bmod 3$ …); (iii) *kongruenciák / Fermat* (lásd [[concepts/dimatii/euler-fermat-tetel]]). Ha $k$ prímhatványok szorzata, a prímhatványokra külön elég igazolni.

- $6 \mid n(n+1)(2n+1)$: $n(n+1)$ páros; $3$-mal: ha $n \equiv 0$, $n \mid$; ha $n \equiv 1$, $3 \mid 2n+1$; ha $n \equiv 2$, $3 \mid n+1$.
- $30 \mid m^5 - m = m(m-1)(m+1)(m^2+1)$: három egymást követő szám szorzata osztható $6$-tal; $5$-tel a Fermat-tétel ($m^5 \equiv m \bmod 5$), vagy $m \bmod 5$ szerinti esetek.
- $960 = 64\cdot 15 \mid a(a^2-1)(a^2-4)$, ha $a$ páros, de $4 \nmid a$: a kifejezés $(a-2)(a-1)a(a+1)(a+2)$, öt egymást követő szám szorzata, így $3$ és $5$ osztja; $a = 2k$, $k$ páratlan esetén $a(a^2-4) = 8k(k-1)(k+1)$, ahol $k^2-1$ osztható $8$-cal, így összesen $2\cdot 4\cdot 8 = 64$.
- $(n-1)^3 + n^3 + (n+1)^3 = 3n(n^2+2)$: osztható $3n$-nel, és $9$-cel is, mert $n \equiv 0$ esetén $3 \mid n$, $n \equiv \pm 1$ esetén $3 \mid n^2 + 2$.
- A $abcabc = abc\cdot 1001 = abc\cdot 7\cdot 11\cdot 13$ trükk: háromjegyű szám kétszeri egymás mellé írása $1001$-gyel szoroz.
- $(2k+1)^2 - (2l+1)^2 = 4(k-l)(k+l+1)$, és a két tényező összege páratlan, ezért az egyik páros: $8 \mid$.
- $37 \mid \overline{abc} \Rightarrow 37 \mid \overline{bca}$, mert $\overline{bca} = 10\,\overline{abc} - 999a$ és $999 = 27\cdot 37$.
- $23 \mid 5a + 9b \Rightarrow 23 \mid 3a + 10b$, mert $3a + 10b \equiv 19\,(5a+9b) \pmod{23}$ ($19\cdot 5 = 95 \equiv 3$, $19 \cdot 9 = 171 \equiv 10$).
- $133 \mid 11^{n+2} + 12^{2n+1}$: $= 121\cdot 11^n + 12\cdot 144^n$, és $144 \equiv 11 \pmod{133}$, tehát $\equiv 11^n(121+12) = 133\cdot 11^n \equiv 0$.
- $(c^6 - 3)/(c^2+2)$ egész: $c^6 - 3 = (c^2+2)(c^4 - 2c^2 + 4) - 11$, így $c^2 + 2 \mid 11$, azaz $c^2 + 2 = 11$, $c = \pm 3$.
- Öt egymást követő szám négyzetösszege $5n^2 + 10 = 5(n^2+2)$ (középső szám $n$); négyzetszám csak úgy lehetne, ha $5 \mid n^2 + 2$, vagyis $n^2 \equiv 3 \pmod 5$, de a négyzetek mod $5$ maradéka $0, 1, 4$.

**2. Igaz-e az állítás?** Az oszthatósági tulajdonságok (lásd fent) „tipikus hamis általánosításai" ellenpéldával cáfolandók; a forrás kérdései és a helyes válaszok:

| állítás | igaz? | indok / ellenpélda |
|---|---|---|
| $c \mid a+b \Rightarrow c \mid a \wedge c \mid b$ | hamis | $c = 2$, $a = b = 1$ |
| $c \mid a+b \wedge c \mid a \Rightarrow c \mid b$ | igaz | $b = (a+b) - a$ lineáris kombináció |
| $c \mid a+b \wedge c \mid a-b \Rightarrow c \mid a \wedge c \mid b$ | hamis | $c = 2$, $a = b = 1$ ($c \mid 2a$ csak) |
| $c \mid a \wedge d \mid a \Rightarrow cd \mid a$ | hamis | $c = d = 2$, $a = 2$ |
| $c \mid ab \Rightarrow c \mid a \vee c \mid b$ | hamis (csak prím $c$-re igaz) | $c = 6$, $a = 2$, $b = 3$ |
| $c \mid a \wedge d \mid b \Rightarrow cd \mid ab$ | igaz | 4. tulajdonság |
| $c \mid 2a+5b \wedge c \mid 3a+7b \Rightarrow c \mid a \wedge c \mid b$ | igaz | $3(2a+5b) - 2(3a+7b) = b$, $7(2a+5b) - 5(3a+7b) = -a$ |

**3. Egyéb.** A $100$ cellás zárfeladat: a $k$-adik cella annyiszor változik, ahány osztója van; páratlan sokszor pontosan a négyzetszámok ($\tau(n)$ páratlan $\iff$ minden kitevő páros, lásd [[concepts/dimatii/osztok-szama]]), tehát az $1, 4, 9, \dots, 100$ cellák lesznek nyitva. A $7$-, $11$-, $13$-, $17$-, $19$-cel való oszthatósági szabályok a $10^k$ maradékain alapulnak (pl. $1001 = 7\cdot 11\cdot 13$ miatt a $3$-jegyű csoportok váltott előjelű összege).

## Kapocs

- [[concepts/dimatii/egyseg-es-asszocialt]] — az oszthatóság szempontjából nem megkülönböztethető számok
- [[concepts/dimatii/maradekos-osztas]] — mi történik, ha az oszthatóság nem áll fenn
- [[concepts/dimatii/legnagyobb-kozos-oszto]] — az oszthatósági rendezés szerinti „legnagyobb”
- [[concepts/dimatii/felbonthatatlan-es-prim]] — az oszthatóság alapján definiált két primitív fogalom
- [[concepts/dimatii/kongruencia]] — oszthatóság különbségekre megfogalmazva
- [[concepts/dimatii/bovitett-euklideszi-algoritmus]] — a lineáris kombinációk és a vízkancsó-invariáns alkalmazása
- [[concepts/dimatii/integritasi-tartomany]] — az a keret, amelyben a fenti tulajdonságok általánosan érvényesek
- [[concepts/dimatii/osztok-szama]] — az osztók számának paritása (zárfeladat)
