---
tags: [concept]
sources: [BDAEM-2022-EA12.pdf]
references: ["LeCun, Bottou, Bengio, Haffner: Gradient-Based Learning Applied to Document Recognition, Proceedings of the IEEE, 86(11):2278-2324, 1998"]
derivation: source
updated: 2026-09-12
---

# Konvolúciós neurális hálózat (ConvNet)

A konvolúciós neurális hálózat (ConvNet, CNN) olyan feedforward hálózat,
amely konvolúciós szűrőkkel és résztávmintavételezéssel (subsampling)
dolgozza fel a bemenetet, jelentősen kevesebb paraméterrel, mint egy azonos
méretű, teljesen összekötött hálózat.

## Tartalom

### Motiváció: kevesebb paraméter, könnyebb tanítás

A forrás a hagyományos, teljesen összekötött feedforward hálózatokhoz
képest a ConvNet-ek három tulajdonságát emeli ki: sokkal kevesebb kapcsolat
és paraméter; ebből adódóan könnyebb taníthatóság; miközben az elméletileg
elérhető legjobb teljesítmény csak kis mértékben marad el a teljesen
összekötött hálózatétól. Ez a paraméterszám-csökkenés a konvolúciós
rétegekben megvalósuló **súlymegosztásból** (ugyanaz a szűrő fut végig a
teljes bemeneten) fakad.

### A konvolúciós szűrő (kernel)

A konvolúciós réteg egy kis méretű (a bemutatott példában $3\times3$)
szűrőmátrixot (kernel/filter) csúsztat végig a bemeneti mátrixon (pl. egy
képen); minden pozícióban a szűrő és a lefedett bemeneti terület
elemenkénti szorzatösszegét számítja ki, ez adja a kimeneti (konvolvált)
mátrix egy celláját. A forrás numerikus példán mutatja be a szűrő
négy egymást követő pozícióban való alkalmazását egy $5\times5$-ös
bemeneten, amely egy $3\times3$-as kimeneti térképet eredményez.

Ugyanez az elv hagyományos képfeldolgozási szűrőkre (nem tanult, hanem
kézzel tervezett kernelekre) is alkalmazható — a forrás az élkiemelés (edge
detection), élesítés (sharpen), box blur és Gauss-elmosás (Gaussian blur)
szűrőmátrixait és azok hatását mutatja be egy fényképen. A ConvNet-ben a
különbség az, hogy a szűrők együtthatóit a hálózat **tanulja**, nem
kézzel adják meg.

### LeNet-5 architektúra

A forrás a LeCun és szerzőtársai (1998) által bemutatott LeNet-5
architektúrát ismerteti kézzel írott karakterek felismerésére:

- **bemenet**: $32\times32$ pixeles kép (a legnagyobb karakter $20\times20$,
  hogy a legmagasabb szintű jellemződetektorok receptív mezőjének
  közepébe essen minden fontos információ),
- **C1, C3** — konvolúciós rétegek (feature map-eket állítanak elő, pl. C1:
  $6@28\times28$, C3: $16@10\times10$),
- **S2, S4** — résztávmintavételező (subsampling) rétegek, amelyek
  csökkentik a feature map-ek felbontását (pl. S2: $6@14\times14$, S4:
  $16@5\times5$),
- **C5, F6** — teljesen összekötött rétegek,
- **kimenet**: 10 osztály (a tíz számjegy),
- a fekete-fehér pixelértékeket normalizálják (pl. fehér $=-0.1$, fekete
  $=1.175$), hogy a pixelek átlaga 0, szórása 1 legyen.

Rétegtípusok jelölése: Cx — konvolúciós réteg, Sx — subsample réteg, Fx —
teljesen összekötött (fully connected) réteg.

### Rétegenkénti jellemzőtanulás

Arcfelismerési példán a forrás azt mutatja be, hogy az egymás után épített
konvolúciós rétegek egyre absztraktabb jellemzőket tanulnak: az első réteg
alacsony szintű mintázatokat (élirányokat, foltokat), a második réteg ezekből
összeálló arcrészleteket (szem, orr, száj), a harmadik réteg pedig teljes,
arcszerű mintázatokat reprezentál. Ez konkrét illusztrációja annak az
általánosabb megfigyelésnek, hogy a mély hálózatok egymást követő rétegei
egyre magasabb szintű jellemzőket detektálnak — lásd
[[concepts/bigdata/mesterseges-neuron]] a rejtett rétegek
jellemződetektorrá válásáról.

### Eredmények MNIST-en

A forrás az MNIST kézzel írott számjegy-adathalmazon mért teszthibát idézi:
60 000 eredeti tanítópéldával 0,95%, míg 540 000 mesterségesen torzított
példával kiegészítve (összesen 600 000 tanítópélda) 0,8% teszthiba érhető
el. A félrekvantosított példák (Misclassified examples) diája azt mutatja,
hogy a hibák jellemzően vizuálisan is összetéveszthető számjegypárok között
(pl. 4→9, 3→5, 9→4) fordulnak elő.

### Alkalmazás molekuláris rendszerekre

A forrás röviden három, a képfeldolgozáson túlmutató mélytanulási alkalmazást
is bemutat molekuláris rendszerekre: a Behler–Parrinello hálózat atomi
energiafüggvények tanulására (Behler & Parrinello, 2007), generátorhálózatok
(variational autoencoder) molekulatervezésre (Gómez-Bombarelli et al., 2016),
és a VAMPnets molekuláris kinetika tanulására (Mardt et al., 2017). Ezek a
tesztkérdéshez közvetlenül nem kapcsolódó, illusztratív alkalmazási példák;
a forrás nem részletezi az architektúrájukat annyira, hogy önálló fogalomlap
indokolt lenne belőlük.

## Kapocs

- [[concepts/bigdata/mesterseges-neuron]] — a ConvNet a feedforward
  hálózatok egy specializált altípusa
- [[concepts/bigdata/hibavisszaterjesztes]] — a ConvNet súlyait (a szűrők
  együtthatóit is beleértve) hibavisszaterjesztéssel tanítják
- [[concepts/bigdata/aktivacios-fuggvenyek]] — a konvolúciós rétegek
  kimenetére is nemlineáris aktivációs függvényt alkalmaznak
