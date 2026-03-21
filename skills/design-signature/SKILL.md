---
name: design-signature
version: 1.0.0
description: "Use when creating any website, landing page, or visual component. Contains signature visual effects, typography rules, and adaptive theming with real code examples from past projects. Triggers on: 'create a site', 'build a page', 'design', 'visual style', 'colors', 'animations', 'typography'."
---

# Design Signature

## Overview

Your visual DNA for web projects. Not a template — a set of proven effects, patterns, and taste that adapt to any sector while maintaining premium quality. Every example comes from a real project and evolves over time.

**Core principle:** The visual identity adapts to the client. The quality standard never drops.

## Companion Skills (Optional)
These skills are not required. If you have equivalents, use them:
- `design-eye` — FIRST, before any visual work. Produces the validated design direction.
- A brainstorming/planning skill (author uses `superpowers`)
- A text humanization skill for visible copy (author uses `humanizer`)
- A frontend component quality skill (author uses `frontend-design`)
- A motion design skill for animations (author uses `motion-design`)
- `expertise-web` — sister skill, always loaded alongside

## GATE: Design Direction Required

**Before ANY visual work, check if `design-direction.md` exists in the project.**

- If it exists and has a `## Validation` section → read it. All visual decisions below must respect the constraints and direction in that file. If a pattern in this skill conflicts with the validated direction, **the direction wins**.
- If it does NOT exist → invoke `design-eye` first. Do NOT proceed with New Project Discovery until a validated direction exists.

This gate exists because this skill applied mechanically destroys the soul of existing sites. The direction file ensures we know what to preserve and what to improve before applying any pattern.

## New Project Discovery

**Only run this AFTER design-eye has produced a validated `design-direction.md`. Use this section to complement the direction with technical details (palette generation, z-index system, etc.).**

When starting a new website, ask these 3 questions BEFORE any design work:

1. **Sector?** (tech, deeptech, real estate (immobilier), healthcare (sante), finance, manufacturing (industrie)...)
2. **Vibe?** (luxe sombre, corporate lumineux, tech moderne, chaleureux, minimaliste)
3. **Primary color?** (or suggest based on sector + vibe)

Then generate:
- **Palette:** accent, accent-hover (-10% lightness), accent-light (+15%), background, text, muted (gray range), + semantic colors if needed
- **Typography duo:** serif for headlines + sans-serif for body (reference: Instrument Serif + IBM Plex Sans) — UNLESS the design direction specifies otherwise
- **Which effects to use** (not all projects need all effects — the vibe AND the design direction decide)
- **Z-index system:** define all layers upfront (see Z-Index Management below)

## NON-NEGOTIABLE Visual Standards

**Visual-specific rules. Universal standards (ARIA, touch 48px, focus ring, OG+Twitter) are owned by `expertise-web` and always apply alongside these.**

| Standard | Rule | Why |
|----------|------|-----|
| **Serif + Sans-serif** | Always import a serif font for titles | Sans-only = generic. The duo creates visual hierarchy instantly |
| **Grain texture** | Always add SVG grain overlay on dark themes | Eliminates "flat digital" feel. Costs nothing performance-wise |
| **Glassmorphism on cards** | Use `backdrop-filter` + `mask-composite` gradient borders on all card components | Flat cards = amateur. Glass = premium. Even subtle glass makes a difference |

## Signature Effects

### Glassmorphism Cards (proven: 2 projects)
**Source:** gtm-deeptech.io (2026-02), setting.live (2026-03)
**When:** ALL projects with dark themes. Adapt opacity for lighter vibes.

```css
.card {
  background: linear-gradient(135deg, rgba(255,255,255,0.04) 0%, rgba(255,255,255,0.01) 100%);
  border: 1px solid rgba(255, 255, 255, 0.08);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
}

/* Gradient border — no extra DOM element */
.card::before {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: inherit;
  padding: 1px;
  background: linear-gradient(135deg, rgba(255,255,255,0.1) 0%, transparent 50%);
  -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
  mask-composite: exclude;
  pointer-events: none;
}
```

