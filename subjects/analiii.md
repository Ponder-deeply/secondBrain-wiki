---
tags:
  - subject
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf, SimonP-Anal2.pdf]
references: ["Kós Géza: Analízis 3 előadásjegyzet, 2024", "Simon Péter: Analízis II., 3–4. fejezet", "Fridli Sándor: Analízis III. tematika"]
derivation: source
updated: 2026-09-07
state: "[[V]]"
---

# Analízis III.

Többváltozós analízis. A félév négy nagy tömbje: a metrikus és normált terek topológiája, a többváltozós differenciálszámítás (az implicit- és inverzfüggvény-tételig és a feltételes szélsőértékig), a Jordan-mérték szerinti többszörös integrál, valamint a vonal- és felületi integrálok elmélete, amely a Green-, Gauss–Osztrogradszkij- és Stokes-tételekben csúcsosodik ki.

## A tárgy célja

Az egyváltozós analízis fogalmait — konvergencia, folytonosság, integrál, primitív függvény — átvinni tetszőleges metrikus térbe, illetve több változóra. A vezérfonal végig ugyanaz: minden egyváltozós tétel megkeresi a maga többváltozós általánosítását, a Newton–Leibniz formulától az általános Stokes-tételig.

Előfeltétel: az [[subjects/analii]] anyaga (derivált, Riemann-integrál, primitív függvény, Taylor-formula).

## Metrikus és normált terek

### Alapstruktúrák

- [[concepts/analiii/metrikus-ter]] — távolságfüggvény három axiómával; a félév topológiai apparátusának alapja
- [[concepts/analiii/normalt-vektorter]] — norma, indukált metrika, $L^q$-normák, $C[a,b]$ maximumnorma
- [[concepts/analiii/holder-es-minkowski-egyenlotlenseg]] — Hölder, Cauchy–Bunyakovszkij–Schwarz, Minkowski
- [[concepts/analiii/ekvivalens-normak]] — normaekvivalencia; véges dimenzióban minden norma ekvivalens
- [[concepts/analiii/skalaris-szorzat-ter]] — skaláris szorzat, euklideszi tér, paralelogramma-szabály, Hilbert-tér
- [[concepts/analiii/felmetrikus-ter]] — a $\rho(x,y)=0\Rightarrow x=y$ axióma elhagyása és a faktorizálás
- [[concepts/analiii/metrikabol-uj-metrika]] — metrika transzformálása monoton szubadditív függvénnyel; altér-metrika
- [[concepts/analiii/metrikus-terek-szorzata]] — szorzatmetrika, szorzatnorma; minden koordinátánként dől el
- [[concepts/analiii/ekvivalens-metrikak]] — a $\rho_p$ metrikák $p\geq 1$-re ekvivalensek, $p<1$-re nem

### Konvergencia és topológia

- [[concepts/analiii/konvergencia-metrikus-terben]] — a limesz $\varepsilon$–$n_0$ definíciója metrikával; koordinátánkénti konvergencia
- [[concepts/analiii/halmaz-pontjai-metrikus-terben]] — belső, külső, határ-, izolált és torlódási pont; lezárt, derivált halmaz
- [[concepts/analiii/nyilt-es-zart-halmazok]] — a metrikus tér topológiája; uniók és metszetek viselkedése
- [[concepts/analiii/topologikus-ter]] — a nyílt halmazok három tulajdonsága axiómaként

### Teljesség

- [[concepts/analiii/cauchy-sorozat-es-teljes-ter]] — Cauchy-tulajdonság, teljesség, Banach-tér, az $L^1$ ellenpéldák
- [[concepts/analiii/banach-fixponttetel-metrikus-terben]] — kontrakció fixpontja teljes tér zárt részhalmazán
- [[concepts/analiii/fixponttetel-gombon]] — a zárt gömbre szűkített változat, a priori és a posteriori hibabecslés
- [[concepts/analiii/linearis-lekepezes-kontrakcio-volta]] — affin leképezés kontrakció volta $\rho_1,\rho_2,\rho_\infty$ szerint
- [[concepts/analiii/sehol-sem-suru-halmazok]] — sűrű, szeparábilis, sehol sem sűrű halmazok
- [[concepts/analiii/baire-kategoriatetel]] — I./II. kategória, reziduális halmazok; a topológiai „kicsi–nagy" felbontás

