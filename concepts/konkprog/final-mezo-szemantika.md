---
tags: [concept]
sources: [Java-Language-Specification-SE-21.pdf]
derivation: source
kind: theorem
element: air
updated: 2026-10-23
---

# A final mezők szemantikája a memóriamodellben

A `final` mező a konstruktor végén „befagy”; ha egy másik szál az objektumot csak a konstruktor befejezése után látja, a `final` mezők helyes értékét garantáltan látja szinkronizáció nélkül is.

## Tartalom

### Használati modell (JLS §17.5)

A `final` mezőket az objektum **konstruktorában** kell beállítani, és az épülő objektumra mutató referenciát nem szabad olyan helyre írni, ahol másik szál a konstruktor vége előtt láthatja. Ha ez teljesül, a másik szál mindig a helyesen felépített `final` mezőket látja, valamint a mezők által hivatkozott objektumok/tömbök legalább olyan friss állapotát. Ezzel szinkronizáció nélkül is megvalósíthatók szálbiztos **immutábilis** objektumok.

### Példák

- 17.5-1: `final int x = 3; int y = 4;` – a `reader` biztosan 3-at lát az `f.x`-ben, de `f.y` lehet 0.
- 17.5-2: a `String` mezői `final`-ok, ezért akkor sem látható egy `String` félkész állapotban, ha adatversennyel adják át – a biztonsági funkciók erre támaszkodnak.

### Formális váz (§17.5.1)

A **freeze** akció a konstruktor kilépésekor történik (beágyazott konstruktorhívásnál a meghívott konstruktor végén). Két további részrendezés befolyásolja az olvasásokat: a dereferencia-lánc `dereferences()` és a memórialánc `mc()`. A happens-before nem tranzitív e rendezésekkel.

### Mellékesetek

- **Olvasás építés közben** (§17.5.2): az építő szál a konstruktoron belül a szokásos happens-before szerint látja, mielőtt/miután beállította.
- **Utólagos módosítás** (§17.5.3): pl. reflexióval; az ilyen módosítás után is freeze történik, de a konstans kifejezéssel inicializált `final` mező változása nem észlelhető (fordításkor behelyettesítődik), és a fordító átrendezheti az olvasásokat (a példában `new A().f()` lehet −1, 0 vagy 1). A *final-field-safe context* szálkészletek (executor) esetén lehet hasznos.
- **Írásvédett mezők** (§17.5.4): `System.in/out/err` `static final`, mégis módosíthatók (`System.setIn` stb.), ezért normál mezőként kezelendők.

## Kapocs

- [[concepts/konkprog/java-memoriamodell]] — happens-before
- [[concepts/konkprog/volatile-mezo]] — másik láthatósági eszköz
