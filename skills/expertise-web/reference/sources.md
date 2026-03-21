# Component Discovery & Reference Sources

> **Ownership:** When browsing for **visual direction** (palette, layout, vibe), `design-eye` leads.
> When browsing for **technical architecture** (component APIs, patterns, accessibility), `expertise-web` leads.

---

## Full-Page Inspiration

Sites that show complete landing pages and websites. Use these when starting a project or pitching a direction to a client.

### Landing.love — Animated Landing Page Showcase
**URL:** https://www.landing.love/
**What:** 1963+ animated website designs with full-page VIDEO recordings. The only gallery where you see the page in motion, not just a screenshot. That's the key difference — you see how scroll, transitions, and micro-interactions actually feel.
**Categories:** Minimal (1313), Portfolio (517), Studio (493), Agency (341), AI, SaaS, Fashion, Real Estate, and dozens more
**Styles:** Dark Mode, Gradient, Retro, Light Mode
**Collections by tech:** GSAP, WebGL, Three.js
**When to use:**
- Starting a new landing page → watch video recordings for layout and flow inspiration
- Planning animations → browse GSAP/WebGL/Three.js collections for technique references
- Pitching a direction to a client → share specific examples as mood references
**How to use:** Filter by industry + style. WATCH the videos, don't just look at thumbnails. Scroll behavior and transitions are the real value here.

### Saaspo — SaaS Design Inspiration
**URL:** https://saaspo.com/
**What:** 1400+ curated SaaS landing pages and sections, updated daily. Free. The most valuable thing: you can filter by SECTION TYPE (hero, pricing, features, onboarding). No other gallery does this as well for SaaS.
**Section types:** Pricing pages, Features sections, Hero sections, Onboarding flows, AI SaaS pages
**When to use:**
- Building a SaaS landing page → browse by section type, not just full pages
- Need a pricing section layout → filter directly to pricing examples
- Benchmarking competitors → find similar SaaS sites side by side
**How to use:** Filter by section type first, then by style. Especially valuable for pricing and feature sections — the two hardest sections to get right.

### Landingfolio — Landing Pages + Component Library
**URL:** https://www.landingfolio.com/
**What:** 4650+ landing page components AND full-page examples. The dual nature is what makes it special: you see both the big picture (full pages) and the building blocks (individual sections). Includes Tailwind and Webflow code for some components.
**When to use:**
- Need a specific section with code → Landingfolio often has Tailwind snippets ready
- Exploring layouts before committing → browse full pages, then zoom into the section you like
- Client presentations → the component-level screenshots are clean and easy to share
**How to use:** Start with full page inspiration, then drill into components. Check if Tailwind code is available before building from scratch.

### Land-book — Cross-Industry Landing Pages
**URL:** https://land-book.com/
**What:** Landing pages sorted by industry, color palette, and layout theme. Where Landing.love is animation-focused, Land-book is LAYOUT-focused. Great for finding structure patterns across industries that aren't SaaS.
**When to use:**
- Non-SaaS projects (real estate, finance, healthcare, education) where Saaspo doesn't help
- Color palette exploration → filter by palette to find sites that use similar colors
- Layout patterns → how do professional service sites structure their story?
**How to use:** Filter by industry first. The color palette filter is underrated — use it when the client says "I like blue" and you need to show them what "blue" looks like across 20 sites.

### PureLanding — Daily Fresh Inspiration
**URL:** https://purelanding.page/
**What:** One carefully selected landing page per day. No noise, no infinite scrolling through mediocre sites. Think of it as a daily design pill rather than a library.
**When to use:**
- Daily design diet → check it each morning to stay sharp
- Quick inspiration when you're stuck → today's pick might unlock your thinking
- Sharing with clients → "look at this landing page from today" feels more curated than a gallery link
**How to use:** Subscribe or check daily. The value is curation quality, not quantity.

---

## Copy-Paste Components

Sites where you grab individual components (buttons, cards, heroes) with working code. Use these DURING implementation, not just for inspiration.

