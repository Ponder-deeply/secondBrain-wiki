---
tags: [concept]
sources: [elte_eva_ea09_avaloniaui.pdf]
derivation: source
updated: 2026-09-13
---

# Avalonia alkalmazás tulajdonságai és kihelyezés

Az Avalonia UI alkalmazások tulajdonságait és képességeit az *alkalmazás
leíró* (*application manifest*) segítségével írhatjuk le, platformonként
eltérő fájlformátumban.

## Tartalom

Az alkalmazás leíró tartalmazza az alkalmazás nevét, leírását, verzióját és
a fejlesztő adatait, valamint megadja az engedélyeket a rendszerhez és más
alkalmazásokhoz (pl. internet, kamera, pozicionálás, telefonkönyv).

A leírást tartalmazó fájl platformonként más:

- **Android**: `AndroidManifest.xml`
- **Windows**: `Package.appxmanifest`
- **iOS/macOS**: `Info.plist`

A megfelelően konfigurált alkalmazások kihelyezhetők fizikai eszközökre,
illetve elhelyezhetők a platform alkalmazásboltjában is — ehhez az
alkalmazást megfelelő, szintén platformspecifikus aláírással kell ellátni.

## Kapocs

- [[concepts/esemalk/avalonia-bevezetes]] — az Avalonia UI többplatformos
  architektúrája, amelynek a leíró fájlok a platformonkénti eltérését
  tükrözik
- [[concepts/esemalk/avalonia-projekt-felepites]] — a platformfüggő
  projektek, amelyekhez ezek a leíró fájlok tartoznak
- [[subjects/esemalk]]
