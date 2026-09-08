---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Sűrű, szeparábilis, sehol sem sűrű

A sűrűség azt méri, mennyire „hézagtalanul" ül egy halmaz a térben; a sehol sem sűrűség ennek az ellentéte, és éppen ez a topológiai értelemben vett „kicsi halmaz" fogalma, amelyre a Baire-kategóriatétel épül.

## Tartalom

### Sűrű halmaz

**Definíció.** Legyen $(M,d)$ metrikus tér és $G \subset M$ nyílt. Az $S \subset G$ halmaz **sűrű $G$-ben**, ha

$$\forall a \in G\ \ \forall r > 0:\quad S \cap B(a,r) \neq \emptyset.$$

**Példák.**

- $\mathbb{Q}^p$ és $\mathbb{R}^p \setminus \mathbb{Q}^p$ is sűrű $\mathbb{R}^p$-ben.
- $C[a,b]$-ben sűrű a szakaszonként lineáris függvények altere.
- $C[a,b]$-ben sűrű a polinomok altere (Weierstrass I. approximációs tétele).

### Szeparábilis tér

**Definíció.** Egy $(M,d)$ metrikus tér **szeparábilis**, ha tartalmaz megszámlálható sűrű halmazt.

**Példák.** $\mathbb{R}^p$ szeparábilis, mert $\mathbb{Q}^p$ megszámlálható sűrű részhalmaza. $C[a,b]$ is szeparábilis: sűrű benne például a racionális pontokat összekötő szakaszokból álló, szakaszonként lineáris függvények halmaza, vagy a racionális együtthatós polinomok halmaza.

### Sehol sem sűrű halmaz

**Definíció.** Az $S \subset M$ halmaz **sehol sem sűrű** (s.s.s.), ha

$$\forall a \in M\ \forall r>0\ \exists b \in B(a,r)\ \exists s>0:\quad B(b,s)\cap S = \emptyset,$$

ekvivalensen $\operatorname{int}\operatorname{cl} S = \emptyset$: a lezártjának nincs belső pontja.

**Példák.** $\mathbb{R}^p$-ben sehol sem sűrű a $\mathbb{Z}^p$ rács; $\mathbb{R}$-ben sehol sem sűrű a Cantor-halmaz.

Fontos, hogy az „$S$ nem sűrű" és az „$S$ sehol sem sűrű" nem ugyanaz: az utóbbi minden gömbre megköveteli, hogy legyen benne $S$-től teljesen elszigetelt kisebb gömb.

## Kapocs

- [[concepts/analiii/baire-kategoriatetel]] — a sehol sem sűrű halmazok fő alkalmazása
- [[concepts/analiii/halmaz-pontjai-metrikus-terben]] — a lezárt és a belső, amivel a s.s.s. megfogalmazható
- [[concepts/analiii/heine-borel-tetel]] — a $\mathbb{Q}^p$ sűrűségét használó racionális gömbök
- [[concepts/analiii/nyilt-es-zart-halmazok]] — a definíciók terepe