### 21st.dev — Community Component Marketplace
**URL:** https://21st.dev/community/components
**What:** Community-driven marketplace of React components you can copy-paste. The difference from shadcn: components here are DESIGNED, not just functional. They come from designers who care about aesthetics, not just developers who care about APIs.
**Categories:** Hero sections, Features, Pricing, Testimonials, AI Chat, Calls to Action, Buttons, Text Components, Shaders/Visual Effects
**When to use:**
- Starting a new page section → search by component type before building from scratch
- Rapid prototyping → copy-paste as starting point, then apply design-signature rules
- Need visual "wow factor" → browse shaders and visual effects
**How to use:** Browse by Featured/Newest/Popular. Always adapt to your palette and standards (glassmorphism, grain, serif duo, 48px touch targets).

### shadcn/ui — The Standard React Component Library
**URL:** https://ui.shadcn.com/
**What:** 66k+ GitHub stars. THE copy-paste React component library. You don't install it — you copy component code into your project and own it completely. Built on Radix UI (accessible primitives) + Tailwind CSS. Every component is accessible by default.
**When to use:**
- Building ANY React UI → check shadcn first for the base component
- Need accessible form controls, dialogs, dropdowns → shadcn has them with proper ARIA
- Want a component system that respects your design tokens → it uses CSS variables you control
**How to use:** Copy the component, then style it. shadcn gives you structure and accessibility; you add the visual identity from design-signature. Think of it as the skeleton that you dress up.

### Aceternity UI — Premium Animated Components
**URL:** https://ui.aceternity.com/
**What:** React + Tailwind components with built-in animations that look expensive. Bento grids, parallax sections, text reveal effects, background beams, spotlight effects. Where shadcn is functional, Aceternity is theatrical.
**When to use:**
- Need a hero section that makes people stop scrolling → browse their hero components
- Building a portfolio or agency site where "wow" matters → bento grids, 3D cards
- Adding animation to an existing component → grab just the animation pattern
**How to use:** Don't use everything — pick 1-2 effects per project. Overusing Aceternity makes your site look like every other dev who discovered it. Apply the design-eye principle: choose effects that serve the direction, not effects that look cool.

### Magic UI — Landing Page Animations
**URL:** https://magicui.design/
**What:** Animated components specifically designed for landing pages: number counters, marquee scrolls, text reveal animations, gradient backgrounds. Smaller library than Aceternity but more focused on landing page needs.
**When to use:**
- Need a specific landing page animation (counter, marquee, text reveal)
- Building a stats/metrics section → their animated counters are excellent
- Want subtle background animations → gradient meshes, dot patterns
**How to use:** Use alongside shadcn (Magic UI for animation, shadcn for structure). Most components are drop-in — no complex configuration needed.

### HeroUI — Accessible React Components
**URL:** https://heroui.com/
**What:** Previously NextUI. Full-featured React component library focused on accessibility and developer experience. Think of it as an alternative to shadcn with more opinionated styling out of the box.
**When to use:**
- Want a component library that looks good without much customization
- Building a dashboard or app UI (not just a landing page) → HeroUI has data tables, date pickers, etc.
- Need components that work well together as a system → more cohesive than mixing shadcn + random components
**How to use:** Better for app-like interfaces than marketing sites. If you're building a dashboard, start here. If you're building a landing page, start with shadcn + Aceternity.

### Hover.dev — Hover-First Animated Components
**URL:** https://hover.dev/
**What:** React components where the hover interaction is the star. Buttons that morph, cards that tilt, links that animate. Every component is built around its hover state.
**When to use:**
- Designing CTAs → browse their button hover effects
- Need card hover interactions → 3D tilt, reveal, scale effects
- Building a portfolio or showcase → hover states make browsing feel premium
**How to use:** Desktop-focused by nature (no hover on mobile). Always pair with design-signature's mobile degradation table — use `active:scale-[0.98]` as the mobile equivalent.

---

