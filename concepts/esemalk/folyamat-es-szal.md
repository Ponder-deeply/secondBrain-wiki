---
tags: [concept]
sources: [elte_eva_ea05_winforms_multithread.pdf]
derivation: source
updated: 2026-09-13
---

# Folyamat és szál

A párhuzamos programozás két alapfogalma: a *folyamat* (*process*) és a *szál*
(*thread*) közötti különbség.

## Tartalom

A párhuzamos programozás szempontjából megkülönböztetjük a **folyamatokat**
(*process*) és a **szálakat** (*thread*).

- A folyamatok teljes végrehajtási környezettel és saját futásidejű
  erőforrásokkal rendelkeznek (például memória). Egy C# program
  alapértelmezetten egyetlen folyamat.
- Egy folyamat több szálat is tartalmazhat. Ezek közös virtuális címtérrel és
  a folyamat rendszererőforrásaival rendelkeznek, ezért a szálak lényegesen
  könnyebb súlyúak a folyamatokhoz képest.
- Minden folyamat rendelkezik egy kezdeti szállal, amelyet gyakran elsődleges
  vagy fő szálnak (*main thread*) neveznek.

A számítógépek több feladatot is el tudnak végezni párhuzamosan, és a
párhuzamos feldolgozás gyakran még egyszerű alkalmazások esetén is
követelmény — például egy szövegszerkesztőnek a felhasználói bevitel
kezelését függetlenül kell tudnia végezni a felhasználói felület
frissítésétől és a szemantikai elemzéstől. A C# nyelv és a .NET keretrendszer
több eszközzel is támogatja a párhuzamos programozást: az alacsony szintű
`Thread` típustól a magasabb absztrakciós szintű taszkokig.

## Kapocs

- [[concepts/esemalk/csharp-szal-letrehozasa-kezelese]] — a `Thread` típus
  használata új szál indítására
- [[concepts/esemalk/csharp-task-alapok]] — a taszk-alapú aszinkron
  programozás mint magasabb absztrakciós szint
