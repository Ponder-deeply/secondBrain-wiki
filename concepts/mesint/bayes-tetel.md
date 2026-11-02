---
tags: [concept]
sources: [10.bizonytalansag.pdf]
derivation: source
kind: theorem
element: fire
updated: 2026-10-12
---

# Bayes-tétel

A Bayes-tétel a feltételes valószínűség megfordítását adja: $p(B \mid A)$-t az ismertebb $p(A \mid B)$ és az apriori valószínűségek segítségével számolja ki.

## Tartalom

### Alakjai

a) **Klasszikus**:
$$p(B \mid A) = \frac{p(A \mid B)\,p(B)}{p(A)}$$

b) **Háttértudás ($E$) mellett**:
$$p(B \mid A, E) = \frac{p(A \mid B, E)\,p(B \mid E)}{p(A \mid E)}$$

c) **Általánosított** ($B_1,\dots,B_n$ teljes és független eseményrendszer):
$$p(B_i \mid A) = \frac{p(A \mid B_i)\,p(B_i)}{\sum_k p(A \mid B_k)\,p(B_k)}$$

### Példa: szuvas-e egy fog, ha lyukas és fáj? (Russel–Norvig)

Keressük: $p(sz \mid ly, f)$. Apriori ismeretek: $p(sz)=0.65$, $p(f \mid sz)=0.5$, $p(f \mid \neg sz)=0.1$, $p(ly \mid \neg sz)=0.01$, és $p(ly \mid sz)$ értéke 0.95 a feladatkitűzésben, de a végső számolásban 0.7 szerepel (a dia belső ellentmondása).

- A klasszikus alak itt zsákutca: $p(sz \mid ly,f) = p(f,ly \mid sz)\,p(sz)/p(f,ly)$, de csak $p(sz)$-t ismerjük.
- **Bayes-i frissítés**: először a háttértudásos alakot alkalmazzuk az $f$ eseményre mint háttértényre, majd a $p(sz \mid f)$-re a közönséges Bayes-tételt:
$$p(sz \mid ly,f) = \frac{p(ly \mid sz,f)\,p(sz \mid f)}{p(ly \mid f)} = \frac{p(ly \mid f,sz)\,p(f \mid sz)\,p(sz)}{p(ly \mid f)\,p(f)}$$
- A [[concepts/mesint/felteteles-fuggetlenseg]] kihasználásával $p(ly \mid f,sz) = p(ly \mid sz)$ (a lyukas fog és a fájás egyaránt a szuvasodás következménye), így
$$p(sz \mid ly,f) = \frac{p(ly \mid sz)\,p(f \mid sz)\,p(sz)}{p(ly \mid f)\,p(f)}$$
- A nevezőt nem ismerjük, de a számláló $\neg sz$-re is kiszámolható, ezért **normalizálunk** ($\alpha$ a nevező reciproka):
$$p(sz \mid ly,f) = \alpha\, p(ly \mid sz)\,p(f \mid sz)\,p(sz)$$
$$\alpha = \frac{1}{p(ly \mid sz)p(f \mid sz)p(sz) + p(ly \mid \neg sz)p(f \mid \neg sz)p(\neg sz)}$$
- Számszerűen: $\alpha = 1/[0.7\cdot0.5\cdot0.65 + 0.01\cdot0.1\cdot0.35] = 4.38885$, és
$$p(sz \mid ly,f) = 4.38885 \cdot 0.2275 = 0.99846.$$

## Kapocs

- [[concepts/mesint/klasszikus-valoszinuseg-szamitas]] — feltételes valószínűség és normalizálás
- [[concepts/mesint/felteteles-fuggetlenseg]] — a példa kulcslépése
- [[concepts/mesint/bayes-halo]] — a módszer általánosítása tömör reprezentációval
- [[concepts/bigdata/naive-bayes]] — ugyanez a gondolat osztályozóként
