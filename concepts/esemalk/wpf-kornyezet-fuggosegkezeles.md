---
tags: [concept, esemalk/wpf-eroforrasok-es-stilusok]
sources: [elte_eva_ea08_wpf_complex_resources.pdf]
derivation: source
updated: 2026-09-13
---

# A környezet (Environment) és a függőségkezelés MVVM architektúrában

Az MVVM rétegei közötti laza csatolást (*loose coupling*) függőség-
befecskendezéssel érjük el; a rétegek példányosítását és összekötését egy
külön komponens, az *alkalmazáskörnyezet* (*environment*) végzi.

## Tartalom

### Laza csatolás a rétegek között

Az [[concepts/esemalk/wpf-mvvm-alapok]] architektúra akkor megfelelő, ha az
egyes rétegek (nézet, nézetmodell, modell, perzisztencia) között minél
kisebb a függőség: egyik réteg sem függhet a másik konkrét
megvalósításától, és nem avatkozhat be a másik működésébe. Ezt
[[concepts/esemalk/fuggoseg-befecskendezes]] (*dependency injection*)
segítségével érjük el:

- a nézetmodellt a nézetbe egy tulajdonságon keresztül fecskendezzük be
  (*setter injection*)
- a modellt a nézetmodellbe, a perzisztenciát a modellbe konstruktoron
  keresztül helyezzük (*constructor injection*)

A modell és a perzisztencia réteg emiatt absztrakció (interfész) mögött
jelenik meg a felette lévő rétegek felől nézve, a konkrét megvalósítás
(*realization*) pedig ettől elkülönül — ugyanaz a minta, mint amit az
`IExamGenerator` interfész is követ a példaalkalmazásban (lásd
[[concepts/esemalk/wpf-tobbablakos-mvvm-pelda]]).

### Az alkalmazáskörnyezet (environment)

A programegységek példányosítását és befecskendezését az *alkalmazás
környezete* (*application environment*) végzi:

- ismeri és kezeli az alkalmazás összes programegységét, az absztrakciókat
  és a megvalósításokat is
- nem az adott komponens, hanem a környezet dönti el, hogy a függőségek
  mely megvalósításai kerülnek alkalmazásra (*Inversion of Control*, IoC)
- egyszerű esetben magát az alkalmazást (`App`) használhatjuk környezetként,
  de külön komponens is bevezethető

A környezet hatásköre kibővíthető olyan, a teljes alkalmazást érintő
globális tevékenységekkel is, mint például az
[[concepts/esemalk/wpf-idozites|időzítés]].

### A rétegek közötti adat- és vezérlésáramlás

A környezet a példányosítást és befecskendezést végzi minden réteg felé
(nézet, nézetmodell, modell, perzisztencia). Ezután a rétegek között az
adat és a vezérlés a megszokott irányokban áramlik:

- nézet ↔ nézetmodell: adatkötés, parancskötés (le), változáskövetés (fel)
- nézetmodell ↔ modell: metódushívások (le), visszatérési értékek és
  események (fel)
- modell → környezet: események (pl. globális állapotváltozás jelzése)

## Kapocs

- [[concepts/esemalk/wpf-mvvm-alapok]] — az MVVM rétegei, amelyek közötti
  csatolást ez a lap függőségkezelése lazítja
- [[concepts/esemalk/fuggoseg-befecskendezes]] — a függőség-befecskendezés
  általános fogalma, itt WPF/MVVM kontextusban
- [[concepts/esemalk/wpf-idozites]] — az időzítés mint a környezet
  hatáskörébe tartozó globális tevékenység
- [[concepts/esemalk/wpf-tobbablakos-mvvm-pelda]] — a vizsgatétel-generátor
  példa, ahol az `App` tölti be a környezet szerepét
- [[concepts/esemalk/wpf-mvvm-parancsok-icommand]] — a parancskötés, amelyen
  keresztül a nézet a nézetmodellel kommunikál
- [[subjects/esemalk]]
