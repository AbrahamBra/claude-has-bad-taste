# Architecture

## The 3-Layer Pipeline

```
User says "I want a website"
          │
          ▼
    ┌─────────────┐
    │  design-eye  │  Layer 1: DIRECTION
    │              │  - Brain dump
    │              │  - Reference browsing
    │              │  - User feedback loops
    │              │  - Binary choice reduction
    └──────┬──────┘
           │
           ▼
  design-direction.md  ◄── THE GATE
  (validated by user)      Nothing visual happens
           │               without this file
           ▼
    ┌──────────────────┐
    │ design-signature  │  Layer 2: VISUAL IDENTITY
    │                   │  - Glassmorphism, grain, glow
    │                   │  - Typography rules
    │                   │  - Dark/light theme patterns
    │                   │  - Mobile degradation
    └──────┬───────────┘
           │
           ▼
    ┌───────────────┐
    │ expertise-web  │  Layer 3: TECHNICAL QUALITY
    │                │  - Accessibility (ARIA, focus, touch)
    │                │  - SEO/GEO (robots.txt, llms.txt, JSON-LD)
    │                │  - Performance (lazy loading, dynamic imports)
    │                │  - Components (FAQ, forms, calculators)
    └───────────────┘
```

## The Gate: design-direction.md

The central mechanism is the **gate**: both `design-signature` and `expertise-web` check for a `design-direction.md` file with a `## Validation` section before doing any visual work.

- If the file exists and is validated → proceed, respecting the direction
- If the file does NOT exist → invoke `design-eye` first
- If the direction conflicts with a skill's default pattern → **the direction wins**

This prevents the most common AI design problem: Claude applying patterns mechanically without understanding what the site is supposed to feel like.

## Conflict Resolution

When skills disagree, the hierarchy is:
1. **User's explicit instructions** — always highest priority
2. **design-direction.md** — the validated aesthetic direction
3. **Skill patterns** — default behaviors from design-signature and expertise-web

Examples:
- design-signature says "always use serif + sans-serif" but the direction says "keep the single sans-serif that defines this brand" → keep the sans-serif
- expertise-web says "add social proof above the fold" but the direction says "the minimal hero is the identity" → don't add social proof

## Skill Ownership

Each skill owns specific domains:

| Domain | Owner | Others defer |
|--------|-------|-------------|
| Aesthetic direction | design-eye | design-signature, expertise-web |
| Visual effects | design-signature | expertise-web |
| Typography rules | design-signature | expertise-web (uses them) |
| Accessibility | expertise-web | design-signature (follows them) |
| SEO/GEO | expertise-web | — |
| Performance | expertise-web | — |
| Component architecture | expertise-web | design-signature (styles them) |
| Reference browsing (visual) | design-eye | expertise-web (technical) |
| Reference browsing (technical) | expertise-web | design-eye (visual) |

## Evolution

These skills grow after every project:
- New effects → add to design-signature with `**Source:** [project] (date)`
- New components → add to `expertise-web/reference/components.md`
- Better version of existing pattern → replace the old one
- Mistakes discovered → add `**CRITICAL**` warnings
- Examples compete — the best version wins, annotated with `(proven: N projects)`
