---
tags: [concept]
sources: [szelmJegyzet.pdf]
derivation: source
updated: 2026-08-05
---

# Problémák mint formális nyelvek

A kiszámítási problémák — különösen az eldöntési problémák — formális nyelvekként reprezentálhatók: a probléma azonosítható azzal a nyelvvel, amely a pozitív bemeneteinek kódjait tartalmazza.

## Kiszámítási probléma

*Kiszámítási problémának* nevezünk egy, a matematika nyelvén megfogalmazott kérdést, amire egy algoritmussal szeretnénk megadni a választ. Egy probléma konkrét bemenetét a probléma egy *példányának* nevezzük (pl. a körpakolás probléma egy példánya: adott alakzat és körök paraméterei).

- $P_1$ a $P_2$ *speciális esete*, ha $P_1$ minden példánya $P_2$-nek is példánya.
- Egy $P$ probléma reprezentálható egy $f_P : A \to B$ függvénnyel, ahol $A$ a (kódolt) bemeneteket, $B$ a (kódolt) válaszokat tartalmazza.
- $f : A \to B$ *kiszámítható*, ha minden $x \in A$-ra $f(x)$ kiszámítható valamilyen algoritmusmodellel. A $P$ probléma *megoldható*, ha $f_P$ kiszámítható.

## Eldöntési problémák

Speciális kiszámítási problémák az *eldöntési problémák*: a kapcsolódó kérdés egy eldöntendő kérdés, a válasz `igen` vagy `nem`. Ekkor $f_P$ értékkészlete kételemű ($\{\text{igen}, \text{nem}\}$, $\{1,0\}$ stb.). A megoldható eldöntési problémákat *eldönthető problémáknak* nevezzük.

- Egy `igen` válaszú bemenet *igen példány* (*pozitív bemenet*), egy `nem` válaszú *nem példány* (*negatív bemenet*).
- Példa: a **Sat** probléma — adott egy $\varphi$ ítéletkalkulusbeli konjunktív normálforma; kielégíthető-e $\varphi$? A Sat eldönthető (minden értékelést kipróbáló algoritmussal), de ez exponenciális időigényű, és nem ismert lényegesen jobb.

## Probléma mint formális nyelv

Egy eldöntési probléma tekinthető formális nyelvként: a példányokat kódoljuk egy ábécé feletti szavakkal, majd a problémát azonosítjuk azzal a nyelvvel, amely a pozitív bemenetek kódjait tartalmazza. A $D$ objektum egy szóval való kódolását $\langle D \rangle$ jelöli.

Az eldöntési problémákra szorítkozás nem szűkíti az általánosságot: tetszőleges $P$ kiszámítási problémához ($f_P : A \to B$) megadható egy $P'$ eldöntési probléma — pontosan azoknak az $(a, b)$ pároknak az elfogadása, ahol $b = f_P(a)$ —, és $P$ pontosan akkor kiszámítható, ha $P'$ eldönthető.

## Hány probléma van?

Mivel az eldöntési problémák megfeleltethetők a formális nyelveknek, annyi eldöntési probléma van, mint amennyi formális nyelv. Egy $\{a\}^*$ feletti formális nyelvek száma $|\mathcal{P}(\mathbb{N})|$, azaz megszámlálhatatlanul végtelen. Az algoritmusok halmaza ezzel szemben megszámlálhatóan végtelen (minden algoritmus végesen reprezentálható, kódolható egy rögzített ábécé feletti szóval). Tehát nagyságrendileg több probléma van, mint algoritmus — biztosan létezik **eldönthetetlen probléma**.

## Kapocs

- [[concepts/bvszam/formalis-nyelvek]] — szavak, nyelvek, ábécé
- [[concepts/bvszam/kiszamithato-szofuggveny]] — kiszámítható függvény fogalma
- [[concepts/bvszam/ksat-es-3sat]] — a Sat probléma részletesen
- [[concepts/bvszam/eldonthetetlen-problemak]] — a számossági érvtől a konkrét eldönthetetlen nyelvekig
- [[concepts/bvszam/kiszamithatosagelmelet-tortenete]] — kontextus
