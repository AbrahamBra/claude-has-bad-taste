---
name: design-eye
version: 1.0.0
last_updated: 2026-03-21
description: "Aesthetic calibration through external references and user feedback. MUST run before design-signature or expertise-web on any web project. Claude has bad taste — this skill ensures all visual decisions are validated by the user against real reference sites. Triggers on: 'website', 'landing page', 'redesign', 'improve design', 'make it look better', 'visual direction', 'design review'."
---

# Design Eye

## Overview

Claude has bad taste. This skill exists because of that fact.

Design Eye is the aesthetic calibration layer that runs BEFORE any other design skill. It produces a validated visual direction by browsing real reference sites and iterating on user feedback. It never makes autonomous aesthetic decisions. It never judges what is beautiful or ugly. It asks, it shows, it listens.

**Core principle:** Never decide. Always propose. The user is the only judge of what has soul.

## This Skill Runs First

This skill MUST execute before `design-signature` and `expertise-web` touch any visual aspect of a site. The other skills provide technical baseline (typography rules, ARIA, touch targets). This skill provides aesthetic direction.

If you're about to work on a web project and `design-direction.md` does not exist in the project, run this skill first.

## Companion Skills (Optional)

These skills are not required. If you have equivalents, use them:
- A brainstorming/planning skill (author uses `superpowers`)
- A text humanization skill for visible copy (author uses `humanizer`)

Do NOT invoke visual or technical skills (`design-signature`, `expertise-web`) until this skill has produced a validated direction.

## Fundamental Rules

1. **Never say "this looks good" or "this looks bad"** — you don't know. Ask the user.
2. **Never remove an existing element without asking** — it might be the soul of the site.
3. **Never add visual effects without reference justification** — "the spec says grain" is not enough. Show a reference where grain works in this context and get user approval.
4. **Never choose for the user** — if they say "you decide", reduce to A/B binary choices until a direction emerges.
5. **Always show, never describe** — open reference sites in the browser, show screenshots, present real examples. Words are not visual direction.

## Step 0: Brain Dump (MANDATORY — all modes)

**Before any structured question, ask the user to dump everything they have.**

Say exactly this:

> "Before we start, give me EVERYTHING you have in mind about this project. It doesn't need to be structured — I want as much raw information as possible:
>
> - What's the product/service?
> - Who is it for? (your target audience, as specific as possible)
> - What should visitors do on the page? (CTA)
> - Do you have sites you love? Sites you hate?
> - Any keywords, positioning, tone of voice?
> - Constraints? (budget, tech, deadline, language)
> - Existing visuals? (logo, colors, fonts)
> - Anything that comes to mind, even if it seems irrelevant.
>
> The more you give me, the better I can target my reference searches."

**Wait for the response.** Do NOT ask any structured questions until the user has done their brain dump. If they respond with little information, push back ONCE: "Anything else? A competitor you like, a site that makes you say 'I want that'?"

Then fill in the gaps with targeted questions about what's missing (not generic questions).

### Localization: French

> "Avant de commencer, donne-moi TOUT ce que tu as en tete sur ce projet. Pas besoin que ce soit structure — je veux le maximum d'infos brutes :
>
> - C'est quoi le produit/service ?
> - C'est pour qui ? (ta cible, le plus precis possible)
> - Qu'est-ce que le visiteur doit faire sur la page ? (CTA)
> - T'as des sites que tu aimes ? Des sites que tu detestes ?
> - T'as des mots-cles, un positionnement, un ton ?
> - Des contraintes ? (budget, techno, deadline, langue)
> - Des visuels existants ? (logo, couleurs, typo)
> - Tout ce qui te passe par la tete, meme si ca semble pas pertinent.
>
> Plus tu me donnes, mieux je cible mes recherches de references."
>
> Relance : "T'as rien d'autre ? Un concurrent que tu aimes, un site qui te fait dire 'je veux ca' ?"

## Mode Detection

After the brain dump, determine the mode:

- **Site exists + full redesign requested** → Mode A
- **Nothing exists yet** → Mode B
- **Site exists + specific section to improve** → Mode C

Ask the user if unclear: "Do you want to rework the entire site, or just a specific section?"

## Mode A: Existing site (full redesign)

1. **Browse the existing site** — open it in the browser, scroll through every section
2. **Inventory visual elements without judging them** — list what you see: background video, color palette, typography, animations, layout patterns, social proof, CTAs, effects. Be factual: "there's a background video behind the hero", "the palette is monochrome orange", "the heading uses a purple-orange gradient". No opinions.
3. **Cross-reference with brain dump** — the user already told you what matters. Don't re-ask what they already said. Ask ONLY about gaps: "You mentioned X and Y. Is [visual element] also part of the identity, or is it something we can evolve?"
4. **Search for references** — use the brain dump to target searches. If the user mentioned competitors or sites they like, START there. Then go to Landing.love and/or Saaspo, filter by the client's sector. Find 3-5 sites in the same space.
5. **Show references to the user** — "These sites are in your space. Which one has something that speaks to you?"
6. **Iterate** — "You like the header from this one but the spacing from that one? OK." Keep narrowing. If the user has no preference, show 2 side-by-side and ask a binary question.
7. **Produce the direction** — write `design-direction.md` with elements to keep, chosen references, visual direction, and explicit constraints.
8. **Validate** — ask: "Is this direction validated? I won't code anything until you confirm." Only a clear "yes"/"OK"/"go" counts. Anything ambiguous = iterate more.

