---
tags: [subject]
sources: [Java-Language-Specification-SE-21.pdf, konkprog-canvas-feladat-1-a-runnable-interfesz.md, konkprog-canvas-feladat-1-az-alvo-borbely-problema.md, konkprog-canvas-feladat-1-callable-es-future-objektumok.md, konkprog-canvas-feladat-1-egyszeru-java-osztaly.md, konkprog-canvas-feladat-1-elso-szalak.md, konkprog-canvas-feladat-1-etkezo-filozofusok.md, konkprog-canvas-feladat-1-gyakorlo-feladat-banki-ugyfelek-tovabbfejlesztes.md, konkprog-canvas-feladat-1-gyakorlo-feladat-banki-ugyfelek.md, konkprog-canvas-feladat-1-gyakorlo-feladat-termelo-es-fogyaszto.md, konkprog-canvas-feladat-1-gyakorlo-feladat-tovabbi-metodusok-a-threadsafemutableinte.md, konkprog-canvas-feladat-1-szinkronizalt-metodusok.md, konkprog-canvas-feladat-1-threadsafemutableinteger.md, konkprog-canvas-feladat-2-absztrakt-osztaly-es-oroklodes.md, konkprog-canvas-feladat-2-egyszeru-thread-pool-ok.md, konkprog-canvas-feladat-2-gyakorlo-feladat-szinkronizalt-metodusok-a-banyaszok-es-ep.md, konkprog-canvas-feladat-2-gyakorlo-feladat-tovabbi-metodusok-a-threadsafemutableinta.md, konkprog-canvas-feladat-2-harom-szal.md, konkprog-canvas-feladat-2-szalak-bevarasa.md, konkprog-canvas-feladat-2-szinkronizalt-blokkok.md, konkprog-canvas-feladat-2-threadsafemutableintarray.md, konkprog-canvas-feladat-2-tovabbfejlesztes.md, konkprog-canvas-feladat-3-atomic-tipusok.md, konkprog-canvas-feladat-3-gyakorlo-feladat-szinkronizalt-blokkok-a-banyaszok-es-epit.md, konkprog-canvas-feladat-3-gyujtemenyek-eleresenek-szinkronizacioja.md, konkprog-canvas-feladat-3-interfesz.md, konkprog-canvas-feladat-3-szovegiro-szalak.md, konkprog-canvas-feladat-3-varakozas-szalon-belul.md, konkprog-canvas-feladat-4-lassu-szovegiras.md, konkprog-canvas-feladat-4-szalak-varakozasanak-megszakitasa.md, konkprog-canvas-feladat-4-szinkronizalt-gyujtemenyek.md, konkprog-canvas-feladat-5-megszakitott-szal-ujrainditasa.md, konkprog-canvas-feladat-gyakorlo-feladat-banyaszok-es-epitok.md, konkprog-canvas-feladat-gyakorlo-feladat-sajat-blokkolo-sor-megvalositasa-varakozas.md, konkprog-canvas-feladat-pelda-alternativ-modszer-szalak-letrehozasara-szalak-bevaras.md]
derivation: source
math: 10
updated: 2026-10-23
---

# Konkurens programozás (konkprog)

ELTE IK kurzus (Ea + Gy), Java-alapú konkurens programozás: szálak létrehozása és életciklusa, kölcsönös kizárás és monitorok, várakozás–ébresztés, holtpont, a Java memóriamodell, szálbiztos adatszerkezetek, thread pool-ok.

## Tárgykör

- Forrásanyag: a Java Language Specification SE 21 szálakra és zárakra vonatkozó részei (§8.3.1.4, §8.4.3.6, §14.19, §17), valamint a Canvas gyakorlati feladatlapok (megoldásfájlokra hivatkozással).
- Félév: 2026/27/1; követelmények és a vizsga formája a forrásokból nem derül ki (a Canvas-lapok csak gyakorlati feladatok).

## Fogalomlapok

### Szálak alapjai

- [[concepts/konkprog/szal-letrehozas]] — Java-ban szál a `Thread` osztály példánya; két szokásos létrehozási mód van: a `Thread` kiterjesztése, vagy a `Runnable` interfész megvalósítása
- [[concepts/konkprog/szal-varakozas-es-megszakitas]] — A `join()` bevár egy szálat, a `Thread.sleep()` altatja az aktuális szálat, az `interrupt()` megszakítást jelez; mindhárom `InterruptedException`-t dobhat
- [[concepts/konkprog/java-oop-alapok]] — A kurzus bevezető OOP-feladatsora: osztály, absztrakt osztály és öröklődés, interfész – egyetlen `Employee` példán keresztül

