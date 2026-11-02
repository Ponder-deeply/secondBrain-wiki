---
tags: [concept]
sources: [Laki_Lecture_12_new.pdf]
derivation: source
kind: procedure
element: water
updated: 2026-09-25
---

# HTTP és a web: kapcsolatok, üzenetek, sütik, gyorsítótárak

A HTTP (*HyperText Transfer Protocol*) a web alkalmazási rétegbeli protokollja: kliens–szerver modell, TCP felett (80-as port), elméletben állapotmentes. Egy weboldal egy alap HTML-fájlból és sok hivatkozott objektumból áll; hogy ezeket hány TCP-kapcsolaton és hány RTT alatt töltjük le, az a nem-perzisztens / perzisztens / pipelining változatokon múlik. Az állapotot sütik (*cookies*) viszik, a késleltetést gyorsítótárak és proxyk csökkentik.

## Tartalom

### Alapfogalmak

- Egy **weboldal objektumokból** áll (HTML-fájl, JPEG-kép, Java applet, hangfájl…): egy **alap HTML-fájlból**, amely **több hivatkozott objektumot** tartalmaz.
- Minden objektum egy **URL**-lel címezhető: `www.someschool.edu/someDept/pic.gif` = hosztnév + útvonal.
- **Kliens**: a böngésző, amely HTTP-vel kéri, fogadja és „megjeleníti” az objektumokat; **szerver**: a webszerver, amely a kérésekre objektumokat küld.
- **TCP-t használ**: a kliens TCP-kapcsolatot kezdeményez (socketet hoz létre) a szerver **80-as portjára**, a szerver elfogadja, HTTP-üzeneteket cserélnek, a kapcsolat lezárul ([[concepts/telekom/tcp]]).
- **Állapotmentes** („elméletben”): a szerver nem tárol információt a kliens korábbi kéréseiről. (Az állapottartó protokollok bonyolultak: a múltat karban kell tartani, és összeomláskor a két fél képe inkonzisztens lehet.)
- **Statikus** weboldal: csak manuális szerkesztéssel változik; **dinamikus**: kód végrehajtásaként keletkezik (JavaScript a kliensen, PHP a szerveren, vagy mindkettő).

### Kapcsolattípusok

| | Nem-perzisztens HTTP (HTTP/1.0) | Perzisztens HTTP | Pipelining (HTTP/1.1) |
|---|---|---|---|
| Objektum/kapcsolat | legfeljebb 1 objektum egy TCP-kapcsolaton, utána lezárul | több objektum egy kapcsolaton, egymás után | a kérések aszinkron módon, egymás után kiküldhetők egy perzisztens kapcsolaton |
| Költség | **2 RTT objektumonként**, OS-overhead kapcsolatonként; a böngészők ezért gyakran **párhuzamos** kapcsolatokat nyitnak | amortizálja a TCP-overheadet, de a szerver tovább tartja az állapotot (időkorlátig) | akár **1 RTT** az összes hivatkozott objektumra; a kéréseket sorrendben kell kiszolgálni |

**Válaszidő nem-perzisztens HTTP-nél:**
$$T = 2\,\text{RTT} + \text{fájlátviteli idő},$$
ahol az első RTT a TCP-kapcsolat felépítése, a második a HTTP-kérés és a válasz első bájtjai (feltéve, hogy a GET a harmadik kézfogás-üzenet ACK-jára „ül”). Példa: `page.html` + `hpface.jpg` + `castle.gif` nem-perzisztens, soros letöltése három külön SYN–GET–FIN ciklus.

### Üzenetformátum

Kétféle üzenet: **kérés** (*request*) és **válasz** (*response*), ASCII (ember által olvasható) formátumban.

**Kérés:** kérés-sor (`method sp URL sp version cr lf`), fejlécsorok (`name: value cr lf`), üres sor (`cr lf`), majd a törzs (*entity body*):
```
GET /index.html HTTP/1.1\r\n
Host: www-net.cs.umass.edu\r\n
User-Agent: Firefox/3.6.10\r\n
Connection: keep-alive\r\n
\r\n
```

