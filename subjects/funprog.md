---
tags: [subject]
sources: [Wiki/sources/funprog/tanterv.pdf, Wiki/sources/funprog/kviz-minta.pdf]
derivation: source
updated: 2026-08-05
---

# Funkcionális programozás (Haskell)

ELTE IK kurzus. Haskell-alapú bevezetés a funkcionális programozásba: lusta kiértékelés, currying, mintaillesztés, paraméteres és ad-hoc polimorfizmus, algebrai adattípusok, típusosztályok, magasabb rendű függvények, ZF-kifejezések, listák, klasszikus algoritmusok funkcionális stílusban.

## Témakörök heti bontásban (tanterv 5. oldal)

| Hét | Téma | Fő fogalmak |
|---|---|---|
| 1 | Bevezetés | — |
| 2 | Alapvető fogalmak | tisztaság, referencia-transzparencia |
| 3 | Egyszerű függvények | [[concepts/funprog/lusta-kiertekeles]], [[concepts/funprog/moho-kiertekeles]] |
| 4 | Fontosabb fogalmak | [[concepts/funprog/rekurzio]], [[concepts/funprog/currying]], [[concepts/funprog/margoszabaly]] |
| 5 | ZF-kifejezések, modul | [[concepts/funprog/zf-kifejezes]], [[concepts/funprog/modul]] |
| 6 | Esetszétválasztás | [[concepts/funprog/guard]], [[concepts/funprog/case-kifejezes]] |
| 7 | 8 királynő | [[concepts/funprog/nyolc-kiralyno]] |
| 8 | Típusok, polimorfizmus, minta | [[concepts/funprog/alaptipusok]], [[concepts/funprog/parametrikus-polimorfizmus]], [[concepts/funprog/mintaillesztes]] |
| 9 | Ad-hoc polimorfizmus | [[concepts/funprog/ad-hoc-polimorfizmus]], [[concepts/funprog/peldanyositas]] |
| 10 | Magasabb rendű függvények | [[concepts/funprog/magasabb-rendu-fuggveny]], [[concepts/funprog/map-filter-fold]] |
| 11 | Lista reprezentáció | [[concepts/funprog/lista-reprezentacio]], [[concepts/funprog/lista-muveletek]] |
| 12 | Rendezések | [[concepts/funprog/beszuras-rendezes]], [[concepts/funprog/merge-sort]], [[concepts/funprog/quicksort]] |
| 13 | Algebrai adattípusok, típusosztály | [[concepts/funprog/algebrai-adattipus]], [[concepts/funprog/tipusosztaly]] |

## Vizsga

- **Gyakorlat**: kódolás Haskellben.
- **Elméleti kvíz** (12 kérdés, ≥7 helyes): típus-szignatúrák, mintaillesztés-struktúra, ZF↔HOF ekvivalencia, ADT-konstruktorok típusa, totalitás (lásd `Wiki/sources/funprog/kviz-minta.pdf`).

## Fogalomlapok

### Kiértékelés és tisztaság

- [[concepts/funprog/lusta-kiertekeles]] — lazy evaluation: thunk, WHNF, végtelen lista
- [[concepts/funprog/moho-kiertekeles]] — eager/strict eval; `seq`, `($!)`, `foldl'`, BangPatterns
- [[concepts/funprog/referencia-transzparencia]] — érték helyettesíthetőség, equational reasoning
- [[concepts/funprog/tiszta-fuggveny]] — pure: determinisztikus, mellékhatás-mentes; IO monád határa
- [[concepts/funprog/bottom-undefined]] — ⊥, `undefined`, `error`, végtelen rekurzió
- [[concepts/funprog/totalis-vs-parcialis]] — totális ⇔ ⊥-mentes; típusszignatúra-alapú döntés

### Szintaxis és esetszétválasztás

- [[concepts/funprog/margoszabaly]] — off-side rule: behúzás határoz blokkot
- [[concepts/funprog/mintaillesztes]] — pattern matching: literál, wildcard, konstruktor, as-minta
- [[concepts/funprog/guard]] — `|` őrfeltételek; `otherwise`; fentről le
- [[concepts/funprog/case-kifejezes]] — kifejezésszintű mintaillesztés, guard-okkal
- [[concepts/funprog/let-where]] — `let ... in` (kifejezés) vs `where` (egyenlet)
- [[concepts/funprog/lambda]] — `\x -> e`, eta-redukció