### Kompaktság és összefüggőség

- [[concepts/analiii/cantor-metszettetel]] — egymásba skatulyázott zárt halmazok metszete; Bolzano–Weierstrass
- [[concepts/analiii/kompakt-halmazok]] — fedéses kompaktság; kompakt $\Rightarrow$ korlátos és zárt
- [[concepts/analiii/kompaktsag-ekvivalens-jellemzesei]] — a fedéses, sorozatos és torlódási pontos definíció egyenértékűsége
- [[concepts/analiii/heine-borel-tetel]] — $\mathbb{R}^p$-ben a megfordítás is igaz; Lindelöf-lemma
- [[concepts/analiii/osszefuggo-halmazok]] — topológiai összefüggőség, tartomány
- [[concepts/analiii/ivszeru-osszefuggoseg]] — folytonos görbével való összeköthetőség; nyílt halmazon egybeesik

### Folytonos leképezések

- [[concepts/analiii/folytonossag-metrikus-terben]] — az $\varepsilon$–$\delta$ definíció metrikákkal; a nyílt halmazos jellemzés, kompozíció, műveletek
- [[concepts/analiii/atviteli-elv-metrikus-terben]] — a folytonosság és a határérték sorozatos jellemzése; a fejezet bizonyítási motorja
- [[concepts/analiii/fuggvenyhatarertek-metrikus-terben]] — a határérték definíciója, egyértelműsége, lokalitása és műveletei
- [[concepts/analiii/koordinatafuggvenyek-folytonossaga]] — koordinátánként folytonos $\iff$ folytonos; projekciók, szorzattér
- [[concepts/analiii/egyenletes-folytonossag-metrikus-terben]] — a ponttól független $\delta$; Lipschitz-tulajdonság és a Heine-tétel
- [[concepts/analiii/weierstrass-tetel-kompakt-halmazon]] — kompakt halmaz folytonos képe kompakt; a szélsőérték felvétele
- [[concepts/analiii/folytonos-inverz-kompakt-halmazon]] — kompakt tartományon a folytonos bijekció inverze is folytonos
- [[concepts/analiii/bolzano-tetel-osszefuggo-halmazon]] — összefüggő kép, $\mathbb{R}$ összefüggő halmazai, gyöktétel
- [[concepts/analiii/brouwer-fixponttetel]] — zárt gömb folytonos önleképezésének fixpontja
- [[concepts/analiii/halmaztol-vett-tavolsagfuggveny]] — az $1$-Lipschitz távolságfüggvény; zérushalmaza a lezárt
- [[concepts/analiii/korlatos-linearis-lekepezes]] — $\mathcal{L}(X,Y)$, operátornorma, sor-, oszlop- és spektrálnorma
- [[concepts/analiii/kompakt-tartoju-fuggveny-es-egysegosztas]] — tartó, egységosztás, lokálisan koncentrált felbontás

## Differenciálszámítás

### A derivált fogalmai

- [[concepts/analiii/frechet-derivalt]] — a teljes (Fréchet-értelmű) derivált $\mathbb{R}^n \to \mathbb{R}^m$ függvényekre
- [[concepts/analiii/jacobi-matrix]] — a derivált mátrixalakja
- [[concepts/analiii/parcialis-derivalt]] — egyetlen változó szerinti derivált
- [[concepts/analiii/iranymenti-derivalt]] — tetszőleges irány szerinti derivált; $\partial_e f(a) = f'(a)e$
- [[concepts/analiii/gradiens-parcialis-derivaltakbol]] — a gradiens koordinátái a parciális deriváltak
- [[concepts/analiii/koordinatafuggvenyek-differencialhatosaga]] — a vektorértékű eset visszavezetése skalárértékűre
- [[concepts/analiii/folytonosan-differencialhato-fuggveny]] — a $C^1$ osztály
- [[concepts/analiii/differencialhatosag-elegseges-feltetele]] — folytonos parciális deriváltak $\Rightarrow$ differenciálhatóság
- [[concepts/analiii/differencialhatosagi-fogalmak-hierarchiaja]] — az öt regularitási fogalom implikációlánca és az ellenpéldák
- [[concepts/analiii/cauchy-riemann-egyenletek]] — komplex differenciálhatóság mint valós differenciálhatóság plusz lineáris megkötés