## Micro-Interactions & Animation Inspiration

Not component libraries — inspiration galleries where you see WHAT to build, then implement it yourself.

### Design Spells — Micro-Interaction Gallery
**URL:** https://designspells.com/
**What:** Bi-weekly gallery of micro-interactions, easter eggs, skeuomorphic animations, and delightful details from real products. The focus is on the SMALL things that make a UI feel alive: how a toggle switches, how a notification appears, how a button confirms an action.
**When to use:**
- Polishing an existing UI → find the small touches that elevate it
- Looking for "delight" moments → easter eggs, confetti, satisfying animations
- Justifying micro-interaction work to a client → "here's how Stripe/Linear/Notion does it"
**How to use:** Browse for the TYPE of interaction you need (toggle, button, notification, loading). Recreate the feel, not the exact implementation.

### CodeMyUI — Snippets with Code
**URL:** https://codemyui.com/
**What:** CSS/JS interaction snippets with working code on CodePen. Where Design Spells shows you WHAT, CodeMyUI shows you HOW. Every example has a live demo and source code.
**When to use:**
- Found an interaction you like → search CodeMyUI for a similar implementation
- Need a specific CSS animation → browse by tag (hover, scroll, loading, text)
- Learning new techniques → the code is readable and well-organized
**How to use:** Search by tag, then open the CodePen. Copy the core technique, not the full snippet — adapt it to your stack and design system.

### Codrops — Advanced Web Effects Tutorials
**URL:** https://tympanus.net/codrops/
**What:** Tutorials and demos of advanced web effects: shaders, scroll-driven animations, WebGL experiments, creative layouts. This is where you go when you want something that makes people ask "how did they do that?"
**When to use:**
- Client wants something genuinely unique → browse Codrops for techniques nobody else uses
- Learning WebGL/GSAP/scroll-driven animations → their tutorials are the best on the web
- Building a portfolio or agency site where creativity is the product
**How to use:** Browse the demos first. If an effect fits your direction, read the tutorial. These are advanced — budget extra time. Not everything here is production-ready or performant on mobile.

---

## Navigation Patterns

### Navbar Gallery — Navigation-Specific Designs
**URL:** https://www.navbar.gallery/
**What:** The only gallery dedicated exclusively to navigation. Scored by visitors. Every entry shows which patterns are used (sticky, dropdown, mega-menu, sidebar, etc.) via icons.
**Pattern types:** Static/Sticky navbars, Dropdown/Flyout menus, Mega Menus, Sidebars, Search Bars, Announcement Bars, Full Screen Menus, Breadcrumbs
**When to use:**
- Designing navigation for ANY new site → browse before coding
- Choosing between mega-menu vs sidebar vs hamburger → compare real implementations
**How to use:** Compare across industries. The scoring system helps identify what users actually find effective, not just what designers think looks good.

---

## Design Systems & UI Patterns

Reference sources for HOW to structure components, not how they look. Use these for architecture decisions, accessibility patterns, and API design.

### Component Gallery — Design System Catalog
**URL:** https://component.gallery/design-systems/
**What:** 100+ design systems from major organizations (Google Material, Shopify Polaris, IBM Carbon, GOV.UK). The value is not copying their look — it's studying how they STRUCTURE their components: props, variants, accessibility, documentation.
**Filter by:** Platform (GitHub, Storybook, Figma), Technology (React, Vue, Angular), Features (code examples, accessibility docs)
**When to use:**
- Designing a component API → study how Polaris/Carbon structure props
- Accessibility patterns → GOV.UK and US Web Design System are gold standard
- Building a reusable library → learn from proven architecture
**How to use:** Filter by technology, then by features. Study architecture, not visuals.

