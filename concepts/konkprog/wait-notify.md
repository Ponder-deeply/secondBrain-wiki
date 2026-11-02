---
tags: [concept]
sources: [Java-Language-Specification-SE-21.pdf, konkprog-canvas-feladat-1-az-alvo-borbely-problema.md, konkprog-canvas-feladat-2-tovabbfejlesztes.md, konkprog-canvas-feladat-gyakorlo-feladat-sajat-blokkolo-sor-megvalositasa-varakozas.md]
derivation: source
kind: procedure
element: earth
updated: 2026-10-23
---

# Várakozás és ébresztés (wait, notify, notifyAll)

Az `Object.wait/notify/notifyAll` a monitorhoz tartozó wait set-et kezeli; csak a monitor birtokában hívhatók, és a `wait`-et mindig olyan ciklusban kell használni, amely a feltételt újraellenőrzi.

## Tartalom

### Wait set (JLS §17.2)

Minden objektumhoz a monitoron kívül egy *wait set* (várakozó szálak halmaza) is tartozik; kezdetben üres. A halmazt kizárólag az `Object.wait`, `notify`, `notifyAll` módosítja, ezek atomiak.

### wait (§17.2.1)

Alakok: `wait()`, `wait(long ms)`, `wait(long ms, int ns)`; a nulla időzítésű forma egyenértékű a `wait()`-tel. Ha a szál nem birtokolja a monitort, `IllegalMonitorStateException` jön; ha a nanosec kívül esik a 0–999999 tartományon vagy a ms negatív, `IllegalArgumentException`; ha a szál meg van szakítva, `InterruptedException`. Különben a szál bekerül a wait set-be, **feloldja a monitort** (a birtokolt lockok számának megfelelő unlockkal), majd addig nem fut, amíg ki nem kerül a halmazból: `notify`, `notifyAll`, `interrupt`, időzített waitnél az idő lejárta, vagy *spurious wake-up* (az implementáció jogosult, bár nem ösztönzött erre). Ezután újra megszerzi a monitort.

**Következmény:** a `wait`-et csak olyan ciklusban használjuk, amely akkor ér véget, ha a várt logikai feltétel valóban teljesül.

### notify és notifyAll (§17.2.2)

Csak a monitor birtokában hívhatók (különben `IllegalMonitorStateException`). A `notify` a wait set egy **tetszőleges** (nem meghatározott) szálát távolítja el, ha van; a `notifyAll` mindet. Az ébresztett szál csak akkor folytathatja, ha az értesítő szál már teljesen feloldotta a monitort, és egyszerre csak egy szál szerzi meg.

### Kölcsönhatás megszakítással (§17.2.4)

Értesítés nem veszhet el megszakítás miatt: ha egy `notify` után a kiválasztott szál `InterruptedException`-nel tér vissza, akkor egy másik szálnak kell megkapnia az értesítést.

### Feladatok (Canvas)

- **Az alvó borbély probléma:** a borbély a munkaterem székében alszik, ha nincs ügyfél; az ügyfél felébreszti, ha alszik, vár a váróteremben, ha van szabad szék, különben elmegy. A hiányzó részeket `wait()`/`notify()`-jal kell megvalósítani (`BarberShop.java`).
- **Továbbfejlesztés:** a `Barber` szál megszakítása helyett `wait(long timeoutMillis)`-szel korlátozzuk a borbély alvásának hosszát.
- **Saját blokkoló sor:** a `BlockingQueue.take()` megírása várakozás–ébresztéssel; mivel a sor nem tartja nyilván a várakozókat, `notifyAll()` használandó; a `Queue` interfészt és egy megvalósítását (`ArrayDeque`) kell kiterjeszteni (`MyBlockingQueue.java`).

## Kapocs

- [[concepts/konkprog/synchronized-monitor]] — a monitor, amelyen a wait fut
- [[concepts/konkprog/termelo-fogyaszto]] — tipikus alkalmazás
- [[concepts/konkprog/szal-varakozas-es-megszakitas]] — megszakítás
