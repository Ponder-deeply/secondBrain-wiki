---
tags: [concept]
sources: [konkprog-canvas-feladat-1-gyakorlo-feladat-termelo-es-fogyaszto.md, konkprog-canvas-feladat-gyakorlo-feladat-sajat-blokkolo-sor-megvalositasa-varakozas.md]
derivation: source
kind: model
element: earth
updated: 2026-10-23
---

# Termelő–fogyasztó probléma és blokkoló sor

Egy termelő szál elemeket tesz egy sorba, egy fogyasztó szál kiveszi és kiírja; a közös sor elérését szálbiztossá kell tenni, a blokkoló sor pedig a várakozást is kezeli.

## Tartalom

### Feladat

A `ProducerConsumer` osztályban egy termelő szál elemeket helyez egy sorba, egy fogyasztó kiveszi és kiírja őket, egy harmadik szál időnként pillanatképet ír ki a sor állapotáról. Az eredeti program hibás, mert a sorhoz való hozzáférés **versenyhelyzetes**; a javításban a sor elérését és a képernyőre írást is konzisztenssé kell tenni (két megoldás szerepel: `ProducerConsumer`, `ProducerConsumer2`). Lásd [[concepts/konkprog/verseny-helyzet-es-adatverseny]], [[concepts/konkprog/synchronized-monitor]].

### Saját blokkoló sor

A `BlockingQueue.take()` műveletet várakozás–ébresztéssel írjuk meg: üres sornál a hívó `wait()`-el vár, `put` után `notifyAll()` ébreszt (a sor nem nyilvántartja a várakozókat, ezért `notifyAll`). A megvalósítás a `Queue` interfészt és egy implementációt (`ArrayDeque`) terjeszti ki (`MyBlockingQueue`); a korábbi termelő–fogyasztó megoldás a teszt. Alapja: [[concepts/konkprog/wait-notify]].

## Kapocs

- [[concepts/konkprog/wait-notify]] — várakozás és ébresztés
- [[concepts/konkprog/synchronized-monitor]] — a sor védelme
- [[concepts/konkprog/szinkronizalt-gyujtemenyek]] — szinkronizált sor
