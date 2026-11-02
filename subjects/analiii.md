---
tags:
  - subject
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf, SimonP-Anal2.pdf, tematika-analiii.pdf, EloadasHetiTematika.pdf, GyakorlatHetiTematika.pdf, analiii-canvas-tanmenet.md, zhInformaciok.md, RopzhKerdesek.pdf, ElozetesKerdesekMegajanlottVizsgajegyhez1.pdf, ElozetesMegajanlottVizsgaTetelek1.pdf, 01_ea_An3_2025_osz.pdf, 02_ea_An3_2022_tavasz.pdf, 03_ea_An3_2022_tavasz.pdf, 04_ea_An3_2022_tavasz.pdf, 05_ea_An3_2022_tavasz.pdf, 06_ea_An3_2022_tavasz.pdf, 07_ea_An3_2022_tavasz.pdf, 08_ea_An3_2022_tavasz.pdf, 09_ea_An3_2022_tavasz.pdf, 10_ea_An3_2022_tavasz.pdf, 11_ea_An3_2022_tavasz.pdf, 12_ea_An3_2022_tavasz.pdf, 13_ea_An3_2022_tavasz.pdf, 01_gyak_An_III_2024_25_Ifelev.pdf, 02_gyak_An_III_2024_25_Ifelev.pdf, 03_gyak_An_III_2022_tavasz.pdf, 04_gyak_An_III_2022_tavasz.pdf, 05_gyak_An_III_2022_tavasz.pdf, 06_gyak_An_III_2022_tavasz.pdf, 07_gyak_An_III_2022_tavasz.pdf, 08_gyak_An_III_2022_tavasz.pdf, 09_gyak_An_III_2022_tavasz.pdf, 10_gyak_An_III_2022_tavasz.pdf, 11_gyak_An_III_2022_tavasz.pdf]
references: ["Kós Géza: Analízis 3 előadásjegyzet, 2024", "Simon Péter: Analízis II., 3–4. fejezet", "Fridli Sándor: Analízis III. tematika"]
derivation: source
math: 100
updated: 2026-10-21
---

# Analízis III.

Többváltozós analízis. A félév négy nagy tömbje: a metrikus és normált terek topológiája, a többváltozós differenciálszámítás (az implicit- és inverzfüggvény-tételig és a feltételes szélsőértékig), a Jordan-mérték szerinti többszörös integrál, valamint a vonal- és felületi integrálok elmélete, amely a Green-, Gauss–Osztrogradszkij- és Stokes-tételekben csúcsosodik ki.

## A tárgy célja

Az egyváltozós analízis fogalmait — konvergencia, folytonosság, integrál, primitív függvény — átvinni tetszőleges metrikus térbe, illetve több változóra. A vezérfonal végig ugyanaz: minden egyváltozós tétel megkeresi a maga többváltozós általánosítását, a Newton–Leibniz formulától az általános Stokes-tételig.

Előfeltétel: az [[subjects/analii]] anyaga (derivált, Riemann-integrál, primitív függvény, Taylor-formula).

## Követelmények és vizsga

A félévi követelményrendszer (`analiii-canvas-tanmenet.md`) és a ZH-időpontok (`zhInformaciok.md`) szerint:

- **ZH-k:** 1. ZH 2026. november 5., 2. ZH 2026. december 10., mindkettő csütörtökön 18 órakor, a gyakorlati és a megajánlott jegyért is. A ZH feladatmegoldást kér számon (feladatonként max. 40 pont, sikeres: legalább 11 pont); pótZH a félév végén.
- **Röpdolgozatok:** 10 gyakorlat elején, max. 10 perc: 2 definíció/tétel (2 × 1 pont) és 1 előző órai/házi példa (2 pont), összesen 40 pont ($F$). Sikeres, ha az elméleti és a gyakorlati részpontszám is legalább 8. A kérdéssor: `RopzhKerdesek.pdf` (előadásonként).
- **Gyakorlati jegy:** $Ö = F/2 + Z_1 + Z_2$; 2-es 30–45, 3-as 46–60, 4-es 61–80, 5-ös 81–100 pont. Elégtelen jegyre egyszeri utóvizsga (mindkét ZH-témakörből külön legalább 30%).
- **Megajánlott vizsgajegy:** legalább elégséges gyakorlati jegy (nem utóvizsgán szerzett), a heti számonkérés definíció/tétel pontjaiból legalább 12/20, és a két ZH-n egy-egy előadáson elhangzott tétel kimondása és bizonyítása (egyenként 4 pont, mindkettőre legalább 2, összesen legalább 5). Bizonyításra kért tételek: `ElozetesMegajanlottVizsgaTetelek1.pdf` (1. rész); kérdéslista: `ElozetesKerdesekMegajanlottVizsgajegyhez1.pdf` (1. rész, 54 kérdés).
- **Vizsga:** írásbeli (kötelező) és szóbeli rész. Az írásbeli 2 tétel kimondása és bizonyítása plusz 15 kérdés; sikeres, ha a 15-ből legalább 8 jó és a két tétel közül legalább az egyik kimondása és bizonyítása rendben van. A kérdések és tételek előre közzétett listákból jönnek. Nem megengedett eszköz használata esetén szóbeli bizottsági vizsga következik.

