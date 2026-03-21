# Component Discovery & Reference Sources

> **Ownership:** When browsing for **visual direction** (palette, layout, vibe), `design-eye` leads.
> When browsing for **technical architecture** (component APIs, patterns, accessibility), `expertise-web` leads.

## 21st.dev — Component Marketplace
**URL:** https://21st.dev/community/components
**What:** Community-driven marketplace of copy-paste React components. Thousands of high-quality components published by designers and developers.
**Categories:** Hero sections, Features, Pricing, Testimonials, AI Chat, Calls to Action, Buttons, Text Components, Shaders/Visual Effects
**When to use:**
- Starting a new page section (hero, pricing, features) → browse for inspiration and proven layouts
- Need a specific interactive component → search before building from scratch
- Rapid prototyping → copy-paste components as starting points, then apply design-signature rules
**How to use:** Browse by Featured/Newest/Popular. Search by component type. Adapt to project palette and design-signature standards (glassmorphism, grain, serif+sans-serif, 48px touch targets).

## Navbar Gallery — Navigation Patterns
**URL:** https://www.navbar.gallery/
**What:** Curated collection of real-world navigation designs, scored by visitors. Created by Christina Liubynska to fill a gap in navigation-specific design resources.
**Pattern types:** Static/Sticky navbars, Dropdown/Flyout menus, Mega Menus, Sidebars, Search Bars, Announcement Bars, Full Screen Menus, Breadcrumbs
**When to use:**
- Designing navigation for ANY new site → browse for the right pattern before coding
- Client wants a specific nav style → find reference examples to validate the approach
- Choosing between mega-menu vs sidebar vs hamburger → compare real implementations
**How to use:** Each entry shows screenshots + icons indicating which patterns are used. Compare implementations across industries. Cross-reference with design-signature Glassmorphism Navbar patterns.

## Component Gallery — Design System Catalog
**URL:** https://component.gallery/design-systems/
**What:** Catalog of 100+ design systems from major organizations (Google Material, Shopify Polaris, IBM Carbon, Salesforce Lightning, GOV.UK, etc.).
**Filter by:** Platform (GitHub, Storybook, Figma), Technology (React, Vue, Angular, Web Components, Sass), Features (code examples, accessibility docs)
**When to use:**
- Evaluating component API design → study how Polaris/Carbon/Material structure props and variants
- Accessibility patterns → reference GOV.UK or US Web Design System for gold-standard a11y
- Building a reusable component library → learn from proven architecture decisions
- Need evidence-based best practices → see how established teams solve the same problem
**How to use:** Filter by technology (React: 51 systems) and features. Study component architecture, not just visuals. Extract accessibility patterns and API conventions.

## Landing.love — Animated Landing Page Showcase
**URL:** https://www.landing.love/
**What:** Curated showcase of 1963+ animated website designs with full-page video recordings. The go-to for seeing landing pages in motion, not just static screenshots.
**Categories:** Minimal (1313), Portfolio (517), Studio (493), Agency (341), AI, SaaS, Fashion, Real Estate, and dozens more
**Styles:** Dark Mode, Gradient, Retro, Light Mode
**Collections by tech:** GSAP, WebGL, Three.js
**Platforms:** Webflow, Framer, Wix Studio
**When to use:**
- Starting a new landing page → watch video recordings of similar industry sites for layout and flow inspiration
- Planning animations → browse GSAP/WebGL/Three.js collections for technique references
- Choosing a visual style → filter by Dark Mode, Gradient, Retro, etc.
- Pitching a design direction to a client → share specific examples as mood references
**How to use:** Filter by industry + style. Watch the video recordings (not just screenshots) to understand scroll behavior, transitions, and interaction patterns. Cross-reference with motion-design skill for implementation.

## Saaspo — SaaS Design Inspiration
**URL:** https://saaspo.com/
**What:** 1400+ curated SaaS landing pages and sections, updated daily. Free, no monetization. Upcoming components library.
**Section types:** Pricing pages, Features sections, Hero sections, Onboarding flows, AI SaaS pages
**Styles:** Dark Mode, Light Mode, and more
**When to use:**
- Building a SaaS landing page → browse category-specific inspiration (pricing, features, hero)
- Designing onboarding flows → study real user flows from sign-up to setup
- Need section-specific inspiration → filter by section type (121 features sections, 219 AI SaaS pages, etc.)
- Benchmarking against competitors → find similar SaaS sites for comparison
**How to use:** Filter by section type for targeted inspiration. Use for SaaS-specific patterns that general design galleries don't cover. Especially valuable for pricing page layouts and feature presentation patterns.

---

## Fallback Sources

If primary sources are unavailable (down, redesigned, paywalled):

| Primary | Fallback 1 | Fallback 2 | Notes |
|---------|-----------|-----------|-------|
| **Landing.love** | Awwwards (awwwards.com) | Mobbin (mobbin.com) | Awwwards = curated quality, Mobbin = real app screenshots |
| **Saaspo** | SaaS Landing Page (saaslandingpage.com) | Screenlane (screenlane.com) | Less curated but broader coverage |
| **21st.dev** | shadcn/ui (ui.shadcn.com) | Aceternity UI (ui.aceternity.com) | Copy-paste components, React-focused |
| **Navbar Gallery** | Dribbble search "navigation" | Land-book (land-book.com) | Less nav-specific but still useful |
| **Component Gallery** | Storybook showcase (storybook.js.org/showcase) | Adele (adele.uxpin.com) | Design system catalogs |

**Last resort:** Ask the user directly: "My usual sources aren't available. Do you have any sites you like that we could use as references?" The user's own references are always the best fallback.

---

## Usage Rules
1. **Always check references BEFORE building a new component type** — someone has likely solved it well
2. **Adapt, don't copy** — apply design-signature rules (glassmorphism, grain, serif duo, focus rings) to any reference
3. **21st.dev for specific components** (what does a good pricing section look like?)
4. **Navbar Gallery for navigation decisions** (should this site use a mega-menu or sidebar?)
5. **Component Gallery for architecture decisions** (how should this component API be structured?)
6. **Landing.love for full-page inspiration + animations** (how should this landing page flow and move?)
7. **Saaspo for SaaS-specific sections** (how do top SaaS companies present pricing/features/onboarding?)
8. **Document new discoveries** — if a reference site reveals a pattern worth adopting, add it to this skill with `**Source:** [reference] (date)`
