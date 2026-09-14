---
tags: [concept]
sources: [12_ea_An3_2022_tavasz.pdf]
derivation: source
updated: 2026-09-14
---

# Síkgörbék megadásának módjai

Egy síkgörbe explicit, implicit, paraméteres vagy polárkoordinátás alakban is megadható; a négy leírásmód ugyanazt a ponthalmazt írhatja le, de eltérő eszközöket kínál a további vizsgálathoz (érintő, ívhossz, terület).

## Tartalom

### A négy alak

Legyen $\Gamma \subset \mathbb{R}^2$ síkgörbe (l. [[concepts/analiii/gorbe-erintoje]]: $n=2$ esetén beszélünk síkgörbéről).

- **Explicit alak.** $f : [a,b] \to \mathbb{R}$ (pl. $C^1$-beli) függvény **grafikonja**: $\Gamma = \{(x, f(x)) \mid x \in [a,b]\}$.
- **Implicit alak.** $F(x,y) = 0$, ahol $F \in \mathbb{R}^2 \to \mathbb{R}$ adott függvény. Például $x^2 + y^2 = 1$ az egységkör.
- **Paraméteres alak.** $\varphi(t) = \bigl(\varphi_1(t), \varphi_2(t)\bigr)$ ($t \in [a,b]$), az [[concepts/analiii/parameteres-gorbe]] és [[concepts/analiii/gorbe-erintoje]] lapokon tárgyalt általános görbefogalom $n=2$-re. Például $\varphi(t) = (\cos t, \sin t)$ ($t \in [0,\pi]$) a felső félkörív.
- **Polárkoordinátás alak.** Egy $r(\varphi)$ ($\varphi \in [a,b]$) adott függvény a síkban meghatároz egy $\Gamma$ görbét, amelyet a polárkoordinátákkal megadott $\bigl(r(\varphi), \varphi\bigr)$ pontok futnak be $\varphi \in [a,b]$ esetén. Mivel az $\bigl(r(\varphi), \varphi\bigr)$ pont Descartes-koordinátái $\bigl(r(\varphi)\cos\varphi,\, r(\varphi)\sin\varphi\bigr)$, ezért

$$\bigl(r(\varphi)\cos\varphi,\, r(\varphi)\sin\varphi\bigr) \qquad (\varphi \in [a,b])$$

a $\Gamma$ görbe egy paraméteres előállítása — a polárkoordinátás alak tehát a paraméteres alak speciális esete, ahol a paraméter éppen a szög. Ez ugyanaz a $(x,y) = (r\cos\varphi, r\sin\varphi)$ leképezés, amely a [[concepts/analiii/polarkoordinatas-helyettesites]] lapon a kettős integrálok transzformációjának alapja.

### Példák polárkoordinátás alakra

- **Egységkör (felső félkörív).** $r(\varphi) = 1$ ($\varphi \in [0,\pi]$) az origó középpontú, $1$ sugarú félkörív polárkoordinátás alakja.
- **Arkhimédészi spirális.** $r(\varphi) = \varphi$ ($\varphi \in [0, 6\pi]$).

### Bernoulli-féle lemniszkáta

Klasszikus példa arra, hogy egy görbe implicit és polárkoordinátás alakja is természetesen adódik. A lemniszkáta azon $P$ pontok halmaza a síkon, amelyekre két rögzített $F_1, F_2$ ponttól ("fókuszponttól") mért távolságok szorzata állandó:

$$F_1P \cdot F_2P = \left(\frac{F_1F_2}{2}\right)^2.$$

**Implicit alak.** Descartes-koordinátákkal, $F_1, F_2 = (\mp a, 0)$ választással:

$$(x^2+y^2)^2 - 2a^2(x^2-y^2) = 0.$$

**Polárkoordinátás alak.** A $P$ pont polárkoordinátáira

$$r^2 = 2a^2\cos(2\varphi), \qquad \text{azaz} \qquad r(\varphi) = \sqrt{2}\,a\sqrt{\cos(2\varphi)} \qquad \left(\varphi \in \left[-\tfrac{\pi}{4}, \tfrac{\pi}{4}\right] \cup \left[\tfrac{3\pi}{4}, \tfrac{5\pi}{4}\right]\right)$$

adódik. A polárkoordinátás alak jóval kezelhetőbb, mint az implicit: a lemniszkáta területe és ívhossza is ebből az alakból számítható ki (l. [[concepts/analiii/szektorterulet-polarkoordinatakban]] és [[concepts/analiii/sikgorbe-ivhossza]]).

## Kapocs

- [[concepts/analiii/gorbe-erintoje]] — a sima elemi görbe és az érintő fogalma, amely mind a négy megadási módra alkalmazható
- [[concepts/analiii/parameteres-gorbe]] — az általános ($\mathbb{R}^m$-beli) görbefogalom, amelynek a paraméteres síkgörbe az $m=2$ esete
- [[concepts/analiii/polarkoordinatas-helyettesites]] — ugyanaz az $(x,y)=(r\cos\varphi, r\sin\varphi)$ leképezés kettős integrálok transzformációjaként
- [[concepts/analiii/sikgorbe-ivhossza]] — a polárkoordinátás alakban megadott síkgörbe ívhossza
- [[concepts/analiii/szektorterulet-polarkoordinatakban]] — a polárkoordinátás alakban megadott görbe által határolt szektorszerű tartomány területe
