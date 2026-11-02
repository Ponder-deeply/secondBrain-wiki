---
title: Telekom ZH — feladattípusok és gyakorlás
---

# Telekom ZH — feladattípusok és gyakorlás

A ZH két részből áll: **számolós kérdések** (átviteli idő, késleltetés, újraküldés, bitbeszúrás, Hamming-távolság, CRC) és egy **Wireshark-rész** (egy `.pcap` + TLS-kulcsnapló alapján). Minden típushoz: képlet → a fotón szereplő feladat megoldása → csapdák → gyakorló feladatok (a megoldás becsukható blokkban).

> [!warning] A fotókon beírt válaszok közül három hibás
> - **Bitbeszúrás:** `1000111111` ✗ → helyesen **`100011111001`**
> - **CRC:** `1111011` ✗ → helyesen **`1110100`**
> - **Switches késleltetés:** `4224` ✗ (valószínűleg) → **`8424`** ms, mert a switch *tárol és továbbít*, azaz a csomagot kétszer kell „feltenni” a vonalra (lásd 2.)

---

## 1. Átviteli idő hatékonysággal

Elmélet: [[concepts/telekom/halozati-alapfogalmak]] (átviteli késleltetés $d_T = L/B$, SI-prefixumok).

$$t = \frac{\text{adatméret [bit]}}{\text{sebesség [bit/s]} \cdot \text{hatékonyság}}$$

**Fotó:** 48 GB, 3 Gbps, 69%
$t = \dfrac{48 \cdot 8\ \text{Gb}}{3 \cdot 0{,}69\ \text{Gb/s}} = \dfrac{384}{2{,}07} \approx$ **185,51 s**

**Csapdák:** bájt → bit (×8)! Hálózati sebességnél SI-prefixum: 1 GB $=10^9$ B, 1 Gbps $=10^9$ bit/s (a $2^{30}$-os számolás 199,19-et adna — a várt válasz a 185,5).

> [!example]- Gyakorlás (megoldással)
> 1. 5 Gbps, 80%, 30 GB → $240/4 =$ **60 s**
> 2. 100 Mbps, 75%, 600 MB → $4800/75 =$ **64 s**
> 3. 1 Gbps, 50%, 2,5 GB → $20/0{,}5 =$ **40 s**

## 2. Teljes késleltetés switchen át

Elmélet: [[concepts/telekom/halozati-alapfogalmak]] (propagációs vs. átviteli késés), [[concepts/telekom/bridge-es-switch]].

Az egyszerű switch **tárol és továbbít** (*store-and-forward*): előbb a teljes csomagot fogadja, csak utána kezdi továbbküldeni. Így **minden szakaszon** újra fellép az átviteli késés is:

$$d_{\text{teljes}} = k \cdot \frac{L}{B} + \sum_{i=1}^{k} d_{\text{prop},i}\qquad (k = \text{szakaszok száma} = \text{switchek} + 1)$$

**Fotó:** 3 Kbps, 2 szakasz × 12 ms, 12 600 bit
$L/B = 12600/3000 = 4{,}2\ \text{s} = 4200$ ms → $2\cdot 4200 + 2\cdot 12 =$ **8424 ms**

**Csapdák:** a `4224` az a hiba, amikor az átviteli időt csak egyszer számolod (mintha a switch nem is lenne ott). 1 Kbps $=1000$ bit/s. Mértékegység: ms!

> [!example]- Gyakorlás (megoldással)
> 1. 8 Kbps, 2 szakasz × 20 ms, 16 000 bit → $2\cdot 2000 + 40 =$ **4040 ms**
> 2. 10 Kbps, 2 switch (3 szakasz) × 5 ms, 5000 bit → $3\cdot 500 + 15 =$ **1515 ms**
> 3. 2 Mbps, 1 switch, 2 × 1 ms, 1500 bájt → $L/B = 12000/2\cdot10^6 = 6$ ms → $12 + 2 =$ **14 ms**

## 3. Hány egységet kellett újraküldeni?

Nincs rá külön lap; az 1. típus képletének megfordítása.

1. Az idő alatt ténylegesen átküldött adat: $\text{sebesség} \cdot t$.
2. Ez hány egység: $\dfrac{\text{átküldött}}{\text{egységméret}}$.
3. Hasznos egységek: $\dfrac{\text{adatméret}}{\text{egységméret}}$ (felfelé kerekítve, csak teljes egység küldhető).
4. Újraküldött = (2) − (3).

**Fotó:** 13 Mbps, 232 MB, 200 KB egységek, 4 perc
$240 \cdot 13 = 3120$ Mb $= 390$ MB → $390\,000/200 = 1950$ egység; hasznos: $232\,000/200 = 1160$ → **790**

