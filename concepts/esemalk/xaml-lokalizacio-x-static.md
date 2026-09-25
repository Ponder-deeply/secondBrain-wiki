---
tags: [concept, esemalk/lokalizacio]
sources: [elte_eva_ea12_localization.pdf]
derivation: source
updated: 2026-09-13
---

# Lokalizált erőforrások megjelenítése (WinForms tervező, WPF/Avalonia XAML)

A lokalizált szöveges erőforrások betöltése a felhasznált UI-keretrendszertől
függően más-más módon jelenik meg: a WinForms tervezőfelülete beépített
támogatást ad, míg a WPF és az Avalonia esetén a XAML-ból közvetlenül, az
`x:Static` hivatkozással érhetők el.

## Tartalom

### WinForms — tervezőfelületi támogatás

Windows Forms alkalmazások esetén a lokalizációt a Visual Studio grafikus
tervezőfelülete is támogatja:

- a lokalizáció az ablakok (*formok*) szintjén engedélyezhető a
  `Localizable` tulajdonsággal, majd a `Language` tulajdonsággal adhatók meg
  a támogatott nyelvek
- a Visual Studio automatikusan elkészíti az ablakhoz tartozó lokalizált
  erőforrás-állományokat
- a felületi vezérlők tulajdonságainak kitöltésekor a megfelelő
  erőforrás-állomány frissítésre kerül
- a `Designer.cs` állományba olyan C# kód generálódik, amely a `.resx`
  erőforrás-állományokból tölti be az értékeket

### WPF/Avalonia — `x:Static` hivatkozás XAML-ban

WPF és Avalonia alkalmazások esetén, ha a lokalizációt nem háttérkódban,
hanem a grafikus felületen (XAML-ban) szeretnénk betölteni, a statikus
erőforrásokat az `x:Static` hivatkozással tölthetjük be:

1. az ablakon vagy oldalon definiálunk egy névtér kapcsolást a szöveges
   erőforrásaink helyére:
   ```xml
   <Window
       ...
       xmlns:resx="clr-namespace:MyApp.Resources">
   ```
2. ezt felhasználva tölthető be a kívánt erőforrás:
   ```xml
   <Label Text="{x:Static resx:AppText.Test}" />
   ```

### Példák

A lokalizáció elvét egy Tic-Tac-Toe és egy számológép példaalkalmazáson
keresztül mutatja be a forrás: a szövegeket erőforrásban (`ApplicationText`)
tárolják, amelyből alapértelmezett és magyar változatot készítenek; ezeket az
alkalmazás környezeti rétegében (`App`) és a nézetben (`MainView`) töltik be.
Mindkét alkalmazást Windows Forms, WPF és Avalonia UI nézettel is
megvalósítják, és mindhárom változat felületét lokalizálják — az Avalonia UI
változatnál asztali és mobil (Android) környezetre egyaránt, ahol a tizedes
elválasztót a nézetmodell közvetlenül a nyelvi környezettől kérdezi le.

## Kapocs

- [[concepts/esemalk/dotnet-lokalizacio-kulturak]] — a `CultureInfo` és a
  kultúra-specifikus `.resx` fájlok háttérkódból történő elérése, amire ez a
  lap épül
- [[concepts/esemalk/wpf-eroforrasok-alapjai]] — a WPF erőforrás-fogalom
  (`Resources`, `x:Key`/`StaticResource`) általánosan, amelynek a
  lokalizációs `x:Static` hivatkozás egy speciális esete
- [[concepts/esemalk/wpf-xaml-nyelv]] — a XAML nyelv, amelyben az `x:Static`
  hivatkozás elhelyezkedik
- [[concepts/esemalk/avalonia-xaml-felulet]] — az Avalonia `.axaml`
  felületleírás, ahol ugyanez a hivatkozási mód használható
- [[subjects/esemalk]] — a kurzus áttekintése
