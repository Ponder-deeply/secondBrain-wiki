---
tags: [concept, logika/bizonyitaselmelet]
sources: ["Szintaktikus következmény.pdf"]
derivation: source
updated: 2026-09-08
---

# Dedukciós tétel és a levezetés tulajdonságai

A dedukciós tétel egy több premisszájú levezetést egyetlen, csupa-implikációs formula bizonyításává alakít át; ez teszi lehetővé, hogy a levezethetőségről szóló állításokat (konkatenáció, vágás, konzisztencia) a bizonyítás szintjén, ne a levezetés-konstrukció szintjén kelljen igazolni.

## Tartalom

### A dedukciós tétel

Általánosított alakjában: az $\{F_1, F_2, \dots, F_n\} \vdash_0 G$ pontosan akkor áll fenn, ha

$$\vdash_0 F_1 \supset (F_2 \supset (\dots \supset (F_{n-1} \supset (F_n \supset G)) \dots))$$

azaz a premisszahalmazból való levezethetőség ekvivalens azzal, hogy a premisszák implikációláncba rendezve, a konklúzióval a végén, **bizonyítható** (üres feltételhalmazból levezethető) formulát adjanak. Az $n=1$ eset a tétel legegyszerűbb alakja: $F \cup \{A\} \vdash_0 G$ pontosan akkor, ha $F \vdash_0 A \supset G$; ennek **megfordítása** ugyanez az irány visszafelé, amit a fenti ekvivalencia már tartalmaz.

A tétel a [[concepts/logika/bizonyitaselmeleti-levezetes]]-ben definiált $\vdash_0$-t köti össze a formulák közötti implikációval, és számos következő tétel bizonyítási eszköze.

### A levezetés tulajdonságai

**Két levezetés összefésülése (konkatenáció):** ha $F$-ből levezethető $G_1$, és $S$-ből levezethető $G_2$, akkor a két levezetés egymás után fűzése az $F \cup S$-ből való levezetés — tehát $G_1$ és $G_2$ együtt levezethető $F \cup S$-ből.

**Vágás (tranzitivitás-szerű tulajdonság):** ha $F$-ből levezethető $G_1$, $S$-ből levezethető $G_2$, és $\{G_1, G_2\}$-ből levezethető $A$, akkor $F \cup S$-ből levezethető $A$. A közbülső formulák ($G_1, G_2$) tehát „eltüntethetők”, ha a végkövetkeztetés belőlük is levezethető.

**A dedukciós tétel következménye — az eldöntésprobléma tétele a bizonyításelméletben:** a fenti ekvivalencia $\{F_1, \dots, F_n\} \vdash_0 G \Leftrightarrow \; \vdash_0 F_1 \supset (\dots \supset (F_n \supset G) \dots)$ éppen ez; bizonyítása a dedukciós tétel ismételt alkalmazása.

### Levezethetőség és konzisztencia

- Ha $F$-ből levezethető $G$, akkor $F \cup \{\neg G\}$ ellentmondásos.
- Ha $\{F_1, \dots, F_n\}$ ellentmondásos, akkor kielégíthetetlen.
- **Tétel:** legyen $A$ formula és $F$ konzisztens formulahalmaz. Ekkor (a) $F, \neg A$ ellentmondásos $\iff F \vdash_0 A$; (b) $F, A$ ellentmondásos $\iff F \vdash_0 \neg A$.

*Bizonyítás vázlata (a):* $\Rightarrow$: ha $F, \neg A$ ellentmondásos, van $B$, hogy $F, \neg A \vdash_0 B$ és $F, \neg A \vdash_0 \neg B$. A dedukciós tétel szerint $F \vdash_0 \neg A \supset B$ és $F \vdash_0 \neg A \supset \neg B$. A két levezetés konkatenációja, majd az (A3) axióma $(\neg A \supset B) \supset ((\neg A \supset \neg B) \supset A)$ alakjának alkalmazása és kétszeri modus ponens adja $F \vdash_0 A$-t. $\Leftarrow$: ha $F \vdash_0 A$, akkor $F, \neg A \vdash_0 A$ és $F, \neg A \vdash_0 \neg A$ triviálisan, tehát $F, \neg A$ ellentmondásos. A (b) rész az (a)-ra vezethető vissza $A$ helyére $\neg A$-t írva, felhasználva hogy ami $F, A$-ból levezethető, az $F, \neg\neg A$-ból is az.

### Kalmár László lemmája

Egy $k$ változós $G$ formula igazságtáblájának minden sorára, ha $X_1', X_2', \dots, X_k'$ (az adott sorbeli literálok $X_i$ vagy $\neg X_i$ alakban) és $G'$ jelöli a formulák literállal helyettesített változatát, akkor $X_1', X_2', \dots, X_k' \vdash_0 G'$.

**Tétel (Kalmár lemmája):** ha $X_1', X_2', \dots, X_k' \vdash_0 G'$ és $\neg X_1', X_2', \dots, X_k' \vdash_0 G'$ egyaránt fennáll (azaz $X_1'$ mindkét értékére levezethető $G'$), akkor $X_2', \dots, X_k' \vdash_0 G'$ — az $X_1'$ literál eltüntethető a feltételek közül. A lemma ismételt alkalmazásával a teljes igazságtábla-eset-analízisből egyetlen levezetés áll össze; ez a [[concepts/logika/bizonyitaselmelet-helyesseg-teljesseg]]-ben tárgyalt (gyenge) teljességi bizonyítás kulcslépése.

## Kapocs

- [[concepts/logika/bizonyitaselmeleti-levezetes]] — a levezetés és a $\vdash_0$ fogalma, amelyre ez a tétel épül
- [[concepts/logika/axiomasemak-iteletkalkulus]] — az (A3) axióma, amelyet a fenti bizonyítás felhasznál
- [[concepts/logika/bizonyitaselmelet-helyesseg-teljesseg]] — ahol a dedukciós tétel és Kalmár lemmája a teljességi bizonyítás eszközei
- [[concepts/logika/kovetkeztetesforma]] — a szemantikus következményfogalom, amelynek ekvivalenciáját e tulajdonságok megalapozzák
