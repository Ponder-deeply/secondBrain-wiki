---
tags: [concept]
sources: [DimatIIEa05.pdf, DimatIIEa06.pdf]
derivation: source
updated: 2026-09-08
---

# Polinomok maradékos osztása

Egységelemes integritási tartomány fölött egy polinom egyértelműen elosztható maradékosan egy olyan polinommal, amelynek főegyütthatója egység — a maradék foka az osztóénál kisebb.

## Tartalom

### A tétel

**Tétel.** Legyen $R$ egységelemes integritási tartomány, $f, g \in R[x]$, és tegyük fel, hogy $g$ főegyütthatója egység $R$-ben. Ekkor **egyértelműen léteznek** olyan $q, r \in R[x]$ polinomok, melyekre

$$f = qg + r, \qquad \deg(r) < \deg(g).$$

A $q$ polinom a maradékos osztás **hányadospolinomja**, az $r$ polinom az osztási **maradékpolinom**. A tétel az $f$ polinom $g$-vel való maradékos elosztásának egyértelmű elvégezhetőségét mondja ki.

A főegyütthatóra tett kikötés lényeges: az eljárás minden lépésben az osztó főegyütthatójával kell osztani. Test fölött ez automatikusan teljesül minden nem-nulla $g$-re, mert testben minden nem-nulla elem egység.

### Létezés

$f$ foka szerinti teljes indukció. Ha $\deg(f) < \deg(g)$, akkor $q = 0$ és $r = f$ megfelelő előállítás.

Legyen $\deg(f) = n$, $f$ főegyütthatója $f_n$, $g$ főegyütthatója $g_k$, és $n \ge k$. Legyen

$$f^*(x) = f(x) - f_n g_k^{-1} g(x) x^{n-k}.$$

Ekkor $\deg(f^*) < \deg(f)$ (a főtagok kiejtik egymást), így az indukciós feltevés használható $f^*$-ra: léteznek $q^*, r^* \in R[x]$, amikre $f^* = q^*g + r^*$. Ebből

$$f(x) = f^*(x) + f_n g_k^{-1} g(x) x^{n-k} = q^*(x)g(x) + r^*(x) + f_ng_k^{-1}g(x)x^{n-k},$$

vagyis $q = q^* + f_n g_k^{-1} x^{n-k}$ és $r = r^*$ jó választás.

### Egyértelműség

Tekintsük $f$ két megfelelő előállítását: $f = qg + r = q^*g + r^*$. Ebből

$$g(q - q^*) = r^* - r.$$

Ha a bal oldal nem $0$, akkor foka legalább $k = \deg(g)$, de a jobb oldal foka legfeljebb $k-1$. Ez csak úgy lehetséges, ha $0 = g(q-q^*) = r^* - r$, és így $q = q^*$ és $r = r^*$. $\square$

## Kapocs

- [[concepts/dimatii/polinom-foka]] — a maradék fokára tett kikötés az egyértelműség kulcsa
- [[concepts/dimatii/integritasi-tartomany]] — a tétel feltétele
- [[concepts/dimatii/horner-elrendezes]] — az $(x-c)$-vel való maradékos osztás gyakorlati elvégzése
- [[concepts/dimatii/gyoktenyezo-es-gyokok-szama]] — a tétel közvetlen következményei
- [[concepts/dimatii/polinomok-bovitett-euklideszi-algoritmusa]] — a maradékos osztásra épülő eljárás
