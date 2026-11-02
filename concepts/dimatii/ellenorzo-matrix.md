---
tags: [concept]
sources: [DimatIIEa09.pdf, DimatIIEa10.pdf, dm2gy12.pdf]
derivation: source
kind: definition
element: fire
updated: 2026-10-21
---

# Ellenőrző mátrix

Az a mátrix, amelynek magtere éppen a lineáris kód; belőle a kódszó-tulajdonság egy szorzással ellenőrizhető, és a kód távolsága is leolvasható.

## Tartalom

### Definíció

Egy $[n,k,d]_q$ kódnak $\mathbf{H} \in \mathbb{F}_q^{(n-k) \times n}$ mátrix az **ellenőrző mátrixa**, ha
$$\mathbf{H}v = 0 \iff v \text{ kódszó}.$$

Egy $\mathbf{G}$ mátrixhoz tartozó kódolásnak $\mathbf{H}$ pontosan akkor ellenőrző mátrixa, ha $\mathrm{Ker}(\mathbf{H}) = \mathrm{Im}(\mathbf{G})$.

### Példák

1. A $(*)$ kód egy ellenőrző mátrixa:
   $$\mathbf{H} = \begin{pmatrix} 1 & 1 & 1 & 0 & 0 \\ 0 & 1 & 0 & 1 & 0 \\ 1 & 0 & 0 & 0 & 1 \end{pmatrix}.$$
2. A háromszori ismétlés kódjának egy ellenőrző mátrixa:
   $$\mathbf{H} = \begin{pmatrix} -1 & 1 & 0 \\ -1 & 0 & 1 \end{pmatrix}.$$
3. A paritásbites kód egy ellenőrző mátrixa: $\mathbf{H} = (1\ 1\ \cdots\ 1)$.

### Szisztematikus kód ellenőrző mátrixa

**Állítás.** Legyen $\mathbf{G} = \begin{pmatrix} \mathbf{I}_k \\ \mathbf{P} \end{pmatrix}$ egy szisztematikus kód generátormátrixa. Ekkor $\mathbf{H} = (-\mathbf{P} \mid \mathbf{I}_{n-k})$ ellenőrző mátrixa a kódnak.

*Bizonyítás.*
$$\mathbf{H}\cdot\mathbf{G} = (-\mathbf{P} \mid \mathbf{I}_{n-k})\begin{pmatrix} \mathbf{I}_k \\ \mathbf{P}\end{pmatrix} = -\mathbf{P} + \mathbf{P} = \mathbf{0} \in \mathbb{F}_q^{(n-k)\times k}.$$
Tehát bármely $u$ kódolandó szóra $\mathbf{H}(\mathbf{G}u) = 0$, vagyis $\mathrm{Im}(\mathbf{G}) \subset \mathrm{Ker}(\mathbf{H})$, amiből $\dim(\mathrm{Im}(\mathbf{G})) \le \dim(\mathrm{Ker}(\mathbf{H}))$. Mivel $\dim(\mathrm{Im}(\mathbf{G})) = k$ és $\dim(\mathrm{Ker}(\mathbf{H})) \le k$, ezért $\dim(\mathrm{Im}(\mathbf{G})) \ge \dim(\mathrm{Ker}(\mathbf{H}))$ is teljesül, így $\mathrm{Im}(\mathbf{G}) = \mathrm{Ker}(\mathbf{H})$. $\square$

### A kód távolsága leolvasható az ellenőrző mátrixból

**Állítás.** Legyen $\mathbf{H}$ egy $[n,k]$ kód ellenőrző mátrixa. A $\mathbf{H}$-nak pontosan akkor van $\ell$ darab lineárisan összefüggő oszlopa, ha van olyan kódszó, aminek a súlya legfeljebb $\ell$.

