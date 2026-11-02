---
tags: [concept]
sources: [konkprog-canvas-feladat-3-atomic-tipusok.md]
derivation: source
kind: definition
element: earth
updated: 2026-10-23
---

# Atomic típusok (java.util.concurrent.atomic)

A `java.util.concurrent.atomic` csomag kész, szálbiztos típusokat ad: az `AtomicInteger` a `ThreadSafeMutableInteger`, az `AtomicIntegerArray` a `ThreadSafeMutableIntArray` beépített megfelelője.

## Tartalom

A saját szálbiztos típusok ([[concepts/konkprog/szalbiztos-osztaly-tervezes]]) Java-beli megfelelői a `java.util.concurrent.atomic` csomagban találhatók:

| Saját típus | Beépített megfelelő |
|---|---|
| `ThreadSafeMutableInteger` | `AtomicInteger` |
| `ThreadSafeMutableIntArray` | `AtomicIntegerArray` |

**Feladat:** a kipróbáló programot át kell írni úgy, hogy ezeket használja; az eredménynek ugyanannak kell lennie.

## Kapocs

- [[concepts/konkprog/szalbiztos-osztaly-tervezes]] — a saját változat
- [[concepts/konkprog/volatile-mezo]] — a volatile nem atomi
