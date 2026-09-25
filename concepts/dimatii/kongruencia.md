---
tags: [concept, dimatii/kongruenciak]
sources: [DimatIIEa01.pdf, DimatIIEa02.pdf]
derivation: source
updated: 2026-09-08
---

# Kongruencia

Oszthatósági kérdésekben gyakran csak a maradék számít; a kongruencia ezt a „modulo $m$ egyenlőséget” teszi számolható relációvá.

## Tartalom

Sok problémában — a hét napjai, az órák száma — csak a maradékos osztás maradéka fontos. Például $16 \bmod 3 = 1$ és $4 \bmod 3 = 1$: $3$-mal való oszthatóság szempontjából $16$ „$=$” $4$.

**Definíció.** Legyenek $a, b, m$ egészek. Azt mondjuk, hogy $a \equiv b \pmod m$ ($a$ és $b$ **kongruensek** modulo $m$), ha $m \mid a - b$; és $a \not\equiv b \pmod m$ ($a$ és $b$ **inkongruensek**), ha $m \nmid a - b$.

**Ekvivalens megfogalmazás.** $a \equiv b \pmod m \iff a \bmod m = b \bmod m$, azaz $a$ és $b$ $m$-mel osztva ugyanazt a maradékot adják.

**Példák.** $16 \equiv 4 \pmod 3$, mert $3 \mid 16 - 4$, és valóban $16 \bmod 3 = 1 = 4 \bmod 3$. $16 \equiv 4 \pmod 2$, mert $2 \mid 12$, és $16 \bmod 2 = 0 = 4 \bmod 2$. Viszont $16 \not\equiv 4 \pmod 5$, mert $5 \nmid 12$, és $16 \bmod 5 = 1 \neq 4 = 4 \bmod 5$.

### A kongruencia tulajdonságai

**Tétel.** Minden $a, b, c, d$ és $m$ egész számra igaz:

1. $a \equiv a \pmod m$ (reflexív);
2. $a \equiv b \pmod m$, $m' \mid m \Rightarrow a \equiv b \pmod{m'}$;
3. $a \equiv b \pmod m \Rightarrow b \equiv a \pmod m$ (szimmetrikus);
4. $a \equiv b \pmod m$, $b \equiv c \pmod m \Rightarrow a \equiv c \pmod m$ (tranzitív);
5. $a \equiv b \pmod m$, $c \equiv d \pmod m \Rightarrow a + c \equiv b + d \pmod m$;
6. $a \equiv b \pmod m$, $c \equiv d \pmod m \Rightarrow ac \equiv bd \pmod m$.

**Bizonyítás.** 1. $m \mid 0 = a - a$. 2. $m' \mid m$, $m \mid a - b \Rightarrow m' \mid a - b$. 3. $m \mid a - b \Rightarrow m \mid b - a = -(a-b)$. 4. $m \mid a - b$, $m \mid b - c \Rightarrow m \mid a - c = (a-b) + (b-c)$. 5. $m \mid a - b$, $m \mid c - d \Rightarrow m \mid (a+c) - (b+d)$. 6. $a = q_1m + b$, $c = q_2m + d \Rightarrow ac = (q_1m+b)(q_2m+d) = m(q_1q_2m + q_1d + q_2b) + bd$. $\square$

Az 1., 3. és 4. pont szerint a kongruencia ekvivalenciareláció; osztályai a [[concepts/dimatii/maradekosztaly]]ok. Az 5. és 6. pont szerint a művelettartás miatt lehet velük „úgy számolni, mint egyenletekkel”.

**Példa.** Mi lesz $345 \bmod 7$? $345 = 34\cdot 10 + 5 \equiv 6\cdot 3 + 5 = 18 + 5 \equiv 4 + 5 = 9 \equiv 2 \pmod 7$.

### Egyszerűsítés

A szorzás megfordítása nem szabad korlátlanul: $14 \equiv 6 \pmod 8 \Rightarrow 42 \equiv 18 \pmod{24}$, de visszafelé nem: $2\cdot 7 \equiv 2\cdot 3 \pmod 8$, mégis $7 \not\equiv 3 \pmod 8$.

**Tétel.** Legyenek $a, b, c, m$ egészek. Ekkor
$$ac \equiv bc \pmod m \iff a \equiv b \ \left(\operatorname{mod} \tfrac{m}{(c,m)}\right).$$

**Következmény.** Ha $(c,m) = 1$, akkor $ac \equiv bc \pmod m \iff a \equiv b \pmod m$, azaz a modulushoz relatív prím tényezővel szabadon egyszerűsíthetünk.

**Bizonyítás.** Legyen $d = (c,m)$. Ekkor $m \mid c(a-b) \iff \frac{m}{d} \mid \frac{c}{d}(a-b)$. Mivel $\left(\frac{m}{d}, \frac{c}{d}\right) = 1$, ezért $\frac{m}{d} \mid (a-b) \iff a \equiv b \pmod{\frac{m}{d}}$. $\square$

**Példa.** $2\cdot 7 \equiv 2\cdot 3 \pmod 8 \Rightarrow 7 \equiv 3 \pmod{\frac{8}{2}}$.

## Kapocs

- [[concepts/dimatii/oszthatosag]] — a definiáló reláció
- [[concepts/dimatii/maradekos-osztas]] — az ekvivalens megfogalmazás alapja
- [[concepts/dimatii/maradekosztaly]] — a kongruencia ekvivalenciaosztályai
- [[concepts/dimatii/linearis-kongruencia]] — az $ax \equiv b \pmod m$ egyenlet
- [[concepts/dimatii/szimultan-kongruenciak]] — kongruenciarendszerek
- [[concepts/kript/linearis-kongruencialis-generator]] — kongruenciákra épülő álvéletlen-generátor
