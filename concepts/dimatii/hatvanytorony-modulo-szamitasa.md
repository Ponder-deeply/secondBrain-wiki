---
tags: [concept]
sources: [dimat2gyak04mo.pdf, Dimat2mintaZH1.pdf, dm2gy05_Szamelmelet.pdf, dm2gy06.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-22
---

# Hatványtorony és nagy hatvány maradéka

Az $a^{b^c} \bmod m$ típusú feladatban az Euler–Fermat-tétellel a kitevőt szintről szintre redukáljuk $\varphi$ szerint, majd a maradék hatványt gyorshatványozással számoljuk ki.

## Tartalom

### Az eljárás

Ha $(a,m) = 1$, akkor $a^{\varphi(m)} \equiv 1 \pmod m$, ezért
$$a^{n} \equiv a^{\,n \bmod \varphi(m)} \pmod m.$$
Torony esetén a kitevő maga is hatvány, így rekurzívan haladunk: $a^{(b^c)} \bmod m$ kiszámításához $b^c \bmod \varphi(m)$ kell, ahhoz $c \bmod \varphi(\varphi(m))$, és így tovább. Minden szinten ellenőrizni kell, hogy az alap relatív prím-e az aktuális modulushoz.

1. számoljuk ki $\varphi(m)$-et ([[concepts/dimatii/euler-fi-fuggveny]]);
2. redukáljuk a kitevőt modulo $\varphi(m)$, ehhez ugyanezt az eljárást alkalmazzuk a kitevőre;
3. a megmaradt kis kitevős hatványt [[concepts/dimatii/gyors-hatvanyozas]]sal számoljuk.

Ha az alap nem relatív prím a modulushoz, az Euler–Fermat-tétel nem használható, és a hatványok ciklusát kell vizsgálni: [[concepts/dimatii/hatvanyok-periodicitasa-zm-ben]].

### Ötletek, amelyek megspórolják a számolást

- $a \equiv -1 \pmod m$ esetén csak a kitevő paritása számít: $12 \equiv -1 \pmod{13}$, tehát $12^{\text{páratlan}} \equiv 12$.
- Ha $a^k \equiv a^{-1}$ alakú kitevő jön ki, például $3^{47} \equiv 3^{15} = 3^{-1} \equiv 27 \pmod{40}$ (mert $3 \cdot 27 = 81 \equiv 1$), a hatványozás elmarad.

### Példák

**ZH-minta (a).** $12^{11^{10^{9^{8^{7^{6^{5^{4^{3^{2^{1}}}}}}}}}}} \bmod 13$: $12 \equiv -1$, a kitevő $11^{\dots}$ páratlan, így az eredmény $(-1)^{\text{páratlan}} = -1 \equiv 12$.

**ZH-minta (b).** $11^{45} \bmod 23$: $\varphi(23) = 22$, $45 = 2 \cdot 22 + 1$, tehát $11^{45} \equiv 11^1 = 11$.

**Egyszintes kitevők modulo 7** ($\varphi(7) = 6$): $3^{10} \equiv 3^4 \equiv 4$; $3^{15} \equiv 3^3 \equiv 6$; $3^{115} \equiv 3^1 = 3$; $3^{1155} \equiv 3^3 \equiv 6$.

**Kétszintes torony:** $2^{3^{12}} \bmod 11$. $\varphi(11) = 10$, így $3^{12} \bmod 10$ kell. $\varphi(10) = 4$, $12 \equiv 0 \pmod 4$, tehát $3^{12} \equiv 1 \pmod{10}$ és $2^{3^{12}} \equiv 2^1 = 2$.

**Másik:** $2^{7^{122}} \bmod 11$. $7^{122} \bmod 10$: $\varphi(10) = 4$, $122 \equiv 2 \pmod 4$, tehát $7^{122} \equiv 7^2 = 49 \equiv 9$, és $2^9 \bmod 11$ gyorshatványozással: $9 = 1001_2$, így $2^9 = 512 \equiv 6$.

**Harmadik:** $2^{5^{11}} \bmod 13$. $\varphi(13) = 12$, $5^{11} \bmod 12$: $5^2 = 25 \equiv 1$, így $5^{11} \equiv 5$, és $2^5 = 32 \equiv 6 \pmod{13}$.

**Negyedik:** $2^{3^{1111}} \bmod 17$. $\varphi(17) = 16$, $3^{1111} \bmod 16$: $\varphi(16) = 8$ és $1111 \equiv 7 \pmod 8$, így $3^{1111} \equiv 3^7 \equiv 3^3 = 27 \equiv 11 \pmod{16}$ (mert $3^4 = 81 \equiv 1$). Az eredmény $2^{11} = 2048 \equiv 8 \pmod{17}$. (A gyakorlati megoldókulcs ennél $2$-t közöl, mert a kitevőt $3^8$-ra redukálta $3^7$ helyett: az ellenőrző számolás $8$-at ad.)

**Utolsó két számjegy.** $7^{3^{47}}$ utolsó két jegye, azaz $7^{3^{47}} \bmod 100$. $\varphi(100) = 40$, $3^{47} \bmod 40$: $\varphi(40) = 16$, $47 \equiv 15 \pmod{16}$, így $3^{47} \equiv 3^{15} \equiv 3^{-1} \equiv 27 \pmod{40}$. Marad $7^{27} \bmod 100$: $27 = 11011_2$, a négyzetre emelések $7^2 = 49$, $7^4 = 2401 \equiv 1$ miatt $7^{27} = 7^{24}\cdot 7^3 \equiv 343 \equiv 43$. Az utolsó két jegy $43$.

**Utolsó jegyek gyakorló feladat.** $3^{1003} \bmod 1000$: $\lambda(1000) = 100$, $3^{100} \equiv 1$, $1003 \equiv 3 \pmod{100}$, tehát az utolsó három jegy $027$.

## Kapocs

- [[concepts/dimatii/euler-fermat-tetel]] — a kitevő redukálásának alapja
- [[concepts/dimatii/euler-fi-fuggveny]] — a $\varphi$ értékek kiszámítása minden szinten
- [[concepts/dimatii/gyors-hatvanyozas]] — a végső kis hatvány kiszámítása
- [[concepts/dimatii/hatvanyok-periodicitasa-zm-ben]] — mi a teendő, ha az alap nem relatív prím
- [[concepts/dimatii/utolso-jegyek-kongruenciaval]] — az utolsó jegyek mint modulo $b^k$ maradék
