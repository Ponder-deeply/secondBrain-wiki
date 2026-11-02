---
tags: [concept]
sources: [DimatIIEa02.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, Lehman-Leighton-Meyer-Mathematics-for-Computer-Science.pdf, dimat2gyak04mo.pdf]
derivation: source
kind: theorem
element: fire
updated: 2026-10-21
---

# Invertálhatóság $\mathbb{Z}_m$-ben

$\mathbb{Z}_m$-ben egy maradékosztály vagy nullosztó, vagy van multiplikatív inverze — a modulushoz vett legnagyobb közös osztó dönti el, melyik.

## Tartalom

**Tétel.** Legyen $m > 1$ egész.

- Ha $1 < (a,m) < m$, akkor $\overline{a}$ **nullosztó** $\mathbb{Z}_m$-ben: van olyan $\overline{b} \neq \overline{0}$, hogy $\overline{a}\cdot\overline{b} = \overline{0}$.
- Ha $(a,m) = 1$, akkor $\overline{a}$-nak van **reciproka** (multiplikatív inverze) $\mathbb{Z}_m$-ben: van olyan $\overline{x}$, hogy $\overline{a}\cdot\overline{x} = \overline{1}$.

**Speciálisan:** ha $m$ prím, akkor minden nem nulla maradékosztállyal lehet osztani, azaz $\mathbb{Z}_m$ test.

**Bizonyítás.** Legyen $d = (a,m)$. Ekkor $a\cdot\frac{m}{d} = \frac{a}{d}\cdot m \equiv 0 \pmod m$, ahonnan $b = m/d$ jelöléssel $\overline{a}\cdot\overline{b} = \overline{0}$, és $\overline{b} \neq \overline{0}$, mert $d > 1$.

Ha $d = 1$, akkor a [[concepts/dimatii/bovitett-euklideszi-algoritmus]]sal megadhatók olyan $x, y$ egészek, hogy $ax + my = 1$. Ekkor $ax \equiv 1 \pmod m$, azaz $\overline{a}\cdot\overline{x} = \overline{1}$. $\square$

**Példa.** Legyen $m = 9$. Ekkor $\overline{6}\cdot\overline{3} = \overline{18} = \overline{0}$, azaz $\overline{6}$ nullosztó. Viszont $(2,9) = 1$, így $\overline{2}\cdot\overline{5} = \overline{10} = \overline{1}$: $\overline{2}$ inverze $\overline{5}$.

Az invertálható osztályok tehát pontosan a [[concepts/dimatii/redukalt-maradekrendszer]] osztályai, $\mathbb{Z}_m^*$ elemei; számuk $\varphi(m)$.

**Megjegyzés (Farkas-diák).** Az inverz előállítása: $d=1$ esetén a bővített euklideszi algoritmus $ax + my = 1$-et ad, ebből $ax \equiv 1 \pmod m$, azaz $\overline{a}\cdot\overline{x} = \overline{1}$. Ha $m$ prím és $a \not\equiv 0 \pmod m$, akkor $d = 1$ mindig teljesül, ezért $\mathbb{Z}_m$ test — lásd [[concepts/dimatii/test]].

### Egyediség, egyszerűsíthetőség és ekvivalens feltételek (Lehman–Leighton–Meyer 9.9)

- **Példa.** $\mathbb{Z}_{15}$-ben $2\cdot 8 = 16 \equiv 1$, tehát $8$ inverze $2$. A $3$-nak nincs inverze: ha $3j \equiv 1$ lenne, $5$-tel szorozva $5 = 5\cdot 3 j = 15 j \equiv 0$ adódna, ellentmondás.
- **Lemma (egyediség).** Ha $i$ és $j$ is inverze $k$-nak $\mathbb{Z}_n$-ben, akkor $i = i\cdot 1 = i(kj) = (ik)j = 1\cdot j = j$.
- **Inverz képlete.** Ha $(k,n) = 1$, akkor $sn + tk = 1$ (bővített euklideszi algoritmus), és mod $n$ redukálva $\operatorname{rem}(t,n)\cdot k = 1$: az inverz $\operatorname{rem}(t,n)$.
- **Egyszerűsíthetőség.** $k$ *egyszerűsíthető* $\mathbb{Z}_n$-ben, ha $ka = kb \Rightarrow a = b$ minden $a,b\in[0,n)$-re. Ha $k$-nak van inverze, egyszerűsíthető (szorzunk az inverzzel). Ellenpélda: $3\cdot 10 \equiv 3\cdot 5 \pmod{15}$, de $10 \not\equiv 5$.

