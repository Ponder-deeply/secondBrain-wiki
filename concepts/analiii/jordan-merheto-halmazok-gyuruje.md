---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# A Jordan-mérhető halmazok halmazgyűrűje

A Jordan-mérhető halmazok $\mathcal{J}_p$ rendszere zárt a véges unióra, metszetre és különbségre, tehát halmazgyűrű; rajta a Jordan-térfogat az egyetlen pozitív, additív, normált és eltolásinvariáns halmazfüggvény.

## Tartalom

### Zártság a halmazműveletekre

**Tétel.** Ha $A, B \subset \mathbb{R}^p$ mérhetők, akkor $A \cup B$, $A \cap B$ és $A \setminus B$ is mérhető.

**Bizonyítás (unióra).** Halmazelméleti azonosságokból

$$\operatorname{cl}(A \cup B) \subset (\operatorname{cl} A) \cup (\operatorname{cl} B), \qquad \operatorname{int}(A \cup B) \supset (\operatorname{int} A) \cup (\operatorname{int} B),$$

ezért

$$\partial(A \cup B) = \operatorname{cl}(A\cup B) \setminus \operatorname{int}(A \cup B) \subset (\operatorname{cl} A \setminus \operatorname{int} A) \cup (\operatorname{cl} B \setminus \operatorname{int} B) = \partial A \cup \partial B.$$

Mivel $\partial A$ és $\partial B$ nullmértékű, $\partial(A \cup B)$ is az, tehát $A \cup B$ mérhető. A metszetre és a különbségre ugyanez a gondolatmenet megy. $\square$

### Additivitás

**Tétel.** Ha $A, B$ mérhetők és $(\operatorname{int} A) \cap (\operatorname{int} B) = \emptyset$, akkor

$$t(A \cup B) = t(A) + t(B).$$

**Bizonyítás.** A szubadditivitást és a szuperadditivitást összefűzve

$$b(A \cup B) \leq k(A \cup B) \leq k(A) + k(B) = t(A) + t(B) = b(A) + b(B) \leq b(A \cup B),$$

tehát végig egyenlőség áll. $\square$

Figyeljük meg, hogy nem teljes diszjunktságot követelünk, csak azt, hogy a halmazok *egymásba ne nyúljanak* — közös határdarabjuk lehet, az úgyis nullmértékű.

### Eltolásinvariancia

Ha $A$ mérhető és $v \in \mathbb{R}^p$, akkor $A + v = \{x + v : x \in A\}$ is mérhető, és $t(A+v) = t(A)$. A bizonyítás egyszerű: a külső és belső mérték definíciójában szereplő belső és fedő téglákat is eltolhatjuk $v$-vel.

### A $\mathcal{J}$ halmazgyűrű

Legyen

$$\mathcal{J} = \mathcal{J}_p = \{A \subset \mathbb{R}^p : A \text{ Jordan-mérhető}\}.$$

Ekkor

- $\emptyset \in \mathcal{J}$;
- bármely $A, B \in \mathcal{J}$-re $A \cup B,\ A \cap B,\ A \setminus B \in \mathcal{J}$, tehát $\mathcal{J}$ **halmazgyűrű**;
- $\prod_{i=1}^{p}[a_i,b_i] \in \mathcal{J}$;
- a $\mathcal{J}$ halmazgyűrűn a térfogat pozitív, additív, normált és eltolásinvariáns;
- a $\mathcal{J}$ halmazgyűrűn a Jordan-térfogat az **egyetlen** pozitív, additív, normált és eltolásinvariáns függvény (házi feladat).

Ez az egyértelműségi állítás a fejezet célja: a bevezetőben megfogalmazott elvárások $\mathcal{J}_p$-n pontosan egy térfogatfogalmat engednek meg.

## Kapocs

- [[concepts/analiii/jordan-nullmerteku-halmazok]] — a zártsági tétel a $\partial(A \cup B) \subset \partial A \cup \partial B$ tartalmazáson és a nullmértékűségen múlik
- [[concepts/analiii/kulso-belso-mertek-tulajdonsagai]] — az additivitás bizonyítása a szubadditivitást és szuperadditivitást fűzi össze
- [[concepts/analiii/jordan-mertek-linearis-transzformaltja]] — az eltolásinvariancia általánosítása tetszőleges lineáris leképezésre
- [[concepts/analiii/jordan-mertek-szerinti-integral]] — az integrál értelmezési tartománya mindig egy $\mathcal{J}_p$-beli halmaz
