---
tags: [concept]
sources: [elte_eva_mintazh_winforms.pdf, elte_eva_mintazh_winforms_2.pdf, elte_eva_mintazh_wpf.pdf, elte_eva_mintazh_wpf_2.pdf, elte_eva_mintazh_avalonia.pdf, elte_eva_mintazh_avalonia_2.pdf]
derivation: source
kind: overview
element: earth
updated: 2026-10-21
---

# Géptermi zárthelyi mintafeladatok

A géptermi zárthelyi mintafeladatai egy-egy játékot vagy alkalmazást írnak le, részfeladatokra bontva: a megoldást ZIP-ben kell feltölteni a TMS-be (a `bin`, `obj`, esetleg `.vs` könyvtárak kivételével). Mindegyik feladat egy keretrendszerhez és architektúrához kötött, és a részfeladatok fokozatosan építkeznek: a megjelenítéstől a szabályokon és a játék végén át a mentésig, ill. a környezeti követelményig.

## Tartalom

### Áttekintés

| Minta | Keretrendszer, architektúra | Feladat | Dátum |
|---|---|---|---|
| BlockDocu | WinForms, MV (kétrétegű) | alakzatok elhelyezése $4\times 4$-es táblán | 2021. 01. 07. |
| Gerrymandering | WinForms, MV | választókörzetek kijelölése $3\times 6$-os városban | 2024. 12. 19. |
| Támadás | WPF, MVVM | kétszemélyes figurás játék $n\times n$ táblán | 2021. 01. 07. |
| Dáma | WPF, MVVM | egyszerűsített dáma | 2024. 01. 08. |
| Invázió | Avalonia, MVVM, mobil | várvédő játék valós időben | 2024. 12. 02. |
| Huszárpárbaj | Avalonia, MVVM, cross-platform | lovak $L$ alakú lépései, mezőfoglalás | 2025. 01. 13. |

### WinForms mintafeladatok

**BlockDocu** — négyféle alakzat: két 2 blokkos (vízszintes, függőleges) és két 3 blokkos (L alakú és tükörképe). Minden körben véletlenszerű alakzat; a játékos az alakzat bal felső blokkjának helyét jelöli meg; az alakzat nem lóghat ki és nem fedhet le már lerakott alakzatot; teli sor vagy oszlop újra üressé válik.
1. Kétrétegű MV architektúra; üres $4\times 4$-es tábla és külön $2\times 2$-es keretben a kisorsolt alakzat; elhelyezés kék színezéssel, kilógás esetén ismétlés.
2. Alakzatok egymás után; csupa fehér blokkra helyezés ellenőrzése; teli sor/oszlop felismerése és fehérre színezése.
3. Annak felismerése, ha az alakzat nem tehető fel sehova; kilépés vagy új játék.
4. Pont minden sikeres elhelyezés után, kijelezve játék közben és a végén.
5. Játékállás mentése és betöltése.

**Gerrymandering** — Pirézia $3\times 6$-os, 18 kerületből álló város; minden kerület Zöld (G) vagy Lila (P, a Kormányzó) pártot támogat; 3–3 összefüggő kerületből álló körzetek (átlósan nem összefüggő); cél: kétharmados győzelem kisebbségi támogatás ellenére.
- Térkép megjelenítése, 3 összefüggő kerület kijelölése egy körzetként, érvénytelen kijelölés tiltása; új játék bármikor.
- Csak az aktuális körzet újrakezdése; mind a 6 körzet után kijelzés, hogy a Kormányzó győz-e (a körzetek többségében).
- Város kiválasztása, a térkép fájlból (első sor a méretek, majd a kerületek G/P kódja); a betöltést a modell vagy külön perzisztencia réteg végzi.
- Kijelölés bal egérgomb lenyomva tartásával az egér kerületek fölé húzásával.

### WPF mintafeladatok

**Támadás** — $n\times n$-es tábla, kezdetben 4–4 figura két ellentétes sarokban; nyolc szomszédos irányba lépés és átlós ütés; a figurákkal rögzített sorrendben lehet lépni (1., 2., ... 4., majd ismét 1.); cél: egy figura eljut a szemközti sarokba.
1. $6\times 6$-os tábla, kezdőállással.
2. Felváltva lépés a soron következő bábuval (elég a célmező kijelölése), csak szabályos lépés; kijelzés, melyik játékos és hányas figura következik.
3. Szabályos ütés; leütött bábu nem kerülhet újra sorra.
4. A játék végének felismerése, győztes kijelzése, automatikus új játék.
5. Táblaméret választása ($4\times 4$, $6\times 6$, $8\times 8$), új játék bármikor.

