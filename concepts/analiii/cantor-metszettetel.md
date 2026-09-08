---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Bolzano–Weierstrass-tétel és Cantor-metszettétel

Egymásba skatulyázott, korlátos, zárt, nemüres halmazok metszete $\mathbb{R}^p$-ben nemüres. A bizonyítás motorja a Bolzano–Weierstrass-tétel; a metszettétel innen közvetlenül a Heine–Borel-tétel bizonyításába vezet.

## Tartalom

### Korlátos halmaz és korlátos sorozat

**Definíció.** Legyen $(M,d)$ metrikus tér, $K \subset M$. A $K$ halmaz **korlátos**, ha van olyan $B(a,r)$ gömb, amely tartalmazza $K$-t.

Az $(a_n)$ pontsorozat **korlátos**, ha (ezek ekvivalensek): az $\{a_1,a_2,\dots\}$ halmaz korlátos; ($\mathbb{R}^p$-ben) az $|a_n|$ számsorozat korlátos, azaz $\exists K \in \mathbb{R}\ \forall n: |a_n| \leq K$; ($\mathbb{R}^p$-ben) minden $1 \leq i \leq p$-re az $(a_{n,i})$ számsorozat korlátos.

### Bolzano–Weierstrass-tétel

**Tétel.** $\mathbb{R}^p$-ben minden korlátos sorozatból kiválasztható konvergens részsorozat.

*Bizonyítás.* Az egydimenziós Bolzano–Weierstrass-tételt alkalmazzuk $p$-szer egymás után: először az első koordináták szerint választunk konvergens részsorozatot, ebből a második koordináták szerint, és így tovább. $\blacksquare$

### Cantor-metszettétel

**Tétel.** Ha $K_1 \supset K_2 \supset \dots$ korlátos, zárt, nemüres halmazok $\mathbb{R}^p$-ben, akkor $\bigcap K_n \neq \emptyset$.

A Cantor-axióma (egymásba skatulyázott zárt intervallumokra) ennek speciális esete.

*Bizonyítás.* Válasszunk minden $K_n$-ből egy $a_n$ pontot. Minden $n \geq m$ esetén $a_n \in K_n \subset K_m$. A kiválasztott sorozat korlátos, mert minden eleme $K_1$-ben van, így Bolzano–Weierstrass szerint van konvergens $(a_{n_i})$ részsorozata; legyen $c = \lim a_{n_i}$. Bármely $m$-re elég nagy $i$ esetén $n_i \geq m$, tehát $a_{n_i} \in K_m$; mivel $K_m$ zárt, $c \in K_m$. A $c$ tehát közös pontja az összes $K_m$-nek. $\blacksquare$

### Mindkét feltétel kell

- Az $A_n = \{\mathbf{x} : x_1 \geq n\}$ zárt félterek zártak és nemüresek, $A_1 \supset A_2 \supset \dots$, de a metszetük üres — hiányzik a korlátosság.
- A $B_n = B(1/n,\, 1/n)$ nyílt gömbök korlátosak és nemüresek, $B_1 \supset B_2 \supset \dots$, de a metszetük üres — hiányzik a zártság.

## Kapocs

- [[concepts/analiii/heine-borel-tetel]] — a metszettétel a Borel-tétel bizonyításának kulcslépése
- [[concepts/analiii/kompakt-halmazok]] — a korlátosság és zártság párosa
- [[concepts/analiii/nyilt-es-zart-halmazok]] — a zártság sorozatos jellemzése, amit a bizonyítás használ
- [[concepts/analiii/ekvivalens-normak]] — a normaekvivalencia bizonyítása szintén Bolzano–Weierstrassra épül
