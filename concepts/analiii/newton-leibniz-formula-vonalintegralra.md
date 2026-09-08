---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Newton–Leibniz-formula valós vonalintegrálokra

Ha az $f$ vektormezőnek van $F$ primitív függvénye, akkor bármely szak.$C^1$ görbén $\int_\gamma f = F(\gamma(b)) - F(\gamma(a))$: a vonalintegrál csak a görbe végpontjaitól függ.

## Tartalom

### A tétel

**Tétel.** Legyen $G \subset \mathbb{R}^p$ nyílt, $f : G \to \mathbb{R}^p$ folytonos vektormező, $\gamma : [a,b] \to G$ szak.$C^1$ görbe, és tegyük fel, hogy $F : G \to \mathbb{R}$ primitív függvénye $f$-nek (azaz $f = \operatorname{grad} F$). Ekkor

$$\int_\gamma f = F(\gamma(b)) - F(\gamma(a)).$$

A jobb oldalon **semmi** nem szerepel a görbéből azon kívül, hogy hol kezdődik és hol végződik. Ez a fejezet központi állítása: primitív függvény létezése esetén a vonalintegrál **úttól független**.

### Bizonyítás

Az állítást visszavezetjük a klasszikus, egyváltozós Newton–Leibniz-formulára.

Legyen $a = a_0 < a_1 < \dots < a_n = b$ olyan felosztás, hogy minden $i$-re $\gamma_i = \gamma|_{[a_{i-1},a_i]}$ folytonosan differenciálható. Egy ilyen darabon, a vonalintegrál kiszámítási formulájával és a **láncszabállyal**:

$$\int_{\gamma_i} f = \int_{t=a_{i-1}}^{a_i}\bigl\langle f(\gamma(t)); \dot\gamma(t)\bigr\rangle\,\mathrm{d}t = \int_{t=a_{i-1}}^{a_i}\bigl\langle (\operatorname{grad} F)(\gamma(t)); \dot\gamma(t)\bigr\rangle\,\mathrm{d}t = \int_{t=a_{i-1}}^{a_i}\bigl(F\circ\gamma\bigr)'(t)\,\mathrm{d}t,$$

hiszen az $F \circ \gamma$ összetett függvény deriváltja éppen $\bigl\langle (\operatorname{grad} F)(\gamma(t)); \dot\gamma(t)\bigr\rangle$. Az egyváltozós Newton–Leibniz-formula szerint ez

$$= F(\gamma(a_i)) - F(\gamma(a_{i-1})).$$

Összegezve, teleszkopikus összeggel:

$$\int_\gamma f = \sum_{i=1}^{n}\int_{\gamma_i} f = \sum_{i=1}^{n}\Bigl(F(\gamma(a_i)) - F(\gamma(a_{i-1}))\Bigr) = F(\gamma(b)) - F(\gamma(a)).$$

A bizonyítás lényege tehát: a **láncszabály** alakítja a $\langle \operatorname{grad} F; \dot\gamma\rangle$ integrandust egy egyváltozós függvény deriváltjává, onnantól az egyváltozós tétel dolgozik.

### Következmények

- Zárt görbén ($\gamma(a) = \gamma(b)$) a vonalintegrál $0$.
- Közös végpontú görbéken a vonalintegrál megegyezik.
- Két primitív függvény különbsége konstans (a különbségre a formulát felírva).

Ezek a következmények éppen a konzervatív vektormezőt jellemző tulajdonságok — a nagy ekvivalenciatételben az „$\text{(a)} \Rightarrow$ minden más" irány mind ebből a formulából jön.

### Potenciálfüggvénnyel

Ha $F$ nem primitív, hanem **potenciál**függvény ($f = -\operatorname{grad} F$), akkor a formula

$$\int_\gamma f = F(\gamma(a)) - F(\gamma(b)),$$

vagyis a végzett munka a helyzeti energia csökkenése — ez a negatív előjel értelme.

## Kapocs

- [[concepts/analii/newton-leibniz-tetel]] — az egyváltozós tétel, $\int_a^b f = F(b) - F(a)$. A mostani formula szó szerint ennek a görbés általánosítása, és a bizonyítása is erre vezeti vissza: az $[a,b]$ intervallum helyére egy irányított görbe, a $F'$ helyére a $\operatorname{grad} F$ lép, de a „végpontok különbsége" alak változatlan.
- [[concepts/analiii/vektormezo-primitiv-fuggvenye]] — a formulában szereplő $F$ fogalma.
- [[concepts/analiii/valos-vonalintegral]] — a bal oldal; a bizonyítás a kiszámítási formuláját használja.
- [[concepts/analiii/konzervativ-vektormezo]] — a formula következményeinek megfordítása.
