---
tags: [concept]
sources: [08.evolucio.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-12
---

# Rekombináció és keresztezés

Az evolúciós algoritmus rekombinációs operátora a szülők kódjából utódot állít elő; a keresztezés bináris és permutációs, a rekombináció valós vektoros kódolásnál használatos változatai.

## Tartalom

A rekombináció a szülőpárokból (a [[concepts/mesint/szelekcio]] által kiválasztott egyedekből) utódokat képez. A megfelelő operátor a [[concepts/mesint/evolucios-kodolas]] típusától függ.

### Keresztezés bináris (vagy általános jelsorozat-) kódolásnál

- **Egy- illetve többpontos keresztezés**: a szülők kódjában egy vagy több vágási pontot választunk, és a közöttük lévő *kódszakaszokat cseréljük*. Példa a diából (három vágási pont, `|` jelöli): `0|0 1|0|1` és `1|1 1|1|0` → `0 1 1 0 0` és `1 0 1 1 1`.
- **Egyenletes keresztezés**: nem szakaszokat, hanem egyedi *jeleket* cserélünk a két szülő között, pozíciónként (általában véletlen pozíciókon). Példa: a `00101` és `11110` szülőkből az 1. és 3. pozíció cseréjével `10101` és `01110` lesz.

### Permutációk keresztezése

Permutáció-kódolásnál a sima keresztezés megsértené a permutáció tulajdonságot (duplikátumok jelennének meg), ezért speciális operátorok kellenek.

- **Parciálisan illesztett keresztezés** (PMX jellegű): egy szakasz cseréje után a szakaszon *kívüli* elemek között, amelyek megsértik a permutáció tulajdonságot (duplikátumok), párba állítja a duplikátumokat és kicseréli őket. Példa: `2 3 1 5 | 4 6 7` és `1 7 4 2 | 5 3 6` — a `|`-ok közötti szakaszokat cserélve duplikátumok keletkeznek, ezeket párba állítva és cserélve érvényes permutációkat kapunk: `1 7 4 2 5 6 3` és `2 3 1 5 4 7 6`.
- **Ciklikus keresztezés**:
  1. válassz egy véletlen $i \in [1..length]$ pozíciót;
  2. cseréld meg $a_i \leftrightarrow b_i$ (a két szülő $i$-edik elemét);
  3. keress olyan $j \ne i$ pozíciót, amelyre $a_j = a_i$ (duplikátum a felső utódban);
  4. ha nincs ilyen, vége; különben $i := j$;
  5. ugorj a 2. lépésre.

  Azaz a duplikátum pozícióján is cserélünk, és ezt addig ismételjük, amíg a ciklus be nem záródik.

### Rekombináció vektorokra (valós kódolás)

Az $x$, $y$ szülők valós vektorok, az $u$ utód az alábbiak szerint jön létre ($h \ge 0$ a kiterjesztés mértéke):

- **Köztes rekombináció**: az utód a szülők által kifeszített *hipertégla* környezetében lesz:
  $$\forall i = 1 \dots n:\; u_i = a_i x_i + (1-a_i) y_i,\quad a_i \in [-h, 1+h] \text{ véletlen}$$
  (koordinátánként külön véletlen $a_i$).
- **Lineáris rekombináció**: az utód a szülők által kifeszített *egyenesen* (a szülők között vagy környezetükben) lesz:
  $$\forall i = 1 \dots n:\; u_i = a x_i + (1-a) y_i,\quad a \in [-h, 1+h] \text{ véletlen}$$
  (egyetlen közös $a$ minden koordinátára).

## Kapocs

- [[concepts/mesint/evolucios-algoritmus]] — a rekombináció az algoritmus ciklusának lépése
- [[concepts/mesint/evolucios-kodolas]] — a kódolás határozza meg, melyik operátor használható
- [[concepts/mesint/szelekcio]] — a szülők kiválasztása a rekombináció előtt
- [[concepts/mesint/mutacio]] — a másik változtató operátor
- [[concepts/mesint/visszahelyezes]] — az utódok populációba illesztése
