---
tags: [concept, logika/rezolucio-elsorendu-logika]
sources: [Rezolúció_II.pdf]
references: [Tk. 259. o., Tk. 261. o.]
derivation: source
updated: 2026-09-08
---

# Herbrand univerzum

A Herbrand univerzum az elsőrendű klózhalmaz leíró nyelvének konstans- és függvényszimbólumaiból szimbolikusan felépített, legfeljebb megszámlálhatóan végtelen univerzum, amelyen a klózhalmaz kielégíthetetlensége ekvivalens az általános (tetszőleges univerzumon vett) kielégíthetetlenséggel — ez Herbrand eredménye, amely a kielégíthetetlenség eldöntését egyetlen, a nyelvből konstruálható univerzumra redukálja.

## Tartalom

### Motiváció

[[concepts/logika/elsorendu-kloz|Korábban]] láttuk, hogy a kielégíthetetlenségre nincs olyan általános tétel, mint a kielégíthetőségre (Löwenheim–Skolem): nem biztos, hogy van olyan $U$, amelyen a kielégíthetetlenség minden univerzumra vonatkozó kielégíthetetlenséget biztosít (Tk. 254. o./6.3.45. példa). Herbrand megmutatta, hogy a klózhalmaz leíró nyelvének **alaptermjeiből** felépíthető egy szimbolikus $U_H$ Herbrand univerzum, amelyre ez a biztosíték mégis fennáll: az elsőrendű klózhalmaz kielégíthetetlensége $H$-n a klózhalmaz kielégíthetetlenségét jelenti általában.

*Egy elsőrendű klózhalmaz kielégíthetetlen akkor és csak akkor, ha Herbrand univerzumán kielégíthetetlen.*

### Herbrand univerzum előállítása (Tk. 259. o.)

A Herbrand univerzum konstrukciója lépésről lépésre:

1. $H_0 = \{S\text{-ben előforduló konstansok halmaza}\}$, vagy ha a klózhalmazban nincs konstansszimbólum, egy szimbolikus konstans, $\{a\}$.
2. $H_{i+1} = H_i \cup F_i$, ahol $F_i$ azon alaptermek halmaza, amelyeket $H_i$ elemeinek a klózhalmazban szereplő függvényszimbólumokba való behelyettesítésével kapunk.
3. $H_\infty = \bigcup_{k \in \mathbb{N}} H_k$.

**Példa:** legyen $S = \{P(x),\ \lnot Q(y,z) \vee \lnot P(z),\ Q(u, f(u))\}$ klózhalmaz. Ekkor $H_0 = \{a\}$ (fiktív konstans, mert $S$-ben nincs konstansszimbólum), $H_1 = \{a, f(a)\}$, és általában $H_j = \{a, f(a), f(f(a)), \dots, f(\dots f(a)\dots)\}$ ($j$-szeres iteráció), tehát

$$H_\infty = \{a,\ f(a),\ f(f(a)),\ \dots,\ f(\dots f(a) \dots),\ \dots\}$$

### Herbrand bázis

A **Herbrand bázis** a $H_\infty$ feletti alapatomok halmazának egy sorozata. A fenti példában: $\{P(a),\ Q(a,a),\ P(f(a)),\ Q(a,f(a)),\ Q(f(a),a),\ Q(f(a),f(a)),\ P(f(f(a))),\ \dots\}$.

A klózhalmaz alaptermekkel való helyettesítésével (pl. $x/a, y/a, u/a, z/f(a)$) az **alapklózhalmaz** előáll: $\{P(f(a)),\ \lnot Q(a,f(a)) \vee \lnot P(f(a)),\ Q(a,f(a))\}$. Az [[concepts/logika/iteletlogikai-szemantikus-fa|erre a bázisra épülő szemantikus fa]] ellenőrizhetően már a negyedik szinten zárt.

### Herbrand interpretáció ($I_H$)

A **Herbrand interpretáció** univerzuma $H_\infty$; a konstansszimbólumokhoz önmagukat rendeli, az $n$-változós $f$ függvényszimbólumhoz az $f(h_1, h_2, \dots, h_n)$ Herbrand univerzumelemet rendeli. $I_H$ a bázisra épített szemantikus fa ágain jelenik meg.

**Tetszőleges $I$ interpretációnak megfelelő Herbrand interpretáció** (Tk. 261. o.): legyen $I$ univerzuma $U$, $\langle U, Pr, Fn, Cnst \rangle$. Az $I$-nek megfelelő $I_H$ Herbrand interpretáció, ha van olyan $\varphi: H \to U$ leképezés, hogy

- ha $a$ fiktív konstans ($Cnst = \emptyset$), akkor $\varphi(a)$ az $U$ egy tetszőleges eleme;
- ha $Cnst$ nem üres ($a_1, \dots, a_n$), akkor $\varphi(a_i) = I_{Cnst}(a_i)$;
- ha $h \in H$ $f(h_1, h_2, \dots, h_n)$ alakú, akkor $\varphi(f(h_1,\dots,h_n)) = f^I(\varphi(h_1), \dots, \varphi(h_n))$.

Ezt a $\varphi$-t felhasználva azt az $I_H$-t választjuk, amelyben $P(h_1,\dots,h_n)$ alapatom pontosan akkor igaz, ha $P^I(\varphi(h_1),\dots,\varphi(h_n))$ igaz $I$-ben.

## Kapocs

- [[concepts/logika/elsorendu-kloz]] — a Herbrand univerzum kiindulópontja: elsőrendű klózhalmaz és annak alappéldányai
- [[concepts/logika/herbrand-tetel]] — a Herbrand interpretációhoz és a Herbrand univerzumhoz kapcsolódó tételek, alaprezolúció
- [[concepts/logika/term]] — az alaptermek fogalma, amiből $H_\infty$ felépül
- [[concepts/logika/iteletlogikai-szemantikus-fa]] — a Herbrand bázisra épülő szemantikus fa
- [[concepts/logika/elsorendu-interpretacio]] — az általános elsőrendű interpretáció, amelynek a Herbrand interpretáció speciális esete