**Metódusok:** HTTP/1.0: **GET**, **POST**, **HEAD** (a kért objektumot hagyja ki a válaszból). HTTP/1.1: ezek mellett **PUT** (a törzsben lévő fájl feltöltése az URL-ben megadott útvonalra) és **DELETE** (az URL-ben megadott fájl törlése). Űrlapadat feltöltése: **POST** esetén a törzsben, **URL-módszer** (GET) esetén a kérés-sor URL-jében: `www.somesite.com/animalsearch?monkeys&banana`.

**Válasz:** státuszsor (protokoll, státuszkód, státuszszöveg), fejlécsorok (Date, Server, Last-Modified, ETag, Content-Length, Content-Type…), üres sor, adat. Státuszkódok:

| Kód | Jelentés |
|---|---|
| **200 OK** | sikeres kérés, az objektum az üzenetben |
| **301 Moved Permanently** | az objektum elköltözött, új helye a `Location:` fejlécben |
| **400 Bad Request** | a szerver nem értette a kérést |
| **404 Not Found** | a dokumentum nincs a szerveren |
| **505 HTTP Version Not Supported** | |

Kipróbálható kézzel: `telnet cis.poly.edu 80`, majd `GET /~ross/ HTTP/1.1` és `Host: cis.poly.edu`, két Enterrel.

### Sütik (cookies) — állapot a HTTP felett

Négy komponens: (1) cookie-fejlécsor a HTTP **válaszban** (`set-cookie: 1678`); (2) cookie-fejlécsor a következő **kérésben** (`cookie: 1678`); (3) a felhasználó gépén tárolt, böngésző által kezelt cookie-fájl; (4) háttéradatbázis a webhelyen. Első látogatáskor a webhely egyedi azonosítót és adatbázis-bejegyzést hoz létre; a későbbi (akár egy héttel későbbi) kéréseknél a süti alapján süti-specifikus műveletet végez.

Felhasználás: authorizáció, bevásárlókosár, ajánlások, munkamenet-állapot (webes e-mail). Kétféle állapottartás: a protokoll végpontjai tartják (több tranzakción át), vagy **a HTTP-üzenetek viszik** (sütik).

**Harmadik felek:** egy cikkbe ágyazott megosztás-gomb (`sharebutton.gif`) letöltésekor a böngésző a gomb gazdájának (pl. Facebook) a saját sütijét is elküldi — így az megtudja, hogy meglátogattuk az oldalt, minden oldalon, ahol a gomb szerepel. A sütik sokat elárulnak rólunk (magánszféra).

### Web caching és proxy

A felhasználók gyakran újralátogatják az oldalakat; a lap lokális másolata használható (*caching*). **Mikor használható a másolat?**
- **Lokális döntés**: lejárati információ alapján (pl. `Expires` fejléc) vagy heurisztikával. Előny: a tartalom **azonnal** elérhető.
- **Újravalidálás a szerverrel** (*conditional GET*): időbélyeg (`Last-Modified`) vagy tartalom (`ETag`) alapján; a szerver „Not modified”-dal vagy az új tartalommal válaszol. Előny: a tartalom **egy RTT** késleltetéssel elérhető.

**Web proxy**: a kliensek csoportja és a külső szerverek közé helyezett közbülső elem. Előnyök: nagyobb cache és biztonsági ellenőrzés, szervezeti hozzáférés-szabályozás. A **proxy cache** elosztott, nagy gyorsítótárat biztosít; korlát: biztonságos (titkosított) és dinamikus tartalmak nem tárolhatók. (A proxy a rétegzés „megsértésének” példája is: alkalmazási végpontot szimulál a hálózatban — [[concepts/telekom/retegzett-halozati-architektura]].)

**Vizsgaszempont:** nem-perzisztens vs. perzisztens vs. pipelining és a $2\,\text{RTT}$ + átvitel képlet; kérés/válasz formátuma; metódusok és státuszkódok; a süti négy komponense; conditional GET.

## Kapocs

- [[concepts/telekom/tcp]] — a HTTP szállítója, kézfogás és slow start
- [[concepts/telekom/dns]] — a név feloldása a kérés előtt
- [[concepts/telekom/cdn-es-p2p]] — a webes tartalom skálázható kiszolgálása
- [[concepts/telekom/tcp-torlodasvezerles]] — a kis webes folyamok el sem hagyják a slow startot
