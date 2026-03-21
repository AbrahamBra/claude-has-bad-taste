# Claude Web Design Skills

Three [Claude Code](https://claude.com/claude-code) skills for building websites that don't look AI-generated.

## The Problem

Claude has bad taste. Left to its own devices, it produces the same dark-mode-with-gradient-accents, glassmorphism-everything, generic-font sites that scream "AI made this."

These skills fix that by:

1. **Forcing aesthetic validation** before any code is written
2. **Providing battle-tested visual patterns** from real production sites
3. **Encoding web expertise** (accessibility, SEO, performance) as non-negotiable standards

## The 3-Layer Architecture

```
┌──────────────┐     ┌───────────────────┐     ┌────────────────┐
│  design-eye   │ ──→ │  design-signature  │ ──→ │  expertise-web  │
│  (Direction)  │     │  (Visual Identity) │     │  (Technical)    │
└──────────────┘     └───────────────────┘     └────────────────┘
     Layer 1               Layer 2                  Layer 3
  "What do we want       "How should it          "How should it
   visually?"              LOOK?"                  WORK?"
```

### design-eye (Layer 1: Calibration)

Runs FIRST on any web project. Browses reference sites, collects user feedback, produces a validated `design-direction.md`. Never makes autonomous aesthetic decisions — it asks, shows, and listens.

Key features:
- Mandatory brain dump before any questions
- 3 modes: full redesign (A), new site (B), partial redesign (C)
- Binary choice reduction when the user has no opinion
- Client mode vs solo mode detection
- Multi-page project handling

### design-signature (Layer 2: Visual Identity)

Signature effects library: glassmorphism cards, grain textures, button glow, cursor effects, fluid typography. Every pattern comes from a real project with source attribution.

Key features:
- Gate system: checks `design-direction.md` exists before any visual work
- Dark and light/warm theme patterns
- Mobile degradation table for every effect
- Non-negotiable visual standards (serif duo, grain, glassmorphism)

### expertise-web (Layer 3: Technical Excellence)

Modular web expertise hub with 6 reference modules. Non-negotiable standards (ARIA, touch targets, focus rings, OG/Twitter meta) plus patterns for components, content architecture, GEO/SEO, and static sites.

Reference modules:
| Module | Contents |
|--------|----------|
| `components.md` | Offer Picker, ROI Calculator, FAQ Accordion, Calendly, Video Player, Scroll Reveal |
| `content-arch.md` | Situation-based segmentation, Semantic Layers, Playbook pattern, Internal linking |
| `technical.md` | Next.js App Router, Framer Motion, Tailwind config, Domain migration |
| `geo-seo.md` | robots.txt, llms.txt, JSON-LD, Security headers, Accessibility, Performance |
| `static-patterns.md` | Vanilla HTML, native accordions, mailto forms, single-page landings |
| `sources.md` | 21st.dev, Landing.love, Saaspo, Navbar Gallery, Component Gallery |

## Installation

### Option 1: Global installation (recommended)

```bash
git clone https://github.com/YOUR_USERNAME/claude-web-design.git /tmp/claude-web-design
cp -r /tmp/claude-web-design/skills/* ~/.claude/skills/
```

Skills will be available in every Claude Code session.

### Option 2: Project-level installation

```bash
git clone https://github.com/YOUR_USERNAME/claude-web-design.git /tmp/claude-web-design
cp -r /tmp/claude-web-design/skills/* .claude/skills/
```

### Option 3: Individual skills

```bash
git clone https://github.com/YOUR_USERNAME/claude-web-design.git /tmp/claude-web-design

# Just design-eye (aesthetic calibration)
cp -r /tmp/claude-web-design/skills/design-eye ~/.claude/skills/

# Just design-signature (visual effects)
cp -r /tmp/claude-web-design/skills/design-signature ~/.claude/skills/

# Just expertise-web (web patterns)
cp -r /tmp/claude-web-design/skills/expertise-web ~/.claude/skills/
```

### Verify installation

Start a new Claude Code session and ask:
> "What design skills do you have available?"

Claude should mention design-eye, design-signature, and/or expertise-web.

## How It Works

1. Start a web project — design-eye triggers automatically
2. Brain dump — you dump everything about the project, unstructured
3. Reference browsing — design-eye finds real sites in your space
4. Direction validation — you approve a `design-direction.md` before any code
5. Implementation — design-signature applies visual patterns within the direction
6. Technical quality — expertise-web ensures accessibility, SEO, and performance throughout

The critical insight: **design-direction.md is the gate**. No visual code gets written until the user has explicitly validated the direction. This prevents the "Claude just did whatever it wanted" problem.

## Localization

All content is in English. French localization sections are included for client-facing prompts (brain dump, feedback loops, direction template) since these skills were originally developed for French B2B projects.

To add your own language:
1. Add `### Localization: [Language]` sections with translated client prompts
2. See `CONTRIBUTING.md` for guidelines

## Patterns Included

All patterns are extracted from real production projects. Source annotations like `Source: setting.live (2026-03)` reference the original project where a pattern was first used or proven. These are kept for traceability.

| Category | Patterns | Proven across |
|----------|----------|---------------|
| Visual effects | Glassmorphism, grain texture, cursor glow, button shine, radial gradients | 2-3 projects |
| Typography | Serif+sans-serif duo, fluid clamp(), z-index system | 2-3 projects |
| Components | Offer picker, ROI calculator, FAQ accordion, lazy Calendly, video player | 1-2 projects |
| Content architecture | Situation-based segmentation, semantic layers, playbook pattern | 1-2 projects |
| GEO/SEO | AI-friendly robots.txt, llms.txt, graph JSON-LD, hreflang | 2 projects |
| Static patterns | Native details, mailto forms, scroll reveal, 3-tier pricing | 1 project |

## Customization

See [docs/customization.md](docs/customization.md) for detailed guidance on:
- Adding your own project sources
- Modifying non-negotiable standards
- Adding effects to the signature
- Localizing prompts to your language

## Disclaimer

These are community-created skills, not official Anthropic products. They are opinionated guides based on one team's production experience.

## License

MIT — see [LICENSE](LICENSE)
