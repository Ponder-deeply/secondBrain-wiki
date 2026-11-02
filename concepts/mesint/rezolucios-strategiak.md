---
tags: [concept]
sources: [09.kovetkeztetes.pdf]
derivation: source
kind: comparison
element: water
updated: 2026-10-12
---

# Rezolúciós stratégiák

A rezolúció nemdeterminisztikus, ezért az alapalgoritmust vezérlési stratégiákkal egészítik ki. Ezek modellfüggő stratégiák: csak klózalapú reprezentáció esetén értelmezhetők.

## Tartalom

### A nemdeterminizmus forrásai

Egy lépésben egyszerre több rezolválható klózpár lehet; egy klózpárban több komplemens literálpár lehet; ugyanannak a literálnak több előfordulása lehet. Példa: $\{P(x,f(a))\vee P(x,f(y))\vee Q(y),\ \neg P(z,f(a))\vee\neg Q(z),\ P(u,f(a))\vee\neg Q(a)\}$.

### Stratégia fogalma

A rezolúciós stratégia az alapalgoritmust kiegészítő előírás, amely

- **sorrendet ad** a rezolvens képzésekre (sorrendi stratégia), vagy
- **korlátozza** egy adott pillanatban előállítható rezolvensek körét (vágó stratégia); ilyenkor sérülhet a módszer teljessége.

### Értékelés

A rezolúcióba nem építhető heurisztika, és a stratégiák ellenére sem hatékony; ezért a kurzus szerint nem jó MI-módszer (lásd [[concepts/mesint/rezolucio-mint-keresesi-rendszer]]). Szabályalapú alternatíva: [[concepts/mesint/szabalyalapu-kovetkeztetes]].

## Kapocs

- [[concepts/mesint/rezolucio-mint-keresesi-rendszer]] — az alapalgoritmus, amelynek vezérlését kiegészítik
- [[concepts/mesint/modellfuggo-vezerles]] — a modellfüggő vezérlési stratégia általános fogalma
- [[concepts/mesint/vezerlesi-strategiak]] — vezérlési stratégiák általában
- [[concepts/mesint/cafolati-graf]] — a keresési tér, amelyet a stratégia szűkít
