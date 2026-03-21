# GEO, SEO & Quality Standards

AI search optimization, security headers, accessibility, and performance patterns.

## GEO Patterns (AI Search Optimization)
**Source:** setting.live (2026-03)
**CRITICAL:** These patterns make your site visible to AI search engines (ChatGPT, Perplexity, Claude, Gemini).

### AI-Friendly robots.txt
```
User-agent: *
Allow: /

# AI search bots — explicitly allowed
User-agent: GPTBot
Allow: /

User-agent: PerplexityBot
Allow: /

User-agent: ClaudeBot
Allow: /

User-agent: anthropic-ai
Allow: /

User-agent: Google-Extended
Allow: /

Sitemap: https://www.example.com/sitemap.xml
```

**Lesson:** Most sites block AI bots by default. Explicitly allowing them = more citations in AI answers.

### llms.txt — AI-Readable Site Summary
Create `public/llms.txt` (concise) and `public/llms-full.txt` (detailed):

```markdown
# Site Name
> One-line description

## Services
- Service 1: description, pricing
- Service 2: description, pricing

## Key Pages
- /page-1: description
- /page-2: description

## Contact
- email, phone, location
```

**Lesson:** `llms.txt` is the new `robots.txt` for AI. It helps LLMs understand your site without crawling every page.

### Graph-Based JSON-LD (Multi-Entity)
```typescript
const jsonLd = {
  '@context': 'https://schema.org',
  '@graph': [
    { '@type': 'WebSite', '@id': `${BASE_URL}/#website`,
      url: BASE_URL, name: 'Site Name', inLanguage: 'fr-FR' },
    { '@type': 'ProfessionalService', '@id': `${BASE_URL}/#business`,
      name: 'Business Name',
      hasOfferCatalog: { '@type': 'OfferCatalog', itemListElement: [...] },
      aggregateRating: { '@type': 'AggregateRating', ratingValue: '4.8', reviewCount: '20' },
    },
  ],
}
```

### Page-Specific Schemas
- **Homepage:** `FAQPage` schema for FAQ section
- **Methodology pages:** `BreadcrumbList` schema
- **Results/testimonials:** `Service` + `AggregateRating` + `Review` schemas
- **Articles:** `Article` schema with `author`, `datePublished`, `image`

### Hreflang (French Sites)
```typescript
alternates: {
  canonical: 'https://www.example.com/page',
  languages: {
    'fr': 'https://www.example.com/page',
    'x-default': 'https://www.example.com/page',
  },
}
```

**Lesson:** Even monolingual French sites should declare `fr` + `x-default` for proper international SEO signals.

---

## Security Headers (proven: 2 projects)
```typescript
// next.config.ts headers()
{ key: 'X-Content-Type-Options', value: 'nosniff' },
{ key: 'X-Frame-Options', value: 'SAMEORIGIN' },
{ key: 'Referrer-Policy', value: 'strict-origin-when-cross-origin' },
{ key: 'Permissions-Policy', value: 'camera=(), microphone=(), geolocation=()' },
{ key: 'Strict-Transport-Security', value: 'max-age=63072000; includeSubDomains; preload' },
```

---

## Accessibility Standards (NON-NEGOTIABLE)
- Touch targets: **48px minimum** (`min-h-[48px]`)
- `aria-label` on ALL interactive elements without visible text
- `aria-expanded` + `aria-controls` on ALL accordions/dropdowns
- `role="region"` + `aria-labelledby` on accordion panels
- `focus-visible:ring-2 focus-visible:ring-accent` on EVERY interactive element
- `aria-hidden="true"` on decorative elements (particles, grain, cursor glow, icons)
- `tabIndex` management for keyboard navigation in tabs/carousels
- Form inputs: visible `<label>` or `aria-label`, error messages linked with `aria-describedby`

---

## Performance
- Dynamic imports for Three.js, heavy animation components
- Lazy-load third-party widgets (Calendly, etc.) on user interaction
- Next.js Image for all images (automatic optimization)
- GTM/GA4 with `afterInteractive` strategy + noscript fallback
- Lenis DISABLED on mobile (see components reference)
- Fonts: `display: 'swap'` to prevent FOIT

---

## SEO Technical (proven: 2 projects)
- Dynamic sitemap (`app/sitemap.ts`) listing ALL routes
- `robots.txt` with AI bot whitelist (see GEO Patterns above)
- Canonical URLs on every page
- OG + Twitter Card meta on every page:
  ```typescript
  // Next.js metadata
  openGraph: { title, description, locale: 'fr_FR', type: 'website', images: [...] },
  twitter: { card: 'summary_large_image', title, description, images: [...] },
  ```
- Google Search Console: verification + sitemap submission
- `llms.txt` + `llms-full.txt` for AI discoverability
- Hreflang on all pages (even monolingual)
