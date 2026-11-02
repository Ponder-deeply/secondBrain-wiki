---
tags: [concept]
sources: [NM1_ea12.pdf]
derivation: source
kind: comparison
element: water
updated: 2026-10-21
---

# Húrmódszer és szelőmódszer

Derivált nélküli gyökkeresők: a Newton-módszer érintője helyett két pont közötti egyenes zérushelyét veszik. A húrmódszer mindig előjelváltó pontpárt tart meg (biztonságos, elsőrendű); a szelőmódszer a két legutóbbi pontot használja (gyorsabb, $p = \tfrac{1+\sqrt5}{2}$ rendű, de csak lokálisan konvergens).

## Tartalom

### Két ponton átmenő egyenes zérushelye

Az $(a, f(a))$ és $(b, f(b))$ pontokon átmenő egyenes meredeksége $\tfrac{f(a) - f(b)}{a - b}$, egyenlete

$$y - f(a) = \frac{f(a) - f(b)}{a - b}(x - a),$$

zérushelye ($y = 0$):

$$x = a - \frac{f(a)\,(a - b)}{f(a) - f(b)}.$$

Mindkét módszer ezt a képletet alkalmazza, csak a pontpár választásában különböznek.

### Húrmódszer (regula falsi)

**Alapötlet:** mint az [[concepts/nummodi/intervallumfelezes|intervallumfelezés]], mindig olyan pontpárt tartunk meg, amelyben $f$ előjelet vált, de a felezőpont helyett a húr zérushelyét vesszük új pontnak.

**Definíció.** $f \in C[a;b]$, $f(a)f(b) < 0$ esetén

$$x_0 := a,\quad x_1 := b,\qquad x_{k+1} = x_k - \frac{f(x_k)\,(x_k - x_s)}{f(x_k) - f(x_s)} \quad (k = 1, 2, \dots),$$

ahol $s$ a legnagyobb olyan index, amelyre $f(x_k)\cdot f(x_s) < 0$.

**Szemléltetés:** az $(x_s, f(x_s))$ és $(x_k, f(x_k))$ pontokat összekötő húr metszi az $x$ tengelyt $x_{k+1}$-ben; mivel a két pont előjele különböző, $x_{k+1}$ közöttük van, és a gyök mindig bennmarad a bezárt intervallumban.

**Tétel** (biz. nélkül). Ha $f \in C^2[a;b]$, $f(a)f(b) < 0$ és $M(b - a) < 1$, akkor a húrmódszer **elsőrendben** konvergál az $x^*$ gyökhöz, és

$$|x_k - x^*| \le \frac1M\bigl(M|x_0 - x^*|\bigr)^k, \qquad M = \frac{M_2}{2m_1}$$

(mint a [[concepts/nummodi/newton-modszer|Newton-módszer]] lokális tételében).

### Szelőmódszer

**Alapötlet:** a Newton-módszerben a deriváltat a két utolsó pont különbségi hányadosával helyettesítjük: $f'(x_k) \approx \tfrac{f(x_k) - f(x_{k-1})}{x_k - x_{k-1}}$, azaz az érintő helyett a szelő zérushelyét vesszük. Előjelváltást nem követelünk.

**Definíció.** $f \in C[a;b]$ esetén

$$x_0, x_1 \in [a;b],\qquad x_{k+1} = x_k - \frac{f(x_k)\,(x_k - x_{k-1})}{f(x_k) - f(x_{k-1})} \quad (k = 1, 2, \dots).$$

**Szemléltetés:** az $(x_{k-1}, f(x_{k-1}))$ és $(x_k, f(x_k))$ pontokon átmenő szelő zérushelye $x_{k+1}$ — lehet a két pont intervallumán kívül is.

**Tétel** (biz. nélkül). Ha $f \in C^2[a;b]$ és

1. $\exists\, x^* \in [a;b]$: $f(x^*) = 0$,
2. $f'$ állandó előjelű,
3. $x_0, x_1 \in [a;b]$: $|x_0 - x^*|, |x_1 - x^*| < r := \min\bigl\{\tfrac1M, |x^* - a|, |x^* - b|\bigr\}$,

akkor a szelőmódszer $p = \tfrac{1 + \sqrt5}{2} \approx 1{,}618$ rendben konvergál $x^*$-hoz.

### Összehasonlítás

| | Húrmódszer | Szelőmódszer | [[concepts/nummodi/newton-modszer\|Newton-módszer]] |
|---|---|---|---|
| Kiinduló adat | $[a;b]$, $f(a)f(b) < 0$ | $x_0, x_1$ a gyök közelében | $x_0$ a gyök közelében |
| Derivált kell? | nem | nem | igen, $f'(x_k)$ |
| Új függvényérték lépésenként | 1 | 1 | $f$ és $f'$ |
| Konvergencia | globális (a gyök bezárva marad), $M(b-a) < 1$ mellett | lokális | lokális (vagy monoton, ha $f', f''$ előjeltartó) |
| [[concepts/nummodi/konvergenciarend\|Rend]] | $1$ | $\tfrac{1+\sqrt5}{2} \approx 1{,}618$ | $2$ |

A húrmódszer tehát megbízható, de lassú; a szelőmódszer gyorsabb, de előjelváltást nem tart meg, így „elszállhat”; a Newton a leggyorsabb, cserébe deriváltat igényel és csak elég közelről biztos.

### Vizsgán (26. tétel, a))

Mindkét módszer alapötlete, ábrája és képletének levezetése (két ponton átmenő egyenes zérushelye); a konvergenciarend fogalma; összevetés egymással és a Newton-módszerrel (fenti táblázat). A b) rész a Newton lokális konvergenciatétele.

## Kapocs

- [[concepts/nummodi/newton-modszer]] — az érintős változat; a 26. b) bizonyítása
- [[concepts/nummodi/intervallumfelezes]] — szintén előjelváltást tartó, de felező módszer
- [[concepts/nummodi/konvergenciarend]] — a rendek definíciója és összevetése
- [[concepts/nummodi/nemlinearis-egyenletek-fixpont]] — a feladat, gyök létezése
