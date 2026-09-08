---
tags: [concept]
sources: [iteletlogika.pdf]
references: [Pásztorné Varga Katalin – Várterész Magda, A matematikai logika alkalmazásszemléletű tárgyalása]
derivation: source
updated: 2026-09-08
---

# Kielégíthetőség, tautológia és szemantikus következmény

A formulák és formulahalmazok legfontosabb szemantikai tulajdonságai — kielégíthetőség, kielégíthetetlenség, tautológia — és az ezekre épülő szemantikus következményfogalom ($\models_0$), amely a [[concepts/logika/kovetkeztetesforma|következtetésforma]] helyességét pontos ítéletlogikai fogalommá teszi.

## Tartalom

### Interpretáció kielégít egy formulát

Az [[concepts/logika/iteletlogikai-interpretacio|$I$ interpretáció]] **kielégít** egy $B$ formulát ($I \models_0 B$), ha a formula helyettesítési értéke $i$ az $I$ interpretációban. A formulát kielégítő interpretációt a formula **modelljének** is nevezik.

### Kielégíthetőség, kielégíthetetlenség, tautológia

- $B$ **kielégíthető**, ha legalább egy interpretáció kielégíti.
- $B$ **kielégíthetetlen**, ha egyetlen interpretáció sem elégíti ki.
- $B$ **tautológia** ($\models_0 B$), ha minden interpretáció kielégíti. A tautológiát **ítéletlogikai törvénynek** is nevezik.

Példák ítéletlogikai törvényekre: $\models_0 A \supset (B \supset A)$; $\models_0 (A \supset B \supset C) \supset (A \supset B) \supset A \supset C$; $\models_0 A \supset B \supset (A \wedge B)$; $\models_0 ((A \supset B) \supset A) \supset A$.

Ugyanez formulahalmazra: egy $F = \{A_1, \dots, A_n\}$ formulahalmazt egy $I$ interpretáció kielégít ($I \models_0 F$), ha $F$ minden formulájának helyettesítési értéke $i$. $F$ kielégíthető, ha van ilyen $I$; kielégíthetetlen, ha bármely interpretációban $F$-nek van legalább egy hamis eleme. Formulahalmazokra a tautológia fogalmát nem használjuk.

### Tautologikus ekvivalencia

Két formula **tautologikusan ekvivalens** ($A \sim_0 B$), ha igazságtáblájuk azonos; ezzel ekvivalens megfogalmazás, hogy $A \models_0 B$ és $B \models_0 A$ egyaránt fennáll, azaz $\models_0 (A \supset B) \wedge (B \supset A)$.

Fontos átalakítási szabályok:

- $X \supset Y \sim_0 \neg X \vee Y$
- $\neg\neg X \sim_0 X$
- **De Morgan:** $\neg(X \wedge Y) \sim_0 \neg X \vee \neg Y$; $\neg(X \vee Y) \sim_0 \neg X \wedge \neg Y$
- **Egyszerűsítés:** $(X \vee d) \wedge (\neg X \vee d) \sim_0 d$, ahol $d$ elemi diszjunkció; $(X \wedge k) \vee (\neg X \wedge k) \sim_0 k$, ahol $k$ elemi konjunkció (lásd [[concepts/logika/iteletlogikai-formula]]).

### Szemantikus következmény

Egy $G$ formula **szemantikus** (vagy **tautologikus**) **következménye** az $F = \{F_1, \dots, F_n\}$ formulahalmaznak, ha minden olyan $I$ interpretációra, amelyre $I \models_0 F$, $I \models_0 G$ is fennáll — azaz $F$ minden modellje $G$-nek is modellje. Jelölés: $F \models_0 G$.

**Tétel.** Ha $G$ bármely $F$ feltételhalmaznak következménye, akkor $G$ tautológia.

Egy $(F, G)$ [[concepts/logika/kovetkeztetesforma|következtetésforma]] pontosan akkor **helyes**, ha $F \models_0 G$ **és** létezik olyan $I$ interpretáció, amelyre $I \models_0 F$ (azaz $F$ kielégíthető).

**Tétel (tranzitivitás).** Ha $F \models_0 G_1$ és $F \models_0 G_2$, valamint $\{G_1, G_2\} \models_0 A$, akkor $F \models_0 A$.

