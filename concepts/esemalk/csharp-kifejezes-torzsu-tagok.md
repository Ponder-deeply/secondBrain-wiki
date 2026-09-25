---
tags: [concept, esemalk/csharp-nyelvi-alapok]
sources: [elte_eva_ea00_csharp.pdf]
derivation: source
updated: 2026-09-12
---

# Kifejezés törzsű tagok (expression body)

A metódusok és tulajdonságok implementációja *kifejezés törzzsel*
(*expression body*) is megadható a szokásos blokk törzs helyett; rövidebb
eljárásoknál ez tömörebb, a funkcionális nyelvekből ismerős szintaxist ad.

## Tartalom

Hagyományos (blokk törzsű) tulajdonság és metódus:

```csharp
struct Rational {
    // mezők ...

    public Int32 Denominator {
        get { return denom; }
        set { denom = (value == 0) ? 1 : value; }
    } // nevező tulajdonsága

    public Double ToDouble() {
        return num / denom;
    } // konvertálás lebegőpontos értékre
}
```

Ugyanez kifejezés törzzsel:

```csharp
struct Rational {
    // mezők ...

    public Int32 Denominator {
        get => denom;
        set => denom = (value == 0) ? 1 : value;
    } // nevező tulajdonsága

    public Double ToDouble() => num / denom;
    // konvertálás lebegőpontos értékre
}
```

A `get`/`set` ág és az egyértékű metódustörzs is helyettesíthető egyetlen,
`=>` utáni kifejezéssel, amennyiben a teljes implementáció egyetlen
kifejezésként megfogalmazható.

## Kapocs

- [[concepts/esemalk/csharp-tulajdonsagok]] — a `get`/`set`/`init` tulajdonság
  blokk törzsű alapformája, amelyet a kifejezés törzs röviden helyettesít
- [[concepts/esemalk/csharp-osztaly-szerkezete]] — a metódusok és
  tulajdonságok helye az osztály szerkezetében
- [[subjects/esemalk]] — a kurzus áttekintése
