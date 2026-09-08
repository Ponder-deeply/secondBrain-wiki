
# Analízis II — Határozott integrál kérdések

#flashcards/AnalII/R9


> Forrás: [[concepts/analii/hatarozott-integral-ertelmezese]], [[concepts/analii/integralhato-fuggvenyek]]
---


## 1. Milyen viszony van a felső és alsó közelítő összegek között?
?
Legyen $f \in K[a,b]$, és legyenek $\tau_1, \tau_2 \in \mathcal{F}[a,b]$ tetszőleges felosztások. Ekkor
$$s(f,\tau_1) \leq S(f,\tau_2).$$
Azaz **bármely alsó közelítő összeg legfeljebb akkora, mint bármely felső közelítő összeg** — még akkor is, ha a két összeg különböző felosztáshoz tartozik.
**Bizonyítás vázlata.** Legyen $\tau = \tau_1 \cup \tau_2$. Ekkor $\tau$ finomabb mindkét felosztásnál, ezért a finomítási tétel alapján:
$$s(f,\tau_1) \leq s(f,\tau) \leq S(f,\tau) \leq S(f,\tau_2). \qquad \blacksquare$$
---

## 2. Mi a Darboux-féle alsó integrál definíciója?
?
Legyen $f \in K[a,b]$. Az $f$ függvény **Darboux-féle alsó integrálja**:
$$I_*(f) := \sup_{\tau \in \mathcal{F}[a,b]} s(f,\tau).$$
Azaz az összes lehetséges felosztáshoz tartozó alsó közelítő összeg szuprémuma.
---

## 3. Mi a Darboux-féle felső integrál definíciója?
?
Legyen $f \in K[a,b]$. Az $f$ függvény **Darboux-féle felső integrálja**:
$$I^*(f) := \inf_{\tau \in \mathcal{F}[a,b]} S(f,\tau).$$
Azaz az összes lehetséges felosztáshoz tartozó felső közelítő összeg infimuma.
Az 1. pontban látott összefüggés következménye, hogy mindig $I_*(f) \leq I^*(f)$.
---

## 4. Mikor nevezünk egy függvényt (Riemann-)integrálhatónak?
?
Az $f \in K[a,b]$ függvény **Riemann-integrálható** $[a,b]$-n, ha a Darboux-féle alsó és felső integrál egyenlő:
$$I_*(f) = I^*(f).$$
Jelölés: $f \in R[a,b]$.
---

## 5. Hogyan értelmezzük egy függvény határozott (vagyis Riemann-) integrálját?
?
Ha $f \in R[a,b]$, azaz $I_*(f) = I^*(f)$, akkor ezt a közös értéket nevezzük $f$ **határozott integrálján** $[a,b]$-n:
$$\int_a^b f := \int_a^b f(x)\,dx := I_*(f) = I^*(f).$$
---

## 6. Adjon példát nem integrálható függvényre!
?
A **Dirichlet-függvény** nem integrálható $[0,1]$-en:
$$D(x) = \begin{cases} 1, & \text{ha } x \in \mathbb{Q}, \\ 0, & \text{ha } x \notin \mathbb{Q}. \end{cases}$$
**Miért?** Minden $[x_{i-1}, x_i]$ részintervallumon van racionális és irracionális pont egyaránt, ezért
$$m_i = 0, \quad M_i = 1 \qquad (i = 1, \ldots, n)$$
minden $\tau$ felosztáshoz. Tehát $s(D,\tau) = 0$ és $S(D,\tau) = b - a$ minden felosztásra, amiből
$$I_*(D) = 0 \neq 1 = I^*(D),$$
vagyis $D \notin R[0,1]$.
---

## 7. Mi az oszcillációs összeg definíciója?
?
Legyen $f \in K[a,b]$, $\tau \in \mathcal{F}[a,b]$. Az $f$ függvény $\tau$ felosztáshoz tartozó **oszcillációs összege**:
$$\Omega(f,\tau) := S(f,\tau) - s(f,\tau) = \sum_{i=1}^n (M_i - m_i)(x_i - x_{i-1}),$$
ahol $m_i = \inf_{[x_{i-1},x_i]} f$ és $M_i = \sup_{[x_{i-1},x_i]} f$.
Az oszcillációs összeg azt méri, mennyire „ingadozik" $f$ az egyes részintervallumokon: minél kisebb $\Omega(f,\tau)$, annál pontosabb a közelítés.
---

## 8. Hogyan szól a Riemann-integrálhatósággal kapcsolatos kritérium oszcillációs összegekkel megfogalmazva?
?
**Darboux-kritérium.** Legyen $f \in K[a,b]$. Ekkor
$$f \in R[a,b] \iff \forall \varepsilon > 0\ \exists \tau \in \mathcal{F}[a,b]: \Omega(f,\tau) < \varepsilon.$$
Azaz $f$ pontosan akkor Riemann-integrálható, ha az oszcillációs összeg tetszőlegesen kicsivé tehető alkalmas felosztás választásával.
**Bizonyítás vázlata.**
$(\Rightarrow)$ Ha $f \in R[a,b]$, akkor $I_*(f) = I^*(f) =: I$. Adott $\varepsilon > 0$-hoz léteznek $\tau_1, \tau_2$ felosztások, melyekre $I - s(f,\tau_1) < \varepsilon/2$ és $S(f,\tau_2) - I < \varepsilon/2$. Legyen $\tau = \tau_1 \cup \tau_2$. Ekkor a finomítási tétel alapján:
$$\Omega(f,\tau) = S(f,\tau) - s(f,\tau) \leq S(f,\tau_2) - s(f,\tau_1) < \varepsilon.$$
$(\Leftarrow)$ Ha $\forall \varepsilon > 0\ \exists \tau: \Omega(f,\tau) < \varepsilon$, akkor
$$0 \leq I^*(f) - I_*(f) \leq S(f,\tau) - s(f,\tau) = \Omega(f,\tau) < \varepsilon,$$
tehát $I^*(f) = I_*(f)$, azaz $f \in R[a,b]$. $\blacksquare$