### Collect UI — UI Pattern Library
**URL:** https://collectui.com/
**What:** UI inspiration sorted by pattern type: login forms, pricing tables, 404 pages, onboarding flows, settings screens, profiles. Every design problem has its own category. Where other galleries sort by industry, Collect UI sorts by WHAT the component does.
**When to use:**
- "How do other people design a [settings page / 404 / pricing table]?" → go straight to the category
- Stuck on a specific UI problem → browse 50 different solutions to the same problem
- Exploring edge cases → categories like "not found", "empty state", "loading" that other galleries ignore
**How to use:** Go directly to the category you need. The breadth is the value — seeing 50 pricing tables teaches you more than seeing 5.

### Mobbin — Real App Screenshots
**URL:** https://mobbin.com/
**What:** Screenshots from real mobile and web apps, organized by flow (onboarding, checkout, search, settings). The difference from other galleries: these are ACTUAL apps people use, not designed concepts. You see how Notion, Linear, Figma, Stripe actually solve UI problems.
**When to use:**
- Need to design a flow that exists in other apps → see how the best do it
- Mobile-first design → Mobbin's mobile coverage is unmatched
- Justifying design decisions → "here's how Stripe handles this exact flow"
**How to use:** Search by app name or flow type. Free tier has limits — worth the paid version if you design frequently.

### TOOOLS.design — Meta-Directory of Design Tools
**URL:** https://www.toools.design/
**What:** Not a design gallery — a directory of 1500+ design tools and resources, categorized. Think of it as "the index of everything else." When you need a tool for a specific job (color palette generator, font pairing tool, icon library, illustration pack), start here.
**When to use:**
- Looking for a tool you don't know exists → browse categories
- Need a font pairing tool → TOOOLS lists them all
- Exploring the design tool ecosystem → stay up to date on new resources
**How to use:** Browse by category. Bookmark the tools you use. Check back monthly for new additions.

---

## Fallback Sources

If primary sources are unavailable (down, redesigned, paywalled):

| Primary | Fallback 1 | Fallback 2 |
|---------|-----------|-----------|
| **Landing.love** | Awwwards (awwwards.com) | Land-book (land-book.com) |
| **Saaspo** | Landingfolio (landingfolio.com) | SaaS Landing Page (saaslandingpage.com) |
| **21st.dev** | shadcn/ui (ui.shadcn.com) | Aceternity UI (ui.aceternity.com) |
| **Navbar Gallery** | Dribbble search "navigation" | Land-book (land-book.com) |
| **Component Gallery** | Storybook showcase (storybook.js.org/showcase) | Adele (adele.uxpin.com) |
| **Mobbin** | Screenlane (screenlane.com) | Page Flows (pageflows.com) |

**Last resort:** Ask the user directly: "My usual sources aren't available. Do you have any sites you like that we could use as references?" The user's own references are always the best fallback.

---

## Usage Rules

### Which source for which question?

| Question | Go to |
|----------|-------|
| "What should this landing page look and FEEL like?" | Landing.love (video), Land-book (layout) |
| "What should this SaaS section look like?" | Saaspo, Landingfolio |
| "I need a ready-made React component" | shadcn/ui (functional), 21st.dev (designed), Aceternity (animated) |
| "How should this navigation work?" | Navbar Gallery |
| "How do real apps solve this UX problem?" | Mobbin, Collect UI |
| "I want a micro-interaction idea" | Design Spells (inspiration), CodeMyUI (with code) |
| "I want something technically impressive" | Codrops, Aceternity |
| "How should I structure this component's API?" | Component Gallery |
| "What hover effect should this button have?" | Hover.dev |
| "I need a landing page animation (counter, marquee)" | Magic UI |
| "Is there a tool for [specific need]?" | TOOOLS.design |
| "What's trending / fresh today?" | PureLanding (daily pick) |

### General rules
1. **Always check references BEFORE building** — someone has likely solved it
2. **Adapt, don't copy** — apply your design-signature rules to any reference
3. **Inspiration sources (Design Spells, Landing.love) → then code sources (shadcn, CodeMyUI)** — see WHAT first, then figure out HOW
4. **Document new discoveries** — if a reference reveals a pattern worth adopting, add it with `**Source:** [reference] (date)`