**Dáma** — egyszerűsített szabályok: egy mezőt lép előre átlósan vagy ütéssel átugrik egy ellenséges figurát, ha mögötte nincs másik figura.
- $8\times 8$-as tábla, kezdőállás; váltott lépések, hibaüzenetek szabálytalan lépésre; vesztes, akinek nincs figurája vagy szabályos lépése — felugró ablak.
- **Ütéskényszer**: ha van ütési lehetőség, ütni kell; hibaüzenet és a szabályosan léphető figurák jelzése a celláknál.
- Az utolsó sorba lépő figura dámává változik, amely hátra is lép és üt; megkülönböztető jelölés.
- Sakktábla minta a cellák hátterének színezésével, a figurák képekkel.

### Avalonia mintafeladatok

**Invázió** — a vár fala a pálya egyik szélén; az ellenségek az átellenes oldalról egyenesen a fal felé tartanak; a falat elérő ellenség kiesik, a vár egy életet veszít (3 élet); katonák: kezdetben 2, minden harmadik megölt ellenségért újabb vásárolható; ütközéskor mindkettő meghal, elhaladáskor csak az ellenfél hal meg; a katonák nem mozdulnak.
1. Fix méretű pálya vezérlőkkel vagy elemi grafikával; látszik a vár élete, az eltelt idő és a lerakható katonák száma.
2. Időnként véletlen mennyiségű ellenség véletlen pozíciókban, valós időben haladva.
3. Katona lehelyezése üres pozícióra; az interakciók implementálása.
4. Szünet, folytatás, új játék vereség után kilépés nélkül; az OS általi felfüggesztéskor automatikus szünet.
5. Mentés és betöltés; felfüggesztés/leállítás esetén az utolsó állapot megőrzése és visszatöltése.

**Huszárpárbaj** — két játékos lovakkal felváltva lép $L$ alakban, minden lépéssel egy mezőt foglal el; foglalt mezőre nem léphet; akinek nincs legális lépése, veszít.
- (2) $8\times 8$-as tábla, a lovak a jobb alsó és bal felső sarokban; szürke alapszín, az 1. játékos mezői fehérek, a 2.-é feketék (a kezdőmező is); érvénytelen lépés tiltása; új játék bármikor; elég asztali alkalmazásként.
- (3) Kijelzés, kinek a köre; a lehetséges lépések keretének színezése: zöld, ha több van; sárga, ha pontosan 2; piros, ha csak 1; ha nincs lépés, felugró ablakkal a vége és a nyertes; lovak képekkel.
- (4) Android: felfüggesztéskor a játékállás perzisztálása, aktiváláskor automatikus visszatöltés.
- (5) Négylovas játék (mindkét játékosnak két ló, a másik két sarokban); ha egy mezőre mindkét ló léphet, a játékos dönthessen; az új játék mindig ugyanannyi lóval indul, mint az előző.

### Közös minták

- A modell eseményeket küld a nézetnek (nézetmodellnek); játékállás-mentés perzisztencia rétegben; időzítő a modellben ([[concepts/esemalk/winforms-idozito-parhuzamositas]], [[concepts/esemalk/wpf-idozites]], [[concepts/esemalk/avalonia-idozites]]).
- Mobil követelménynél az alkalmazás életciklusát az `App` osztály kezeli ([[concepts/esemalk/avalonia-mobil-alkalmazaskornyezet-eletciklus]]).
- Az $n\times n$-es dinamikus mezők WPF-ben/Avalonián a [[concepts/esemalk/wpf-itemscontrol-elrendezes-dinamikus-mezok]] mintával, WinForms-ban [[concepts/esemalk/winforms-dinamikus-vezerlok]]-kal építhetők.
- A számozás az eredeti kiírásban a 2–5 részfeladatoknál néhol a 2. ponttól kezdődik (az 1. részfeladat a dokumentumban hiányzik: Gerrymandering, Dáma, Huszárpárbaj).

## Kapocs

- [[concepts/esemalk/beadando-2-avalonia-feladatkiiras]] — a beadandók hasonló szerkezetű feladatai
- [[concepts/esemalk/modell-nezet-architektura]] — az MV architektúra a WinForms mintákhoz
- [[concepts/esemalk/wpf-mvvm-alapok]] — az MVVM architektúra a WPF és Avalonia mintákhoz
- [[concepts/esemalk/winforms-eger-esemenyek]] — egérhúzásos kijelölés (Gerrymandering 5. részfeladat)
- [[subjects/esemalk]]
