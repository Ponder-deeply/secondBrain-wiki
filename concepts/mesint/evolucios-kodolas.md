---
tags: [concept]
sources: ["08.evolucio.pdf"]
derivation: source
kind: definition
element: air
updated: 2026-10-12
---

# Evolúciós kódolás

Az evolúciós algoritmus egy egyedet jelsorozattal (kromoszómával) kódol, amelynek ki kell elégítenie a kód-invariánst; az operátorok a kódon keresztül változtatják meg az egyedet.

## Tartalom

### Alapfogalmak

- **Kromoszóma:** az egyedet leíró jelsorozat. A **kód-invariáns** a jelsorozat által teljesítendő feltétel (pl. permutáció legyen).
- **Gén:** egy jel vagy jelcsoport, amely az egyed egy tulajdonságát (attribútum-érték párját) írja le.
- Gyakran a gén pozíciója a kódsorozatban (**lókusz**) jelöli ki az attribútumot, a gén értéke maga az **allél**.
- A kód ekkor tulajdonságonként **feldarabolható**: egy rövid kódszakasz megváltoztatása kis mértékben változtat az egyeden.

### Gyakori kódolások

- **Vektor:** valós vagy egész számok rögzített hosszú tömbje.
- **Bináris kód:** bitek rögzített hosszú tömbje.
- **Permutáció:** véges sok elem permutációja.

### Példák

**n-királynő.** (1.) Egyed: olyan elrendezés, ahol minden oszlopban pontosan egy királynő áll; kód: az oszloponkénti sorpozíciók sorozata, pl. `3 2 7 5 2 4 1 1`. (2.) Ha minden sorban is pontosan egy királynő áll, a kód az oszloponkénti sorpozíciók **permutációja**, pl. `2 8 7 5 4 1 6 3`; ekkor a rekombináció és a mutáció után ellenőrizni (javítani) kell a permutáció-invariánst.

**SAT.** Egy igazságkiértékelés egyed; a kód logikai értékek (bitek) sorozata, pl. `11010`.

**Gráfszínezés (4 szín).**
- *Direkt kódolás:* $x[i]$ az $i$-edik csúcs színe; a rátermettség a jó élek (különböző színű végpontúak) száma (a példában $f=10$).
- *Indirekt kódolás:* a kód csúcssorrend (permutáció); az $i$-edik lépésben az $x[i]$-edik csúcsot a lehető legvilágosabb színnel színezzük a szomszédjaihoz igazodva, ha lehet; $f$ a kiszínezett csúcsok száma (a példában $f=6$).

**Kő-papír-olló stratégia.** Jelek: K ~ 0, P ~ 1, O ~ 2. Az előzmény az utolsó két csata (ÉnŐÉnŐ), négy jegyű hármas számrendszerbeli szám: `KKKK ~ 0000 ~ 0`, `KKKP ~ 0001 ~ 1`, ... `OOOO ~ 2222 ~ 80`. Az egyed kódja egy 81 hosszú sorozat $\{0,1,2\}^{0..80}$, ahol a $k$-adik jel az előzmény-$k$ esetén javasolt válasz (pl. `1201 … 20`). Összes stratégia: $3^{81}$.

## Kapocs

- [[concepts/mesint/evolucios-algoritmus-tervezese]] — a kódolás az első tervezési döntés
- [[concepts/mesint/ratermettseg-kiertekelese]] — a rátermettség a kódoláshoz kapcsolódik
- [[concepts/mesint/rekombinacio-es-keresztezes]] — az operátoroknak meg kell őrizniük a kód-invariánst
- [[concepts/mesint/grafszinezes]] — a feladat más megközelítésben