*Bizonyítás.* ($\Rightarrow$) Ha $\sum_{j=1}^{\ell} u_j \cdot h_{\ell_j} = 0$, tekintsük azt a vektort, aminek az $\ell_j$-edik koordinátája $u_j$, a többi pedig $0$. Ez egyrészt kódszó lesz, másrészt a súlya legfeljebb $\ell$.
($\Leftarrow$) Legyen $u = (u_1, \dots, u_n)^T$ az a kódszó, aminek a súlya $\ell$. Ekkor $\mathbf{H}$-nak az $u$ nem-nulla koordinátáinak megfelelő oszlopai lineárisan összefüggőek. $\square$

**Következmény.** A kód távolsága a legkisebb pozitív egész $\ell$, amire létezik az ellenőrző mátrixnak $\ell$ darab lineárisan összefüggő oszlopa.

**Példa.** A $(*)$ kód fenti $\mathbf{H}$ mátrixában egyik oszlopvektor sem a nullvektor, így nincs 1 darab lineárisan összefüggő oszlop; egyik oszlopvektor sem többszöröse egy másiknak, így nincs 2 darab sem. Az 1., 3. és 5. oszlop lineárisan összefüggő, így a kód távolsága 3.

### Feladattípusok és módszerek: $[n,k,d]$ létezése az ellenőrző mátrix oszlopaiból (2024. 12. sorozat)

**Elv.** $d\ge3\iff\mathbf H$ oszlopai nem nullák és páronként lineárisan függetlenek (egyik sem skalárszorosa egy másiknak). Ha $\mathbf H$-nak $r=n-k$ sora van, a páronként független oszlopok száma legfeljebb $\frac{q^r-1}{q-1}$ (a projektív tér pontjai). $r=2$ esetén ez $q+1$.

**Létezik-e $\mathbb{F}_q$ fölött $[n,k,d]$ kód?**

- $[7,6,2]_5$: létezik, a paritásellenőrző kód $c_7=-(c_1+\dots+c_6)$ ($\mathbf H=(1\ 1\ \cdots\ 1)$); Singleton-egyenlőség, MDS.
- $[8,6,3]_2$: **nem**, mert $r=2$, és $\mathbb{F}_2^2$-ben csak $q+1=3$ páronként független oszlop van, nem $8$ (a Hamming-korlát is kizárja: $2^6(1+8)=576>2^8$).
- $[8,6,3]_9$: **létezik**, mert $q+1=10\ge8$ oszlop választható (MDS kód).
- $[6,4,3]_2$: **nem** ($3<6$ oszlop; Hamming-korlát: $2^4\cdot7=112>2^6$).
- $[6,4,3]_5$: **létezik**, $q+1=6\ge6$ (MDS).
- $n=5,k=2,d=4$: Singleton szerint $d\le n-k+1=4$, tehát MDS kód kellene. A generátormátrix öt sora $\mathbb{F}_q^2$-ben páronként nem arányos nem nulla vektor kell legyen (különben egy üzenet két helyen is nullát adna, így $w\le3$), ezért $5\le q+1$, azaz $q\ge4$. $q=2$ és $q=3$ kizárt, $q=4$-re létezik (mind az $5=q+1$ pont kell), és minden $q\ge4$ prímhatványra is.

**Tipikus hiba.** A Singleton-korlát *teljesülésénél* megállni (az csak szükséges feltétel: $[8,6,3]_2$ megfelel neki, mégsem létezik); $d$-t az $\mathbf H$ sorainak számával keverni.

## Kapocs

- [[concepts/dimatii/linearis-kod]] — a kód, amelyet a mátrix magtereként kapunk
- [[concepts/dimatii/generatormatrix]] — a duális, képtér felőli leírás
- [[concepts/dimatii/szindroma-dekodolas]] — a $\mathbf{H}v$ szorzat mint dekódolási eszköz
- [[concepts/dimatii/hamming-kod]] — konstrukció, amely közvetlenül az ellenőrző mátrix oszlopaiból indul
