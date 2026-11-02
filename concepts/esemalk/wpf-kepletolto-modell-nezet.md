---
tags: [concept]
sources: [elte_eva_gy07_munkafuzet.pdf]
derivation: source
kind: procedure
element: earth
updated: 2026-10-21
---

# WPF képletöltő: kétrétegű (modell-nézet) alkalmazás

A 7. gyakorlat WPF-ben épít aszinkron képletöltő alkalmazást (`ImageDownloader`): egy weboldal képeit listázza, majd egy külön ablakban megnyitva letölthetővé teszi — kétrétegű modell-nézet architektúrában, eseményvezérelten, reszponzív felülettel.

## Tartalom

### Modell

- `WebImage`: `Url` (`System.Uri`) és `Data` (`byte[]`); a konstruktor triviális, a példányt a `static async Task<WebImage> DownloadAsync(Uri url)` állítja elő: ellenőrzi, hogy az `url` nem `null` és abszolút (`IsAbsoluteUri`), kivételt dob ha nem, majd `HttpClient.GetByteArrayAsync(url)`. Aszinkron konstruktor nem létezik (a konstruktornak a konstruált objektumot kell visszaadnia, nem `Task`-ot), ezért a statikus `DownloadAsync` valójában a **factory** tervezési mintát valósítja meg; a konstruktor `private`/`protected` is lehet.
- `WebPage`: `BaseUrl` (`Uri`), `Images` (`ICollection<WebImage>`, pl. `List`); a konstruktor ellenőrzi az URL-t; `async Task LoadImagesAsync()`:
  1. HTML lekérése (`client.GetAsync` + `ReadAsStringAsync`, vagy `GetStringAsync`);
  2. `HtmlAgilityPack` (NuGet): `HtmlDocument.LoadHtml`, `doc.DocumentNode.SelectNodes("//img")` (XPath); ha nem HTML, `nodes == null`;
  3. minden `<img>`-re: ha nincs `src` attribútum, ugrás; abszolút URL előállítása: `new Uri(src, UriKind.RelativeOrAbsolute)`, ha nem abszolút, `new Uri(BaseUrl, imageUrl)`;
  4. `WebImage.DownloadAsync` `try-catch`-ben (a nem kép vagy nem támogatott formátum kivételét kihagyjuk).
- Események: `ImageLoaded` (egy új kép letöltésekor, átadja a `WebImage`-et) és `LoadProgress` (0–100, a `nodes.Count` előre ismert); a Microsoft konvenciója szerint az argumentum az `EventArgs` leszármazottja.

### Nézet

- `MainWindow`: `DockPanel` (`TextBox` URL-nek és `Button` felül, `StatusBar` alul — `TextBlock` a képek számának és `ProgressBar` —, középen `WrapPanel` a képeknek); aggregálja a `WebPage` modellt (`_model`).
- A letöltés gombjának kezelője: állapotsor nullázása, folyamatjelző láthatóvá (`Visibility`), gomb tiltása (`IsEnabled`), `WrapPanel.Children.Clear()`, új `WebPage`, feliratkozás az eseményeire, `await _model.LoadImagesAsync()`, majd folyamatjelző elrejtése és gomb engedélyezése.
- `ImageLoaded` kezelő: `BitmapImage` memóriabeli létrehozása (`BeginInit`, `StreamSource = new MemoryStream(e.Data)`, `EndInit` — a `BitmapImage` egyszer inicializálható), `Image` vezérlő (100×100, `Source`), `WrapPanel.Children`-hez adás (keret: `Border` + `Margin`), számláló növelése; `LoadProgress` kezelő: a `ProgressBar.Value` beállítása.
- `ImageWindow`: `DockPanel`, `Image` középen, `Button` lent; konstruktora `BitmapImage`-t kap. Mentés: `SaveFileDialog` (`Filter`, `InitialDirectory`, `RestoreDirectory`), `ShowDialog() == true`, majd `PngBitmapEncoder` + `BitmapFrame.Create(...)` + `FileStream` (`FileMode.Create`). A `MainWindow` az `Image.Click`-re `ShowImage`-ben nyitja az ablakot; `window.Owner = this` miatt a főablak bezárásakor az összes képablak bezáródik.

### Megszakítható letöltés

- A `WebPage` kap `CancellationTokenSource` és `CancellationToken` mezőt (a konstruktorban létrehozva) és `CancelLoad()` metódust (`_cancelSource.Cancel()`); a ciklusban minden `<img>` előtt `if (_cancelToken.IsCancellationRequested) break;`; a HTML letöltése is megszakítható: `client.GetAsync(BaseUrl, _cancelToken)`. A már letöltött képek megmaradnak. Lásd [[concepts/esemalk/taszk-megszakitasa-cancellationtoken]].
- A gomb felirata *Letöltés megszakítására* vált; a nézet vagy egy `_isDownloading` logikai változóval dönt, vagy két kezelő közt vált a feliratkozás (a felirat alapján dönteni nem érdemes).

## Kapocs

- [[concepts/esemalk/wpf-kepletolto-mvvm]] — ugyanez az alkalmazás MVVM-ben, változatlan modellel
- [[concepts/esemalk/csharp-async-await]] — `async`/`await`, `HttpClient`
- [[concepts/esemalk/wpf-elemi-grafika]] — `BitmapImage`
- [[concepts/esemalk/wpf-panelek]] — `DockPanel`, `WrapPanel`
- [[concepts/esemalk/esemeny-letrehozasa-kivaltasa]] — a modell eseményei
- [[subjects/esemalk]]
