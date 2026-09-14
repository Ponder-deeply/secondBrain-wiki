---
tags: [concept]
sources: [elte_eva_ea08_wpf_complex_resources.pdf]
derivation: source
updated: 2026-09-13
---

# Időzítés WPF alkalmazásokban

A WPF két időzítő típust kínál rendszeresen ismétlődő tevékenységek
megvalósítására, amelyek eltérően viszonyulnak a felületi (UI) szálhoz.

## Tartalom

### A két időzítő típus

- **`System.Timers.Timer`** — a felülettől független időzítő, amely nem
  szinkronizál automatikusan a UI szállal; jellemzően a modellben
  használjuk
- **`DispatcherTimer`** — felületi időzítő, amely szinkronizál a
  felülettel; a [[concepts/esemalk/wpf-kornyezet-fuggosegkezeles|környezetben]]
  vagy a nézetmodellben használjuk

### Szálbiztos felületfrissítés: `Dispatcher.BeginInvoke`

Ha egy tevékenység (pl. egy modellbeli, `System.Timers.Timer`-rel vezérelt
művelet) nem a UI szálon fut, de a felületet kell módosítania, a
végrehajtást a `Dispatcher.BeginInvoke(…)` metódussal kell a UI szálra
ütemezni, az alkalmazásból hívva:

```csharp
Application.Current.Dispatcher.
    BeginInvoke(new Action(() => {
        textBox.Text = "Hello World!";
    }));
```

Ez a minta a WPF megfelelője a WinForms
[[concepts/esemalk/winforms-vezerlo-invoke-begininvoke|`Control.Invoke`/`BeginInvoke`]]
párosának: mindkét keretrendszerben csak a felületet létrehozó szál nyúlhat
a vezérlőkhöz, és az idegen szálról érkező módosítást a megfelelő
dispatcher/üzenetsorra kell ütemezni.

## Kapocs

- [[concepts/esemalk/wpf-kornyezet-fuggosegkezeles]] — az időzítés mint a
  környezet hatáskörébe tartozó globális tevékenység
- [[concepts/esemalk/winforms-vezerlo-invoke-begininvoke]] — az analóg
  `Invoke`/`BeginInvoke` minta WinForms-ban
- [[concepts/esemalk/csharp-task-szinkronizacio]] — a `SynchronizationContext`
  és a felületi szálra való visszatérés általánosabb fogalma
- [[concepts/esemalk/folyamat-es-szal]] — a szál fogalma, amelyre az
  időzítők szálkezelése épül
- [[subjects/esemalk]]
