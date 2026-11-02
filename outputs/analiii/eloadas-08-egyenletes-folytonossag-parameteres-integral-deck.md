`button-fc-review` | `button-fc-cram`

#flashcards/analiii/eloadas-08-egyenletes-folytonossag-parameteres-integral

## Definiálja az egyenletes folytonosság fogalmát $\mathbb{R}^n \to \mathbb{R}$ típusú függvények körében!
?
$f$ **egyenletesen folytonos**, ha minden $\varepsilon>0$-hoz van olyan $\delta>0$ (amely csak $\varepsilon$-tól függ, a ponttól nem), hogy minden $x,t \in D_f$, $\|x-t\|<\delta$ esetén $|f(x)-f(t)|<\varepsilon$.
---

## Mi a kapcsolat a folytonosság és az egyenletes folytonosság között?
?
Minden egyenletesen folytonos függvény folytonos. A megfordítás általában nem igaz — például $f(x)=1/x$ ($x>0$) folytonos, de nem egyenletesen folytonos: a $0$-hoz közeledve a jó $\delta$ kényszerűen nullához tart.
---

## Mondja ki Heine tételét $\mathbb{R}^n \to \mathbb{R}$ ($n \in \mathbb{N}, n \geq 1$) típusú függvények esetére!
?
Ha $f$ folytonos és $D_f$ kompakt, akkor $f$ egyenletesen folytonos. (A bizonyítás indirekt, kétszeri részsorozat-kiválasztással: ha nem volna egyenletesen folytonos, kapnánk $x_n,t_n\in D_f$ sorozatokat $\|x_n-t_n\|\to0$, de $|f(x_n)-f(t_n)|\geq\varepsilon$ tulajdonsággal; a kompaktság miatt közös limeszhez konvergáló részsorozatok ellentmondásra vezetnek.)
---

## Értelmezze a paraméteres integrál fogalmát!
?
Ha $f$ kétváltozós függvény, akkor az $F(t) = \int_{x=a}^{b} f(t,x)\,\mathrm{d}x$ alakú, $t$-től (a paramétertől) függő kifejezés a **paraméteres integrál** — az integrálás $x$ szerint történik, $t$ szabadon marad. Improprius változata: $F(t) = \int_{x=\alpha}^{\beta} f(t,x)\,\mathrm{d}x := \lim_{a\searrow\alpha,\,b\nearrow\beta}\int_a^b f(t,x)\,\mathrm{d}x$, aminek konvergenciáját (a folytonosság öröklődéséhez) egy $t$-től független **domináns függvénnyel** ($|f(t,x)|\leq g(x)$, $\int g<\infty$) biztosítjuk.
---

## Hogyan szól a paraméteres integrál differenciálhatóságára vonatkozó tétel?
?
Ha $f: I\times[a,b]\to\mathbb{R}$ folytonos és $\partial_t f(t,x)$ létezik és folytonos, akkor $F(t)=\int_{x=a}^b f(t,x)\,\mathrm{d}x$ differenciálható, és $F'(t) = \int_{x=a}^b \partial_t f(t,x)\,\mathrm{d}x$ (integráljel alatti deriválás). Improprius esetben ehhez a $\partial_t f$-nek is kell domináns függvény, nem elég $f$-nek.
---

## Hogyan szól a paraméteres integrál integrálására vonatkozó tétel?
?
Ha $f:[c,d]\times[a,b]\to\mathbb{R}$ folytonos és $F(t)=\int_{x=a}^b f(t,x)\,\mathrm{d}x$, akkor $\int_{t=c}^d F(t)\,\mathrm{d}t = \int_{x=a}^b\bigl(\int_{t=c}^d f(t,x)\,\mathrm{d}t\bigr)\mathrm{d}x$ — a $t$ és $x$ szerinti integrálás sorrendje felcserélhető. Improprius esetben ugyanez igaz, ha $F$ minden $t$-re konvergens improprius integrál és $f$-nek van domináns függvénye.
---
