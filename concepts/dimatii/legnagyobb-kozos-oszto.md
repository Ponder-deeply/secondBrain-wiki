---
tags: [concept]
sources: [DimatIIEa01.pdf, Lehman-Leighton-Meyer-Mathematics-for-Computer-Science.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, dimat2gyak02mo.pdf, Dimat2mintaZH1.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-21
---

# Legnagyobb közös osztó

Két szám közös osztói közül az, amely az összes többi közös osztónak többszöröse — a „legnagyobb” itt az oszthatósági rendezésre utal, nem a szokásosra.

## Tartalom

**Definíció.** Az $a$ és $b$ **legnagyobb közös osztója** a $d$ szám — jelölés: $d = (a,b) = \operatorname{lnko}(a,b)$ —, ha

$$d \mid a, \quad d \mid b, \qquad \text{és} \qquad c \mid a,\ c \mid b \;\Rightarrow\; c \mid d.$$

**Figyelem!** Itt a „legnagyobb” nem a szokásos rendezésre utal: e definíció szerint $12$ és $9$ legnagyobb közös osztója $-3$ is. A legnagyobb közös osztó csak asszociáltság erejéig egyértelmű; a továbbiakban $(a,b)$ mindig a **pozitív** legnagyobb közös osztót jelöli.

Ha $(a,b) = 1$, azaz csak az egységek közös osztók, akkor $a$ és $b$ **relatív prímek**.

### További észrevételek

Több szám legnagyobb közös osztója hasonló módon definiálható: $(a_1, a_2, \dots, a_n)$.

**Állítás.** Bármely $a_1, \dots, a_n$ egész számokra létezik $(a_1, \dots, a_n)$, és
$$(a_1, a_2, \dots, a_n) = \big((\dots(a_1,a_2),\dots,a_{n-1}), a_n\big).$$

Az $n$ szám legnagyobb közös osztója tehát páronkénti lépésekben számolható.

**Állítás.** Bármely $a, b, c$ egészre $(ca, cb) = c\,(a,b)$.

A létezés nem magától értetődő; azt az [[concepts/dimatii/euklideszi-algoritmus]] konstruktívan igazolja. A [[concepts/dimatii/szamelmelet-alaptetele]] kanonikus alakjából pedig zárt képlet is adódik a kitevők minimumával.

### Tulajdonságok (Lehman–Leighton–Meyer 9.2.4)

Minden $a, b$ egészre, $k > 0$ esetén:

- $(ka, kb) = k\,(a,b)$;
- $d \mid a$ és $d \mid b \iff d \mid (a,b)$;
- ha $(a,b) = 1$ és $(a,c) = 1$, akkor $(a, bc) = 1$;
- ha $a \mid bc$ és $(a,b) = 1$, akkor $a \mid c$.

Mind a négy abból következik, hogy $(a,b)$ lineáris kombináció ($(a,b) = sa + tb$, lásd [[concepts/dimatii/bovitett-euklideszi-algoritmus]]). Fontos: ezeket **nem** szabad a prímfelbontás egyértelműségéből levezetni, mert az egyértelműség bizonyítása éppen ezekre épül (körkörös lenne). Triviális értékek: $(n,1) = 1$, $(n,n) = (n,0) = |n|$ ($n \neq 0$).

**Következmény.** Egy egész szám pontosan akkor lineáris kombinációja $a$-nak és $b$-nek, ha $(a,b)$ többszöröse. Ezért például $4$ nem állítható elő $12x + 18y$ alakban ($(12,18) = 6 \nmid 4$), de $3 = 21s + 26t$ megoldható, mert $(21,26) = 1$.

### Általános definíció és relatív prímek (előadásdiák)

*(Farkas Gábor előadásdiái.)* Egységelemes integritási tartományban legyen $a_1, \dots, a_n \in R$ és $L \subseteq R$ olyan, hogy minden $d \in L$-re $d \mid a_i$ ($i = 1,\dots,n$) és $d' \mid a_i\ (\forall i) \Rightarrow d' \mid d$. Ekkor $L$ elemei az $a_1, \dots, a_n$ legnagyobb közös osztói; jelölés $\operatorname{lnko}(a_1,\dots,a_n) = (a_1,\dots,a_n) = d$. A $d$ csak asszociáltság erejéig egyértelmű, ezért kijelölünk egyet.

Az $a_1, \dots, a_n$ **relatív prímek**, ha $d$ egység. Erősebb fogalom a **páronként relatív prímek**.

**Példa.** $(4,8,9) = 1$, de $(4,8) = 4$, $(4,9) = 1$, $(8,9) = 1$: a három szám relatív prím, páronként viszont nem.

**Következmény.** Bármely $a_1,\dots,a_n \in \mathbb{Z}$-nek létezik legnagyobb közös osztója és $\operatorname{lnko}(a_1,\dots,a_n) = \operatorname{lnko}(\operatorname{lnko}(a_1,a_2),a_3,\dots,a_n)$. *Bizonyítás:* $a_1, a_2$ közös osztói pontosan $d_{1,2}$ osztói, így $a_1,\dots,a_n$ közös osztói $d_{1,2}, a_3,\dots,a_n$ közös osztói. $\square$

### Feladattípusok és módszerek

Hatványkifejezések és Fibonacci-számok lnko-ját (pl. $(2^{13}-1, 2^8-1) = 1$, $(2^{15}-1, 2^9-1) = 7$, $(11^4+1, 11^6+1) = 2$, $(F_{n+3}, F_n) \in \{1,2\}$) a $(ca,cb) = c(a,b)$ és $(a,b) = (a-b,b)$ azonosságokkal számoljuk, lásd [[concepts/dimatii/lnko-hatvanykifejezesekre]]. ZH-tipp: $(a+1, b+1) = (a-b, b+1)$, de $(a-1, b+1) = (a+b, b+1)$.

## Kapocs

- [[concepts/dimatii/euklideszi-algoritmus]] — a legnagyobb közös osztó kiszámítása
- [[concepts/dimatii/bovitett-euklideszi-algoritmus]] — előállítása $xa + yb$ alakban
- [[concepts/dimatii/legkisebb-kozos-tobbszoros]] — a duális fogalom
- [[concepts/dimatii/szamelmelet-alaptetele]] — kanonikus alakból számolt képlet
- [[concepts/dimatii/oszthatosag]] — az alapreláció
- [[concepts/dimatii/linearis-kongruencia]] — a megoldhatóság feltétele $(a,m) \mid b$
- [[concepts/dimatii/lnko-hatvanykifejezesekre]] — kitevős kifejezések, Fibonacci-számok lnko-ja