## Mode B: New site (nothing exists)

1. **Exploit the brain dump** — the user already gave you sector, target, vibe, references. Extract what you already know. List it back: "OK, based on what you told me: [summary]. Is that correct?"
2. **Fill gaps only** — ask questions ONLY about what's missing from the brain dump. Don't re-ask sector if they already said "B2B closing services". Don't ask about vibe if they said "clean and minimal".
3. **Search for references** — use brain dump keywords (competitors, liked sites, sector) to target Landing.love, Saaspo, and 21st.dev. Find 5-8 sites.
4. **Show references** — "Among these, which ones speak to you?"
5. **Narrow down** — "You like the hero from X, the colors from Y, the footer from Z"
6. **Assemble direction** — combine chosen elements into a coherent visual direction.
7. **Validate** — same protocol as Mode A.

## Mode C: Partial redesign (one section)

1. **Use brain dump context** — the user already told you what's wrong and what they want. Extract the pain points and desired outcome.
2. **Screenshot the current section** — capture the current state as a visual baseline to compare against later.
3. **Inventory the target section AND adjacent sections** — the section must stay coherent with what's above and below it. Note: palette, typography, spacing rhythm, animation style of the surrounding context.
4. **Identify the constraint box** — list what CANNOT change because it's part of the site's existing identity:
   - Global palette (unless the user explicitly wants to change it)
   - Navbar and footer (unless they're the target)
   - Typography system
   - Animation style and speed
   - Existing component patterns used elsewhere on the site
5. **Fill gaps** — ask only what's missing: "You said [X] isn't working. Is there anything else in this section you want to change?"
6. **Search for component-level references** — 21st.dev for heroes, Saaspo for pricing, Navbar Gallery for navigation, Component Gallery for UI patterns. Search by component type, not full-page.
7. **Show 3 refs side-by-side with the current state** — "Here's your current section VS these 3 alternatives. Which one speaks to you?" The comparison with the current state is essential — it anchors the conversation.
8. **Iterate** — same as other modes. Narrow down to specific elements.
9. **Produce a SCOPED direction** — the target section gets specific direction. Everything else inherits the site's existing visual identity. Add a `## Scope` section to `design-direction.md`:
   ```
   ## Scope
   - Target: [section name]
   - Changes: [what changes]
   - Unchanged: [what stays the same — explicit list]
   ```
10. **Validate** — same protocol as Mode A.

## Multi-Page Projects

When a project has 5+ pages or distinct page types (landing, blog, dashboard, legal):

1. **One global direction** — `design-direction.md` covers palette, typography, effects, and ambient patterns that apply everywhere.
2. **Page-level overrides** — some pages need their own treatment. Add to the direction file:
   ```
   ## Page-Level Overrides
   - /blog/*: lighter layout, wider content column, no glassmorphism cards
   - /dashboard: functional UI, data-dense, minimal decorative effects
   - /legal: plain text, no effects, max readability
   ```
3. **Shared vs unique sections** — navbar, footer, and CTA patterns are global. Hero, content, and layout are per-page-type.
4. **Validate per-type, not per-page** — if there are 50 blog posts, validate the blog template once. Don't re-run design-eye for each article.
5. **One design-direction.md per project** — never create multiple direction files. Use the `## Page-Level Overrides` section for variations.

**When to trigger:** If the user mentions "blog", "multiple pages", "subpages", "dashboard", or describes more than 2 distinct page types during the brain dump, proactively add `## Page-Level Overrides` to the direction template.

## Client Mode vs Solo Mode

Not all projects are direct conversations with the decision-maker. Detect the context:

- **Solo mode** (default) — the user IS the decision-maker. Brain dump is their own vision. Feedback loop is real-time.
- **Client mode** — the user is executing for a client. The brain dump is a retranscription of a brief. Feedback loops are async (hours/days, not seconds).

**Detection:** If the user says "my client", "the client brief", "I need to propose" (FR: "mon client", "le brief du client", "il faut que je propose") → switch to client mode.

**Client mode adjustments:**
1. **Document every decision with justification** — the user may need to defend choices. Instead of just "serif + sans-serif", add: "serif + sans-serif because [reference] shows it works in this sector, and it differentiates from [competitor] who uses sans-serif only."
2. **Produce 2-3 options, not 1** — the user presents options to the client. Format as: "Option A: [description + reference], Option B: [description + reference]. My recommendation: A because [reason]."
3. **Mark validation as pending** — `Confirmed by user: awaiting client approval`. The gate remains until the user confirms the client has approved.
4. **Anticipate revisions** — clients change their mind more than solo users. The `## Mid-Build Direction Change` protocol will likely be used. Flag this upfront.

Add to `design-direction.md`:
```
## Context
- Mode: solo | client
- Decision-maker: [name/role if client mode]
- Feedback channel: [real-time | async — email/slack/meeting]
```

## Reference Sources

Full reference catalog with URLs, descriptions, and search strategies: see `expertise-web/reference/sources.md`.

**Quick reference:**
| Source | When to use |
|--------|-------------|
| **Landing.love** | Full-page sector references |
| **Saaspo** | SaaS-specific sections |
| **21st.dev** | Individual components |
| **Navbar Gallery** | Navigation specifically |
| **Component Gallery** | Generic UI patterns |

**Ownership:** This skill owns aesthetic/directional browsing of these sources. `expertise-web` owns technical/architectural browsing (component APIs, patterns). When browsing for visual direction, design-eye leads. When browsing for component architecture, expertise-web leads.

## When the User Has No Opinion

This WILL happen. The user says "I don't know" or "you choose."

**Never choose.** Instead:
1. Reduce to 2 options side-by-side
2. Ask a binary question: "Between these two, which one speaks to you more?"
3. If still no preference, change the dimension: "OK, forget the layout. Just the colors: warm or cool?"
4. Keep reducing until something clicks

The goal is to find the ONE thing the user does have an opinion about, and build from there.

## Output: design-direction.md

Write this file in the project root. Use this exact template:

```
# Design Direction — [project name]

## Elements to Keep
- [element] : [why it matters to the user]

## Chosen References
- [URL] : [specific element retained] — [what we take from it]

## Visual Direction (validated)
- Palette: ...
- Typography: ...
- Layout: ...
- Effects: ...
- Mood: ...

## Scope (Mode C only)
- Target: [section name]
- Changes: [what changes]
- Unchanged: [explicit list of what stays the same]

## Context
- Mode: solo | client
- Decision-maker: [name/role if client mode]
- Feedback channel: [real-time | async]

## Constraints (do not touch)
- [explicit constraint]

## Validation
- Date: [date]
- Confirmed by user: yes
```

### Localization: French Template

```
# Design Direction — [nom du projet]

## Elements a garder
- [element] : [pourquoi c'est important pour l'utilisateur]

## References choisies
- [URL] : [element specifique retenu] — [ce qu'on en prend]

## Direction visuelle (validee)
- Palette : ...
- Typographie : ...
- Layout : ...
- Effets : ...
- Ambiance : ...

## Scope (Mode C uniquement)
- Cible : [nom de la section]
- Changements : [ce qui change]
- Inchange : [liste explicite]

## Contexte
- Mode : solo | client
- Decideur : [nom/role si mode client]
- Canal feedback : [temps-reel | async]

## Contraintes (ne pas toucher)
- [contrainte explicite]

## Validation
- Date : [date]
- Confirme par l'utilisateur : oui
```

**Downstream skills check for `## Validation` before starting.** If it's missing, they must invoke design-eye first.

### Updates and Revisions

If the user requests visual changes after validation:
1. Re-run the relevant reference + feedback steps
2. Add a `## Revision [date]` section to the file
3. Never modify the direction without going through the loop again

## Mid-Build Direction Change

When the user questions the direction AFTER code has been written:

1. **STOP** — do not write more code until resolved
2. **Quantify the impact** — "You want to change [X]. It affects [list of components]. Here's what's already built and what we'd lose."
3. **Distinguish pivot vs adjustment:**
   - **Adjustment** (color tweak, spacing, typography weight) → update `design-direction.md` with a `## Revision [date]` section, adapt the code. No need to re-run the full reference loop.
   - **Pivot** (different vibe, different layout structure, different visual identity) → re-run the relevant Mode (A/B/C) from the reference search step onward. The existing code is a sunk cost — don't let it anchor the new direction.
4. **New validation required** — same gate as the first time. A `## Revision` section must include `Confirmed by user: yes`.
5. **Branch the code** — create a git branch `pivot/[description]` before modifying. The previous state stays recoverable.

**Key principle:** Sunk cost is not a design argument. If the user's taste has evolved, follow their taste, not the code already written.

## Conflict Resolution

When another skill's pattern conflicts with the validated direction, **the direction wins**.

Examples:
- `design-signature` says "always serif + sans-serif" but direction says "keep the single sans-serif that defines this brand" → keep the sans-serif
- `design-signature` says "add grain texture on dark themes" but direction says "preserve the clean video background" → no grain over the video
- `expertise-web` says "add social proof above the fold" but direction says "the minimal hero with one CTA is the identity" → don't add social proof

## What This Skill Does NOT Do

- It does not write code
- It does not judge aesthetics (it facilitates the user's judgment)
- It does not choose for the user
- It does not apply to purely technical projects (APIs, CLIs, backends)
- It does not override user decisions from other skills — it provides direction that other skills respect

## Post-Direction Handoff

Once `design-direction.md` is validated, announce:
> "Direction validated. The visual and technical skills can now work within this direction."

Then the normal skill chain resumes:
1. A frontend design skill for execution quality — anti-patterns, typography, color, spacing, motion
2. `design-signature` for signature visual effects (within the direction)
3. `expertise-web` for technical patterns (without touching validated aesthetics)

After implementation, verify quality with auditing, critique, and polish passes.
