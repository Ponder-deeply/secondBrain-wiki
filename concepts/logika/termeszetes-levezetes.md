---
tags: [concept, logika/gentzen-stilusu-kalkulusok]
sources: ["Természetes levezetés.pdf"]
derivation: source
updated: 2026-09-08
---

# Természetes levezetés (természetes technika)

A természetes technika egy [[concepts/logika/gentzen-stilusu-kalkulusok|Gentzen stílusú kalkulus]]: strukturális és logikai szabályok segítségével egy $\Gamma \vdash_0 A$ szekvencia megalapozhatóságát egyszerűbb szerkezetű szekvenciák megalapozhatóságára vezeti vissza, amíg egy megállási feltételig el nem jut.

## Tartalom

### Alapgondolat

A szabályok azt mutatják meg, hogy a vonal alatt megjelölt (összetettebb) szekvencia levezethetősége akkor áll fenn, ha a vonal felett megjelölt (egyszerűbb) szekvenciák levezethetősége fennáll. Mivel minden szabály egyben helyes következtetésforma, ez biztosítja a **helyességet**: ha a megállási feltételt — $\Gamma, A \vdash_0 A$, az azonosság törvénye — elértük egy szekvenciára a szabályok alkalmazásával, akkor a szekvencia jobb oldalán álló formula valóban levezethető a feltételhalmazból.

Egy szabály tehát általában kisebb logikai összetettségű szekvencia megalapozottságának fennállása esetén garantálja az összetettebb szekvencia megalapozhatóságát — innen a "visszakövetkeztetés" jelleg (lásd [[concepts/logika/gentzen-stilusu-kalkulusok]]).

### Strukturális szabályok

- **Azonosság törvénye:** $\Gamma, A \vdash_0 A$ — ez a megállási feltétel.
- **Bővítés:** $\dfrac{\Gamma \vdash_0 A}{\Gamma, B \vdash_0 A}$
- **Szűkítés:** $\dfrac{\Gamma, B, B, \Delta \vdash_0 A}{\Gamma, B, \Delta \vdash_0 A}$
- **Felcserélés:** $\dfrac{\Gamma, B, C, \Delta \vdash_0 A}{\Gamma, C, B, \Delta \vdash_0 A}$
- **Vágás:** $\dfrac{\Gamma \vdash_0 A \quad \Delta, A \vdash_0 B}{\Gamma, \Delta \vdash_0 B}$

**A vágás szabályának bizonyítása:** a [[concepts/logika/dedukcios-tetel]] szerint ha $\Delta, A \vdash_0 B$, akkor $\Delta \vdash_0 A \supset B$. A $\Gamma \vdash_0 A$-t és a $\Delta \vdash_0 A \supset B$-t igazoló két levezetés konkatenációja (lásd [[concepts/logika/dedukcios-tetel]]) után egy modus ponens megalapozza $\Gamma, \Delta \vdash_0 B$-t.

### Logikai szabályok (ítéletlogika)

Minden logikai összekötőhöz egy **bevezető szabály** (a jobb oldalon jelenik meg az összekötő) és egy **alkalmazó szabály** (a bal oldali feltételek közt jelenik meg) tartozik:

- $(\supset b)$: $\dfrac{\Gamma, A \vdash_0 B}{\Gamma \vdash_0 A \supset B}$ — épp a dedukciós tétel.
- $(\supset a)$: $\dfrac{\Gamma \vdash_0 A \quad \Gamma \vdash_0 A \supset B}{\Gamma \vdash_0 B}$ — a két levezetés konkatenációja után modus ponens.
- $(\wedge a)$: $\dfrac{\Gamma, A, B \vdash_0 C}{\Gamma, A \wedge B \vdash_0 C}$
- $(\vee b)$: a diszjunkció bevezetése — ha $\Gamma$-ból levezethető $A$, akkor az $A \supset A \vee B$ axiómát beírva és modus ponenst alkalmazva megkapjuk $\Gamma$-ból $A \vee B$ egy levezetését.
- $(\vee a)$: $\dfrac{\Gamma, A \vdash_0 C \quad \Gamma, B \vdash_0 C}{\Gamma, A \vee B \vdash_0 C}$ — a dedukciós tétel miatt $\Gamma \vdash_0 A \supset C$ és $\Gamma \vdash_0 B \supset C$ is megalapozható; ezek konkatenációja után az $(A \supset C) \supset ((B \supset C) \supset (A \vee B \supset C))$ axióma és kétszeri modus ponens adja $\Gamma \vdash_0 A \vee B \supset C$-t, majd az $A \vee B$ hipotézis beírásával és egy újabb modus ponensszel $\Gamma, A \vee B \vdash_0 C$-t.
- $(\neg a)$: $\dfrac{\Gamma \vdash_0 \neg\neg A}{\Gamma \vdash_0 A}$

> **A forrásról.** A diasor logikai szabálytáblázatának bal oszlopa — a *bevezető szabályok* — a PDF szövegkinyerése során elveszett, így a $(\wedge b)$ és a $(\neg b)$ szabály pontos alakja ebből a forrásból nem olvasható ki; a lenti Példa I. a $(\neg b)$-t mégis használja. A fenti szabályok a táblázat megmaradt oszlopából és a hozzájuk tartozó, szövegesen kiírt bizonyításokból származnak. A hiányzó két szabály alakja a kötelező tankönyvből pótolandó.

Az összes szabály bizonyítása visszavezethető az [[concepts/logika/axiomasemak-iteletkalkulus]]ban rögzített axiómasémákra, a dedukciós tételre és a modus ponensre — a természetes technika tehát nem ad új levezethetőségi fogalmat, csak kényelmesebb, "felülről lefelé" (előrekövetkeztetéssel) vagy "alulról felfelé" (visszakövetkeztetéssel) alkalmazható lépéskészletet ugyanarra a $\vdash_0$-ra.

