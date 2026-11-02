---
tags: [concept]
sources: [DimatIIEa02.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, Lehman-Leighton-Meyer-Mathematics-for-Computer-Science.pdf, dimat2gyak04mo.pdf, dm2gy05_Szamelmelet.pdf, dm2gy05.pdf, dm2gy06.pdf]
derivation: source
kind: theorem
element: fire
updated: 2026-10-21
---

# Euler–Fermat-tétel

A modulushoz relatív prím alap $\varphi(m)$-edik hatványa mindig $1$ modulo $m$ — a moduláris hatványozás alaptétele.

## Tartalom

**Tétel (Euler–Fermat).** Legyen $m > 1$ egész, $a$ olyan egész, melyre $(a,m) = 1$. Ekkor
$$a^{\varphi(m)} \equiv 1 \pmod m.$$

**Következmény (kis Fermat-tétel).** Legyen $p$ prímszám és $p \nmid a$. Ekkor $a^{p-1} \equiv 1 \pmod p$; tetszőleges $a$ esetén pedig $a^p \equiv a \pmod p$.

**Példák.** $\varphi(6) = 2 \Rightarrow 5^2 = 36 \equiv 1 \pmod 6$; $\varphi(12) = 4 \Rightarrow 5^4 = 625 \equiv 1 \pmod{12}$ és $7^4 = 2401 \equiv 1 \pmod{12}$.

**Figyelem!** A relatív prímség feltétel lényeges: $2^4 = 16 \equiv 4 \not\equiv 1 \pmod{12}$, mert $(2,12) = 2 \neq 1$.

### Bizonyítás

**Lemma.** Legyen $m > 1$ egész, $a_1, \dots, a_m$ teljes maradékrendszer modulo $m$. Ekkor minden $a, b$ egészre, melyre $(a,m) = 1$, az $a\cdot a_1 + b,\ \dots,\ a\cdot a_m + b$ számok is teljes maradékrendszert alkotnak. Továbbá, ha $a_1, \dots, a_{\varphi(m)}$ redukált maradékrendszer modulo $m$, akkor $a\cdot a_1, \dots, a\cdot a_{\varphi(m)}$ szintén redukált maradékrendszer.

*A lemma bizonyítása.* $i \neq j$ esetén $aa_i + b \equiv aa_j + b \pmod m \iff aa_i \equiv aa_j \pmod m$. Mivel $(a,m) = 1$, $a$-val egyszerűsíthetünk: $a_i \equiv a_j \pmod m$ — ellentmondás. Tehát a számok páronként inkongruensek, és számuk $m$, így teljes maradékrendszert alkotnak. A redukált esetben $(a_i,m) = 1$ és $(a,m) = 1 \Rightarrow (a\cdot a_i, m) = 1$; a szorzatok páronként inkongruensek és számuk $\varphi(m)$, tehát redukált maradékrendszert alkotnak. $\square$

*A tétel bizonyítása.* Legyen $a_1, a_2, \dots, a_{\varphi(m)}$ egy redukált maradékrendszer modulo $m$. Mivel $(a,m) = 1$, a lemma szerint $a\cdot a_1, \dots, a\cdot a_{\varphi(m)}$ is redukált maradékrendszer, tehát ugyanazokat a maradékosztályokat futja be. Innen
$$a^{\varphi(m)}\prod_{j=1}^{\varphi(m)}a_j = \prod_{j=1}^{\varphi(m)}a\cdot a_j \equiv \prod_{j=1}^{\varphi(m)}a_j \pmod m.$$
Mivel $\prod_j a_j$ relatív prím $m$-hez, egyszerűsíthetünk vele: $a^{\varphi(m)} \equiv 1 \pmod m$. $\square$

### Alkalmazások

**Nagy hatvány maradéka.** Mi lesz $3^{111}$ utolsó számjegye tízes számrendszerben, azaz mennyi $3^{111} \bmod 10$? $\varphi(10) = 4$, ezért
$$3^{111} = 3^{4\cdot 27 + 3} = \left(3^4\right)^{27}\cdot 3^3 \equiv 1^{27}\cdot 3^3 = 27 \equiv 7 \pmod{10}.$$

**Lineáris kongruencia megoldása.** Ha $(a,m) = 1$, akkor $\overline{a}$ inverze $\overline{a}^{\,\varphi(m)-1}$, így az $ax \equiv b \pmod m$ kongruencia mindkét oldalát $a^{\varphi(m)-1}$-nel szorozva adódik $x$.

