---
tags: [concept]
sources: [Java-Language-Specification-SE-21.pdf, konkprog-canvas-feladat-2-szalak-bevarasa.md, konkprog-canvas-feladat-3-varakozas-szalon-belul.md, konkprog-canvas-feladat-4-szalak-varakozasanak-megszakitasa.md, konkprog-canvas-feladat-5-megszakitott-szal-ujrainditasa.md, konkprog-canvas-feladat-pelda-alternativ-modszer-szalak-letrehozasara-szalak-bevaras.md]
derivation: source
kind: procedure
element: earth
updated: 2026-10-23
---

# Szálak bevárása, altatása és megszakítása

A `join()` bevár egy szálat, a `Thread.sleep()` altatja az aktuális szálat, az `interrupt()` megszakítást jelez; mindhárom `InterruptedException`-t dobhat. Megszakított szál nem indítható újra.

## Tartalom

### join

A `Thread.join()` a hívó szálat addig várakoztatja, amíg a célszál be nem fejeződik. A JLS happens-before szabálya: egy szál összes művelete *happens-before* minden olyan művelettel, amely egy másik szálban sikeresen visszatér az adott szálon végzett `join()`-ból (§17.4.5), így a bevárás után a szál eredményei láthatók. A hívást `InterruptedException` elkapásával kell körülvenni.

### sleep és yield

A `Thread.sleep()` az aktuális szálat a megadott időre felfüggeszti, **de a szál nem veszíti el a birtokolt monitorokat** (§17.3). Sem a `sleep`, sem a `yield` nem rendelkezik szinkronizációs szemantikával: a fordító nem köteles a regiszterben tárolt értékeket kiírni vagy újratölteni. A JLS példája: ha a `done` mező nem `volatile`, akkor a `while (!this.done) Thread.sleep(1000);` ciklus a gyorsítótárazott érték miatt sosem fejeződhet be (lásd [[concepts/konkprog/volatile-mezo]]).

### interrupt

Az `u.interrupt()` hívás (§17.2.3) `u` megszakítási állapotát `true`-ra állítja. Ha `u` éppen egy objektum wait set-jében vár, kikerül belőle, és `wait` után – a monitor újrazárolását követően – `InterruptedException`-t dob. Lekérdezés: `Thread.isInterrupted()`; a statikus `Thread.interrupted()` az állapotot lekérdezi **és törli**. Az `InterruptedException` dobásakor az állapot `false`-ra áll. A megszakítás szintén szinkronizál: a megszakító szál `interrupt()` hívása *synchronizes-with* azzal a ponttal, ahol a megszakított szál ezt észleli.

Kölcsönhatás értesítéssel (§17.2.4): ha egy várakozó szálat egyszerre értesítenek és megszakítanak, vagy normálisan tér vissza a `wait`-ből (függő megszakítással), vagy `InterruptedException`-nel; az értesítés nem veszhet el (lásd [[concepts/konkprog/wait-notify]]).

### Feladatok (Canvas)

- **Szálak bevárása:** az előző program kiír „kész”-et a `join` után (a ciklushatár 1000-re csökkentve).
- **Várakozás szálon belül:** két kiírás között 5 ms `sleep`.
- **Megszakítás:** egy másodperc futás után `interrupt()`.
- **Megszakított szál újraindítása?:** `TryRestart.java` – nem működik, kivételt dob (a már elindított szál ismét `start()`-olva `IllegalThreadStateException`-t eredményez; ezt a Canvas-oldal csak annyiban rögzíti, hogy „kivételt dob”).

## Kapocs

- [[concepts/konkprog/szal-letrehozas]] — a szálak indítása
- [[concepts/konkprog/wait-notify]] — várakozás monitoron
- [[concepts/konkprog/java-memoriamodell]] — happens-before élek