### Az 1. rész bizonyítandó tételei

1. Vektorsorozat és koordinátasorozatai konvergenciájának kapcsolata — [[concepts/analiii/konvergencia-metrikus-terben]]
2. $(C[a,b], \|\cdot\|_\infty)$ teljes normált tér — [[concepts/analiii/cauchy-sorozat-es-teljes-ter]]
3. $\mathbb{R}^n$-ben bármely két norma ekvivalens — [[concepts/analiii/ekvivalens-normak]]
4. Zárt halmazok jellemzése torlódási pontokkal — [[concepts/analiii/nyilt-es-zart-halmazok]]
5. Zárt halmazok jellemzése sorozatokkal — [[concepts/analiii/nyilt-es-zart-halmazok]]
6. A deriváltmátrix egyértelmű — [[concepts/analiii/frechet-derivalt]]
7. Vektorértékű függvény és koordinátafüggvényei differenciálhatósága — [[concepts/analiii/koordinatafuggvenyek-differencialhatosaga]]
8. Elégséges feltétel a totális deriválhatóságra parciális deriváltakkal — [[concepts/analiii/differencialhatosag-elegseges-feltetele]]
9. Az összetett függvény deriválási szabálya — [[concepts/analiii/lancszabaly]]
10. Young tétele — [[concepts/analiii/young-tetel]]

## Heti tematika

A 2026/27. őszi félév tematikája (`EloadasHetiTematika.pdf`, `GyakorlatHetiTematika.pdf`; tárgyleírás: `tematika-analiii.pdf`, 5 kredit, kollokvium + gyakorlati jegy, felelős: Fridli Sándor).

| Hét | Előadás | Gyakorlat |
|---|---|---|
| 1 | Térstruktúrák: $\mathbb{R}^n$, metrikus és normált terek, ekvivalens normák, euklideszi terek | Integrálszámítás (primitív függvény, Riemann- és improprius integrál) |
| 2 | Konvergens sorozatok normált terekben, Cauchy-kritérium, Banach-terek, Bolzano–Weierstrass | Metrikus és normált terek 1. |
| 3 | Folytonosság és határérték, átviteli elv, nyílt/zárt/kompakt halmazok, Weierstrass tétele | Metrikus és normált terek 2.: teljesség, nyílt és zárt halmazok, függvénysorozatok |
| 4 | Differenciálszámítás 1.: parciális és iránymenti derivált, lineáris leképezések, totális derivált, Jacobi-mátrix, érintősík | Folytonosság és határérték ($\mathbb{R}^2	o\mathbb{R}$) |
| 5 | Differenciálszámítás 2.: folytonosság és deriválhatóság, elégséges feltétel, láncszabály | Parciális, iránymenti és totális derivált |
| 6 | Differenciálszámítás 3.: Hesse-mátrix, Young-tétel, Taylor-polinom, Lagrange-maradéktag | Deriváltak kapcsolata, érintősík, láncszabály |
| 7 | Differenciálszámítás 4.: Peano-maradéktag, lokális szélsőérték, kvadratikus alakok | Taylor-polinomok és -formula |
| 8 | Differenciálszámítás 5.: abszolút szélsőérték, Heine-tétel, paraméteres integrál | Lokális szélsőértékek |
| 9 | Integrálszámítás 1.: többszörös integrál, integrálhatóság, Fubini, normáltartomány | Abszolút szélsőértékek |
| 10 | Integrálszámítás 2.: integráltranszformáció, polárkoordináták, Gauss-integrál | Szukcesszív integrálás, normáltartomány |
| 11 | Integrálszámítás 3.: hármas integrál, henger- és gömbi koordináták, alkalmazások | Sorrendcsere, polárkoordinátás helyettesítés, terület és térfogat |
| 12 | Görbék és felületek 1.: görbe, érintő, ívhossz, síkgörbék, Bézier-görbék | Kettős és hármas integrálok alkalmazásai |
| 13 | Görbék és felületek 2.: felületek a térben | — |

