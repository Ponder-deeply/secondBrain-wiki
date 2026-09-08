# Plan: tortenelmi-titkositok diagrams

Page: Wiki/concepts/kript/tortenelmi-titkositok.md
Date: 2026-04-19

## Proposed diagrams

### 1. titkositasi-sema
- Label: titkositasi-sema
- Filename: tortenelmi-titkositok-titkositasi-sema.excalidraw.md
- Rationale: The (Gen, Enc, Dec) triple is the foundation of every scheme discussed. A flowchart showing the three components and how plaintext + key → ciphertext → plaintext gives spatial intuition that anchors the rest of the page.
- Placement: after ## Alapfogalmak

### 2. tamadasi-modellek
- Label: tamadasi-modellek
- Filename: tortenelmi-titkositok-tamadasi-modellek.excalidraw.md
- Rationale: The four attack models (COA, KPA, CPA, CCA) form a hierarchy of increasing attacker power. A layered diagram makes the containment relationship explicit better than the prose table.
- Placement: after ## Támadasmodellek, replacing or supplementing the table

### 3. vigenere-kriptanalisis
- Label: vigenere-kriptanalisis
- Filename: tortenelmi-titkositok-vigenere-kriptanalisis.excalidraw.md
- Rationale: Vigenère cryptanalysis is a two-step pipeline (Kasiski → key length → column frequency analysis → key). A flowchart of the attack steps is high-leverage because the prose lists steps without showing their sequential dependency.
- Placement: after ## Vigenère-titkosítás
