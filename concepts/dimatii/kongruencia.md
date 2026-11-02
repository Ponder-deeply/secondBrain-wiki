---
tags: [concept]
sources: [DimatIIEa01.pdf, DimatIIEa02.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, Lehman-Leighton-Meyer-Mathematics-for-Computer-Science.pdf, dimat2gyak03mo.pdf]
derivation: source
kind: definition
element: fire
updated: 2026-10-21
---

# Kongruencia

Oszthatósági kérdésekben gyakran csak a maradék számít; a kongruencia ezt a „modulo $m$ egyenlőséget” teszi számolható relációvá.

## Tartalom

Sok problémában — a hét napjai, az órák száma — csak a maradékos osztás maradéka fontos. Például $16 \bmod 3 = 1$ és $4 \bmod 3 = 1$: $3$-mal való oszthatóság szempontjából $16$ „$=$” $4$.

**Definíció.** Legyenek $a, b, m$ egészek. Azt mondjuk, hogy $a \equiv b \pmod m$ ($a$ és $b$ **kongruensek** modulo $m$), ha $m \mid a - b$; és $a \not\equiv b \pmod m$ ($a$ és $b$ **inkongruensek**), ha $m \nmid a - b$.

**Ekvivalens megfogalmazás.** $a \equiv b \pmod m \iff a \bmod m = b \bmod m$, azaz $a$ és $b$ $m$-mel osztva ugyanazt a maradékot adják.

**Példák.** $16 \equiv 4 \pmod 3$, mert $3 \mid 16 - 4$, és valóban $16 \bmod 3 = 1 = 4 \bmod 3$. $16 \equiv 4 \pmod 2$, mert $2 \mid 12$, és $16 \bmod 2 = 0 = 4 \bmod 2$. Viszont $16 \not\equiv 4 \pmod 5$, mert $5 \nmid 12$, és $16 \bmod 5 = 1 \neq 4 = 4 \bmod 5$.

### A kongruencia tulajdonságai

**Tétel.** Minden $a, b, c, d$ és $m$ egész számra igaz:

1. $a \equiv a \pmod m$ (reflexív);
2. $a \equiv b \pmod m$, $m' \mid m \Rightarrow a \equiv b \pmod{m'}$;
3. $a \equiv b \pmod m \Rightarrow b \equiv a \pmod m$ (szimmetrikus);
4. $a \equiv b \pmod m$, $b \equiv c \pmod m \Rightarrow a \equiv c \pmod m$ (tranzitív);
5. $a \equiv b \pmod m$, $c \equiv d \pmod m \Rightarrow a + c \equiv b + d \pmod m$;
6. $a \equiv b \pmod m$, $c \equiv d \pmod m \Rightarrow ac \equiv bd \pmod m$.

**Bizonyítás.** 1. $m \mid 0 = a - a$. 2. $m' \mid m$, $m \mid a - b \Rightarrow m' \mid a - b$. 3. $m \mid a - b \Rightarrow m \mid b - a = -(a-b)$. 4. $m \mid a - b$, $m \mid b - c \Rightarrow m \mid a - c = (a-b) + (b-c)$. 5. $m \mid a - b$, $m \mid c - d \Rightarrow m \mid (a+c) - (b+d)$. 6. $a = q_1m + b$, $c = q_2m + d \Rightarrow ac = (q_1m+b)(q_2m+d) = m(q_1q_2m + q_1d + q_2b) + bd$. $\square$

Az 1., 3. és 4. pont szerint a kongruencia ekvivalenciareláció; osztályai a [[concepts/dimatii/maradekosztaly]]ok. Az 5. és 6. pont szerint a művelettartás miatt lehet velük „úgy számolni, mint egyenletekkel”.

**Példa.** Mi lesz $345 \bmod 7$? $345 = 34\cdot 10 + 5 \equiv 6\cdot 3 + 5 = 18 + 5 \equiv 4 + 5 = 9 \equiv 2 \pmod 7$.

### Egyszerűsítés

A szorzás megfordítása nem szabad korlátlanul: $14 \equiv 6 \pmod 8 \Rightarrow 42 \equiv 18 \pmod{24}$, de visszafelé nem: $2\cdot 7 \equiv 2\cdot 3 \pmod 8$, mégis $7 \not\equiv 3 \pmod 8$.

**Tétel.** Legyenek $a, b, c, m$ egészek. Ekkor
$$ac \equiv bc \pmod m \iff a \equiv b \ \left(\operatorname{mod} \tfrac{m}{(c,m)}\right).$$

**Következmény.** Ha $(c,m) = 1$, akkor $ac \equiv bc \pmod m \iff a \equiv b \pmod m$, azaz a modulushoz relatív prím tényezővel szabadon egyszerűsíthetünk.

**Bizonyítás.** Legyen $d = (c,m)$. Ekkor $m \mid c(a-b) \iff \frac{m}{d} \mid \frac{c}{d}(a-b)$. Mivel $\left(\frac{m}{d}, \frac{c}{d}\right) = 1$, ezért $\frac{m}{d} \mid (a-b) \iff a \equiv b \pmod{\frac{m}{d}}$. $\square$