### Elsőrendű kvantoros szabályok

- $(\forall b)$: $\dfrac{\Gamma \vdash A}{\Gamma \vdash \forall x A}$, ha $x \notin Par(\Gamma)$.
- $(\forall a)$: $\dfrac{\Gamma \vdash \forall x A}{\Gamma \vdash [A(x \| t)]}$
- $(\exists b)$: $\dfrac{\Gamma \vdash [A(x \| t)]}{\Gamma \vdash \exists x A}$
- $(\exists a)$: $\dfrac{\Gamma, A \vdash B}{\Gamma, \exists x A \vdash B}$, ha $x \notin Par(\Gamma, B)$.

A $\forall$-bevezetés és az $\exists$-alkalmazás szabályánál a **paraméterfeltétel** ($x \notin Par(\dots)$) elengedhetetlen: enélkül a szabály olyan általánosítást engedne meg, amely a $\Gamma$-ban (illetve $B$-ben) még szabadon szereplő $x$-et illetéktelenül lezárná.

**Az egzisztenciális kvantort bevezető szabály bizonyítása:** ha adott a $\Gamma \vdash [A(x \| t)]$ szekvenciát megalapozó levezetés, írjuk be az $[A(x \| t)] \supset \exists x A$ axiómát, majd alkalmazzuk a modus ponenst — így $\Gamma$-ból levezettük $\exists x A$-t.

**Az egzisztenciális kvantort alkalmazó szabály bizonyítása:** ha adott a $\Gamma, A \vdash B$ szekvenciát megalapozó levezetés, a dedukciós tétel miatt megkonstruálható $\Gamma \vdash A \supset B$ is; ebből az általánosítás szabálya miatt ($x \notin Par(\Gamma)$) $\Gamma \vdash \forall x (A \supset B)$ adódik. Beírva a $\forall x (A \supset B) \supset (\exists x A \supset B)$ axiómát (itt lényeges, hogy $x \notin Par(B)$) és alkalmazva a modus ponenst, megkapjuk $\exists x A \supset B$ egy levezetését $\Gamma$-ból; a dedukciós tétel újbóli alkalmazásával adódik $\Gamma, \exists x A \vdash B$.

Ezek a szabályok a [[concepts/logika/predikatumkalkulus-axiomasemak]]ban rögzített elsőrendű axiómasémákra épülnek.

### Példa I. — $\vdash_0 A \supset (\neg A \supset B)$

"Felülről lefelé" (előrekövetkeztetéssel):

1. $A, \neg A, \neg B \vdash_0 A$ — az azonosság törvénye
2. $A, \neg A, \neg B \vdash_0 \neg A$ — az azonosság törvénye
3. $A, \neg A \vdash_0 \neg\neg B$ — 1-ből és 2-ből, $(\neg b)$
4. $A, \neg A \vdash_0 B$ — 3-ból, $(\neg a)$
5. $A \vdash_0 \neg A \supset B$ — $(\supset b)$
6. $\vdash_0 A \supset (\neg A \supset B)$ — $(\supset b)$

Ugyanez "alulról felfelé" (visszakövetkeztetéssel): a bizonyítandó formulára kétszer alkalmazva $(\supset b)$-t az $A, \neg A \vdash_0 B$ szekvenciára jutunk. A negáció alkalmazásának szabálya ezt visszavezeti $A, \neg A \vdash_0 \neg\neg B$-re, majd a negáció bevezetésének szabálya arra a kérdésre, hogy az $A, \neg A, \neg B$ hipotézisekből levezethető-e egyszerre egy formula és annak negáltja — ami az azonosság törvénye szerint $A$-ra és $\neg A$-ra fennáll.

### Példa II. — elsőrendű levezetés

Egy egzisztenciálisan kvantált hipotézisből ($A \vdash \neg\forall x \neg A$, ahol $x \notin Par(\neg\forall x \neg A)$) az egzisztenciális kvantort alkalmazó szabály szerint elég igazolni ugyanezt a szekvenciát; a jobb oldali negáció miatt a negáció bevezetése alkalmazandó, ami az $A, \forall x \neg A \vdash \neg A$ és $A, \forall x \neg A \vdash A$ szekvenciák megalapozására vezet vissza. Az első az univerzális kvantort alkalmazó szabállyal az $A, \forall x \neg A \vdash \forall x \neg A$ szekvenciára — az azonosság törvényére — vezethető vissza; a második önmagában az azonosság törvénye.

## Kapocs

- [[concepts/logika/gentzen-stilusu-kalkulusok]] — a kalkuluscsalád, amelynek a természetes technika egy tagja
- [[concepts/logika/bizonyitaselmeleti-levezetes]] — a $\vdash_0$ szintaktikus következményfogalom, amelyre a strukturális szabályok épülnek
- [[concepts/logika/dedukcios-tetel]] — a dedukciós tétel, amelyet több logikai szabály bizonyítása közvetlenül felhasznál
- [[concepts/logika/axiomasemak-iteletkalkulus]] — az ítéletlogikai axiómasémák, amelyekre a logikai szabályok bizonyítása visszavezet
- [[concepts/logika/predikatumkalkulus-axiomasemak]] — az elsőrendű axiómasémák, amelyekre a kvantoros szabályok épülnek
- [[concepts/logika/bizonyitaselmelet-helyesseg-teljesseg]] — a helyesség és teljesség általános fogalma, amelynek a természetes technika megállási feltétele egy konkrét megvalósítása
