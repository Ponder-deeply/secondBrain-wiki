---
tags: [concept, esemalk/reaktiv-programozas]
sources: [elte_eva_ea11_reactive.pdf]
derivation: source
updated: 2026-09-13
---

# Szimulált szenzoradat feldolgozása Rx.NET-tel

Egy összefüggő példa, amely bemutatja megfigyelhető felsorolók létrehozását, operátorokkal (`Where`, `Select`, `GroupBy`) való feldolgozását, majd a csoportosított eredményre való feliratkozást.

## Tartalom

### Megfigyelhető felsoroló létrehozása

Az `Observable.Interval` egy időzített ütemben (itt 250 ms-onként) bocsát ki elemeket, amelyeket a `Select` operátor szimulált szenzorleolvasássá alakít:

```csharp
var sensorStream = Observable
    .Interval(TimeSpan.FromMilliseconds(250))
    .Select(t => new SensorReading
    {
        SensorId = t % 3, // 3 szenzor
        Celsius = Random.Shared.Next(-10, 60),
        Timestamp = DateTime.UtcNow
    });
```

ahol:

```csharp
public class SensorReading
{
    public long SensorId { get; set; }
    public int Celsius { get; set; }
    public DateTime Timestamp { get; set; }
}
```

### Feldolgozás operátorokkal

A `Where` szűri, a `Select` átalakítja, a `GroupBy` pedig szenzoronként csoportosítja az adatfolyamot:

```csharp
var processedStream = sensorStream
    .Where(r => r.Celsius >= -5 && r.Celsius <= 50)
    .Select(r => new ProcessedReading
    {
        SensorId = r.SensorId,
        Celsius = r.Celsius,
        Fahrenheit = r.Celsius * 9.0 / 5.0 + 32,
        Timestamp = r.Timestamp,
        Status = r.Celsius > 35 ? "WARNING" : "OK"
    })
    .GroupBy(r => r.SensorId);
```

ahol:

```csharp
public class ProcessedReading
{
    public long SensorId { get; set; }
    public int Celsius { get; set; }
    public double Fahrenheit { get; set; }
    public DateTime Timestamp { get; set; }
    public string Status { get; set; }
}
```

A `GroupBy` eredménye megfigyelhető felsorolók megfigyelhető felsorolója: minden csoport (szenzoronként) maga is egy megfigyelhető felsoroló.

### Feliratkozás a csoportosított adatfolyamra

```csharp
processedStream.Subscribe(group => {
    Console.WriteLine(
        $"New group: Sensor {group.Key}");

    group.Subscribe(reading =>
    {
        Console.WriteLine(
            $"Sensor {reading.SensorId} | " +
            $"{reading.Celsius}°C / " +
            $"{reading.Fahrenheit:F1}°F | " +
            $"{reading.Status} | " +
            $"{reading.Timestamp:HH:mm:ss}"
        );
    });
});
```

A külső `Subscribe` minden új szenzorcsoport megjelenésekor fut le, a belső `Subscribe` pedig az adott csoporton belüli minden egyes leolvasásra.

## Kapocs

- [[concepts/esemalk/reaktiv-feliratkozas]] — a `Subscribe()` eljárás és az `onNext`/`onError`/`onSuccess` callback-ek
- [[concepts/esemalk/reaktiv-multicasting]] — mi történik, ha ugyanerre a `sensorStream`-re több helyen iratkozunk fel
- [[concepts/esemalk/rx-observable-alapok]] — az `Observable.Interval`/`Observable.Create` gyártó műveletek
- [[concepts/esemalk/rx-operatorok]] — a `Where`/`Select`/`GroupBy` operátorok általános leírása
- [[subjects/esemalk]] — a kurzus áttekintése