**Color-tinted variant** (for offer cards, per-section accents):
```tsx
// React: tint the gradient border with the section color
<div
  className="absolute inset-0 rounded-xl pointer-events-none"
  style={{
    background: `linear-gradient(135deg, ${sectionColor}30 0%, transparent 50%)`,
    mask: 'linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0)',
    WebkitMask: 'linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0)',
    maskComposite: 'exclude',
    WebkitMaskComposite: 'xor',
    padding: '1px',
  }}
/>
```

**Lesson:** `mask-composite: exclude` for gradient borders. Zero extra DOM, pure CSS. Add color-tinted glow dots (`boxShadow: 0 0 12px ${color}60`) for accent points.

### Button Glow with Elevation + Focus (proven: 2 projects)
**Source:** gtm-deeptech.io (2026-02), setting.live (2026-03)
**When:** Primary CTAs. Adapt color to project accent.

```tsx
// React component with MANDATORY focus ring
<button
  className="relative inline-flex items-center justify-center px-7 py-3.5 rounded-xl
             font-sans font-semibold text-white overflow-hidden min-h-[48px]
             transition-all duration-300
             focus-visible:ring-2 focus-visible:ring-accent focus-visible:ring-offset-2
             focus-visible:ring-offset-bg-primary"
  style={{
    background: 'linear-gradient(135deg, var(--accent) 0%, var(--accent-hover) 100%)',
    boxShadow: '0 2px 16px rgba(var(--accent-rgb),0.32), 0 1px 4px rgba(var(--accent-rgb),0.18)',
  }}
  onMouseEnter={(e) => {
    e.currentTarget.style.transform = 'translateY(-3px)'
    e.currentTarget.style.boxShadow =
      '0 6px 24px rgba(var(--accent-rgb),0.45), 0 2px 8px rgba(var(--accent-rgb),0.25), 0 12px 32px -8px rgba(var(--accent-rgb),0.30)'
  }}
  onMouseLeave={(e) => {
    e.currentTarget.style.transform = 'translateY(0)'
    e.currentTarget.style.boxShadow =
      '0 2px 16px rgba(var(--accent-rgb),0.32), 0 1px 4px rgba(var(--accent-rgb),0.18)'
  }}
>
  {/* Shine overlay */}
  <span aria-hidden="true" className="absolute inset-0 pointer-events-none"
    style={{ background: 'linear-gradient(to right, transparent 0%, rgba(255,255,255,0.06) 50%, transparent 100%)', animation: 'shine 8s infinite', transform: 'rotate(30deg)' }}
  />
  <span className="relative z-10">{children}</span>
</button>
```

**Lessons:**
- Stack 2-3 box-shadows at different blur/spread for depth
- Always `translateY(-3px)` on hover
- **CRITICAL:** `focus-visible:ring-2 focus-visible:ring-accent` on EVERY interactive element
- `min-h-[48px]` for touch target compliance
- Shine animation built into the button, not a separate component

### Shine Animation
**Source:** gtm-deeptech.io (2026-02)
**When:** Buttons, cards, premium elements. Subtle = premium.

```css
@keyframes shine {
  0% { transform: rotate(30deg) translateX(-100%); }
  100% { transform: rotate(30deg) translateX(200%); }
}
.shine::after {
  animation: shine 8s infinite;
  background: linear-gradient(to right, transparent 0%, rgba(255,255,255,0.03) 50%, transparent 100%);
}
```
**Lesson:** 8-10s duration = imperceptible but rich. Rotate 30deg for diagonal. Opacity 0.03 max.

### Cursor Glow (Desktop Only)
**Source:** gtm-deeptech.io (2026-02), setting.live (2026-03)
**When:** Dark themes. Skip for mobile and corporate.

