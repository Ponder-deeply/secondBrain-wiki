---
tags: [concept]
sources: [Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf]
derivation: source
kind: definition
element: water
updated: 2026-10-21
---

# Euklidészi gyűrű

Egységelemes integritási tartomány, amelyben egy $\varphi : R^* \to \mathbb{N}$ „fokfüggvény” mellett maradékos osztás végezhető; ilyen a $\mathbb{Z}$ és a Gauss-egészek gyűrűje.

## Tartalom

### Definíció

Az $R$ egységelemes integritási tartományt **euklidészi gyűrűnek** nevezzük, ha létezik olyan $\varphi : R^* \to \mathbb{N}$ függvény, amelyre

- **I.** minden $\alpha, \beta \in R$, $\beta \ne 0$ esetén létezik olyan $\gamma, \delta \in R$, hogy $\alpha = \beta\gamma + \delta$, ahol $\delta = 0$ vagy ($\delta \ne 0$ és $\varphi(\delta) < \varphi(\beta)$);
- **II.** $\varphi(\alpha\beta) \ge \max(\varphi(\alpha), \varphi(\beta))$ minden $\alpha, \beta \in R^*$ esetén.

### Példa: a Gauss-egészek

$G = \{a + bi \mid a, b \in \mathbb{Z}\}$, $\varphi(a + bi) = (a + bi)(a - bi) = |a + bi|^2 = a^2 + b^2$.

**II. tulajdonság.** $\varphi(\alpha\beta) = |\alpha\beta|^2 = |\alpha|^2 |\beta|^2 \ge \max(|\alpha|^2, |\beta|^2)$ minden $\alpha, \beta \in G^*$-ra (mert $|\cdot|^2 \ge 1$ a nemnulla Gauss-egészekre).

**I. tulajdonság.** Legyen $\alpha, \beta \in G$, $\beta \ne 0$.

1. eset: $\alpha / \beta \in G$. Ekkor $\gamma = \alpha/\beta$, $\delta = 0$.
2. eset: $\alpha/\beta \notin G$. Válasszuk $\gamma$-nak a számsíkon az $\alpha/\beta$-hoz legközelebbi (egyik) rácspontot. Ekkor a távolságuk legfeljebb $\frac{\sqrt{2}}{2}$, így $\left|\frac{\alpha}{\beta} - \gamma\right|^2 < 1$. $|\beta|^2$-tel szorozva $|\alpha - \beta\gamma|^2 < |\beta|^2$, tehát $\delta = \alpha - \beta\gamma$ jó: $\varphi(\delta) < \varphi(\beta)$.

### Lemma (egységelem és egység integritási tartományban)

$R$ integritási tartományban **akkor és csak akkor** létezik egységelem, ha létezik egység. Az $R$ egységelemes integritási tartományban $a \in R$ akkor és csak akkor egység, ha $a \mid e$.

*Bizonyítás.* Ha van $e$ egységelem, akkor $er = r$ minden $r$-re (és $e$ egység). Ha van $a$ egység, akkor $a \mid a$, így létezik $e \in R$: $ae = a$. Ez az $e$ egységelem, mert $a \mid r$-ből $as = r$, és
$e r = e a s = (ea) s = (ae) s = a s = r$. A többi triviális. $\square$

### Állítás (8.2.30): egységek az euklidészi gyűrűben

**Állítás.** Euklidészi gyűrűben pontosan azok az elemek az egységek, amelyekre $\varphi$ minimális értéket vesz fel. Az $a, b$ nem nulla elemekre $a \mid b$ esetén $\varphi(a) \le \varphi(b)$, és egyenlőség pontosan akkor teljesül, ha $a$ és $b$ asszociáltak.

*Bizonyítás.* Legyen $E = \{ r \in R^* \mid \varphi(r) \text{ minimális} \}$.

1. **$E$ elemei egységek.** Legyen $a \in E$, $b \in R$ tetszőleges; osszuk el $b$-t $a$-val maradékosan: $b = ac + d$, ahol $d = 0$ vagy $\varphi(d) < \varphi(a)$. A második eset $\varphi(a)$ minimalitása miatt nem fordulhat elő, így $d = 0$, $a \mid b$. Tehát $a$ minden elemnek osztója: egység.
2. **Minden egység $E$-ben van.** Legyen $a$ egység, $b \in E$ adott; $a \mid b$, $b = ac$, és $b \ne 0$ miatt $a, c \in R^*$. A II. tulajdonság szerint $\varphi(b) = \varphi(ac) \ge \max(\varphi(a), \varphi(c))$, így $\varphi(b) \ge \varphi(a)$; mivel $\varphi(b)$ minimális, $\varphi(a)$ is az.
3. **$a \mid b \Rightarrow \varphi(a) \le \varphi(b)$** a II. tulajdonságból, mert $b = at$.
4. **Egyenlőség esetén asszociáltak.** Tegyük fel $a \mid b$ és $\varphi(a) = \varphi(b)$. Az I. tulajdonság szerint $a = br + s$, ahol $s = 0$ vagy $\varphi(s) < \varphi(b) = \varphi(a)$ $(*)$. Mivel $b = at$ és $a = ae$, $s = a + b(-r) = a(e + t(-r))$, így $a \mid s$. Ha $s \ne 0$, akkor $\varphi(s) \ge \varphi(a)$ a 3. pont szerint, ami $(*)$ miatt nem fordulhat elő; tehát $s = 0$, $b \mid a$, azaz $a \sim b$. $\square$

## Kapocs

- [[concepts/dimatii/euklideszi-algoritmus]] — az algoritmus, amelyet a maradékos osztás tesz lehetővé
- [[concepts/dimatii/maradekos-osztas]] — $\mathbb{Z}$ maradékos osztása
- [[concepts/dimatii/polinomok-maradekos-osztasa]] — a másik fő példa (test fölötti polinomok)
- [[concepts/dimatii/egyseg-es-asszocialt]] — az egységek és az asszociáltság
- [[concepts/dimatii/integritasi-tartomany]] — a keret
- [[concepts/dimatii/gauss-gyuru]] — az egyértelmű faktorizáció és a $\mathbb{Z}[\sqrt{-5}]$ ellenpélda
- [[concepts/dimatii/foideal]] — az ideálok és az oszthatóság kapcsolata