### Függvények

- [[concepts/funprog/rekurzio]] — lineáris/kettős/farok-rekurzió, akkumulátor minta
- [[concepts/funprog/currying]] — `a -> b -> c` ≡ `a -> (b -> c)`; jobbra zár
- [[concepts/funprog/parcialis-alkalmazas]] — kevesebb arg ⇒ új függvény; `add 1`, `(+1)`
- [[concepts/funprog/magasabb-rendu-fuggveny]] — HOF: `map`, `filter`, `foldr`, `(.)`, `flip`, `($)`
- [[concepts/funprog/map-filter-fold]] — kanonikus HOF-ok: típusok, definíciók, ZF↔HOF ekvivalencia
- [[concepts/funprog/fuggveny-kompozicio]] — `(.)`; `($)` zárójel-helyettesítő
- [[concepts/funprog/operator-szekcio]] — `(+1)`, `(10-)`, `(>0)`; `(-1)` csapda

### Listák

- [[concepts/funprog/lista-reprezentacio]] — `[]` és `(:)`; `String = [Char]`
- [[concepts/funprog/lista-muveletek]] — `(++)`, `(!!)`, `take`/`drop`, `zip`; parciális vs totális
- [[concepts/funprog/zf-kifejezes]] — `[ e | x <- xs, f x ]`; ekvivalens `(map e . filter f) xs`

### Típusok és polimorfizmus

- [[concepts/funprog/alaptipusok]] — `Int`, `Integer`, `Double`, `Char`, `Bool`, `String`, tuple
- [[concepts/funprog/tipus-szignatura]] — `::`, `=>`, kanonikus aláírások
- [[concepts/funprog/tipusozhatosag]] — well-typed kifejezés; típushiba-detektálás
- [[concepts/funprog/parametrikus-polimorfizmus]] — parametricitás; totalitás polimorf típusból
- [[concepts/funprog/ad-hoc-polimorfizmus]] — túlterhelés típusosztály + példány alapján
- [[concepts/funprog/tipusosztaly]] — `class`, metódusok, default impl, superclass
- [[concepts/funprog/peldanyositas]] — `instance`, `deriving (Eq, Show, ...)`
- [[concepts/funprog/szabvanyos-tipusosztalyok]] — `Eq`, `Ord`, `Show`, `Num`, `Enum`, `Bounded`

### Adattípusok

- [[concepts/funprog/algebrai-adattipus]] — `data`: sum (`|`) of products; `Maybe`, `Either`; rekord
- [[concepts/funprog/adatkonstruktor-mint-fuggveny]] — konstruktor típusa; típusparaméter-sorrend
- [[concepts/funprog/rekurziv-adattipus]] — `List`, `Tree`, `Nat`; strukturális rekurzió
- [[concepts/funprog/tipusszinonima]] — `type` alias, nem új típus
- [[concepts/funprog/newtype]] — egy-konstruktor egy-mező típusbiztos burok
- [[concepts/funprog/maybe-either]] — `Maybe a`, `Either a b`: totalizált hibajelzés
- [[concepts/funprog/modul]] — `module`, export-lista, `import`, `qualified`

### Algoritmusok

- [[concepts/funprog/beszuras-rendezes]] — `foldr insert []`, $O(n^2)$
- [[concepts/funprog/merge-sort]] — felezés + `merge`, $O(n\log n)$
- [[concepts/funprog/quicksort]] — Haskell-egysoros, ZF-partícionálás
- [[concepts/funprog/nyolc-kiralyno]] — backtrack ZF-kifejezéssel

## Források

- Hutton: *Programming in Haskell* (2nd ed.) — kanonikus
- *Learn You a Haskell* (learnyouahaskell.com) — barátságos
- Haskell Wiki (wiki.haskell.org) — definíciók
- Haskell 2010 Report — szintaxis (margószabály)

## Kapocs

- [[index]] — wiki tartalomjegyzék
