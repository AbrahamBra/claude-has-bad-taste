---
name: brief-mode
description: "Mode D for design-eye. Load when user has no existing site AND provides only keywords/adjectives with no named reference. Generates original visual directions from inspiration words using pure reasoning — no web browsing."
---

# Brief Mode (Mode D)

Load this module when BOTH conditions are met:
- a) No existing site in the brain dump (no URL, no current visual elements, no "mon site actuel")
- b) Keywords-only brief: adjectives, moods, words — no named site, brand, or competitor

If ANY named reference appears → Mode B, not Mode D.
Keywords alone without any named reference = Mode D.

## This mode does NOT browse references

Mode D is pure reasoning from design principles. No WebFetch. No Agent calls.
References can be added afterward if the user wants to validate against real examples.

## Step 1: Extract visual DNA

For each inspiration word, derive across 5 dimensions:

| Dimension | What to derive |
|-----------|----------------|
| Spatial ratio | Whitespace density (sparse / balanced / dense) |
| Palette | Hue family, saturation level, contrast ratio |
| Typography | Family class (serif / sans / mono / display), weight, relative size |
| Motion | Speed (slow / medium / fast), amplitude (subtle / expressive), style (ease / spring / linear) |
| Texture | Surface feel (grain / flat / glass / matte) |

## Step 2: Detect creative tensions

When input words pull in opposite directions, resolve the tension into a coherent principle instead of averaging:

- "minimal" + "powerful" → minimalism of means, maximalism of impact: few elements, each one very strong
- "warm" + "technical" → precision in a warm material: tight grid, organic color
- "simple" + "expensive" → restraint as luxury: nothing unnecessary, everything intentional

## Step 3: Propose 2 original directions

Use output-formats.md Format 4 (canonical structure for original directions).
The two directions should represent genuinely different resolutions of the brief — not variations of the same answer.
Name each direction with an evocative title that captures its principle.

## Step 4: User picks one direction

Ask: "Laquelle te parle ?" — wait for response before proceeding.
If the user wants to blend elements: extract what they want from each and synthesize.

## Step 5: Validate

Synthesize the chosen direction into output-formats.md Format 3.
In the "Inspiré de" field: use the sub-line "dérivé de : [mots-clés input]" (same field, sub-line).
Omit "Non retenu" field (there are no rejected references in Mode D).

Wait for explicit confirmation ("oui" / "OK" / "go" / "validé") before writing design-direction.md.
Ambiguous response → "Je confirme la direction avant de coder. C'est validé ?"

Sequence: Format 4 (2 options) → user picks → Format 3 (synthesis) → user validates → design-direction.md
