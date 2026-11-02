---
tags: [concept]
sources: [Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf]
derivation: source
kind: theorem
element: water
updated: 2026-10-21
---

# Homomorfizmus magja és homomorfizmustétel

Csoporthomomorfizmusnál a mag (az egységelem teljes inverz képe) normálosztó, és a faktorcsoport izomorf a képpel; minden normálosztó egy kanonikus homomorfizmus magja. Gyűrűhomomorfizmus a két művelet megtartásával definiálható.

## Tartalom

### A homomorfizmus magja

Egy $G$ csoportnak egy $G'$ csoportba való $\varphi$ homomorfizmusánál a **homomorfizmus magja** a $G'$ csoport $e'$ egységelemének teljes inverz képe: $\ker(\varphi) = \varphi^{-1}(e')$.

### Homomorfizmustétel (8.1.39)

Egy $G$ csoport egy $\varphi$ homomorfizmusánál a homomorfizmus magja normálosztó, és a $G/\ker(\varphi)$ faktorcsoport izomorf $G' = \varphi(G)$-vel. A $G$ bármely $N$ normálosztója magja valamely homomorfizmusnak: $G$-nek $G/N$-re való kanonikus leképezése homomorfizmus, amelynek magja $N$.

**Bizonyítás.** A $\varphi^{-1}(a')$, $a' \in G'$ halmazrendszer $G$ egy osztályozása. Kompatibilis a szorzással: ha $a \in \varphi^{-1}(a')$ és $b \in \varphi^{-1}(b')$, akkor $\varphi(ab) = \varphi(a)\varphi(b) = a'b'$, azaz $ab \in \varphi^{-1}(a'b')$. Az előző tétel (2) pontja szerint $e$ osztálya, azaz $\ker(\varphi)$, normálosztó, így az $a' \mapsto \varphi^{-1}(a')$ leképezés $G'$ izomorfizmusa $G/\ker(\varphi)$-re. A tétel második fele a 8.1.35 bizonyítása alapján triviális. $\square$

Szemléltető példa (az előadás ábrája): $G = \mathbb{Z}$, $\varphi$ a paritás leképezése, $\ker\varphi = \{0, \pm 2, \pm 4, \dots\}$; a $G/\ker\varphi$ két mellékosztálya ($0 + \ker\varphi$ és $1 + \ker\varphi$) a páros és páratlan számok, és ez izomorf a $G'$ két osztályával. A $\nu$ a kanonikus leképezés.

### Gyűrűhomomorfizmus

Ha $(R; +, \cdot)$ gyűrű és $(R_1; \oplus, \otimes)$ két bináris műveletes algebrai struktúra, a $\varphi: R \to R_1$ leképezés **homomorfizmus**, ha minden $r, s \in R$-re

$$\varphi(r + s) = \varphi(r) \oplus \varphi(s), \qquad \varphi(r \cdot s) = \varphi(r) \otimes \varphi(s).$$

**Tétel (8.2.8).** Gyűrű homomorf képe gyűrű. *Bizonyítás:* csak a disztributivitást kell látni: $a'(b' + c') = a'(b+c)' = (a(b+c))' = (ab + ac)' = (ab)' + (ac)' = a'b' + a'c'$ (képelemekkel); a másik oldal hasonlóan.

## Kapocs

- [[concepts/dimatii/homomorfizmus-es-izomorfizmus]] — a homomorfizmus és izomorfizmus alapfogalma
- [[concepts/dimatii/normaloszto-es-faktorcsoport]] — a mag normálosztó, a faktorcsoport a kép
- [[concepts/dimatii/reszgyuru-es-idealok]] — gyűrűkben az ideál játssza a normálosztó szerepét
- [[concepts/dimatii/gyuru]] — a gyűrű mint célstruktúra
