---
tags: [concept]
sources: [elte_eva_ea00_csharp.pdf]
derivation: source
kind: procedure
element: earth
updated: 2026-09-30
---

# C# megjegyzések, előfordítási direktívák és attribútumok

A C# kétféle megjegyzést különböztet meg: az egyszerű megjegyzések fordításkor
törlődnek, a *dokumentációs megjegyzések* viszont fordításkor egy külön XML
dokumentációs fájlba gyűjthetők ki (a lefordított szerelvénybe nem kerülnek
bele), és onnan utólag feldolgozhatók (pl. súgó, dokumentációgenerálás).

## Tartalom

**Egyszerű megjegyzések.** Sor végéig tartó (`// megjegyzés`), vagy
tetszőleges határok között (`/* megjegyzés */`).

**Dokumentációs megjegyzések.** Osztályok és tagjaik deklarációjánál
használhatók; céljuk az automatikus dokumentálás elősegítése és a
fejlesztőkörnyezetben azonnali segítség megjelenítése. A `///` jeltől a sor
végéig tart, belül XML blokkok adhatók meg, amelyek meghatározzák az
információ jelentését (pl. `<summary>`, `<remarks>`, `<param>`).

```csharp
/// <summary>
/// Racionális szám típusa.
/// </summary>
/// <remarks>Két egész szám hányadosa.</remarks>
struct Rational {
    ...
    /// <summary>
    /// Racionális szám példányosítása.
    /// </summary>
    /// <param name="n">Számláló.</param>
    /// <param name="d">Nevező.</param>
    public Rational(Int32 n, Int32 d) { ... }
    ...
}
```

### Előfordítási direktívák és régiók

A nyelv *előfordítási direktívákat* tartalmaz, amelyek előzetesen kerülnek
feldolgozásra, még a tényleges fordítás előtt.

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

### Attribútumok

Az *attribútumok* (`attribute`) olyan speciális osztályok, amelyek elsősorban
a virtuális gépnek (CLR) szolgálnak információkat (úgynevezett *metaadat*okat),
kiegészítve a kód deklarációit.

Az attribútumok segítségre lehetnek a kód kezelésében, *reflexió*
segítségével kezelhetőek (lekérdezhetők futásidőben). A deklaráció elé,
szögletes zárójelben adjuk meg őket, alkalmazhatóak osztályra, metódusra,
paraméterre és más nyelvi elemekre is.

```csharp
[Serializable] // attribútumok
[ComVisible(true)]
class SomeClass { ... }
```

## Kapocs

- [[concepts/esemalk/csharp-osztaly-szerkezete]] — dokumentációs
  megjegyzések osztályok és tagjaik deklarációjánál
- [[subjects/esemalk]] — a kurzus áttekintése
