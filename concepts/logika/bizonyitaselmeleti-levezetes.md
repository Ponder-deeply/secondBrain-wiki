---
tags: [concept, logika/bizonyitaselmelet]
sources: ["Szintaktikus következmény.pdf"]
derivation: source
updated: 2026-09-08
---

# Bizonyításelméleti levezetés és szintaktikus következmény

A szintaktikus következményfogalom ($\vdash_0$) a helyesség fogalmát nem a szemantikán (minden interpretációban), hanem egy formulasorozat mechanikus felépíthetőségén keresztül ragadja meg — ez a bizonyításelméleti (szintaktikus) tárgyalás lényege.

## Tartalom

### A levezetés definíciója

Egy $G$ formula $F$-ből való **levezetése** egy $\varphi_1, \varphi_2, \dots, \varphi_k, \dots, \varphi_n$ formulasorozat, amelynek utolsó tagja $G$, és amelyben minden $\varphi_k$ tagra teljesül, hogy

- $\varphi_k \in F$ (premissza), vagy
- $\varphi_k$-t axiómasémából kaptuk (lásd [[concepts/logika/axiomasemak-iteletkalkulus]]), vagy
- $\varphi_k$-t a levezetési szabállyal kaptuk két korábbi taggal, $\varphi_k = mp(\varphi_s, \varphi_t)$, ahol $s, t < k$.

Az egyetlen levezetési szabály a **modus ponens** (leválasztási szabály): $\varphi_s = A$, $\varphi_t = A \supset B$ esetén $\varphi_k = B$.

### Szintaktikus következmény és bizonyítás

Egy $G$ formula **levezethető** az $F = \{F_1, F_2, \dots, F_n\}$ formulahalmazból — jelölésben $F \vdash_0 G$ —, ha létezik $G$-nek $F$-ből való levezetése. Ez a **szintaktikus következményfogalom**, a [[concepts/logika/kovetkeztetesforma]]-ban tárgyalt szemantikus következményfogalom ($\models_0$) párja: ugyanazt a kérdést válaszolja meg (helyes-e a következtetésforma), de tisztán a formulasorozat felépíthetőségén keresztül, interpretáció megkerülésével.

Ha $F$ üres — a levezetés csak axiómákra és modus ponensre épül —, akkor $A$-nak az üres feltételhalmazból való levezetését $A$ **bizonyításának** nevezzük, jelölésben $\vdash_0 A$; ekkor $A$ **bizonyítható**.

### Elsőrendű logika

A predikátumkalkulusban — az elsőrendű logika bizonyításelméleti felépítésében — a levezetés, a szintaktikus következményfogalom és a dedukciós tétel fogalma szó szerint ugyanígy működik, csak az axiómasémák bővülnek ki a kvantorokra vonatkozókkal: lásd [[concepts/logika/predikatumkalkulus-axiomasemak]].

### Konzisztencia

Egy $F = \{F_1, \dots, F_n\}$ formulahalmaz **ellentmondásos** (inkonzisztens), ha van olyan $G$, hogy $F \vdash_0 G$ és $F \vdash_0 \neg G$ egyaránt fennáll; egyébként **konzisztens**. A konzisztencia és a levezethetőség kapcsolatát, valamint a levezetés további tulajdonságait a [[concepts/logika/dedukcios-tetel]] tárgyalja.

## Kapocs

- [[concepts/logika/axiomasemak-iteletkalkulus]] — az axiómasémák, amelyekre a levezetés épül
- [[concepts/logika/dedukcios-tetel]] — a levezetés tulajdonságai és a dedukciós tétel
- [[concepts/logika/predikatumkalkulus-axiomasemak]] — a levezetésfogalom elsőrendű kiterjesztése
- [[concepts/logika/bizonyitaselmelet-helyesseg-teljesseg]] — a szintaktikus és szemantikus következmény ekvivalenciája
- [[concepts/logika/kovetkeztetesforma]] — a szemantikus következményfogalom, amelynek szintaktikus párja ez a levezetés
