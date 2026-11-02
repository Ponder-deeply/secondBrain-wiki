---
tags: [concept]
sources: [DimatIIEa01.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, dimat2gyak01mo.pdf, Dimat2mintaZH1.pdf, dm2gy01_Szamelmelet.pdf]
derivation: source
kind: theorem
element: fire
updated: 2026-10-21
---

# Maradékos osztás

Az elemi számelmélet fő eszköze: bármely egész egyértelműen felírható egy adott nem nulla szám többszöröseként plusz egy nála kisebb nemnegatív maradékként.

## Tartalom

**Tétel.** Tetszőleges $a$, $b \neq 0$ egész számokhoz egyértelműen léteznek olyan $q, r$ egészek, hogy
$$a = bq + r \quad \text{és} \quad 0 \leq r < |b|.$$

**Bizonyítás** (nemnegatív számokra; az általános eset ebből adódik).

*Létezés*, $a$ szerinti indukcióval. Ha $a < b$, akkor $a = b\cdot 0 + a$, tehát $q = 0$, $r = a$. Ha $a \geq b$, akkor az indukciós feltevés szerint az $a$-nál kisebb számok már felírhatók ilyen alakban; legyen $a - b = bq^* + r^*$. Ekkor $a = b(q^* + 1) + r^*$, azaz $q = q^* + 1$, $r = r^*$.

*Egyértelműség*: legyen $a = bq + r = bq^* + r^*$. Ekkor $b(q - q^*) = r^* - r$. Mivel $|r^* - r| < |b|$, ez csak úgy lehet, ha $q = q^*$ és $r = r^*$. $\square$

### Jelölés

Legyenek $a, b$ egészek ($b \neq 0$), és $a = b\cdot q + r$ a fenti felbontás. Ekkor

- $a \bmod b = r$;
- $q = \lfloor a/b \rfloor$, ha $b > 0$, és $q = \lceil a/b \rceil$, ha $b < 0$.

**Példák.** $123 \bmod 10 = 3$, $123 \bmod 100 = 23$, $123 \bmod 1000 = 123$, $123 \bmod (-10) = 3$. Negatív osztandóra: $-123 \bmod 10 = 7$, $-123 \bmod 100 = 77$, $-123 \bmod 1000 = 877$, $-123 \bmod (-10) = 7$. A maradék definíció szerint mindig nemnegatív.

### Példák: ciklikus mennyiségek

*Hány óra lesz 123 óra múlva, ha most 9 óra van?* $123 = 24\cdot 5 + 3$, tehát $9 + 3 = 12$: dél lesz. *104 óra múlva?* $104 = 24 \cdot 4 + 20$, tehát $9 + 20 = 29$, újabb redukcióval $29 = 24\cdot 1 + 5$: hajnali 5 óra.

*Milyen napra esik jövőre szeptember 16?* A napokat számozzuk $\text{hétfő} \mapsto 0, \dots, \text{vasárnap} \mapsto 6$ szerint. $365 = 7\cdot 52 + 1$, tehát szerda $+\,1$ nap $= 2 + 1 = 3 =$ csütörtök. Visszafelé: ha egy dátum vasárnapra esik, két évvel korábban (a közbeeső időszakban egy szökőnappal): $-(365 + 366) = -731 = 7\cdot(-104) - 3$, azaz vasárnap $-\,3$ nap $= 6 - 3 = 3 =$ csütörtök.

A maradékos osztás az alapja a [[concepts/dimatii/szamrendszerek]] felírási tételének, az [[concepts/dimatii/euklideszi-algoritmus]]nak és a [[concepts/dimatii/kongruencia]] fogalmának egyaránt.

### Megjegyzés az előadásdiák alapján

*(Farkas Gábor előadásdiái.)* $a, b \in \mathbb{Z}$, $b \neq 0$, $a \mid b \Rightarrow |a| \leq |b|$; innen a maradékos osztás tétele ($a = qb + r$, $0 \leq r < |b|$, egyértelműen) $\mathbb{Z}$-ben érvényes, és ezen múlik, hogy az euklideszi algoritmus elvégezhető (véget ér).

### Feladattípusok és módszerek: számolás maradékokkal

*(Gyakorlat 1., minta-ZH 4. feladat.)* Összeg, szorzat és hatvány maradéka a tagok maradékából számolható; **minden művelet után újra redukálunk**, és csak a maradékokkal számolunk tovább ([[concepts/dimatii/kongruencia]]).

- $13\cdot15 + 31\cdot42 + 51^2 \bmod 2 = (1\cdot1 + 1\cdot0 + 1^2) \bmod 2 = 0$.
- $73\cdot82 + 17\cdot71 \bmod 4 = (1\cdot2 + 1\cdot3) \bmod 4 = 1$; $123\cdot594\cdot931 \bmod 10 = 3\cdot4\cdot1 \bmod 10 = 2$.
- $39\cdot47\cdot29\cdot11\cdot36\cdot83 \bmod 5 = 4\cdot2\cdot4\cdot1\cdot1\cdot3 \bmod 5 = 1$.

**Hatvány maradéka.** Két módszer: (1) ismételt négyzetre emelés minden lépés után redukálva ($3^{32} \bmod 5$: $3^2 \equiv 4 \equiv -1$, $3^4 \equiv 1$, így $3^{32} \equiv 1$); (2) az első néhány hatvány kiszámolása, amíg az $1$ vissza nem tér, utána a kitevő redukciója a periódussal.
- $17^{10} \bmod 3 = 2^{10} = (2^2)^5 \equiv 1^5 = 1$.
- $3^{100} \bmod 7$: $3^6 \equiv 1 \pmod 7$ ($3,2,6,4,5,1$), $100 = 6\cdot16 + 4$, tehát $3^{100} \equiv 3^4 \equiv 4$.

