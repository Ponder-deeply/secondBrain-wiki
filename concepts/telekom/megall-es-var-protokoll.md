---
tags: [concept]
sources: [Laki_Lecture_4.pdf]
derivation: source
kind: procedure
element: water
updated: 2026-09-25
---

# Forgalomszabályozás és a megáll-és-vár protokollok

Az elemi adatkapcsolati protokollok lépésről lépésre építik fel a megbízható átvitelt: a hibamentes „utópiától” a nyugtázó megáll-és-vár protokollon át az **alternáló bit protokollig (ABP)**, amely időzítővel és 1 bites sorszámmal már zajos csatornán is helyesen működik. Közben kiderül, hogy nagy propagációs késés mellett a csatorna kihasználtsága nagyon rossz — ez vezet a csúszóablakhoz.

## Tartalom

### Forgalomszabályozás (flow control)

Probléma: **gyors adó, lassú vevő** — még hibamentes átvitelnél is elárasztja a vevőt, amely nem tudja kezelni a bejövő kereteket. Megoldások:

1. **Visszacsatolás alapú** (*feedback-based*): a vevő engedélyezi a további küldést (nyugták).
2. **Sebesség alapú** (*rate-based*): a protokollba integrált sebességkorlát; az adatkapcsolati réteg nem használja.

### Feltevések és kommunikációs fajták

A fizikai, adatkapcsolati és hálózati réteg független, üzenetekkel kommunikáló folyamatok; A gép megbízható, összeköttetés alapú szolgálattal hosszú adatfolyamot küld B-nek; a gépek nem fagynak le; a keret fejrészében vezérlési információ, lábrészében ellenőrző összeg van.

- **Szimplex**: csak egy irányba.
- **Fél-duplex**: mindkét irányba, de egyszerre csak egy irány aktív.
- **Duplex**: mindkét irányba egyszerre.

### 1. Korlátozás nélküli szimplex protokoll („utópia”)

Környezet: a hálózati rétegek mindig készen állnak, a feldolgozási idő elhanyagolható, végtelen puffer, a csatorna sosem ront el és sosem veszít el keretet. Protokoll: nincs sorszámozás, nincs nyugta; a küldő végtelen ciklusban küld, a vevő minden keretet továbbad a hálózati rétegnek.

### 2. Szimplex megáll-és-vár (stop-and-wait)

Új feltétel: a vevőnek $\Delta t$ idő kell egy keret feldolgozásához (nincs pufferelés). Ezért a küldő **egyesével** küld, és addig nem küld újat, amíg nyugtát nem kap; a vevő a keret továbbadása után nyugtáz. Következmény: **fél-duplex csatorna kell** (a nyugták visszafelé mennek).

### 3. Szimplex protokoll zajos csatornához

A csatorna most elronthat vagy elveszíthet keretet. A küldő **időzítőt** indít: ha a határidőn belül nem jön nyugta, újraküldi az aktuális keretet. A vevő ellenőrzi az ellenőrző összeget: hibátlan keretet továbbad és nyugtáz, hibásat eldob és nem nyugtáz.

Következmény: **duplikátumok lehetnek**. Ha a keret megérkezett, de a *nyugta* veszett el, a küldő időtúllépés után újraküldi, és a vevő ugyanazt a keretet kétszer adja át a hálózati rétegnek.

### 4. Alternáló bit protokoll (ABP)

Megoldás: **sorszámok** — és ehhez a $\{0, 1\}$ halmaz elegendő.

- **Küldő**: a keretet sorszámmal küldi (kezdetben 0). Ha a nyugta a határidőn belül megérkezik, a sorszámot mod 2 lépteti, és a következő keretet küldi; ha a határidő lejár, az aktuális sorszámú keretet küldi újra.
- **Vevő**: 0-s sorszámú keretre vár. Érkezéskor ellenőrzi az összeget **és a sorszámot**; ha minden rendben, továbbadja, nyugtáz, és mod 2 lépteti a várt sorszámot. Hibás keretet eldob, nem nyugtáz. A rossz sorszámú (duplikált) keretet **eldobja, de nyugtázza**, így a küldő továbbléphet.

Forgatókönyvek: keretvesztés → időtúllépés → újraküldés; nyugtavesztés → újraküldés → a vevő a duplikátumot felismeri és eldobja. Az ABP egy ARQ-protokoll ([[concepts/telekom/hibakezeles-alapjai]]).

### Csatornakihasználtság

A kihasználtság ($\eta$) a csomag elküldéséhez szükséges idő ($T_{packet}$) és a következő keret küldéséig eltelő idő aránya. ABP esetén:

$$\eta = \frac{T_{packet}}{T_{packet} + d + T_{ack} + d},$$

ahol $d$ a propagációs késés, $T_{ack}$ a nyugta átviteli ideje. Jelölje $a = d / T_{packet}$: ha $a > 1$, a keret eleje még meg sem érkezett, amikor az adó már befejezte a küldést — a csatorna nagyrészt üres.

Számpélda: 1 Gbps vonalon 1000 bájtos keret, $T_{packet} = 8000/10^9 = 8\,\mu s$; 15 ms propagációs késés mellett (és elhanyagolható $T_{ack}$-val) $\eta \approx 8\cdot10^{-6} / 0{,}03 \approx 0{,}03\%$. **Nagy propagációs idő esetén az ABP nem hatékony.**

A megoldás: egyszerre több keret küldése nyugta megvárása nélkül (*pipelining*), az ABP kiterjesztése több sorszámmal: [[concepts/telekom/csuszoablak-protokollok]].

**Vizsgaszempont:** miért kell sorszám (duplikátumok), miért elég 1 bit megáll-és-várnál, és a kihasználtsági képlet alkalmazása.

## Kapocs

- [[concepts/telekom/csuszoablak-protokollok]] — a pipelining és a nagyobb ablak
- [[concepts/telekom/hibakezeles-alapjai]] — ARQ mint stratégia
- [[concepts/telekom/halozati-alapfogalmak]] — propagációs és átviteli késleltetés
