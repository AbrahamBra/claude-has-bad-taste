# Interactive Components

Battle-tested component patterns from real projects. Each has source, code, and transferable lessons.

## Situation-Based Offer Picker (proven: 1 project)
**Source:** setting.live (2026-03)
**When:** Service businesses with multiple offerings mapped to customer pain points.

```typescript
// Data structure: typed offers with situation mapping
interface Offer {
  id: string
  slug: string
  eyebrow: string
  color: string              // Per-offer accent color
  situation: string          // "Je n'ai pas de leads"
  description: string
  features: { title: string; detail: string }[]
  pricing: {
    type: 'fixed' | 'custom'
    setup?: { amount: number; label: string; detail: string }
    subscription?: { amount: number; period: string; detail: string }
    bonus?: string           // Tiered: "50€ (<5k), 150€ (5-15k), 250€ (>15k)"
  }
  guarantee?: string
  noCommitment?: boolean
  cta: { label: string; href: string }
  methodeLink: string
}

// UI: tabs → panel with AnimatePresence
const [selected, setSelected] = useState(0)

// Tab buttons with per-offer color tinting
<button style={isActive ? {
  borderColor: `${offer.color}50`,
  backgroundColor: `${offer.color}0D`,
  boxShadow: `0 0 24px ${offer.color}12`,
} : { backgroundColor: 'rgba(255,255,255,0.02)' }}>

// Panel transitions
<AnimatePresence mode="wait">
  <motion.div
    key={offers[selected].id}
    initial={{ opacity: 0, y: 16 }}
    animate={{ opacity: 1, y: 0 }}
    exit={{ opacity: 0, y: -8 }}
    transition={{ duration: 0.3, ease: [0.16, 1, 0.3, 1] }}
  >
    <OfferPanel offer={offers[selected]} />
  </motion.div>
</AnimatePresence>
```

**Lessons:**
- Centralize all offer data in `lib/offers-data.ts` — single source of truth
- Color-code each offer for visual differentiation
- Situation text = customer's words, not marketing jargon
- `mode="wait"` ensures clean transitions (old exits before new enters)
- Pricing panel inside the card, not a separate section — reduces clicks

## ROI Calculator
**Source:** setting.live (2026-03)
**When:** Any service with quantifiable ROI. B2B especially.

```typescript
// Adapted from a French B2B project — rename variables to match your domain

// Tiered bonus logic
function getBonusPerMeeting(averageTicket: number): number {
  if (averageTicket < 5000) return 50
  if (averageTicket <= 15000) return 150
  return 250
}

// Dynamic calculation with useMemo
const results = useMemo(() => {
  const bonus = getBonusPerMeeting(averageTicket)
  const monthlyCost = FIXED_COST + bonus * meetingsPerMonth
  const clientsWon = meetingsPerMonth * (closingRate / 100)
  const monthlyRevenue = clientsWon * averageTicket
  const roi = monthlyRevenue / monthlyCost
  return { monthlyCost, clientsWon, monthlyRevenue, roi, netRevenue: monthlyRevenue - monthlyCost }
}, [averageTicket, meetingsPerMonth, closingRate])

// Display: tabular-nums for alignment
<span className="font-sans text-accent font-extrabold text-3xl tabular-nums">
  {results.roi.toFixed(1)}x
</span>
```

**Lessons:**
- `useMemo` for real-time recalculation without re-renders
- `tabular-nums` CSS for aligned numeric displays
- Use offer-specific color with low opacity for result backgrounds
- Always show pessimistic AND optimistic scenarios

## FAQ Accordion (Accessible)
**Source:** setting.live (2026-03) — corrected version
**CRITICAL:** The original version had no ARIA. This is the correct implementation.

```tsx
function FAQ({ faqs }: { faqs: { q: string; a: string }[] }) {
  const [open, setOpen] = useState<number | null>(null)

  return (
    <div className="space-y-2" role="list">
      {faqs.map((faq, i) => (
        <div key={i} className="border border-white/[0.06] rounded-xl overflow-hidden" role="listitem">
          <button
            onClick={() => setOpen(open === i ? null : i)}
            aria-expanded={open === i}
            aria-controls={`faq-panel-${i}`}
            id={`faq-btn-${i}`}
            className="w-full flex items-center justify-between gap-4 p-5 text-left
                       hover:bg-white/[0.02] transition-colors min-h-[48px]
                       focus-visible:ring-2 focus-visible:ring-accent focus-visible:ring-inset"
          >
            <span className="font-sans text-sm font-semibold text-text-primary">{faq.q}</span>
            <motion.span
              className="text-text-muted text-lg shrink-0"
              animate={{ rotate: open === i ? 45 : 0 }}
              transition={{ duration: 0.2 }}
              aria-hidden="true"
            >+</motion.span>
          </button>
          <AnimatePresence>
            {open === i && (
              <motion.div
                id={`faq-panel-${i}`}
                role="region"
                aria-labelledby={`faq-btn-${i}`}
                initial={{ height: 0, opacity: 0 }}
                animate={{ height: 'auto', opacity: 1 }}
                exit={{ height: 0, opacity: 0 }}
                transition={{ duration: 0.25, ease: [0.16, 1, 0.3, 1] }}
                className="overflow-hidden"
              >
                <div className="px-5 pb-5">
                  <p className="font-sans text-sm text-text-secondary leading-relaxed">{faq.a}</p>
                </div>
              </motion.div>
            )}
          </AnimatePresence>
        </div>
      ))}
    </div>
  )
}
```

**Lessons:**
- `aria-expanded` on button, `aria-controls` pointing to panel `id`
- `role="region"` + `aria-labelledby` on the answer panel
- `AnimatePresence` with `height: 0 → auto` for smooth open/close
- `min-h-[48px]` + `focus-visible:ring` = accessible touch target
- `+` rotates to `×` via CSS transform, not icon swap

