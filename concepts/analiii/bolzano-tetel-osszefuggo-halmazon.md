---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 2.7. Lemma és 2.8. Tétel"]
derivation: source
updated: 2026-09-07
---

# Bolzano-tétel: folytonos kép összefüggő halmazon

Összefüggő halmaz folytonos képe összefüggő. Mivel $\mathbb{R}$-ben az összefüggő halmazok pontosan az intervallumok, ebből következik a klasszikus Bolzano-tétel: előjelet váltó folytonos függvénynek van gyöke.

## Tartalom

### Összefüggőség metrikus térben

Az $(X,\rho)$ metrikus tér $\emptyset \ne A \subset X$ részhalmaza **nem összefüggő**, ha $A = B \cup C$, ahol

$$B \ne \emptyset, \quad C \ne \emptyset, \quad B \cap C = \emptyset,$$

és alkalmas $D, E \subset X$ **nyílt** halmazokkal $B = A \cap D$, $C = A \cap E$. Ha ilyen felbontás nincs, $A$ **összefüggő**. Nyílt $A$ esetén feltehető, hogy maguk a $B, C$ halmazok nyíltak (ekkor $D, E$-re nincs szükség). Lásd [[concepts/analiii/osszefuggo-halmazok]].

### 2.7. Lemma — $\mathbb{R}$ összefüggő részhalmazai

**Lemma.** Az $X := \mathbb{R}$ szokásos metrikájával egy $A \subset \mathbb{R}$ halmaz akkor és csak akkor összefüggő, ha $A$ (valódi) intervallum.

*Bizonyítás.* **Minden intervallum összefüggő.** Ha $A = B \cup C$ egy fenti felbontás, $b \in B$, $c \in C$, mondjuk $b < c$, akkor $[b,c] \subset A$. Mivel $b \in D$ nyílt, alkalmas $b < u < c$ mellett $[b,u] \subset B$; hasonlóan alkalmas $b < v < c$ mellett $[v,c] \subset C$, és $u < v$. Legyen

$$\beta := \sup\{u \in (b,c) : [b,u] \subset B\},$$

ekkor $b < \beta \le v$ és $\beta \in A$. Ha $\beta \in B$, akkor ugyanezzel a gondolattal $\beta$-n túl is folytatható $B$, ami ellentmond a szuprémumnak; ha $\beta \in C$, akkor $B$-nek és $C$-nek közös pontja lenne. Így $\beta \notin B \cup C = A$ — ellentmondás.

**Minden összefüggő halmaz intervallum.** Legyen $\xi := \inf A$, $\eta := \sup A$; elég $(\xi,\eta) \subset A$. Ha $\xi = \eta$ volna, $A = \{\xi\}$ nem lenne (valódi) összefüggő halmaz. Ha valamilyen $\xi < \omega < \eta$ számra $\omega \notin A$, akkor

$$A = \bigl((-\infty,\omega)\cap A\bigr) \cup \bigl(A\cap(\omega,+\infty)\bigr)$$

két nemüres, diszjunkt, relatív nyílt darabra bontja $A$-t, tehát $A$ nem összefüggő. $\blacksquare$

### 2.8. Tétel (Bolzano)

**Tétel.** Ha az $f \in X \to Y$ függvény folytonos és $D_f$ összefüggő, akkor $R_f$ is összefüggő. Speciálisan ha $f \in X \to \mathbb{R}$, és valamilyen $a,b \in D_f$ esetén $f(a) < 0 < f(b)$, akkor alkalmas $c \in D_f$ helyen $f(c) = 0$.

*Bizonyítás.* Indirekt: ha $R_f = B \cup C$ egy nem összefüggő felbontás $B = R_f \cap D$, $C = R_f \cap E$ nyílt $D, E \subset Y$ halmazokkal, akkor

$$D_f = f^{-1}[B\cup C] = f^{-1}[D] \cup f^{-1}[E],$$

és a [[concepts/analiii/folytonossag-metrikus-terben|2.1. Tétel]] szerint $f^{-1}[D] = U \cap D_f$, $f^{-1}[E] = V \cap D_f$ alkalmas nyílt $U, V \subset X$ halmazokkal. Ezek nemüresek és diszjunktak, uniójuk $D_f$ — tehát $D_f$ nem összefüggő, ellentétben a feltétellel.

A gyökre vonatkozó rész: valós értékű $f$ esetén $R_f$ összefüggő, tehát a 2.7. Lemma szerint intervallum; ha tartalmaz negatív ($f(a)$) és pozitív ($f(b)$) számot is, akkor a nullát is tartalmazza. $\blacksquare$

### A séma

Ez a tétel a [[concepts/analiii/weierstrass-tetel-kompakt-halmazon|Weierstrass-tétel]] mintáját követi: egy topológiai tulajdonság (ott kompaktság, itt összefüggőség) öröklődik folytonos képre, és a valós értékű specializálás adja a klasszikus analízisbeli tételt (ott szélsőérték-tétel, itt gyöktétel). A [[concepts/analiii/brouwer-fixponttetel|Brouwer-fixponttétel]] egydimenziós esete is ebből következik.

## Kapocs

- [[concepts/analiii/osszefuggo-halmazok]] — az összefüggőség fogalma és a tartomány
- [[concepts/analiii/ivszeru-osszefuggoseg]] — az erősebb, görbével megfogalmazott változat
- [[concepts/analiii/folytonossag-metrikus-terben]] — a bizonyításban használt nyílt halmazos jellemzés
- [[concepts/analiii/weierstrass-tetel-kompakt-halmazon]] — a kompaktságra vonatkozó párja
- [[concepts/analiii/brouwer-fixponttetel]] — az $n=1$ eset következménye