**Tétel.** $k \in [0,n)$-re ekvivalens: (i) $(k,n) = 1$; (ii) $k$-nak van inverze $\mathbb{Z}_n$-ben; (iii) $k$ egyszerűsíthető $\mathbb{Z}_n$-ben.

**Alkalmazás (Turing „2.0-ás kódja”).** Titkosítás: $\hat m = m k \pmod n$ ($n$ prím, $k$ titkos kulcs); visszafejtés a $k$ inverzével szorozva. A sebezhetősége: ha $m$ és $\hat m$ is ismert (known-plaintext), $m$ inverzével szorozva $k = j\hat m$ kiadódik. (Az egész számokon való szorzással titkosító 1.0-ás változatot a két titkosított üzenet lnko-ja törte meg.)

### Feladattípusok (gyakorlat 4.)

**Mely inverzek léteznek?** Az $a^{-1} \bmod m$ az $ax \equiv 1 \pmod m$ megoldása. Döntés: $(a,m) = 1$? Ha igen, ad hoc észrevétellel ($1 + 2\cdot 7 = 15$, $1 + 8 = 9$, $31 \equiv -3 \pmod{17}$ és $1 + 17 = 18$) vagy bővített euklideszi algoritmussal számolunk: $3^{-1} \equiv 5 \pmod 7$, $3^{-1} \equiv 3 \pmod 8$, $2^{-1} \equiv 4 \pmod 7$, $1^{-1} \equiv 1$, $2^{-1} \equiv 2 \pmod 3$, $31^{-1} \equiv 11 \pmod{17}$. Nem létezik: $0^{-1} \bmod 8$ és $2^{-1} \bmod 8$ ($(2,8) = 2$).

**Euler–Fermat-féle zárt alak.** $a^{-1} \equiv a^{\varphi(m)-1}$: $3^{-1} \equiv 3^5 \pmod 7$, $3^{-1} \equiv 3^3 \pmod 8$ ($\varphi(8) = 4$), $2^{-1} \equiv 2^5 \pmod 7$, $31^{-1} \equiv 31^{15} \pmod{17}$ — ez utóbbit gyakorlatilag csak [[concepts/dimatii/gyors-hatvanyozas]]sal lehet kiszámolni.

**Nilpotens elemek.** Ha $m$ nem négyzetmentes, van olyan $a \not\equiv 0$, amelynek egy hatványa $0$: $\mathbb{Z}_4$-ben $2^2 = 4 \equiv 0$. Általában $m = p^n q$ ($p \nmid q$, $n > 1$) esetén $pq \not\equiv 0$, de $(pq)^n \equiv 0 \pmod m$. Mátrixoknál is van ilyen: $M = \begin{pmatrix}0&1&0\\0&0&1\\0&0&0\end{pmatrix}$, $M^3 = 0$.

## Kapocs

- [[concepts/dimatii/maradekosztaly]] — a $\mathbb{Z}_m$-beli műveletek
- [[concepts/dimatii/redukalt-maradekrendszer]] — az invertálható osztályok halmaza
- [[concepts/dimatii/bovitett-euklideszi-algoritmus]] — az inverz kiszámítása
- [[concepts/dimatii/legnagyobb-kozos-oszto]] — a döntő mennyiség
- [[concepts/dimatii/test]] — prím modulusnál $\mathbb{Z}_m$ test
- [[concepts/dimatii/euler-fermat-tetel]] — az inverz zárt alakja, $\overline{a}^{\,\varphi(m)-1}$
- [[concepts/dimatii/nemlinearis-kongruencia]] — miért lehet több megoldás a fokszámnál
- [[concepts/dimatii/turing-kodja]] — a szorzásos titkosítás dekódolása az inverzzel