**Példa.** $2\cdot 7 \equiv 2\cdot 3 \pmod 8 \Rightarrow 7 \equiv 3 \pmod{\frac{8}{2}}$.

### További tulajdonságok (Farkas-diák)

- **Polinomokra:** ha $a \equiv b \pmod m$ és $f(x) \in \mathbb{Z}[x]$, akkor $f(a) \equiv f(b) \pmod m$ (az összeadás- és szorzástartásból adódik).
- **Megjegyzés:** $a' \equiv a \pmod m \Rightarrow (a, m) = (a', m)$ — a modulushoz vett lnko az osztály tulajdonsága.
- Az egyszerűsítési tétel bizonyítása a diákon két irányban: $\Rightarrow$ $m \mid (a-b)c \Rightarrow \frac{m}{d} \mid (a-b)\frac{c}{d}$, és $\left(\frac{m}{d}, \frac{c}{d}\right) = 1$, így $\frac{m}{d} \mid a-b$; $\Leftarrow$ ha $a - b = \frac{m}{d}q$, akkor $(a-b)c = m q \frac{c}{d}$, és $\frac{c}{d}$ egész, tehát $m \mid ac - bc$.

### Maradéktétel és osztályfelbontás (Lehman–Leighton–Meyer 9.6)

**Lemma (maradékos jellemzés).** $a \equiv b \pmod n \iff \operatorname{rem}(a,n) = \operatorname{rem}(b,n)$.

*Bizonyítás.* Legyen $a = q_1 n + r_1$, $b = q_2 n + r_2$ ($r_1, r_2 \in [0, n)$). Ekkor $a - b = (q_1 - q_2)n + (r_1 - r_2)$, ahol $r_1 - r_2 \in (-n, n)$. $n \mid a - b \iff n \mid r_1 - r_2$, és az $(-n, n)$ intervallum egyetlen $n$-többszöröse a $0$, tehát $r_1 = r_2$. $\square$

Ebből azonnal $a \equiv \operatorname{rem}(a,n) \pmod n$. A kongruencia $n$ osztályra bontja $\mathbb{Z}$-t: pl. mod $3$ a $\{\dots,-3,0,3,\dots\}$, $\{\dots,-2,1,4,\dots\}$ és $\{\dots,-1,2,5,\dots\}$ halmazokra. Modulo $n$ így csak $n$ „fajta” szám van, ezért a moduláris számolás a közönséges számolás egyszerűsítése. A modulus mindig pozitív ($n \le 0$ nem hasznos).

**Jelölési figyelmeztetés.** A „$\pmod n$” a reláció egészére vonatkozik, nem a jobb oldali tagra: $29 \equiv 15 \pmod 7$ azt jelenti, hogy $7 \mid 14$, és mindkettő maradéka $1$.

### Feladattípusok (gyakorlat 3.)

**Oszthatóság bizonyítása kongruenciával.** A tagokat a modulus szerint közös alapra hozzuk. Példa: $3^{3n+1}5^{2n+1} + 2^{5n+1}11^n \equiv 0 \pmod{17}$. Az első tag $= 3^n\cdot 3^{2n+1}5^{2n+1} = 3^n\cdot 15^{2n+1} \equiv 3^n(-2)^{2n+1} = -3^n 2^{2n+1}$, mert $15 \equiv -2$. A második tagban $11 \equiv -2\cdot 3$ és $2^{5n+1} = 2\cdot 32^n \equiv 2(-2)^n$, így $\equiv 2(-2)^n(-2)^n 3^n = 2^{2n+1}3^n$. A két tag összege $0$. Hasonlóan mod $23$: $61 \equiv -8$, $2^{5k+3} \equiv 9^k\cdot 8$, és a kifejezés $-8(-8)^k + (-8)^k\cdot 8 \equiv 0$.

**Egységgyök-egyenlet kongruenciára visszavezetve.** $z = \tfrac{1+i}{\sqrt2}$ primitív $8$-adik egységgyök, $z^k = z^n \iff k \equiv n \pmod 8$. Így $z^{3x} = i = z^2 \iff 3x \equiv 2 \pmod 8 \iff x \equiv 6 \pmod 8$ ($3x \equiv 18$, és $(3,8) = 1$-gyel egyszerűsítünk).

## Kapocs

- [[concepts/dimatii/oszthatosag]] — a definiáló reláció
- [[concepts/dimatii/maradekos-osztas]] — az ekvivalens megfogalmazás alapja
- [[concepts/dimatii/maradekosztaly]] — a kongruencia ekvivalenciaosztályai
- [[concepts/dimatii/linearis-kongruencia]] — az $ax \equiv b \pmod m$ egyenlet
- [[concepts/dimatii/szimultan-kongruenciak]] — kongruenciarendszerek
- [[concepts/kript/linearis-kongruencialis-generator]] — kongruenciákra épülő álvéletlen-generátor
- [[concepts/dimatii/maradekosztaly]] — a maradékokkal való számolás általános elve és a $\mathbb{Z}_n$ gyűrű (Lehman–Leighton–Meyer 9.7)
