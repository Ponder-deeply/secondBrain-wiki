---
tags: [concept]
sources: [Analizis-3-gyakorlati-jegyzet-ELTE-IK.pdf, gyakorlat.pdf, An_III_Gyak_2022_tavasz.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-22
---

# Többváltozós határérték és folytonosság vizsgálata gyakorlatban

Egy $\mathbb{R}^n \to \mathbb{R}^m$ függvény határértékének létezését a gyakorlatban három lépésben döntjük el: közvetlen behelyettesítés, ha lehet; különben cáfolat két különböző pálya mentén; végül bizonyítás becsléssel (közrefogás).

## Tartalom

### 1. Behelyettesítés és algebrai átalakítás

Ha a függvény a pontban folytonos (polinom, racionális tört nem nulla nevezővel, folytonos függvények kompozíciója), a határérték a helyettesítési érték. Ezt az [[concepts/analiii/atviteli-elv-metrikus-terben|átviteli elv]] és a koordinátánkénti konvergencia indokolja:
$\lim_{(x,y)\to(6,3)} xy\cos(x-2y) = 6\cdot 3\cdot\cos 0 = 18$.

Ha $0/0$ alakú a kifejezés, a szokásos egyváltozós trükkök működnek, például gyökös kifejezés bővítése:
$$\lim_{(x,y)\to(0,0)}\frac{x^2+y^2}{\sqrt{x^2+y^2+1}-1}=\lim\bigl(\sqrt{x^2+y^2+1}+1\bigr)=2.$$

### 2. Nemlétezés: két pálya, két érték

Az [[concepts/analiii/fuggvenyhatarertek-metrikus-terben|egyértelműség]] miatt egy határértéknek csak egy értéke lehet. Ha a pontot két különböző nullához tartó sorozattal (vagy görbe mentén) megközelítve különböző limeszt kapunk, a határérték nem létezik. A cél mindig egy olyan, a ponthoz tartó sorozat választása, amelyen a függvény viselkedése eltér.

- $f=\dfrac{x^2}{x^2+y^2}$: az $x$ tengely mentén $1$, az $y$ tengely mentén $0$, tehát nincs határérték az origóban.
- $f=\dfrac{xy}{x^2+y^2}$: $y=0$ mentén $0$, $y=x$ mentén $\tfrac12$, ezért az $f(0,0)=0$ értékkel kiegészített függvény nem folytonos az origóban, bár minden $x=x_0$ vagy $y=y_0$ egyenesre való megszorítása folytonos.
- $f=\dfrac{x^2y^2}{x^2y^2+(x-y)^2}$: a tengelyek mentén $0$, de az $y=x$ egyenes mentén $f(x,x)=1$; ráadásul mindkét iterált limesz létezik és $0$.

### 3. Csapda: az egyenesek nem elegendők

Az $f=\dfrac{x^2y}{x^4+y^2}$, $f(0,0)=0$ függvény **minden origón átmenő egyenes mentén folytonos** (az $y=mx$ egyenesen $f=\frac{mx}{x^2+m^2}\to0$, és az $x=0$, $y=0$ tengelyeken azonosan $0$), mégsem folytonos az origóban: az $y=x^2$ parabola mentén $f(x,x^2)=\tfrac12$. Ugyanez a tanulság az iterált limeszekre: a $\lim_{x\to0}\lim_{y\to0}$ és a fordított sorrend létezése és egyenlősége nem bizonyítja a kétváltozós határérték létezését. A cáfolathoz tehát görbéket is kell próbálni ($y=x^2$, $y=x^3$, ...), nem csak egyeneseket.

### 4. Létezés bizonyítása: közrefogás

Ha a pálya-próbák mind ugyanazt a $A$ értéket adják, sejtés $\lim f=A$, és ezt definíció szerint vagy becsléssel igazoljuk: $|f(x)-A|\le K\,\|x-a\|$ alakú felső becslés elég (ekkor $\delta=\varepsilon/K$). Például
$$\left|\frac{xy}{\sqrt{x^2+y^2}}\right|\le\frac{\tfrac12(x^2+y^2)}{\sqrt{x^2+y^2}}=\tfrac12\|(x,y)\|_2\to0,$$
a $|xy|\le\tfrac12(x^2+y^2)$ számtani-mértani közép egyenlőtlenséggel; hasonlóan $(x^2+y^2)\ln(x^2+y^2)\to0$ polárkoordinátákkal ($r^2\ln r^2\to0$). Lásd még [[concepts/analiii/polarkoordinatas-helyettesites]].

### Összefoglaló recept

1. Helyettesíts be / alakíts át.
2. Próbáld a tengelyeket, az $y=x$ egyenest, majd a görbéket ($y=x^2$).
3. Ha két pálya eltér: nincs határérték. Ha mind egyezik: sejtés, majd $\|x-a\|$-val vett becslés.
4. Folytonossághoz hasonlítsd a határértéket a függvényértékkel; a szakaszonként definiált pontban külön kell vizsgálni.

## Kapocs

- [[concepts/analiii/fuggvenyhatarertek-metrikus-terben]] — a határérték definíciója és egyértelműsége.
- [[concepts/analiii/atviteli-elv-metrikus-terben]] — a sorozatos jellemzés, amire a pálya-módszer épül.
- [[concepts/analiii/folytonossag-metrikus-terben]] — a folytonosság vizsgálata ugyanezzel.
- [[concepts/analiii/koordinatafuggvenyek-folytonossaga]] — koordinátánkénti vizsgálat.
- [[concepts/analiii/differencialhatosag-ellenpeldai]] — ugyanezek a függvények a deriválhatóság ellenpéldáiként.
