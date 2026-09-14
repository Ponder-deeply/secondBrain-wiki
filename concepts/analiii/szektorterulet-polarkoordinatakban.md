---
tags: [concept]
sources: [12_ea_An3_2022_tavasz.pdf]
derivation: source
updated: 2026-09-14
---

# Szektorszerű tartomány területe polárkoordinátákban

Ha egy síkgörbét az origó pontjaival kötünk össze, a keletkező szektorszerű tartomány területe a görbe polárkoordinátás alakjából egyetlen egyváltozós integrállal, $t(T) = \tfrac{1}{2}\int r^2(\varphi)\,\mathrm{d}\varphi$ alakban számítható ki.

## Tartalom

### Szektorszerű tartomány

Legyen $\Gamma$ egy [[concepts/analiii/sikgorbe-megadasi-modok|polárkoordinátás alakban megadott]] síkgörbe, $r(\varphi)$ ($\varphi \in [a,b]$) folytonos függvény. Az origót a $\Gamma$ görbe pontjaival összekötő szakaszok unióját **szektorszerű tartománynak** nevezzük:

$$T := \bigl\{(r\cos\varphi,\, r\sin\varphi) \mid a \le \varphi \le b,\ 0 \le r \le r(\varphi)\bigr\}.$$

### A terület képlete

**Tétel.** Legyen $0 \le a < b \le 2\pi$. Ha $r(\varphi)$ ($\varphi \in [a,b]$) nemnegatív, folytonos függvény, akkor a fentivel megadott $T$ szektorszerű tartománynak van területe, és

$$t(T) = \frac{1}{2}\int_a^b r^2(\varphi)\,\mathrm{d}\varphi.$$

**Bizonyítás.** A $T$ halmaznak az $(r,\varphi)$ polársíkon a

$$H = \{(r,\varphi) \in \mathbb{R}^2 \mid a \le \varphi \le b,\ 0 \le r \le r(\varphi)\}$$

normáltartomány felel meg. A [[concepts/analiii/polarkoordinatas-helyettesites|polárkoordináta-transzformációra vonatkozó tétel]] alapján a $T$ halmaznak van területe, és

$$t(T) = \iint_T 1\,\mathrm{d}x\,\mathrm{d}y = \iint_H r\,\mathrm{d}r\,\mathrm{d}\varphi = \int_a^b \left[\frac{r^2}{2}\right]_{r=0}^{r=r(\varphi)}\,\mathrm{d}\varphi = \frac{1}{2}\int_a^b r^2(\varphi)\,\mathrm{d}\varphi. \qquad \blacksquare$$

### Rokon képlet: paraméteres alakban megadott görbe alatti terület

Ha $\varphi(t) = \bigl(\varphi_1(t), \varphi_2(t)\bigr)$ ($t \in [a,b]$) a felső félsíkba eső egyszerű sima görbe egy paraméterezése, akkor a görbe alatti $A$ síkidomnak van területe, és

$$t(A) = \int_a^b \varphi_2(t) \cdot \varphi_1'(t)\,\mathrm{d}t.$$

Ez a [[concepts/analiii/jordan-tartomany-terulete|Green-tételből levezetett $t(K) = -\int_{\partial K} y\,\mathrm{d}x$ vonalintegrál-képlet]] közvetlen alkalmazása arra a speciális esetre, amikor a határgörbe egy része a görbe maga, más része a tengelyen futó szakasz.

### Példa: a Bernoulli-lemniszkáta területe

A [[concepts/analiii/sikgorbe-megadasi-modok]] lapon bevezetett lemniszkátára, $r(\varphi) = \sqrt{2}\,a\sqrt{\cos(2\varphi)}$, szimmetria okok miatt elég a lemniszkáta első síknegyedbe eső részének a területét kiszámítani. Mivel szektorszerű tartományról van szó:

$$\frac{1}{2}\int_0^{\pi/4} r^2(\varphi)\,\mathrm{d}\varphi = \frac{1}{2}\int_0^{\pi/4} 2a^2\cos(2\varphi)\,\mathrm{d}\varphi = \frac{a^2}{2}.$$

A négy síknegyedbeli résszel (a lemniszkáta négy "szirma" közül csak kettő esik a $\varphi \in [-\pi/4,\pi/4] \cup [3\pi/4, 5\pi/4]$ paramétertartományba, de a szimmetria miatt a négyszerezés így is helyes):

$$t = 4 \cdot \frac{1}{2}\int_0^{\pi/4} r^2(\varphi)\,\mathrm{d}\varphi = 2a^2.$$

## Kapocs

- [[concepts/analiii/polarkoordinatas-helyettesites]] — a mögöttes koordinátatranszformáció és a hozzá tartozó mérték-/integráltranszformációs tétel
- [[concepts/analiii/sikgorbe-megadasi-modok]] — a polárkoordinátás görbemegadás és a Bernoulli-lemniszkáta
- [[concepts/analiii/jordan-tartomany-terulete]] — a rokon, vonalintegrállal felírt területképlet a Green-tételből
- [[concepts/analii/sikido-terulete]] — az egyváltozós, függvénygrafikon alatti terület fogalma, amelynek ez a polárkoordinátás megfelelője
