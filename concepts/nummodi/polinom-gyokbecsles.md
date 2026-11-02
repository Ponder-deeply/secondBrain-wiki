---
tags: [concept]
sources: [NM1_ea13.pdf]
derivation: source
kind: theorem
element: water
updated: 2026-09-25
---

# Becslés polinom gyökeinek elhelyezkedésére

Egy $n$-edfokú polinom minden (valós vagy komplex) gyöke az origó körüli $r < |x| < R$ nyílt körgyűrűben van, ahol $R$ a főegyütthatóval, $r$ a konstans taggal normált együttható-maximumból számolható. A felső korlát a háromszög-egyenlőtlenségből, az alsó a reciprok-polinomra alkalmazott felső korlátból adódik.

## Tartalom

### Feltételek

$$P(x) = a_nx^n + a_{n-1}x^{n-1} + \dots + a_1x + a_0, \qquad a_i \in \mathbb{R},\ a_0 \ne 0,\ a_n \ne 0.$$

- Az együtthatók akár komplexek is lehetnek; a bizonyításon ez nem változtat.
- Ha $a_0 = 0$, akkor $x = 0$ gyök, $x$-szel leosztva egyszerűbb polinomot vizsgálhatunk.
- Ha $a_n = 0$, akkor nem is $n$-edfokú.

### Tétel

**Tétel.** Ha $a_0 \ne 0$ és $a_n \ne 0$, akkor $P$ bármely $x_k$ gyökére

$$r < |x_k| < R, \qquad R = 1 + \frac{\max_{i=0}^{n-1}|a_i|}{|a_n|}, \qquad r = \frac{1}{1 + \dfrac{\max_{i=1}^{n}|a_i|}{|a_0|}}.$$

Ezzel a gyökök helyére egy origó középpontú nyílt körgyűrűt adtunk a komplex számsíkon.

### Bizonyítás

**1. Felső becslés.** Megmutatjuk: ha $|x| \ge R$, akkor $|P(x)| > 0$, tehát $x$ nem gyök. (Mivel $R > 1$, itt $|x| > 1$.)

A háromszög-egyenlőtlenség fordított alakjával:

$$|P(x)| \ge |a_nx^n| - \bigl|a_{n-1}x^{n-1} + \dots + a_1x + a_0\bigr|.$$

Lefelé becsülünk, ezért a kivonandót felülről becsüljük (háromszög-egyenlőtlenség, majd mértani sor):

$$\bigl|a_{n-1}x^{n-1} + \dots + a_0\bigr| \le |a_{n-1}||x|^{n-1} + \dots + |a_0| \le \max_{i=0}^{n-1}|a_i|\bigl(|x|^{n-1} + \dots + 1\bigr) = \max_{i=0}^{n-1}|a_i|\cdot\frac{|x|^n - 1}{|x| - 1} < \max_{i=0}^{n-1}|a_i|\cdot\frac{|x|^n}{|x| - 1}.$$

Így

$$|P(x)| > |a_n||x|^n - \max_{i=0}^{n-1}|a_i|\cdot\frac{|x|^n}{|x| - 1},$$

és ez a jobb oldal $\ge 0$ pontosan akkor, ha (szorozva $|x| - 1 > 0$-val és osztva $|a_n||x|^n$-nel)

$$|a_n||x|^n \ge \max_{i=0}^{n-1}|a_i|\frac{|x|^n}{|x| - 1} \iff |x| - 1 \ge \frac{\max_{i=0}^{n-1}|a_i|}{|a_n|} \iff |x| \ge 1 + \frac{\max_{i=0}^{n-1}|a_i|}{|a_n|} = R.$$

Tehát $|x| \ge R \Rightarrow |P(x)| > 0$, vagyis minden gyökre $|x_k| < R$.

**2. Alsó becslés — reciprok-polinom.** Legyen $y := \tfrac1x$ ($x \ne 0$; $a_0 \ne 0$ miatt a $0$ nem gyök):

$$P(x) = a_n\Bigl(\frac1y\Bigr)^n + a_{n-1}\Bigl(\frac1y\Bigr)^{n-1} + \dots + a_1\frac1y + a_0 = \Bigl(\frac1y\Bigr)^n\underbrace{\bigl(a_n + a_{n-1}y + \dots + a_1y^{n-1} + a_0y^n\bigr)}_{Q(y)} = x^n\,Q\Bigl(\frac1x\Bigr).$$

$Q$ a $P$ **reciprok-polinomja**: főegyütthatója $a_0$, konstans tagja $a_n$. Ekkor $P(x_k) = 0 \iff Q(1/x_k) = 0$, azaz $Q$ gyökei $P$ gyökeinek reciprokai.

Az 1. részt $Q$-ra alkalmazva (főegyüttható $a_0$, a többi együttható $a_1,\dots,a_n$):

$$\frac{1}{|x_k|} < 1 + \frac{\max_{i=1}^n|a_i|}{|a_0|} = \frac1r \implies |x_k| > r. \ \square$$

### Vizsgán (28. tétel, a))

A tétel kimondása és teljes bizonyítása: felső korlát a kétféle háromszög-egyenlőtlenséggel és a mértani összeggel, alsó korlát a reciprok-polinommal. A b) rész a [[concepts/nummodi/horner-algoritmus]].

## Kapocs

- [[concepts/nummodi/horner-algoritmus]] — a 28. tétel b) része: polinom és deriváltjai értékének kiszámítása
- [[concepts/nummodi/newton-modszer]] — gyökkereső, amelynek kezdőpontjához a becslés tartományt ad
- [[concepts/nummodi/intervallumfelezes]] — gyökkeresés egy előjelváltó intervallumon
