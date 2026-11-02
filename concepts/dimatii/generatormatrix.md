---
tags: [concept]
sources: [DimatIIEa09.pdf, DimatIIEa10.pdf, dm2gy12.pdf]
derivation: source
kind: definition
element: fire
updated: 2026-10-21
---

# Generátormátrix

Lineáris kód esetén a kódolást megvalósító mátrix, amelynek képtere maga a kód; szisztematikus alakban a kódszó eleje az üzenet maga.

## Tartalom

### Definíció

Lineáris kód esetén a kódolás elvégezhető mátrixszorzással. Legyen $G : \mathbb{F}_q^k \to \mathbb{F}_q^n$ egy teljes rangú lineáris leképezés, illetve $\mathbf{G} \in \mathbb{F}_q^{n \times k}$ a hozzá tartozó mátrix. $K = \mathrm{Im}(G)$ esetén $\mathbf{G}$-t a $K$ kód **generátormátrixának** nevezzük.

A kódolás:
$$\begin{pmatrix} g_{11} & \cdots & g_{1k} \\ \vdots & \ddots & \vdots \\ g_{n1} & \cdots & g_{nk}\end{pmatrix} \begin{pmatrix} m_1 \\ \vdots \\ m_k \end{pmatrix} = \begin{pmatrix} c_1 \\ \vdots \\ c_n \end{pmatrix}.$$

### Példák

1. A $(*)$ kód egy generátormátrixa:
   $$\mathbf{G} = \begin{pmatrix} 1 & 0 \\ 0 & 1 \\ 1 & 1 \\ 0 & 1 \\ 1 & 0 \end{pmatrix}.$$
2. A háromszori ismétlés kódjának egy generátormátrixa: $\mathbf{G} = (1,1,1)^T$.
3. A paritásbites kód egy generátormátrixa az $\mathbf{I}_{n-1}$ egységmátrix alá írt csupa 1-es sor.

### Szisztematikus kódolás

Ha a kódszavak első $k$ betűje megfelel az eredeti kódolandó szónak, akkor **szisztematikus kódolásról** beszélünk. Ekkor az első $k$ karakter az **üzenetszegmens**, az utolsó $n-k$ pedig a **paritásszegmens**.

Példák:
1. a háromszori ismétlés kódja: $(\underbrace{a}_{\text{üz.sz.}}, \underbrace{a, a}_{\text{par.sz.}})$;
2. a paritásbites kód: $\left(\underbrace{b_1, \dots, b_{n-1}}_{\text{üz.sz.}}, \underbrace{\textstyle\sum_{j=1}^{n-1} b_j}_{\text{par.sz.}}\right)$.

Szisztematikus kódolás esetén könnyen tudunk dekódolni: a paritásszegmens elhagyásával megkapjuk a kódolandó szót.

Egy szisztematikus kód generátormátrixa speciális alakú:
$$\mathbf{G} = \begin{pmatrix} \mathbf{I}_k \\ \mathbf{P} \end{pmatrix},$$
ahol $\mathbf{I}_k \in \mathbb{F}_q^{k \times k}$ egységmátrix, továbbá $\mathbf{P} \in \mathbb{F}_q^{(n-k) \times k}$.

### Feladattípusok és módszerek: $\mathbf{G}$ és $\mathbf{H}$ felírása (2024. 12. sorozat)

**Kódolási szabályból mátrix.** A komponensek együtthatóiból sorokat írunk: az első $k$ komponens ($c_1,\dots,c_k$) az $\mathbf{I}_k$ sorait adja, a további komponensek együtthatói a $\mathbf{P}$ sorait. Az $n,k$ paraméterek az első bejegyzésből: $n$ a komponensek száma, $k$ az üzenet hossza.

