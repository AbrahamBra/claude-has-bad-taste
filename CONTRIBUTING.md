# Contributing

## How to Contribute

### Add patterns from your projects

Every example should follow this format:

```markdown
### [Pattern Name] (proven: N projects)
**Source:** [project-name] (YYYY-MM)
**When:** [context where this pattern applies]

[Code example]

**Lessons:**
- [Transferable insight]
```

- `**Source:**` is mandatory — it traces where the pattern was first used
- `**When:**` helps others know if the pattern applies to their project
- `(proven: N projects)` — add once validated across multiple builds

### Replace existing patterns

Examples compete. If your version of a component, effect, or pattern is better than the current one, propose it. The best version wins.

When replacing, note why: "Replaces [old pattern] because [reason]."

### Add localizations

Client-facing prompts (brain dump, feedback loops) in your language are valuable. Add them under `### Localization: [Language]` subsections.

The brain dump prompt in `design-eye` is the most important piece to localize — it sets the tone for the entire project.

### Report what doesn't work

If a pattern caused problems in your project, open an issue. Include:
- Which pattern
- What went wrong
- What you did instead

## Guidelines

- Keep code examples real. No theoretical snippets.
- Include both what TO do and what NOT to do.
- Maintain the `**Source:**` annotation convention.
- Test in Claude Code before submitting.
- Keep the non-negotiable standards non-negotiable.

## File Structure

- **design-eye/SKILL.md** — aesthetic calibration process
- **design-signature/SKILL.md** — visual effects and patterns
- **expertise-web/SKILL.md** — technical hub (short, references modules)
- **expertise-web/reference/*.md** — detailed pattern modules (add new patterns here)