- $2x \equiv 5 \pmod 7$: $\varphi(7) = 6$, szorozzuk be mindkét oldalt $2^5$-nel. Ekkor $5\cdot 2^5 = 2^6 x \equiv x \pmod 7$, és $5\cdot 2^5 = 5\cdot 32 \equiv 5\cdot 4 = 20 \equiv 6 \pmod 7$.
- $23x \equiv 4 \pmod{211}$: $\varphi(211) = 210$, szorozzuk be mindkét oldalt $23^{209}$-nel. Ekkor $4\cdot 23^{209} \equiv 23^{210}x \equiv x \pmod{211}$.

### A diák bizonyítási vázlata és a Fermat-tétel bizonyítása

A bizonyítás a diákon: legyen $\{r_1,\dots,r_{\varphi(m)}\}$ RMR; $(a,m)=1 \Rightarrow \{ar_1,\dots,ar_{\varphi(m)}\}$ is RMR, a megfelelő párosítással $r_i \equiv ar_j$; összeszorozva $a^{\varphi(m)}\prod r_i \equiv \prod r_i$, és $(r_i,m)=1$ miatt egyszerűsítve $a^{\varphi(m)} \equiv 1 \pmod m$.

**Fermat-tétel bizonyítása.** $\varphi(p) = p-1$, így az első alak ($p \nmid a \Rightarrow a^{p-1}\equiv1$) az Euler–Fermat-tételből adódik. A második alak ($a^p \equiv a$): ha $p \mid a$, akkor $0 \equiv 0$; ha $p \nmid a$, az első alakot $a$-val szorozva kapjuk.

### Bizonyítás $\mathbb{Z}_n^*$ nyelven és az inverz (Lehman–Leighton–Meyer 9.10)

Legyen $\mathbb{Z}_n^* = \{k \in [0,n) : (k,n) = 1\}$, így $\varphi(n) = |\mathbb{Z}_n^*|$. Két könnyű lemma elég:

1. $\mathbb{Z}_n^*$ zárt a szorzásra ($j,k \in \mathbb{Z}_n^* \Rightarrow jk \in \mathbb{Z}_n^*$).
2. Ha $k \in \mathbb{Z}_n^*$ és $S \subseteq \mathbb{Z}_n$, akkor $|kS| = |S|$ ($k$ egyszerűsíthető, tehát a $k$-val szorzás injektív). Következésképp $k\mathbb{Z}_n^* = \mathbb{Z}_n^*$: ugyanazokat az elemeket kapjuk, más sorrendben.

Legyen $P = k_1 k_2 \cdots k_{\varphi(n)}$ az $\mathbb{Z}_n^*$ elemeinek szorzata. Ekkor $P = (kk_1)(kk_2)\cdots(kk_{\varphi(n)}) = k^{\varphi(n)}P$, és $P \in \mathbb{Z}_n^*$ miatt egyszerűsíthetünk vele: $k^{\varphi(n)} = 1$ $(\mathbb{Z}_n)$.

**Az inverz zárt alakja.** $(k,n) = 1 \Rightarrow k^{\varphi(n)-1}$ inverze $k$-nak $\mathbb{Z}_n$-ben, gyors hatványozással hatékonyan kiszámítható ([[concepts/dimatii/gyors-hatvanyozas]]). Csakhogy $\varphi(n)$ ismeretéhez $n$ faktorizálása kell, ezért nagy $n$-re a bővített euklideszi algoritmus a gyakorlatibb út.

### Feladattípusok és módszerek (gyakorlat 4.)

**1. Hatványok ciklusa modulo $m$.** Soroljuk fel $a^1, a^2, \dots$ maradékait, amíg ismétlődést látunk: $3 \bmod 5$: $3, 4, 2, 1$ (periódus $4$, $3^{4n+k} \equiv 3^k$); $2 \bmod 7$: $2, 4, 1$ (periódus $3$); $3 \bmod 7$: $3,2,6,4,5,1$ (periódus $6$); $7 \bmod 8$: $7, 1$ ($7^{2n} \equiv 1$, $7^{2n+1} \equiv 7$); $2 \bmod 4$: $2, 0, 0, \dots$ (nilpotens, lásd [[concepts/dimatii/invertalhatosag-zm-ben]]). A periódus osztója $\varphi(m)$-nek.