> [!example]- Gyakorlás (megoldással)
> 1. 10 Mbps, 100 MB, 250 KB, 2 perc → $150\ \text{MB}/250\ \text{KB} = 600$; hasznos $400$ → **200**
> 2. 20 Mbps, 500 MB, 500 KB, 5 perc → $750\ \text{MB} \to 1500$; hasznos $1000$ → **500**
> 3. 8 Mbps, 50 MB, 100 KB, 1 perc → $60\ \text{MB} \to 600$; hasznos $500$ → **100**

## 4. Bitbeszúrás

Elmélet: [[concepts/telekom/keretezes]] — HDLC-keretjelző `01111110`.

**Szabály:** balról jobbra olvasva **minden öt egymást követő `1` után** beszúrunk egy `0`-t (akkor is, ha utána amúgy is 0 jönne, és akkor is, ha az adat végén van). A számláló a beszúrt 0 után nulláról indul. „Keret nélkül” = a keretjelzőket nem írjuk az elejére/végére.

**Fotó:** `10001111101`
`1000` `11111` → **0** → `01` = **`100011111001`**

**Csapdák:** a 0-t az ötödik 1 *után* szúrjuk, nem az 1-est cseréljük. A beszúrás után a hossz nő (11 → 12 bit) — ha a válaszod rövidebb, biztosan rossz.

> [!example]- Gyakorlás (megoldással)
> 1. `0111111101111110` → **`011111011011111010`**
> 2. `111111111111` (12 db 1) → **`11111011111011`**
> 3. `1011111011111` → **`101111100111110`** (a végén álló öt 1 után is kell a 0!)

## 5. Kódkönyv: hány hiba detektálható / javítható?

Elmélet: [[concepts/telekom/hamming-tavolsag-es-korlat]].

1. Minden kódszópárra: $d(x,y)$ = XOR-uk egyeseinek száma.
2. $d(S) =$ a **legkisebb** páronkénti távolság.
3. Detektálható: $d(S) - 1$; javítható: $\lfloor (d(S)-1)/2 \rfloor$.

4 kódszó → $\binom42 = 6$ pár. Elég megtalálni egy 1-es távolságot, onnan 0 a válasz mindkettőre.

**Fotó 1:** {110011, 010111, 001110, 000111} — távolságok: 2, 5, 3, 3, **1** (010111–000111), 2 → $d=1$ → detektálható: **0**
**Fotó 2:** {100001, 011010, 001101, 000101} — 5, 3, 2, 4, 5, **1** (001101–000101) → $d=1$ → javítható: **0** ✓

> [!example]- Gyakorlás (megoldással)
> 1. {000000, 111000, 000111, 111111} → $d=3$ → detektál **2**, javít **1**
> 2. {00000, 01011, 10101, 11110} → $d=3$ → detektál **2**, javít **1**
> 3. {0000000000, 0000011111, 1111100000, 1111111111} → $d=5$ → detektál **4**, javít **2**
> 4. {0000, 0011, 1100, 1111} → $d=2$ → detektál **1**, javít **0**

## 6. CRC

Elmélet és kidolgozott példa: [[concepts/telekom/crc]].

1. $r$ = generátor hossza − 1 (fokszám). Fűzz $r$ darab 0-t az üzenethez.
2. Mod 2 osztás: ahol a maradék aktuális első bitje 1, XOR-old alá a generátort; ahol 0, lépj tovább.
3. A maradék utolsó $r$ bitje az ellenőrzőösszeg — **pontosan $r$ bit**, vezető nullákkal együtt.

**Fotó:** üzenet `1000100100101111`, generátor `11001001` ($r=7$)

```
10001001001011110000000      (üzenet + 7 nulla)
11001001                     XOR
01000000001011110000000
 11001001
00100100101011110000000
  11001001
00010110111011110000000
   11001001
00001111110011110000000
    11001001
00000011010111110000000
      11001001
00000000011110110000000
         11001001
00000000000111111000000
           11001001
00000000000001101010000
             11001001
00000000000000001110100      → maradék: az utolsó 7 bit
```
A maradék: **`1110100`**. (Ellenőrzés: `1000100100101111` + `1110100` osztható a generátorral.)

**Csapdák:** a nullák hozzáfűzése kimarad; rossz $r$ (a generátor *hossza* mínusz egy); a vezető 0-kat levágod (`0100` ≠ `100`, ha $r=4$).

> [!example]- Gyakorlás (megoldással)
> 1. `1101011011`, gen `10011` → **`1110`** (a lap kidolgozott példája)
> 2. `11010011101100`, gen `1011` → **`100`**
> 3. `101110001`, gen `10011` → **`0100`**
> 4. `1111000010101100`, gen `110101` → **`01111`**