### Visszavezetés kielégíthetetlenségre — az eldöntésprobléma

**Tétel.** $F$-nek akkor és csak akkor következménye $G$, ha az $F \cup \{\neg G\}$ formulahalmaz (ekvivalensen az $F_1 \wedge \dots \wedge F_n \wedge \neg G$ formula) kielégíthetetlen.

Ez alapján az egyik szemantikus **eldöntésprobléma**: tetszőleges formuláról eldönteni, kielégíthetetlen-e.

### Dedukciós tétel

**Tétel (dedukciós).** $\{F_1, \dots, F_n\} \models_0 G$ akkor és csak akkor, ha $\{F_1, \dots, F_{n-1}\} \models_0 (F_n \supset G)$.

Ismételt alkalmazásával: $\{F_1, \dots, F_n\} \models_0 G$ akkor és csak akkor, ha
$$\models_0 F_1 \supset (F_2 \supset \dots (F_{n-1} \supset (F_n \supset G)) \dots)$$

Ez adja a másik szemantikus eldöntésproblémát: tetszőleges formuláról eldönteni, tautológia-e.

### Legszűkebb következmény, elő- és visszakövetkeztetés

Legyen $F$ feltételhalmazban $n$ változó szerepel. A **legszűkebb következmény** az az $\{i,h\}^n \to \{i,h\}$ leképezés, amely pontosan azokhoz az interpretációkhoz rendel $i$ értéket, amelyek kielégítik $F$-et. $G$ pontosan akkor következménye $F$-nek, ha $R \supset G$ tautológia, ahol $R$ a legszűkebb következményt leíró formula — azaz $R$ igazhalmaza része $G$ igazhalmazának.

- **Előrekövetkeztetés:** ismert $F$, és keressük a lehetséges következményeket a legszűkebb következmény ($R$) meghatározásával.
- **Visszakövetkeztetés:** ismert $F$ és egy $B$ jelölt következmény; azt vizsgáljuk, hogy $F \cup \{\neg B\}$ kielégíthetetlen-e.

**Példa (nyomozás, [[concepts/logika/kovetkeztetesforma]]).** $F = \{F \supset K, K \supset A, F \vee R, (R \wedge H) \supset A, \neg A\}$. Előrekövetkeztetéssel: $F$-et egyetlen interpretáció elégíti ki ($A=h, F=h, K=h, R=i, H=h$), a legszűkebb következmény $\neg A \wedge \neg F \wedge \neg K \wedge R \wedge \neg H$, és mivel $(\neg A \wedge \neg F \wedge \neg K \wedge R \wedge \neg H) \supset \neg F$ tautológia, $\neg F$ következmény. Visszakövetkeztetéssel ugyanez: $F \cup \{F\}$ kielégíthetetlen, tehát $\neg F$ következmény.

### Alkalmazás: kielégíthetőség és tautológia igazságtáblával

Az [[concepts/logika/igazsagtabla]] felírásával közvetlenül eldönthető minden fenti tulajdonság: ha egy formula igazságtáblájának minden sora $i$, tautológia; ha minden sora $h$, kielégíthetetlen; egyébként kielégíthető, de nem tautológia. Szemantikus következmény vizsgálatakor csak azokban a sorokban kell a következményformula értékét nézni, ahol a feltételhalmaz minden eleme igaz.

**Példa.** Helyes-e a $\{\neg A, \neg A \vee B, B \supset A\} \models_0 \neg A \supset B$ következmény? A feltételhalmaz a $(h,i)$ és $(h,h)$ interpretációkban (az $A,B$ bázison) kielégíthető. A $(h,i)$ interpretációban a következmény igaz, de a $(h,h)$ interpretációban hamis — tehát a következmény **nem helyes**.

## Kapocs

- [[concepts/logika/iteletlogikai-interpretacio]] — az interpretáció, amelyre a kielégítés fogalma épül
- [[concepts/logika/igazsagtabla]] — a szemantikai tulajdonságok kimerítő ellenőrzésének eszköze
- [[concepts/logika/kovetkeztetesforma]] — a helyes következtetésforma pontos definíciója szemantikus következménnyel
- [[concepts/logika/iteletlogikai-formula]] — elemi konjunkció és elemi diszjunkció, az egyszerűsítési szabályokban használt fogalmak
