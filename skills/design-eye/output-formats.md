---
name: output-formats
description: "Canonical output formats for design-eye. Load when presenting any comparison table or direction proposal to the user. Defines Format 1 (reference comparison), Format 2 (element-level selection), Format 3 (synthesized direction), Format 4 (original directions — Mode D only)."
---

# Output Formats

Load this module whenever presenting options or a direction proposal to the user.
Always end every format with a closed question — never leave the user without a clear next action.

## Format 1 — Reference comparison

Use after parallel research (Modes A/B/C). Shows researched sites side by side.

```
| # | Site | Ambiance | Typography | Colors | What we take |
|---|------|----------|------------|--------|--------------|
| A | url  | Minimal dark | Serif bold | Mono black | Hero spacing |
| B | url  | Editorial    | Sans mono  | Cream/black | Content grid |
| C | url  | Bold agency  | Display    | Saturated   | Title motion |

→ "Lesquels te parlent ? Tu peux en choisir plusieurs."
```

**"What we take" column rules:** 1–3 words naming a specific design element (e.g., "Hero spacing", "Card style", "Title motion"). Never a full sentence. Never vague ("nice layout").

## Format 2 — Element-level selection

Use when the user wants to mix elements from different references.

```
Titre H1    → comme A (display, très grand)
Fond        → comme B (crème, pas noir)
Bouton CTA  → comme C (couleur saturée)
Spacing     → comme A (très aéré)

→ "C'est ça le mix ?"
```

## Format 3 — Synthesized direction

Use before final validation in all modes. Single direction summary after user has made choices.

```
## Direction proposée — [nom du projet]

Ambiance    : [1 phrase]
Palette     : [3 valeurs oklch]
Typographie : [famille + usage]
Effets      : [liste courte]
Motion      : [principe]

Inspiré de  : A pour X, B pour Y        ← Modes A/B/C : références lettres du Format 1
              dérivé de : [mots-clés]   ← Mode D uniquement (même champ, sous-ligne)
Non retenu  : C (trop chargé vs brief)  ← omettre en Mode D

→ "C'est validé ?"
```

**Validation gate:** only "oui" / "OK" / "go" / "validé" counts as confirmed. Anything ambiguous → ask again: "Je confirme la direction avant de coder. C'est validé ?"

## Format 4 — Original directions (Mode D only)

Use in Mode D to present 2 original directions derived from keywords. This is the canonical source for this structure — brief-mode.md references it.

```
Direction A — "[nom évocateur]"
Principe : [1 phrase]
├── Fond : [valeur oklch]
├── Typographie : [décision]
└── Motion : [décision]

Direction B — "[nom évocateur]"
Principe : [1 phrase]
├── Fond : [valeur oklch]
├── Typographie : [décision]
└── Motion : [décision]

→ "Laquelle te parle ?"
```

After the user picks one direction: synthesize into Format 3, then validate.
Sequence: Format 4 (2 options) → user picks → Format 3 (synthesis) → user validates → design-direction.md
