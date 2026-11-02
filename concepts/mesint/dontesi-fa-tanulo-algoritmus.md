---
tags: [concept]
sources: [11.gepi_tanulas.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-12
---

# Döntési fa tanuló algoritmusa

A döntési fát fokozatosan építjük: minden lépésben egy még értékkel nem rendelkező levélcsúcsról döntjük el, hogy értéket kap-e, vagy attribútummal címkézett belső csúccsá válik. A kész fa $x$-re adott értéke a hozzá tartozó levél mintáiból számolható.

## Tartalom

### Az építés adatszerkezete

Az épülő fában minden csúcsnál eltároljuk:

- a csúcshoz tartozó **tanító mintákat** (azokat, amelyek rendelkeznek a csúcshoz vezető ág attribútum-érték párjaival);
- a csúcsnál még **választható attribútumokat** (azokat, amelyek nem szerepelnek a csúcshoz vezető út csúcsainak címkéi között).

Egy csúcs lehet attribútummal címkézett **belső csúcs** (a kivezető éleket az attribútum lehetséges értékei címkézik), vagy **kiértékelt / értékkel még nem rendelkező levélcsúcs**.

### Az algoritmus

Kezdetben a fa egyetlen címkézetlen csúcsból áll (ez a gyökér), amelyhez az összes mintát és attribútumot rendeljük. Amíg van értékkel még nem rendelkező levélcsúcs, veszünk egyet, és:

1. Ha nincsenek mintái ($P=\emptyset$), a **szülőcsúcs mintái** alapján számoljuk ki a csúcs értékét.
2. Ha a csúcshoz tartozó minták kimenete nem nagyon tér el egymástól, ezekből számoljuk ki a csúcs értékét.
3. Ha nincsenek választható attribútumai ($A=\emptyset$), a csúcs mintái alapján számoljuk ki az értékét.
4. Egyébként a választható attribútumok közül a **legkedvezőbbnek** látszóval megcímkézzük a csúcsot, és generáljuk a gyerekeit az azokhoz tartozó mintákkal és választható attribútumokkal együtt.

A „legkedvezőbb" attribútum kiválasztását lásd [[concepts/mesint/informacio-nyereseg]].

### Példa: az étterem probléma

A diák étterem-példájában (várjunk-e az asztalra?) a gyökér a „Hány" attribútum (senki / kevés / tele): „senki" esetén *Nem*, „kevés" esetén *Igen*. A „tele" ágon a minták (+: 4, 12; −: 2, 5, 9, 10) még vegyesek, ezért a maradék attribútumok (Más, Bár, P/Sz, Éhes, Ár, Eső, Fogl, Fajt, Idő) közül az „Éhes" kerül a következő csúcsba. Az „Éhes = nem" ág tiszta (mind negatív), ezért *Nem*; az „Éhes = igen" ág (+: 4, 12; −: 2, 10) tovább bomlik. A végső fában: Hány → tele → Éhes → igen → Fajt (Fra: Igen, Ol: Nem, Thai: P/Sz-től függően Igen/Nem, Burg: Igen).

### Megjegyzések

- **Zaj**: azonos attribútum-értékű minták kimenete különbözik; ilyenkor a minták válaszainak átlagolása félrevezethet.
- **Túlzott illeszkedés** (overfitting): olyan attribútumokat is figyelembe veszünk, amelyek a kimenetre nincsenek hatással (pl. kockadobás eredményéhez a kocka színe, a dobás dátuma). A lényegtelen attribútumokat ($C(P,a)\approx 0$) félre kell állítani.
- **Általánosítások**: hiányzó adatok (attribútum-értékek) problémája; folytonos értékű attribútumok.

### Tanulás döntési fával

Az $x \in X$ bemenetre a levélcsúcs értéke, ahol $P(x)$ az $x$-re kiszámolt levélcsúcs tanító mintáinak bemeneteiből álló halmaz:

$$f(\Theta, x) = \sum_{n=1..N} \frac{\mathbb{I}(x_n \in P(x))}{|P(x)|}\cdot y_n$$

(átlag, regresszió), illetve osztályozásnál a leggyakoribb érték:

$$f(\Theta, x) = \arg\max_{y} \sum_{x_i \in P(x),\ \varphi(x_i)=y} 1 .$$

$\Theta$ maga a döntési fa; „optimalizálása" a mohó felépítése.

- **Előny**: jól értelmezhető (a mintákra tökéletes, a hasonló inputokra többnyire jó eredményt ad); a tanító minták helyett csak a fát kell tárolni; az $x$-re adott eredmény gyorsan számolható.
- **Hátrány**: az optimális döntési fa építése NP-teljes; a mohó módszerrel csak lokálisan optimális fához jutunk.

## Kapocs

- [[concepts/mesint/dontesi-fa-epitese]] — a döntési fa fogalma és építésének alapjai
- [[concepts/mesint/informacio-nyereseg]] — attribútumválasztás a „legkedvezőbb" kritériummal
- [[concepts/mesint/veletlen-erdo]] — sok fa együtt, a mohóság és túltanulás csökkentésére
- [[concepts/mesint/felugyelt-tanulas]] — a tanítási keret
- [[concepts/bigdata/dontesi-fa]] — általános (nagy adat) tárgyalás
