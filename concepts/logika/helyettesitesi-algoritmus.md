---
tags: [concept]
sources: [Szabo-Ivan-Elsorendu-logika-egyetemi-jegyzet.pdf]
derivation: source
kind: procedure
element: water
updated: 2026-10-21
---

# Helyettesítési algoritmus és helyettesítési lemma

A helyettesítési algoritmus az $F$ formulából szintaktikusan előállítja az $F[x/t]$ formulát úgy, hogy az $x$ változó értékének átállítása $t$ értékére a struktúrában ugyanazt adja, mint az $F[x/t]$ kiértékelése az eredeti struktúrában.

## Tartalom

### A feladat

Az algoritmus bemenete egy $F$ formula, egy $x$ változó és egy $t$ term; kimenete az $F[x/t]$ formula. Elvárás, hogy tetszőleges $\mathcal{A}$ struktúrában

$$\mathcal{A}[x \mapsto \mathcal{A}(t)](F) = \mathcal{A}(F[x/t])$$

teljesüljön. Szavakkal: ha a struktúrában $x$ értékét $t$ értékére állítjuk át, és így értékeljük ki $F$-et (ezt nehéz megcsinálni), ugyanazt kapjuk, mint ha az eredeti struktúrában az $F[x/t]$ kimenetet értékelnénk ki. Az algoritmus tehát a struktúráról semmit sem tud, mégis elvégzi az értékadást.

### Az eljárás

1. $F$-ben $x$ **minden szabad** előfordulását átírjuk $t$-re (a kötött előfordulásokat nem bántjuk).
2. Ha egy beírt $t$-ben szereplő változó emiatt valamely kvantor hatáskörébe kerülne („lekötődne”), a kötő kvantor változóját — az általa kötött előfordulásokkal együtt — **új** változóra nevezzük át ([[concepts/logika/valtozoiban-tiszta-alak]]).

Termekben nincs kvantor, így ott minden előfordulás szabad: a helyettesítés egyszerű „mindent cserélj”.

**Példa.** $\big(\forall x\,p(g(x),y)\big) \wedge \big(\exists z\,\neg q(z,g(x))\big)\ [x/f(x,y,z)]$. Az első $x$ a $\forall x$ hatáskörében van, ezt nem bántjuk; a második $x$ szabad, ezért $f(x,y,z)$-re cseréljük. A beírt $z$ bekerülne a $\exists z$ hatáskörébe, ezért a kötő $z$-t $u$-ra nevezzük át:

$$\big(\forall x\,p(g(x),y)\big) \wedge \big(\exists u\,\neg q(u,g(f(x,y,z)))\big)$$

### A helyettesítési lemma

**Állítás (termekre).** Minden $x$ változóra, $t,u$ termre és $\mathcal{A}$ struktúrára: $\mathcal{A}[x\mapsto t](u) = \mathcal{A}(u[x/t])$.

**Állítás (formulákra).** Minden $x$ változóra, $t$ termre, $F$ formulára és $\mathcal{A}$ struktúrára: $\mathcal{A}[x\mapsto t](F) = \mathcal{A}(F[x/t])$.

(A jegyzet itt az induktív definíciót és a bizonyítást „később”-nek jelöli, a részleges vázlatban nem szerepel; a $t$ a bal oldalon a $t$ term értékét jelenti.) A $\kappa$ változókiértékelésekkel kifejezve ([[concepts/logika/valtozokiertekeles]]) a lemma azt mondja, hogy az $x$ szerinti variáns kiértékelése megegyezik a behelyettesített formula kiértékelésével — ez a kvantor-szabályok (tablóban a $\gamma$ és $\delta$ lépések) szemantikai alapja.

## Kapocs

- [[concepts/logika/valtozokiertekeles]] — a változókiértékelés és variánsai, amelyekkel a lemma kifejezhető
- [[concepts/logika/term-szemantika]] — a term értéke, amit a termekre vonatkozó lemma használ
- [[concepts/logika/szabad-es-kotott-valtozo]] — mely előfordulások szabadok (csak azokat cseréljük)
- [[concepts/logika/valtozoiban-tiszta-alak]] — az átnevezés, amellyel a változófogás elkerülhető
- [[concepts/logika/elsorendu-tablo]] — a $\gamma$/$\delta$ szabályok $A(x\|a)$ helyettesítése