A gyakorlatokhoz kapcsolódó feladattípusok a megfelelő fogalomlapok `Feladatok` részeiben vannak (források: `An_III_Gyak_2022_tavasz.pdf`, `Analizis-3-gyakorlati-jegyzet-ELTE-IK.pdf`, `gyakorlat.pdf`; a `01_gyak_An_III_2024_25_Ifelev.pdf` … `11_gyak_An_III_2022_tavasz.pdf` lapok hivatalos megoldásokat is tartalmaznak, ezekkel ellenőrizve és bővítve a `Feladatok` részeket; az 1. gyakorlat egyváltozós integrálszámítás, lásd [[subjects/analii]]).

## Előadások (2026 őszi félév állása szerint)

A tárgy anyaga a jelen félév tényleges előadássorrendje szerint, a flashcard index lecture-bontása alapján. Az 1–8. blokk a mostanáig megtartott előadásokat fedi le. A 9–13. blokk még nem hangzott el: a 2022 tavaszi diasor (`09_ea_An3_2022_tavasz.pdf`–`13_ea_An3_2022_tavasz.pdf`) és a heti tematika alapján előre besorolva; frissítendő, ahogy a félév halad.


### 1. előadás — Metrikus és normált terek

- [[concepts/analiii/metrikus-ter]] — távolságfüggvény három axiómával; a félév topológiai apparátusának alapja
- [[concepts/analiii/normalt-vektorter]] — norma, indukált metrika, $L^q$-normák, $C[a,b]$ maximumnorma
- [[concepts/analiii/holder-es-minkowski-egyenlotlenseg]] — Hölder, Cauchy–Bunyakovszkij–Schwarz, Minkowski
- [[concepts/analiii/halmaz-pontjai-metrikus-terben]] — belső, külső, határ-, izolált és torlódási pont; lezárt, derivált halmaz
- [[concepts/analiii/nyilt-es-zart-halmazok]] — a metrikus tér topológiája; uniók és metszetek viselkedése
- [[concepts/analiii/ekvivalens-normak]] — normaekvivalencia; véges dimenzióban minden norma ekvivalens
- [[concepts/analiii/ekvivalens-metrikak]] — a $\rho_p$ metrikák $p\geq 1$-re ekvivalensek, $p<1$-re nem
- [[concepts/analiii/skalaris-szorzat-ter]] — skaláris szorzat, euklideszi tér, paralelogramma-szabály, Hilbert-tér


### 2. előadás — Konvergencia, teljesség

- [[concepts/analiii/konvergencia-metrikus-terben]] — a limesz $\varepsilon$–$n_0$ definíciója metrikával; koordinátánkénti konvergencia
- [[concepts/analiii/cauchy-sorozat-es-teljes-ter]] — Cauchy-tulajdonság, teljesség, Banach-tér, az $L^1$ ellenpéldák
- [[concepts/analiii/bolzano-weierstrass-kivalasztasi-tetel]] — a kiválasztási tétel véges dimenzióban igaz, végtelen dimenzióban általában nem


### 3. előadás — Folytonosság, kompaktság

- [[concepts/analiii/atviteli-elv-metrikus-terben]] — a folytonosság és a határérték sorozatos jellemzése; a fejezet bizonyítási motorja
- [[concepts/analiii/fuggvenyhatarertek-metrikus-terben]] — a határérték definíciója, egyértelműsége, lokalitása és műveletei
- [[concepts/analiii/folytonossag-metrikus-terben]] — az $\varepsilon$–$\delta$ definíció metrikákkal; a nyílt halmazos jellemzés, kompozíció, műveletek
- [[concepts/analiii/koordinatafuggvenyek-folytonossaga]] — koordinátánként folytonos $\iff$ folytonos; projekciók, szorzattér
- [[concepts/analiii/kompakt-halmazok]] — fedéses kompaktság; kompakt $\Rightarrow$ korlátos és zárt
- [[concepts/analiii/kompaktsag-ekvivalens-jellemzesei]] — a fedéses, sorozatos és torlódási pontos definíció egyenértékűsége
- [[concepts/analiii/heine-borel-tetel]] — $\mathbb{R}^p$-ben a megfordítás is igaz; Lindelöf-lemma
- [[concepts/analiii/weierstrass-tetel-kompakt-halmazon]] — kompakt halmaz folytonos képe kompakt; a szélsőérték felvétele


### 4. előadás — Deriválás alapjai

