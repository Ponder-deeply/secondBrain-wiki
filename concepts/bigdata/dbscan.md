---
tags: [concept, bigdata/gepi-tanulas-klaszterezes-es-dimenziocsokkentes]
sources: [BDAEM-2022-EA10.pptx]
derivation: source
updated: 2026-09-12
---

# DBSCAN

A DBSCAN (*Density-Based Spatial Clustering of Applications with Noise*) egy
sűrűségalapú klaszterező algoritmus: a klasztereket nem középpont-távolság,
hanem lokális pontsűrűség alapján határozza meg, ami lehetővé teszi tetszőleges
alakú klaszterek felismerését és a zaj kezelését.

## Tartalom

### Pontok osztályozása

A DBSCAN két paramétere: $\varepsilon$ (Eps, a szomszédság sugara) és
$\text{MinPts}$ (a klaszterponthoz szükséges minimális szomszédszám). Ezek
alapján minden pont három kategória egyikébe kerül:

- **Belső pont (core point):** egy $p$ pont akkor belső pont, ha az
  $\varepsilon$-sugarú környezetében legalább $\text{MinPts}$ pont található:
  $$|N_\varepsilon(p)| = |\{q \mid \text{dist}(p,q) \le \varepsilon\}| \ge \text{MinPts}$$
- **Határpont (border point):** nem belső pont, de egy (vagy több) belső pont
  $\varepsilon$-környezetében helyezkedik el.
- **Zajpont (noise point):** sem nem belső, sem nem határpont.

### Az algoritmus lépései

1. Minden pontot minősítsünk belső, határ- vagy zajpontnak.
2. Töröljük a zajpontokat.
3. Kössünk élt minden olyan belső pontpár közé, amelyek egymás
   $\varepsilon$-környezetében vannak.
4. Az így összefüggő belső pontok minden csoportja külön klaszter legyen.
5. Minden határpontot rendeljünk hozzá ahhoz a klaszterhez, amelynek belső
   pontjához (pontjaihoz) tartozik.

### Idő- és tárkomplexitás

Egy $n$ pontból álló $X$ adathalmazra a DBSCAN időigénye
$O(n \times \text{az } \varepsilon\text{-környezet megkeresésének költsége})$.

- Legrosszabb esetben ez $O(n^2)$.
- Alacsony dimenziószámú terekben hatékony adatszerkezetekkel (pl. kd-fák)
  $O(n \log n)$-re csökkenthető, mivel ezek gyorsan megtalálják egy pont adott
  sugarú környezetét.

### $\varepsilon$ és MinPts megválasztása

Az ötlet, hogy egy klaszteren belüli pontok $k$. legközelebbi szomszédja
nagyjából azonos távolságra van, míg a zajpontok $k$. legközelebbi szomszédja
ennél távolabb esik. Ez alapján az egyes pontok $k$. szomszédig mért, sorba
rendezett távolságát ábrázolva egy "törésponton" (éles emelkedésen) leolvasható
egy ésszerű $\varepsilon$ érték.

### Erősségek és gyengeségek

**Erősségek:**

- ellenálló a zajjal szemben;
- tetszőleges alakú és méretű klasztereket képes felismerni, nem csak
  konvex/gömbszerű alakzatokat.

**Gyengeségek:**

- nehezen kezeli az eltérő sűrűségű klasztereket (ha a klaszterek
  sűrűsége nagyon különböző, egyetlen $\varepsilon$/MinPts pár nem
  megfelelő mindegyikre);
- magas dimenziószámú terekben problémás, mert a sűrűség fogalma ott
  elmosódik ("curse of dimensionality");
- számításigényes lehet, ha a legközelebbi szomszédok keresése drága.

## Kapocs

- [[concepts/bigdata/k-means]] — másik klaszterező algoritmus; szemben a
  DBSCAN sűrűségalapú megközelítésével a k-means középpont-távolság alapján,
  előre rögzített klaszterszámmal particionál
- [[concepts/bigdata/gepi-tanulas-alapfogalmak]] — a felügyelet nélküli
  tanulás fogalmi kerete, amelybe a klaszterezés (így a DBSCAN is) tartozik
- [[concepts/bigdata/dimenziocsokkentes]] — a felügyelet nélküli tanulás
  másik fő ága: míg a klaszterezés kategorikus címkével, a dimenziócsökkentés
  alacsonyabb dimenziós valós vektorral tömöríti az adatot
</content>