Ez ugyanaz a kitevő-redukció, mint a [[concepts/dimatii/komplex-egysegiyokok-hatvanyai]]nál, csak itt a modulus körében; nagy kitevőre a [[concepts/dimatii/euler-fermat-tetel]] ($a^{\varphi(m)} \equiv 1$) és a [[concepts/dimatii/gyors-hatvanyozas]] kell.

**Minta-ZH 4. feladata.**
- $12^{11^{10^{9^{\cdot^{\cdot^{\cdot^{1}}}}}}} \bmod 13$: $12 \equiv -1$, így csak a kitevő paritása számít; a kitevő $11$ egy pozitív hatványa, tehát páratlan, és az eredmény $(-1)^{\text{páratlan}} \equiv -1 \equiv 12$.
- $11^{45} \bmod 23$: $23$ prím, $(11,23) = 1$, a kis Fermat-tétel szerint $11^{22} \equiv 1$, tehát $11^{45} = (11^{22})^2\cdot 11 \equiv 11$.

### Tipikus hibák

- Kitevőt maradékolunk a *modulussal* ($a^n \bmod m \ne a^{n \bmod m}$); a kitevő a periódussal (Euler–Fermat esetén $\varphi(m)$-mel) redukálható.
- Egyetlen nagy szám kiszámolása ($3^{100}$) és csak a végén redukálás helyett lépésenként kell redukálni.
- Hatványtornyoknál a kitevő paritása vagy maradéka kell, nem az értéke; $\pm1$ alappal csak a paritás számít.
- Eratoszthenész szitája: a $150$ alatti prímek ($2,3,5,7,11,\dots,149$) kereséséhez elég $\sqrt{150} < 13$ alatti prímek ($2,3,5,7,11$) többszöröseit kihúzni; lásd [[concepts/dimatii/primek-eloszlasa]].

### Feladattípusok és módszerek (2020. 1. feladatsor)

**1. Maradékos osztás negatív számokkal.** A maradék mindig $0 \le r < |b|$; előbb $r = a \bmod |b|$-t keressük, majd $q = (a - r)/b$. A forrás feladatai ($a$, $b$):

| $a$, $b$ | $q$ | $r$ |
|---|---:|---:|
| $20, 6$ | $3$ | $2$ |
| $-71, 5$ | $-15$ | $4$ |
| $102, -7$ | $-14$ | $4$ |
| $-68, -11$ | $7$ | $9$ |
| $5, 12$ | $0$ | $5$ |
| $-104, 8$ | $-13$ | $0$ |
| $-327, -42$ | $8$ | $9$ |
| $-3, 12$ | $-1$ | $9$ |

Tipikus hiba: a negatív osztandónál a „lefelé kerekítést" elrontani ($-71 = 5\cdot(-14) - 1$ nem megfelelő, a maradék nem lehet negatív).

**2. Maradékok kezelése.** Ha $a \bmod 7 = 3$ és $b \bmod 7 = 6$, akkor $(a+b) \bmod 7 = 9 \bmod 7 = 2$, $(a-b) \bmod 7 = -3 \bmod 7 = 4$, $ab \bmod 7 = 18 \bmod 7 = 4$. Az igazolás: $a = 7k+3$, $b = 7l+6$ behelyettesítése, a $7$-tel osztható tagok kiesnek; ugyanez általánosan $m$-re bizonyítja, hogy az összeg, különbség, szorzat maradéka csak $a \bmod m$-től és $b \bmod m$-től függ (lásd [[concepts/dimatii/kongruencia]]).

**3. Hatványok maradéka, utolsó számjegy.** Előbb az alapot redukáljuk, majd a hatvány periódusát keressük: $2019 \equiv 3 \pmod 6$, $3^3 = 27 \equiv 3$, tehát $2019^3 \bmod 6 = 3$. $2019 \equiv 3 \pmod 7$, a $3$ hatványai mod $7$ periódusa $6$: $2019^{32} \equiv 3^{32 \bmod 6} = 3^2 \equiv 2$, $2019^{288} \equiv 3^{0} = 1 \pmod 7$. Az utolsó számjegy a $\bmod 10$ maradék: $1017677^{838}$ utolsó jegye $7^{838}$-é; a $7$ hatványainak utolsó jegye $7, 9, 3, 1$ ismétlődik, $838 \equiv 2 \pmod 4$, tehát $9$. A nagy kitevők szisztematikus módszere: [[concepts/dimatii/euler-fermat-tetel]].

## Kapocs

- [[concepts/dimatii/oszthatosag]] — a maradék nulla volta pontosan az oszthatóság
- [[concepts/dimatii/szamrendszerek]] — ismételt maradékos osztásból adódó jegyek
- [[concepts/dimatii/euklideszi-algoritmus]] — maradékos osztások láncolata
- [[concepts/dimatii/kongruencia]] — a maradékok egyenlőségének relációja

- [[concepts/dimatii/komplex-egysegiyokok-hatvanyai]] — kitevő-redukció egységgyököknél, mátrixoknál
- [[concepts/dimatii/szamrendszerek]] — az utolsó számjegy a számrendszer alapja szerinti maradék
