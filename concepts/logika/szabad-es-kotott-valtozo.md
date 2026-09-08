---
tags: [concept]
sources: ["Elsőrendű_logika_ bevezetés.pdf"]
derivation: source
updated: 2026-09-08
---

# Szabad és kötött változó

Egy elsőrendű formulában egy individuumváltozó-előfordulás szabad vagy kötött aszerint, hogy esik-e az adott változóra vonatkozó kvantor hatáskörébe; ez a megkülönböztetés dönti el, hogy a formula elsőrendű (zárt) vagy paraméteres (nyitott) állítást szimbolizál-e.

## Tartalom

### Előfordulás: szabad vagy kötött

Egy [[concepts/logika/elsorendu-formula|formulában]] egy $x$ változó egy előfordulása

- **szabad**, ha nem esik az $x$-re vonatkozó kvantor hatáskörébe,
- **kötött**, ha az $x$-re vonatkozó kvantor hatáskörébe esik.

(A kvantor hatásköre a $QxA$ alakú kvantált formulában maga az $A$ törzs — lásd [[concepts/logika/elsorendu-formula]].)

### Változó: szabad, kötött vagy vegyes

Egy $x$ változó egy formulában

- **kötött változó**, ha $x$ minden előfordulása kötött,
- **szabad változó**, ha $x$ minden előfordulása szabad,
- **vegyes változó**, ha $x$-nek van szabad és kötött előfordulása is.

*Megjegyzés:* ha egy formulában egy változó kötött, a formulában elő nem forduló változónévre átnevezve a formula ekvivalens marad az eredetivel. Ily módon minden formula átírható változóátnevezésekkel olyan formulává, amely már nem tartalmaz vegyes változót.

### Példa

A $\forall xP(x) \supset \exists yQ(w,y) \vee P(v) \supset \forall zQ(w,z)$ formula prímkomponensei: $\forall xP(x)$, $\exists yQ(w,y)$, $P(v)$, $\forall zQ(w,z)$. A szabad individuumváltozók: $v$, $w$.

### Zártság és nyitottság

- Egy formula **zárt**, ha minden változója kötött.
- Egy formula **nyitott**, ha legalább egy individuumváltozónak van legalább egy szabad előfordulása.
- Egy formula **kvantormentes**, ha nem tartalmaz kvantort.

Az elsőrendű ($L$) nyelven az **1. rendű állításokat** a zárt formulák — más néven **mondatok** — szimbolizálják; a nyitott formulák a [[concepts/logika/nulladrendu-es-elsorendu-allitas|paraméteres állításoknak]] felelnek meg.

## Kapocs

- [[concepts/logika/elsorendu-formula]] — a formula, amelyben az előfordulások szabadsága/kötöttsége értelmezve van
- [[concepts/logika/nulladrendu-es-elsorendu-allitas]] — a zárt formula mint elsőrendű állítás, a nyitott formula mint paraméteres állítás
- [[concepts/logika/term]] — a term, amelynek argumentumaiban a változók előfordulnak
