---
tags: [concept, esemalk/csharp-nyelvi-alapok]
sources: [elte_eva_ea00_csharp.pdf]
derivation: source
updated: 2026-09-12
---

# C# előfordítási direktívák

A nyelv *előfordítási direktívákat* tartalmaz, amelyek előzetesen kerülnek
feldolgozásra, még a tényleges fordítás előtt.

## Tartalom

Az előfordítási direktívák lehetőséget adnak bizonyos kódsorok feltételes
fordítására, hibajelzésre, környezetfüggő beállítások lekérdezésére, pl.
`#if`, `#define`, `#error`, `#line`.

Mivel C#-ban nem választható szét a deklaráció a definíciótól, a kód
tagolását a *régiók* segítik elő, amelyek tetszőleges kódblokkokat foghatnak
közre:

```csharp
#region <név>
...
#endregion
```

A régiók nem befolyásolják a lefordított kódot, csupán a
fejlesztőkörnyezetben (összecsukható blokkként) érhetőek el.

## Kapocs

- [[concepts/esemalk/csharp-megjegyzesek]] — a régiókhoz hasonlóan a
  megjegyzések sem befolyásolják a lefordított kódot
- [[subjects/esemalk]] — a kurzus áttekintése
