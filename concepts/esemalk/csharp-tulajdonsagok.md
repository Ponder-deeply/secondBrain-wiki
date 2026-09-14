---
tags: [concept]
sources: [elte_eva_ea00_csharp.pdf]
derivation: source
updated: 2026-09-12
---

# C# tulajdonságok (properties)

A tulajdonság (`property`) a programozó számára könnyítés a lekérdező és író
műveletek absztrakciójára: kívülről mezőnek tűnik, belülről metódusokkal
(`get`/`set`/`init`) van implementálva.

## Tartalom

**Alapforma.** Az író tulajdonság a `value` pszeudováltozón keresztül veszi
át az értéket:

```csharp
class Rational {
    // ...
    int getDenominator() { return denom; }
    void setDenominator(int value) {
        denom = (value == 0) ? 1 : value;
    }
    // publikus lekérdező és beállító művelet
}
```

C#-ban ugyanez tulajdonságként:

```csharp
struct Rational {
    // ...
    public Int32 Denominator {
        get { return denom; }
        set { denom = (value == 0) ? 1 : value; }
    } // változóhoz tartozó publikus tulajdonság
}

Rational r = new Rational(10, 5);
r.Denominator = 10; // a 10 kerül a value-ba
```

Külön definiálható csak lekérdező, csak beállító művelet is, és a
láthatósági szintjük is lehet eltérő (pl. publikus `get`, `private set`).

**Automatikus tulajdonságok (auto-property).** Ha a getter és setter
működése triviális, a kódunk könnyen repetitívvé válhat. Ilyenkor a
tulajdonsággal automatikusan létrehozható a mögöttes mező is:

```csharp
struct MyClass {
    private Int32 data;
    public Int32 Data {
        get { return data; }
        private set { data = value; }
    }
}
```

egyenértékű ezzel:

```csharp
struct MyClass {
    public Int32 Data { get; private set; }
}
```

**`init` beállítók (C# 9).** A `set` helyett használható az `init` ág is,
ekkor az érték beállítása csak az objektum inicializálása során lehetséges:

```csharp
struct MyClass {
    private Int32 data;
    public Int32 Data {
        get { return data; }
        init { data = value; }
    }
}

var obj = new MyClass { Data = 42 }; // ok
obj.Data = 100; // fordítási hiba
```

## Kapocs

- [[concepts/esemalk/csharp-osztaly-szerkezete]] — az osztályok általános szintaxisa, amelynek a tulajdonság is része
- [[concepts/esemalk/csharp-ertek-referencia-osztalyok]] — a `Rational` példa érték- és referencia szerinti kezelése
- [[concepts/esemalk/csharp-kifejezes-torzsu-tagok]] — a `get`/`set` ág rövidebb, kifejezés törzsű megadása
- [[subjects/esemalk]] — a kurzus áttekintése