## Lazy-Loaded Calendly
**Source:** setting.live (2026-03)
**When:** Embedding any heavy third-party widget (Calendly, HubSpot, Typeform).

```tsx
function CalendlySlot({ url }: { url: string }) {
  const [loaded, setLoaded] = useState(false)

  if (!loaded) {
    return (
      <div className="flex flex-col items-center justify-center gap-5 min-h-[260px]">
        <ButtonGlow onClick={() => setLoaded(true)}>
          Book 30 min →
        </ButtonGlow>
      </div>
    )
  }

  // Only imported after click
  const { InlineWidget } = require('react-calendly')
  return <InlineWidget url={url} styles={{ height: '500px', minWidth: '280px' }} />
}
```

**Lesson:** Never load third-party widgets on page load. Show a CTA button first, lazy-load the widget on click. Saves 200-500KB of initial JS.

## Custom Video Player
**Source:** gtm-deeptech.io (2026-02) — 3 iterations, v3 is reference
**Lesson:** Start with native controls, then layer custom UI. The stop button required its own iteration.

Features: play/pause, stop, mute, fullscreen, speed (1x/1.25x/1.5x/2x), clickable scrubber.
Pattern: `group-hover` for progressive disclosure — controls minimal by default, expand on hover.
Mobile: always show controls (no hover on touch). Auto-hide with timeout on desktop.

```typescript
// Scrubber: minimal by default, detailed on hover
<div className="flex-1 group/scrubber cursor-pointer">
  <div className="h-[2px] group-hover/scrubber:h-1 bg-blanc/20 transition-all">
    <div className="h-full bg-accent" style={{ width: `${progress}%` }} />
    <div className="w-3 h-3 bg-blanc opacity-0 group-hover/scrubber:opacity-100" />
  </div>
</div>
```

## Scroll Reveal (IntersectionObserver) (proven: 2 projects)
**Source:** gtm-deeptech.io (2026-02), setting.live (2026-03)
**When:** Entrance animations for sections and cards.

```typescript
const observer = new IntersectionObserver(
  ([entry]) => {
    if (entry.isIntersecting) {
      setTimeout(() => setIsVisible(true), delay)
      observer.unobserve(entry.target)  // Fire ONCE — memory safe
    }
  },
  { threshold: 0.1, rootMargin: '0px 0px -50px 0px' }
)
```

**Lessons:**
- `rootMargin: -50px` triggers 50px before bottom → anticipates scroll
- `unobserve` after fire → prevents memory leaks on long pages
- Configurable direction (up/down/left/right) via `translate3d`
- Easing: `cubic-bezier(0.16, 1, 0.3, 1)` for silky reveal

## Sticky Phase Navigation with Scroll Progress
**Source:** setting.live (2026-03)
**When:** Long methodology pages with multiple phases/steps.

```typescript
// 3 IntersectionObservers working together:
// 1. Show nav when hero exits viewport
const heroObs = new IntersectionObserver(
  ([entry]) => setVisible(!entry.isIntersecting), { threshold: 0 })

// 2. Track which section is active
sectionIds.forEach((id) => {
  const obs = new IntersectionObserver(
    ([entry]) => { if (entry.isIntersecting) setActivePhase(id) },
    { threshold: 0.3, rootMargin: '-80px 0px -50% 0px' })
})

// 3. Scroll progress bar
const updateProgress = () => {
  const scrollY = window.scrollY + window.innerHeight * 0.5
  const pct = ((scrollY - firstSection.offsetTop) / totalHeight) * 100
  setProgress(Math.min(100, Math.max(0, pct)))
}
```

**Lessons:**
- `z-[var(--z-phase-nav)]` = below navbar, above content
- Keyboard navigation: ArrowLeft/Right between phases
- `role="tablist"`, `aria-selected` on active tab
- `bg-bg-primary/95 backdrop-blur-md` for semi-transparent sticky bar

## Smooth Scroll (Lenis)
**Source:** gtm-deeptech.io (2026-02)
**CRITICAL:** DISABLE on mobile. Check `(hover: none)` BEFORE init. Native mobile scroll is better.
**CRITICAL:** Actually import and use LenisProvider in layout. Don't define it and forget to call it.

## Form with Conversion Tracking (proven: 2 projects)
**Source:** gtm-deeptech.io (2026-02), setting.live (2026-03)

```typescript
// Resend API for email delivery
const resend = new Resend(process.env.RESEND_API_KEY)

// Form handler
const handleSubmit = async (e: React.FormEvent) => {
  e.preventDefault()
  setState('loading')
  try {
    const res = await fetch('/api/contact', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify(form),
    })
    if (!res.ok) { setState('error'); return }
    setState('success')

    // GA4 AFTER success — NEVER before
    if (typeof window !== 'undefined' && typeof (window as any).gtag === 'function') {
      ;(window as any).gtag('event', 'generate_lead', {
        event_category: 'contact',
        lead_type: 'setting',
        method: 'form',
      })
    }
  } catch { setState('error') }
}
```

**Lessons:**
- Analytics AFTER `res.ok` confirmation, never before
- Resend for email delivery — simpler than SendGrid for small teams
- Email validation: `/^[^\s@]+@[^\s@]+\.[^\s@]+$/` on both client and server
- All form inputs: `min-h-[48px]`, `focus-visible:ring-accent`

## Cursor Effects
**Source:** gtm-deeptech.io (2026-02)
**Pattern:** Dual-layer glow (large halo + small bright point). Desktop only.
**Performance:** ALWAYS throttle with `requestAnimationFrame`. See design-signature for code.
