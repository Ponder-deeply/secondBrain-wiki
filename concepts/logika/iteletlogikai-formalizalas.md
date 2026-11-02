---
tags: [concept]
sources: [Ítéletlogika_alapjai.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-21
---

# Ítéletlogikai formalizálás: a betörős feladat

Természetes nyelvű állítások formalizálása ítéletlogikában: atomi állításokból ítéletváltozók, az összetett mondatokból formulák lesznek, majd a formulahalmazból következtetést vonunk le igazságtáblával. A gyakorlat egyetlen végigvitt feladaton mutatja be az egész láncot.

## Tartalom

### Egyszerű és összetett állítások

Az **egyszerű** (atomi) állítás egy ítéletváltozó (pl. $E$: „esik az eső”, $F$: „felhős az ég”). Az **összetett** állítás összekötőjelekkel épül fel:

| Mondat | Formula | Típus |
|---|---|---|
| Nem süt a Nap. | $\neg N$ | negációs |
| Esik az eső és nem süt a Nap. | $E \wedge \neg N$ | konjunkciós |
| Süt a Nap vagy felhős az ég. | $N \vee F$ | diszjunkciós |
| Ha esik az eső, akkor felhős az ég. | $E \supset F$ | implikációs |

### A feladat: melyik szobákban járt a betörő?

A helyszínelők hét megfigyelése:

1. A konyhában az ajtó be volt törve, így a betörő ott biztos járt.
2. Ha a konyhában járt, akkor biztos nem volt a fürdőben.
3. A hálóban vagy a fürdőben volt, illetve nem járt a spájzban vagy járt a hálóban.
4. Nem igaz, hogy a hallban járt, és ha nem járt a nappaliban, akkor a spájzban volt.
5. Akkor és csak akkor volt a spájzban, ha volt az étkezőben is.
6. A spájzt feldúlta a betörő, és csak akkor járt a nappaliban, ha a hallban is.
7. A betörő csak akkor járt a fürdőben, ha nem volt a spájzban vagy járt a fürdőben.

**Atomi állítások.** $A$: konyha, $B$: fürdő, $C$: háló, $D$: spájz, $E$: étkező, $F$: nappali, $G$: hall (mindegyik: „a betörő ott járt”). Azonos állítás mindig azonos változó.

**Formulák.**

1. $A$
2. $A \supset \neg B$
3. $(C \vee B) \wedge (\neg D \vee C)$
4. $\neg(G \wedge (\neg F \supset D))$
5. $(D \supset E) \wedge (E \supset D)$ — a „akkor és csak akkor” két implikációval
6. $D \wedge (F \supset G)$ — a „csak akkor … ha” iránya: $F \supset G$
7. $B \supset (\neg D \vee B)$

A „csak akkor, ha” a hibaforrás: „$X$ csak akkor, ha $Y$” jelentése $X \supset Y$ (nem fordítva). A zárójelek elhagyását a [[concepts/logika/zarojelelhagyas]] szabályai adják; a hatodik formula teljesen zárójelezve $(D \wedge (F \supset G))$.

### Lépésenkénti következtetés igazságtáblával

A feladatot nem egyetlen óriás táblával, hanem kisebb következményekkel oldjuk meg ([[concepts/logika/szemantikus-kovetkezmeny]]):

- $\{A,\ A \supset \neg B\} \models_0 \neg B$: a konyhában járt, a fürdőben nem (kétváltozós tábla; az egyetlen sor, ahol mindkét premissza igaz, $A=i,B=h$).
- $\{\neg B,\ (C \vee B) \wedge (\neg D \vee C)\} \models_0 C$: a hálóban járt (három változó, 8 sor; a premisszák csak olyan sorban igazak, ahol $C=i$).
- A maradék formulákból (4–6) kiderül, hogy a spájzban és az étkezőben is járt ($D \wedge E$), a nappaliban és a hallban viszont nem.

Az összegzett állítás ellenőrizhető egyetlen következményként is:

$$\{\neg(G \wedge (\neg F \supset D)),\ (D \supset E) \wedge (E \supset D),\ D \wedge (F \supset G)\} \models_0 D \wedge E \wedge \neg F \wedge \neg G$$

A levezetés kézzel: a 6. formula szerint $D=i$ és $F \supset G$; mivel $D=i$, $\neg F \supset D$ igaz, így a 4. formula csak $G=h$ esetén teljesül; $F \supset G$ és $G=h$ miatt $F=h$; az 5. formulából $E=i$. A betörő tehát a **konyhában, a hálóban, a spájzban és az étkezőben** járt, a fürdőben, a nappaliban és a hallban nem.

### Két visszavezetés az eldöntésre

A fenti következmény két módon alakítható át egyetlen eldöntendő kérdéssé (mindkettő a [[concepts/logika/szemantikus-kovetkezmeny]] lapon szereplő tételekből jön):

1. **Dedukciós tétel / az eldöntésprobléma tétele**: $\{A_1,\dots,A_n\} \models_0 B$ pontosan akkor, ha $A_1 \supset A_2 \supset \dots \supset A_n \supset B$ tautológia.
2. **Visszakövetkeztetés**: $\{A_1,\dots,A_n\} \models_0 B$ pontosan akkor, ha $\{A_1,\dots,A_n,\neg B\}$ kielégíthetetlen.

Ugyanezt a két irányt viszi tovább a tablókalkulus ([[concepts/logika/analitikus-tablo]]).

### Következmények felismerése a táblán

Ha $\{A,\ B \supset A\}$ formulahalmaz közös igazságtáblája adott, akkor egy $G$ pontosan akkor következmény, ha $G$ igaz minden olyan sorban, ahol a halmaz minden eleme igaz. Példa: $\{A, B \supset A\}$ következménye $A \vee D$, $A \vee B$, $A \vee \neg A$; *nem* következménye $\neg B$, $\neg A$, $\neg A \vee B$. A $\{A \wedge B,\ \neg B \vee \neg A\}$ halmaz kielégíthetetlen (nincs olyan sor, ahol mindkét eleme igaz), ezért **minden** formula következménye (a definíció szerint nincs olyan sor, ahol a premisszák igazak és a következmény hamis).

## Kapocs

- [[concepts/logika/igazsagtabla]] — a közös igazságtábla felírása
- [[concepts/logika/szemantikus-kovetkezmeny]] — a következmény, a dedukciós tétel és a visszavezetés kielégíthetetlenségre
- [[concepts/logika/kovetkeztetesforma]] — a következtetésforma helyessége
- [[concepts/logika/zarojelelhagyas]] — a formulák rövid, zárójel nélküli alakja
- [[concepts/logika/elsorendu-formalizalas]] — ugyanez elsőrendben: predikátumok és kvantorok
