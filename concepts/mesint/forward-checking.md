---
tags: [concept]
sources: [04.visszalep.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-12
---

# Forward Checking (FC)

A Forward Checking a VL1 visszalépéses algoritmus kiegészítése egy vágó szabállyal: ha egy még kitöltetlen változó tartománya kiürül, azonnal visszalép.

## Tartalom

**FC algoritmus = VL1 + vágó szabály.**

A $k$-dik lépésben a $k$-adik királynő elhelyezése után az üres sorok szabad mezőinek száma csökken. Legyen $D_i$ az $i$-dik sor szabad mezői. A $k$-dik lépésben végzett törlések:

```
for i = k+1 .. n loop
    Töröl(i, k)
endloop
```

ahol $\text{Töröl}(i,k)$ törli $D_i$ azon mezőit, amelyeket a $k$-dik sor királynője üt. Ehhez jön a vágó szabály:

$$\exists i \in [k+1..n]: D_i = \emptyset \;\Rightarrow\; \text{visszalép}.$$

Az alap VL1 csak akkor lép vissza, ha $D_k=\emptyset$ (a következő királynőnek nincs helye); az FC már akkor, ha bármelyik későbbi sor tartománya kiürül. A slide példája $6\times6$-os táblán $k=4$ mellett: $D_6=\emptyset$, tehát az algoritmus rögtön visszalép.

Korlát-kielégítési megfogalmazásban: $\text{Töröl}(i,k): D_i := D_i - \{e\in D_i \mid \neg C_{ik}(e,x_k)\}$ ([[concepts/mesint/korlat-kielegitesi-modell]]). Ez modellfüggő vezérlési stratégia, nem heurisztika: nem a feladathoz, hanem a modellezési módszerhez kapcsolódik.

## Kapocs

- [[concepts/mesint/visszalepeses-kereses]] — az alap VL1
- [[concepts/mesint/look-forward]] — erősebb szűrés (PLF, LF)
- [[concepts/mesint/korlat-kielegitesi-modell]] — a modell, amelyben a szabály általánosan megfogalmazható
- [[concepts/mesint/n-kiralyno-problema]] — alkalmazott feladat
