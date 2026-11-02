---
tags: [concept]
sources: [09.kovetkeztetes.pdf]
derivation: source
kind: procedure
element: earth
updated: 2026-10-12
---

# Válaszadás rezolúcióval

Kérdésre (ki, mit, hol, mikor, mennyiért) adott választ is kinyerhetünk a rezolúciós cáfolatból: a cáfolati gráf mintájára válaszgráfot építünk, amelynek gyökere tartalmazza a választ.

## Tartalom

### Példa

"Ha Fifi mindenhová követi Jánost, és János most az iskolában van, akkor hol van most Fifi?" Formalizálás: $H(y,x)$ = az $y$ dolog az $x$ helyen van; axiómák: $\forall x[H(János,x)\to H(Fifi,x)]$, $H(János,iskola)$.

Először megmutatjuk, hogy létezik-e Fifi számára hely: célállítás $\exists x\,H(Fifi,x)$, negáltja $\neg H(Fifi,x_2)$. A cáfolat: $\neg H(Fifi,x_2)$ és $\neg H(János,x_1)\vee H(Fifi,x_1)$ rezolvense (helyettesítés $\{x_2|x_1\}$) $\neg H(János,v)$; ez $H(János,iskola)$-val ($\{v|iskola\}$) adja $\square$-t.

A válaszgráfban a célállítás negáltjához hozzáfűzzük annak negáltját ($H(Fifi,x_2)\vee\neg H(Fifi,x_2)$), és ugyanazokat a lépéseket követjük: a gyökérben $H(Fifi,iskola)$ áll, azaz Fifi az iskolában van.

### Válaszadási eljárás

1. A kérdést "van-e válasz a kérdésre" célállítással helyettesítjük.
2. Rezolúcióval belátjuk, hogy a célállítás következik az axiómákból.
3. A célállítás negáltjából származó klózokat negáltjaik hozzáfűzésével érvényes formulákká egészítjük ki.
4. A cáfolati gráf által meghatározott rezolúciót követve létrehozzuk a hasonló szerkezetű válaszgráfot, amelynek gyökere tartalmazza az egyik választ.

## Kapocs

- [[concepts/mesint/cafolati-graf]] — a válaszgráf a cáfolati gráf szerkezetét követi
- [[concepts/mesint/rezolucio-mint-keresesi-rendszer]] — az alapeljárás
- [[concepts/mesint/sknf-atalakitas]] — az axiómák klózformája
