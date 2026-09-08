---
tags: [concept]
sources: [szelmJegyzet.pdf]
derivation: source
updated: 2026-08-05
---

# Turing-gép egy irányban végtelen szalaggal

Az *egyirányú Turing-gép* egy balra zárt, jobbra végtelen szalagon dolgozik; ekvivalens számítási erejű az eredeti (kétirányban végtelen szalagú) *többirányú* Turing-géppel.

## Definíció

A Turing-gép definícióját úgy módosítjuk, hogy a fej nem "eshet le" a szalag bal oldalán: ha a fej a bal szélső cellán áll, balra lépés nem megengedett. Az eredeti, kétirányban végtelen szalagú modellt ehhez képest *többirányú Turing-gépnek* nevezzük. Az egyirányú TG-nek is létezik többszalagos verziója.

## Ekvivalencia a többirányú TG-vel

**Tétel.** Minden többirányú Turing-géphez megadható vele ekvivalens egyirányú Turing-gép.

**Bizonyítás vázlata.** Legyen $M$ többirányú TG. Megkonstruálunk egy $M$-mel ekvivalens, kétszalagos $M'$ egyirányú TG-t (ebből a [[concepts/bvszam/turing-gep-szimulacio|turing-gep-szimulacio]] tételéhez hasonlóan kapható ekvivalens egyszalagos egyirányú gép).

- $M'$ mindkét szalagján egy új, $M$ szalagszimbólumai között nem szereplő $\$$ szimbólummal megjelöli a fej kezdőpozícióját.
- $M'$ szalagjai rendre az első, illetve a második szalag azon részét reprezentálják, amely $M$ kezdőkonfigurációjában a fejtől jobbra, illetve balra szerepel.
- Amikor $M$ a kezdőpozíciótól jobbra dolgozik, $M'$ az első szalagon másolja $M$ működését; amikor $M$ a kezdőpozíciótól balra lévő szalagrészen történik a lépés, $M'$ a második szalagon, *ellentétes irányú* lépéssel szimulálja (ezért $M'$ második szalagja az $M$ megfelelő szalagrészének tükörképe).
- $M'$ állapotai tárolják $M$ állapotait, plusz azt az információt, hogy $M'$-nek az első vagy a második szalagon kell-e dolgoznia.

A fordított irányú szimuláció (egyirányú → többirányú) triviális, hiszen az egyirányú gép a többirányú speciális esete.

## Kapocs

- [[concepts/bvszam/turing-gep]] — az eredeti (többirányú) modell
- [[concepts/bvszam/tobb-szalagos-turing-gep]] — a bizonyításban használt kétszalagos segédmodell
- [[concepts/bvszam/turing-gep-szimulacio]] — kétszalagos → egyszalagos redukció
