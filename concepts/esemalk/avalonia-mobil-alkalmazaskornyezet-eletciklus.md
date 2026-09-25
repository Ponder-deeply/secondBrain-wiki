---
tags: [concept, esemalk/avaloniaui-halado-temak]
sources: [elte_eva_ea10_avaloniaui_complex.pdf]
derivation: source
updated: 2026-09-13
---

# Avalonia UI mobil alkalmazáskörnyezet és életciklus

A mobil platformokon futó Avalonia UI-alkalmazások egy zárt (sandboxolt)
környezetben futnak, és más életciklust követnek, mint az asztali
alkalmazások: a futás alatti és a terminált állapot mellett megjelenik a
felfüggesztett állapot is, amelyet a keretrendszer egységesen kezel.

## Tartalom

### Alkalmazáskörnyezet (sandbox)

Az alkalmazások egy biztonságos környezetben futnak:

- nem férhetnek hozzá más alkalmazások adataihoz
- csak korlátozott módon, és csak engedéllyel férhetnek hozzá a rendszer
  adataihoz (pl. fájlrendszer)
- az eszközöket (pl. kamera, GPS) is csak engedéllyel használhatják, amelyet
  az alkalmazás leírója (*application manifest*) deklarál

Mindegyik alkalmazás számára rendelkezésre áll egy lokális könyvtár, amely
csak az alkalmazás saját fájljait tárolja; ennek eléréséhez nem szükséges
külön jogosultság egyik támogatott platformon sem, és az alkalmazás
törlésekor a hozzá tartozó adatok is törlődnek.

### Alkalmazások életciklusa

A mobil alkalmazások más életciklusban futnak, mint az asztali
alkalmazások: a *futás alatt* (running) és a *terminált* (not running)
állapotok mellett megjelenik a *felfüggesztett* (suspended) állapot is,
amely akkor lép életbe, ha az alkalmazás a háttérbe (vagy a gép alvó
állapotba) kerül; célja a takarékosság.

```
leállítva --(aktiválás)--> futás alatt --(felfüggesztés)--> felfüggesztve
felfüggesztve --(folytatás)--> futás alatt
felfüggesztve --(leállítás)--> leállítva
```

A felfüggesztés célja az erőforrásokkal való takarékoskodás: a fejlesztőnek
törekednie kell rá, hogy felfüggesztett állapotban az alkalmazás minél
kevesebb erőforrást igényeljen — a futó tevékenységeket célszerű leállítani,
az adatokat pedig perzisztálni. A rendszer úgy is dönthet (pl. ha kevés a
memória), hogy a felfüggesztett alkalmazást leállítja, majd újraindítja, ha
a felhasználó visszavált rá; célszerű, hogy a felhasználó ennek ellenére
olyan állapotban kapja vissza az alkalmazást, amelyben hagyta — ezért az
állapot eltárolását felfüggesztéskor kell elvégezni.

### Egységes életciklus-kezelés Avalonia UI-ban

Az Avalonia UI keretrendszerű mobil alkalmazások egységes életciklus-
kezeléssel rendelkeznek: az `App` osztály `OnFrameworkInitializationCompleted`
metódusát felüldefiniálva, eseménykezelőkkel adható meg az életciklus-
váltáskor végrehajtandó tevékenység (`Activated`, `Deactivated`), minden
platformra (Android, iOS, macOS) egységesen:

```csharp
if (Application.Current
        .TryGetFeature<IActivatableLifetime>()
        is { } activatableLifetime)
{
    activatableLifetime.Activated += (sender, args) =>
    {
        // alkalmazás aktív
    };
    activatableLifetime.Deactivated += (sender, args) =>
    {
        // alkalmazás inaktív
    };
}
```

## Kapocs

- [[concepts/esemalk/avalonia-eletciklus-kezeles]] — az asztali (Windows/
  Linux) alkalmazás-életciklus kezelése (`Startup`/`Exit`); ez a lap a
  mobil (Android/iOS) oldali életciklust (futás alatt/felfüggesztve/
  leállítva) írja le
- [[concepts/esemalk/avalonia-eszkozfuggo-viselkedes]] — az eszköztípus
  lekérdezése és a platformfüggő viselkedés, amely a mobil
  alkalmazáskörnyezethez szorosan kapcsolódik
- [[concepts/esemalk/idisposable-eroforras-felszabaditasa]] — az
  erőforrás-felszabadítás elve C#-ban, amely a felfüggesztéskori
  takarékossághoz hasonló megfontolást igényel
- [[concepts/esemalk/avalonia-idozites]] — a háttérszálon futó időzítők és a
  UI-szálra való szinkronizálás, amely a felfüggesztett állapotban futó
  tevékenységek leállításával is összefügg