**2. Kitevő redukciója $\varphi(m)$ szerint.** $(a,m) = 1 \Rightarrow a^n \equiv a^{n \bmod \varphi(m)}$. Értékek: $\varphi(7) = 6$, $\varphi(9) = 6$, $\varphi(11) = 10$, $\varphi(13) = 12$.
- $2^7 \equiv 2$, $2^8 \equiv 4$, $2^9 \equiv 1 \pmod 7$; $2^{13} \equiv 2 \pmod{13}$; $2^{13} \equiv 2^{3} = 8 \pmod{11}$; $2^{10} \equiv 2^4 = 16 \equiv 7 \pmod 9$.
- $3^{10} \equiv 3^4 \equiv 4$, $3^{15} \equiv 3^3 \equiv 6$, $3^{115} \equiv 3$, $3^{1155} \equiv 3^3 \equiv 6 \pmod 7$.

**3. Hatványtorony ($a^{b^c}$).** A kitevőt modulo $\varphi(m)$ kell kiszámolni, ehhez az alapnak relatív prímnek kell lennie $\varphi(m)$-hez, és szükség esetén újra redukálunk.
- $2^{3^{12}} \bmod 11$: $3^{12} \bmod 10$; $3$ relatív prím $10$-hez, $\varphi(10) = 4$, $3^{12} \equiv 3^0 = 1$, tehát $2^{3^{12}} \equiv 2 \pmod{11}$.
- $2^{7^{122}} \bmod 11$: $7^{122} \equiv 7^2 = 49 \equiv 9 \pmod{10}$, így $2^9 \equiv 6 \pmod{11}$ (gyors hatványozással: $9 = 1001_2$).
- $2^{5^{11}} \bmod 13$: $5^{11} \bmod 12$, $\varphi(12) = 4$, $5^2 \equiv 1$, $5^{11} \equiv 5$, $2^5 = 32 \equiv 6 \pmod{13}$.
- $2^{3^{1111}} \bmod 17$: a kitevő $3^{1111} \bmod 16$. Itt $3^4 = 81 \equiv 1 \pmod{16}$ és $1111 \equiv 3 \pmod 4$, így $3^{1111} \equiv 3^3 = 27 \equiv 11 \pmod{16}$ és $2^{11} = 2048 \equiv 8 \pmod{17}$. *Figyelem:* a forrás megoldása $1111 \equiv 7 \pmod 8$-ból $3^8 \equiv 1$-et ír (ami nem következik: a $7$-es kitevőt $3^8$-ra cserélte), és $2^1 = 2$-t közöl; az itt szereplő $8$ saját újraszámolás, a forrás végeredménye hibás.

**4. Utolsó két számjegy ($\bmod 100$).** $7^{3^{47}} \bmod 100$: $\varphi(100) = 40$, kitevő $3^{47} \bmod 40$; $\varphi(40) = 16$, $47 \equiv 15 \pmod{16}$, $3^{47} \equiv 3^{15} \equiv 3^{-1} \equiv 27 \pmod{40}$ (mert $3\cdot 27 = 81 \equiv 1$). Így $7^{27} \bmod 100$: $27 = 11011_2$, gyors hatványozással $7^{27} \equiv 43$. Az utolsó két számjegy: $43$.

**Tipikus hibák.** A kitevőt nem szabad modulo $m$ redukálni, hanem modulo $\varphi(m)$-et kell; és az Euler–Fermat-tétel csak $(a,m) = 1$ esetén áll (a toronynál minden szinten ellenőrizni kell).

### További feladattípusok (2020. 5. feladatsor, 2024. 5–6. sorozat)

**$\varphi$ értékei.** $\varphi(1) = 1$, $\varphi(2) = 1$, $\varphi(3) = 2$, $\varphi(4) = 2$, $\varphi(10) = 4$, $\varphi(24) = 8$, $\varphi(96) = 32$, $\varphi(100) = 40$ ([[concepts/dimatii/euler-fi-fuggveny]]; a kanonikus alakból: $96 = 2^5\cdot 3$, $\varphi = 2^4\cdot 2 = 32$).

**Oszthatósági bizonyítások.** Ha $(n,7) = 1$, akkor $n^6 \equiv 1 \pmod 7$, tehát $n^{6k} - 1 = (n^6)^k - 1 \equiv 0$ (ebből $n^{12} - 1$ is). $x^7 \equiv x \pmod{42}$: $42 = 2\cdot 3\cdot 7$, és $x^7 \equiv x$ mod $2$, mod $3$ (mert $p - 1 \mid 6$), mod $7$ (Fermat). Hasonlóan $n^{13} - n$ osztható $2, 3, 5, 7, 13$-mal, mert $p - 1 \mid 12$ ezekre a prímekre ($1, 2, 4, 6, 12$). $1729 = 7\cdot 13\cdot 19$ és $6, 12, 18 \mid 1728$, ezért $a^{1729} \equiv a$ mod $7$, $13$, $19$, tehát mod $1729$ is, bár $1729$ összetett (Carmichael-szám).

