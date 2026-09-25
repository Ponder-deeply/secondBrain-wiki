---
tags: [concept, dimatii/kongruenciak]
sources: [DimatIIEa02.pdf]
derivation: source
updated: 2026-09-08
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

## Kapocs

- [[concepts/dimatii/euler-fi-fuggveny]] — a kitevőben szereplő függvény
- [[concepts/dimatii/redukalt-maradekrendszer]] — a bizonyítás kerete
- [[concepts/dimatii/teljes-maradekrendszer]] — a lemma bővebb változata
- [[concepts/dimatii/invertalhatosag-zm-ben]] — az inverz zárt alakja
- [[concepts/dimatii/linearis-kongruencia]] — alternatív megoldási módszer
- [[concepts/dimatii/kongruencia]] — az egyszerűsítési szabály
