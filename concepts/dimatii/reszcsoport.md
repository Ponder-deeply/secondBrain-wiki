---
tags: [concept]
sources: [Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf]
derivation: source
kind: theorem
element: water
updated: 2026-10-21
---

# Részcsoport, komplexus és generátum

A csoport nem üres részhalmaza a komplexus; a részcsoport olyan komplexus, amely maga is csoport. A részcsoportokat négy ekvivalens feltétel jellemzi, metszetük részcsoport, unióik viszont általában nem; egy halmaz generátuma a őt tartalmazó legszűkebb részcsoport.

## Tartalom

### Részstruktúra, komplexus, komplexusszorzás

Ha $B \subseteq A$ és $B$ műveletei az $A$-beli műveletek megszorításainak felelnek meg, akkor $B$ **részstruktúrája** $A$-nak ($B \le A$); ha $B$ valódi részhalmaz, **valódi részstruktúráról** beszélünk. Csoport tetszőleges nem üres részhalmaza a **komplexus**. Komplexusok szorzata: $KL = \{kl \mid k \in K,\ l \in L\}$, és $K^{-1} = \{k^{-1} \mid k \in K\}$.

**Lemma (komplexusok félcsoportja).** Egy csoport komplexusai a komplexusszorzásra egységelemes félcsoportot alkotnak. *Bizonyítás:* a szorzás zárt (a $P^2 \to P$ függvény); asszociatív, mert $K(LM) = \{k(lm)\} = \{(kl)m\} = (KL)M$; az egységelem $E = \{e\}$, mert $EK = KE = K$.

### Ekvivalens állítások részcsoportokra

Legyen $(G,\cdot)$ csoport és $H$ komplexus $G$-ben. Ekvivalensek:

1. $H \le G$ (részcsoport);
2. a művelet $H$-ra való leszűkítése $H \times H \to H$ leképezés, $H$ tartalmazza $G$ egységelemét, és $H^{-1} \subseteq H$;
3. $HH \subseteq H$ és $H^{-1} \subseteq H$;
4. $H^{-1}H \subseteq H$ (**részcsoport-kritérium**: elég, hogy $k^{-1}l \in H$ minden $k,l \in H$-ra).

*Bizonyítás.*

- (1)$\Rightarrow$(2): a leszűkítésnek belső műveletnek kell lennie. $H$ egységelemére $e_H k = k$, és $G$-ben $e_G k = k$, a regularitásból $e_G = e_H$. Ha $k^{-1}_H$ és $k^{-1}_G$ az inverzek, akkor $k_G^{-1}k = e_H = k_H^{-1}k$, a regularitásból $k_G^{-1} = k_H^{-1}$.
- (2)$\Rightarrow$(3): triviális. (3)$\Rightarrow$(4): $H^{-1} \subseteq H$ miatt $H^{-1}H \subseteq HH \subseteq H$.
- (4)$\Rightarrow$(1): $H \ne \emptyset$, így van $k \in H$, és $k^{-1}k = e \in H^{-1}H \subseteq H$. Minden $k \in H$-ra $k^{-1}e \in H^{-1}H \subseteq H$, tehát az inverz is $H$-ban van. Ha $k,l \in H$, akkor $k^{-1} \in H$, így $kl = (k^{-1})^{-1}l \in H^{-1}H \subseteq H$.

*Megjegyzés:* $H \le G$ esetén $H^{-1}H = H$ és $HH = H$, mert $H = eH \subseteq H^{-1}H \subseteq H$ (illetve $H = eH \subseteq HH \subseteq H$).

### Metszet és unió

**Következmény.** Részcsoportok tetszőleges (nem üres indexhalmazú) metszete részcsoport: $D = \bigcap_{\gamma \in \Gamma} H_\gamma \le G$. *Bizonyítás:* $e \in D$, így $D \ne \emptyset$ komplexus, és $D^{-1}D \subseteq H_\gamma^{-1}H_\gamma \subseteq H_\gamma$ minden $\gamma$-ra, tehát $D^{-1}D \subseteq D$; a tétel (4) pontja adja: $D \le G$.

**Részcsoportok uniójára hasonló állítás nem mondható.** A Klein-csoportban ($H = \{e,a,b,c\}$; a szorzótábla szerint minden elem önmaga inverze, $ab = c$) $K = \{e,a\}$ és $L = \{e,b\}$ részcsoport, de $K \cup L = \{e,a,b\}$ nem az (nem zárt a szorzásra: $ab = c \notin K\cup L$).

### Generátum, generátorrendszer

Legyen $G$ csoport és $K$ komplexus $G$-ben. $K$ **generátuma** a $K$-t tartalmazó legszűkebb részcsoport:

$$\langle K \rangle = \bigcap_{L \le G,\ K \subseteq L} L.$$

Ha $\langle K \rangle = G$, akkor $K$ a $G$ **generátorrendszere**. Ha $K = \{g\}$, akkor $g$ **generátor** (generáló elem), és $G$ a $g$ által generált [[concepts/dimatii/ciklikus-csoport]].

**Tétel (a generátum elemei).** Ha $K$ komplexus $G$-ben, akkor
$$\langle K \rangle = \{k_1 \cdots k_s \mid s \in \mathbb{N},\ k_j \in K \cup K^{-1},\ 1 \le j \le s\},$$
ahol az üres szorzat az egységelem. *Bizonyítás:* jelölje $H$ a jobb oldalt. $H \subseteq \langle K\rangle$ nyilvánvaló, mert $\langle K\rangle$ részcsoport. $H$ is részcsoport (tartalmazza az egységelemet, zárt a szorzásra és az inverzképzésre) és tartalmazza $K$ elemeit, ezért $\langle K \rangle \subseteq H$.

**Következmény.** $\langle g \rangle = \{g^n : n \in \mathbb{Z}\}$.

## Kapocs

- [[concepts/dimatii/csoport]] — az alapfogalom; a bizonyításokban a regularitást használjuk
- [[concepts/dimatii/ciklikus-csoport]] — egy elem generátuma
- [[concepts/dimatii/elem-rendje]] — az elem és a csoport rendje
- [[concepts/dimatii/algebrai-struktura]] — a részstruktúra fogalma
- [[concepts/dimatii/felcsoport-es-monoid]] — a komplexusok egységelemes félcsoportot alkotnak
