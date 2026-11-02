---
tags: [concept]
sources: ["09.kovetkeztetes.pdf"]
derivation: source
kind: overview
element: water
updated: 2026-10-12
---

# Szabályalapú következtetés

A szabályalapú logikai következtetés az axiómákat tényekre és szabályokra osztja, hogy a formulák eredeti alakját (különösen az implikációt) megőrizve lehessen bizonyítani; a rezolúció ezt nem teszi lehetővé.

## Tartalom

### Motiváció: az alak segíthet

A formulák alakja segítheti a következtetést. Például a

$$A,\; C\to\neg A,\; A\to B,\; \neg B\to D \;\Rightarrow\; B$$

állításnál könnyű kitalálni, hogy a bizonyításhoz csak $A,\; A\to B \Rightarrow B$ kell. A rezolúció viszont nem tudja használni ezt a segítséget, mert klózformára hozáskor eliminálja az implikációt: $A,\ \neg C\vee\neg A,\ \neg A\vee B,\ B\vee D,\ \neg B$. Olyan következtetési eljárás kell tehát, ahol az állítások megőrzik eredeti alakjukat, különösen az implikációkat. (Lásd [[concepts/mesint/rezolucio-mint-keresesi-rendszer]].)

### Tények és szabályok

Egy $A_1,\dots,A_n \Rightarrow C$ problémában az axiómák két csoportba sorolhatók:

- **tények**: konkrét ismeret, implikáció nélküli formulákban;
- **szabályok**: általános ismeret, implikációs ($A \to B$) formulákban.

### Előre- és hátrafelé láncolás

- **Előrefelé láncolás**: egy alkalmas (illeszthető) szabály segítségével egy állításból új állítást vezet le. Példa: a tény $Kutya(Fifi)\wedge Postás(Jani)$ és a szabály $\forall x\forall y\ Kutya(x)\wedge Postás(y)\to Harap(x,y)$ alapján $Harap(Fifi,Jani)$. Az illeszthetőség vizsgálata: a tény legyen ekvivalens a szabály előfeltételével az $\{x|Fifi,\ y|Jani\}$ helyettesítés mellett (ezt az egyesítő algoritmus számolja ki).
- **Hátrafelé láncolás**: egy állítás bizonyítását visszavezeti egy alkalmas szabály előfeltételének igazolására. Példa: cél $Kutya(Fifi)$, szabály $\forall x\ Ugat(x)\to Kutya(x)$, így elég belátni $Ugat(Fifi)$-t. Az illeszthetőség: a cél legyen ekvivalens a szabály következményével az $\{x|Fifi\}$ helyettesítés mellett.

Logikai ekvivalenciát igazolni nehéz lenne (pl. a tény $\neg(\neg Kutya(Fifi)\vee\neg Postás(Jani))$ alakban); szerencsére az illesztésnél literált literállal kell összevetni, ilyenkor az alaki azonosság = logikai ekvivalencia.

### A következtetés irányai

Egy tényekkel, szabályokkal és célállítással megadott probléma bizonyítható

- **előre haladva**: a tényekből előrefelé láncolással új állításokat vezetünk le, majd azokból még újabbakat, amíg a célállítást meg nem kapjuk;
- **visszafelé haladva**: a célt hátrafelé láncolással részcélokra cseréljük, a részcélokat további részcélokkal váltjuk fel, amíg tények által igazolható részcélokhoz nem jutunk.

Részletek: [[concepts/mesint/elore-halado-szabalyalapu-kovetkeztetes]], [[concepts/mesint/visszafele-halado-szabalyalapu-kovetkeztetes]].

**Nem teljes módszerek.** Például a $P\to Q,\ \neg P\to Q$ szabályokból a fenti módszerek egyike sem vezeti le a $Q$ célt, pedig $P\to Q,\ \neg P\to Q \Rightarrow Q$.

### Keresőrendszerként

A szabályalapú következtetés visszalépéses keresés (lásd [[concepts/mesint/visszalepeses-kereses]]). Célja egy olyan bizonyítás keresése, amit egy ÉS/VAGY gráfbeli ellentmondásmentes megoldásgráf reprezentál ([[concepts/mesint/es-vagy-grafok]]).

- globális munkaterület: a megkezdett bizonyítás (hiperút);
- keresőrendszer szabályai: láncolások, illetve visszalépés;
- elsődleges vezérlési stratégia: visszalépéses stratégia;
- modellfüggő stratégiák: a formulák alakjának kihasználása; a tény (cél) illesztése megelőzi a szabály-illesztést ([[concepts/mesint/modellfuggo-vezerles]]);
- heurisztikák: az adott feladat speciális ismeretei, metaszabályok, kiértékelő függvény.

## Kapocs

- [[concepts/mesint/rezolucio-mint-keresesi-rendszer]] — az alternatíva, amely klózformára hoz és elveszíti az implikációkat
- [[concepts/mesint/elore-halado-szabalyalapu-kovetkeztetes]] — az előre haladó reprezentáció és példa
- [[concepts/mesint/visszafele-halado-szabalyalapu-kovetkeztetes]] — a visszafelé haladó reprezentáció és példák
- [[concepts/logika/legaltalanosabb-illeszto-helyettesites]] — az egyesítő algoritmus, amely az illeszthetőséget számolja
- [[concepts/mesint/kereso-rendszer]] — a keresőrendszer fogalma
