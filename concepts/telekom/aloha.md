---
tags: [concept]
sources: [Laki_Lecture_5.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-09-25
---

# ALOHA és réselt ALOHA

Az ALOHA-t a 70-es években a University of Hawaii fejlesztette szigetek közötti rádiós (műholdas) kommunikációra: **ha van elküldendő adat, elküldi**. Egyszerű, olcsó, radikális megoldás — a korábbi módszerek (TDMA, FDMA) mind felosztották a csatornát, az ALOHA kevés küldőre készült. Poisson-modellel levezethető, hogy a tiszta ALOHA legfeljebb a kapacitás 18%-át, a réselt ALOHA 37%-át tudja kihasználni.

## Tartalom

### Poisson-folyam

A „véletlen érkezések” klasszikus modellje a sorbanállás-elméletben. Feltevései:
- egy érkezés valószínűsége egy rövid $\Delta t$ intervallumban arányos az intervallum hosszával, és nem függ annak kezdetétől (**memória nélküliség**);
- annak valószínűsége, hogy egy rövid $\Delta t$ alatt több érkezés történik, nullához tart.

Annak valószínűsége, hogy $t$ hosszú intervallumban pontosan $k$ érkezés történik:
$$P_k(t) = \frac{(\lambda t)^k e^{-\lambda t}}{k!},$$
ahol $\lambda$ az érkezési ráta — egyparaméteres modell.

### Az ALOHA vizsgálata

**Jelölések:**
- $T_f$ — keretidő (feldolgozási, átviteli és propagációs);
- $S$ — a sikeres keretátvitelek átlagos száma $T_f$ idő alatt (*throughput*);
- $G$ — az összes átviteli kísérlet átlagos száma $T_f$ alatt;
- $D$ — a küldésre kész állapot és a sikeres átvitel között eltelt átlagos idő.

**Feltevések:** minden keret azonos méretű; a csatorna zajmentes, hibák csak ütközésből erednek; a keretek nem kerülnek sorba az állomásokon; a csatorna Poisson-folyamként viselkedik.

**Levezetés.**
$$S = G \cdot P(\text{„jó” átvitel}).$$

A **sebezhetőségi idő** egy keret sikeres átviteléhez $2T_f$: ha a kék keret $t_0 + T_f$-kor indul, akkor ütközik minden olyan kerettel, amely $t_0$ és $t_0 + 2T_f$ között indul (az előtte indulók a kék elejével, az utána indulók a végével fednek át). A jó átvitel valószínűsége tehát annak valószínűsége, hogy a $2T_f$ sebezhetőségi idő alatt **nincs** újabb érkezés ($k = 0$, $t = 2T_f$). Mivel $\lambda = G / T_f$:

$$P_0(2T_f) = \frac{(\lambda\cdot 2T_f)^0 e^{-\lambda 2T_f}}{0!} = e^{-2G},\qquad\boxed{S = G\,e^{-2G}}.$$

**Maximum:** $S'(G) = e^{-2G}(1 - 2G) = 0$-ból $G = 0{,}5$, és ekkor
$$S = \frac{1}{2e} \approx 0{,}18.$$
A maximális throughput **csak 18%-a** a teljes kapacitásnak.

### Réselt ALOHA (slotted ALOHA)

A csatornát azonos időrésekre bontjuk, amelyek hossza pontosan egy keret átviteli ideje; átvitel **csak időréshatáron** lehetséges. Ha egy új keret küldésre kész, a következő időréshatáron küldjük ki.

Ezzel a **sebezhetőségi idő a felére csökken**: $t = T_f$, $k = 0$:
$$P_0(T_f) = e^{-G},\qquad\boxed{S = G\,e^{-G}}.$$

Maximum $G = 1$-nél: $S = 1/e \approx 0{,}37$ — a kapacitás **37%-a**, kétszerese a tiszta ALOHA-nak. Ára: az állomásoknak szinkronizált órával kell rendelkezniük.

| | Tiszta ALOHA | Réselt ALOHA |
|---|---|---|
| Időmodell | folytonos | diszkrét |
| Sebezhetőségi idő | $2T_f$ | $T_f$ |
| Átvitel | $S = Ge^{-2G}$ | $S = Ge^{-G}$ |
| Optimum | $G = 0{,}5$, $S \approx 0{,}184$ | $G = 1$, $S \approx 0{,}368$ |

**Vizsgaszempont:** a $S = Ge^{-2G}$ képlet levezetése a sebezhetőségi időből és a Poisson-eloszlásból, a maximum kiszámítása deriválással, és a réselt változat összevetése — klasszikus kifejtős kérdés.

## Kapocs

- [[concepts/telekom/kozeghozzaferes-alapjai]] — a dinamikus csatornakiosztás modellje és a $S$, $G$ mértékek
- [[concepts/telekom/csma]] — a vivőjel-érzékelés tovább javít az ALOHA-n
- [[concepts/telekom/multiplexalas]] — a TDMA/FDMA alternatíva
