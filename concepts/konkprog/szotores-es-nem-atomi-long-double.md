---
tags: [concept]
sources: [Java-Language-Specification-SE-21.pdf]
derivation: source
kind: pitfall
element: air
updated: 2026-10-23
---

# Szótörés és a long/double nem atomi kezelése

A JVM-nek külön mezők és tömbelemek frissítése nem zavarhatja egymást (nincs word tearing); a nem `volatile` 64 bites `long` és `double` írása viszont két 32 bites írásnak számíthat.

## Tartalom

### Szótörés (JLS §17.6)

Minden mező és tömbelem *különálló*: egyik frissítése nem hathat más mező/elem olvasására vagy írására. Két szál, amely egy `byte` tömb szomszédos elemeit írja, nem zavarhatja egymást, és nem igényel szinkronizációt a szekvenciális konzisztenciához. Ha a processzor nem tud egyetlen bájtot írni, a megvalósítás nem oldhatja meg úgy, hogy egy egész szót felolvas, módosít és visszaír – ezt nevezik *word tearing*-nek. A JLS tesztprogramja (`WordTearing`) ilyen hibát keres.

### long és double (§17.7)

A memóriamodell szempontjából a nem `volatile` `long`/`double` egyetlen írása **két külön, 32 bites írás** lehet; egy szál láthatja az egyik írás első 32 bitjét és a másik második felét. Garanciák:

- `volatile` `long`/`double` olvasása/írása mindig atomi;
- referenciák olvasása/írása mindig atomi (32 vagy 64 bites megvalósítástól függetlenül).

**Javaslat:** a megosztott 64 bites értékeket deklaráljuk `volatile`-nak, vagy szinkronizáljuk a programot.

## Kapocs

- [[concepts/konkprog/volatile-mezo]] — atomicitás volatile esetén
- [[concepts/konkprog/java-memoriamodell]] — a modell
