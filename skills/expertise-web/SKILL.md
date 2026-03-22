---
name: expertise-web
version: 2026.03.1
last_updated: 2026-03-21
projects: [gtm-deeptech, setting-live, izaia]
description: "Use on ANY web project — always active in background. Abraham's accumulated web expertise: battle-tested components, content architecture, navigation patterns, maillage interne, SEO/GEO implementation, and technical patterns. Grows after every project. Triggers on: 'website', 'web app', 'landing page', 'components', 'navigation', 'maillage', 'content structure'."
---

# Expertise Web

## Relevance Check

**Pas un projet web ?** Ignore ce skill entièrement.

**Charge uniquement ce dont la tâche a besoin** — ne charge pas tout en bloc :

| Si la tâche est… | Charge |
|------------------|--------|
| Construire un composant UI | `reference/components.md` + `reference/protocols.md` |
| Planifier contenu / navigation | `reference/content-arch.md` |
| Implémentation framework (Next.js, etc.) | `reference/technical.md` |
| SEO / GEO / performance | `reference/geo-seo.md` |
| Site statique vanilla | `reference/static-patterns.md` |
| Chercher des références design | `reference/sources.md` |
| Détection de gap ou harvest | `reference/protocols.md` uniquement |

Si la tâche est purement conversationnelle (stratégie, pas de build), charge **aucun** fichier référence — les sections ci-dessous suffisent.

**Bundles nommés** — raccourcis pour les workflows multi-modules fréquents :

| Bundle | Modules | Quand |
|--------|---------|-------|
| `ui-harvest-loop` | `components.md` + `protocols.md` | Construction de composant UI + capture de leçon |
| `design-calibration` | skill `design-eye` + `sources.md` | Démarrage visuel d'un projet (avant tout code) |
| `seo-full` | `geo-seo.md` + skill `geo` | Session SEO/GEO complète |
| `static-build` | `static-patterns.md` + `technical.md` | Site statique avec un minimum de JS |

---

## Overview

Abraham's accumulated web expertise from real projects. Always active on web development work. Contains battle-tested patterns for interactive components, content architecture, navigation, SEO/GEO, and performance.

**Core principle:** This skill is a living document. Every project adds lessons. Examples compete — the best version wins. Nothing is theoretical; everything comes from production.

## CRITICAL: Always Invoke These Skills Too

- `design-eye` — FIRST, before any visual work on web projects. Check if `design-direction.md` exists; if not, invoke design-eye before proceeding with any visual decisions.
- `superpowers` — always (brainstorming, plans, verification, debug)
- `design-signature` — sister skill, always loaded alongside for visual decisions
- `humanizer` — when writing ANY visible text content
- `geo` — when doing ANY SEO, structured data, AI visibility, or search optimization work (replaces seo-audit + ai-seo + schema-markup — `geo` covers all three)
- `copywriting` — when writing marketing copy
- `content-strategy` — when planning content architecture

## GATE: Design Direction Required

**Before ANY visual work on a web project, check if `design-direction.md` exists in the project.**

- If it exists and has a `## Validation` section → read it. All visual decisions must respect the direction. If a pattern in this skill conflicts with the validated direction, **the direction wins**.
- If it does NOT exist → invoke `design-eye` first. Do NOT proceed with visual work until a validated direction exists.

This gate does not apply to purely technical work (accessibility fixes, performance optimizations, SEO) that does not affect validated aesthetics.

## NON-NEGOTIABLE Standards

**Universal rules. These apply to EVERY web project regardless of stack, framework, or context. The skill won't let you ship without them.**

| Standard | Rule | Why |
|----------|------|-----|
| **ARIA on all interactives** | `aria-expanded`, `aria-controls`, `aria-label`, `role` on buttons, accordions, modals, tabs | Screen readers. Legal compliance. Not optional. |
| **Focus visible everywhere** | `focus-visible:ring-2 focus-visible:ring-accent` on EVERY button, link, input | Keyboard users exist. They can't use your site without this. |
| **Touch targets 48px** | `min-h-[48px]` on ALL buttons and inputs. Not just padding — explicit min-height | WCAG. Fat fingers. Mobile is 60%+ of traffic. |
| **Twitter Card + OG** | Both `openGraph` AND `twitter` metadata on EVERY page | OG alone = suboptimal Twitter/X sharing. Always add both. |
| **Gap check before improvising** | Before generating any component without an internal pattern → load `reference/protocols.md` and trigger Gap Detection. Never build blind. | Avoids accumulating one-off code that never becomes a reusable lesson. |

> **Note:** `design-signature` inherits these standards. Its visual-specific non-negotiables (serif duo, grain, glassmorphism) are defined there, not here. This avoids duplication.

## Craft Conventions

**Our opinionated standards. Proven across multiple projects — follow them when the stack applies.**

| Convention | Rule | Why | Applies when |
|------------|------|-----|-------------|
| **Stagger animations** | `staggerChildren` on any list of 3+ items | Simultaneous entrance = cheap. Cascade = quality. | Using Framer Motion or any animation library |
| **GA4 after success only** | `gtag('event', ...)` fires AFTER `res.ok` confirmation, NEVER before | Avoids false conversions. | Using Google Analytics / any conversion tracking |
| **Lenis off on mobile** | Check `(hover: none)` before initializing | Mobile scroll is native and better. Lenis = jank on touch. | Using Lenis or any smooth scroll library |
| **Smooth scroll: desktop only** | Any custom scroll behavior must detect touch devices and bail out | Native mobile scroll has momentum, rubber-banding, accessibility. | Using any scroll override library |

