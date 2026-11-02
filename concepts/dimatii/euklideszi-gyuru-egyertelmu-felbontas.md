---
tags: [concept]
sources: [Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf]
derivation: source
kind: theorem
element: water
updated: 2026-10-21
---

# Prímfelbontás euklideszi gyűrűben

Euklideszi gyűrűben a felbonthatatlan és a prím elem egybeesik, minden nem nulla, nem egység elem sorrendtől és asszociáltaktól eltekintve egyértelműen áll elő prímek szorzataként, és minden ideál főideál.

## Tartalom

Jelölés: $R$ euklideszi gyűrű $\varphi$ euklideszi normával (lásd [[concepts/dimatii/euklideszi-gyuru]]), $R^*$ a nem nulla elemek halmaza, $U(R)$ az egységek csoportja. A bizonyítások az előadásdiák 8.2.30 tételére támaszkodnak: ha $b \mid f$ és $b$, $f$ nem asszociáltak, akkor $\varphi(b) < \varphi(f)$.

### Bővített euklideszi algoritmus $R$-ben (8.2.32)

Az eljárás az $a, b \in R$ elemekhez egy $d$ legnagyobb közös osztót és olyan $x, y \in R$ elemeket ad, hogy $d = ax + by$; végig $ax_n + by_n = r_n$. Ugyanaz, mint $\mathbb{Z}$-ben ([[concepts/dimatii/bovitett-euklideszi-algoritmus]]), de $x_0 = e$ (az egységelem), $y_0 = 0$, $r_0 = a$, $x_1 = 0$, $y_1 = e$, $r_1 = b$; a ciklusban $r_n = q_{n+1}r_{n+1} + r_{n+2}$ ahol $r_{n+2} = 0$ vagy $\varphi(r_{n+2}) < \varphi(r_{n+1})$, és $x_{n+2} = x_n - q_{n+1}x_{n+1}$, $y_{n+2} = y_n - q_{n+1}y_{n+1}$. Akkor áll meg, ha $r_{n+1} = 0$: $d = r_n$.

### Felbonthatatlan = prím (8.2.33)

**Tétel.** Euklideszi gyűrű egy eleme pontosan akkor felbonthatatlan, ha prím.

*Bizonyítás.* A prím $\Rightarrow$ felbonthatatlan irány minden integritási tartományban igaz ([[concepts/dimatii/felbonthatatlan-es-prim]]). Fordítva: legyen $p$ irreducibilis és $p \mid ab$. Ha $p \mid a$, kész. Ha $p \nmid a$, akkor $(p,a) = e$ egység (mert $p$ osztói csak az egységek és az asszociáltjai), így a bővített euklideszi algoritmus szerint $e = px + ay$. Ebből $b = b\,e\,e^{-1} = pbxe^{-1} + abye^{-1}$, és mindkét tag osztható $p$-vel, tehát $p \mid b$. $\square$

### Egyértelmű prímfelbontás (8.2.34)

**Tétel.** Euklideszi gyűrűben minden nem nulla, nem egység elem sorrendtől és asszociáltságtól eltekintve egyértelműen felírható prímelemek szorzataként.

*Bizonyítás.*

