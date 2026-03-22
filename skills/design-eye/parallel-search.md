---
name: parallel-search
description: "Multi-source parallel research mechanics for design-eye. Load when launching research on 2+ independent sources. Defines agent brief format, source distribution, compilation, and failure fallback."
---

# Parallel Search

Load this module before launching any research involving 2+ independent sources.

## Decision rule

- 1 source → direct WebFetch, no agents
- 2+ sources → background agents, one per source (use Agent tool with `run_in_background: true`)

## Agent brief format (all fields mandatory)

Each agent receives a brief containing:
1. **Source URL + entry point** — exact URL to open, which page/category/filter to start from
2. **Filter/category** — which visual style filter or section to browse
3. **What to find** — specific target: ambiance, component type, color approach, layout pattern
4. **What to ignore** — noise reduction: "ignore dark mode results", "skip illustrations", etc.
5. **Return format** — max 300 words + 3–5 specific page URLs (not gallery thumbnails)

Each agent returns a synthesis. Never raw content. The main context only sees compiled results.

## Default source distribution

| Agent | Source | Default mandate |
|-------|--------|-----------------|
| 1 | Landing.love | Visual style category matching the brief |
| 2 | Land-book | Same visual filter, different curation |
| 3 | Saaspo | SaaS or digital product references (skip if non-digital) |
| 4 | 21st.dev | Specific UI components mentioned in brain dump |
| 5 | Direct web search | Sites from the client's exact sector |
| 6–10 | Named competitors | Comparative analysis of identified competitors |

Agents 6–10 are optional. Only launch them if competitors or specific sites were named in the brain dump.

## Compilation

After all agents complete:
1. Merge all results into a single list, deduplicated
2. Assign a letter (A, B, C...) to each distinct site
3. Load output-formats.md and present using Format 1

## Failure fallback

If an agent returns an error or empty results after 2 attempts:
- Mark that source as "unavailable — [source name]" in the synthesis
- Proceed with results from remaining agents
- If fewer than 2 agents succeed → fall back to sequential WebFetch for the missing sources
- Never block the flow or wait indefinitely for a failed agent
