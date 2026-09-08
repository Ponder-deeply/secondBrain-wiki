#flashcards/bvszam/eldonthetetlenseg
## 1. Mit jelent, hogy egy $L$ nyelv eldönthetetlen?
?
Egy $L$ nyelv **eldönthetetlen**, ha $L \notin \mathrm{R}$: nem létezik olyan Turing-gép, amely minden bemeneten megáll és helyesen eldönti, hogy a szó $L$-ben van-e. Ha ráadásul $L \notin \mathrm{RE}$, akkor még felismerni sem lehet.
---

## 2. Definiálja a many-one visszavezetést ($L_1 \leq L_2$)!
?
$L_1 \subseteq \Sigma^*$ **visszavezethető** $L_2 \subseteq \Delta^*$-ra ($L_1 \leq L_2$), ha létezik olyan kiszámítható $f : \Sigma^* \to \Delta^*$ szófüggvény, amelyre minden $w$-re:
$$w \in L_1 \iff f(w) \in L_2.$$
---

## 3. Mik a visszavezetés következményei az eldönthetőség/felismerhetőség szempontjából?
?
Ha $L_1 \leq L_2$, akkor:
| Feltétel | Következmény |
|---|---|
| $L_2 \in \mathrm{RE}$ | $L_1 \in \mathrm{RE}$ |
| $L_2 \in \mathrm{R}$ | $L_1 \in \mathrm{R}$ |
| $L_1 \notin \mathrm{RE}$ | $L_2 \notin \mathrm{RE}$ |
| $L_1 \notin \mathrm{R}$ | $L_2 \notin \mathrm{R}$ |
Az utóbbi két sor mutatja, hogy ha egy ismerten (nem felismerhető /) eldönthetetlen problémát visszavezetünk $L_2$-re, akkor $L_2$ is (nem felismerhető /) eldönthetetlen.
---

## 4. Definiálja a megállási problémát! Melyik bonyolultsági osztályba esik?
?
$$L_h = \{\langle M, w \rangle \mid M \text{ megáll a } w \text{ bemeneten}\}$$
azon kódolt párok nyelve, amelyeken $M$ megáll (elfogadó vagy elutasító állapotban). Besorolás: $L_h \in \mathrm{RE} \setminus \mathrm{R}$ — felismerhető, de nem eldönthető.
---

## 5. Hogyan bizonyítjuk, hogy $L_h \notin \mathrm{R}$? (visszavezetéses bizonyítás)
?
Megmutatjuk, hogy $L_u \leq L_h$. Adott $\langle M, w \rangle$-hez konstruáljuk $M'$-t:
1. $M'$ futtatja $M$-et $w$-n.
2. Ha $M$ elfogadja $w$-t, $M'$ is elfogad.
3. Ha $M$ elutasítja $w$-t, $M'$ végtelen ciklusba kerül (soha nem áll meg).
Ekkor $\langle M, w \rangle \in L_u \iff \langle M', w \rangle \in L_h$. Mivel $L_u \notin \mathrm{R}$, $L_h \notin \mathrm{R}$.
---

## 6. Hogyan bizonyítjuk, hogy $L_h \in \mathrm{RE}$?
?
Megmutatjuk, hogy $L_h \leq L_u$. Adott $\langle M, w \rangle$-hez konstruáljuk $M'$-t úgy, hogy $M$ minden elutasító állapotba vezető átmenetét elfogadóra cseréljük. Ekkor $M$ megáll $w$-n $\iff$ $M'$ elfogadja $w$-t, vagyis $\langle M, w \rangle \in L_h \iff \langle M', w \rangle \in L_u$. Mivel $L_u \in \mathrm{RE}$, a 2.19. tétel alapján $L_h \in \mathrm{RE}$.
---

## 7. Miért nem zárt RE a komplementerre?
?
**Tétel:** Ha $L \in \mathrm{RE}$ és $\bar{L} \in \mathrm{RE}$, akkor $L \in \mathrm{R}$.
**Bizonyítás:** Legyen $M_1$ az $L$-t, $M_2$ a $\bar{L}$-t felismerő TG. Egy $M'$ gép felváltva szimulál egy-egy lépést mindkét gépen — valamelyik véges lépésen belül elfogad, tehát $M'$ mindig megáll és eldönti $L$-t.
**Következmény:** Ha $\bar{L} \in \mathrm{RE}$ lenne $L_u$-ra, akkor $L_u \in \mathrm{R}$ következne — ellentmondás, tehát $\overline{L_u} \notin \mathrm{RE}$.
---

