# Customization

## Adding Your Own Project Sources

After completing a project, add your patterns to the relevant files:

```markdown
### [Pattern Name] (proven: 1 project)
**Source:** your-project.com (2026-04)
**When:** [context]

[code example]

**Lesson:** [what you learned]
```

Over time, your skills become a living knowledge base of YOUR work, not just the original patterns.

## Modifying Non-Negotiable Standards

### expertise-web standards (universal)

These are in `expertise-web/SKILL.md` under `## NON-NEGOTIABLE Standards`:
- ARIA on all interactives
- Focus visible everywhere
- Touch targets 48px
- Twitter Card + OG

To modify: edit the table directly. But think twice before removing accessibility standards — they exist for legal and ethical reasons.

### design-signature standards (visual)

These are in `design-signature/SKILL.md` under `## NON-NEGOTIABLE Visual Standards`:
- Serif + Sans-serif duo
- Grain texture on dark themes
- Glassmorphism on cards

These are more opinionated. Feel free to modify based on your aesthetic preferences. Replace with your own signature effects.

## Adding Effects to the Signature

1. Add the effect to `design-signature/SKILL.md` with:
   - `**Source:** [project] (date)`
   - CSS/React code example
   - `**Lesson:**` with the transferable insight

2. Add a row to the `## Mobile Degradation Table` — every effect needs a mobile plan.

3. If the effect is theme-specific, add it to the appropriate section (dark or light/warm).

## Localizing Prompts

The brain dump prompt and direction template are the most important pieces to localize. They set the tone for the entire client interaction.

### Adding a new language

In `design-eye/SKILL.md`, after any client-facing prompt, add:

```markdown
### Localization: [Language]

> [Your translated prompt here]
```

Key prompts to localize:
- Step 0: Brain dump prompt
- Output: design-direction.md template headings
- Mode detection question
- Validation question

### Tips for localization
- Use informal register if your language supports it (tu vs vous, du vs Sie) — it helps clients open up
- Keep the structure identical to the English version
- The relance/follow-up prompt is important — don't skip it

## Removing Companion Skill References

The skills reference external skills (`superpowers`, `humanizer`, `frontend-design`, etc.) that you may not have. These are all optional.

To clean up:
1. Open each SKILL.md
2. Find the `## Companion Skills (Optional)` section
3. Remove or replace references with your own skills
4. If you have no equivalent, just remove the line — the skill works standalone

## Adapting for Different Tech Stacks

The code examples assume Next.js + React + Tailwind + Framer Motion. If you use a different stack:

- **Svelte/SvelteKit** — the patterns translate directly. Replace `useState` with `$state`, `AnimatePresence` with Svelte transitions.
- **Vue/Nuxt** — same patterns, different syntax. Replace React hooks with Vue composables.
- **Vanilla HTML** — see `expertise-web/reference/static-patterns.md` for framework-free versions of many patterns.
- **Other CSS** — the Tailwind classes map to standard CSS. The design tokens (colors, spacing, z-index) work in any system.