*Példa* ($\mathbb{F}_5$, $(c_1,c_2,c_3)\mapsto(c_1,c_2,c_3,2c_1+3c_2,c_1+4c_3)$): $n=5$, $k=3$,
$$\mathbf G=\begin{pmatrix}\mathbf I_3\\ \mathbf P\end{pmatrix},\ \mathbf P=\begin{pmatrix}2&3&0\\1&0&4\end{pmatrix},\qquad \mathbf H=(-\mathbf P\mid\mathbf I_2)=\begin{pmatrix}3&2&0&1&0\\4&0&1&0&1\end{pmatrix}\ (\bmod 5).$$
Ellenőrzés: $\mathbf H\mathbf G=-\mathbf P+\mathbf P=0$; a $\mathbf H$ harmadik és ötödik oszlopa megegyezik ($(0,1)^T$), tehát két oszlop összefüggő, és $d=2$.

**Nem szisztematikus mátrix.** Ha a megadott $\mathbf G$ első $k$ sora nem az egységmátrix, sorműveletekkel (illetve a kódszavak koordinátáinak permutálásával) szisztematikus alakra hozzuk, vagy az $\mathrm{Ker}\,\mathbf H=\mathrm{Im}\,\mathbf G$ feltételből oldjuk meg a $\mathbf H$ sorait. A 2024. 12. sorozat 3. feladata ($\mathbb{F}_2$ fölött, $n\times k$ mátrixok): az $\mathbf{G}_1=\begin{pmatrix}\mathbf I_4\\ \mathbf P\end{pmatrix}$ ($\mathbf P$ sorai $1100$, $1001$, $1110$) esetén $[7,4]$, $\mathbf H=(\mathbf P\mid\mathbf I_3)$, a $\mathbf H$ oszlopai között egyező párok vannak (a 3. és 7., a 4. és 6.), így $d=2$; a $\mathbf G_2$ ($\mathbf I_3$ alatt a sorok $111,100,111,010$) $[7,3,3]$ kódot ad (nincs két egyező vagy nulla oszlop a $\mathbf H$-ban). A $\mathbf G_3$ ötsoros mátrixa $\mathbb{F}_2$ fölött $[5,3]$, $d=2$ (a test nincs kiírva a lapon; $\mathbb{F}_2$-t feltételeztük).

**Két különböző generátor- és ellenőrző mátrix.** A $\mathbf G\mapsto\mathbf G\mathbf A$ ($\mathbf A$ invertálható $k\times k$) ugyanazt a kódot adja, és a $\mathbf H$ sorai tetszőlegesen kombinálhatók ($\mathbf B\mathbf H$, $\mathbf B$ invertálható). Példa: $(c_1,c_2,c_3)\mapsto(c_1,c_2,c_3,c_1+c_2,c_1+c_3)$ binárisan: $\mathbf G=\begin{pmatrix}\mathbf I_3\\ 110\\ 101\end{pmatrix}$, $\mathbf H=\begin{pmatrix}1&1&0&1&0\\1&0&1&0&1\end{pmatrix}$; másik pár: $\mathbf G'=\mathbf G\mathbf A$ az $\mathbf A=\begin{pmatrix}1&1&0\\0&1&0\\0&0&1\end{pmatrix}$ mátrixszal (sorai $110,010,001,100,111$), $\mathbf H'$ a $\mathbf H$ második sorához az elsőt adva: $\begin{pmatrix}1&1&0&1&0\\0&1&1&1&1\end{pmatrix}$.

**Tipikus hibák.** A mátrix irányát elcserélni (itt $\mathbf G\in\mathbb{F}_q^{n\times k}$, a kód $\mathbf G\mathbf m$ oszlopvektorok); $\mathbb{F}_5$ fölött $-\mathbf P$ helyett $\mathbf P$-t írni a $\mathbf H$-ban; a $d$-t az $\mathbf H$ sorainak vizsgálatával számolni (az oszlopok összefüggősége számít).

## Kapocs

- [[concepts/dimatii/linearis-kod]] — a kód, amelyet a mátrix generál
- [[concepts/dimatii/ellenorzo-matrix]] — a duális leírás; szisztematikus alakban $\mathbf{H} = (-\mathbf{P} \mid \mathbf{I}_{n-k})$
- [[concepts/dimatii/szindroma-dekodolas]] — a dekódolás, amely az ellenőrző mátrixra épül
- [[concepts/dimatii/hibakorlatozo-kodolas-peldai]] — a paritásbites kód mint szisztematikus lineáris kód
