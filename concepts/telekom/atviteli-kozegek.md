---
tags: [concept]
sources: [Laki_Lecture_2.pdf]
derivation: source
kind: overview
element: air
updated: 2026-09-25
---

# Átviteli közegek

A fizikai réteg alatt fekvő médium lehet vezetékes (sodrott érpár, koaxiális kábel, optikai szál) vagy vezeték nélküli (rádió, mikrohullám, infravörös, látható fény, műhold). A közeg határozza meg az elérhető sávszélességet, a távolságot, a csillapítást és a késleltetést.

## Tartalom

### Vezetékes közegek

- **Mágneses adathordozók** — a sávszélesség jó, de a késleltetés nagy (nem on-line kapcsolat; „a teherautónyi szalag” esete).
- **Sodort érpár** (*twisted pair*) — főként távbeszélő-rendszerekben; dupla rézhuzal; analóg és digitális jelátvitelre is. Változatai: **UTP** (árnyékolatlan) és **STP** (árnyékolt).
- **Koaxiális kábel** — nagyobb sebesség és távolság érhető el, mint sodort érpárral. Felépítése: rézmag, szigetelőanyag, fonott külső vezető, műanyag védőburkolat. Analóg (75 Ω) és digitális (50 Ω) jelátvitelre.
- **Fényvezető szálak** — részei a fényforrás, az átviteli közeg és a detektor; fényimpulzus = 1-es bit, nincs impulzus = 0-s bit. A fény a **teljes belső visszaverődés** miatt marad a szálban (ha a beeső sugár szöge eléri a határszöget); a különböző szögben haladó sugaraknak más-más **módusa** van. Felépítés: üvegmag, tükröző anyag (üveg), műanyag köpeny.

A fényforrás szerinti összevetés:

| Jellemző | LED | Félvezető lézer |
|---|---|---|
| Adatátviteli sebesség | alacsony | magas |
| Módus | többmódusú | több- vagy egymódusú |
| Távolság | kicsi | nagy |
| Élettartam | hosszú | rövid |
| Hőmérséklet-érzékenység | kicsi | jelentős |
| Ár | olcsó | drága |

### Hullámfizikai alapok

- **Frekvencia** $f$: az elektromágneses hullám másodpercenkénti rezgésszáma, Hz-ben.
- **Hullámhossz** $\lambda$: két egymást követő hullámcsúcs (vagy -völgy) távolsága.
- **Fénysebesség** $c \approx 3\cdot 10^8$ m/s vákuumban; **rézben és üvegszálban kb. $2/3$-ára csökken**.
- Összefüggés: $\lambda f = c$. Példa: egy 3 GHz-es jel hullámhossza vákuumban $\lambda = 3\cdot10^8 / 3\cdot10^9 = 0{,}1$ m $= 10$ cm — éppen a rádió és a mikrohullám határa.

### Az elektromágneses spektrum

| Tartomány | Hullámhossz (cm) | Frekvencia (Hz) |
|---|---|---|
| Rádió | > 10 | < $3\cdot10^9$ |
| Mikrohullám | 10 – 0,01 | $3\cdot10^9$ – $3\cdot10^{12}$ |
| Infravörös | 0,01 – $7\cdot10^{-5}$ | $3\cdot10^{12}$ – $4{,}3\cdot10^{14}$ |
| Látható | $7\cdot10^{-5}$ – $4\cdot10^{-5}$ | $4{,}3\cdot10^{14}$ – $7{,}5\cdot10^{14}$ |
| Ultraibolya | $4\cdot10^{-5}$ – $10^{-7}$ | $7{,}5\cdot10^{14}$ – $3\cdot10^{17}$ |
| Röntgen | $10^{-7}$ – $10^{-9}$ | $3\cdot10^{17}$ – $3\cdot10^{19}$ |
| Gamma | < $10^{-9}$ | > $3\cdot10^{19}$ |

A rádiósávok elnevezése tizedes lépésekben: VLF (< 30 kHz, pl. órajelek), LF (30–300 kHz, tengeri mobil), MF (300 kHz–3 MHz, szárazföldi mobil, AM rádió), HF (3–30 MHz, légiforgalmi), VHF (30–300 MHz, TV, FM rádió), UHF (300 MHz–3 GHz, TV, navigáció), SHF (3–30 GHz, műholdas kommunikáció). A sodrott érpár kb. $10^4$–$10^6$ Hz, a koax $10^5$–$10^8$ Hz, az optikai szál $10^{14}$ Hz körül dolgozik.

### Vezeték nélküli közegek

- **Rádiófrekvenciás** — egyszerűen előállítható, nagy távolság, kültéren és beltéren is; terjedési jellemzői frekvenciafüggők (földközeli hullám vagy az ionoszféráról visszaverődő hullám).
- **Mikrohullámú** — egyenes vonal mentén terjed; az elhalkulás (*fading*) problémája; nem drága.
- **Infravörös és milliméteres hullámú** — kis távolságra; szilárd tárgyakon nem hatol át.
- **Látható fényhullámú** — lézerforrás + fényérzékelő; nagy sávszélesség, olcsó, nem engedélyköteles, de az időjárás erősen befolyásolja.

### Kommunikációs műholdak

Transzpondereket tartalmaznak, amelyek a spektrum egy részét figyelik, a jelet felerősítik és egy másik frekvencián továbbítják (széles vagy keskeny területre). A magassággal nő a keringési idő és a késleltetés.

| Típus | Magasság | Késleltetés | Műholdak a teljes lefedéshez |
|---|---|---|---|
| **GEO** (geoszinkron) | ~35 800 km | ~270 ms | 3 |
| **MEO** (közepes röppályás) | a két Van Allen-öv között | 35–85 ms | 10 |
| **LEO** (alacsony röppályás) | az alsó Van Allen-öv alatt | 1–7 ms | 50 |

### Internet a kábel-TV hálózaton

A fejállomástól (*head-end*) nagy sávszélességű optikai trönk vezet a *fiber node*-okig, onnan koaxiális kábel a házakig (HFC). A frekvenciakiosztás: 5–42 MHz **upstream** adat, 54–550 MHz TV és FM, 550–750 MHz **downstream** adat — az aszimmetria a letöltés-központú használatot tükrözi. Ez a frekvenciaosztás egyben FDM ([[concepts/telekom/multiplexalas]]).

**Vizsgaszempont:** $\lambda f = c$ számolás, a műholdtípusok késleltetése, a LED és a lézer összevetése.

## Kapocs

- [[concepts/telekom/halozati-alapfogalmak]] — a médium és a propagációs késés fogalma
- [[concepts/telekom/fourier-analizis-es-savkorlat]] — csillapítás és torzítás a közegben
- [[concepts/telekom/multiplexalas]] — a közeg megosztása több jel között
