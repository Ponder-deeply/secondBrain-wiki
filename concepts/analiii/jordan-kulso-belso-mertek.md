---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Jordan-féle külső és belső mérték

A $\mathbb{R}^p$-beli korlátos halmazok térfogatát tengelypárhuzamos téglákkal közelítjük kívülről (fedéssel) és belülről (kitöltéssel); ha a két közelítés közös értékhez tart, a halmaz Jordan-mérhető.

## Tartalom

### Mit várunk el egy térfogatfogalomtól?

A cél olyan $t$ halmazfüggvény, amely $\mathbb{R}^p$ minél több részhalmazán értelmes (poliéderek, gömb, henger stb.), és

- **pozitív**: $t(A) \geq 0$;
- **additív**: diszjunkt halmazokra $t(A \cup B) = t(A) + t(B)$;
- **egybevágóság-invariáns**: egybevágó halmazok térfogata egyenlő;
- **normált**: az egységkocka térfogata $1$.

### A tégla térfogata

A zárt $R_1 = [a_1,b_1] \times \dots \times [a_p,b_p]$ és a nyílt $R_2 = (a_1,b_1) \times \dots \times (a_p,b_p)$ tengelypárhuzamos téglák térfogata definíció szerint

$$\tau(R_1) = \tau(R_2) = \prod_{i=1}^{p} (b_i - a_i).$$

Ez az egyetlen kiindulási adat: minden további mértéket erre vezetünk vissza.

### Külső és belső Jordan-mérték

Legyen $H \subset \mathbb{R}^p$ korlátos.

**Külső Jordan-mérték** (külső Jordan-térfogat): véges téglafedések össztérfogatának infimuma,

$$k(H) = \inf\left\{ \sum_{i=1}^{n} \tau(R_i) \;:\; R_1,\dots,R_n \text{ tengelypárhuzamos téglák}, \; H \subset R_1 \cup \dots \cup R_n \right\}.$$

**Belső Jordan-mérték** (belső Jordan-térfogat): a halmazba írt, egymásba nem nyúló téglarendszerek össztérfogatának szuprémuma,

$$b(H) = \sup\left\{ \sum_{i=1}^{n} \tau(R_i) \;:\; R_1,\dots,R_n \subset H \text{ egymásba nem nyúló téglák} \right\},$$

ahol az *egymásba nem nyúló* azt jelenti, hogy $\operatorname{int} R_1, \dots, \operatorname{int} R_n$ diszjunktak.

### Mérhetőség

A $H$ halmaz **Jordan-mérhető**, ha $k(H) = b(H)$; ekkor a közös érték a $H$ **Jordan-mértéke** (Jordan-térfogata):

$$t(H) = k(H) = b(H).$$

A definíció ebben az alakban még azt sem garantálja, hogy $b(H) \leq k(H)$ — ezt csak a kockázásos átfogalmazás bizonyítja, lásd [[concepts/analiii/jordan-mertek-kockazassal]]. Onnan következik az is, hogy minden tégla mérhető, és $t(R) = \tau(R)$; ettől kezdve a $\tau$ jelölésre nincs többé szükség.

## Kapocs

- [[concepts/analiii/jordan-mertek-kockazassal]] — a külső és belső mérték ekvivalens, rácskockákra épülő definíciója, amely a $b(H) \leq k(H)$ egyenlőtlenséget is szolgáltatja
- [[concepts/analiii/kulso-belso-mertek-tulajdonsagai]] — szubadditivitás, szuperadditivitás, monotonitás, és hogy egyik mérték sem additív
- [[concepts/analiii/jordan-nullmerteku-halmazok]] — a $k(\partial A) = 0$ mérhetőségi kritérium
- [[concepts/analii/hatarozott-integral-ertelmezese]] — az egyváltozós Riemann-integrál ugyanezt a „belülről közelítem / kívülről közelítem" sémát intervallumfelosztásokon és alsó/felső összegeken keresztül valósítja meg; a Jordan-mérték ennek dimenziófüggetlen, halmazokra vonatkozó általánosítása
- [[concepts/analii/sikido-terulete]] — az egyváltozós integrállal számolt síkidomterület a $p = 2$ eset speciális, grafikon alatti alakja
