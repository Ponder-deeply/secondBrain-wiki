---
tags: [concept]
sources: [1.-bevezetés.md, 6.-veremauto-és-környezetfüggetlen-nyelv.md, szelmJegyzet.pdf]
derivation: source
updated: 2026-08-05
---

# Chomsky-hierarchia

A Chomsky-hierarchia a generatív grammatikák négy osztályba sorolása a szabályaik alakja alapján; az osztályok egymásba ágyazódó ($\mathcal{L}_3 \subsetneq \mathcal{L}_2 \subsetneq \mathcal{L}_1 \subsetneq \mathcal{L}_0$) nyelvcsaládokat határoznak meg.

## Tartalom

### A négy típus

A $G = (V, \Sigma, R, S)$ grammatika típusait a szabályaira tett megszorítások alapján különböztetjük meg.

| Típus | Szabályok alakja | Elnevezés | Felismerő |
|---|---|---|---|
| **0** | nincs semmilyen megkötés | Általános / mondatszerkezetű | Turing-gép |
| **1** | $\alpha A \beta \to \alpha\gamma\beta$ ($A \in V$, $\alpha, \beta, \gamma \in (V \cup \Sigma)^*$, $\gamma \neq \varepsilon$), KES megengedett | Környezetfüggő | Lineárisan korlátolt automata |
| **2** | $A \to v$ ($A \in V$, $v \in (V \cup \Sigma)^*$) | Környezetfüggetlen (CF) | (Nemdeterminisztikus) veremautomata |
| **3** | $A \to vB$ vagy $A \to v$ ($A, B \in V$, $v \in \Sigma^*$) | Reguláris | Véges automata |

**KES (Korlátozott ε-szabály):** 1-es típuson kivételként megengedett az $S \to \varepsilon$ szabály, de ha $R$ tartalmazza ezt a szabályt, akkor $S$ nem fordulhat elő egyetlen szabály jobb oldalán sem.

Egy $L$ nyelv **$i$-típusú**, ha van olyan $i$-típusú $G$ grammatika, hogy $L(G) = L$.

### Chomsky nyelvhierarchia tétele

$$\mathcal{L}_3 \subsetneq \mathcal{L}_2 \subsetneq \mathcal{L}_1 \subsetneq \mathcal{L}_0$$

A valódi tartalmazásokat külön bizonyítani kell; pl. $\{a^n b^n c^n \mid n \in \mathbb{N}\} \in \mathcal{L}_1 \setminus \mathcal{L}_2$.

### Grammatikaosztályok jelölése

- $\mathcal{G}_i$: $i$-típusú grammatikák osztálya
- $\mathcal{L}_i = \{L \mid \exists G \in \mathcal{G}_i : L = L(G)\}$: az $i$-típusú nyelvek osztálya

### 0-típusú normálforma

Bármely 0-típusú grammatikához létezik ekvivalens grammatika, amelynek szabályai az alábbi alakok egyike ($A, B, C \in V$, $a \in \Sigma$):
- $S \to \varepsilon$, $A \to a$, $A \to B$, $A \to BC$, $AB \to B$, $AB \to AC$, $BA \to CA$

## Kapocs

- [[concepts/bvszam/generativ-grammatika]] — grammatika alapfogalmak, levezetés
- [[concepts/bvszam/regularis-normalforma]] — 3-as típusú normálalak
- [[concepts/bvszam/kornyezetfuggetlen-grammatika]] — 2-es típus részletesen
- [[concepts/bvszam/kornyezetfuggo-nyelvek]] — 1-es típus, hossz-nemcsökkentő grammatikák
- [[concepts/bvszam/zartsagi-tulajdonsagok]] — zártsági tételek minden szinten