- [[concepts/analiii/parcialis-derivalt]] — egyetlen változó szerinti derivált
- [[concepts/analiii/iranymenti-derivalt]] — tetszőleges irány szerinti derivált; $\partial_e f(a) = f'(a)e$
- [[concepts/analiii/korlatos-linearis-lekepezes]] — $\mathcal{L}(X,Y)$, operátornorma, sor-, oszlop- és spektrálnorma
- [[concepts/analiii/frechet-derivalt]] — a teljes (Fréchet-értelmű) derivált $\mathbb{R}^n \to \mathbb{R}^m$ függvényekre
- [[concepts/analiii/jacobi-matrix]] — a derivált mátrixalakja
- [[concepts/analiii/fuggvenygrafikon-erintosikja]] — kétváltozós függvény grafikonjának érintősíkja a gradiensből


### 5. előadás — Derivált, láncszabály

- [[concepts/analiii/gradiens-parcialis-derivaltakbol]] — a gradiens koordinátái a parciális deriváltak
- [[concepts/analiii/nivofelulet-es-gradiens]] — a gradiens merőleges a nívófelületre
- [[concepts/analiii/differencialhatosagi-fogalmak-hierarchiaja]] — az öt regularitási fogalom implikációlánca és az ellenpéldák
- [[concepts/analiii/koordinatafuggvenyek-differencialhatosaga]] — a vektorértékű eset visszavezetése skalárértékűre
- [[concepts/analiii/differencialhatosag-elegseges-feltetele]] — folytonos parciális deriváltak $\Rightarrow$ differenciálhatóság
- [[concepts/analiii/lancszabaly]] — $(f\circ g)'(a) = f'(g(a))g'(a)$; a fejezet legfontosabb tétele


### 6. előadás — Másodrendű deriváltak

- [[concepts/analiii/magasabbrendu-parcialis-derivaltak]] — a $D^k$ és $C^k$ osztályok felépítése
- [[concepts/analiii/hesse-matrix]] — a második deriváltmátrix és a hozzá tartozó kvadratikus alak
- [[concepts/analiii/young-tetel]] — a deriválás sorrendjének felcserélhetősége, és az ellenpélda nélküle
- [[concepts/analiii/tobbvaltozos-taylor-polinom]] — multiindexes jelölés és a Taylor-polinom
- [[concepts/analiii/tobbvaltozos-taylor-formula]] — Lagrange- és Peano-maradéktag


### 7. előadás — Szélsőérték, kvadratikus alak

- [[concepts/analiii/lokalis-szelsoertek-feltetelei]] — elsőrendű szükséges, másodrendű elégséges és szükséges feltétel
- [[concepts/analiii/kvadratikus-alak-definitsege]] — az öt kategória, az egységgömbös becslés, Sylvester-kritérium


### 8. előadás — Egyenletes folytonosság, paraméteres integrál

- [[concepts/analiii/egyenletes-folytonossag-metrikus-terben]] — a ponttól független $\delta$; Lipschitz-tulajdonság és a Heine-tétel
- [[concepts/analiii/parameteres-integral]] — $F(t) = \int_a^b f(t,x)\,\mathrm{d}x$; a folytonosság öröklődése
- [[concepts/analiii/parameteres-integral-differencialasa]] — deriválás az integráljel alatt
- [[concepts/analiii/parameteres-integral-integralhatosaga]] — az integrálási sorrend felcserélhetősége

### 9. előadás — Többszörös integrál, Fubini-tétel

- [[concepts/analiii/jordan-mertek-szerinti-integral]] — felosztás, alsó és felső összegek, alsó és felső integrál
- [[concepts/analiii/also-felso-osszegek-kockazassal]] — végtelenül finomodó felosztássorozatok
- [[concepts/analiii/tobbvaltozos-integralhatosag]] — oszcillációs összeg; „nullmértékűtől eltekintve folytonos" elégséges feltétel
- [[concepts/analiii/tobbvaltozos-integral-muveletei]] — műveleti tulajdonságok és tartomány szerinti additivitás
- [[concepts/analiii/grafikon-alatti-halmaz-terfogata]] — a mérték és az integrál összezárása
- [[concepts/analiii/lebontasi-tetel]] — a szukcesszív integrálás kulcslemmája
- [[concepts/analiii/szukcessziv-integralas]] — egymás utáni egyváltozós integrálások, normáltartomány
- [[concepts/analiii/kettos-integralok-felcserelhetosege]] — a sorrendcsere feltételei és ellenpéldái


### 10. előadás — Integráltranszformáció, polárkoordináták

- [[concepts/analiii/mertek-es-integraltranszformacio]] — a többváltozós helyettesítés; Jacobi-determináns
- [[concepts/analiii/polarkoordinatas-helyettesites]] — a legfontosabb konkrét eset
- [[concepts/analiii/gauss-integral]] — $\int_{-\infty}^{\infty} e^{-x^2} = \sqrt{\pi}$ polárkoordinátákkal


### 11. előadás — Hármas integrál, henger- és gömbi koordináták