### Szinkronizáció és kommunikáció

- [[concepts/konkprog/synchronized-monitor]] — Minden Java-objektumhoz tartozik egy monitor; a `synchronized` metódus vagy blokk a végrehajtás idejére zárolja azt, így egyszerre csak egy szál futtathatja az ugyanazon monitorra szinkronizált kódot
- [[concepts/konkprog/wait-notify]] — Az `Object.wait/notify/notifyAll` a monitorhoz tartozó wait set-et kezeli; csak a monitor birtokában hívhatók, és a `wait`-et mindig olyan ciklusban kell használni, amely a feltételt újraellenőrzi
- [[concepts/konkprog/holtpont]] — Holtpont akkor áll elő, ha szálak körkörösen várnak egymás zárjaira
- [[concepts/konkprog/verseny-helyzet-es-adatverseny]] — Szinkronizálatlan közös adat elérése nemdeterminisztikus, gyakran hibás eredményhez vezet

### Memóriamodell

- [[concepts/konkprog/java-memoriamodell]] — A memóriamodell azt írja le, hogy egy program adott végrehajtási nyoma szabályos-e: melyik olvasás melyik írás értékét láthatja
- [[concepts/konkprog/volatile-mezo]] — A `volatile` mező olvasásakor és írásakor a Java memóriamodell biztosítja, hogy minden szál konzisztens értéket lásson; zár nélküli, de csak láthatóságot és sorrendet adó alternatíva
- [[concepts/konkprog/final-mezo-szemantika]] — A `final` mező a konstruktor végén „befagy”; ha egy másik szál az objektumot csak a konstruktor befejezése után látja, a `final` mezők helyes értékét garantáltan látja szinkronizáció nélkül is
- [[concepts/konkprog/szotores-es-nem-atomi-long-double]] — A JVM-nek külön mezők és tömbelemek frissítése nem zavarhatja egymást (nincs word tearing); a nem `volatile` 64 bites `long` és `double` írása viszont két 32 bites írásnak számíthat

### Szálbiztos adatszerkezetek és könyvtárak

- [[concepts/konkprog/szalbiztos-osztaly-tervezes]] — Egy `int` vagy `int[]` fölé épített szálbiztos absztrakció: az egész objektumot egyetlen zárral, a tömböt elemenkénti zárakkal védjük, hogy a különböző elemek párhuzamosan írhatók legyenek
- [[concepts/konkprog/atomic-tipusok]] — A `java.util.concurrent.atomic` csomag kész, szálbiztos típusokat ad: az `AtomicInteger` a `ThreadSafeMutableInteger`, az `AtomicIntegerArray` a `ThreadSafeMutableIntArray` beépített megfelelője
- [[concepts/konkprog/szinkronizalt-gyujtemenyek]] — A szinkronizálatlan gyűjtemény több szálból nem használható biztonságosan; két megoldás: a hozzáférést szinkronizált blokkba tesszük, vagy a gyűjteményt a `Collections.synchronizedXxx()` burkolóval szálbiztossá tesszük
- [[concepts/konkprog/executor-es-thread-pool]] — Az `ExecutorService` rögzített számú szálon hajtja végre a beküldött feladatokat (`Executors.newFixedThreadPool`); a pool leállítása `shutdown()`, a befejezés megvárása `awaitTermination()`
- [[concepts/konkprog/callable-es-future]] — A `Callable` értéket visszaadó feladat; `ExecutorService.submit()` azonnal `Future`-t ad vissza, amelynek `get()` metódusa az eredményt (szükség esetén várakozással) szolgáltatja

### Klasszikus feladatok

- [[concepts/konkprog/termelo-fogyaszto]] — Egy termelő szál elemeket tesz egy sorba, egy fogyasztó szál kiveszi és kiírja; a közös sor elérését szálbiztossá kell tenni, a blokkoló sor pedig a várakozást is kezeli
- [[concepts/konkprog/banyaszok-es-epitok]] — Szimuláció, amelyben bányász- és építőszálak közös erőforrásokon (arany, házak) dolgoznak; a feladatsor a szálindítást, bevárást, majd a szinkronizálás finomhangolását gyakoroltatja

## Kapocs

Lapszámok, az ingestre váró tárgyak és a feldolgozatlan források: `Wiki/state.md` (generált).
