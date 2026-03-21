# Static / Vanilla HTML Patterns

Patterns for sites without frameworks. Proven on real projects.

## When to Go Static (proven: 1 project)
**Source:** IzaIA / izaia.fr (2026-03)
**When:** Single-page landing + small blog (< 10 articles), low-maintenance sites, privacy-first positioning.

**Decision framework:**
- < 10 pages AND no dynamic content → **Static HTML** (zero build, zero hosting cost, GitHub Pages)
- 10-50 pages OR growing blog → **SSG** (Hugo, 11ty, Astro) for DRY templates
- Dynamic content OR auth → **Next.js / SvelteKit**

**Lesson:** The IzaIA site (1900-line index.html + 5 blog articles) works perfectly as pure HTML/CSS/JS. The technical simplicity mirrors the business message (practical, no-BS). Don't reach for a framework when the problem doesn't need one.

## Native `<details>` Accordion (proven: 1 project, vanilla)
**Source:** IzaIA / izaia.fr (2026-03)
**When:** FAQ sections on static sites. Zero JS required.

```html
<details class="faq-item">
  <summary class="faq-q">
    Question text
    <span class="faq-icon">+</span>
  </summary>
  <div class="faq-a">Answer text</div>
</details>
```
```css
.faq-item { border: 1px solid var(--border); border-radius: 12px; overflow: hidden; }
.faq-q { cursor: pointer; padding: 1.2rem 1.5rem; font-weight: 600; list-style: none; display: flex; justify-content: space-between; align-items: center; }
.faq-q::-webkit-details-marker { display: none; }
.faq-icon { transition: transform 0.3s ease; }
details[open] .faq-icon { transform: rotate(45deg); }
.faq-a { padding: 0 1.5rem 1.2rem; color: var(--muted); }
```

**Lessons:**
- Native `<details>` = accessible by default, no JS, keyboard navigable
- Hide default marker with `::-webkit-details-marker { display: none }`
- `+` rotates to `x` via `rotate(45deg)` — pure CSS
- Combine with FAQ JSON-LD schema for rich snippets (dual output: visible + structured data)

## Vanilla Scroll Reveal (proven: 1 project, no framework)
**Source:** IzaIA / izaia.fr (2026-03)
**When:** Entrance animations on static sites without Framer Motion.

```html
<div class="reveal">Content</div>
<div class="reveal reveal-d1">Staggered</div>
<div class="reveal reveal-d2">Staggered more</div>
```
```css
.reveal { opacity: 0; transform: translateY(30px); transition: opacity 0.8s ease, transform 0.8s ease; }
.reveal.visible { opacity: 1; transform: translateY(0); }
.reveal-d1 { transition-delay: 0.15s; }
.reveal-d2 { transition-delay: 0.30s; }
.reveal-d3 { transition-delay: 0.45s; }
```
```javascript
const observer = new IntersectionObserver((entries) => {
  entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('visible'); observer.unobserve(e.target); } });
}, { threshold: 0.1, rootMargin: '0px 0px -50px 0px' });
document.querySelectorAll('.reveal').forEach(el => observer.observe(el));
```

**Lessons:**
- Stagger via CSS classes (`reveal-d1`, `reveal-d2`) — no JS timing needed
- `unobserve` after triggering = memory safe on long pages
- `rootMargin: -50px` = triggers slightly before element enters viewport
- This is the static-site equivalent of Framer Motion `staggerChildren`

## Mailto Form (Zero-Backend Contact)
**Source:** IzaIA / izaia.fr (2026-03)
**When:** Low-volume contact forms (< 100/month) where privacy-first positioning matters.

```javascript
// Adapt labels to your language
form.addEventListener('submit', (e) => {
  e.preventDefault();
  const data = new FormData(form);
  const subject = encodeURIComponent(`Quote request — ${data.get('company')}`);
  const body = encodeURIComponent(
    `Name: ${data.get('firstName')} ${data.get('lastName')}\nCompany: ${data.get('company')}\nEmail: ${data.get('email')}\nTel: ${data.get('tel')}\nMessage: ${data.get('message')}`
  );
  window.location.href = `mailto:contact@example.com?subject=${subject}&body=${body}`;
});
```

**Lessons:**
- Zero server, zero data stored = strong privacy argument for RGPD-sensitive audiences
- Pre-fills email subject with context (company name) for easy triage
- **Limitation:** depends on user having an email client configured — add visible email as fallback
- **Upgrade path:** Formspree or Basin when volume grows (no code change needed, just swap handler)

