---
tags: [concept]
sources: [Java-Language-Specification-SE-21.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-23
---

# A volatile mező

A `volatile` mező olvasásakor és írásakor a Java memóriamodell biztosítja, hogy minden szál konzisztens értéket lásson; zár nélküli, de csak láthatóságot és sorrendet adó alternatíva.

## Tartalom

### Definíció (JLS §8.3.1.4)

A szálak közös változókat érnek el; a szokásos módszer a kölcsönös kizárás zárral. A `volatile` mező ennél kényelmesebb *bizonyos célokra*: a memóriamodell garantálja, hogy minden szál konzisztens értéket lát. **Fordítási hiba**, ha egy `final` változó egyben `volatile`.

### Szinkronizációs hatás (§17.4)

- `volatile` olvasás és írás *szinkronizációs művelet*; a `volatile` változóra írás *synchronizes-with* minden későbbi olvasásával, így happens-before él.
- `volatile` `long` és `double` írása/olvasása mindig atomi ([[concepts/konkprog/szotores-es-nem-atomi-long-double]]).

### A JLS példája (8.3.1.4-1)

`static int i = 0, j = 0;` – az egyik szál ismételten `one()`-t hívja (`i++; j++;`), a másik `two()`-t (kiírja `i`-t és `j`-t). Szinkronizálás nélkül `two()` olyan `j`-t is kiírhat, amely nagyobb `i`-nél. Két javítás:

1. mindkét metódus `synchronized` – kizárja az egyidejű futást, `two()` mindig azonos értéket lát;
2. `i` és `j` legyen `volatile` – a metódusok futhatnak párhuzamosan, `j` sosem nagyobb `i`-nél (az írások sorrendje megmarad), de `two()` mégis láthat a `i`-nél jóval nagyobb `j`-t, mert `one()` sokszor lefuthat az `i` és a `j` beolvasása között.

Tehát a `volatile` **nem teszi atomivá** az összetett műveleteket (`i++`).

## Kapocs

- [[concepts/konkprog/java-memoriamodell]] — happens-before
- [[concepts/konkprog/synchronized-monitor]] — az alternatíva
- [[concepts/konkprog/atomic-tipusok]] — atomi összetett műveletek
