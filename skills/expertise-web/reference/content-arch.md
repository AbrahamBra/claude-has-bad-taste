# Content Architecture & Navigation

Patterns for organizing content, internal linking, and navigation structures.

## Situation-Based Segmentation
**Source:** setting.live (2026-03)
**When:** Services that solve different problems depending on where the customer is in their journey.

**Pattern:** Map each offer to a customer **situation** (pain point in their words), not a product name.
- "I don't have any leads" (FR: "Je n'ai pas de leads") → LinkedIn Setting
- "I have leads but no meetings" (FR: "J'ai des leads mais pas de RDV") → Phone Setting
- "I have leads but I lose contact" (FR: "J'ai des leads mais je perds le contact") → Nurturing

**Lesson:** Customers don't know your product names. They know their problem. Let them self-select.

## Semantic Layer System
**Source:** setting.live (2026-03)
**When:** Educational content explaining a process that mixes AI, methodology, and human work.

```typescript
// FR: IA, Méthode, Humain, IA + Méthode
const layerConfig = {
  ia: { label: 'AI', color: '#A78BFA' },
  methode: { label: 'Method', color: '#FBBF24' },
  humain: { label: 'Human', color: '#34D399' },
  hybrid: { label: 'AI + Method', color: '#C084FC' },
} as const

// Each step is tagged:
{ num: '01', label: 'Targeting', layers: ['hybrid'], tools: ['Sales Navigator'] } // FR: Ciblage
```

**Lesson:** Color-coding process steps by WHO does the work (AI/human/both) builds trust and demystifies the service.

## Playbook Pattern (Progressive Chapters)
**Source:** gtm-deeptech.io (2026-02)
**When:** Educational content, methodology, step-by-step guides.

```typescript
interface PlaybookPhase {
  id: string          // URL anchor: #comprendre
  label: string       // "Comprendre"
  number: number
  description: string
  slugs: string[]     // Article slugs in this phase
}
```

**Lessons:**
- Organize content in progressive phases (beginner → advanced)
- Phases = navigation structure = mega-menu columns = SEO sitemap
- Same article can appear in phase AND sector → dense internal linking

## Article Fusion / Consolidation
**Source:** gtm-deeptech.io (2026-02)

**Checklist — easy to forget a file:**
1. Create the new merged article page
2. Delete old article pages
3. Add 301 redirects in `next.config.ts` (old URLs → new URL)
4. Update `lib/blog-data.ts` (slugs, phases, sectors)
5. Update `app/sitemap.ts` (remove old, add new)
6. Update `public/llms.txt` and `public/llms-full.txt`
7. Update all cross-references in other articles (grep old slugs site-wide)
8. Update glossary links if applicable
9. Update mega-menu if articles were featured

**Lesson:** Never fuse articles without the full checklist. Forgotten redirects = 404s that kill SEO.

---

## Navigation & Maillage Interne

### Mega-Menu (Data-Driven)
**Source:** gtm-deeptech.io (2026-02)

```typescript
// FR: Playbook GTM, Par secteur, Outils
const megaMenuColumns = [
  { title: 'GTM Playbook', links: [{ label, href, desc }...] },
  { title: 'By sector', links: [...] },
  { title: 'Tools', links: [...] },
]
```

**Lessons:**
- Structure as data arrays → easy to A/B test, rotate content
- Mobile = accordion with expandable sections (NOT same as desktop grid)
- Featured articles footer for SEO link juice

### Internal Linking Rules
- Articles link to each other by phase AND by sector
- Mega-menu deep-links to article anchors
- Navigation mirrors content architecture
- Anchor IDs on every major section for shareable URLs
- **Always add a "related articles" section at the bottom of each article page**