- [[concepts/analiii/hengerkoordinatas-helyettesites]] — polárkoordináta plusz egy változatlan tengely, Jacobi-determináns $r$
- [[concepts/analiii/gombi-koordinatas-helyettesites]] — térbeli polárkoordináta, Jacobi-determináns $r^2\sin\theta$
- [[concepts/analiii/tobbszoros-integral-fizikai-alkalmazasai]] — tömeg, tömegközéppont, tehetetlenségi nyomaték


### 12. előadás — Görbék, ívhossz, Bézier-görbék

- [[concepts/analiii/parameteres-gorbe]] — görbe mint folytonos $[a,b]\to\mathbb{R}^m$ függvény értékkészlete
- [[concepts/analiii/gorbe-erintoje]] — egyszerű sima görbe és az érintő fogalma
- [[concepts/analiii/sikgorbe-megadasi-modok]] — explicit, implicit, paraméteres és polárkoordinátás alak
- [[concepts/analiii/sikgorbe-ivhossza]] — rektifikálhatóság, ívhossz paraméteres és polárkoordinátás alakban
- [[concepts/analiii/szektorterulet-polarkoordinatakban]] — $t(T)=\tfrac12\int r^2\,\mathrm{d}\varphi$
- [[concepts/analiii/bezier-gorbe]] — Bernstein-polinomok, Weierstrass- és Bernstein-approximáció, Bézier-görbe


### 13. előadás — Felületek a térben

- [[concepts/analiii/parameteres-felulet]] — felületelem, felszínelem, a lampion-ellenpélda, a felület megadásának három módja
- [[concepts/analiii/feluleti-gorbe]] — a paramétertartományban futó görbe képe a felületen
- [[concepts/analiii/feluleti-erintosik]] — a felület pontbeli érintősíkja a felületi görbék érintőiből

## További anyag

A tárgy azon fogalomlapjai, amelyek egyik előadásblokkhoz sem kötődnek (a Kós- és Simon-jegyzet többletanyaga) — topikus csoportosításban.


### Metrikus és normált terek

#### Alapstruktúrák

- [[concepts/analiii/felmetrikus-ter]] — a $\rho(x,y)=0\Rightarrow x=y$ axióma elhagyása és a faktorizálás
- [[concepts/analiii/metrikabol-uj-metrika]] — metrika transzformálása monoton szubadditív függvénnyel; altér-metrika
- [[concepts/analiii/metrikus-terek-szorzata]] — szorzatmetrika, szorzatnorma; minden koordinátánként dől el
- [[concepts/analiii/elemi-egyenlotlensegek]] — számtani–mértani közép, Bernoulli, háromszög-, Cauchy–Schwarz- és Minkowski-egyenlőtlenség; indukciós becslések

#### Konvergencia és topológia
- [[concepts/analiii/fuggvenysorozat-egyenletes-konvergenciaja]] — függvénysorozatok pontonkénti és egyenletes (normabeli) konvergenciája; a 3. gyakorlat példái

- [[concepts/analiii/topologikus-ter]] — a nyílt halmazok három tulajdonsága axiómaként

#### Teljesség

- [[concepts/analiii/banach-fixponttetel-metrikus-terben]] — kontrakció fixpontja teljes tér zárt részhalmazán
- [[concepts/analiii/fixponttetel-gombon]] — a zárt gömbre szűkített változat, a priori és a posteriori hibabecslés
- [[concepts/analiii/linearis-lekepezes-kontrakcio-volta]] — affin leképezés kontrakció volta $\rho_1,\rho_2,\rho_\infty$ szerint
- [[concepts/analiii/sehol-sem-suru-halmazok]] — sűrű, szeparábilis, sehol sem sűrű halmazok
- [[concepts/analiii/baire-kategoriatetel]] — I./II. kategória, reziduális halmazok; a topológiai „kicsi–nagy" felbontás

#### Kompaktság és összefüggőség

- [[concepts/analiii/cantor-metszettetel]] — egymásba skatulyázott zárt halmazok metszete; Bolzano–Weierstrass
- [[concepts/analiii/osszefuggo-halmazok]] — topológiai összefüggőség, tartomány
- [[concepts/analiii/ivszeru-osszefuggoseg]] — folytonos görbével való összeköthetőség; nyílt halmazon egybeesik

#### Folytonos leképezések

