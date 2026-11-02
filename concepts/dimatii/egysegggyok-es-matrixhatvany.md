---
tags: [concept]
sources: [dimat2gyak01mo.pdf, dimat2gyak02mo.pdf, dimat2gyak03mo.pdf, Dimat2mintaZH1.pdf, dm2gy06.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-22
---

# Egységgyökök és mátrixok hatványa

Ha egy elem valamilyen hatványa az egységelem, akkor a hatványai ciklikusan ismétlődnek, így a kitevőt elég az ismétlődési periódussal vett osztási maradékával helyettesíteni. Ez a komplex egységgyökökre, a mátrixokra és a maradékosztályokra ugyanúgy működik.

## Tartalom

### A szabály

**Állítás.** Legyen $z$ primitív $m$-edik egységgyök, azaz $z^m = 1$, de $z^k \neq 1$, ha $0 < k < m$. Ha $n = qm + k$ a [[concepts/dimatii/maradekos-osztas]] szerint, akkor
$$z^n = (z^m)^q \cdot z^k = z^k = z^{\,n \bmod m}.$$
Ez akkor is igaz, ha $z$ csak egységgyök (nem primitív), de érdemes a legkisebb olyan $m$-et megkeresni, amelyre $z^m = 1$.

Következmény: $z^k = z^n \iff k \equiv n \pmod m$, és $z^n = 1 \iff m \mid n$.

### Komplex számok

| $z$ | rend | $z^3$ | $z^{13}$ | $z^{135}$ |
|---|---:|---|---|---|
| $i$ | 4 | $-i$ | $i$ | $-i$ |
| $\frac{1+i}{\sqrt2}$ | 8 | $\frac{-1+i}{\sqrt2}$ | $\frac{-1-i}{\sqrt2}$ | $\frac{1-i}{\sqrt2}$ |

Itt $13 \bmod 8 = 5$, $135 \bmod 8 = 7$, $13 \bmod 4 = 1$, $135 \bmod 4 = 3$.

Ha $z$ nem egységgyök, de egy egységgyök valós számszorosa, akkor a hatvány a szorzót is hatványozza. Például $z = 1 - i = \sqrt2 \cdot w$, ahol $w = \frac{1-i}{\sqrt2}$ primitív nyolcadik egységgyök, tehát $z^3 = 2\sqrt2 \cdot w^3 = -2 - 2i$ és $z^{13} = 2^6\sqrt2\,w^5 = -64 + 64i$.

**ZH-példa.** $z = \frac12 + \frac{\sqrt3}{2}i = \cos 60^\circ + i\sin 60^\circ$ primitív hatodik egységgyök, ezért $z^3 = -1$ és $z^{12357} = z^{12357 \bmod 6} = z^3 = -1$ (mert $12357 = 6 \cdot 2059 + 3$).

**Közös egységgyök-feltételek.** Ha $z^n = w^n = 1$, ahol $z$ rendje $4$, $w$ rendje $6$, akkor $4 \mid n$ és $6 \mid n$, vagyis $[4,6] = 12 \mid n$.

**Exponenciális egyenlet.** $z = \frac{1+i}{\sqrt2}$ esetén $z^{3x} = i = z^2 \iff 3x \equiv 2 \pmod 8$. Mivel $(3,8) = 1$, $3x \equiv 18 \pmod 8$ egyszerűsíthető: $x \equiv 6 \pmod 8$. Ez a feladat kongruenciára vezetett vissza, lásd [[concepts/dimatii/linearis-kongruencia]].

### Mátrixok

Ugyanez a gondolat mátrixhatványokra is érvényes, ha $M^m = I$.

- $M = \begin{pmatrix} 8 & -21 \\ 3 & -8 \end{pmatrix}$: $M^2 = I$, így $M^5 = M$ és $M^{123} = M$.
- $M = \begin{pmatrix} -3 & 2 \\ -5 & 3 \end{pmatrix}$: $M^2 = -I$, tehát $M^4 = I$, $M^5 = M$ és $M^{123} = (-I)^{61} M = -M$. Az $i$-hez hasonlóan viselkedik.
- $M = \begin{pmatrix} 1 & \sqrt3 \\ -\sqrt3 & 1 \end{pmatrix}$: $M^3 = -8I$, így $M^6 = 64I$ és $M^{123} = (M^3)^{41} = -2^{41} I$. Az $\begin{pmatrix} a & b \\ -b & a \end{pmatrix}$ alakú mátrixok az $a + bi$ komplex számokat valósítják meg, ez az $1 + \sqrt3 i = 2(\cos 60^\circ + i\sin 60^\circ)$ kétszeres hatodik egységgyök.

**Permutációmátrix.** A $\begin{pmatrix} 0&0&1\\1&0&0\\0&1&0 \end{pmatrix}$ mátrixra $M^3 = I$, így $M^2 = M^{-1}$, $M^5 = M^2$, $M^{123} = I$.

### Séták száma: szomszédsági mátrix hatványa

Egy irányított gráf $M$ szomszédsági mátrixának $n$-edik hatványában az $(i,j)$ elem az $i$-ből $j$-be vezető $n$ hosszú sétákat számolja. Ez teljes indukcióval látszik: $(M^2)_{ij} = \sum_k M_{ik}M_{kj}$, vagyis a közbülső csúcs szerinti esetszétválasztás.

A hat csúcsú irányított körre ($1 \to 2 \to \dots \to 6 \to 1$) $M^6 = I$, tehát $M^n = M^{n \bmod 6}$. Így $M^{24} = I$ és $M^{113} = M^5 = M^{-1}$. Az $M$ permutációmátrix, a $\sigma: i \mapsto i+1$ ciklikus permutációé; hatványa a permutáció hatványának mátrixa.

## Kapocs

- [[concepts/dimatii/maradekos-osztas]] — a kitevő maradékos osztása adja a szabályt
- [[concepts/dimatii/hatvanyok-periodicitasa-zm-ben]] — ugyanez maradékosztályokra, és a kitevő redukálásának csapdája
- [[concepts/dimatii/euler-fermat-tetel]] — a periódus $\varphi(m)$ osztója $\mathbb{Z}_m^*$-ban
- [[concepts/dimatii/legkisebb-kozos-tobbszoros]] — két egységgyök közös periódusa
- [[concepts/dimatii/linearis-kongruencia]] — az exponenciális egyenlet kongruenciára vezet