### Műveletek differenciálható függvényekkel

- [[concepts/analiii/differencialasi-szabalyok-tobbvaltozos]] — linearitás, szorzat, hányados, mátrixszal való szorzás
- [[concepts/analiii/lancszabaly]] — $(f\circ g)'(a) = f'(g(a))g'(a)$; a fejezet legfontosabb tétele
- [[concepts/analiii/nivofelulet-es-gradiens]] — a gradiens merőleges a nívófelületre
- [[concepts/analiii/euler-tetel-homogen-fuggvenyekre]] — homogenitás mint differenciálegyenlet

### Magasabb rendű deriváltak

- [[concepts/analiii/magasabbrendu-parcialis-derivaltak]] — a $D^k$ és $C^k$ osztályok felépítése
- [[concepts/analiii/young-tetel]] — a deriválás sorrendjének felcserélhetősége, és az ellenpélda nélküle
- [[concepts/analiii/hesse-matrix]] — a második deriváltmátrix és a hozzá tartozó kvadratikus alak
- [[concepts/analiii/laplace-operator]] — $\Delta = \operatorname{div}\operatorname{grad}$, radiális függvények, a három nevezetes egyenlet
- [[concepts/analiii/tobbvaltozos-taylor-polinom]] — multiindexes jelölés és a Taylor-polinom
- [[concepts/analiii/tobbvaltozos-taylor-formula]] — Lagrange- és Peano-maradéktag
- [[concepts/analiii/lagrange-kozepertektetel-tobbvaltozos]] — a középértéktétel, és miért nem vektorértékű

### Szélsőérték

- [[concepts/analiii/kvadratikus-alak-definitsege]] — az öt kategória, az egységgömbös becslés, Sylvester-kritérium
- [[concepts/analiii/lokalis-szelsoertek-feltetelei]] — elsőrendű szükséges, másodrendű elégséges és szükséges feltétel
- [[concepts/analiii/felteteles-szelsoertek]] — Lagrange-multiplikátorok
- [[concepts/analiii/felteteles-szelsoertek-masodrendu-feltetelei]] — feltételes definitség a magtéren

### Az implicit- és inverzfüggvény-kör

- [[concepts/analiii/lokalis-invertalhatosag]] — $\det f'(a) \ne 0$ $\Rightarrow$ lokális inverz; Banach-fixponttétellel
- [[concepts/analiii/implicitfuggveny]] — az egyenlettel megadott függvény fogalma
- [[concepts/analiii/implicitfuggveny-tetel]] — létezés, differenciálhatóság, $C^1$-ség
- [[concepts/analiii/inverzfuggveny-tetel]] — a lokális inverz folytonosan differenciálható, $h' = (f'\circ h)^{-1}$
- [[concepts/analiii/egyszeru-lekepezesekre-bontas]] — lokális felbontás egyszerű leképezésekre és cserékre

## Jordan-mérték

### A mérték felépítése

- [[concepts/analiii/jordan-kulso-belso-mertek]] — téglás fedés és kitöltés; a mérhetőség definíciója
- [[concepts/analiii/jordan-mertek-kockazassal]] — rácskockás közelítés; $b(H) \le k(H)$
- [[concepts/analiii/kulso-belso-mertek-tulajdonsagai]] — szub- és szuperadditivitás; $k(A) = b(A) + k(\partial A)$
- [[concepts/analiii/jordan-nullmerteku-halmazok]] — nullmértékűség és a $k(\partial A) = 0$ mérhetőségi kritérium
- [[concepts/analiii/jordan-merheto-halmazok-gyuruje]] — $\mathcal{J}_p$ halmazgyűrű; a térfogat egyértelműsége

