---
tags: [concept]
sources: [gyakorlat.pdf]
derivation: inferred
kind: procedure
element: fire
updated: 2026-10-21
---

# Görbe görbülete, Frenet-elemek és torzió

Egy paraméteres görbe görbülete azt méri, milyen gyorsan fordul el az érintő; a görbe mentén a kísérő triéder (érintő, főnormális, binormális) és a torzió írja le az alakját térben. A lap képletei a gyakorlati feladatsor (Differenciálgeometria, 8–22.) alapján, számolási eszköztárként állnak itt; a bizonyításokat a gyakorlat kéri, itt nincsenek levezetve.

## Tartalom

### Képletek

Legyen $\varphi:I\to\mathbb{R}^3$ (vagy $\mathbb{R}^2$) háromszor folytonosan deriválható, $\varphi'\ne0$ (lásd [[concepts/analiii/gorbe-erintoje]]).

- **Görbület:** $\displaystyle\kappa(t)=\frac{|\varphi'(t)\times\varphi''(t)|}{|\varphi'(t)|^3}$. Síkgörbére $\varphi=(\varphi_1,\varphi_2)$ ezt a $z$ komponenssel számoljuk: $\kappa=\frac{|\varphi_1'\varphi_2''-\varphi_2'\varphi_1''|}{|\varphi'|^3}$.
- **Gráf** $y=f(x)$: $\displaystyle\kappa(x)=\frac{|f''(x)|}{\left(1+f'(x)^2\right)^{3/2}}$ (a $\varphi(x)=(x,f(x))$ paraméterezés speciális esete).
- **Egységérintő** $T=\frac{\varphi'}{|\varphi'|}$, **főnormális** $N=\frac{T'}{|T'|}$, **binormális** $B=T\times N$. Az $(T,N,B)$ jobbrendszer a Frenet-triéder.
- **Simulókör:** sugara $\frac1\kappa$, középpontja $\varphi(t_0)+\frac1\kappa N$; a simulósík a $T$ és $N$ által kifeszített, a ponton átmenő sík (normálvektora $B$).
- **Gyorsulás felbontása:** $a=\varphi''=a_T\,T+a_N\,N$, ahol $a_T=\frac{\varphi'\cdot\varphi''}{|\varphi'|}$ és $a_N=\kappa|\varphi'|^2=\frac{|\varphi'\times\varphi''|}{|\varphi'|}$. Egyenletes körmozgásnál (sugár $R$, sebesség $v$) a centripetális gyorsulás $v^2/R$.
- **Torzió:** $\displaystyle\tau=\frac{(\varphi'\times\varphi'')\cdot\varphi'''}{|\varphi'\times\varphi''|^2}$; síkgörbére $\tau=0$.

### Kidolgozott feladatok

- **Csavarvonal** $\varphi(t)=(2\sin t,2\cos t,4t)$: $\varphi'=(2\cos t,-2\sin t,4)$, $\varphi''=(-2\sin t,-2\cos t,0)$, $\varphi'\times\varphi''=(8\cos t,-8\sin t,-4)$, $|\cdot|=4\sqrt5$, $|\varphi'|=2\sqrt5$, így $\kappa=\frac{4\sqrt5}{40\sqrt5}=\frac1{10}$ (állandó).
- **Általános csavarvonal** $(a\cos t,a\sin t,bt)$: $\kappa=\frac a{a^2+b^2}$, $\tau=\frac b{a^2+b^2}$ (a $\varphi'\times\varphi''=(ab\sin t,-ab\cos t,a^2)$ és $\varphi'''\cdot(\varphi'\times\varphi'')=a^2b$ alapján).
- **Parabola** $y=ax^2+bx+c$: $\kappa=\frac{2|a|}{(1+(2ax+b)^2)^{3/2}}$, ami $x\to\infty$-nél $0$-hoz tart. Hasonlóan: $y=e^{2x}$, $y=x^3$, $y=\sqrt x$ görbülete is $0$-hoz tart a végtelenben.
- **Konkrét pontok:** $y=\sin x$ a $\frac\pi2$-ben $\kappa=1$; $y=x^3-1$ az $x=1$-ben $\kappa=\frac{6}{10^{3/2}}$.
- **Szélsőérték:** az $(2\cos t,3\sin t)$ ellipszisre $\kappa=\frac{6}{(4\sin^2t+9\cos^2t)^{3/2}}$; a maximum $\frac34$ a $(0,\pm3)$ pontokban (a hosszú tengely végpontjai), a minimum $\frac29$ a $(\pm2,0)$ pontokban. Az $y=4x^2-3$ görbülete a csúcsban maximális ($8$), $y=\sin x$-é a $\frac\pi2+k\pi$ pontokban ($1$), az inflexiós pontokban $0$.
- **Centripetális gyorsulás:** $r(t)=(6\cos4t,6\sin4t)$ sebessége $24$, sugara $6$, így $a=\frac{24^2}6=96$.
- **Egységérintő és -normális:** $r(t)=(t,t^2)$ a $t=0$-ban $T=(1,0)$, $N=(0,1)$.

### Gyakorló feladatok a forrásban

Polárkoordinátás görbék görbülete ($r=\sin3\theta$, $3+2\cos3\theta$, $3e^{2\theta}$), simulókör egyenlete, binormális és simulósík adott pontokban, torzió megadott paraméterértéknél, a gyorsulás érintő- és normálkomponense (gyakorlat.pdf, 53–54. oldal, 12–22. feladat).

## Kapocs

- [[concepts/analiii/parameteres-gorbe]] — a görbe paraméteres megadása, amelyből a képletek kiindulnak
- [[concepts/analiii/gorbe-erintoje]] — az érintő, amelyből a Frenet-triéder kezdődik
- [[concepts/analiii/sikgorbe-ivhossza]] — az ívhossz-paraméterezés, ahol $\kappa=|\varphi''(s)|$
- [[concepts/analiii/sikgorbe-megadasi-modok]] — a síkgörbe explicit, implicit és polár megadása
