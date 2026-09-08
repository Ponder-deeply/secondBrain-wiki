---
tags: [concept]
sources: [szelmJegyzet.pdf]
derivation: source
updated: 2026-08-05
---

# Halmaz- és relációelméleti alapfogalmak

A számításelmélethez használt diszkrét matematikai alapok: hatványhalmaz, komplementer, relációk és azok lezártjai, karakterisztikus függvény.

## Tartalom

### Halmazok

- Tetszőleges $H$ halmazra $\mathcal{P}(H)$ a $H$ **részhalmazainak halmaza** (hatványhalmaza).
- Rögzített $U$ univerzum mellett $H \subseteq U$ **komplementere** $\overline{H} = \{u \in U \mid u \notin H\}$.
- Véges $H$ esetén $|H|$ a $H$ elemszáma.
- $\mathbb{N}$ a természetes számok halmaza; $n \in \mathbb{N}$ esetén $[n] = \{1, 2, \ldots, n\}$, speciálisan $[0] = \emptyset$.
- $n$ valós számra $\lfloor n \rfloor$ illetve $\lceil n \rceil$ az alsó illetve felső egész rész.

### Karakterisztikus függvény

Legyen $A \subseteq H$. Az $f_A : H \to \{0,1\}$ függvény az $A$ halmaz **karakterisztikus függvénye**, ha minden $a \in H$ esetén $f_A(a) = 1$ akkor és csak akkor, ha $a \in A$.

### Relációk

- $H^n$ a $H$ halmaz $n$-szeres Descartes-szorzata.
- Egy **$n$ változós $H$-feletti reláció** a $H^n$ egy részhalmaza; ekvivalensen egy $\hat{\rho} : H^n \to \{igaz, hamis\}$ leképezés, ahol $\hat{\rho}(a_1, \ldots, a_n) = igaz \iff (a_1, \ldots, a_n) \in \rho$.

### Kétváltozós relációk tulajdonságai

Legyen $\rho \subseteq H \times H$; $a\rho b$ jelöli, hogy $(a,b) \in \rho$.

- **Reflexív:** minden $a \in H$-ra $a\rho a$.
- **Tranzitív:** minden $a, b, c \in H$-ra $a\rho b$ és $b\rho c$ esetén $a\rho c$.
- A $\rho$ **reflexív és tranzitív lezártja** az a legszűkebb reflexív és tranzitív $\rho^*$ reláció, amelyre $\rho \subseteq \rho^*$.

A reflexív-tranzitív lezárt fogalma adja a [[concepts/bvszam/generativ-grammatika|levezetési reláció]] $\Rightarrow^*$ definícióját.

## Kapocs

- [[concepts/bvszam/graf-alapfogalmak]] — a gráf mint kétváltozós reláció
- [[concepts/bvszam/generativ-grammatika]] — a $\Rightarrow^*$ levezetési reláció lezártként
- [[concepts/bvszam/itelet-kalkulus]] — interpretáció mint karakterisztikus jellegű leképezés
