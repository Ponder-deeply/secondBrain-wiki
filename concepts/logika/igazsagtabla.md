---
tags: [concept, logika/iteletlogika-szemantika]
sources: [iteletlogika.pdf]
references: [Pásztorné Varga Katalin – Várterész Magda, A matematikai logika alkalmazásszemléletű tárgyalása]
derivation: source
updated: 2026-09-08
---

# Igazságtábla

Az igazságtábla a logikai összekötőjelek, illetve egy formula helyettesítési értékeinek kimerítő, táblázatos megadása minden lehetséges interpretációra.

## Tartalom

### A négy összekötőjel igazságtáblája

Az ítéletlogika a lehetséges kétváltozós logikai műveletek közül csak négyet használ: a $\neg$ (unér), valamint a $\wedge$, $\vee$, $\supset$ (binér) műveleteket. (A táblázat, amelyből ezek választhatók, összesen 16 kétváltozós műveletet tartalmaz — a 4 db egy- és a 2 db nulla-változós művelet is közéjük tartozik —, de a tárgy csak a fenti négyre szorítkozik.)

| $A$ | $B$ | $\neg A$ | $A \wedge B$ | $A \vee B$ | $A \supset B$ |
|---|---|---|---|---|---|
| $i$ | $i$ | $h$ | $i$ | $i$ | $i$ |
| $i$ | $h$ | $h$ | $h$ | $i$ | $h$ |
| $h$ | $i$ | $i$ | $h$ | $i$ | $i$ |
| $h$ | $h$ | $i$ | $h$ | $h$ | $i$ |

### Formula igazságtáblája

Egy **$n$-változós formula igazságtáblája** egy $n+1$ oszlopból és $2^n + 1$ sorból álló táblázat: a fejlécben a bázis (a formula változói rögzített sorrendben) és maga a formula szerepel, a sorokban a változók alatt az [[concepts/logika/iteletlogikai-interpretacio]] szerinti interpretációk, a formula alatt a hozzájuk tartozó helyettesítési értékek.

Egy $n$-változós formula így az igazságtáblájával megadott $\{i,h\}^n \to \{i,h\}$ $n$-változós logikai műveletet ír le.

**Példa.** A $(\neg(Z \supset \neg X) \vee Y)$ formula igazságtáblája:

| $X$ | $Y$ | $Z$ | $(\neg(Z \supset \neg X) \vee Y)$ |
|---|---|---|---|
| $i$ | $i$ | $i$ | $i$ |
| $i$ | $i$ | $h$ | $i$ |
| $i$ | $h$ | $i$ | $i$ |
| $i$ | $h$ | $h$ | $h$ |
| $h$ | $i$ | $i$ | $i$ |
| $h$ | $i$ | $h$ | $i$ |
| $h$ | $h$ | $i$ | $h$ |
| $h$ | $h$ | $h$ | $h$ |

Ebben a példában az $X, Y, Z$ bázis mellett a formula igazhalmaza $\{(i,i,i), (i,i,h), (i,h,i), (h,i,i), (h,i,h)\}$, hamishalmaza $\{(i,h,h), (h,h,i), (h,h,h)\}$.

### Alkalmazás: szemantikai tulajdonságok vizsgálata

Az igazságtábla kimerítő módszer a [[concepts/logika/szemantikus-kovetkezmeny]] lapon tárgyalt tulajdonságok — kielégíthetőség, tautológia, szemantikus következmény — közvetlen ellenőrzésére: ha egy formula minden sorban $i$ értéket vesz fel, tautológia; ha minden sorban $h$, kielégíthetetlen; egyébként kielégíthető, de nem tautológia.

Formulahalmaz vizsgálatakor a halmaz elemeit egyetlen közös táblázatban is fel lehet tüntetni, vagy — mivel egy $F$ formulahalmaz pontosan azokban az interpretációkban elégíthető ki, amelyekben minden eleme igaz — a halmaz konjunkciójaként képzett egyetlen formula igazságtáblájára vissza lehet vezetni a vizsgálatot.

## Kapocs

- [[concepts/logika/iteletlogikai-interpretacio]] — a táblázat sorai: interpretációk és helyettesítési értékek
- [[concepts/logika/zarojelelhagyas]] — a táblázatban szereplő formulák tömör, zárójel nélküli alakja
- [[concepts/logika/szemantikus-kovetkezmeny]] — kielégíthetőség, tautológia és szemantikus következmény igazságtáblával
- [[concepts/logika/kovetkeztetesforma]] — a következtetésforma helyességének igazságtáblás ellenőrzése
