---
tags: [concept]
sources: [03.lokalker.pdf]
derivation: source
kind: model
element: water
updated: 2026-10-12
---

# Kereső rendszer (KR)

A kereső rendszer (KR) a keresési algoritmusok közös, absztrakt váza: egy globális munkaterület, keresési szabályok és egy vezérlési stratégia hármasa, amely ciklusban módosítja a munkaterületet, amíg a terminálási feltétel nem teljesül.

## Tartalom

### A KR eljárása

```
Procedure KR
1. ADAT := kezdeti érték
2. while ¬terminálási feltétel(ADAT) loop
3.     SELECT SZ FROM alkalmazható szabályok
4.     ADAT := SZ(ADAT)
5. endloop
end
```

### Három komponens

- **Globális munkaterület (ADAT)** — a keresés során megszerzett és megőrzött ismeret, tipikusan a reprezentációs gráf egy részgráfja. A *kezdeti érték* a startcsúcsnak, a *terminálási feltétel* a célcsúcsnak felel meg.
- **Keresési szabályok** — megváltoztathatják a globális munkaterület tartalmát; mindegyiknek van *előfeltétele* és *hatása*.
- **Vezérlési stratégia** — az alkalmazható szabályok közül kiválaszt egy „megfelelőt"; alapja általános elv és heurisztika. Szintjeit lásd: [[concepts/mesint/vezerlesi-strategiak]].

### Hogyan „látja" a keresés a reprezentációs gráfot

A keresés fokozatosan fedezi fel a gráfot: bizonyos részeihez soha nem jut el, a felfedezett részt sem feltétlenül tárolja el teljesen. Ha egy csúcshoz érve nem vizsgálja meg, hogy korábban már felfedezte-e, hanem új csúcsként regisztrálja, akkor az eredeti gráf helyett egy **fát** lát („fává egyenesítés").

- Előny: a körök eltűnnek, de a megoldási utak megmaradnak.
- Hátrány: duplikátumok jelennek meg, a körök kiegyenesítése végtelen hosszú utakat eredményez.
- A kétirányú (oda-vissza) élek drasztikusan megnövelik a kapott fa méretét. Olcsóbb, ha minden csúcshoz eltároljuk azt a szülőcsúcsot, amelyik felől elértük: az onnan oda visszavezető él így könnyen felismerhető és figyelmen kívül hagyható.

## Kapocs

- [[concepts/mesint/vezerlesi-strategiak]] — a KR vezérlési szintjei és a stratégiák osztályozása
- [[concepts/mesint/hegymaszo-modszer]] — a KR legegyszerűbb lokális keresési példánya
- [[concepts/mesint/modellezes-es-kereses]] — a modell, amelyen a KR dolgozik
- [[concepts/mesint/graf-reprezentacio]] — a reprezentációs gráf
