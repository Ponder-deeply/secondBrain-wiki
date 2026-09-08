---
tags: [concept]
sources: ["5.-környezetfüggetlen-gramm,-cnf,-cyk-pumpálási-lemma.md"]
derivation: source
updated: 2026-04-07
---

# Bar-Hillel lemma (Pumpálási lemma KF nyelvekre)

A Bar-Hillel lemma (vagy nagy pumpálási lemma) szükséges feltételt ad KF nyelvekre: minden elég hosszú szó „pumpálható" úgy, hogy a kapott szavak is a nyelvbe esnek; ezzel **belátható**, hogy bizonyos nyelvek nem KF-ek.

## Tartalom

### Tétel (Bar-Hillel lemma)

> Minden $L$ KF nyelvhez léteznek $p, q \in \mathbb{N}$, hogy minden $|w| > p$ szóhoz ($w \in L$) létezik $w = uxvyz$ felbontás, ahol:
> - $|xvy| \leq q$
> - $xy \neq \varepsilon$
> - $ux^i vy^i z \in L$ minden $i \geq 0$-ra

$p$ és $q$ csak a **nyelvtől** függ (nem a pumpált szótól). A kis pumpálási lemma a reguláris nyelvekre szól (ott egykomponensű pumpálás elég).

### Bizonyítás vázlata

Legyen $G$ Chomsky normálformájú grammatika $n$ nemterminálissal. Legyen $p = 2^{n-1}$, $q = 2^n$.

Ha $|w| > p$, a levezetési fa leghosszabb útján $> n$ csúcs van. A **skatulya-elvnél** fogva valamelyik $A$ nemterminális legalább kétszer ismétlődik. Az utolsó ismétlő pár alapján:
$$S \Rightarrow^* uAz, \quad A \Rightarrow^* xAy, \quad A \Rightarrow^* v$$
ahol $xy \neq \varepsilon$ (CNF biztosítja). Ekkor $ux^i vy^i z \in L$ minden $i \geq 0$-ra.

### Alkalmazás: $\{a^n b^n c^n\} \notin \mathcal{L}_2$

Legyenek $p, q$ a lemma konstansai. Legyen $w = a^k b^k c^k$ ($k > \max\{p,q\}$). Mivel $|xvy| \leq q < k$, az $xy$ legfeljebb 2 betűfajtát tartalmaz. A $ux^0 vy^0 z$ szóban valamelyik betűfajtából kevesebb lesz $k$-nál, míg a többi $k$ marad — ez nem lehet $\{a^n b^n c^n\}$-beli. Ellentmondás.

### Következmény: $\mathcal{L}_2$ zártsági hiányai

$\mathcal{L}_2$ **nem zárt** a következő műveletekre: metszet, komplementer, különbség, szimmetrikus differencia.

Ellenpélda: $\{a^n b^n c^n\} = \{a^k b^n c^n\} \cap \{a^n b^n c^k\}$, ahol mindkét tényező KF, de a metszet nem az.

## Kapocs

- [[concepts/bvszam/kornyezetfuggetlen-grammatika]] — KF grammatikák és algoritmikus problémák
- [[concepts/bvszam/chomsky-normalforma]] — a CNF szükséges a bizonyításhoz
- [[concepts/bvszam/levezetes-fa]] — a skatulya-elv a fán alkalmazandó
- [[concepts/bvszam/zartsagi-tulajdonsagok]] — $\mathcal{L}_2$ nem zárt bizonyos műveletekre
- [[concepts/bvszam/kornyezetfuggo-nyelvek]] — az $\mathcal{L}_1$ tartalmazza $\{a^n b^n c^n\}$-t
