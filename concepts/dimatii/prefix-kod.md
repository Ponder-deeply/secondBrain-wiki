---
tags: [concept]
sources: [DimatIIEa08.pdf]
derivation: source
updated: 2026-09-08
---

# Prefix kód

Olyan betűnkénti kódolás, amelyben egyetlen kódszó sem prefixe egy másiknak; ettől a kód felbontható, sőt menet közben, várakozás nélkül dekódolható.

## Tartalom

Tekintsük az injektív $\varphi : A \to B^+$ leképezést, illetve az általa meghatározott $\psi$ betűnkénti kódolást.

- Ha $\mathrm{rng}(\varphi)$ prefixmentes halmaz, akkor **prefix kódról** beszélünk.
- Ha $\mathrm{rng}(\varphi)$ elemei azonos hosszúságúak, akkor **egyenletes kódról**, **fix hosszúságú kódról**, esetleg **blokk-kódról** beszélünk.
- **Vesszős kódról** beszélünk, ha van egy olyan $\vartheta \in B^+$ szó (a **vessző**), amely minden kódszónak szuffixe, de egyetlen kódszó sem áll elő $\alpha\vartheta\beta$ alakban üres $\beta$ szóval.

### Prefix kód felbontható

*Bizonyítás (konstruktív).* Nézzük az eddig beérkezett szimbólumokból összeálló szót. Amint ez kiadja a kódolandó ábécé valamelyik betűjének a kódját, azonnal dekódolhatunk a megfelelő betűre, mert a folytatásával kapott jelsorozat egyetlen betűnek sem lehet a kódja. $\square$

### Egyenletes kód prefix

*Bizonyítás.* Mivel a kódszavak hossza azonos, ezért csak úgy lehet egy kódszó prefixe egy másiknak, ha megegyeznek. $\square$

Így az egyenletes kód nyilván felbontható is.

### Vesszős kód prefix

*Bizonyítás.* A vessző egyértelműen jelzi egy kódszó végét, hiszen ha folytatva kódszót kapnánk, abban a vessző tiltott módon szerepelne. $\square$

Így a vesszős kód is felbontható.

A három osztály viszonya tehát: egyenletes $\Rightarrow$ prefix, vesszős $\Rightarrow$ prefix, prefix $\Rightarrow$ felbontható. A megfordítások nem igazak: van felbontható, de nem prefix kód (lásd a betűnkénti kódolás példáinak 3. oszlopát).

## Kapocs

- [[concepts/dimatii/betunkenti-kodolas]] — a keret, amelyben ezek a kódosztályok értelmezettek
- [[concepts/dimatii/mcmillan-egyenlotlenseg]] — a felbontható és a prefix kódok ugyanazokat a szóhosszakat engedik meg
- [[concepts/dimatii/kodfa]] — a prefix tulajdonság fa alakú megfelelője
- [[concepts/dimatii/huffman-kod]] — konkrét, optimális prefix kód konstrukciója
