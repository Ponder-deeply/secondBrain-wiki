---
tags: [concept]
sources: [elte_eva_ea00_csharp.pdf]
derivation: source
updated: 2026-09-12
---

# Vezérlési szerkezetek (C#)

A C# nyelv vezérlési szerkezetei a szekvenciától a bejáró cikluson át
szokásos, C-szerű elemkészletet nyújtanak.

## Tartalom

- **Szekvencia**: a `;` tagolja az utasításokat.
- **Programblokk**: `{ <utasítások> }`
- **Elágazás**: lehet kétágú (`if`), illetve többágú (`switch`); utóbbinál az
  ágakat le kell zárni (`break`, `goto`, `return`).
- **Ciklus**:
  - számláló (`for`), előtesztelő (`while`), utántesztelő (`do … while`)
  - bejáró (egy `IEnumerable` gyűjtemény elemein halad végig):

    ```csharp
    foreach (<deklaráció> in <gyűjtemény>)
        <utasítás>;
    ```

## Kapocs

- [[concepts/esemalk/csharp-tipusok]] — az `IEnumerable` gyűjtemény elemeinek
  típusa a bejáró ciklusban