- [[concepts/analiii/folytonos-inverz-kompakt-halmazon]] — kompakt tartományon a folytonos bijekció inverze is folytonos
- [[concepts/analiii/bolzano-tetel-osszefuggo-halmazon]] — összefüggő kép, $\mathbb{R}$ összefüggő halmazai, gyöktétel
- [[concepts/analiii/brouwer-fixponttetel]] — zárt gömb folytonos önleképezésének fixpontja
- [[concepts/analiii/halmaztol-vett-tavolsagfuggveny]] — az $1$-Lipschitz távolságfüggvény; zérushalmaza a lezárt
- [[concepts/analiii/kompakt-tartoju-fuggveny-es-egysegosztas]] — tartó, egységosztás, lokálisan koncentrált felbontás

### Differenciálszámítás

#### A derivált fogalmai

- [[concepts/analiii/folytonosan-differencialhato-fuggveny]] — a $C^1$ osztály
- [[concepts/analiii/cauchy-riemann-egyenletek]] — komplex differenciálhatóság mint valós differenciálhatóság plusz lineáris megkötés

#### Gyakorlati módszerek

- [[concepts/analiii/tobbvaltozos-hatarertek-modszerei]] — többváltozós határérték és folytonosság vizsgálata: behelyettesítés, két út, közrefogás, polárkoordináták

#### Műveletek differenciálható függvényekkel

- [[concepts/analiii/differencialasi-szabalyok-tobbvaltozos]] — linearitás, szorzat, hányados, mátrixszal való szorzás
- [[concepts/analiii/euler-tetel-homogen-fuggvenyekre]] — homogenitás mint differenciálegyenlet

#### Magasabb rendű deriváltak

- [[concepts/analiii/laplace-operator]] — $\Delta = \operatorname{div}\operatorname{grad}$, radiális függvények, a három nevezetes egyenlet
- [[concepts/analiii/lagrange-kozepertektetel-tobbvaltozos]] — a középértéktétel, és miért nem vektorértékű

#### Szélsőérték

- [[concepts/analiii/abszolut-szelsoertek]] — korlátos zárt halmazon: belső stacionárius pontok + perem összevetése
- [[concepts/analiii/felteteles-szelsoertek]] — Lagrange-multiplikátorok
- [[concepts/analiii/felteteles-szelsoertek-masodrendu-feltetelei]] — feltételes definitség a magtéren

#### Az implicit- és inverzfüggvény-kör

- [[concepts/analiii/lokalis-invertalhatosag]] — $\det f'(a) \ne 0$ $\Rightarrow$ lokális inverz; Banach-fixponttétellel
- [[concepts/analiii/implicitfuggveny]] — az egyenlettel megadott függvény fogalma
- [[concepts/analiii/implicitfuggveny-tetel]] — létezés, differenciálhatóság, $C^1$-ség
- [[concepts/analiii/inverzfuggveny-tetel]] — a lokális inverz folytonosan differenciálható, $h' = (f'\circ h)^{-1}$
- [[concepts/analiii/egyszeru-lekepezesekre-bontas]] — lokális felbontás egyszerű leképezésekre és cserékre

### Jordan-mérték

#### A mérték felépítése

- [[concepts/analiii/jordan-kulso-belso-mertek]] — téglás fedés és kitöltés; a mérhetőség definíciója
- [[concepts/analiii/jordan-mertek-kockazassal]] — rácskockás közelítés; $b(H) \le k(H)$
- [[concepts/analiii/kulso-belso-mertek-tulajdonsagai]] — szub- és szuperadditivitás; $k(A) = b(A) + k(\partial A)$
- [[concepts/analiii/jordan-nullmerteku-halmazok]] — nullmértékűség és a $k(\partial A) = 0$ mérhetőségi kritérium
- [[concepts/analiii/jordan-merheto-halmazok-gyuruje]] — $\mathcal{J}_p$ halmazgyűrű; a térfogat egyértelműsége

#### A mérték kiszámítása

- [[concepts/analiii/jordan-mertek-szeletelessel]] — a Cavalieri-elv pontos alakja
- [[concepts/analiii/p-dimenzios-gomb-terfogata]] — $\gamma_p r^p$ Wallis-integrálokkal
- [[concepts/analiii/jordan-mertek-linearis-transzformaltja]] — $t(M(A)) = |\det M|\,t(A)$

### Többváltozós integrál

#### Az integrál kiszámítása

- [[concepts/analiii/szorzathalmaz-merteke-es-integralja]] — szorzathalmaz mértéke, szeparálható integrandus

#### Transzformáció és paraméteres integrálok

- [[concepts/analiii/gamma-fuggveny]] — a faktoriális kiterjesztése; a paraméteres integrálok mintapéldája
- [[concepts/analiii/wallis-formula-es-stirling-formula]] — Wallis-integrálok, a Gauss-integrál elemi levezetése, Stirling-formula

### Vonalintegrál és primitív függvény

#### Alapfogalmak

