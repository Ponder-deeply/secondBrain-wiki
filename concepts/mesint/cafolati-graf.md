---
tags: [concept]
sources: [09.kovetkeztetes.pdf]
derivation: source
kind: model
element: water
updated: 2026-10-12
---

# Cáfolati, rezolúciós és reprezentációs gráf

A rezolúciós keresés három gráffal szemléltethető: a cáfolati gráf az üres klóz előállítását, a rezolúciós gráf az összes klóz előállítását mutatja, a reprezentációs gráf pedig a keresés állapotait (klózhalmazait).

## Tartalom

- **Cáfolati gráf**: az üres klóz előállítását bemutató gráf. Levelei a kiinduló klózok, minden rezolvens két szülőből jön, a gyökér (nyelő) az üres klóz $\square$.
- **Rezolúciós gráf**: az összes (előállítható) klóz előállítását mutató gráf. Egy cáfolati gráf ennek részgráfja.
- **Reprezentációs gráf**: a keresőrendszer állapotgráfja. Egy csúcs egy klózhalmaz; gyermeke úgy áll elő, hogy egyetlen új klózzal, a szülő két klózából levezethető rezolvenssel bővül. A cél csúcsok az üres klózt tartalmazó halmazok.

### A reprezentációs gráf tulajdonságai

- Egy csúcs egyetlen klózzal tartalmaz többet a szülőjénél.
- Mindegyik csúcs tartalmazza a kiinduló klózokat.
- Nincsenek körök.
- Az a rezolúciós lépés, amely egy csúcsban elvégezhető, elvégezhető a belőle egy másik lépés árán elért gyermekcsúcsban is.
- Ha van cáfolat, akkor minden csúcsból el lehet jutni üres klózt tartalmazó célcsúcsba: **nincs rossz döntés**, legfeljebb felesleges. (Nincs zsákutca, így a visszalépés nem kell; ezért nem módosítható stratégiájú, lokális keresésként írható le.)
- Ítéletkalkulusban a gráfnak csak véges sok különböző csúcsa lehet, predikátumkalkulusban végtelen sok is.

### Elsőrendű példa: kuruzslók

$A_1$: van olyan páciens, aki minden doktorban megbízik: $\exists x\{P(x)\wedge\forall y[D(y)\to M(x,y)]\}$. $A_2$: a kuruzslókban egyetlen páciens sem bízik meg: $\forall x\{P(x)\to\forall y[K(y)\to\neg M(x,y)]\}$. Belátandó $B$: egyetlen doktor sem kuruzsló: $\forall x[D(x)\to\neg K(x)]$. Elég $A_1\wedge A_2\wedge\neg B$ kielégíthetetlenségét megmutatni. SKNF-re hozás: [[concepts/mesint/sknf-atalakitas]]. A klózok $P(a)$, $\neg D(y)\vee M(a,y)$, $\neg P(x)\vee\neg K(u)\vee\neg M(x,u)$, $D(b)$, $K(b)$; a cáfolat helyettesítései $\{x|a\}$, $\{y|b\}$, $\{u|v\}$, $\{v|b\}$, és az utolsó lépés $\neg K(b)$ és $K(b)$ rezolválása adja $\square$-t.

## Kapocs

- [[concepts/mesint/rezolucio-mint-keresesi-rendszer]] — a keresőrendszer, amelynek állapottere a reprezentációs gráf
- [[concepts/mesint/valaszadas-rezolucioval]] — a cáfolati gráfból válaszgráf épül
- [[concepts/mesint/rezolucios-strategiak]] — melyik élt érdemes bejárni
- [[concepts/logika/kloz-es-klozhalmaz]] — klózok és klózhalmazok
