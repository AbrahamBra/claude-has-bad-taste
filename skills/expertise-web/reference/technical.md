# Technical Patterns

Framework-specific patterns and infrastructure checklists.

## Next.js App Router (proven: 2 projects)
- `app/[page]/page.tsx` for each route
- Heavy components: `dynamic(() => import(...), { ssr: false })`
- `'use client'` only where needed (interactivity)
- API routes: `app/api/[name]/route.ts`

## Framer Motion (proven: 2 projects)
**CRITICAL: staggerChildren is mandatory on any list of 3+ items.**

```typescript
// Container with stagger
const container = {
  hidden: {},
  show: { transition: { staggerChildren: 0.12 } }
}

// Child items
const item = {
  hidden: { opacity: 0, y: 20 },
  show: { opacity: 1, y: 0, transition: { duration: 0.5, ease: [0.16, 1, 0.3, 1] } }
}

<motion.div variants={container} initial="hidden" animate="show">
  {items.map((i) => <motion.div key={i} variants={item} />)}
</motion.div>
```

Additional patterns:
- `AnimatePresence mode="wait"` for panel/tab transitions
- `filter: blur(8px)` on enter/exit for text rotation (see design-signature)
- Scale on hover (1.02) + tap (0.98) for tactile feel on buttons
- `useScroll` + `useTransform` for parallax sections

## Tailwind Extended Config (proven: 2 projects)
**Source:** setting.live (2026-03)

```typescript
// tailwind.config.ts essentials
theme: {
  extend: {
    colors: {
      accent: '#COLOR',
      'accent-hover': '#DARKER',
      'accent-light': '#LIGHTER',
      'bg-primary': '#BG',
      'bg-secondary': '#BG2',
      'text-primary': '#TEXT',
      'text-secondary': '#TEXT2',
      'text-muted': '#MUTED',
    },
    fontFamily: {
      sans: ['var(--font-sans)', 'system-ui', 'sans-serif'],
      serif: ['var(--font-serif)', 'Georgia', 'serif'],
      mono: ['var(--font-mono)', 'monospace'],
    },
    fontSize: {
      // Fluid typography with clamp() — see design-signature
    },
    spacing: {
      'section': '120px',
      'section-sm': '80px',
    },
  },
}
```

## Domain Migration Checklist
**Source:** setting.live (2026-03) — migrated challengerslab.fr → setting.live

```typescript
// next.config.ts — permanent redirects
async redirects() {
  return [
    { source: '/blog', destination: '/ressources', permanent: true },
    { source: '/blog/:slug', destination: '/ressources/:slug', permanent: true },
    { source: '/old-page', destination: '/new-page', permanent: true },
  ]
}
```

**Full migration checklist:**
1. Add 301 redirects for ALL old URLs in `next.config.ts`
2. Update canonical URLs on every page
3. Update sitemap.xml with new domain
4. Update robots.txt with new sitemap URL
5. Update all internal links (grep old domain site-wide)
6. Update structured data (JSON-LD) with new URLs
7. Update `llms.txt` and `llms-full.txt`
8. Set up Google Search Console for new domain
9. Request domain change in Search Console
10. Update OG images and social sharing URLs
11. Monitor 404s in Search Console for 3 months