**Utolsó jegyek és maradékok — a módszer:** az alapot és a kitevőt külön redukáljuk ($\bmod m$, illetve $\bmod \varphi(m)$, ha $(a,m) = 1$). Megoldott példák:
- $3^{1003}$ utolsó három jegye: $\varphi(1000) = 400$, $1003 \equiv 3$, $3^3 = 27$: **$027$**.
- $173^{163} \bmod 17$: $173 \equiv 3$, $163 \equiv 3 \pmod{16}$, $3^3 = 27 \equiv 10$.
- $143^{143}$ utolsó három jegye hármas számrendszerben: $\bmod 27$, $143 \equiv 8$, $\varphi(27) = 18$, $143 \equiv 17 \pmod{18}$, $8^{17} \equiv 17 \pmod{27}$, és $17 = 1\cdot 9 + 2\cdot 3 + 2$: **$122_{(3)}$**.
- $205^{206^{207}} \bmod 103$: $205 \equiv -1$, a kitevő páros, így **$1$**.
- $37^{39042}$ utolsó két jegye: $\varphi(100) = 40$, $39042 \equiv 2$, $37^2 = 1369$: **$69$**.
- $17^{3^{2013}}$ utolsó két jegye oktálisan: $\bmod 64$, $\varphi(64) = 32$, $3^{2013} \bmod 32$ ($3$ rendje $8$, $2013 \equiv 5$): $3^5 = 243 \equiv 19$, $17^{19} \equiv 49 = 61_{(8)}$: **$61_{(8)}$**.
- $11^{2013^{26}}$ utolsó két jegye: $11^k \equiv 1 + 10k \pmod{100}$, a kitevő $\bmod 10$: $2013^{26} \equiv 3^{26} \equiv 3^2 = 9$, így $11^9 \equiv 91$: **$91$**.
- $323^{149} \bmod 63 = 8$; $423^{173} \bmod 52 = 11$; $495^{173} \bmod 98 = 87$; $457^{101} \bmod 90 = 67$ (13. feladat; itt a modulus összetett, $\varphi(63) = 36$, $\varphi(52) = 24$, $\varphi(98) = 42$, $\varphi(90) = 24$; az eredményeket számolással ellenőriztük).
- 6. sorozat 14. feladata: $6^{13^{20}} \bmod 11 = 6$; $5^{15^{17}} \bmod 12 = 5$; $137^{7^{120}} \bmod 8 = 1$; $13^{9^{45}} \bmod 17 = 13$.

**Lineáris kongruencia Euler–Fermat-tétellel.** Ha $(a,m) = 1$, $x \equiv b\,a^{\varphi(m)-1}$. Ha $(a,m) = d > 1$, előbb $d$-vel osztunk (a modulussal együtt, és a $b$ oszthatóságát ellenőrizve): $6x \equiv 3 \pmod{15} \Rightarrow 2x \equiv 1 \pmod 5$, $x \equiv 2^{3} \cdot 1 = 8 \equiv 3$; $2x \equiv 1 \pmod 7$: $x \equiv 2^5 = 32 \equiv 4$. A teljes feladatsor megoldásai: [[concepts/dimatii/linearis-kongruencia]].

**Tipikus hibák.** $\varphi(m)$ helyett $m - 1$-gyel redukálni összetett $m$-nél; a kitevőt $\bmod\ m$ redukálni; a tételt nem relatív prím alapnál ($\gcd(a,m) > 1$, pl. $6^k \bmod 12$) alkalmazni; ilyenkor külön kell eljárni.

## Kapocs

- [[concepts/dimatii/euler-fi-fuggveny]] — a kitevőben szereplő függvény
- [[concepts/dimatii/redukalt-maradekrendszer]] — a bizonyítás kerete
- [[concepts/dimatii/teljes-maradekrendszer]] — a lemma bővebb változata
- [[concepts/dimatii/invertalhatosag-zm-ben]] — az inverz zárt alakja
- [[concepts/dimatii/linearis-kongruencia]] — alternatív megoldási módszer
- [[concepts/dimatii/kongruencia]] — az egyszerűsítési szabály
- [[concepts/dimatii/hatvanytorony-modulo-szamitasa]] — $a^{b^c} \bmod m$ szintenkénti redukálással
- [[concepts/dimatii/hatvanyok-periodicitasa-zm-ben]] — a hatványok ciklusa és a kitevő redukálásának csapdája
