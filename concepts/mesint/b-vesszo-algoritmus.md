---
tags: [concept]
sources: [05-06.grafker.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-12
---

# B' algoritmus

A B' algoritmus a heurisztikus függvény értékét futás közben javítja: a $h$ megengedhető marad, nem csökken, és a monoton megszorítást sértő élek száma nő.

## Tartalom

A kiterjesztendő $n$ csúcs kiválasztása után, a szomszédok előállításakor az algoritmus a $h$-t korrigálja:

```
if h(n) < min_{m ∈ Γ(n)} (c(n,m) + h(m))
  then h(n) := min_{m ∈ Γ(n)} (c(n,m) + h(m))
  else for ∀ m ∈ Γ(n)-re loop
         if h(n) - h(m) > c(n,m) then h(m) := h(n) - c(n,m)
       endloop
```

Két eset van:

1. **Az $n$ heurisztikája túl optimista** a gyerekeihez képest: $h(n)$ kisebb, mint amit a szomszédok megengednek ($\min_m (c(n,m)+h(m))$). Ekkor $h(n)$-t felemeljük erre az értékre.
2. **Különben** minden $m\in\Gamma(n)$ szomszédra: ha a monoton megszorítás $h(n)-h(m)\le c(n,m)$ sérül, akkor $h(m)$-et felemeljük $h(n)-c(n,m)$-re.

### Tulajdonságok

- A $h$ **megengedhető marad** (nem lépi túl $h^*$-ot).
- A $h$ **nem csökken** (csak nőhet), tehát informáltabb lesz.
- A **monoton megszorításos élek száma nő** – a függvény egyre közelebb kerül a monotonhoz.

### Használat

A változó heurisztikák egyik formája; a másik az $f=g+\phi\cdot h$ súlyozás, ahol $\phi\sim d$ (lásd [[concepts/mesint/heurisztika-szerepe-a-grafkeresesben]]).

## Kapocs

- [[concepts/mesint/heurisztikus-fuggveny-tulajdonsagai]] — megengedhetőség és monoton megszorítás
- [[concepts/mesint/b-algoritmus]] — a futási időt a kiterjesztési sorrenddel csökkentő változat
- [[concepts/mesint/heurisztika-szerepe-a-grafkeresesben]] — a jó heurisztika szempontjai
- [[concepts/mesint/a-algoritmus]] — az alap algoritmus
