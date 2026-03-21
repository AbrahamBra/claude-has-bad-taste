# Design Direction — Acme Consulting

## Elements to Keep
- Logo: the blue triangle icon is recognized by existing clients
- Testimonials section: clients mentioned it builds trust
- Contact form placement: bottom of page works for their funnel

## Chosen References
- https://linear.app : clean layout, generous whitespace — we take the spacing rhythm
- https://cal.com : the hero with one CTA and rotating text — we take the hero pattern
- https://resend.com : dark theme with warm accents — we take the color approach

## Visual Direction (validated)
- Palette: dark navy (#0A0F1C) background, warm gold (#C8973A) accent, off-white (#F0ECE4) text
- Typography: Instrument Serif for headings, Inter for body
- Layout: single-column hero, 2-column features, full-width testimonials
- Effects: grain texture, glassmorphism cards, subtle button glow
- Mood: premium but approachable, not corporate

## Context
- Mode: client
- Decision-maker: Sarah (VP Marketing at Acme)
- Feedback channel: async — Slack + weekly call

## Constraints (do not touch)
- Must keep the existing /blog URL structure (SEO equity)
- Logo cannot be modified (brand guidelines)
- Contact form must integrate with HubSpot

## Validation
- Date: 2026-03-15
- Confirmed by user: yes

## Launch Metrics — 2026-03-20
- Lighthouse Performance: 94
- Lighthouse Accessibility: 98
- LCP: 1.8s
- CLS: 0.04
- INP: 120ms
- Schema errors: 0
- Notes: Performance hit from HubSpot embed, mitigated with lazy loading
