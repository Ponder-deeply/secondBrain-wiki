---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-07
---

# Összefüggő halmazok és tartomány

Egy halmaz összefüggő, ha nem esik szét két diszjunkt, nemüres, relatív nyílt darabra. Ez a tisztán topológiai összefüggőségfogalom; a nemüres, nyílt, összefüggő halmazokat tartománynak hívjuk.

## Tartalom

### Definíció

A $H \subset \mathbb{R}^p$ halmaz **összefüggő**, ha nem bontható fel két diszjunkt, nemüres, relatív nyílt halmaz uniójára. Kifejtve: ha $A, B \subset \mathbb{R}^p$ nyílt halmazok, $H \subset A \cup B$ és $H \cap A \cap B = \emptyset$, akkor $H \subset A$ vagy $H \subset B$.

**Megjegyzés.** Egy $G \subset \mathbb{R}^p$ **nyílt** halmaz akkor és csak akkor összefüggő, ha nem bontható fel két diszjunkt, nemüres nyílt halmaz uniójára.

### Következmények

- $\mathbb{R}^p$ összefüggő (mert ívszerűen összefüggő).
- $\mathbb{R}^p$-ben a teljes téren és az üres halmazon kívül **nincs** olyan halmaz, amely egyszerre nyílt és zárt. (Egy ilyen $H$ és a komplementere ugyanis $\mathbb{R}^p$-t két diszjunkt, nemüres nyílt halmazra bontaná.)

### Tartomány

**Definíció.** **Tartomány**: nemüres, nyílt, összefüggő halmaz.

Nyílt halmazon az összefüggőség egyenértékű az ívszerű összefüggőséggel, sőt a töröttvonallal való összeköthetőséggel is — a tartomány tehát az a halmaz, amelyen belül bármely két pont között „végig lehet sétálni". Lásd [[concepts/analiii/ivszeru-osszefuggoseg]].

### Miért nem elég a szemlélet: a hegymászós feladat

Két hegymászó az $y = h(x)$ grafikonú hegyet mássza meg, ahol $h : [0,1]\to[0,1]$ folytonos, $h(0)=h(1)=0$. Az egyik a $(0,0)$, a másik az $(1,0)$ pontból indul, és úgy szeretnének találkozni, hogy közben mindig azonos magasságban legyenek. Formálisan: léteznek-e olyan $a, b : [0,1]\to[0,1]$ folytonos függvények, amelyekre $a(0)=0$, $b(0)=1$, $a(1)=b(1)$, és minden $t$-re $h(a(t)) = h(b(t))$?

**A hibás bizonyítás.** Ábrázoljuk a mozgást a $[0,1]\times[0,1]$ négyzetben: az $(a,b)$ pont legyen *zöld*, ha $h(a)=h(b)$, *piros*, ha $h(a)>h(b)$, *kék*, ha $h(a)<h(b)$. A kezdőállapot a $(0,1)$ sarok, a cél az $a=b$ átló; ezek zöldek. „Nyilvánvaló", hogy a négyzet bal oldalát a felső oldallal összekötő minden folytonos görbe átmegy zöld ponton, tehát a zöld halmaz elválasztja őket, tehát a zöld halmazban össze lehet kötni a $(0,1)$ sarkot az átlóval.

**Az ellenpélda.** Balról indul Lady Callia, jobbról Lord Stettin. Valahányszor Callia eléri a $0{,}5$ magasságot, Stettinnek át kell sétálnia egy piros szakasz másik végére, hogy Callia tovább haladhasson. Mire Callia eléri a célpontot, Stettinnek végtelen sokszor kell oda-vissza loholnia a szakaszon — akkor viszont nem tud egyetlen pontba konvergálni.

**Hol a hiba?** A bal felső sarokból elindul ugyan egy cikcakkos töröttvonal, de ez nem konvergál egyetlen pontba; és a bal oldalhoz csatlakozó kék halmaz határa nem folytonos görbe, tehát nem lehet rajta „végigsétálni". A tanulság: az összefüggőség és az ívszerű összefüggőség két különböző dolog, és a szemlélet a kettőt összekeveri.

Ugyanez a jelenség a bevezető törpe-példa magja is: az irigy törpe 10, illetve 11 órakor nem egyetlen ponthoz konvergál, hanem egy kiterjedt ponthalmazhoz torlódik — „szétkenődik a térben".

## Kapocs

- [[concepts/analiii/ivszeru-osszefuggoseg]] — az erősebb fogalom; nyílt halmazokon a kettő egybeesik
- [[concepts/analiii/nyilt-es-zart-halmazok]] — az egyszerre nyílt és zárt halmazokról szóló következmény
- [[concepts/analiii/halmaz-pontjai-metrikus-terben]] — a határ fogalma, amit a hibás bizonyítás félreért
- [[concepts/analiii/konvergencia-metrikus-terben]] — a torlódás és a konvergencia különbsége az ellenpéldában
- [[concepts/analiii/bolzano-tetel-osszefuggo-halmazon]] — összefüggő halmaz folytonos képe összefüggő; a gyöktétel
