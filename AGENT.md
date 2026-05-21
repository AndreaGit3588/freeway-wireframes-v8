# Freeway — Builder.io Agent Context

## What This Product Is

Freeway is **career positioning intelligence** — an adaptive platform that matches ambitious talent with the businesses they want to build with. It is built on top of a Phoenix startup data product (Dealroom-powered, 2,020+ funded companies).

**Not** a job board, ATS, LinkedIn competitor, resume portal, or bootcamp. The category is: **career positioning intelligence.**

Two-sided ecosystem: talent transitions toward founding; founders hire from the curated pool.

---

## Design System Summary

### Color Tokens

| Token | Hex | Usage |
|---|---|---|
| Background cream | `#F5F2EC` | Page canvas — always |
| Deep obsidian | `#100C2E` | Primary headings |
| Midnight circuit | `#20175C` | Body text, borders |
| Muted plum | `#5A537A` | Secondary text |
| Lavender | `#534AB7` | AI/system signals, active states |
| Lavender light | `#9384FB` | Atmospheric accents |
| Pink | `#C366A2` | Interaction signals ONLY — arrows, CTAs, links |
| Pink light | `#E07DBD` | Atmospheric/accent only |
| Live green | `#1D9E75` | Strong/live indicators |
| Deep green | `#0F6E56` | Text borders |
| Hairline | `#D9D2C2` | Dividers |

**Critical rule: Pink is reserved for interaction signals only.** Never decorative. Never on body text.

### Typography

- **Font:** Plus Jakarta Sans (Google Fonts) — weights 400, 500, 600, 700
- **Icons:** Tabler Icons CDN `@tabler/icons-webfont@3.0.0`

| Element | Size | Weight | Notes |
|---|---|---|---|
| Hero h1 | 38–44px | 500 | letter-spacing -1.2px, line-height 1.05 |
| Section title | 22px | 500 | letter-spacing -0.5px |
| Card title | 15–17px | 500 | letter-spacing -0.3px |
| Body | 12–14px | 400 | color rgba(32,23,92,0.65), line-height 1.5 |
| Eyebrow label | 10px | 700 | uppercase, letter-spacing 1.5px |

### Surface System (Frosted Glass)

Every card, panel, and pill uses this treatment:

```css
background: rgba(255, 255, 255, 0.55);
backdrop-filter: blur(60px) saturate(180%);
border: 0.5px solid rgba(255, 255, 255, 0.7);
box-shadow:
  0 1px 2px rgba(32, 23, 92, 0.03),
  0 12px 36px rgba(32, 23, 92, 0.04),
  inset 0 1px 0 rgba(255, 255, 255, 0.85);
border-radius: 20–24px;
```

---

## Core Component Vocabulary

| Class | Description |
|---|---|
| `.fw-canvas` | Cream background container |
| `.fw-atmos` | Fixed atmospheric layer (gradient pools, grain, vignette) |
| `.fw-topbar` | Always-visible top navigation row |
| `.fw-dock` | Pill-shaped glass navigation container |
| `.fw-dock-tab` | Individual nav tabs |
| `.fw-search-pill` | Search input pill |
| `.fw-goal-chip` | Toggleable goal chips (active = lavender) |
| `.fw-primary-move` | Dark plum dominant action panel |
| `.fw-primary-cta` | Pink Resume/Continue CTA button |
| `.fw-module` | Standard glass card surface |
| `.fw-opp` | Opportunity row (Home page) |
| `.opp-card` | Opportunity card (Opportunities page) |
| `.fw-pulse` | Ecosystem pulse band at page bottom |

---

## Wireframes in This Repo

| File | Screen |
|---|---|
| `wireframes/freeway-dashboard.html` | Main dashboard / home |
| `wireframes/freeway-opportunities-list.html` | Opportunities browsing |
| `wireframes/freeway-academy.html` | Academy / learning |
| `wireframes/freeway-network.html` | Network / connections |
| `wireframes/freeway-component-reference.html` | Full component library |
| `wireframes/freeway-layout-guide.html` | Layout and spacing guide |
| `wireframes/freeway-customer-journey.html` | User journey map |

Full design system documentation: `docs/freeway-handoff.md`

---

## Component Generation Rules

When generating new components or screens:

1. **Always use the cream canvas** `#F5F2EC` — no white or grey backgrounds
2. **Apply frosted glass** to every card surface
3. **One dominant action panel** per screen (dark plum `.fw-primary-move`)
4. **Max 6–7 decision points per screen** — no dense grids
5. **Pink only on interactive elements** — links, CTAs, arrows
6. **Lavender for AI/system signals** — module headers, match indicators
7. **Tabler Icons** for all iconography
8. **Plus Jakarta Sans** for all text
9. **Animations must be calm** — minimum 1 second, atmospheric pulses 20–32 seconds
10. **No gamification language** — no scores, ranks, badges, leaderboards