```typescript
// ALWAYS throttle mousemove with requestAnimationFrame
// ALWAYS check for touch device and disable
const isTouchDevice = window.matchMedia('(hover: none)').matches
if (isTouchDevice) return // Exit early — no cursor on mobile

let rafId: number | null = null
const handleMouseMove = (e: MouseEvent) => {
  lastX = e.clientX; lastY = e.clientY
  if (!rafId) {
    rafId = requestAnimationFrame(() => {
      updatePosition(lastX, lastY)
      rafId = null
    })
  }
}
```
**Lesson:** Never update DOM on every mousemove. RAF batching = 60fps. Detect mobile with `(hover: none)` and disable entirely.

### Grain Texture (proven: 3 projects)
**Source:** gtm-deeptech.io (2026-02), setting.live (2026-03), IzaIA (2026-03)
**CRITICAL:** Always implement on dark themes. Define `--z-grain` AND use it.

```tsx
// React component — add to layout, NEVER forget
function GrainOverlay() {
  return (
    <svg
      className="fixed inset-0 w-full h-full pointer-events-none select-none"
      style={{ zIndex: 'var(--z-grain)', opacity: 0.018 }}
      aria-hidden="true"
    >
      <filter id="grain">
        <feTurbulence type="fractalNoise" baseFrequency="0.65" numOctaves="3" stitchTiles="stitch" />
      </filter>
      <rect width="100%" height="100%" filter="url(#grain)" />
    </svg>
  )
}
```
**Lesson:** Opacity 1.5-2% max. Fixed position, `pointer-events: none`, `aria-hidden="true"`. Add `stitchTiles="stitch"` for seamless tiling. **Always add to layout — never define the z-index variable without using it.**

### Rotating Persona Text with Blur
**Source:** setting.live (2026-03)
**When:** Hero sections targeting multiple personas. Creates dynamism without being distracting.

```tsx
// Adapt to your target personas — FR: consultants, fondateurs, independants B2B
const personas = ['consultants', 'founders', 'B2B freelancers']
const [index, setIndex] = useState(0)

useEffect(() => {
  const interval = setInterval(() => setIndex((i) => (i + 1) % personas.length), 2500)
  return () => clearInterval(interval)
}, [])

// Fixed-width container prevents layout shift
<span className="relative inline-block w-[195px] h-6">
  <AnimatePresence mode="wait">
    <motion.span
      key={personas[index]}
      initial={{ opacity: 0, filter: 'blur(8px)' }}
      animate={{ opacity: 1, filter: 'blur(0px)' }}
      exit={{ opacity: 0, filter: 'blur(8px)' }}
      transition={{ duration: 0.4, ease: [0.16, 1, 0.3, 1] }}
      className="absolute inset-0 flex items-center justify-center text-accent font-semibold"
    >
      {personas[index]}
    </motion.span>
  </AnimatePresence>
</span>
```

**Lessons:**
- `filter: blur(8px)` on enter/exit = premium feel vs simple fade
- Fixed-width container (`w-[195px]`) = no layout shift during rotation
- 2500ms interval = readable but dynamic
- `mode="wait"` on AnimatePresence = clean transition, no overlap

## Typography Rules

| Rule | Value |
|------|-------|
| **Duo** | ALWAYS serif (titles) + sans-serif (body). No exceptions. |
| **Reference pairs** | Instrument Serif + Inter, Playfair Display + IBM Plex Sans, Cormorant + Inter |
| **Import** | Both fonts in `layout.tsx` via `next/font/google` with `display: 'swap'` and CSS variables |
| **Line-height** | 1.6-1.7 for body. Text must BREATHE |
| **Hierarchy** | Size AND weight. Display 4.5rem > H1 3.5rem > H2 2.5rem |
| **Spacing** | Generous. Sections 80-120px. Content padding 10% sides (min px-8 on mobile) |

### Fluid Typography with clamp() (proven: 2 projects)
**Source:** setting.live (2026-03), IzaIA (2026-03)
**CRITICAL:** Use `clamp()` instead of fixed sizes. Responsive without media queries.