- [[concepts/analiii/skalarmezo-es-vektormezo]] — az elmélet alapszókincse
- [[concepts/analiii/szakaszonkent-c1-gorbe]] — görbe, átparaméterezés, megfordítás, ívhossz
- [[concepts/analiii/valos-vonalintegral]] — a mező által a görbe mentén végzett munka

#### Primitív függvény

- [[concepts/analiii/vektormezo-primitiv-fuggvenye]] — $f = \operatorname{grad} F$; konstans erejéig egyértelmű
- [[concepts/analiii/newton-leibniz-formula-vonalintegralra]] — a vonalintegrál csak a végpontoktól függ
- [[concepts/analiii/konzervativ-vektormezo]] — primitív függvény, útfüggetlenség és zárt görbés nulla ekvivalenciája
- [[concepts/analiii/rotaciomentes-vektormezo]] — a szimmetrikus Jacobi-mátrix mint szükséges, de nem elégséges feltétel
- [[concepts/analiii/goursat-lemma]] — háromszögvonalon vett integrál eltűnése
- [[concepts/analiii/primitiv-fuggveny-csillagszeru-tartomanyon]] — csillagszerű tartományon a rotációmentesség elégséges

#### Homotópia

- [[concepts/analiii/homotop-gorbek]] — folytonos átdeformálás, nullhomotóp zárt görbe
- [[concepts/analiii/vonalintegral-homotop-gorbeken]] — homotóp görbéken az integrál megegyezik
- [[concepts/analiii/egyszeresen-osszefuggo-tartomany]] — a végleges topológiai feltétel a primitív függvény létezéséhez

### Integráltételek

#### A vonalintegrál általánosításai

- [[concepts/analiii/altalanos-vonalintegral]] — tetszőleges bilineáris szorzással; az ívhossz szerinti, valós és komplex esetek közös kerete
- [[concepts/analiii/sikvektorok-keresztszorzata]] — a vektoriális szorzat síkbeli, skalárértékű változata
- [[concepts/analiii/korulfordulasi-szam]] — zárt síkgörbe előjeles megkerüléseinek száma
- [[concepts/analiii/jordan-gorbetetel]] — egyszerű zárt görbe két tartományra bontja a síkot; Jordan-tartomány

#### Síkbeli integráltételek

- [[concepts/analiii/green-tetel]] — a síkbeli integráltételek közös alapköve
- [[concepts/analiii/jordan-tartomany-terulete]] — terület pusztán határgörbén vett vonalintegrállal
- [[concepts/analiii/jordan-tartomany-sulypontja]] — súlypont ugyanígy
- [[concepts/analiii/kulso-normalis]] — érintő- és külső normálvektor; a $t\,\mathrm{d}s$ / $n\,\mathrm{d}s$ fordítókulcs
- [[concepts/analiii/divergencia]] — forrássűrűség; a Gauss–Osztrogradszkij-tétel integrandusa
- [[concepts/analiii/rotacio]] — örvénysűrűség; a Stokes-tétel integrandusa
- [[concepts/analiii/newton-leibniz-formula-tobbvaltozos]] — a gradiens integrálja és a határon vett normálintegrál
- [[concepts/analiii/gauss-osztrogradszkij-tetel]] — a divergencia integrálja egyenlő a határon vett fluxussal
- [[concepts/analiii/stokes-tetel]] — a rotáció integrálja egyenlő a határon vett cirkulációval

#### Görbék

- [[concepts/analiii/gorbe-gorbulete]] — görbület, Frenet-triéder (T, N, B), simulósík és simulókör, torzió

#### Felületek és térbeli integráltételek

- [[concepts/analiii/feluleti-integral]] — felszín szerinti integrál és fluxus
- [[concepts/analiii/green-tetel-harom-dimenzioban]] — minden térbeli integráltétel közös építőköve
- [[concepts/analiii/altalanos-stokes-tetel]] — a négy térbeli tétel közös alakja bilineáris szorzással
- [[concepts/analiii/kelvin-stokes-tetel]] — a rotáció fluxusa peremes felületen
- [[concepts/analiii/maxwell-egyenletek-es-integraltetelek]] — az integráltételek fizikai alkalmazása
- [[concepts/analiii/osszekapcsolodasi-szam]] — Biot–Savart, Ampère, Gauss-féle linking number
- [[concepts/analiii/korulfordulasi-szam-valtozatok]] — megkerülés, átdöfés, átbújás közös sémán

## Követelmények

Forrás: a 2026/27/1 Canvas-tanmenet és a Zh információk. Programtervező informatikus BSc, A szakirány; 5 kredit, kollokvium + gyakorlati jegy, előfeltétel: Analízis II. Az órák jelenléti jellegűek, felvétel nincs.

