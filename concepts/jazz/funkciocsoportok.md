---
tags: [concept]
sources: []
derivation: unsourced
updated: 2026-08-06
---

# Funkciócsoportok és diatonikus helyettesítés

A diatonikus fokok három funkciócsoportba rendeződnek — tonika, szubdomináns, domináns —, és a csoporton belül a fokok korlátozottan felcserélhetők. Ez a legegyszerűbb reharmonizációs eszköz: nem visz be új hangot a hangnembe, mégis megváltoztatja a menet színét.

## A három csoport dúrban

C-dúrban a hét diatonikus négyeshangzat:

| Fok | Akkord | Hangok | Funkció |
|---|---|---|---|
| I | Cmaj7 | C, E, G, B | tonika |
| ii | Dm7 | D, F, A, C | szubdomináns |
| iii | Em7 | E, G, B, D | tonika (gyenge) |
| IV | Fmaj7 | F, A, C, E | szubdomináns |
| V | G7 | G, B, D, F | domináns |
| vi | Am7 | A, C, E, G | tonika |
| vii | Bm7b5 | B, D, F, A | domináns |

## Miért cserélhetők

A csoporton belüli fokok **három közös hangot** tartalmaznak, tercnyi eltolással:

- Cmaj7 és Em7: közös E, G, B
- Cmaj7 és Am7: közös C, E, G
- Dm7 és Fmaj7: közös F, A, C
- G7 és Bm7b5: közös B, D, F

Egy tercnyire lévő diatonikus akkord tehát a négy hangjából hármat megtart — a csere a hangkészlet háromnegyedét érintetlenül hagyja, csak a basszust és egyetlen szélső hangot mozdítja el. Innen a funkcióazonosság: ami eldönti a funkciót, az nagyrészt benne marad.

A domináns csoportnál ez különösen erős: a Bm7b5 pontosan a G7 felső három hangja plusz az A. A G7 [[concepts/jazz/guide-tone|guide-tone]]-jai (B és F) mindkettőben ott vannak, tehát a tritonusz és vele a feszültség megmarad.

## A helyettesítés korlátai

A csoporton belüli csere nem szimmetrikus — nem minden irányban egyformán működik.

**A iii gyenge tonika.** Az Em7 nem tartalmazza az alaphangot (C), viszont tartalmazza a vezetőhangot (B). Ezért nem nyugvópont: inkább továbblendít, mint lezár. Formavégi tonikának alkalmatlan, menet közben viszont jó — tipikusan a I helyén a menet elején, ahonnan lépcsőzetesen indul tovább (Em7 – A7 – Dm7 – G7).

**A vi félig moll színt hoz.** Az Am7 tartalmazza az alaphangot, tehát valódi tonikahelyettes, de a párhuzamos moll felé billenti a hangzást. Zárlatban ez a deceptív hatás (V → vi) alapja.

**A IV és a ii nem cserélhető szabadon.** A Dm7 → Fmaj7 csere elveszíti a D-t, vagyis a kadencia lépcsőzetes basszusmozgását (D → G → C). Kadencia előtt ezért általában a ii marad; a IV inkább önálló szubdomináns-helyzetben, illetve plagális fordulatban jó.

**A vii ritkán önálló.** A Bm7b5-öt dúrban jellemzően nem a V helyett tesszük, hanem a V előkészítéseként vagy basszusvezetés kedvéért. Önálló dominánsként a G7-nél sápadtabb, mert hiányzik belőle az alaphang.

## A dallam dönt

A funkciócsoport megengedi a cserét, a dallam engedélyezi. Ugyanaz a csere az egyik dallamhang alatt magától értetődő, a másik alatt használhatatlan:

- Ha a dallam a **C**-t tartja, a Cmaj7 → Em7 csere rossz: a C az Em7 fölött b13, disszonáns és avoid jellegű.
- Ha a dallam a **G**-t tartja, mindkét tonikahelyettes működik: a G a Cmaj7-ben 5, az Em7-ben b3, az Am7-ben b7 — mindhárom akkordhang.
- Ha a dallam az **E**-t tartja, a Cmaj7 → Am7 csere a dallamot 3-ból 5-be helyezi át: ugyanaz a hang, más szerep, halványabb szín.

Ez a reharmonizáció általános szabálya kicsiben: előbb a dallamot nézzük meg, utána a funkciót. Lásd [[concepts/jazz/reharmonizacio|reharmonizacio]].

## Mollban

A funkciócsoportok mollban is megvannak, de több változat közül lehet választani, mert a moll három anyaskálája (természetes, [[concepts/jazz/harmonic-minor-modusai|harmonikus]], melodikus) eltérő fokokat ad:

| Funkció | Tipikus fokok c-mollban |
|---|---|
| tonika | Cm7 vagy Cm(maj7), Ebmaj7 (bIII) |
| szubdomináns | Dm7b5 (ii), Fm7 (iv), Abmaj7 (bVI) |
| domináns | G7 (V, harmonikus mollból), Bdim7 (vii) |

A bIII itt ugyanaz a viszony, mint dúrban a vi: tercnyire lévő, három közös hangot tartalmazó tonikahelyettes. A bVI szubdomináns-helyettesként a moll kadencia egyik jellegzetes színe. Részletesen: [[concepts/jazz/ii-v-i-mollban|ii-v-i-mollban]].

## Chord-scale következmény

A funkciócsere skálát is cserél: a Cmaj7 fölött C ionian (vagy lydian), az Em7 fölött E phrygian, az Am7 fölött A aeolian. Ugyanaz a hétfokú hangkészlet, más centrummal és más avoid note-tal — az Em7 fölött például az F lesz kerülendő, ami a Cmaj7 fölött nem is merül fel. A [[concepts/jazz/dur-skala-modusai|dur-skala-modusai]] lap ezt fokonként végigveszi.

## Viszony a többi helyettesítéshez

A funkciócsoporton belüli csere a **diatonikus** helyettesítés: nem lép ki a hangnemből. Ehhez képest a [[concepts/jazz/tritone-substitution|tritone-substitution]] és a [[concepts/jazz/modal-interchange|modal-interchange]] kromatikus, tehát feltűnőbb és erősebb. Gyakorlatban ez a sorrend érdemes: előbb diatonikus csere, és csak ha az kevés, akkor kromatikus.

A klasszikus funkciós analízis ugyanezt a hármas felosztást használja, de ott a funkció normatív fogalom (mi *következhet* mi után); a chord-scale keretben inkább leíró: melyik fokok viselkednek hasonlóan a kadenciában. A gyakorlati következtetés ugyanaz, az indoklás nem.

## Kapocs

- [[concepts/jazz/reharmonizacio]] — a gyűjtőlap; ez a technika ott a helyettesítés első sora
- [[concepts/jazz/ii-v-i-durban]] — a kadencia, amelynek fokait itt csoportosítjuk
- [[concepts/jazz/ii-v-i-mollban]] — a moll változat részletesen
- [[concepts/jazz/guide-tone]] — miért marad meg a funkció a cserében
- [[concepts/jazz/dur-skala-modusai]] — a cseréhez tartozó skálák fokonként
- [[concepts/jazz/turnaround]] — a I–vi–ii–V éppen a funkciócsoportok végigjárása
- [[concepts/jazz/modal-interchange]] — a kromatikus továbblépés, ha a diatonikus csere kevés
- [[concepts/jazz/tritone-substitution]] — a legerősebb dominánshelyettes
