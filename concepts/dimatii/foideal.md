---
tags: [concept]
sources: [Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf]
derivation: source
kind: theorem
element: water
updated: 2026-10-21
---

# Főideál és oszthatóság

Kommutatív egységelemes gyűrűben az $a$ által generált főideál $aR$; az ideálok tartalmazása az oszthatóságot, az egyenlőségük az asszociáltságot, az egész gyűrű az egységet kódolja.

## Tartalom

### Főideál kommutatív egységelemes gyűrűben

**Tétel (8.2.25).** Egy $R$ kommutatív egységelemes gyűrűben az $a \in R$ elem által generált főideálra $(a) = aR$. Speciálisan a nulla által generált főideál $\{0\}$, az egységelem által generált főideál pedig $R$.

(A generált ideál és a főideál definíciója: [[concepts/dimatii/reszgyuru-es-idealok]].)

### Oszthatóság az ideálok nyelvén

**Állítás (8.2.26).** Egy $R$ egységelemes integritási tartomány $a, b$ elemeire

1. $(a) \subseteq (b) \iff b \mid a$;
2. $(a) = (b) \iff a$ és $b$ asszociáltak;
3. $(a) = R \iff a$ egység.

Az állítás a diákban bizonyítás nélkül áll ($\square$); az $(a) = aR$ alakból és az egységelemes tartományi oszthatóságból olvasható le.

**Következmény.** Az oszthatóság és az asszociáltság (lásd [[concepts/dimatii/egyseg-es-asszocialt]]) ideálokra fordítható; például $\mathbb{Z}$-ben $(a) \subseteq (b)$ pontosan akkor, ha $b \mid a$, vagyis az osztó generálja a nagyobb ideált.

### Kapcsolódó diaemlékeztető: lnko és felbonthatatlan

Egységelemes integritási tartományban $d$ az $a, b$ **legnagyobb közös osztója**, ha közös osztó ($d \mid a$, $d \mid b$), és minden közös osztónak osztója ($c \mid a$, $c \mid b \Rightarrow c \mid d$). A felbonthatatlan és prím definíciója: [[concepts/dimatii/felbonthatatlan-es-prim]].

## Kapocs

- [[concepts/dimatii/reszgyuru-es-idealok]] — az ideál- és főideál-fogalom
- [[concepts/dimatii/egyseg-es-asszocialt]] — az egység és az asszociáltság
- [[concepts/dimatii/integritasi-tartomany]] — a keret
- [[concepts/dimatii/legnagyobb-kozos-oszto]] — a közös osztók és az lnko
- [[concepts/dimatii/euklideszi-gyuru]] — az euklideszi gyűrű és egységei
