---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 1.8. i) megjegyzés"]
derivation: source
updated: 2026-09-07
---

# Topologikus tér és a metrika indukálta topológia

A metrikus terekkel kapcsolatos meggondolások jó részében nem maga a metrika, hanem csak a nyílt halmazok rendszerének három tulajdonsága játszik szerepet. Ezt a három tulajdonságot axiómának véve kapjuk a metrikus térnél általánosabb topologikus tér fogalmát.

## Tartalom

### A metrika indukálta topológia

Legyen $(X,\rho)$ metrikus tér. Az

$$\mathcal{T}_\rho(X) := \mathcal{T}_\rho := \{A \in \mathcal{P}(X) : A \text{ nyílt}\}$$

halmazrendszert az $(X,\rho)$ metrikus tér **topológiájának** nevezzük. A nyílt halmazokra vonatkozó alaptétel szerint

- $\emptyset, X \in \mathcal{T}_\rho$;
- tetszőleges $\Gamma \neq \emptyset$ és $A_\gamma \in \mathcal{T}_\rho$ ($\gamma\in\Gamma$) esetén $\bigcup_{\gamma\in\Gamma} A_\gamma \in \mathcal{T}_\rho$;
- **véges** $\Gamma$ esetén $\bigcap_{\gamma\in\Gamma} A_\gamma \in \mathcal{T}_\rho$.

### Definíció

Legyen $X$ halmaz és $\mathcal{T} \subset \mathcal{P}(X)$ olyan halmazrendszer, amelyre

1. $\emptyset, X \in \mathcal{T}$;
2. bármely $\Gamma \neq \emptyset$, $A_\gamma \in \mathcal{T}$ ($\gamma\in\Gamma$) esetén $\bigcup_{\gamma\in\Gamma}A_\gamma \in \mathcal{T}$;
3. véges $\Gamma$ esetén $\bigcap_{\gamma\in\Gamma}A_\gamma \in \mathcal{T}$.

Ekkor $\mathcal{T}$ **topológia**, az $(X,\mathcal{T})$ pár pedig **topologikus tér**. A $\mathcal{T}$ elemeit itt is nyílt halmazoknak nevezzük.

Az aszimmetria — tetszőleges unió, de csak véges metszet — az axiómák lényegi része: metrikus térben a $K_{1/n}(a)$ környezetek metszete az $\{a\}$ egypontú halmaz, ami általában nem nyílt.

### Példák

- $(X,\{\emptyset,X\})$ — a legszűkebb (indiszkrét) topológia.
- $(X,\mathcal{P}(X))$ — a legbővebb (diszkrét) topológia; ezt indukálja a diszkrét metrika, hiszen ott $K_{1/2}(a) = \{a\}$, tehát minden részhalmaz nyílt.
- Ha $(X,\rho)$ metrikus tér, akkor $(X,\mathcal{T}_\rho)$ topologikus tér: **minden metrikus tér topologikus tér is.**

A megfordítás nem igaz — nem minden topológia származik metrikából; az ilyen kérdés a metrizálhatóság problémája.

### Miért érdemes elválasztani?

A metrikus terek elméletének számos tétele — a nyílt és zárt halmazok műveleti tulajdonságai, a folytonosság „nyílt halmaz ősképe nyílt" jellemzése, a fedéses kompaktság — kimondható és bizonyítható pusztán a $\mathcal{T}$ axiómáiból, metrika említése nélkül. Ez az észrevétel adja a topologikus terek bevezetésének motivációját, és az is látszik belőle, hogy ekvivalens metrikák — amelyek ugyanazt a $\mathcal{T}_\rho$-t adják — az elmélet e részéből megkülönböztethetetlenek.

## Kapocs

- [[concepts/analiii/nyilt-es-zart-halmazok]] — a három axióma tartalma metrikus térben
- [[concepts/analiii/ekvivalens-metrikak]] — ekvivalens metrikák ugyanazt a topológiát indukálják
- [[concepts/analiii/metrikus-ter]] — a szűkebb, távolságra épülő struktúra
- [[concepts/analiii/kompakt-halmazok]] — a fedéses kompaktság tisztán topologikus fogalom
- [[concepts/analiii/folytonossag-metrikus-terben]] — a folytonosság nyílt halmazos jellemzése
