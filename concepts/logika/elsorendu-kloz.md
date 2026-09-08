---
tags: [concept]
sources: [Rezolúció_II.pdf]
references: [Tk. 251-254. o.]
derivation: source
updated: 2026-09-08
---

# Elsőrendű klóz

Az elsőrendű klóz olyan zárt [[concepts/logika/skolem-normalforma|Skolem formula]], amelynek magja az elsőrendű nyelv literáljainak diszjunkciója; tetszőleges elsőrendű formula felírható elsőrendű klózok konjunkciójaként, ami a kielégíthetetlenség eldöntését az ítéletlogikai [[concepts/logika/kloz-es-klozhalmaz|klózhalmaz]]-vizsgálat elsőrendű általánosítására vezeti vissza.

## Tartalom

### Fogalom

**Elsőrendű klóz:** olyan zárt Skolem formula, amelynek magja az elsőrendű nyelv literáljainak diszjunkciója. Példa: $\forall x \forall y (P(x) \vee \lnot Q(x, f(y)))$.

Az ítéletlogikai klózhalmaz (KNF) elsőrendű megfelelője az **elsőrendű klózhalmaz** — elsőrendű klózok konjunkciója.

### Formula felírása elsőrendű klózok konjunkciójaként

A feladat: tetszőleges elsőrendű formula átírása elsőrendű klózok konjunkciós formulájává. Az eldöntésprobléma: az így kapott elsőrendű klózhalmaz kielégíthetetlenségének eldöntése. Az eljárás három lépésből áll:

1. tetszőleges formula átírható [[concepts/logika/prenex-forma|prenex alakba]];
2. tetszőleges prenex formula átírható [[concepts/logika/skolem-normalforma|Skolem alakba]];
3. tetszőleges Skolem normálforma felírható elsőrendű klózok konjunkciójaként — a Skolem formula magja KNF, az elsőrendű nyelv literáljaiból felírt klózok konjunkciós lánca, amelyre a 3. kvantorkiemelési szabály ([[concepts/logika/prenex-forma]]) alkalmazható.

**Példa:** a $\forall x \forall y \forall y_1\big((\lnot P(x,y) \vee Q(y_1)) \wedge (R(y, f(x)) \vee P(x,a)) \wedge (P(x,y_1) \vee \lnot R(x,y))\big)$ Skolem formula elsőrendű klózok konjunkciós lánc alakja:

$$\forall x \forall y \forall y_1(\lnot P(x,y) \vee Q(y_1)) \wedge \forall x \forall y \forall y_1(R(y, f(x)) \vee P(x,a)) \wedge \forall x \forall y \forall y_1(P(x,y_1) \vee R(x,y))$$

### Változóidegenné tétel

Mivel egy kvantált formula értéke nem függ a benne szereplő kötött változó nevétől, a klózok kötött változói egymástól függetlenül átnevezhetők — **változóidegen klózok konjunkciója** áll elő. Ezután az egyes klózok magja önmagában, a közös prefixum nélkül is felírható klózhalmazként, pl.

$$\{(\lnot P(x,y) \vee \lnot Q(y_1)),\ (R(w, f(z)) \vee P(z,a)),\ (P(v,y_3) \vee \lnot R(v,z_1))\}$$

### Kielégíthetőség és a mag kifejtése

Ha egy univerzális formulát kifejtünk egy $U$ univerzum felett, a mag alappéldányainak konjunkciója $U$-ekvivalens lesz az eredeti formulával. Ha elsőrendű klózok halmazával tesszük ugyanezt, **alapklózok halmazát** kapjuk — a kifejtett klózhalmaz kielégíthetetlensége ekvivalens a kapott $U$ feletti alapklózok halmazának kielégíthetetlenségével. Az alapklózokra a rezolúciós kalkulus ugyanúgy definiálható, mint az ítéletlogikában: **alaprezolúció** (Tk. 251-254. o.) — alaprezolúcióval bármely adott $U$ univerzumon való kielégíthetetlenség eldönthető.

### Kielégíthetőség és az $U$ számossága

- Ha egy formula azonosan igaz $|U| = n$ számosságon, akkor ennél kisebb számosságon is azonosan igaz (Tk. 257. o.).
- Ha egy formula kielégíthető $|U| = n$ számosságon, akkor ennél nagyobb számosságon is kielégíthető (Tk. 258. o.).
- **Löwenheim–Skolem tétel** (Tk. 258. o.): ha egy formula egyáltalán kielégíthető, akkor kielégíthető legfeljebb megszámlálhatóan végtelen $U$ univerzumon.

A kielégíthetetlenségre hasonló tételek **nincsenek**: nincs olyan általános $U$, amelyen való kielégíthetetlenség biztosítaná a kielégíthetetlenséget minden univerzumon (Tk. 254. o./6.3.45. példa). A klózhalmaz leíró nyelvének függvény- és konstansszimbólumaiból azonban felépíthető egy szimbolikus, az ábécé által meghatározott $U_H$ univerzum, amely biztosítja a kielégíthetetlenséget — ez a [[concepts/logika/herbrand-univerzum|Herbrand univerzum]].

**Példa:** a $\forall x \forall y \exists z\big((P(x,y) \supset \lnot P(y,x)) \wedge (P(x,z) \vee P(z,y))\big)$ formula nem elégíthető ki kételemű univerzumon, de háromelemű univerzumon már kielégíthető — ez mutatja, hogy a kielégíthetőség számosságfüggő, és igazolja a fenti tételek szükségességét.

## Kapocs

- [[concepts/logika/prenex-forma]] — az első átalakítási lépés
- [[concepts/logika/skolem-normalforma]] — a második átalakítási lépés, amelynek magjából a klóz felírható
- [[concepts/logika/kloz-es-klozhalmaz]] — az ítéletlogikai klóz, amelynek elsőrendű általánosítása ez a fogalom
- [[concepts/logika/herbrand-univerzum]] — az univerzum, amelyen a kielégíthetetlenség eldönthető
- [[concepts/logika/elsorendu-rezolucio]] — a klózhalmazon végzett elsőrendű rezolúciós levezetés
