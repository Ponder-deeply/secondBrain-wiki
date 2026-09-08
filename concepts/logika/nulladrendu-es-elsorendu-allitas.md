---
tags: [concept]
sources: ["Elsőrendű_logika_ bevezetés.pdf"]
derivation: source
updated: 2026-09-08
---

# Nulladrendű és elsőrendű állítás

A kijelentő mondat alanya szerint különböztetjük meg a konkrét dologról szóló **nulladrendű** és a halmazról szóló **elsőrendű** állítást; ez a különbség indokolja, hogy az ítéletlogikán túl kell lépni.

## Tartalom

### Amit az ítéletlogika nem lát

Az ítéletlogikában az állításokat oszthatatlan egészként kezeltük: egy ítéletváltozó igazságértéket hordoz, de a *belső szerkezetéről* — miről szól, milyen dologra vonatkozik — semmit nem mond. Az állítások **minősítésével** és **leírásával** az ítéletlogika nem foglalkozik. Ezért olyan következtetések, amelyek éppen a belső szerkezeten múlnak („minden ember halandó”, „Szókratész ember”, tehát „Szókratész halandó”), az ítéletlogika eszközeivel nem formalizálhatók: három, egymással semmilyen kapcsolatban nem álló ítéletváltozó marad belőlük.

### Nulladrendű állítás

Ha a kijelentő mondat **alanya valamely konkrét dolog**, akkor az állítás **nulladrendű**. Formális leírásukra relációt (logikai függvényt) definiálunk, például:

- $E(x) = i$, ha $x$ egész szám,
- $P(x) = i$, ha $x$ prímszám,
- $L(x, y, z) = i$, ha $z$ az $x$ és az $y$ legnagyobb közös osztója.

Maga az állítás a **konkrét egyedekkel behelyettesített reláció**: $E(9)$ és $L(9,6,3)$ állítás. Ezzel szemben $L(9,6,z)$ *nem* állítás, mert nincs igazságértéke, amíg $z$ értéke ismeretlen — ezt **paraméteres állításnak** nevezzük.

### Elsőrendű állítás

Ha a kijelentő mondat **alanya egy halmaz**, akkor az állítás **elsőrendű**. Az ilyen állítás vagy a halmaz *összes* elemére egyidejűleg fennálló megállapítást (általánosítás), vagy a halmaz *bizonyos* — nem feltétlenül minden — elemére fennálló megállapítást (létezés) fogalmaz meg. Leírásukhoz a **kvantorokat** ($\forall$, $\exists$) használjuk:

- $\forall x\,E(x)$: a halmaz minden eleme egész szám,
- $\exists x\,P(x)$: a halmazban van olyan elem, amely prímszám.

### Miért ez a felépítés sorrendje

A két állításfajta pontosan azt a két eszközkészletet jelöli ki, amit az elsőrendű nyelvnek biztosítania kell: a nulladrendű (és paraméteres) állításokhoz **nevekre** van szükség — relációk, műveletek és megjelölt elemek nevére —, az elsőrendűekhez pedig **individuumváltozókra és kvantorokra**. Ez a leíró nyelv ábécéjének logikán kívüli, illetve logikai része; lásd [[concepts/logika/leiro-nyelv-es-szignatura]].

A dolgok, amelyekről az állítások szólnak, a [[concepts/logika/matematikai-struktura]] univerzumából valók: a szintaxis nem önmagában áll, hanem egy struktúra leírásának eszköze.

## Kapocs

- [[concepts/logika/matematikai-struktura]] — az a struktúra, amelyről az állítások szólnak
- [[concepts/logika/leiro-nyelv-es-szignatura]] — a nyelv, amely mindkét állításfajtát leírja
- [[concepts/logika/elsorendu-formula]] — az állítások formális megfelelője
- [[concepts/logika/szabad-es-kotott-valtozo]] — a zárt formula szimbolizálja az elsőrendű állítást, a nyitott a paraméteres állítást
- [[concepts/logika/iteletlogikai-formula]] — az a formulafogalom, amelyen az elsőrendű túllép
- [[concepts/bvszam/elsorendu-logika]] — ugyanezen anyag tömör, halmazelméleti felépítése a bvszam kurzuson
