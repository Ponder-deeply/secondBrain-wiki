---
tags: [concept]
sources: [szelmJegyzet.pdf]
derivation: source
updated: 2026-08-05
---

# Post megfelelkezési probléma (PMP)

A Post megfelelkezési probléma (dominóprobléma) azt kérdezi, hogy egy adott dominókészletből összerakható-e olyan sorozat, amelynek felső és alsó szava megegyezik; ez a probléma eldönthetetlen, és nem szól Turing-gépek tulajdonságáról.

## Definíció

Legyen $\Sigma$ legalább kétbetűs ábécé, és
$$D = \left\{ \left[\tfrac{u_1}{v_1}\right], \ldots, \left[\tfrac{u_n}{v_n}\right] \right\} \quad (n \geq 1)$$
egy **dominóhalmaz**, ahol $u_1, \ldots, u_n, v_1, \ldots, v_n \in \Sigma^+$.

A $D$ egy **megoldása** olyan $1 \leq i_1, \ldots, i_m \leq n$ ($m \geq 1$) indexsorozat, amelyre a dominókat egymás mellé írva felül és alul ugyanaz a szó adódik:
$$u_{i_1} \cdots u_{i_m} = v_{i_1} \cdots v_{i_m}.$$

Formális nyelvként:
$$\mathrm{PMP} = \{\langle D \rangle \mid D\text{-nek van megoldása}\}.$$

### Példa

- $D = \left[\tfrac{a}{baa}\right]\left[\tfrac{ab}{aa}\right]\left[\tfrac{bba}{bb}\right]$ egy megoldása a $3,2,3,1$ sorozat: $bba\,ab\,bba\,a = bb\,aa\,bb\,baa$.
- $D = \left[\tfrac{bb}{b}\right]\left[\tfrac{ab}{ba}\right]\left[\tfrac{a}{b}\right]$ készletnek nincs megoldása.

## Tétel: $\mathrm{PMP} \notin \mathrm{R}$

A bizonyítás két lépésből áll, egy segédfogalom — a **módosított Post megfelelkezési probléma (MPMP)** — közbeiktatásával. Az MPMP ugyanaz, mint a PMP, de a megoldásnak az **első dominóval $\left[\tfrac{u_1}{v_1}\right]$ kell kezdődnie**.

### 2.28. tétel: $\mathrm{MPMP} \leq \mathrm{PMP}$

Adott MPMP-példányhoz, $D = \{[\tfrac{u_1}{v_1}], \ldots, [\tfrac{u_n}{v_n}]\}$, konstruáljuk a $D'$ készletet két új ($D$-ben nem szereplő) $*$ és $\#$ szimbólummal:
$$D' = \left\{ \left[\tfrac{*u_1}{*v_1*}\right], \left[\tfrac{*u_1}{v_1*}\right], \left[\tfrac{*u_2}{v_2*}\right], \ldots, \left[\tfrac{*u_n}{v_n*}\right], \left[\tfrac{*\#}{\#}\right] \right\}.$$
A $*$ jelek beszúrása kikényszeríti, hogy $D'$ megoldása a $\left[\tfrac{*u_1}{*v_1*}\right]$ dominóval kezdődjön és a $\left[\tfrac{*\#}{\#}\right]$ dominóval végződjön; a köztes dominók $D$ egy MPMP-megoldásának felelnek meg.

### 2.29. tétel: $L_u \leq \mathrm{MPMP}$

Adott $M = (Q, \Sigma, \Gamma, \delta, q_i, q_n)$ Turing-géphez és $w \in \Sigma^*$ bemenethez olyan $D$ dominókészletet konstruálunk, amelynek pontosan akkor van megoldása, ha $\langle M, w \rangle \in L_u$. Az ötlet: a dominósorozat felső és alsó szava az $M$ egymást követő, $\#$-cal elválasztott **konfigurációit** kódolja, az alsó szó mindig egy konfigurációval előbb tart. A készlet részei:

1. **Kezdő dominó:** $\left[\tfrac{\#}{\#q_0 a_1 \ldots a_n\#}\right]$ (az $M$ kezdőkonfigurációja $w$-n).
2. **Átmenet-dominók:** minden $\delta$-átmenethez (jobbra, balra, helyben lépés) a megfelelő $\left[\tfrac{pa}{bq}\right]$, $\left[\tfrac{cpa}{qcb}\right]$, $\left[\tfrac{pa}{qb}\right]$ típusú dominó.
3. **Másoló dominók:** minden $a \in \Gamma$-ra $\left[\tfrac{a}{a}\right]$, valamint $\left[\tfrac{\#}{\#}\right]$ és $\left[\tfrac{\#}{\sqcup\#}\right]$ a szalag végének kezeléséhez.
4. **Záró dominók:** ha $M$ eléri a $q_i$ elfogadó állapotot, az $\left[\tfrac{aq_i}{q_i}\right]$, $\left[\tfrac{q_i a}{q_i}\right]$ típusú dominók „eltüntetik" a $q_i$ körüli szimbólumokat, és végül $\left[\tfrac{q_i\#\#}{\#}\right]$ zár, így a felső szó utoléri az alsót.

Ekkor $D$-nek pontosan akkor van (MPMP-)megoldása, ha $M$ elfogadja $w$-t, vagyis $\langle M, w \rangle \in L_u$.

A két visszavezetésből: $L_u \leq \mathrm{MPMP} \leq \mathrm{PMP}$, és mivel $L_u \notin \mathrm{R}$, a [[concepts/bvszam/visszavezetes|2.19. tétel]] alapján $\mathrm{PMP} \notin \mathrm{R}$.

## Kapocs

- [[concepts/bvszam/univerzalis-turing-gep]] — $L_u$, ahonnan a visszavezetés indul
- [[concepts/bvszam/visszavezetes]] — many-one visszavezetés
- [[concepts/bvszam/eldonthetetlen-problemak]] — további eldönthetetlen problémák
- [[concepts/bvszam/turing-gep]] — konfiguráció fogalma
- [[concepts/bvszam/kornyezetfuggetlen-grammatika]] — a PMP-re visszavezetett KF eldönthetetlenségi kérdések
