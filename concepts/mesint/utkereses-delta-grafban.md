---
tags: [concept]
sources: [01.bevezetes.pdf]
derivation: source
kind: procedure
element: water
updated: 2026-10-12
---

# Útkeresés $\delta$-gráfban

A reprezentációs gráf nagy mérete miatt az útkeresési problémához speciális, nem-determinisztikus, heurisztikus útkereső algoritmus kell, amely a startcsúcsból indul és csak a feltárt gráfrészt tárolja.

## Tartalom

Az útkereső algoritmus:

- a startcsúcsból **indul** (ez a kezdeti aktuális csúcs);
- minden lépésben **nem-determinisztikus** módon új aktuális csúcso(ka)t **választ** a korábbi aktuális csúcs(ok) segítségével (gyakran azok gyerekei közül);
- **tárolja** a már feltárt reprezentációs gráf egy részét;
- **megáll**, ha célcsúcsot talál, vagy nyilvánvalóvá válik, hogy erre semmi esélye.

Ez a vázlat a későbbi keresőrendszer-felfogás ősképe; a konkrét vezérlési stratégiák és algoritmusok külön témák.

## Kapocs

- [[concepts/mesint/graf-reprezentacio]] — a reprezentációs gráf, amelyben keresünk
- [[concepts/mesint/utkeresesi-problema]] — a megoldandó probléma
- [[concepts/mesint/kereso-rendszer]] — a keresőrendszer pontos felépítése
- [[concepts/mesint/vezerlesi-strategiak]] — hogyan választ az algoritmus
- [[concepts/mesint/utkereses-es-vagy-grafban]] — ÉS/VAGY gráf visszavezetése $\delta$-gráfra
