---
tags: [concept, esemalk/csharp-nyelvi-alapok]
sources: [elte_eva_ea00_csharp.pdf]
derivation: source
updated: 2026-09-12
---

# C# öröklődés

A .NET keretrendszerben az osztályok egy teljes származtatási hierarchiában
vannak; az öröklődés révén a referencia osztályok (`class`) felüldefiniálható
és elrejthető tagokkal bővíthetők.

## Tartalom

**Az öröklődési hierarchia.** Minden osztály őse az `Object`, így megkapja
annak műveleteit (pl. `Equals(...)`, `GetHashCode()`, `ToString()`). Csak
egyszeres öröklődés van, az ősosztály konstruktora és destruktora
automatikusan meghívódik. Az osztály saját tagjait a `this` kulcsszóval, az
ős tagjait (beleértve a konstruktort) a `base` kulcsszóval érhetjük el.
Polimorfizmus során lehetőségünk van a típusazonosításra (`is`), valamint az
explicit, illetve biztonságos típuskonverzióra (`as`).

```csharp
class BaseClass /* : Object */ { // ősosztály
    public Int32 Value;
    public BaseClass(Int32 v) { value = v; }
}

class DerivedClass : BaseClass { // leszármazott
    public DerivedClass(Int32 v) : base(v) { }
        // ős konstruktorának meghívása
}

Object o = new DerivedClass(1); // polimorfizmus
if (o is BaseClass)             // típusazonosítás, konverzió
    Console.WriteLine((o as BaseClass).Value)
```

**Felüldefiniálás és elrejtés.** Öröklődés során a műveletek és
tulajdonságok felüldefiniálhatóak, illetve elrejthetőek:

- felüldefiniálni csak a virtuális (`virtual`) és absztrakt (`abstract`)
  műveleteket, tulajdonságokat lehet,
- a felüldefiniálást is jelölni kell (`override`),
- a felüldefiniálhatóság lezárható (`sealed`),
- absztrakt metódusok törzs nélküliek, absztrakt tulajdonságoknál csak azt
  kell jelezni, hogy lekérdezésre vagy értékadásra szolgálnak-e,
- az ős működése elrejthető (`new`), ekkor polimorfizmus esetén a statikus
  típus (jellemzően az ős) művelete érvényesül — szemben a `virtual`/
  `override` páros dinamikus kötésével.

```csharp
class BaseClass { // ősosztály
    public void StandardMethod() {
        // lezárt (nem felüldefiniálható) művelet
        Console.WriteLine("BaseStandard");
    }
    public virtual void VirtualMethod() {
        // virtuális (felüldefiniálható) művelet
        Console.WriteLine("BaseVirtual");
    }
}
```

## Kapocs

- [[concepts/esemalk/csharp-osztaly-szerkezete]] — az osztályok általános szintaxisa, amelyre az öröklődés épül
- [[concepts/esemalk/csharp-ertek-referencia-osztalyok]] — csak a referencia osztályok szerepelhetnek öröklődésben
- [[subjects/esemalk]] — a kurzus áttekintése
