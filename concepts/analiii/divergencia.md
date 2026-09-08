---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Divergencia (forrássűrűség)

Vektormező forrássűrűsége: az a skalármező, amely megmondja, egy pont körül egységnyi térfogatból mennyi „anyag" fakad fel időegység alatt. A Gauss–Osztrogradszkij tétel integrandusa.

## Tartalom

### Szemléletes bevezetés: a talajvíz forráserőssége

Kertünk, $K$, talajvízzel elárasztott $G$ területen fekszik, a vízszint állandó. Bármely pontban a talajvíz feltörhet vagy elszivároghat, de a feltörő víz a $\partial K$ kerítésen keresztül kiáramlik. A víz sebességét az $f : G \to \mathbb{R}^2$ vektormező adja meg.

A kertből a kerítésen át másodpercenként kifolyó vízmennyiség a kert **forráserőssége**. Egy $\mathrm{d}s$ hosszú kerítésdarabon, amelynek kifelé mutató normálvektora $\mathbf{n}$, másodpercenként $\langle f, \mathbf{n}\,\mathrm{d}s\rangle$ víz folyik ki, tehát a forráserősség

$$\int_{\partial K} \langle f, \mathbf{n}\,\mathrm{d}s\rangle .$$

Most osszuk fel a kertet kis, $2r$ oldalú négyzetekre, és nézzük az $(a,b)$ körüli $[a-r,a+r]\times[b-r,b+r]$ négyzetet, oldalanként az oldalfelező pontbeli értékkel számolva. A jobb oldalon $f_1(a+r,b)\cdot 2r$ folyik ki, a bal oldalon $-f_1(a-r,b)\cdot 2r$ (ott a negatív irány mutat kifelé), fent $f_2(a,b+r)\cdot 2r$, lent $-f_2(a,b-r)\cdot 2r$. Összeadva:

$$\left( \frac{f_1(a+r,b)-f_1(a-r,b)}{2r} + \frac{f_2(a,b+r)-f_2(a,b-r)}{2r} \right)\cdot (2r)^2 \approx \bigl( D_1f_1(a,b) + D_2f_2(a,b) \bigr)\cdot \text{terület}.$$

Az $(a,b)$ pont körül tehát négyzetméterenként és másodpercenként $D_1f_1 + D_2f_2$ köbméter víz tör fel: ez a **forrássűrűség**. A kert teljes forráserőssége ennek területi integrálja, $\int_K (D_1f_1 + D_2f_2)\,\mathrm{d}A$ — ugyanaz a mennyiség, amelyet fentebb a határon vett integrállal írtunk fel. A két heurisztikus képlet egyenlősége éppen a Gauss–Osztrogradszkij tétel.

### Definíció

Legyen $G \subset \mathbb{R}^p$ nyílt és $\mathbf{f} : G \to \mathbb{R}^p$ differenciálható. Az $\mathbf{f}$ vektormező *divergenciája* vagy *forrássűrűsége*

$$\operatorname{div}\mathbf{f} = D_1f_1 + D_2f_2 + \dots + D_pf_p = \operatorname{tr} J_f .$$

A $\nabla = (D_1, \dots, D_p)^t$ jelöléssel alternatív felírások:

$$\operatorname{div}\mathbf{f} = \langle \nabla, \mathbf{f}\rangle = \operatorname{tr} f' = \nabla^t \mathbf{f} .$$

Vegyük észre: a divergencia **vektormezőből skalármezőt** csinál, és csak akkor értelmes, ha az értelmezési tartomány és az értékkészlet dimenziója megegyezik.

### Nem függ a koordinátarendszertől

**Tétel.** A divergencia nem függ a koordinátarendszer irányától.

*Bizonyítás.* Térjünk át a $(\mathbf{u}_1,\dots,\mathbf{u}_p)$ koordináta-egységvektorokra; ezekből a $T = (\mathbf{u}_1,\dots,\mathbf{u}_p)$ mátrix ortogonális ($T^tT = TT^t = I$, azaz $T^{-1} = T^t$) és pozitív irányítású ($\det T = 1$). Egy vektor új koordinátái $\mathbf{y} = T^t\mathbf{x}$; a transzformáció megtartja a skaláris szorzatot, hiszen $\langle T^t\mathbf{x}, T^t\mathbf{y}\rangle = \mathbf{x}^t(TT^t)\mathbf{y} = \langle \mathbf{x},\mathbf{y}\rangle$.

Az $\mathbf{u}_i$ irányú iránymenti derivált $D_{\mathbf{u}_i} = \mathbf{u}_i^t\nabla$, tehát az új deriváló operátor $\nabla_{\text{új}} = T^t\nabla$, azaz $\operatorname{grad}_{\text{új}} f = T^t \operatorname{grad}_{\text{régi}} f$. A vektormezőt is az új rendszerben kell felírni, tehát $\nabla_{\text{új}}$-t az $\mathbf{f}_{\text{új}} = T^t\mathbf{f}$ függvényre alkalmazzuk:

$$\operatorname{div}_{\text{új}}\mathbf{f}_{\text{új}} = \nabla_{\text{új}}^t \mathbf{f}_{\text{új}} = (\nabla^t T)(T^t\mathbf{f}) = \nabla^t(TT^t)\mathbf{f} = \nabla^t\mathbf{f} = \operatorname{div}\mathbf{f}. \qquad \square$$

Ez fontos: a definíció koordinátákkal történt, az eredmény mégis geometriai — a fizikai értelmezés (forrássűrűség) csak így lehet értelmes.

### Koordinátafüggetlen definíció

A Gauss–Osztrogradszkij tétel lehetőséget ad a divergencia koordinátamentes megadására, egy pontra összehúzódó tartományokkal:

$$\operatorname{div} f(\mathbf{a}) = \lim_{r\to+0}\left( \frac{1}{2\pi r}\int_{|\mathbf{x}-\mathbf{a}|=r}\langle f(\mathbf{x}), \mathbf{n}\,\mathrm{d}s\rangle \right).$$

### Divergenciamentesség és erővonalak

Az elektromos, mágneses és gravitációs mezőket szeretjük „erővonalakkal" szemléltetni: az erővonalak iránya a térerősség iránya, sűrűségük a térerősség nagysága, és egy irányított felületdarabon a mező fluxusa a felületet átdöfő erővonalak száma. Ez a szemléltetés akkor jogos, ha a mező **forrásmentes**, azaz $0$ töltésű/tömegű térrészeken a fluxus $0$ — vagyis ha a vektormező divergenciamentes. Ezért sem szoktunk töltött testek belsejében erővonalakat rajzolni.

## Kapocs

- [[concepts/analiii/gauss-osztrogradszkij-tetel]] — a tétel, amelyben a divergencia az integrandus
- [[concepts/analiii/rotacio]] — a párhuzamos fogalom: örvénysűrűség forrássűrűség helyett
- [[concepts/analiii/newton-leibniz-formula-tobbvaltozos]] — a külső normális és a $\mathbf{n}\,\mathrm{d}s$ jelölés
- [[concepts/analiii/maxwell-egyenletek-es-integraltetelek]] — a divergencia fizikai szerepe a Gauss-törvényekben
