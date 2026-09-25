---
tags: [concept, esemalk/winforms-architektura-es-teszteles]
sources: [elte_eva_ea04_winforms_architecture_testing.pdf]
derivation: source
updated: 2026-09-13
---

# Szerelvények és osztálykönyvtárak

A *szerelvény* (**assembly**) a szoftver egy fizikailag is elkülönített
csomagja: a típusok és erőforrások lefordított, felhasználható állománya,
amely az alkalmazás egy komponensét alkotja.

## Tartalom

### Szerelvények

- Az *alkalmazás* (*executable*, `.exe`) egy önállóan futtatható szerelvény.
- Az *osztálykönyvtár* (*class library*, `.dll`) olyan szerelvény, amely
  önmagában nem futtatható, csupán más szerelvényekben felhasználható
  osztályok gyűjteménye — a nyelvi könyvtár (pl. a .NET keretrendszeré) is
  osztálykönyvtárakban helyezkedik el.
- A Visual Studio-ban minden projekt egy külön szerelvényt eredményez; a
  megoldás (*Solution*) fogja össze az egy szoftverhez tartozó
  szerelvényeket (projekteket).

### Miért érdemes szerelvényekre bontani

Az alkalmazás felbontása több szerelvényre (projektre):

- elősegíti az egyes programrészek szeparálását, a függőségek
  korlátozását, a komponensek újrahasznosítását,
- megkönnyíti a csapatmunka felosztását, a keletkezett kódok
  összeintegrálását, tesztelését, publikálását.

A felosztást legcélszerűbb a [[concepts/esemalk/modell-nezet-architektura]]
rétegei és a függőség-befecskendezés mentén elvégezni — lásd
[[concepts/esemalk/retegek-szerelvenyekre-bontasa]] a konkrét mintáért.

### Cross-platform osztálykönyvtárak és a .NET Standard

Osztálykönyvtár létrehozásakor nem csak egy adott keretrendszert (pl. .NET
Framework, .NET Core, Mono) választhatunk célként, hanem *.NET Standard*
osztálykönyvtárat is: Visual Studio 2022-ben a *Class Library* projekttípus,
majd a *.NET Standard* keretrendszerként való kiválasztásával.

Az így létrehozott osztálykönyvtár minden, a .NET Standard adott verziójára
épülő keretrendszerre és platformra fordítható és használható —
jelentősen megkönnyítve a cross-platform alkalmazásfejlesztést. Cserébe csak
a .NET Standard adott verziójában definiált közös API használható; a
megfeleltetés a .NET Standard verziói és a konkrét keretrendszerek (.NET
Core, .NET Framework, Mono, Xamarin.iOS/Mac/Android, Universal Windows
Platform, Unity) verziói között táblázatosan van rögzítve (pl. .NET Standard
2.0 ⇔ .NET Core 2.0, .NET Framework 4.6.1, Mono 5.4).

## Kapocs

- [[concepts/esemalk/csharp-dotnet-platform]] — a .NET platform felépítése,
  .NET Framework vs. .NET Core, .NET Standard
- [[concepts/esemalk/modell-nezet-architektura]] — a rétegek, amelyek mentén
  a szerelvényekre bontás jellemzően történik
- [[concepts/esemalk/retegek-szerelvenyekre-bontasa]] — konkrét példa a
  szerelvényekre bontásra egy modell/nézet/perzisztencia architektúrában
- [[subjects/esemalk]]