```typescript
// In tailwind.config.ts
fontSize: {
  'display': ['clamp(2rem, 5vw, 2.5rem)', { lineHeight: '1.1', fontWeight: '800', letterSpacing: '-0.04em' }],
  'h1': ['clamp(1.75rem, 4vw, 2.25rem)', { lineHeight: '1.15', fontWeight: '800', letterSpacing: '-0.025em' }],
  'h2': ['clamp(1.375rem, 3vw, 1.75rem)', { lineHeight: '1.2', fontWeight: '700', letterSpacing: '-0.015em' }],
  'h3': ['clamp(1rem, 2vw, 1.125rem)', { lineHeight: '1.3', fontWeight: '600' }],
}
```

**Lesson:** `clamp(min, preferred, max)` — scales between min/max across viewports. Negative `letterSpacing` on large text = tighter, more premium. Always pair with explicit `lineHeight` and `fontWeight`.

## Ambient & Layout

### Radial Gradient Background
**Source:** setting.live (2026-03)
**When:** Dark themes. Applied at `<html>` level, NOT body.

```css
@layer base {
  html {
    background: radial-gradient(ellipse at 50% 0%, rgba(var(--accent-rgb), 0.10) 0%, var(--bg-primary) 55%)
      no-repeat top center / 100% 700px, var(--bg-primary);
  }
}
```

**Lesson:** The gradient creates a warm "spotlight" at the top. 10% opacity of accent color. Size limited to 700px height — doesn't cover the whole page, just the hero zone.

### Z-Index Management System
**Source:** setting.live (2026-03)
**CRITICAL:** Define ALL z-index values as CSS variables in `:root`. Never use arbitrary numbers.

```css
:root {
  --z-base: 0;
  --z-card: 10;
  --z-phase-nav: 40;     /* Sticky sub-nav, below main navbar */
  --z-navbar: 50;
  --z-modal-backdrop: 80;
  --z-modal: 90;
  --z-grain: 9998;        /* Above everything, decorative */
  --z-cursor: 9999;       /* Always on top */
}
```

**Usage:** `z-[var(--z-navbar)]` in Tailwind or `zIndex: 'var(--z-navbar)'` in styles.

**Lesson:** Arbitrary z-index (`z-50`, `z-[100]`) creates conflicts on large projects. Named layers = self-documenting, conflict-free.

### Semantic Color Palette
**Source:** setting.live (2026-03)
**When:** Projects with educational/informational content that needs color-coded categories.

```typescript
// Tailwind config: brand colors + semantic layers
colors: {
  // Brand
  accent: '#C87533',
  'accent-hover': '#A85E28',
  'accent-light': '#D4956A',
  'bg-primary': '#0A0908',
  'bg-secondary': '#141210',
  'text-primary': '#F0ECE4',
  'text-secondary': '#A8A090',
  'text-muted': '#6B6560',

  // Semantic layers (independent from brand)
  'semantic-ia': '#A78BFA',         // Purple — AI/automation
  'semantic-methode': '#FBBF24',    // Amber — methodology
  'semantic-humain': '#34D399',     // Teal — human judgment
  'semantic-hybrid': '#C084FC',     // Light purple — AI + human
}
```

**Lesson:** Semantic colors are independent from the brand palette. They can be reused across projects. Always use `opacity` variants (`bg-semantic-ia/10`, `border-semantic-ia/20`) for backgrounds and borders.

## Video Player (v3 Reference)
**Source:** gtm-deeptech.io (2026-02) — 3 iterations, v3 is the reference
**When:** Hero product demos, testimonials, case studies.

Features: play/pause, stop, mute, fullscreen, speed (1x/1.25x/1.5x/2x), clickable scrubber.

```typescript
// Scrubber: minimal by default, detailed on hover
<div className="flex-1 group/scrubber cursor-pointer">
  <div className="h-[2px] group-hover/scrubber:h-1 bg-blanc/20 transition-all">
    <div className="h-full bg-accent" style={{ width: `${progress}%` }} />
    <div className="w-3 h-3 bg-blanc opacity-0 group-hover/scrubber:opacity-100" />
  </div>
</div>
```
**Lesson:** `:group-hover` for progressive disclosure. Default = clean, hover = detailed.