## 8. Milyen besorolásúak az alábbi Turing-gépes problémák?
?
| Probléma | Jelölés | Besorolás |
|---|---|---|
| Univerzális nyelv | $L_u = \{\langle M,w\rangle \mid w \in L(M)\}$ | $\mathrm{RE} \setminus \mathrm{R}$ |
| Megállási probléma | $L_h = \{\langle M,w\rangle \mid M \text{ megáll } w\text{-n}\}$ | $\mathrm{RE} \setminus \mathrm{R}$ |
| Nemüres nyelv | $L_{\neg\emptyset} = \{\langle M\rangle \mid L(M) \neq \emptyset\}$ | $\mathrm{RE} \setminus \mathrm{R}$ |
| Üres nyelv | $L_\emptyset = \{\langle M\rangle \mid L(M) = \emptyset\}$ | $\notin \mathrm{RE}$ |
| Ekvivalencia | $L_{EQ} = \{\langle M_1,M_2\rangle \mid L(M_1) = L(M_2)\}$ | $\notin \mathrm{RE}$ |
---

## 9. Hogyan bizonyítjuk, hogy $L_{\neg\emptyset} \notin \mathrm{R}$ (visszavezetéssel)?
?
Megmutatjuk, hogy $L_u \leq L_{\neg\emptyset}$. Adott $\langle M, w \rangle$-hez konstruálunk egy $M'$ gépet, amely tetszőleges $u$ bemeneten:
- Ha $u \neq w$: elutasít.
- Ha $u = w$: szimulálja $M$-et $w$-n.
Ekkor $L(M') \neq \emptyset \iff w \in L(M)$, tehát $\langle M, w \rangle \in L_u \iff \langle M' \rangle \in L_{\neg\emptyset}$. Mivel $L_u \notin \mathrm{R}$, következik $L_{\neg\emptyset} \notin \mathrm{R}$.
---

## 10. Miért $L_\emptyset \notin \mathrm{RE}$ és $L_{EQ} \notin \mathrm{RE}$?
?
$L_\emptyset = \overline{L_{\neg\emptyset}}$. Mivel $L_{\neg\emptyset} \in \mathrm{RE} \setminus \mathrm{R}$ és RE nem zárt komplementerre, $L_\emptyset \notin \mathrm{RE}$.
$L_{EQ} \notin \mathrm{RE}$: az $L_\emptyset$ az $L_{EQ}$ speciális esete — rögzítsük $M_2$-t egy semmit el nem fogadó gépre. Ha $L_{EQ} \in \mathrm{RE}$ lenne, akkor $L_\emptyset \in \mathrm{RE}$ is következne, ami ellentmondás.
---

## 11. Fogalmazza meg Rice tételét!
?
**Rice tétele (2.25. tétel):** Ha $\mathcal{P} \subseteq \mathrm{RE}$ a rekurzívan felsorolható nyelvek egy **nemtriviális** tulajdonsága, akkor
$$L_\mathcal{P} = \{\langle M \rangle \mid L(M) \in \mathcal{P}\} \notin \mathrm{R}.$$
Azaz: egyetlen nemtriviális, a felismert nyelvről szóló kérdést sem lehet algoritmikusan eldönteni egy Turing-gépről.
---

## 12. Mit jelent triviális és nemtriviális tulajdonság Rice tételének kontextusában?
?
**Tulajdonság:** $\mathcal{P} \subseteq \mathrm{RE}$, a rekurzívan felsorolható nyelvek egy részhalmaza.
**Triviális:** $\mathcal{P} = \emptyset$ (semmire sem teljesül) vagy $\mathcal{P} = \mathrm{RE}$ (mindenre teljesül) — ezekre a kérdés eldöntése triviálisan megoldható.
**Nemtriviális:** $\mathcal{P} \neq \emptyset$ és $\mathcal{P} \neq \mathrm{RE}$, azaz létezik olyan nyelv, amelyik rendelkezik a tulajdonsággal, és olyan is, amelyik nem.
---

## 13. Vázoljon bizonyítást Rice tételére! (az $\emptyset \notin \mathcal{P}$ eset)
?
Mivel $\mathcal{P} \neq \emptyset$, legyen $L \in \mathcal{P}$ és $M_L$ az azt felismerő TG. Megmutatjuk, hogy $L_u \leq L_\mathcal{P}$.
Adott $\langle M, w \rangle$-hez konstruálunk egy $M'$ TG-t, amely $x$ bemeneten:
- Szimulálja $M$-et $w$-n.
- Ha $M$ nem fogadja el $w$-t: $L(M') = \emptyset \notin \mathcal{P}$.
- Ha $M$ elfogadja $w$-t: szimulálja $M_L$-t $x$-en, azaz $L(M') = L \in \mathcal{P}$.
Tehát $\langle M, w \rangle \in L_u \iff \langle M' \rangle \in L_\mathcal{P}$, vagyis $L_u \leq L_\mathcal{P}$, és így $L_\mathcal{P} \notin \mathrm{R}$.
---

## 14. Soroljon fel négy eldönthetetlen kérdést Rice tétele alapján!
?
Rice tétele alapján eldönthetetlen, hogy egy adott $M$ Turing-gép:
1. az üres nyelvet ismeri-e fel ($\mathcal{P} = \{\emptyset\}$),
2. véges nyelvet ismer-e fel ($\mathcal{P} = \{L \mid L \text{ véges}\}$),
3. környezetfüggetlen nyelvet ismer-e fel ($\mathcal{P} = \{L \mid L \in \mathcal{L}_2\}$),
4. elfogadja-e az üres szót ($\mathcal{P} = \{L \in \mathrm{RE} \mid \varepsilon \in L\}$).
---

## 15. Definiálja a Post megfelelkezési problémát (PMP)!
?
Legyen $D = \left\{\left[\tfrac{u_1}{v_1}\right], \ldots, \left[\tfrac{u_n}{v_n}\right]\right\}$ egy dominóhalmaz, ahol $u_i, v_i \in \Sigma^+$. A $D$ egy **megoldása** olyan $1 \leq i_1, \ldots, i_m \leq n$ indexsorozat ($m \geq 1$), amelyre:
$$u_{i_1} \cdots u_{i_m} = v_{i_1} \cdots v_{i_m}.$$
A PMP formális nyelve:
$$\mathrm{PMP} = \{\langle D \rangle \mid D\text{-nek van megoldása}\}.$$
---

## 16. Mi a módosított PMP (MPMP), és hogyan vezethető vissza MPMP PMP-re?
?
Az **MPMP** ugyanaz, mint a PMP, de a megoldásnak az **első dominóval** $\left[\tfrac{u_1}{v_1}\right]$ kell kezdődnie.
**MPMP $\leq$ PMP:** Adott $D$-hez konstruáljuk $D'$-t két új szimbólummal ($*, \#$):
$$D' = \left\{ \left[\tfrac{*u_1}{*v_1*}\right], \left[\tfrac{*u_1}{v_1*}\right], \left[\tfrac{*u_2}{v_2*}\right], \ldots, \left[\tfrac{*u_n}{v_n*}\right], \left[\tfrac{*\#}{\#}\right] \right\}.$$
A $*$ jelek kikényszerítik, hogy $D'$ megoldása a $\left[\tfrac{*u_1}{*v_1*}\right]$ dominóval kezdődjön — ez megfelel MPMP egy megoldásának.
---

## 17. Hogyan bizonyítjuk, hogy $\mathrm{PMP} \notin \mathrm{R}$? (a visszavezetési lánc)
?
A visszavezetési lánc: $L_u \leq \mathrm{MPMP} \leq \mathrm{PMP}$.
**$L_u \leq \mathrm{MPMP}$:** Adott $\langle M, w \rangle$-hez olyan dominókészletet konstruálunk, amelynek pontosan akkor van megoldása, ha $M$ elfogadja $w$-t. A dominósorozat felső/alsó szava az $M$ egymást követő, $\#$-cal elválasztott konfigurációit kódolja. A készlet tartalmaz:
1. Kezdő dominót (az $M$ kezdőkonfigurációjával),
2. Átmenet-dominókat (minden $\delta$-átmenethez),
3. Másoló dominókat (az $a \to a$ és szalagvég-kezelő dominók),
4. Záró dominókat (amelyek $q_i$ körüli szimbólumokat eltüntetik).
Mivel $L_u \notin \mathrm{R}$, a 2.19. tétel alapján $\mathrm{PMP} \notin \mathrm{R}$.
---

## 18. Fogalmazza meg a 2.32. tételt az elsőrendű logika érvényességéről!
?
**2.32. tétel:**
$$\textsc{ValidityPred} = \{\langle \varphi \rangle \mid \varphi \text{ érvényes elsőrendű logikai formula}\} \notin \mathrm{R}.$$
**Bizonyítás vázlata:** $\mathrm{PMP} \leq \textsc{ValidityPred}$. Adott $D$ dominókészlethez konstruálunk egy $\varphi_D = (\varphi_1 \wedge \varphi_2) \to \varphi_3$ formulát:
- $\varphi_1$: az egyes dominókat $p(f_{u_i}(c), f_{v_i}(c))$ alakban kódolja,
- $\varphi_2$: dominó hozzáfűzését fejezi ki universálisan kvantifikálva,
- $\varphi_3 = \exists z\, p(z, z)$: a felső és alsó szó megegyezik.
$\varphi_D$ érvényes $\iff$ $D$-nek van megoldása, tehát $\textsc{ValidityPred} \notin \mathrm{R}$.
---

## 19. Melyik elsőrendű logikai kérdések eldönthetetlenek, és miért?
?
Eldönthetetlen (mind $\notin \mathrm{R}$):
1. Érvényes-e $\varphi$? ($\textsc{ValidityPred} \notin \mathrm{R}$, 2.32. tétel)
2. Kielégíthetetlen-e $\varphi$?
3. Kielégíthető-e $\varphi$?
4. Teljesül-e $F \models \varphi$?
A kielégíthetetlenség és az érvényesség egymással duálisak (egy formula érvényes $\iff$ negáltja kielégíthetetlen), ezért mindkettő $\notin \mathrm{R}$. A kielégíthetőség ezek komplementere.
---

## 20. Melyik elsőrendű logikai problémák esnek RE-be, és melyek nem?
?
- **Kielégíthetetlenség** (és érvényesség) $\in \mathrm{RE}$: az elsőrendű logika rezolúciós algoritmusa pontosan a kielégíthetetlen formulákon áll meg $igen$ válasszal — tehát ez **felismerhető**.
- **Kielégíthetőség** $\notin \mathrm{RE}$: a kielégíthetőség és kielégíthetetlenség egymás komplementerei. Mivel a kielégíthetetlenség RE-beli és $\notin \mathrm{R}$, RE nem zárt komplementerre, tehát a kielégíthetőség nem lehet RE-beli.
---

## 21. Miért zárt $\mathrm{R}$ a komplementerre, de $\mathrm{RE}$ nem?
?
**R zárt komplementerre:** Ha $L \in \mathrm{R}$ és $M$ eldönti $L$-t, akkor az elfogadó és elutasító állapotokat felcserélve kapott $M'$ gép eldönti $\bar{L}$-t ($M'$ szintén minden bemeneten megáll).
**RE nem zárt komplementerre:** Ha $L \in \mathrm{RE}$ és $\bar{L} \in \mathrm{RE}$, akkor $L \in \mathrm{R}$ (a párhuzamos szimulációs érv alapján). Mivel $L_u \in \mathrm{RE} \setminus \mathrm{R}$, ha $\overline{L_u} \in \mathrm{RE}$ lenne, akkor $L_u \in \mathrm{R}$ következne — ellentmondás. Tehát $\overline{L_u} \notin \mathrm{RE}$, és RE nem zárt komplementerre.
---

## 22. Mit jelent a polinom idejű visszavezetés, és mire használják?
?
A **polinom idejű visszavezetés** ($L_1 \leq_p L_2$) olyan many-one visszavezetés, ahol az $f$ visszavezető függvény polinom időben kiszámítható. Alkalmazás: az NP-teljesség alapfogalma. Ha $L_1 \leq_p L_2$ és $L_1$ NP-nehéz (pl. SAT), akkor $L_2$ is NP-nehéz.
---

