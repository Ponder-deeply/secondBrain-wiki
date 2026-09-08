---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Ívszerű összefüggőség

Egy halmaz ívszerűen összefüggő, ha bármely két pontja összeköthető benne haladó folytonos görbével. Ez a szemléletesebb, „bejárható" összefüggőségfogalom; szigorúbb, mint a topológiai összefüggőség, de nyílt halmazokon egybeesik vele.

## Tartalom

### Folytonos görbe

**Definíció.** A $\gamma : [a,b] \to \mathbb{R}^p$, $t \mapsto \bigl(\gamma_1(t),\dots,\gamma_p(t)\bigr)$ függvény **folytonos görbe**, ha mindegyik $\gamma_i$ koordinátafüggvény folytonos. Speciálisan minden töröttvonal folytonos görbe.

### Definíció

A $H \subset \mathbb{R}^p$ halmaz **ívszerűen összefüggő**, ha bármely két pontja összeköthető a halmazon belül haladó folytonos görbével: minden $a, b \in H$ ponthoz van olyan $\gamma : [0,1] \to H$ folytonos görbe, amelyre $\gamma(0) = a$ és $\gamma(1) = b$.

### Viszonya az összefüggőséghez

**Tétel.** Ha egy halmaz ívszerűen összefüggő, akkor összefüggő.

*Bizonyítás (indirekt).* Tegyük fel, hogy $H$ ívszerűen összefüggő, de nem összefüggő: vannak olyan $A, B$ nyílt halmazok, hogy $H \subset A\cup B$, $H\cap A \neq \emptyset$, $H\cap B\neq\emptyset$ és $H\cap A\cap B = \emptyset$. Legyen $a \in H\cap A$, $b \in H\cap B$, és $\gamma : [0,1]\to H$ folytonos görbe $\gamma(0)=a$, $\gamma(1)=b$-vel. Legyen

$$T = \{t \in [0,1] : \gamma(t) \in A\}, \qquad t_0 = \sup T.$$

Ha $\gamma(t_0) \in A$, akkor $t_0 < 1$, és a folytonosság miatt $t_0$-nak van olyan jobb oldali környezete, amelynek képe $A$-ban fekszik — de akkor $t_0$ nem felső korlátja $T$-nek. Ha $\gamma(t_0) \in B$, akkor $t_0 > 0$, és a folytonosság miatt $t_0$-nak van olyan bal oldali környezete, amelynek képe $B$-ben fekszik — de akkor $t_0$ nem a legkisebb felső korlát. Mindkét eset ellentmondás. $\blacksquare$

**Következmény.** $\mathbb{R}^p$ összefüggő (bármely két pontja szakasszal összeköthető).

A megfordítás **nem** igaz: van $\mathbb{R}^p$-ben olyan halmaz, amely összefüggő, de nem ívszerűen összefüggő.

### Nyílt halmazokra a két fogalom egybeesik

**Tétel.** $\mathbb{R}^p$-ben

- ha egy nyílt halmaz összefüggő, akkor bármely két pontja **töröttvonallal** is összeköthető;
- ha egy nyílt halmaz összefüggő, akkor ívszerűen összefüggő;
- minden nyílt halmaz felbontható ívszerűen összefüggő, nyílt **komponensekre**.

*Bizonyítás.* Legyen $G \subset \mathbb{R}^p$ nyílt, és két pont, $a, b \in G$ legyen ekvivalens, ha összeköthetők $G$-ben töröttvonallal. Ez ekvivalenciareláció: reflexív, szimmetrikus és tranzitív (két töröttvonal egymás után fűzhető). A $G$ ekvivalenciaosztályai páronként diszjunktak, nyíltak — minden pont ekvivalens egy egész gömbkörnyezete minden pontjával, hiszen a gömbön belül szakasszal köthető össze —, és ívszerűen összefüggőek. $\blacksquare$

## Kapocs

- [[concepts/analiii/osszefuggo-halmazok]] — a gyengébb, topológiai összefüggőségfogalom és a tartomány
- [[concepts/analiii/nyilt-es-zart-halmazok]] — a nyíltság, ami a két fogalmat egybeejti
- [[concepts/analiii/konvergencia-metrikus-terben]] — a görbe folytonossága koordinátánként