## Reference Modules

Detailed patterns, code, and lessons are organized in `reference/` files. Load the relevant module for the task at hand:

| Module | Contents | When to load |
|--------|----------|-------------|
| `reference/components.md` | Offer Picker, ROI Calculator, FAQ Accordion, Calendly, Video Player, Scroll Reveal, Sticky Nav, Forms, Cursor | Building interactive components |
| `reference/content-arch.md` | Situation-based segmentation, Semantic Layers, Playbook pattern, Article fusion, Mega-menu, Internal linking | Planning content structure or navigation |
| `reference/technical.md` | Next.js App Router, Framer Motion, Tailwind config, Domain migration checklist | Framework-specific implementation |
| `reference/geo-seo.md` | robots.txt, llms.txt, JSON-LD, hreflang, Security headers, Accessibility standards, Performance, SEO technical | SEO/GEO, security, accessibility, performance |
| `reference/static-patterns.md` | Vanilla HTML, native `<details>`, mailto forms, scroll reveal, single-page landing, pricing tiers, blog patterns | Static sites without frameworks |
| `reference/sources.md` | 21st.dev, Navbar Gallery, Component Gallery, Landing.love, Saaspo — URLs, usage rules, ownership | Discovering components or design references |
| `reference/protocols.md` | Gap Detection (fires before building unknown components), Harvest (captures validated components into components.md) | Quand un composant est absent de components.md, OU quand l'utilisateur approuve ("c'est bon") |

## Launch Metrics Checklist

Capture BEFORE and AFTER for every project:

| Metric | Tool | Target |
|--------|------|--------|
| Lighthouse Performance | Chrome DevTools | > 90 |
| Lighthouse Accessibility | Chrome DevTools | > 95 |
| Largest Contentful Paint | PageSpeed Insights | < 2.5s |
| Cumulative Layout Shift | PageSpeed Insights | < 0.1 |
| Interaction to Next Paint | PageSpeed Insights | < 200ms |
| Mobile usability | Search Console | 0 errors |
| Schema validation | schema.org validator | 0 errors |
| Form conversion rate | GA4 (30 days post-launch) | baseline → delta |

**Rule:** Capture Lighthouse scores on launch day. Note them in the post-project review. If a score < target, document why (conscious trade-off vs oversight).

---

## Handoff Checklist

When handing code to a developer who doesn't use Claude or these skills, verify these 5 things:

1. **Accessibility audit** — run `npx lighthouse --only-categories=accessibility` and fix any score < 95. Check: all buttons have `aria-label` or visible text, all accordions have `aria-expanded`, all images have `alt`, all inputs have labels.
2. **Focus ring verification** — tab through the entire site with keyboard. Every interactive element must show a visible `focus-visible` ring. If any element is invisible when focused, it's a blocker.
3. **Touch target check** — inspect all buttons and links in mobile viewport. Anything with `height < 48px` or `width < 48px` on its clickable area fails. Use DevTools device toolbar.
4. **Responsive sweep** — check 3 breakpoints: 375px (mobile), 768px (tablet), 1280px (desktop). No horizontal scroll, no overlapping elements, no text overflow.
5. **SEO meta validation** — every page must have: `<title>`, `meta description`, `og:title`, `og:description`, `og:image`, `twitter:card`. Run `npx next-sitemap` to verify sitemap includes all pages.

**Optional but recommended:**
- Run PageSpeed Insights on the production URL
- Validate JSON-LD at https://validator.schema.org
- Check `robots.txt` and `llms.txt` exist and are correct

## Metrics Storage

Launch metrics are stored in the project's `design-direction.md` file, alongside the validated direction. This keeps everything in one place per project.

Add after `## Validation`:
```
## Launch Metrics — [date]
- Lighthouse Performance: [score]
- Lighthouse Accessibility: [score]
- LCP: [value]
- CLS: [value]
- INP: [value]
- Schema errors: [count]
- Notes: [any trade-offs or issues]
```

For subsequent measurements (post-optimization, post-redesign), add a new `## Metrics — [date]` section. The history stays in the file for comparison.

---

## Post-Project Review: Expertise

After each project, answer:
1. **New component?** → Add to `reference/components.md` with `**Source:**`, code, and lesson
2. **New pattern?** → Add in the right reference file
3. **Better version of existing example?** → Replace, note why
4. **Mistake discovered?** → Add as **CRITICAL** warning
5. **Non-negotiable violated?** → Fix in the project AND add to the Non-Negotiable table
6. **Strategy with measurable results?** → Document with metrics
7. **Lighthouse scores?** → Record in Launch Metrics section of the project's documentation

**Rule: examples compete.** Project 3's component replaces project 1's if it's better. Annotate proven ones with `(proven: N projects)`.

**Annotation format:** Every example has:
- `**Source:** [project] (date)` — traceability
- `**Lesson:**` or `**Lessons:**` — the transferable insight
- `(proven: N projects)` — once validated across multiple projects