## Single-Page Landing with Anchor Navigation (proven: 1 project)
**Source:** IzaIA / izaia.fr (2026-03)
**When:** Service businesses with a single offering. Keep everything on one scroll.

**Structure pattern:**
```
// Adapt labels to your language
Hero → Who it's for (audience) → Program (offer details) → Trainers (team) →
Testimonials (social proof) → Pricing (pricing) → Contact (form) → FAQ → Footer
```

**Lessons:**
- Navbar uses anchor links (`#programme`, `#tarif`) with `scroll-behavior: smooth`
- Sticky navbar with `backdrop-filter: blur(12px)` and scroll-triggered shadow
- `passive: true` on scroll listener for performance
- Mobile: hamburger opens full-screen overlay with `position: fixed; inset: 0`
- Each section = conversion funnel step. Place CTAs at transition points between sections
- FAQ BEFORE final CTA = answer objections right before decision moment

## Testimonials with Placeholder (Early-Stage Pattern)
**Source:** IzaIA / izaia.fr (2026-03)
**When:** Launching a service with few or no testimonials yet.

**Pattern:** Show 2 real testimonials + 1 transparent placeholder:
```html
<div class="testimonial-card placeholder-card">
  <p>Training currently being deployed — the next reviews will appear here.</p>
  <a href="#contact">Be among the first</a>
</div>
```
```css
.placeholder-card { border: 2px dashed var(--border); background: transparent; }
```

**Lessons:**
- Dashed border signals "coming soon" without looking broken
- CTA inside placeholder converts curiosity into action ("Be among the first")
- More honest than fake testimonials — builds trust with professional audiences
- Remove and replace with real testimonials as they come in

## 3-Tier Pricing with Featured (proven: 1 project)
**Source:** IzaIA / izaia.fr (2026-03)
**When:** Any service with tiers or packages.

**Pattern:**
- 3 cards in grid: Standard | **Featured** (recommended) | Add-on
- Featured card: accent border, badge ("Recommended"), stronger shadow, slight scale (1.02)
- Each card: price + unit + feature checklist + CTA button
- Below grid: full-width "Qualiopi" or funding eligibility box

**Lessons:**
- Featured card gets `transform: scale(1.02)` and `box-shadow` emphasis — subtle but effective
- Price in large serif font + small unit label (`/ per day, excl. tax`) for clarity
- Feature list uses checkmarks (not bullets) — positive framing
- Funding/eligibility info BELOW pricing = removes price objection immediately

## Privacy-First as Trust Signal
**Source:** IzaIA / izaia.fr (2026-03)
**When:** Targeting regulated industries (accounting, legal, healthcare, finance).

**Pattern:**
- "This site does not use tracking cookies" in footer and legal notices
- No Google Analytics, no GTM, no third-party tracking
- Form uses mailto: (no data stored on servers)
- RGPD compliance as a differentiator, not just a legal checkbox

**Lesson:** For B2B in regulated sectors, privacy-first positioning IS a conversion optimization. Prospects in accounting/legal evaluate your site through a compliance lens. Zero tracking = "they practice what they preach."

## Blog as SEO + Authority Driver (proven: 1 project)
**Source:** IzaIA / izaia.fr (2026-03)
**When:** Any service site that needs organic traffic.

**Pattern:**
- Blog on `/blog/` subdirectory (not subdomain) for SEO juice
- Hub page with article cards in grid
- Each article: tag + h1 + intro + author chip + metadata + body + related articles
- Article types: Methode, Conformite, Financement, Tendances — cover different search intents

**Interlinking strategy:**
- Articles reference each other in "Related articles" sections
- Articles link BACK to main landing page sections (`../../index.html#tarif`)
- FAQ answers link TO blog articles for deeper reading
- Blog CTA links to contact form on main page

**Lesson:** Blog articles create entry points for long-tail SEO. Each article should link to at least 2 other articles AND back to the main conversion page. The blog feeds the funnel; the landing page closes it.

## Schema Triple Pattern (proven: 1 project)
**Source:** IzaIA / izaia.fr (2026-03)
**When:** Service sites with educational content.

**Combine 3 schema types:**
1. `Course` (or `Service`) on main page — describes the offering with price, provider, location
2. `FAQPage` on main page — mirrors visible FAQ for rich snippets
3. `Article` on each blog post — headline, author, datePublished, publisher

**Lesson:** Schema markup is cumulative. Each type targets a different SERP feature. FAQ schema is highest-ROI because Google shows it directly in search results.
