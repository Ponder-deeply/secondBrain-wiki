---
tags: [concept]
sources: [Elsőrendű_logika_szemantika.pdf]
derivation: source
updated: 2026-09-08
---

# Elsőrendű szemantikus fa

Az elsőrendű szemantikus fa egy adott véges $U$ univerzum feletti összes lehetséges interpretációt szisztematikusan, egy bináris fa ágaiként állítja elő: a fa minden szintje egy alapatomnak felel meg, minden csúcsból két él indul (az alapatom igaz, illetve hamis a hozzá tartozó interpretációkban).

## Tartalom

### Motiváció

Az [[concepts/logika/szemantikus-tulajdonsagok]] szerint egy formula(halmaz) kielégíthetőségének vagy kielégíthetetlenségének eldöntéséhez elvben az összes interpretáló struktúrára szükség van, ezek száma azonban már megszámlálhatóan végtelen univerzum esetén is kontinuum számosságú ([[concepts/logika/elsorendu-interpretacio]]). Rögzített, **véges** $U$ univerzum mellett viszont a predikátumszimbólumokra vonatkozó összes lehetséges interpretáció véges eszközzel, egy fával felsorolható — ez az elsőrendű szemantikus fa.

### Felépítés

Legyenek az $L$ nyelv szignatúrája szerint $r_1, \dots, r_n$ a predikátumszimbólumok aritásai, és legyen $U$ rögzített. Minden $j = 1,\dots,n$ értékre előállítjuk a $P_{r_j}$ predikátumszimbólumhoz tartozó **összes alapatomot** — azaz $P_j$ minden lehetséges $U^{r_j}$-beli argumentum-behelyettesítését. Rögzítünk egy sorrendet ezen alapatomok között: ez a **bázis** ($B$).

A fa szintjeihez a bázis sorrendjében rendeljük hozzá az alapatomokat: az első szinthez a bázis első alapatomját, és így tovább. Egy-egy szint minden csúcsából pontosan **két él** indul ki:

- az egyik a szinthez rendelt alapatommal van címkézve — ez azt jelenti, hogy az alapatom **igaz** az élhez tartozó interpretációkban;
- a másik ennek **negáltjával** — az alapatom **hamis** az élhez tartozó interpretációkban.

A fa egy gyökértől levélig futó **ága** így a bázis minden alapatomjához hozzárendel egy igazságértéket, azaz pontosan egy interpretációt ad meg a predikátumszimbólumokra. A fa összes ága együtt a lehetséges interpretációk teljes, ismétlés nélküli felsorolása $U$ felett.

### Példa

Legyen a formulahalmaz $K = \{\forall x P(x),\ \forall y \forall z(\lnot Q(y,z) \lor \lnot P(z)),\ \forall u \forall v\, Q(u,v)\}$, és legyen $U = \{a,b,c\}$. A $B$ bázis (az alapatomok egy rögzített sorrendje): $P(a), Q(a,a), P(b), Q(a,b), \dots, Q(c,c)$. A $B$ bázis alapján felépített bináris fa minden ága egy-egy konkrét interpretációt jelöl ki $P$-re és $Q$-ra $U$ felett; a $K$ formulahalmaz kielégíthetősége ezen ágak — vagyis a véges sok interpretáció — végigjárásával eldönthető.

### Szerepe

A szemantikus fa a szemantikai kiértékelés véges, algoritmikus eszközzé tételének első lépése: rögzített véges univerzum mellett a kielégíthetőség eldönthető a fa bejárásával. Ez a gondolat vezet át a szintaktikai eszközökhöz — a **tabló** és a **rezolúció** kalkulusaihoz —, amelyek a szemantikus fa szerkezetét használják fel arra, hogy a kielégíthetetlenséget szintaktikai levezetéssel, az összes interpretáció explicit felsorolása nélkül igazolják.

## Kapocs

- [[concepts/logika/elsorendu-interpretacio]] — a fa ágai által megadott interpretációk
- [[concepts/logika/szemantikus-tulajdonsagok]] — a kielégíthetőség/kielégíthetetlenség fogalma, amit a fa eldönthetővé tesz véges $U$ mellett
- [[concepts/logika/valtozokiertekeles]] — a formulák teljes kiértékeléséhez a fa melletti $\kappa$ is szükséges
- [[concepts/logika/elsorendu-tablo]] — a fa gondolatára épülő szintaktikai kalkulus
- [[concepts/logika/elsorendu-rezolucio]] — a másik, kielégíthetetlenségre kidolgozott szintaktikai kalkulus