- **Gyakorlati jegy.** 10 gyakorlaton max. 10 perces röpdolgozat: 2 definíció/tétel (2×1 pont) + egy példa (2 pont), összesen $F$ ≤ 40; sikeres, ha az elméleti és a gyakorlati részpontszám is legalább 8. Két zh (feladatmegoldás, egyenként max. 40 pont, sikeres ≥ 11 pont: $Z_1$, $Z_2$); igazolatlan hiányzás = nincs jegy; az egyik sikertelen zh pótolható a félév végén. $Ö = F/2 + Z_1 + Z_2$: 30–45 → 2, 46–60 → 3, 61–80 → 4, 81–100 → 5. Egyszeri gyakorlati utóvizsga (mindkét zh-témakörből külön 30%).
- **Megajánlott vizsgajegy.** Feltétel: legalább 2-es gyakorlati jegy (nem utóvizsgán szerezve); a heti számonkérés definíció/tétel pontjaiból legalább 12/20 (12–13 → 2, 14–15 → 3, 16–17 → 4, 18–20 → 5); a két zh-n egy-egy tétel kimondása és bizonyítása (4–4 pont, összesen legalább 5, egyenként legalább 2, a helyes kimondás 1 pont; 5 → 2, 6 → 3, 7 → 4, 8 → 5). Tételpontot csak a két zh-n lehet szerezni. Korábbi félévben szerzett gyakorlati jegy esetén két 45 perces elméleti dolgozat (10 kérdés, ≥ 6 jó + egy tétel).
- **Vizsga.** Írásbeli (kötelező) + szóbeli (javításra). Írásbeli: 2 tétel kimondása és bizonyítása + 15 kérdés az előre közzétett listákból; sikeres, ha ≥ 8/15 jó és legalább az egyik tétel rendben van. Nem megengedett eszköz használata esetén szóbeli bizottsági vizsga.
- **Időpontok.** 1. zh: 2026. november 5., 18:00; 2. zh: 2026. december 10., 18:00 (gyakorlati és megajánlott jegyhez egyaránt).
- **Tematika.** 12 előadás-/gyakorlathét: térstruktúrák és konvergencia → folytonosság, topológia, kompaktság → differenciálszámítás (parciális, totális, láncszabály, Hesse, Young, Taylor, szélsőértékek) → paraméteres integrál → többszörös integrál; a gyakorlatok az 1. héten az egyváltozós integrálszámítást ismétlik. Az exam-kérdések: [[concepts/analiii/vizsgakerdesek-es-bizonyitando-tetelek]].

## Gyakorlat és vizsgakészülés

- [[concepts/analiii/vizsgakerdesek-es-bizonyitando-tetelek]] — a megajánlott vizsgajegy 54 kérdése, a 10 bizonyítandó tétel és a röpdolgozati kérdések, fogalomlapokhoz rendelve
- [[concepts/analiii/tobbvaltozos-hatarertek-vizsgalata]] — határérték és folytonosság: pályák, közrefogás, a csapdák
- [[concepts/analiii/differencialhatosag-igazolasa-definicioval]] — deriválhatóság igazolása, iránymenti derivált, érintősík számolása
- [[concepts/analiii/differencialhatosag-ellenpeldai]] — klasszikus ellenpéldák (parciálisok, iránymenti deriváltak, Young)

A kidolgozott példák az egyes fogalomlapok "Gyakorlat" szakaszaiban is megtalálhatók (lokális és abszolút szélsőérték, Taylor-polinom, egyenletes folytonosság, metrikák konstrukciója).

## Hiányzó anyagrészek

A tárgyleírás tételei közül a görbék görbülete és a Frenet-formulák a [[concepts/analiii/gorbe-gorbulete]] lappal (forrás: `gyakorlat.pdf`) lefedettek; a 12. előadás (`12_ea_An3_2022_tavasz.pdf`) a Bézier-görbéknél megáll, nem tárgyalja. A gyakorlati feladatok (`An_III_Gyak_2022_tavasz.pdf`, `Analizis-3-gyakorlati-jegyzet-ELTE-IK.pdf`, `gyakorlat.pdf`) a fogalomlapok `Feladatok` részeibe kerültek.

Megjegyzés a henger- és gömbi koordinátákhoz: a `11_ea_An3_2022_tavasz.pdf` diasora e két témát csak névvel említi, levezetés nélkül; a [[concepts/analiii/hengerkoordinatas-helyettesites]] és a [[concepts/analiii/gombi-koordinatas-helyettesites]] lap tartalma a gyakorlati jegyzetekből (`An_III_Gyak_2022_tavasz.pdf`, `gyakorlat.pdf`) származik (`derivation: inferred`).
