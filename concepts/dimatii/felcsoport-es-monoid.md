---
tags: [concept, dimatii/algebrai-strukturak]
sources: [DimatIIEa03.pdf, DimatIIEa04.pdf]
derivation: source
updated: 2026-09-08
---

# Félcsoport és monoid

Asszociatív grupoid a félcsoport; ha van benne egységelem is, monoidnak (egységelemes félcsoportnak) nevezzük.

## Tartalom

### Félcsoport

Egy $(G; *)$ grupoid **félcsoport**, ha $*$ asszociatív $G$-n, azaz

$$\forall a, b, c \in G : (a * b) * c = a * (b * c).$$

### Egységelem (semleges elem)

Ha létezik olyan $s \in G$ elem, amire

$$\forall g \in G : s * g = g * s = g,$$

akkor $s$-t **semleges elemnek**, más néven **egységelemnek** nevezzük.

### Monoid

Ha egy $(G; *)$ félcsoportban létezik $s$ semleges elem, akkor $G$-t **egységelemes félcsoportnak**, **semleges elemes félcsoportnak**, más néven **monoidnak** nevezzük.

### Példák

- $\mathbb{N}$ a $+$ művelettel egységelemes félcsoport, egységeleme $n = 0$.
- $\mathbb{Q}$ a $\cdot$ művelettel egységelemes félcsoport, egységeleme $n = 1$.
- $\mathbb{C}^{k \times k}$ a mátrixszorzással egységelemes félcsoport, egységeleme az egységmátrix.

Monoidban az egységelem meglétén túl nem követeljük meg az inverz létezését — épp ez a lépés visz tovább a [[concepts/dimatii/csoport]] fogalmához.

## Kapocs

- [[concepts/dimatii/algebrai-struktura]] — a grupoid, amiből a félcsoport specializálódik
- [[concepts/dimatii/muvelet]] — az asszociativitás definíciója
- [[concepts/dimatii/csoport]] — egységelemes félcsoport, amelyben minden elemnek van inverze
- [[concepts/dimatii/gyuru]] — a gyűrű multiplikatív része félcsoport