1. **Lemma: van felbonthatatlan osztó.** Legyen $a \in R^* \setminus U(R)$ és $D = \{r \in R^* \setminus U(R) : r \mid a \ \text{és ha}\ s \in R^* \setminus U(R),\ s \mid a,\ \text{akkor}\ \varphi(r) \le \varphi(s)\}$, vagyis $a$ azon nem nulla, nem egység osztói, amelyekre $\varphi$ minimális. $D \ne \emptyset$; legyen $f \in D$. Indirekt, ha $f$ nem felbonthatatlan, akkor $f = bc$, $b, c \notin U(R)$, így $b \mid a$, és $b$, $f$ nem asszociáltak, tehát 8.2.30 miatt $\varphi(b) < \varphi(f)$ — ellentmondás, mert $b$ kerülne $D$-be $f$ helyett.
2. **Létezés** $\varphi(a)$ szerinti teljes indukcióval. Ha $\varphi(a)$ minimális $R^* \setminus U(R)$-ben, akkor 8.2.30 miatt $a$ felbonthatatlan. Általában legyen $\varphi(a) = n$ és tegyük fel, hogy $n$-nél kisebb $\varphi$-értékű elemekre igaz az állítás. Az 1. lemma szerint van felbonthatatlan $f \mid a$, $a = fh$. Itt $\varphi(h) \ne \varphi(a)$ (különben $h \mid a$ miatt $a \sim h$ lenne, de $f$ nem egység), így $\varphi(h) < \varphi(a)$. *1. eset:* $h$ egység $\Rightarrow$ $a$ felbonthatatlan. *2. eset:* $h$ nem egység $\Rightarrow$ az indukciós feltevés szerint $h = f_1 f_2 \cdots f_r$, tehát $a = f f_1 f_2 \cdots f_r$. A felbonthatatlanok a 8.2.33 tétel miatt prímek.
3. **Unicitás.** Indirekt: legyen $a$ olyan elem, amelynek két lényegesen különböző felbontása van, és $\varphi(a)$ minimális. $a = p_1 \cdots p_k = q_1 \cdots q_r$. Ekkor $p_1 \mid q_1 \cdots q_r$, így prím volta miatt $p_1 \mid q_i$ valamelyik $i$-re, és mivel mindkettő irreducibilis, asszociáltak. Egyszerűsítve olyan $a'$ elemet kapunk, amelynek két különböző felbontása van, de $\varphi(a') < \varphi(a)$ — ellentmondás. $\square$

### Minden ideál főideál (8.2.35)

**Tétel.** Euklideszi gyűrűben minden ideál főideál (lásd [[concepts/dimatii/foideal]]).

*Bizonyítás.* Ha $I = \{0\}$, akkor $I = \langle 0 \rangle$. Különben legyen $S = \{\varphi(x) : x \in I,\ x \ne 0\}$, legkisebb eleme $\varphi(a)$, $a \in I$, $a \ne 0$. Egy $b \in I$ elemet maradékosan osztva $a$-val: $b = aq + r$, ahol $r = 0$ vagy $\varphi(r) < \varphi(a)$. Mivel $I$ ideál, $r = b - aq \in I$, és $\varphi(a)$ minimalitása miatt $r = 0$. Tehát $b = aq$, azaz $I = \langle a \rangle$. $\square$

**A megfordítás nem igaz.** Az $R_{\sqrt{-19}} = \{a + b\cdot\frac{1+\sqrt{-19}}{2} \mid a, b \in \mathbb{Z}\}$ gyűrű főideálgyűrű, de nem euklideszi (az előadásdiák bizonyítás nélkül közli).

### Euklideszi gyűrű: irreducibilitás és maximális ideál (lemma)

Euklideszi gyűrűben $a \in R^* \setminus U(R)$ esetén $\langle a \rangle$ pontosan akkor maximális valódi ideál, ha $a$ felbonthatatlan; lásd [[concepts/dimatii/maximalis-es-primideal]].

## Kapocs

- [[concepts/dimatii/euklideszi-gyuru]] — a keret és az $\varphi$ norma
- [[concepts/dimatii/felbonthatatlan-es-prim]] — a két fogalom $\mathbb{Z}$-ben és integritási tartományban
- [[concepts/dimatii/bovitett-euklideszi-algoritmus]] — az algoritmus $\mathbb{Z}$-beli alakja
- [[concepts/dimatii/foideal]] — főideál és főideálgyűrű
- [[concepts/dimatii/gauss-gyuru]] — az egyértelmű faktorizáció általános fogalma
- [[concepts/dimatii/szamelmelet-alaptetele]] — a $\mathbb{Z}$-beli speciális eset
- [[concepts/dimatii/maximalis-es-primideal]] — irreducibilitás és maximális ideál