### A mérték kiszámítása

- [[concepts/analiii/jordan-mertek-szeletelessel]] — a Cavalieri-elv pontos alakja
- [[concepts/analiii/p-dimenzios-gomb-terfogata]] — $\gamma_p r^p$ Wallis-integrálokkal
- [[concepts/analiii/jordan-mertek-linearis-transzformaltja]] — $t(M(A)) = |\det M|\,t(A)$

## Többváltozós integrál

### Az integrál fogalma

- [[concepts/analiii/jordan-mertek-szerinti-integral]] — felosztás, alsó és felső összegek, alsó és felső integrál
- [[concepts/analiii/also-felso-osszegek-kockazassal]] — végtelenül finomodó felosztássorozatok
- [[concepts/analiii/tobbvaltozos-integralhatosag]] — oszcillációs összeg; „nullmértékűtől eltekintve folytonos" elégséges feltétel
- [[concepts/analiii/tobbvaltozos-integral-muveletei]] — műveleti tulajdonságok és tartomány szerinti additivitás
- [[concepts/analiii/grafikon-alatti-halmaz-terfogata]] — a mérték és az integrál összezárása

### Az integrál kiszámítása

- [[concepts/analiii/lebontasi-tetel]] — a szukcesszív integrálás kulcslemmája
- [[concepts/analiii/szukcessziv-integralas]] — egymás utáni egyváltozós integrálások, normáltartomány
- [[concepts/analiii/kettos-integralok-felcserelhetosege]] — a sorrendcsere feltételei és ellenpéldái
- [[concepts/analiii/szorzathalmaz-merteke-es-integralja]] — szorzathalmaz mértéke, szeparálható integrandus
- [[concepts/analiii/tobbszoros-integral-fizikai-alkalmazasai]] — tömeg, tömegközéppont, tehetetlenségi nyomaték

### Transzformáció és paraméteres integrálok

- [[concepts/analiii/mertek-es-integraltranszformacio]] — a többváltozós helyettesítés; Jacobi-determináns
- [[concepts/analiii/polarkoordinatas-helyettesites]] — a legfontosabb konkrét eset
- [[concepts/analiii/gauss-integral]] — $\int_{-\infty}^{\infty} e^{-x^2} = \sqrt{\pi}$ polárkoordinátákkal
- [[concepts/analiii/parameteres-integral]] — $F(t) = \int_a^b f(t,x)\,\mathrm{d}x$; a folytonosság öröklődése
- [[concepts/analiii/parameteres-integral-integralhatosaga]] — az integrálási sorrend felcserélhetősége
- [[concepts/analiii/parameteres-integral-differencialasa]] — deriválás az integráljel alatt
- [[concepts/analiii/gamma-fuggveny]] — a faktoriális kiterjesztése; a paraméteres integrálok mintapéldája

## Vonalintegrál és primitív függvény

### Alapfogalmak

- [[concepts/analiii/skalarmezo-es-vektormezo]] — az elmélet alapszókincse
- [[concepts/analiii/szakaszonkent-c1-gorbe]] — görbe, átparaméterezés, megfordítás, ívhossz
- [[concepts/analiii/valos-vonalintegral]] — a mező által a görbe mentén végzett munka

### Primitív függvény

- [[concepts/analiii/vektormezo-primitiv-fuggvenye]] — $f = \operatorname{grad} F$; konstans erejéig egyértelmű
- [[concepts/analiii/newton-leibniz-formula-vonalintegralra]] — a vonalintegrál csak a végpontoktól függ
- [[concepts/analiii/konzervativ-vektormezo]] — primitív függvény, útfüggetlenség és zárt görbés nulla ekvivalenciája
- [[concepts/analiii/rotaciomentes-vektormezo]] — a szimmetrikus Jacobi-mátrix mint szükséges, de nem elégséges feltétel
- [[concepts/analiii/goursat-lemma]] — háromszögvonalon vett integrál eltűnése
- [[concepts/analiii/primitiv-fuggveny-csillagszeru-tartomanyon]] — csillagszerű tartományon a rotációmentesség elégséges

