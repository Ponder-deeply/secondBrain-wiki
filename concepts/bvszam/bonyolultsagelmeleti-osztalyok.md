---
tags: [concept]
sources: [10.md, 11.md, 12.md, 10.md, szelmJegyzet.pdf]
derivation: source
updated: 2026-08-28
---

# Bonyolultságelméleti osztályok: P és NP

A bonyolultságelmélet az eldönthető problémák erőforrás-igényével (idő, tár) foglalkozik.

## Időbonyolultság

**Definíció:** ha $f : \mathbb{N} \to \mathbb{N}$ függvény, akkor
$$\text{TIME}(f(n)) = \{L \mid L \text{ eldönthető } O(f(n)) \text{ időigényű determinisztikus TG-pel}\}$$
$$\text{NTIME}(f(n)) = \{L \mid L \text{ eldönthető } O(f(n)) \text{ időigényű nemdeterminisztikus TG-pel}\}$$

## P és NP osztályok

$$\text{P} = \bigcup_{k \geq 1} \text{TIME}(n^k) \qquad \text{(polinom idejű DTG)}$$

$$\text{NP} = \bigcup_{k \geq 1} \text{NTIME}(n^k) \qquad \text{(polinom idejű NTG)}$$

**Észrevétel:** $\text{P} \subseteq \text{NP}$, mivel minden DTG tekinthető NTG-nek.

**Sejtés (erős sejtés):** $\text{P} \neq \text{NP}$ (nem bizonyított; a Clay Intézet Milleniumi problémáinak egyike). Tapasztalataink alapján valószínű, hogy van olyan NP-beli probléma, amely nem P-beli.

## NP alternatív definíciója: polinom időben ellenőrizhetőség

Az NP-beli problémák közös tulajdonsága: ha adott egy bemenet és egy lehetséges **tömör bizonyíték** (tanú) arra, hogy a bemenet pozitív, akkor a bizonyíték helyessége polinom időben leellenőrizhető. A bizonyíték „tömör": ha a bemenet mérete $n$, a bizonyíték mérete $O(p(n))$ valamely $p$ polinomra.

Egy $L$ nyelv **polinom időben ellenőrizhető**, ha van olyan $L_V \in \text{P}$ nyelv és $k \geq 1$, hogy
$$L = \{u \mid \exists v : (u,v) \in L_V \text{ és } l(v) = O(l(u)^k)\}.$$

Ebből adódik az alternatív definíció:
$$\text{NP} = \{L \mid L \text{ polinom időben ellenőrizhető}\}.$$

A nemdeterminisztikus polinom idejű TG úgy működik, hogy nemdeterminisztikusan „megsejti" a tömör megoldást, majd polinom időben ellenőrzi. Pl. SAT esetén a gép balról jobbra olvassa a formulát, és minden ítéletváltozóra felírja egy szalagjára a megsejtett igazságértékét, végül ellenőrzi a kielégítést.

## Polinom idejű visszavezetés

$L_1 \leq_p L_2$: létezik $f$ polinom idejű kiszámítható függvény, amelyre $w \in L_1 \iff f(w) \in L_2$. Általánosabban: $L_1 \leq_v L_2$, ha az $L_1$-et $L_2$-re visszavezető $f$ függvény a $v$ függvényosztályban van.

Egy $\textbf{C}$ problémaosztály **zárt** a $v$-beli visszavezetésekre, ha $L_1 \leq_v L_2$ és $L_2 \in \textbf{C}$ esetén $L_1 \in \textbf{C}$.

**Tétel:** P és NP zártak a polinom idejű visszavezetésekre nézve.

## NP-teljesség és NP-nehézség

$L$ **NP-teljes**, ha:
1. $L \in \text{NP}$, és
2. minden $L' \in \text{NP}$-re $L' \leq_p L$.

Ha csak a 2. pont teljesül, $L$ **NP-nehéz**.

**Tétel:** Ha $L$ NP-teljes és $L \in \text{P}$, akkor $\text{P} = \text{NP}$. (Bizonyítás: P zártsága miatt minden $L' \in \text{NP}$ P-beli lenne.)

**Tétel (NP-teljesség terjesztése):** ha $L_1$ NP-teljes, $L_2 \in \text{NP}$ és $L_1 \leq_p L_2$, akkor $L_2$ is NP-teljes. Ez a fő eszköz: egy ismert NP-teljes problémából való visszavezetés.

**Cook–Levin tétel:** SAT (Boole-kielégíthetőség) NP-teljes — ez az első NP-teljes probléma, közvetlenül a definícióból bizonyítva.

Részletek, konkrét NP-teljes problémák és visszavezetések: [[concepts/bvszam/np-teljesseg|np-teljesseg]].

## Az NP lehetséges szerkezete

Háromféle eset lehetséges:
- $\text{P} = \text{NP}$ — ekkor minden összeomlik.
- $\text{P} \subsetneq \text{NP}$, és nincs „köztes" — minden NP-beli probléma vagy P-beli, vagy NP-teljes.
- $\text{P} \subsetneq \text{NP}$ **NP-köztes** nyelvekkel: olyan $L \in \text{NP}$, hogy $L \notin \text{P}$, de $L$ nem NP-teljes.

**Tétel (Ladner):** ha $\text{P} \neq \text{NP}$, akkor létezik NP-köztes nyelv. Lehetséges NP-köztes jelölt a **Gráf izomorfizmus** ($\{\langle G_1, G_2\rangle \mid G_1, G_2 \text{ izomorf}\}$); ez NP-ben van, P-belisége és NP-teljessége is nyitott. Babai László eredménye szerint kvázipolinomiális ($2^{(\log n)^k}$) időben megoldható, ami a P-hez közelíti. A **Részgráf izomorfizmus** ellenben NP-teljes.

## Kapocs

- [[concepts/bvszam/nemdeterminisztikus-turing-gep]] — NTG, amelyen NTIME alapul
- [[concepts/bvszam/np-teljesseg]] — NP-teljesség, NP-nehézség, terjesztési tételek részletesen
- [[concepts/bvszam/3szinezes]] — 3SZÍNEZÉS NP-teljessége
- [[concepts/bvszam/grafelmeleti-np-teljes]] — Teljes részgráf, Független csúcshalmaz, Csúcslefedés
- [[concepts/bvszam/hamilton-np-teljes]] — Hamilton-úttal kapcsolatos NP-teljes problémák
- [[concepts/bvszam/np-koztes-es-conp]] — NP-köztes problémák, coNP osztály
- [[concepts/bvszam/cook-levin-bizonyitas]] — SAT NP-teljességének táblakódolásos bizonyítása
- [[concepts/bvszam/ksat-es-3sat]] — 3SAT NP-teljes; SAT $\leq_p$ 3SAT; $\leq_p$ tranzitivitása
- [[concepts/bvszam/2sat]] — 2SAT $\in$ P; implikációs gráf módszer
- [[concepts/bvszam/hornsat]] — HORNSAT $\in$ P; Horn-formulák
