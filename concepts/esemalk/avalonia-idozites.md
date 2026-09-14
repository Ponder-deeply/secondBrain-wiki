---
tags: [concept]
sources: [elte_eva_ea10_avaloniaui_complex.pdf]
derivation: source
updated: 2026-09-13
---

# Avalonia UI időzítés

Az Avalonia UI-ban a felületi és a felületfüggetlen időzítés más-más típust
igényel, és a felületi vezérlőkhöz csak az őket létrehozó szálról lehet
hozzáférni, ezért a háttérszálon kiváltott időzítő-eseményeket a UI-szálra
kell szinkronizálni.

## Tartalom

Felületi időzítésre a platformfüggő `DispatcherTimer` típus használható —
ez az Avalonia saját típusa, **nem egyezik meg** a WPF azonos nevű
időzítőjével, csak a névben és a rendeltetésben hasonló hozzá. Megadható az
időintervallum (`Interval`) és az időzítéskor (`Tick`) elvégzendő
tevékenység.

Felületfüggetlen időzítésre továbbra is használható a
`System.Timers.Timer` típus. Ez az időzítő egy háttérszálon váltja ki az
eseményt — az Avalonia UI keretrendszer esetében is igaz, hogy a felületi
vezérlőkhöz csak az őket létrehozó szálról férhetünk hozzá, ezért a szálak
közötti szinkronizáláshoz a `Dispatcher.UIThread.InvokeAsync()` hívást kell
használni.

## Kapocs

- [[concepts/esemalk/wpf-idozites]] — a WPF `System.Timers.Timer` vs.
  `DispatcherTimer` megkülönböztetése és a `Dispatcher.BeginInvoke`-kal
  történő szálbiztos felületfrissítés — az Avalonia megoldása ugyanezt az
  elvet követi, más típusnevekkel
- [[concepts/esemalk/csharp-task-szinkronizacio]] — a `SynchronizationContext`
  és a taszkok szálszinkronizációja C#-ban
- [[concepts/esemalk/winforms-vezerlo-invoke-begininvoke]] — a WinForms
  `Invoke`/`BeginInvoke` mintája, amelynek az Avalonia `Dispatcher.UIThread`
  hívása a megfelelője
