---
tags: [concept, logika/bizonyitaselmelet]
sources: ["Szintaktikus következmény.pdf"]
derivation: source
updated: 2026-09-08
---

# Bizonyításelmélet helyessége és teljessége

A szintaktikus ($\vdash_0$) és a szemantikus ($\models_0$) következményfogalom két külön irányban egyezik: a **helyesség** azt garantálja, hogy amit levezetünk, az valóban következik; a **teljesség** azt, hogy ami következik, az le is vezethető. E két tétel együtt teszi a bizonyításelméleti kalkulust a szemantikus tárgyalással ekvivalens eszközzé.

## Tartalom

### Helyesség

**Tétel (helyesség):** a bizonyításelméleti kalkulus **helyes**, azaz ha $\{F_1, F_2, \dots, F_n\} \vdash_0 G$, akkor $\{F_1, F_2, \dots, F_n\} \models_0 G$.

A helyesség a könnyebb irány: az axiómák tautológiák ([[concepts/logika/axiomasemak-iteletkalkulus]]), a modus ponens pedig szemantikailag igazságmegőrző lépés, így a levezetés minden lépése szemantikailag is érvényes marad.

### Gyenge teljesség

**Tétel (gyenge teljesség):** legyen $\{F_1, F_2, \dots, F_n\}$ **véges** formulahalmaz. Ha $\{F_1, \dots, F_n\} \models_0 G$, akkor $\{F_1, \dots, F_n\} \vdash_0 G$.

Speciális esete: ha $G$ tautológia, akkor $G$ bizonyítható ($\vdash_0 G$).

### Erős teljesség (Gödel)

**Tétel (Gödel):** ha $\{F_1, F_2, \dots\} \models_0 G$ (tetszőleges, akár végtelen formulahalmazra), akkor $\{F_1, F_2, \dots\} \vdash_0 G$.

A gyenge teljesség csak véges premisszahalmazra állítja ugyanezt; az erős (Gödel-féle) alak tetszőleges formulahalmazra kiterjeszti.

**A bizonyítás gondolatmenete:**

1. Ha $\{F_1, F_2, \dots\} \models_0 G$, akkor $\{F_1, F_2, \dots\} \cup \{\neg G\}$ kielégíthetetlen.
2. Ha $\{F_1, F_2, \dots\} \cup \{\neg G\}$ ellentmondásos (inkonzisztens), akkor $\{F_1, F_2, \dots\} \vdash_0 G$ — ez a [[concepts/logika/dedukcios-tetel]]-ben tárgyalt tétel közvetlen alkalmazása.

A hiányzó láncszem az, hogy a **kielégíthetetlenség** (szemantikus tulajdonság) és az **ellentmondásosság/inkonzisztencia** (szintaktikus tulajdonság) ugyanúgy két diszjunkt osztályra bontja-e a formulahalmazok halmazát. Az egyik irány könnyű: ha egy formulahalmaz kielégíthetetlen, akkor ellentmondásos is. A nehezebb irányt — hogy kielégíthetetlenségből következik az ellentmondásosság — nem közvetlenül látjuk be, hanem a kontrapozícióját: ha egy formulahalmaz **konzisztens** (ellentmondásmentes), akkor **kielégíthető**.

### Összegzés

Az ítéletkalkulus a szemantikus tárgyalással ekvivalens szintaktikus tárgyalásmód: a helyesség és a (gyenge, majd erős) teljesség együtt biztosítja, hogy $\vdash_0$ és $\models_0$ ugyanazt a következményfogalmat írja le. A bizonyításelméleti levezetés konstrukciója így a tételbizonyítás eszköze, egy valódi szintaktikus **kalkulus**.

A predikátumkalkulus (elsőrendű logika) esetén a helyesség tétele ugyanígy fennáll; a **teljességet a jegyzet nem bizonyítja** — a bizonyítás vázlata itt csak az ítéletkalkulusra szerepel.

## Kapocs

- [[concepts/logika/dedukcios-tetel]] — a dedukciós tétel és Kalmár lemmája, a teljességi bizonyítás fő eszközei
- [[concepts/logika/bizonyitaselmeleti-levezetes]] — a $\vdash_0$ fogalma, amelynek helyességét és teljességét ez a lap tárgyalja
- [[concepts/logika/kovetkeztetesforma]] — a $\models_0$ szemantikus következményfogalom, amelynek ekvivalenciáját e tételek igazolják
- [[concepts/logika/predikatumkalkulus-axiomasemak]] — az elsőrendű axiómarendszer, amelyre a helyesség (de nem a teljesség) itt bizonyítva van
- [[concepts/logika/axiomasemak-iteletkalkulus]] — az axiómák, amelyek tautológia volta a helyesség alapja
