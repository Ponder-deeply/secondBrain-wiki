---
tags: [concept, dimatii/forraskodolas]
sources: [DimatIIEa08.pdf]
derivation: source
updated: 2026-09-08
---

# Kódfa

A betűnkénti kódolás fa alakú szemléltetése, amelyben a csúcsok a kódszavak prefixei, az élek pedig a kódoló ábécé betűi.

## Tartalom

### Konstrukció

Legyen $\varphi : A \to B^*$ betűnkénti kódolás, és tekintsük az $\mathrm{rng}(\varphi)$ kódszavak prefixeinek halmazát. Ez a halmaz részbenrendezett a „prefix" relációval; vegyük ennek a Hasse-diagramját. Így egy irányított fát kapunk, aminek a gyökere az üres szó, és minden szó a hosszának megfelelő szinten van.

A fa éleit megcímkézzük $B$ elemeivel: ha $\beta = \alpha b$ valamely $b \in B$-re, akkor az $\alpha$-ból $\beta$-ba vezető él címkéje legyen $b$.

A kódfa csúcsait is megcímkézhetjük: az $a \in A$ betű $\varphi(a)$ kódjának megfelelő csúcs címkéje legyen $a$; az a csúcs, amelynek címkéje nincs $\mathrm{rng}(\varphi)$-ben, legyen „üres".

### A konstrukció megfordítható

Tekintsünk egy véges, élcímkézett irányított fát, ahol az élcímkék halmaza $B$, egy csúcsból kiinduló élek mind különböző címkéjűek, továbbá a $A$ véges ábécének a csúcsokra való leképezését, amelynél minden levél előáll képként. Ekkor $a \in A$ betű kódja legyen az a szó, amelyet úgy kapunk, hogy a gyökértől az $a$-nak megfelelő csúcsig haladó irányított út mentén összeolvassuk az élcímkéket.

### Prefix kód a kódfán

Prefix kód esetén a kódszavaknak megfelelő csúcsok mind levelek: egy kódszó pontosan akkor prefixe egy másiknak, ha a neki megfelelő csúcs őse a másik csúcsának. A kódfa így közvetlenül leolvashatóvá teszi, hogy a kód prefix-e.

### Példa

A Huffman-kódos példa kódja a $\{0,1,2\}$ kódábécé felett:
$\varphi(a) = 00$, $\varphi(b) = 211$, $\varphi(c) = 02$, $\varphi(d) = 212$, $\varphi(e) = 2101$, $\varphi(f) = 1$, $\varphi(g) = 2100$, $\varphi(h) = 01$, $\varphi(i) = 22$, $\varphi(j) = 20$. A kódszavak prefixeinek halmaza:
$$\{\lambda,\ 1,\ 00,\ 0,\ 01,\ 02,\ 20,\ 2,\ 22,\ 211,\ 21,\ 212,\ 2100,\ 210,\ 2101\}.$$

## Kapocs

- [[concepts/dimatii/betunkenti-kodolas]] — a leképezés, amelyet a fa ábrázol
- [[concepts/dimatii/prefix-kod]] — a prefix tulajdonság a fán a „minden kódszó levél" feltétel
- [[concepts/dimatii/huffman-kod]] — a konstrukció során éppen egy ilyen fát építünk fel alulról
- [[concepts/dimatii/shannon-kod]] — a Shannon-kód kódfája ritkábban telített, mint a Huffman-kódé
