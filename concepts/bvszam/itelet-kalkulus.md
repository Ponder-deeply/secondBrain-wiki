---
tags: [concept]
sources: [szelmJegyzet.pdf]
derivation: source
updated: 2026-08-05
---

# Ítéletkalkulus

Az ítéletkalkulus a matematikai logika ága, amely formális keretet ad elemi állításokból (ítéletekből) felépülő összetett állítások helyességének eldöntésére.

## Tartalom

### Szintaxis

**Ítéletváltozó:** olyan $x$ változó, amelynek értéke $igaz$ vagy $hamis$ lehet. Legyen $Var = \{x_1, x_2, \ldots\}$ az ítéletváltozók megszámlálhatóan végtelen halmaza.

Az **ítéletkalkulusbeli formulák** $Form$ halmaza a legszűkebb olyan halmaz, amelyre:

- minden $x \in Var$ esetén $x \in Form$,
- ha $\varphi \in Form$, akkor $\neg\varphi \in Form$,
- ha $\varphi_1, \varphi_2 \in Form$, akkor $(\varphi_1 \circ \varphi_2) \in Form$, ahol $\circ \in \{\land, \lor, \to\}$.

A $\neg, \land, \lor, \to$ műveleti jelek neve rendre **negáció, és, vagy, implikáció**. $Var_n = \{x_1, \ldots, x_n\}$, $Form_n$ pedig azon formulák halmaza, amelyekben legfeljebb $Var_n$-beli változók szerepelnek.

### Szemantika — interpretáció

Egy $I : Var_n \to \{igaz, hamis\}$ függvényt **interpretációnak** nevezünk. Az $I$-t $Form_n$-re kiterjesztjük: $I(\varphi) = igaz$ akkor és csak akkor, ha

- $\varphi \in Var_n$ és $I(\varphi) = igaz$, vagy
- $\varphi = \neg\psi$ és $I(\psi) = hamis$, vagy
- $\varphi = (\varphi_1 \land \varphi_2)$ és $I(\varphi_1) = I(\varphi_2) = igaz$, vagy
- $\varphi = (\varphi_1 \lor \varphi_2)$ és $I(\varphi_1) = igaz$ vagy $I(\varphi_2) = igaz$, vagy
- $\varphi = (\varphi_1 \to \varphi_2)$ és $I(\varphi_1) = hamis$ vagy $I(\varphi_2) = igaz$.

### Kielégíthetőség, tautológia, ekvivalencia

Az $I$ **kielégíti** $\varphi$-t (jele $I \models \varphi$), ha $I(\varphi) = igaz$. A $\varphi$ formula:

- **kielégíthető**, ha van olyan $I$, hogy $I \models \varphi$,
- **kielégíthetetlen**, ha nem kielégíthető,
- **tautológia** (érvényes), ha minden $I$-re $I \models \varphi$.

Egy $F$ formulahalmazt az $I$ kielégít ($I \models F$), ha kielégíti az összes $F$-beli formulát; $F$ **kielégíthetetlen**, ha nincs ilyen $I$. A $\varphi$ az $F$ **logikai következménye** ($F \models \varphi$), ha minden $I$-re $I \models F$ esetén $I \models \varphi$. A $\varphi_1$ és $\varphi_2$ **ekvivalens**, ha minden $I$-re $I \models \varphi_1 \iff I \models \varphi_2$.

### Tétel (1.1)

Legyen $F$ formulahalmaz és $\varphi$ formula. Ekkor:

- $\varphi$ akkor és csak akkor kielégíthetetlen, ha $\neg\varphi$ tautológia,
- $F \models \varphi$ akkor és csak akkor, ha $F \cup \{\neg\varphi\}$ kielégíthetetlen.

### Literál, klóz, konjunktív normálforma

- **Literál:** $x$ vagy $\neg x$ alakú formula ($x \in Var$). A literál **alapja** az $x$ ítéletváltozó.
- **Klóz:** $l_1 \lor l_2 \lor \ldots \lor l_n$ alakú formula, ahol $l_1, \ldots, l_n$ páronként különböző alapú literálok.
- **Konjunktív normálforma (KNF):** $C_1 \land C_2 \land \ldots \land C_m$ ($m \ge 1$) alakú formula, ahol minden $C_i$ klóz.

Minden ítéletkalkulusbeli formulához megadható vele ekvivalens KNF.

## Kapocs

- [[concepts/bvszam/elsorendu-logika]] — a paraméteres állítások általánosabb logikája
- [[concepts/bvszam/halmaz-relacio-alapfogalmak]] — interpretáció mint leképezés
