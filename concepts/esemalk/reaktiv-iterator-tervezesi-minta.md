---
tags: [concept]
sources: [elte_eva_ea11_reactive.pdf]
derivation: source
updated: 2026-09-13
---

# Iterator tervezési minta

A GoF (Gang-of-Four: Erich Gamma, Richard Helm, Ralph Johnson, John
Vlissides — *Design Patterns: Elements of Reusable Object-Oriented
Software*, 1994) egyik tervezési mintája, amely egy gyűjtemény elemeinek
sorozatos, a belső ábrázolástól független bejárását teszi lehetővé.

## Tartalom

Egy tervezési minta (Martin Fowler megfogalmazásában) "*egy ötlet, amely
egy gyakorlati kontextusban hasznosnak bizonyult, és valószínűleg más
kontextusokban is hasznos lesz*", illetve "*a tervezési minták egy
kiindulópontot jelentenek, nem egy végcélt*".

### Szerkezet

Az *Iterator* minta szereplői:

- `Aggregate` — a bejárható gyűjtemény absztrakciója,
  `CreateIterator()` gyártó metódussal
- `ConcreteAggregate` — a konkrét gyűjtemény, amely visszaad egy
  `ConcreteIterator`-t (`return new ConcreteIterator(this)`)
- `Iterator` — a bejárás interfésze: `First()`, `Next()`, `IsDone()`,
  `CurrentItem()`
- `ConcreteIterator` — a konkrét bejáró, amely a `ConcreteAggregate`
  belső állapotát ismeri

### C#-beli megvalósítás

A minta a .NET standard szintjén az `IEnumerable<T>`/`IEnumerator<T>`
típuspárral jelenik meg (egyszerűsített alak):

```csharp
public interface IEnumerable<out T>
{
    IEnumerator<T> GetEnumerator();
}

public interface IEnumerator<out T>
{
    T Current { get; }
    bool MoveNext();
    void Reset();
}
```

Az *Iterator* és az *Observer* tervezési minta gyakran együtt kerül elő,
bár az eredeti GoF szerzők nem feltétlenül gondoltak a két minta együttes
használatára — a kombinációjuk adja a megfigyelhető felsorolók
(`Observable`) modelljét, lásd
[[concepts/esemalk/rx-observable-alapok]].

## Kapocs

- [[concepts/esemalk/reaktiv-observer-tervezesi-minta]] — a másik GoF
  minta, amellyel kombinálva a megfigyelhető felsorolók adódnak
- [[concepts/esemalk/rx-observable-alapok]] — az `IObservable<T>` modell,
  amely az Iterator és az Observer minta kombinációja
- [[concepts/esemalk/reaktiv-programozas-alapjai]] — a reaktív
  programozás áttekintése
- [[concepts/esemalk/csharp-linq]] — az `IEnumerable<T>`-re épülő LINQ
  lekérdezések
