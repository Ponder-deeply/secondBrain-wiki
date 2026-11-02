---
tags: [concept]
sources: [02.modellek.pdf]
derivation: source
kind: definition
element: water
updated: 2026-10-12
---

# Visszafelé haladó keresés

Visszafelé haladó keresésnél a megoldást a céltól a start felé haladva keressük, ha a problématér a cél felől nézve kevesebb alternatívát mutat; a talált utat fordítva kell értelmezni.

## Tartalom

**Alapötlet.** Ha a megoldás megtalálása a cél felől egyszerűbb, mint a start felől (mert a problématér így kevesebb alternatívát mutat), érdemes a célból a start felé haladva keresni. Ügyelni kell arra, hogy az így megtalált megoldási utat fordítva, a starttól a cél irányában is értelmezni lehessen.

**Példa: kockavilág.** A start állapotban az A és B kocka egymás mellett áll a földön, a robotkar üres. Célállapot: B áll az A tetején. A célból visszafelé: `levesz(A,B)`, `letesz(A)`; a megoldás ennek fordítottja: `felvesz(A)`, `rátesz(A,B)`. A visszafelé lépések inverz műveletekkel olvashatók át előrefelé.

**Példa: útvonalkeresés városban.** Egyirányú utcák miatt a gráf aszimmetrikus: a startból induló útból sok van, nehéz közöttük célba vezetőt találni; a célból induló útból kevesebb van, könnyebb startba vezetőt találni, de nem biztos, hogy az végigjárható a start felől is (kék út). Az olyan speciális, cél felől indított keresés, amely figyelembe veszi az élek irányát, a startból célba vezető (zöld) utat adja, kihasználva az aszimmetria előnyeit.

**A visszafelé haladó keresés feltételei:**

1. A reprezentációs gráf élei kétirányúak legyenek (legalább a visszafelé megtalált megoldási út mentén). Állapottér-modellnél ez biztosan teljesül, ha a műveleteknek van inverze.
2. Ismerni kell egy startból elérhető célállapotot.

Ha ezek a feltételek nem állnak fenn, de mégis visszafelé szeretnénk keresni, akkor **problémaredukciót** kell alkalmazni: [[concepts/mesint/problema-redukcios-modell]].

## Kapocs

- [[concepts/mesint/allapotter-modell]] — az a modell, amelyben a visszafelé keresés az inverz műveletekre támaszkodik.
- [[concepts/mesint/kancso-problema]] — példa arra, hogy a műveletnek nincs inverze, ezért a sima visszafelé keresés nem működik.
- [[concepts/mesint/problema-redukcios-modell]] — a feltételek sérülése esetén használt megoldás.
- [[concepts/mesint/utkeresesi-problema]] — a keresés alapfeladata, amelyet visszafelé is lehet végezni.
