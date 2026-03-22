---
name: taste-memory
description: "Persistent visual preference profile for design-eye. Load at skill launch when taste-profile.md exists in project memory. Eliminates repeat questions by pre-filling known preferences. Updates profile after each validated design-direction.md."
---

# Taste Memory

## Detection

At skill launch, before the brain dump, check:
`~/.claude/projects/<active-project-path>/memory/taste-profile.md`

- File exists, non-empty, and parseable → load and apply
- File absent, empty, unparseable, or malformed → treat as absent, skip entirely
- "Parseable" = contains at least one of: `### Confirmed`, `### Tendencies`, `### Explicit rejections`

Load is unconditional when the file is valid — mode detection happens after the brain dump, not here.

## Profile structure

```markdown
## Taste Profile — [user name]

### Confirmed (validated_count >= 2)
- Background: dark by default [validated_count: 3]
- Typography: sans-serif, bold headings [validated_count: 2]
- Effects: grain texture yes, glassmorphism no [validated_count: 2]
- Motion: subtle, never decorative [validated_count: 2]
- Density: airy, generous whitespace [validated_count: 2]

### Tendencies (validated_count = 1)
- Accent color: warm oklch (amber, copper) [validated_count: 1]
- Layout: asymmetric preferred over symmetric grid [validated_count: 1]

### Explicit rejections (never propose)
- Rainbow gradients
- Carousels
- Stock photos
```

## Usage during the session

After loading the profile:
1. Pre-fill brain dump hypotheses from Confirmed entries — present them as assumptions, not questions
2. Skip questions already answered in the profile
3. After the brain dump, cross-reference:
   - Contradiction with profile → flag: "Tu m'as dit que tu aimais X, mais là le brief dit Y — c'est volontaire ?"
   - Confirmation → reinforce, no need to re-validate
   - New territory → treat as first time

**Critical rule:** The profile filters suggestions. It never decides. If a project brief contradicts the profile → follow the brief, note the exception.

## Profile update rules

Trigger: Claude writes design-direction.md (direction validated).

1. For each choice in the validated direction:
   - If entry exists in Tendencies → increment validated_count
   - If validated_count reaches 2 → move to Confirmed
   - If entry is new → add to Tendencies with validated_count: 1

2. For explicit rejections stated by the user during the session ("pas ça", "je veux pas X"):
   - Add to Explicit rejections immediately (no full validation required)

3. Session ends without reaching design-direction.md validation:
   - Discard all inferred preferences
   - Keep any explicit rejections stated during the session

## Tier promotion rule

No cross-project file scanning. The `validated_count` field accumulates across sessions within this single file. Promotion is purely counter-based: when validated_count reaches 2, move the entry from Tendencies to Confirmed at next update.