---

## 7. Wireshark-rész

> [!info] Ez a rész nem a wikiből származik
> A telekom diasorok nem tartalmaznak Wireshark-anyagot; az alábbi szűrők a Wireshark saját mezőnevei. A protokollok háttere: [[concepts/telekom/http-es-web]], [[concepts/telekom/dns]], [[concepts/telekom/arp-dhcp-icmp]], [[concepts/telekom/tcp]].

**0. lépés — a HTTP2 visszafejtése.** A HTTP2 TLS-en megy, a kulcsnapló nélkül csak `TLS Application Data` látszik.
*Edit → Preferences → Protocols → TLS → (Pre)-Master-Secret log filename* → `sslZHKeys.log`. Utána megjelennek a `HTTP2` sorok.
A válaszokat egy szövegfájlba írd, és azt töltsd fel — enélkül a ZH érvénytelen!

**Számolás:** a szűrő beírása után az alsó státuszsor `Displayed: N` értéke a **csomagok** száma.

| Kérdés | Megjelenítési szűrő | Mit olvass le |
|---|---|---|
| Hány `.css` töltődött le a *www.youtube.com*-ról HTTP2-vel? | `http2.headers.authority == "www.youtube.com" && http2.headers.path contains ".css"` | Displayed |
| Hány HTTP2 GET ment a *www.youtube.com*-ra? | `http2.headers.method == "GET" && http2.headers.authority == "www.youtube.com"` | Displayed |
| Az első HTTP2 GET TCP forrásportja a *ggombos.web.elte.hu*-ra | `http2.headers.method == "GET" && http2.headers.authority == "ggombos.web.elte.hu"` | a legkisebb `No.` sor → TCP fejléc *Source Port* |
| Hány csomag érkezett 200-as HTTP2 státusszal? | `http2.headers.status == "200"` | Displayed |
| Hány RST a 157.181.1.232 felé kapcsolódásnál? | `ip.addr == 157.181.1.232 && tcp.flags.reset == 1` | Displayed (nézd meg az irányt is: az elutasító RST a szervertől jön, `ip.src == …`) |
| Milyen IP-t adott a DNS a *lakis.web.elte.hu*-ra? | `dns.qry.name == "lakis.web.elte.hu" && dns.flags.response == 1` | Answers → `A` rekord (ha van CNAME-lánc, az utolsó A rekord) |
| Hány ARP-kérés ment a 157.181.165.65 miatt? | `arp.opcode == 1 && arp.dst.proto_ipv4 == 157.181.165.65` | Displayed (`opcode 1` = kérés, `2` = válasz) |
| Hány ICMP csomagot küldött a 111.203.180.218? | `icmp && ip.src == 111.203.180.218` | Displayed |

**Csapdák:**
- **Csomag ≠ kérés.** Egy TCP-csomagban több HTTP2 HEADERS keret is utazhat. Ha a kérdés *kérést* számol, és gyanús az eredmény, számold meg a mezőértékeket tshark-kal:
  `tshark -r zhTraffic.pcap -o tls.keylog_file:sslZHKeys.log -Y '<szűrő>' -T fields -e http2.headers.method | tr ',' '\n' | grep -c GET`
- A `contains` kis- és nagybetűérzékeny, és a `?ver=…` query-stringes `.css`-t is megtalálja (jó); a `.css` a `.cssx`-re is illeszkedne (ritka).
- A HTTP2 pszeudo-fejlécek (`:authority`, `:path`, `:method`, `:status`) a Wiresharkban `http2.headers.authority`, `.path`, `.method`, `.status` néven szerepelnek. Ha egy szűrő piros, írd be, hogy `http2.headers.`, és a Wireshark felajánlja a mezőket.
- Portot oszlopként is kitehetsz: jobb klikk a *Source Port* mezőre → *Apply as Column*.
- Ha a szűrő 0 találatot ad, először azt ellenőrizd, hogy a kulcsnapló be van-e töltve.

---

## Ismétlőlap (1 perc a ZH előtt)

| Típus | Képlet / szabály |
|---|---|
| átviteli idő | $\dfrac{8 \cdot \text{bájt}}{B \cdot \eta}$, SI-prefixum |
| switch | $k \cdot L/B + \sum d_{prop}$ |
| újraküldés | $\dfrac{B t}{\text{egység}} - \dfrac{\text{adat}}{\text{egység}}$ |
| bitbeszúrás | 5 db `1` után `0`, a hossz nő |
| kódkönyv | $d_{min}$; detektál $d-1$, javít $\lfloor (d-1)/2 \rfloor$ |
| CRC | $r$ nulla, XOR-osztás, $r$ bites maradék |
