---
tags: [concept, esemalk/winforms-elemi-grafika]
sources: [elte_eva_ea03_winforms_dynamic.pdf]
derivation: source
updated: 2026-09-13
---

# Egérkezelés WinForms alkalmazásokban

Az alapvető egérkattintás (`Click`) mellett a WinForms vezérlők számos
egérrel kapcsolatos eseményt tudnak kezelni, amelyek elemi grafikai
alkalmazásokban (pl. rajzolóprogram) a felhasználói interakció alapját
adják.

## Tartalom

- **`MouseDown`** — egérgomb lenyomása; **`MouseUp`** — egérgomb
  felengedése. Mindkettő eseményargumentumából lekérdezhető a lenyomott
  gomb (`Button`), valamint az aktuális egérpozíció (`X`, `Y`).
- **`MouseWheel`** — görgőmozgás; lekérdezhető a mozgatás mértéke
  (`Delta`).
- **`MouseMove`** — egér mozgása; lekérhető az esetlegesen lenyomott gomb
  és az egérpozíció.
- **`MouseEnter`** — a vezérlőn történő megjelenés (az egérmutató belép a
  vezérlő területére); **`MouseHover`** — mozgás a vezérlőn belül;
  **`MouseLeave`** — eltávolodás a vezérlőtől.

Ezek az események tipikusan együtt jelennek meg egy rajzolóalkalmazásban:
`MouseDown`-nal kezdődik egy alakzat felvétele, `MouseMove` frissíti az
alakzat előnézetét (pl. kék kerettel), `MouseUp`-nál kerül végleg az
alakzat a képbe. Lásd a konkrét megvalósítást:
[[concepts/esemalk/rajzolo-alkalmazas-tervezese]].

## Kapocs

- [[concepts/esemalk/winforms-grafika-alapok]] — a rajzfelület és a
  `Graphics` osztály, amelyre az egéreseményekre válaszul rajzolunk
- [[concepts/esemalk/vezerlo-esemenykezelo-tarsitas]] — vezérlők
  eseményeinek kezelése, a `sender` paraméter
- [[concepts/esemalk/billentyuzetkezeles-winforms]] — a billentyűzetes
  eseménykezelés analóg mintája
