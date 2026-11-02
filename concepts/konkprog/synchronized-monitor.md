---
tags: [concept]
sources: [Java-Language-Specification-SE-21.pdf, konkprog-canvas-feladat-1-szinkronizalt-metodusok.md, konkprog-canvas-feladat-2-szinkronizalt-blokkok.md, konkprog-canvas-feladat-2-gyakorlo-feladat-szinkronizalt-metodusok-a-banyaszok-es-ep.md, konkprog-canvas-feladat-3-gyakorlo-feladat-szinkronizalt-blokkok-a-banyaszok-es-epit.md]
derivation: source
kind: definition
element: earth
updated: 2026-10-23
---

# A synchronized kulcsszó és a monitor

Minden Java-objektumhoz tartozik egy monitor; a `synchronized` metódus vagy blokk a végrehajtás idejére zárolja azt, így egyszerre csak egy szál futtathatja az ugyanazon monitorra szinkronizált kódot.

## Tartalom

### Monitor és zár (JLS §17.1)

Az objektumhoz tartozó monitort egy szál zárolni (lock) és feloldani (unlock) tudja; egyszerre egy szál tarthatja. A többi, zárolni próbáló szál blokkolódik. Egy szál ugyanazt a monitort **többször is** zárolhatja (reentráns), minden unlock egy lockot von vissza. A JLS példája kétszeres egymásba ágyazott `synchronized(t)`, amely holtpontot okozna, ha ez nem lenne megengedett.

### synchronized metódus (§8.4.3.6)

Végrehajtás előtt megszerzi a monitort: példánymetódusnál a `this`-hez tartozót, `static` metódusnál az osztály `Class` objektumához tartozót. A `synchronized void bump()` pontosan ekvivalens a `void bump() { synchronized (this) { ... } }` alakkal; a statikus változat az osztályobjektumra szinkronizál.

### synchronized utasítás (§14.19)

`synchronized (Expression) Block`: az `Expression` típusa referencia kell legyen; értéke `null` esetén `NullPointerException`. A blokk normális vagy hirtelen befejeződése esetén a monitor feloldódik. A metódus- és blokk-szinkronizáció ugyanazt a zárat használja.

**Fontos korlát:** a zár megszerzése önmagában nem tiltja meg más szálaknak, hogy hozzáférjenek az objektum mezőihez vagy *nem* `synchronized` metódusaihoz; a kölcsönös kizárás csak akkor működik, ha mindenki ugyanazt a zárat használja.

### Szinkronizálás és láthatóság

Egy monitor unlock-ja *synchronizes-with* az ugyanazon monitoron későbbi lockkal, ezért happens-before él is: a zár nem csak kizárást, hanem láthatóságot is ad ([[concepts/konkprog/java-memoriamodell]]).

### Feladatok (Canvas)

- A lassú szövegíró kiíró metódusa legyen `synchronized`; majd ugyanez **blokkal**: a *hívást* tesszük `synchronized` blokkba.
- Bányászok és építők: a `Resources` osztály közös erőforrásait előbb `synchronized` metódusokkal, utána teljesítményjavításként a lehető legrövidebb `synchronized` blokkokkal védjük ([[concepts/konkprog/banyaszok-es-epitok]]).

## Kapocs

- [[concepts/konkprog/wait-notify]] — a monitor wait set-je
- [[concepts/konkprog/holtpont]] — több zár veszélye
- [[concepts/konkprog/szalbiztos-osztaly-tervezes]] — finomabb zárolás
