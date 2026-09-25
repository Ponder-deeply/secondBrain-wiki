---
tags: [concept, bigdata/bevezetes]
sources: [EA1_bevezetes.pdf]
derivation: source
updated: 2026-09-12
---

# Big Data 5V

A Big Data adatot jellemző öt alapdimenzió — Volume, Velocity, Variety,
Veracity, Value —, amelyek együtt adják meg, hogy egy adathalmaz miért
számít "nagynak", és milyen jellegű feldolgozást igényel.

## Tartalom

### Volume (mennyiség)

Az adat mérete. Illusztrációk: a globális informatikai forgalom volumene
2020-ra becslés szerint 44 zettabájt, a 2020-ig évente létrehozott adat
mennyisége 40 zettabájt (a 2015-ös érték 300%-a), és becslések szerint az
emberiség naponta kb. 2,3 zettabájt adatot termel. Történeti érdekesség: Bill
Gates 1981-es, azóta megcáfolt mondása szerint "640 KB elegendő kell legyen
bárkinek" — a mai adatmennyiséghez képest ez a korlát nevetségesen kicsi.

### Velocity (sebesség)

Az adat keletkezésének és feldolgozásának üteme — jellemzően folyamatos,
valós idejű adatfolyamok formájában. Illusztráció: az internet mai forgalma
percenkénti bontásban (Google-keresések, e-mailek, videómegtekintések,
üzenetek stb.) nagyságrendekkel meghaladja, amit hagyományos batch
feldolgozással kezelni lehetne — ez indokolja a stream (valós idejű)
feldolgozás szükségességét.

### Variety (változatosság)

Az adat formátumainak sokfélesége. Három fő kategória:

- **strukturált** adat (pl. relációs táblák),
- **félig strukturált** adat (pl. JSON, XML, CSV, TSV, e-mail),
- **strukturálatlan** adat (pl. log, hang, videó, kép).

### Veracity (megbízhatóság)

Az adat pontosságának és megbízhatóságának kérdése: mennyire lehet
bízni a levont következtetésekben. A dia klasszikus, humoros
korrelációs példákkal illusztrálja, hogy statisztikai összefüggés
(pl. matematikai doktori fokozatok száma és az atomerőművekben tárolt
urán mennyisége között) nem jelent ok-okozati kapcsolatot — a Big Data
elemzésnél kiemelt kockázat az álösszefüggések (spurious correlation)
téves értelmezése.

### Value (érték)

Az adatból ténylegesen kinyerhető üzleti vagy tudományos érték — az a
dimenzió, amiért a másik négy V (volume, variety, velocity, veracity)
elemzése egyáltalán megéri: ezek együtt adják az "insight"-ot (rálátást),
a Value pedig az ebből származó tényleges hatást (impact). A gyakorlatban
a hasznosítható insight kinyerése az erőfeszítés nagyobbik részét (becslés
szerint kb. kétharmadát) igényli.

### Bővített V-modellek

A négy/öt V-n túl a szakirodalom több bővített felsorolást is használ: a
9V-modell (Owais, 2016) a fentieken felül a variabilityt, validityt és
volatilityt is számon tartja; a 10V-modell (Data Science Central) a venue-t
és vocabulary-t, a vagueness-t is hozzáveszi; a 17V-modell (Panimalar, 2017)
pedig ezeket tovább bővíti (pl. visualization, viscosity, virality,
verbosity, voluntariness, versality). A kurzus a gyakorlatban az öt
alapdimenzióra (Volume, Velocity, Variety, Veracity, Value) épít.

## Kapocs

- [[concepts/bigdata/big-data]] — a Big Data fogalma és motivációja, amelynek
  ez a lap az egyik alfejezete
- [[concepts/bigdata/big-data-architektura]] — az adat kezelésére kialakított
  architektúrák