---

## Light / Warm Theme Patterns

### Warm B2B Palette (proven: 1 project)
**Source:** IzaIA / izaia.fr (2026-03)
**When:** Professional services, B2B training, regulated industries. Warm = trustworthy + human.

```css
:root {
  --cream: #FDFAF6;          /* Background — warmer than white */
  --accent: #C2410C;          /* Rust orange — authoritative, not corporate blue */
  --accent-rgb: 194, 65, 12;  /* For rgba() variants */
  --text: #1C1917;            /* Dark brown — softer than pure black */
  --muted: #78716C;           /* Warm gray — not cold */
  --border: rgba(28, 25, 23, 0.1);  /* Barely visible, warm */
}
```

**Lessons:**
- Cream (#FDFAF6) > pure white for professional warmth — easier on the eyes
- Rust orange > corporate blue for differentiation — stands out in B2B
- Dark brown text > pure black — less harsh, more human
- Store accent as RGB for easy rgba() variants: `rgba(var(--accent-rgb), 0.1)` for backgrounds
- This palette works perfectly with serif + sans-serif font duo

### Light Theme Grain Texture
**Source:** IzaIA / izaia.fr (2026-03)
**When:** Light/warm themes. Same SVG technique, different opacity.

```html
<svg class="grain" aria-hidden="true"
     style="position:fixed;inset:0;width:100%;height:100%;pointer-events:none;z-index:9998;opacity:0.03">
  <filter id="grain">
    <feTurbulence type="fractalNoise" baseFrequency="0.65" numOctaves="3" stitchTiles="stitch"/>
  </filter>
  <rect width="100%" height="100%" filter="url(#grain)"/>
</svg>
```

**Lesson:** On light themes, grain opacity should be 2-4% (vs 1.5-2% on dark). The texture adds a tactile, "printed paper" quality to cream backgrounds.

### Light Theme Radial Gradient
**Source:** IzaIA / izaia.fr (2026-03)
**When:** Hero sections on light-themed sites. Creates depth without being heavy.

```css
.hero-bg {
  background: radial-gradient(
    ellipse 80% 60% at 70% 40%,
    rgba(var(--accent-rgb), 0.07) 0%,
    transparent 70%
  );
}
```

**Lessons:**
- Very low opacity (0.07) on light backgrounds — much subtler than dark theme version
- Off-center positioning (70% 40%) = natural light source feel
- Ellipse shape (not circle) = more organic
- Light theme version uses accent color glow; dark theme uses it as a "spotlight"

### ScaleX Underline Animation (proven: 1 project)
**Source:** IzaIA / izaia.fr (2026-03)
**When:** Card hover effects, navigation links, any element that benefits from an animated underline.

```css
.card::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 3px;
  background: var(--accent);
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.3s ease;
}
.card:hover::after {
  transform: scaleX(1);
}
```

**Lessons:**
- `scaleX(0) → scaleX(1)` is smoother than `width: 0 → 100%` (GPU-accelerated)
- `transform-origin: left` makes it grow from left. Use `center` for centered links
- 3px height + accent color = visible but not heavy
- Combine with card `translateY(-4px)` hover for "lift + reveal" effect

### Glassmorphism Navbar (Light Theme Variant) (proven: 1 project)
**Source:** IzaIA / izaia.fr (2026-03)
**When:** Sticky navbars on light-themed sites.

```css
.nav {
  position: sticky;
  top: 0;
  background: rgba(253, 250, 246, 0.95);  /* cream with 95% opacity */
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  z-index: var(--z-navbar, 50);
  transition: box-shadow 0.3s ease;
}
.nav.scrolled {
  box-shadow: 0 1px 12px rgba(28, 25, 23, 0.08);
}
```
```javascript
window.addEventListener('scroll', () => {
  navbar.classList.toggle('scrolled', window.scrollY > 40);
}, { passive: true });
```

**Lessons:**
- On light themes, use the background color at 95% opacity (not white)
- `passive: true` on scroll listener = no jank
- Shadow appears only after scroll (40px threshold) — clean at top, grounded when scrolling
- Warm shadow color (brown-based, not pure black) matches palette

### Serif + Sans-Serif on Light Themes
**Source:** IzaIA / izaia.fr (2026-03)
**When:** B2B, professional services, training, consulting.

**Duo used:** `Instrument Serif` (headings) + `Inter` (body)

```css
@import url('https://fonts.googleapis.com/css2?family=Instrument+Serif&family=Inter:wght@400;500;600;700&display=swap');

h1, h2, h3 { font-family: 'Instrument Serif', serif; }
body { font-family: 'Inter', sans-serif; }
```

**Lesson:** On light themes, serif fonts feel more "editorial" and authoritative. On dark themes, they feel more "luxurious." Same font, different emotional register depending on the palette.

### Button Shine on Light Themes
**Source:** IzaIA / izaia.fr (2026-03)
**When:** Primary CTA buttons on colored backgrounds.

```css
@keyframes shine {
  0% { left: -100%; }
  50%, 100% { left: 100%; }
}
.btn-primary::after {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255,255,255,0.15), transparent);
  animation: shine 3s infinite;
}
```

**Lesson:** On light themes with colored buttons, shine can be more visible (0.15 opacity vs 0.03 on dark). The animation draws the eye to the CTA without being garish.

## Mobile Degradation Table

Every signature effect must degrade gracefully on mobile. This table is the single source of truth for what happens on touch devices.

**Detection:** `window.matchMedia('(hover: none)').matches` or Tailwind `max-md:` / `touch:` variants.

| Effect | Desktop | Tablet | Mobile | Why |
|--------|---------|--------|--------|-----|
| **Cursor glow** | Full dual-layer | Off | Off | No cursor on touch devices |
| **Glassmorphism** | Full `blur(12px)` | `blur(8px)` | `blur(6px)` or flat fallback | GPU cost scales with blur radius |
| **Grain texture** | 1.5-2% opacity | 1% opacity | Off | Subtle perf cost on low-end mobile GPUs |
| **Shine animation** | 8s infinite | 8s infinite | Off or `prefers-reduced-motion` | Battery drain on continuous animations |
| **Hover elevation** | `translateY(-3px)` + shadow boost | N/A | N/A | No hover on touch — use `active:scale-[0.98]` instead |
| **Radial gradient BG** | Full 700px | Full 500px | Simplified or solid color | Large gradients cost paint on mobile |
| **Rotating persona text** | Blur transition | Blur transition | Simple fade (no blur filter) | `filter: blur()` is expensive on mobile |
| **Stagger animations** | 0.12s stagger | 0.12s stagger | 0.08s stagger or simultaneous | Faster feel on small screens |
| **Video player** | Custom controls, auto-hide | Custom controls, always visible | Native controls | Custom controls are too small on mobile, native = accessible |

**Implementation pattern:**
```tsx
// Tailwind: hide on mobile, show on desktop
<div className="hidden md:block">  {/* Desktop-only effect */}
<div className="md:hidden">        {/* Mobile fallback */}

// JS: detect touch
const isMobile = window.matchMedia('(hover: none)').matches

// CSS: respect reduced motion
@media (prefers-reduced-motion: reduce) {
  .shine::after, .grain, [data-animate] { animation: none !important; }
}
```

**Rule:** When adding any new effect to this skill, immediately add a row to this table. An effect without a mobile degradation plan does not ship.

## Post-Project Review: Design

After each project, answer:
1. New effect or technique discovered? → Add with `**Source:** [project] (date)`
2. Existing example outdated? → Replace with better version
3. Client rejected a design choice? → Note WHY in the example
4. Great vibe/sector combo? → Add to palette recommendations
5. **Non-negotiable violated?** → Fix in the project AND strengthen the rule in this skill

**Rule: examples compete.** Better example replaces older one. Annotate proven ones with `(proven: N projects)`.
