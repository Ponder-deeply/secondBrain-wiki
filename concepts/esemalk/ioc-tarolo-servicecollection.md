---
tags: [concept]
sources: [elte_eva_gy04_munkafuzet.pdf]
derivation: source
kind: definition
element: water
updated: 2026-10-21
---

# IoC tároló (`ServiceCollection`) és szolgáltatások élettartama

Az *IoC tároló* (*Inversion of Control container*) olyan komponens, amely lehetővé teszi szolgáltatások megvalósításának dinamikus (futási idejű) betöltését; a .NET-ben a `ServiceCollection` osztály valósítja meg.

## Tartalom

### Jellemzői

- központi regisztráció, amelyet minden programkomponens elérhet;
- a típusokat (elsősorban) **interfész** alapján azonosítja; regisztrációkor megadjuk a szolgáltatás interfészét és a megvalósító típust (vagy példányt);
- a szolgáltatást interfész alapján kérjük le, ekkor példányosul, vagy egy már létező példányt kapunk;
- ha a szolgáltatásnak függősége van, a tároló azt is példányosítja (konstruktor-befecskendezéssel).

### Élettartamok

| Regisztráció | Viselkedés |
|---|---|
| `AddTransient` | minden kérésnél új példány |
| `AddSingleton` | egyetlen példány, minden kérésre ugyanaz |
| `AddScoped` | hatókörön (*scope*) belül ugyanaz a példány; jellemzően ASP.NET Core-ban, ahol minden oldalbetöltéshez hatókör jön létre |

### Használat (DocuStat példa)

```csharp
ServiceCollection services = new ServiceCollection();
// regisztráció típusokkal
services.AddSingleton<IDocumentStatistics, DocumentStatistics>();
// regisztráció példánnyal
services.AddSingleton<IFileManager>(fileManager);
using ServiceProvider serviceProvider = services.BuildServiceProvider();
IDocumentStatistics stat =
    serviceProvider.GetRequiredService<IDocumentStatistics>();
```

A regisztrált osztályt nem kell manuálisan példányosítani: a `GetRequiredService<T>()` létrehozza, és a függőségeit (itt az `IFileManager`-t) a konstruktoron át automatikusan befecskendezi. A gyakorlaton csak a konzolos projekt használja a tárolót.

## Kapocs

- [[concepts/esemalk/fuggoseg-befecskendezes]] — a befecskendezés alapja, amelyet a tároló automatizál
- [[concepts/esemalk/docustat-perzisztencia-filemanager]] — a példa kontextusa
- [[concepts/esemalk/wpf-kornyezet-fuggosegkezeles]] — az alkalmazáskörnyezet mint IoC-komponens
- [[subjects/esemalk]]
