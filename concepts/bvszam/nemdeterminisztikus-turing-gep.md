---
tags: [concept]
sources: [07.md, 08.md, szelmJegyzet.pdf]
derivation: source
updated: 2026-08-05
---

# Nemdeterminisztikus Turing-gép (NTG)

Az NTG a determinisztikus TG általánosítása: az átmenetfüggvény értéke nem egy konkrét állapot–szalagszimbólum–irány hármas, hanem ezek egy véges halmaza. A nemdeterminizmus nem növeli a Turing-gép számítási erejét.

## Definíció

$$M = (Q, \Sigma, \Gamma, \delta, q_0, q_i, q_n)$$

ahol $Q, \Sigma, \Gamma, q_0, q_i, q_n$ ugyanazok mint a determinisztikus TG-nél, és
$$\delta : (Q \setminus \{q_i, q_n\}) \times \Gamma \to \mathcal{P}(Q \times \Gamma \times \{L, R\})$$

A konfiguráció a determinisztikus esettel megegyezően definiálható. A konfiguráció-átmenet a determinisztikus eset kiterjesztése: $uqav \vdash urbv$, ha $(r,b,S) \in \delta(q,a)$ (és hasonlóan $R$, $L$ esetén).

## Számítási fa

Egy NTG $u$ szón vett számítási sorozatai egy fával reprezentálhatók — ez $M$ *nemdeterminisztikus számítási fája az $u$-n*:
- a fa gyökere $M$ kezdőkonfigurációja,
- a fa szögpontjai $M$ konfigurációi,
- minden levél $M$ egy számítási sorozatának felel meg $u$-n; a gyökértől a levélig vezető úton az adott számítási sorozatban előforduló konfigurációk szerepelnek.

**Elfogadás:** $M$ elfogadja $u$-t, ha a fa valamelyik levele elfogadó konfiguráció — azaz létezik legalább egy elfogadó állapotba vezető számítási sorozat.

**Eldöntés:** $M$ *eldönti* az $L \subseteq \Sigma^*$ nyelvet, ha felismeri, és minden $u \in \Sigma^*$ szóra $M$ minden számítási sorozata véges, és elfogadó vagy elutasító konfigurációba vezet. A definíció a többszalagos esetre is kiterjeszthető.

## Időigény

Az $M$ NTG *időigénye $f(n)$* ($f : \mathbb{N} \to \mathbb{N}$), ha minden $n$ hosszú $u$ bemeneten nincsenek $M$-nek $f(n)$-nél hosszabb számítási sorozatai — azaz $M$ számítási fája az $u$-n legfeljebb $f(n)$ magas.

## NTG és DTG ekvivalenciája

**Tétel.** Minden $M$ nemdeterminisztikus TG-hez megadható vele ekvivalens $M'$ determinisztikus TG.

**Bizonyítás (3-szalagos DTG, szélességi keresés a számítási fában):**
1. Szalag 1: az $u$ bemenő szó (érintetlen).
2. Szalag 2: a szimulációs szalag — $M$ egy konkrét számítási sorozatának lépésenkénti eredménye.
3. Szalag 3: a szelektoros szalag — egy $\{1, \ldots, d\}$ feletti szó, ahol $d$ a $\delta$ által megadott halmazok legnagyobbikának elemszáma; ez kódolja, hogy a kezdőkonfigurációból mely választásokkal jutunk a fa adott szögpontjához.

$M'$ a 3. szalagon lévő szót hosszlexikografikus sorrendben lépteti, így bejárja $M$ számítási fáját szélességében; ezért minden véges elfogadó ágat megtalál. $M'$ akkor és csak akkor lép elfogadó konfigurációba egy szón, ha $M$-nek van azon a szón elfogadó számítási sorozata.

**Időkorlát:** a konstrukció exponenciális időigény-romlást eredményez — $M'$ időigénye az $M$ számítási fában lévő konfigurációk számával arányos, ami $M$ számítási fa magasságában exponenciális. Nem ismert hatékonyabb szimuláció, de azt sem tudjuk bizonyítani, hogy nincs ilyen (vö. **P** vs **NP**).

## Következmény az RE osztályra

$L \in \text{RE} \iff$ létezik $L$-t felismerő NTG.

(Az NTG és DTG ugyanazokat a nyelveket ismerik fel, csak időbonyolultságban különbözhetnek.)

## Kapocs

- [[concepts/bvszam/turing-gep]] — DTG definíciója
- [[concepts/bvszam/r-re-nyelvek]] — RE és R, $L_u$
- [[concepts/bvszam/bonyolultsagelmeleti-osztalyok]] — NP mint NTG polinom időben
