---
tags: [concept]
sources: [Tablókalkulus.pdf]
derivation: source
updated: 2026-09-08
---

# Hintikka halmaz és a Hintikka lemma

A Hintikka halmaz egy szintaktikailag jellemzett, önmagában „lezárt” formulahalmaz, amelynek definiáló tulajdonságaiból — komplemens pár nélküliség és lefelé zártság — közvetlenül következik a kielégíthetőség; ez a [[concepts/logika/analitikus-tablo|tablókalkulus]] teljességi bizonyításának kulcsfogalma, mind ítéletlogikában, mind elsőrendben.

## Tartalom

### Ítéletlogikai Hintikka halmaz

Egy ítéletlogikai formulákat tartalmazó $S$ halmaz **lefelé zárt**, ha tetszőleges $\alpha$, illetve $\beta$ típusú formulára ([[concepts/logika/jelolt-formula-es-formulatipusok]]):

1. $\alpha \in S \Rightarrow \alpha_1 \in S$ és $\alpha_2 \in S$
2. $\beta \in S \Rightarrow \beta_1 \in S$ vagy $\beta_2 \in S$

Egy $S$ formulahalmazt **Hintikka halmaznak** nevezünk, ha lefelé zárt és nem tartalmaz komplemens párt (azaz nincs benne egyszerre $A$ és $\neg A$ alakú formula).

**Lemma.** Minden $H$ Hintikka halmaz kielégíthető.

*Bizonyítás.* Mivel $H$ lefelé zárt, a benne szereplő ítéletváltozók vagy csak negálatlanul, vagy csak negáltan fordulnak elő (különben komplemens pár lenne bennük). Gyűjtsük ki az összes előforduló ítéletváltozót, és definiáljuk az $I$ interpretációt: ha $X$ negálatlanul szerepel, $I(X) = i$; ha negáltan, $I(X) = h$. Megmutatjuk logikai összetettség szerinti indukcióval, hogy $H$ minden elemére a helyettesítési érték $I$-ben $i$.

- Alapeset: ha $L$ literál eleme $H$-nak, akkor $I$ definíciója szerint $|L|^I = i$.
- Indukciós lépés: tegyük fel, hogy az állítás fennáll $n$-nél kisebb logikai összetettségű formulákra. Ha a vizsgált formula $\alpha$-típusú, akkor $H$ (lefelé zártság miatt) tartalmazza $\alpha_1$-et és $\alpha_2$-t is, ezek kisebb összetettségűek, tehát az indukciós feltevés szerint igazak $I$-ben — emiatt $\alpha$ is igaz $I$-ben. Ha a formula $\beta$-típusú, $H$ tartalmazza $\beta_1$ és $\beta_2$ legalább egyikét, ami $I$-ben igaz, ezért $\beta$ is igaz $I$-ben.

Tehát $H$ minden eleme igaz $I$-ben, azaz $H$ kielégíthető. $\blacksquare$

**Szerepe a tablóban.** Az [[concepts/logika/analitikus-tablo|analitikus tabló]] egy nyitott ágán álló formulahalmaz éppen lefelé zárt és komplemens pár nélküli — tehát Hintikka halmaz, ami a lemma szerint kielégíthető. Erre épül a tablókalkulus teljességének bizonyítása.

### Elsőrendű Hintikka halmaz

Elsőrendben a formulák négy típusba sorolódnak: $\alpha$, $\beta$ (mint ítéletlogikában), valamint két új típus — $\gamma$ (univerzális típus: $\forall xA$ és $\neg\exists xA$) és $\delta$ (egzisztenciális típus: $\exists xA$ és $\neg\forall xA$), lásd [[concepts/logika/elsorendu-tablo]].

Egy $U$ univerzum feletti $S$ formulahalmaz **elsőrendű Hintikka halmaz**, ha teljesíti a következő öt feltételt:

- **H0.** Nem fordul elő benne komplemens pár ($U$ feletti atom és annak negáltja).
- **H1.** $\alpha \in S \Rightarrow \alpha_1 \in S$ és $\alpha_2 \in S$.
- **H2.** $\beta \in S \Rightarrow \beta_1 \in S$ vagy $\beta_2 \in S$.
- **H3.** $\gamma \in S \Rightarrow \gamma(k) \in S$ minden $k \in U$-ra.
- **H4.** $\delta \in S \Rightarrow \delta(k) \in S$ legalább egy $k \in U$-ra.

**Lemma (elsőrendű Hintikka lemma).** Minden $U$ feletti $S$ Hintikka halmaz kielégíthető $U$ felett.

*Bizonyítás* (bonyolultság szerinti indukcióval). Tekintsük azt az atomi kiértékelést, amely $P(\xi_1,\dots,\xi_n)$-hez igazat rendel, ha $TP(\xi_1,\dots,\xi_n) \in S$, és hamisat, ha $FP(\xi_1,\dots,\xi_n) \in S$. Az $\alpha$- és $\beta$-típusú formulákra a kielégíthetőség ugyanúgy adódik, mint az ítéletlogikai esetben. Egy $\gamma$ formulára **H3** miatt minden $k \in U$-ra $\gamma(k) \in S$, és az indukciós feltevés szerint ezek mindegyike igaz — tehát $\gamma$ (mint minden $k$-ra igaz állítás) igaz. Egy $\delta$ formulára **H4** miatt van olyan $k \in U$, amelyre $\delta(k) \in S$, ez az indukciós feltevés szerint igaz — tehát $\delta$ (mint létezik olyan $k$, amelyre igaz állítás) igaz. $\blacksquare$

Ez a lemma az [[concepts/logika/elsorendu-tablo|elsőrendű analitikus tabló]] teljességi bizonyításának kulcslépése: egy nyitott ágon előálló formulahalmaz (a kritikus paraméterek $U$ halmaza felett) elsőrendű Hintikka halmaz, tehát kielégíthető.

## Kapocs

- [[concepts/logika/jelolt-formula-es-formulatipusok]] — az $\alpha$/$\beta$ típus fogalma, amelyre H1–H2 épül
- [[concepts/logika/analitikus-tablo]] — a tabló teljességi bizonyítása, amely a Hintikka lemmára hivatkozik
- [[concepts/logika/elsorendu-tablo]] — a $\gamma$/$\delta$ típus és a kritikus paraméter fogalma, amelyre H3–H4 épül
- [[concepts/logika/szemantikus-tulajdonsagok]] — a kielégíthetőség fogalma, amit a Hintikka lemma garantál
