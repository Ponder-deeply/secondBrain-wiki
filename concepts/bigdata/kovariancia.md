---
tags: [concept, bigdata/gepi-tanulas-klaszterezes-es-dimenziocsokkentes]
sources: [BDAEM-2022-EA10.pptx]
derivation: source
updated: 2026-09-12
---

# Variancia és kovariancia

A variancia és a kovariancia egy adathalmaz középpontja (átlaga) körüli
"szóródását" mérik; a kovariancia ennek a szóródásnak a mértéke két dimenzió
között, és a PCA egyik alapvető építőköve.

## Tartalom

### Variancia

A variancia nagyjából egy adateloszlás szóródását fejezi ki, hasonlóan a
szórásnégyzethez: azt méri, hogy egy dimenzió mentén az egyes pontok mennyire
térnek el az átlagtól.

### Kovariancia

A kovariancia két dimenzió közötti együttmozgást méri: megmutatja, hogy az
egyik dimenzió változása mennyire jár együtt a másik dimenzió változásával.

- **Pozitív kovariancia:** a két dimenzió együtt nő vagy együtt csökken.
- **Negatív kovariancia:** amíg az egyik dimenzió nő, a másik csökken.
- Egy dimenzió önmagával vett kovarianciája megegyezik a dimenzió
  varianciájával.

A kovarianciát elsősorban magas dimenziós adathalmazokban a dimenziók közti
kapcsolatok feltárására használjuk — ez a mintaátlaghoz (sample mean) képesti
eltérésekből számítható.

## Kapocs

- [[concepts/bigdata/pca]] — a PCA a kovarianciamátrix
  sajátvektorai/sajátértékei alapján határozza meg a főkomponenseket
- [[concepts/bigdata/sajatvektor-sajatertek]] — a kovarianciamátrixra
  alkalmazott sajátvektor/sajátérték-felbontás adja a főkomponenseket
</content>
