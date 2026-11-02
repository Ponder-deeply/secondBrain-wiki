---
tags: [concept]
sources: [dimat2gyak01mo.pdf, dimat2gyak02mo.pdf, Dimat2mintaZH1.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-21
---

# Komplex egységgyökök és mátrixok hatványai

Ha egy objektum (komplex szám, mátrix) valamelyik pozitív hatványa $1$ (illetve az egységmátrix), akkor a hatványai periodikusan ismétlődnek, így $z^n$ csak $n$ maradékától függ — ezt a maradékos osztás tétele indokolja.

## Tartalom

### Alaptétel

Legyen $z$ **primitív $m$-edik egységgyök**: $z^m = 1$, de $z^k \neq 1$, ha $0 < k < m$. Ha $n = qm + k$ ($0 \le k < m$) a [[concepts/dimatii/maradekos-osztas]] szerint, akkor
$$z^n = (z^m)^q \cdot z^k = z^k, \qquad \text{azaz} \qquad z^n = z^{\,n \bmod m}.$$
Ez akkor is igaz, ha $z$ csak egy (nem feltétlenül primitív) $m$-edik egységgyök, de célszerű mindig a legkisebb olyan $m$-et keresni, amelyre $z^m = 1$. Ugyanez a gondolat érvényes bármely műveletre, ahol a hatványsorozat visszatér az egységhez (mátrixok, permutációk), lásd lent. A bizonyítás a forrás szerint egysoros: $z^n = z^{qm+k} = (z^m)^q z^k$.

Ugyanez egyben a kitevő **redukciója** a [[concepts/dimatii/euler-fermat-tetel]] mintájára, ott a modulus körében.

**Következmény (mikor $z^n = 1$?).** $z^n = 1 \iff m \mid n$. Ha két egységgyökre egyszerre kell $z^n = w^n = 1$, akkor $n$ a két rend közös többszöröse, azaz a [[concepts/dimatii/legkisebb-kozos-tobbszoros]] többszöröse.

### Feladattípusok és módszerek

**1. $z^k$ értéke, ha $z$ egységgyök.** Menet: (i) trigonometrikus alak, $z = \cos\varphi + i\sin\varphi$; (ii) a rend $m$ (a legkisebb pozitív $m$ az $m\varphi \in 2\pi\mathbb{Z}$ feltételből); (iii) $n \bmod m$; (iv) a kis hatvány kiszámítása.

- $z = i$ primitív negyedik egységgyök: $i^{4n} = 1$, $i^{4n+1} = i$, $i^{4n+2} = -1$, $i^{4n+3} = -i$. Így $i^3 = -i$, $i^{13} = i^{12+1} = i$, $i^{135} = i^{120+12+3} = -i$.
- $z = \frac{1+i}{\sqrt 2} = \cos\frac\pi4 + i\sin\frac\pi4$ primitív nyolcadik egységgyök. $z^{3} = \frac{-1+i}{\sqrt 2}$, $z^{13} = z^5 = \frac{-1-i}{\sqrt 2}$, $z^{135} = z^{128+7} = z^7 = \frac{1-i}{\sqrt 2}$.
- $z = \frac12 + \frac{\sqrt3}{2}i = \cos 60^\circ + i\sin 60^\circ$ primitív hatodik egységgyök: $z^{13} = z$, $z^{135} = z^3 = -1$, $z^{13579} = z$ (mert $13579 = 6\cdot 2263 + 1$). A konjugáltja, $\bar z$, szintén primitív hatodik egységgyök, és $\bar z^n = \overline{z^n}$. A $-\frac12 - \frac{\sqrt3}{2}i$ ($240^\circ$) primitív harmadik egységgyök: kitevője $3$-mal redukálódik, $z^{135} = z^0 = 1$.

**2. $z$ nem egységgyök, de egységgyök valós számszorosa.** Ha pl. $z = 1 - i = \sqrt2\left(\cos(-\tfrac\pi4) + i\sin(-\tfrac\pi4)\right)$, akkor $z^n = \sqrt2^{\,n}\cdot\left(\cos(-\tfrac{n\pi}{4}) + i\sin(-\tfrac{n\pi}{4})\right)$: a *szög* $n \bmod 8$-tól függ, a *hossz* viszont nő. Például $z^3 = 2\sqrt2\cdot\frac{-1-i}{\sqrt 2} = -2-2i$, $z^{13} = \sqrt2^{13}\cdot\frac{-1+i}{\sqrt2} = 2^6(-1+i) = -64+64i$, $z^{135} = 2^{67}(1+i)$. Ne keressünk itt kitevőt, amelyre $z^m = 1$: nincs ilyen.

**3. Mátrix hatványai.** Számoljuk ki $M^2$-t (és $M^3$-t), és keressünk olyat, ami az egységmátrix valamely skalárszorosa; utána a kitevőt maradékosan osztjuk.

- $M = \begin{pmatrix}8&-21\\3&-8\end{pmatrix}$: $M^2 = I$, ezért $M^5 = M$, $M^{123} = M$.
- $M = \begin{pmatrix}-3&2\\-5&3\end{pmatrix}$: $M^2 = -I$ (mint az $i$), $M^4 = I$; $M^5 = M$, $M^{123} = M^{122}M = (-I)^{61}M = -M$.
- $M = \begin{pmatrix}1&\sqrt3\\-\sqrt3&1\end{pmatrix}$: $M^2 = 2\begin{pmatrix}-1&\sqrt3\\-\sqrt3&-1\end{pmatrix}$, $M^3 = -8I$, így $M^6 = 64 I$ és $M^{123} = (M^3)^{41} = -2^{41}I$. Ez azért működik, mert az $\begin{pmatrix}a&b\\-b&a\end{pmatrix}$ alakú valós mátrixok az $a+bi$ komplex számok egy megvalósítását adják, itt az $1 + \sqrt3 i = 2(\cos 60^\circ + i\sin 60^\circ)$ számot (hossz 2, szög $60^\circ$).
- $M = \begin{pmatrix}0&0&1\\1&0&0\\0&1&0\end{pmatrix}$ permutációmátrix: $M^3 = I$, $M^{123} = (M^3)^{41} = I$, $M^5 = M^2 = M^{-1}$.

**4. Irányított kör szomszédsági mátrixa.** Ha $M$ egy $N$ csúcsú gráf szomszédsági mátrixa ($M_{ij}$ az $i \to j$ élek száma), akkor $(M^n)_{ij}$ az $i$-ből $j$-be vezető $n$ hosszú *séták* száma. (Indok: $(M^2)_{ij} = \sum_k M_{ik}M_{kj}$ a középső csúcs szerinti esetszétválasztás; általában teljes indukcióval.) A 6 csúcsú irányított körre ($1\to2\to\dots\to6\to1$) $n$ hosszú séta csak $i$-ből $i+n$-be ($\bmod 6$) vezet, ezért $M^6 = I$ és $M^n = M^{n \bmod 6}$: $M^{24} = M^0 = I$, $M^{113} = M^5 = M^{-1}$ (ez a "léptetés visszafelé" mátrixa). Az $M$ egy *permutációmátrix*: minden sorában és oszlopában pontosan egy $1$ áll, hatványa a permutáció hatványához tartozó mátrix.

**5. Közös egységgyök-feltétel.** $z = i$ és $w = \frac12 + \frac{\sqrt3}{2}i$ esetén $z^n = 1 \iff 4 \mid n$, $w^n = 1 \iff 6 \mid n$, tehát $z^n = w^n = 1 \iff [4,6] = 12 \mid n$, vagyis $n = 12k$.

### Tipikus hibák

- A kitevőt a *nem megfelelő* modulussal redukáljuk: a modulus a **rend** ($z$ esetén $8$ a $\frac{1+i}{\sqrt2}$-nél, $6$ a $60^\circ$-nál), nem a nevezők vagy a szög fokszáma.
- Nem egységgyökre alkalmazzuk a $z^n = z^{n \bmod m}$ szabályt: $1-i$ esetén a hossz $\sqrt2^{\,n}$ nem periodikus.
- A $\sin$/$\cos$ cseréje: a forrás $\sin 60^\circ + i\cos 60^\circ$ alakot ír, de az érték a $\cos + i\sin$ alak szerint számolandó (ez a konjugált-párok felismerését nem zavarja, de a szöget mindig a $\cos$ és $\sin$ alapján olvassuk le).
- Mátrixnál csak $M^2$-t számolunk ki és nem veszünk észre $M^3$-nál vagy $M^2 = -I$-nél adódó rövid periódust.

### ZH-példa

*Minta-ZH 1. feladat (a):* $z = \frac12 + \frac{\sqrt3}{2}i$ esetén $z^3$ és $z^{12357}$ értéke. $z$ primitív hatodik egységgyök, $z^3 = -1$; $12357 = 6\cdot 2059 + 3$, tehát $z^{12357} = z^3 = -1$.

## Kapocs

- [[concepts/dimatii/maradekos-osztas]] — a kitevő redukciójának alapja
- [[concepts/dimatii/primitiv-gyok]] — primitív elemek a $\mathbb{Z}_p^*$-ban: ott is a hatványok ciklikusak
- [[concepts/dimatii/euler-fermat-tetel]] — a kitevő redukciója modulo $\varphi(m)$
- [[concepts/dimatii/legkisebb-kozos-tobbszoros]] — a $z^n = w^n = 1$ feltétel
- [[concepts/dimatii/gyors-hatvanyozas]] — nagy kitevők kezelése modulo számoláskor
