---
tags: [concept]
sources: [konkprog-canvas-feladat-1-egyszeru-java-osztaly.md, konkprog-canvas-feladat-2-absztrakt-osztaly-es-oroklodes.md, konkprog-canvas-feladat-3-interfesz.md]
derivation: source
kind: overview
element: earth
updated: 2026-10-23
---

# Java objektumorientált alapok (Employee-feladatsor)

A kurzus bevezető OOP-feladatsora: osztály, absztrakt osztály és öröklődés, interfész – egyetlen `Employee` példán keresztül.

## Tartalom

1. **Egyszerű Java osztály:** `Employee` két privát adattaggal (`name`, `salary`), nyilvános konstruktorral, getterekkel és egy metódussal, amely a fizetést egy százalékkal megemeli (lebegőpontos paraméter). Minden feladathoz külön `main`-nel rendelkező tesztosztály készül.
2. **Absztrakt osztály és öröklődés:** `Employee` absztrakt lesz; leszármazottai `Manager` és `Subordinate`. A `salary` getter absztrakt; az eredeti működés a `Subordinate`-ben felülírva. A `Manager` `Employee`-listát tárol, hozzáadó/törlő metódusokkal, és a `getSalary()` a saját fizetéséhez hozzáadja a listabeli alkalmazottak fizetésének **5%-át**.
3. **Interfész:** `SalariedEntity` egyetlen `getSalary()` metódussal; az `Employee` megvalósítja, és egy új `Subcontractor` (alvállalkozó) osztály is, amely a név helyett az adószámot (`long`) tárolja.

## Kapocs

- [[concepts/konkprog/szal-letrehozas]] — a `Runnable` is interfész
- [[concepts/konkprog/szalbiztos-osztaly-tervezes]] — saját osztályok szálbiztossá tétele
