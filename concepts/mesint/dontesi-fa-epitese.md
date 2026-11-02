---
tags: [concept]
sources: [11.gepi_tanulas.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-12
---

# Döntési fa és építése

A döntési fa attribútum-érték párokkal jellemzett bemenetekhez kimenetet rendelő irányított fa; tanító mintákból, csúcsonként attribútumot választva építjük fel, minél hamarabb levélcsúcsokat előállítva.

## Tartalom

### A döntési fa

Feltesszük, hogy a bemenetek tulajdonságait (attribútumainak értékeit) ismerjük, azaz egy bemenetet attribútum-érték párok halmazával jellemezhetünk. A fa:

- **belső csúcsai** egy-egy attribútumot szimbolizálnak, a kivezető éleket az attribútum lehetséges értékei címkézik;
- **ágai** attribútum-érték párok halmazát jelölik ki;
- **levelei** egy-egy lehetséges kimeneti értéket mutatnak.

Egy $x$ bemenet az attribútum-érték párjai alapján egyértelműen leképezhető a fa egyik levelére, amely a kimenetet adja.

Példa (a diákon): *elfogadjuk-e a megajánlott vizsgajegyet?* Attribútumok: hányast ajánlottak (3, 4, 5), kevés vizsgánk van-e, kell-e átlagot javítani, az MI tárgyról van-e szó, értettük-e az előadást. A gyökér „Hányas?"; ötösnél „Igen", négyesnél tovább „Kevés vizsgánk van?" kérdések, hármasnál „Kell átlagot javítani?" (igen: Nem, nem: Igen).

### Építés tanító mintákból

- Minden csúcshoz hozzárendeljük azokat a tanító mintákat, amelyek a csúcshoz vezető ág attribútum-érték párjaival rendelkeznek.
- Egy csúcs úgy válik belső csúccsá, hogy egy – a hozzávezető ágon még nem szereplő – attribútummal címkézzük fel.
- Egy csúcsot véglegesen **levélcsúcsnak** nyilváníthatunk, ha nincsenek tanító mintái, vagy mind hasonló kimenetűek, vagy a hozzávezető ágon már minden attribútum szerepel.
- A levélcsúcs értéke a hozzá tartozó minták kimeneteinek átlaga vagy leggyakoribb kimenete. (Ha nincs minta, vagy nem egyértelmű a leggyakoribb, a szülőcsúcs mintái alapján számolunk.)

### Étterem probléma (Russell-Norvig)

12 minta, attribútumok: Más (van-e másik étterem a közelben), Bár, P/Sz, Éhes, Hány (vendég: senki/kevés/tele), Ár, Eső, Fogl (foglalás), Fajt (Fra/Tha/Bur/Ol), Idő (várakozás), kimenet: Marad. Pozitív: 1,3,4,6,8,12; negatív: 2,5,7,9,10,11.

Első lépés: a *Hány* attribútum szerint három ág: senki ($-$: 7,11 → Nem), kevés ($+$: 1,3,6,8 → Igen), tele ($+$: 4,12; $-$: 2,5,9,10 → tovább kell bontani). A *Hány* jónak tűnik, mert csak egy olyan új csúcs lesz, amely még nem levél, és annak mintái nem fele-fele arányban igen-nem értékűek. A *Más* vagy a *Fajt* mind a gyerekcsúcsokban kevert mintákat adna.

Fontos: ugyanahhoz a problémához több döntési fa is megadható, és a **lehető legkisebb döntési fa megtalálása NP-teljes**, ezért heurisztikát használunk.

### Heurisztika az attribútum-választáshoz

Egy fa annál kisebb (annál hamarabb találunk benne illeszkedő levelet), minél rövidebbek az ágai. Ezért minél hamarabb levélcsúcsokat próbálunk képezni, ehhez a csúcs mintáinak kimenetei közt kicsi legyen az eltérés (2-es norma) vagy minél kevésbé legyenek változatosak (entrópia). Olyan attribútumot választunk, amely mellett a gyerekcsúcsok minta-halmazai összességében a legkisebb eltérésű kimenetekkel rendelkeznek; ezt az [[concepts/mesint/informacio-nyereseg]] méri.

## Kapocs

- [[concepts/mesint/informacio-nyereseg]] — az attribútum-választás mértéke
- [[concepts/mesint/dontesi-fa-tanulo-algoritmus]] — a teljes rekurzív algoritmus
- [[concepts/mesint/felugyelt-tanulas]] — a keret
- [[concepts/bigdata/dontesi-fa]] — a big data-s tárgyalás (osztályozó modell)
- [[concepts/mesint/veletlen-erdo]] — döntési fák együttese