### Homotópia

- [[concepts/analiii/homotop-gorbek]] — folytonos átdeformálás, nullhomotóp zárt görbe
- [[concepts/analiii/vonalintegral-homotop-gorbeken]] — homotóp görbéken az integrál megegyezik
- [[concepts/analiii/egyszeresen-osszefuggo-tartomany]] — a végleges topológiai feltétel a primitív függvény létezéséhez

## Integráltételek

### A vonalintegrál általánosításai

- [[concepts/analiii/altalanos-vonalintegral]] — tetszőleges bilineáris szorzással; az ívhossz szerinti, valós és komplex esetek közös kerete
- [[concepts/analiii/sikvektorok-keresztszorzata]] — a vektoriális szorzat síkbeli, skalárértékű változata
- [[concepts/analiii/korulfordulasi-szam]] — zárt síkgörbe előjeles megkerüléseinek száma
- [[concepts/analiii/jordan-gorbetetel]] — egyszerű zárt görbe két tartományra bontja a síkot; Jordan-tartomány

### Síkbeli integráltételek

- [[concepts/analiii/green-tetel]] — a síkbeli integráltételek közös alapköve
- [[concepts/analiii/jordan-tartomany-terulete]] — terület pusztán határgörbén vett vonalintegrállal
- [[concepts/analiii/jordan-tartomany-sulypontja]] — súlypont ugyanígy
- [[concepts/analiii/kulso-normalis]] — érintő- és külső normálvektor; a $t\,\mathrm{d}s$ / $n\,\mathrm{d}s$ fordítókulcs
- [[concepts/analiii/divergencia]] — forrássűrűség; a Gauss–Osztrogradszkij-tétel integrandusa
- [[concepts/analiii/rotacio]] — örvénysűrűség; a Stokes-tétel integrandusa
- [[concepts/analiii/newton-leibniz-formula-tobbvaltozos]] — a gradiens integrálja és a határon vett normálintegrál
- [[concepts/analiii/gauss-osztrogradszkij-tetel]] — a divergencia integrálja egyenlő a határon vett fluxussal
- [[concepts/analiii/stokes-tetel]] — a rotáció integrálja egyenlő a határon vett cirkulációval

### Felületek és térbeli integráltételek

- [[concepts/analiii/parameteres-felulet]] — felületelem, felszínelem, a lampion-ellenpélda
- [[concepts/analiii/feluleti-integral]] — felszín szerinti integrál és fluxus
- [[concepts/analiii/green-tetel-harom-dimenzioban]] — minden térbeli integráltétel közös építőköve
- [[concepts/analiii/altalanos-stokes-tetel]] — a négy térbeli tétel közös alakja bilineáris szorzással
- [[concepts/analiii/kelvin-stokes-tetel]] — a rotáció fluxusa peremes felületen
- [[concepts/analiii/maxwell-egyenletek-es-integraltetelek]] — az integráltételek fizikai alkalmazása
- [[concepts/analiii/osszekapcsolodasi-szam]] — Biot–Savart, Ampère, Gauss-féle linking number
- [[concepts/analiii/korulfordulasi-szam-valtozatok]] — megkerülés, átdöfés, átbújás közös sémán

## Hiányzó anyagrészek

A tárgyleírás alábbi tételei még egyetlen laphoz sem tartoznak.

- **Henger- és gömbi koordináták.** Csak a
  [[concepts/analiii/polarkoordinatas-helyettesites]] létezik, a tematika mindhármat
  megnevezi.
- **Differenciálgeometriai alapok.** Ívhossz, görbület, Frenet-formulák. A
  [[concepts/analiii/parameteres-felulet]] és a
  [[concepts/analiii/szakaszonkent-c1-gorbe]] az integrálás előfeltételei, nem
  görbeelmélet.
- **Paraméteres görbe** mint önálló fogalom — felületre van lap, görbére nincs.

Mindhárom forrása az ELTE-IK `Analizis-3-gyakorlati-jegyzet-ELTE-IK.pdf`,
amely még konvertálatlan.
