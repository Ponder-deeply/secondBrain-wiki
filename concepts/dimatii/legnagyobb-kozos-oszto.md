---
tags: [concept]
sources: [DimatIIEa01.pdf]
derivation: source
updated: 2026-09-08
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

## Kapocs

- [[concepts/dimatii/euklideszi-algoritmus]] — a legnagyobb közös osztó kiszámítása
- [[concepts/dimatii/bovitett-euklideszi-algoritmus]] — előállítása $xa + yb$ alakban
- [[concepts/dimatii/legkisebb-kozos-tobbszoros]] — a duális fogalom
- [[concepts/dimatii/szamelmelet-alaptetele]] — kanonikus alakból számolt képlet
- [[concepts/dimatii/oszthatosag]] — az alapreláció
- [[concepts/dimatii/linearis-kongruencia]] — a megoldhatóság feltétele $(a,m) \mid b$
