# Protocols

## Chargement conditionnel

Charge ce fichier UNIQUEMENT si l'une de ces conditions est vraie :

| Condition | Protocole à appliquer |
|-----------|----------------------|
| Sur le point de construire un composant sans pattern interne | **Gap Detection** (Protocol 1) |
| L'utilisateur signale une approbation ("c'est bon", "parfait", etc.) | **Harvest** (Protocol 2) |

Si ni l'une ni l'autre condition n'est remplie → ne charge pas ce fichier. Il ne sera pas utile.

> **Règle de scope** : charge uniquement la section pertinente (Protocol 1 OU Protocol 2), pas les deux systématiquement. Le Gap Registry est toujours utile à garder en mémoire — c'est lui qui déclenche le Gap Detection.

---

Two self-improvement protocols that make expertise-web self-aware and self-growing.

---

## Protocol 1: Gap Detection

Fires when Claude is about to build a component with no internal pattern. Prevents building blind.

### Trigger conditions

- **At project start** — when expertise-web loads, Claude scans the upcoming build against the `components.md` table of contents.
- **During build** — when Claude is about to generate a component type with no matching internal pattern.

### Decision logic

```
Component requested → check components.md TOC → match found? → build with pattern
                                                → no match?  → check Gap Registry below
                                                              → fire split research brief
                                                              → wait for convergence
```

### Split research brief format

When a gap is detected, output this block before building anything:

```markdown
## Gap Détecté : [Component Name]

Aucun pattern interne dans `components.md` pour ce type de composant.
Construction suspendue le temps de chercher des références.

### Claude cherche (technique) :
- [ ] [source] — [requête spécifique]
- [ ] [source] — [catégorie]

### Tu cherches (visuel) :
- [ ] [source] — [filtre suggéré]
- [ ] [source] — [style ou section à explorer]

**Point de convergence avant construction.**
```

### Source split rationale

- **Claude handles technical sources** (shadcn, 21st.dev, Magic UI, Aceternity, CodeMyUI, HeroUI, Hover.dev) — code-readable, adaptable directly. Claude browses these via WebFetch/WebSearch in parallel with the user.
- **User handles visual sources** (Landing.love, Awwwards, Design Spells, Land-book, Saaspo, Mobbin, Collect UI) — aesthetic judgment requires human calibration (see `feedback_aesthetic_judgment.md`). Mobbin and Collect UI are included here because their value is pattern recognition across real apps — a judgment call, not a code lookup.

---

## Protocol 2: Harvest

Fires when the user approves a completed component. Captures the pattern into the appropriate `reference/` file before the lesson dies in the conversation.

### Trigger signals

Explicit approval expressions: "c'est bon", "parfait", "on garde ça", "merge", "top", or approval of a PR/commit containing a component.

**Scope rule:** If the signal is component-level ("c'est bon" after a specific component), Claude proposes one harvest block immediately for that component. If the signal is session-level (merge, PR, commit), Claude proposes one harvest block per new component type built in that session, in sequence.

### Process

1. Claude detects approval signal on a completed component
2. Claude proposes the harvest block, pre-filled with source, code, lessons
3. **Validation Gate** — Claude évalue la maturité du pattern (voir section ci-dessous)
4. User validates the harvest block + Gate classification
5. Claude writes to the appropriate file — `components.md` si validé, `reference/experimental/` si expérimental
6. If the component was listed in the Gap Registry → remove that row. Note: the Gap Registry lives inside `protocols.md` itself — removing a row means editing that file directly.

### Validation Gate

Avant d'écrire dans `components.md`, Claude évalue la maturité du pattern en 1 round.

**Question interne :** "Ce pattern est-il assez mature pour être non-négociable ?"

Critères (1 round, pas de spirale de justification) :

| Critère | Évaluation |
|---------|-----------|
| **Proven** | Vu fonctionner sur ≥ 1 projet réel (pas juste "ça marche dans cette session") |
| **ARIA complet** | `aria-expanded`, `aria-label`, `role` présents si le composant est interactif |
| **Mobile-ready** | Touch targets 48px respectés OU design-system token utilisé |

**Classification :**

| Score | Destination |
|-------|-------------|
| 2/3 critères ou plus | → `components.md` avec `(proven: 1 project)` |
| 1/3 ou moins | → `reference/experimental/[component-name].md` |

Claude annonce la classification avant d'écrire :

```
Validation Gate : [composant]
✓ Proven — [oui/non, pourquoi]
✓ ARIA — [oui/non, ce qui manque]
✓ Mobile — [oui/non, ce qui manque]

Classification : [components.md / experimental] — confirme ou corrige.
```

L'utilisateur confirme ou corrige la classification. Après confirmation → écriture.

### Harvest template

```markdown
## [Component Name]
**Source:** [project] ([date])
**When:** [context — when this component applies]

```[language]
[minimal but complete code snippet]
```

**Lessons:**
- [transferable insight 1]
- [transferable insight 2]
```

### Annotation rules (inherited from SKILL.md)

- Add `(proven: 1 project)` on first harvest
- Increment counter on subsequent harvests
- If a better version exists → replace, annotate why

---

## Gap Registry

Known gaps as of 2026-03-22. Rows are removed after successful harvests.

| Missing component | Technical sources | Visual sources |
|---|---|---|
| Hero section | shadcn, 21st.dev | Landing.love, Awwwards |
| Pricing cards | shadcn, Landingfolio | Saaspo |
| Testimonials carousel | shadcn, 21st.dev | Mobbin, Collect UI |
| Onboarding flow | shadcn, HeroUI | Mobbin |
| Stats / metrics section | Magic UI | Saaspo |
| Multi-step form | shadcn + react-hook-form | Collect UI |
