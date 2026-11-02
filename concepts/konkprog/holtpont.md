---
tags: [concept]
sources: [Java-Language-Specification-SE-21.pdf, konkprog-canvas-feladat-1-etkezo-filozofusok.md]
derivation: source
kind: pitfall
element: water
updated: 2026-10-23
---

# Holtpont és elkerülése

Holtpont akkor áll elő, ha szálak körkörösen várnak egymás zárjaira. A Java sem nem észleli, sem nem akadályozza meg; a programozónak kell a zárak sorrendjével elkerülnie.

## Tartalom

### A nyelv álláspontja (JLS §17.1)

A Java **sem nem előzi meg, sem nem követeli meg** a holtpont-állapotok észlelését. Ha a szálak közvetlenül vagy közvetve több objektum zárját is tartják, a szokásos holtpont-elkerülő technikákat kell alkalmazni, szükség esetén magasabb szintű, nem holtpontosodó zárolási primitívek létrehozásával.

### Étkező filozófusok

Öt filozófus, öt evőpálca (két szomszéd között egy); enni csak mindkét pálca felvételével lehet. A mintaprogram (`Philosophers`) időnként holtpontba kerül, ha mindenki egyszerre a bal pálcáját veszi fel és a jobbra vár.

**Javítás (erőforrás-sorrendezés):** minden filozófus először az alacsonyabb, utána a magasabb sorszámú pálcát veszi fel. Így nem alakulhat ki körkörös várakozás, mert a zárakat globális sorrendben szerezzük.

Kapcsolódó zárszerkezet: [[concepts/konkprog/synchronized-monitor]].

## Kapocs

- [[concepts/konkprog/synchronized-monitor]] — a zárak
- [[concepts/konkprog/wait-notify]] — várakozás a zár elengedésével
