---
tags: [concept, bigdata/ajanlorendszerek]
sources: [BDAEM-2022-EA11.pdf]
derivation: source
updated: 2026-09-12
---

# Felhasználó-alapú kollaboratív szűrés

Memóriaalapú kollaboratív szűrési módszer, amely a célfelhasználóhoz (target
user) leginkább hasonló ízlésű felhasználók (szomszédság) értékeléseinek súlyozott
átlagából jósolja meg a célfelhasználó ismeretlen preferenciáit.

## Tartalom

### A probléma felállítása

Adott $m$ felhasználó és $n$ elem (film, könyv, dal, ...) listája, valamint egy
$n \times m$ értékelési mátrix $v_{ij}$, ahol $v_{ij} = ?$, ha az $i$.
felhasználó nem értékelte a $j$. elemet. A visszajelzés lehet **explicit**
(értékelés) vagy **implicit** (vásárlás, kattintás). A feladat: minden
felhasználóhoz minden elemre megjósolni a preferenciát, azzal az
alapfeltevéssel, hogy **hasonló visszajelzés ↔ hasonló ízlés**.

### A kollaboratív szűrés alapvető lépései

1. Meghatározni a célfelhasználó (target/active user) meglévő értékeléseit.
2. Egy hasonlósági függvény alapján megkeresni a célfelhasználóhoz leginkább
   hasonló felhasználókat (**szomszédság-formálás**, neighborhood formation).
3. Azonosítani, mely termékeket kedvelték ezek a hasonló felhasználók.
4. **Előrejelzést generálni** — megbecsülni azt az értékelést, amit a
   célfelhasználó adna az adott termékre.
5. Az előrejelzés alapján a top-N terméket ajánlani.

### A CF "hozzávalói"

- $m$ felhasználó és $n$ elem listája.
- Minden felhasználóhoz egy elemlista, hozzárendelt véleménnyel: **explicit**
  (értékelési pontszám) vagy **implicit** (vásárlási rekordok, lejátszások).
- A célfelhasználó (active user), akire az előrejelzést végezzük.
- **Metrika** a felhasználók közötti hasonlóság mérésére.
- Módszer a **szomszédok** részhalmazának kiválasztására.
- Módszer az előrejelzés kiszámítására a felhasználó által még nem értékelt
  elemekre.

### Előrejelzés és hasonlóság képletei

Adott $u_i$ felhasználók ($i=1,\dots,n$) és $p_j$ termékek ($j=1,\dots,m$)
gyűjteménye, valamint az $n\times m$ értékelési mátrix $v_{ij}$
($v_{ij}=?$, ha $i$ nem értékelte $j$-t). Az $i$ felhasználó $j$ termékre adott
előrejelzése kétféleképpen számolható:

$$v_{ij}^{*} = K\sum_{v_{kj}\neq ?} u_{ik} v_{kj} \qquad \text{vagy} \qquad
v_{ij}^{*} = v_i + K\sum_{v_{kj}\neq ?} u_{ik}(v_{kj}-v_k)$$

ahol a második változat a felhasználók saját átlagértékeléséhez ($v_i$, $v_k$)
viszonyítva korrigál, $K$ pedig normalizáló konstans.

A felhasználók közti hasonlóság ($u_{ik}$) Pearson-korrelációval:

$$u_{ik} = \frac{\sum_j (v_{ij}-v_i)(v_{kj}-v_k)}{\sqrt{\sum_j(v_{ij}-v_i)^2}\sqrt{\sum_j(v_{kj}-v_k)^2}}$$

vagy koszinusz-hasonlósággal:

$$\cos(u_i,u_j) = \frac{\sum_{k=1}^{m} v_{ik}v_{jk}}{\sqrt{\sum_{k=1}^{m}v_{ik}^2}\sqrt{\sum_{k=1}^{m}v_{jk}^2}}$$

### Levezetett példa

A forrás egy 6 felhasználós, 5 filmes (Sherlock, House of Cards, Avengers,
Breaking Bad, Walking Dead) példán mutatja be a menetet a célfelhasználóra
(a táblázat egyik sora):

1. Kiszámítja a célfelhasználó hasonlóságát ($sim(u,v)$) minden más
   felhasználóval a közösen értékelt filmek alapján (két felhasználó, akikkel
   nincs közös értékelés, `NA` hasonlóságot kap).
2. A kapott hasonlósági értékek (pl. $0{,}87$, $1$, $-1$) alapján súlyozza az
   egyes felhasználók értékeléseit azokra a filmekre, amelyeket a
   célfelhasználó még nem értékelt.
3. Az így kapott súlyozott átlagok (a példában $3{,}51^*$, $3{,}81^*$,
   $2{,}42^*$, $2{,}48^*$) adják a hiányzó értékelések előrejelzését, amelyek
   alapján a top-N ajánlás összeállítható.

### Kihívások

- **Ritkaság (sparsity)** — nagy elemhalmazok kiértékelésénél a felhasználói
  vásárlások/értékelések aránya jellemzően 1% alatti, így sok pár között nem is
  lehet hasonlóságot számolni.
- **Pontatlanság** — a legközelebbi szomszéd (nearest neighbor) alapú
  előrejelzések emiatt gyakran pontatlanok.
- **Skálázhatóság** — a legközelebbi szomszéd keresés számításigénye a
  felhasználók és az elemek számával együtt is nő.
- **Gyenge kapcsolat** a hasonló ízlésű, de ritkán értékelő felhasználók
  között.
- **Megoldási irány**: rejtett (latent) modellek használata, amelyek csökkentett
  dimenziós térben ragadják meg a felhasználók és elemek közti hasonlóságot —
  ld. [[concepts/bigdata/matrixfaktorizacio-ajanlorendszerekben]].

## Kapocs

- [[concepts/bigdata/ajanlorendszerek-alapjai]] — a kollaboratív szűrés helye a
  tartalomalapú/kollaboratív felosztásban, illetve a memória-/modellalapú
  taxonómia
- [[concepts/bigdata/elem-alapu-kollaborativ-szures]] — a másik memóriaalapú
  szomszédsági módszer, amely felhasználók helyett elemek hasonlóságára épít,
  és jobban skálázódik
- [[concepts/bigdata/matrixfaktorizacio-ajanlorendszerekben]] — a felhasználó-
  alapú CF ritkasági és skálázhatósági problémáira adott modellalapú válasz
