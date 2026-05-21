# Freeway — V8 Wireframes

Design handoff for Builder.io development. Contains interactive HTML wireframes, logo assets, and full design system documentation.

## What's Here

```
wireframes/         — 7 interactive HTML screens (V8)
assets/logo/        — Logo files (SVG + PNG, multiple variants)
docs/               — Full design system + handoff documentation
AGENT.md            — Builder.io AI context (component rules, tokens, system)
.builderrules       — Builder.io code generation conventions
```

## Wireframes

| Screen | File |
|---|---|
| Dashboard / Home | `wireframes/freeway-dashboard.html` |
| Opportunities | `wireframes/freeway-opportunities-list.html` |
| Academy | `wireframes/freeway-academy.html` |
| Network | `wireframes/freeway-network.html` |
| Component Reference | `wireframes/freeway-component-reference.html` |
| Layout Guide | `wireframes/freeway-layout-guide.html` |
| Customer Journey | `wireframes/freeway-customer-journey.html` |

Open any HTML file directly in a browser — no build step needed.

## Using with Builder.io

1. Connect this repo to your Builder.io workspace
2. `AGENT.md` provides the design system context for AI code generation
3. `.builderrules` sets component conventions and anti-patterns
4. Use `wireframes/freeway-component-reference.html` as the primary component inventory
5. Full design token and pattern documentation in `docs/freeway-handoff.md`

## Design System Quick Reference

- **Canvas:** `#F5F2EC` cream background — always
- **Font:** Plus Jakarta Sans (Google Fonts)
- **Icons:** Tabler Icons
- **Cards:** frosted glass (`backdrop-blur`, `bg-white/55`, `border-white/70`)
- **Pink `#C366A2`:** interaction signals only — CTAs, links, arrows
- **Lavender `#534AB7`:** AI/system signals only

See `docs/freeway-handoff.md` for full token reference, component patterns, and design principles.
