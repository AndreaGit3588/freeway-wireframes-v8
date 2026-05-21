# Freeway — Project Handoff & Design System

**For the next Claude picking up this work.** Read this end-to-end before designing anything. The HTML files (`freeway-demo.html`, plus separate `home`/`network`/`academy` versions) are the canonical source of truth — pull tokens, components, and patterns from them directly. This document is the orienting brief.

---

## 1. What Freeway Is

**Freeway is career positioning intelligence** — an adaptive platform that matches ambitious talent with the businesses they want to build with. Built on top of an existing Phoenix startup data product (`ecosystem.freewayphx.com`, powered by Dealroom — 2,020 funded companies, 2,282 rounds). The talent-side product we're designing sits as a *personalized lens* on top of that data layer.

**It is not:** a job board, an ATS, a LinkedIn competitor, a resume-matching portal, a bootcamp, or an LMS. Push back hard if anyone tries to position it as those things — that framing kills the category.

**The category:** career positioning intelligence. The user has agency over how the system reads them, sees how it classifies them, and can shift it. That transparency is the moat.

**Two-sided ecosystem:** Talent transitions toward founding; founders hire from the talent pool. Closed loop.

**Primary user types:**
- Ambitious operators becoming founders
- Designers becoming product leaders
- Contributors becoming builders
- Anyone in the middle of professional transformation, becoming startup-ready

**Not the audience:** traditional job seekers, mid-career corporate switchers looking for stability, people who think of work as "remote-first preferences."

---

## 2. Voice & Messaging

### Approved headline stack (current)
> **Creating your next opportunity.**
> *You don't have to build alone.*
> *Experience your match.*

### Approved supporting copy
> AI intelligence, a founder network, and an academy.
> Matching ambitious talent with the businesses they want to build with.
> *A curated community of operators, founders, and the people who back them.*

### Approved closing line (forward-looking, no competitor comparison)
> Matching people to *what they're becoming* — not *what they were.*

### Page-specific headlines that landed
- **Home:** "Discover your next role."
- **Network:** "You're moving. Here's who's moving with you." (alt: "Move from operator to builder.")
- **Academy:** "Who are you becoming?"
- **Opportunities:** "Opportunities matched to where you are."

### Voice rules (these matter)

**Always:**
- Forward-looking, declarative, calm
- Names what we *are*, not what we're *better than*
- "Becoming" / "in transition" / "ambitious" / "curated" / "ecosystem"
- "Match" as an action word — the system matches you to opportunity
- AI-era language without buzzword energy (no "revolutionary," "disrupting," "game-changing")

**Never:**
- Comparative framing ("unlike other platforms," "every other system")
- Gamification ("score," "rank," "leaderboard," "XP," "level up")
- KPI/dashboard energy ("optimize," "boost your rate by 25%")
- Hustle culture ("crush it," "10x," "grind")
- LinkedIn badge culture ("certified," "verified," achievement-obsessed)
- Generic startup-guru motivational language
- "Job seeker," "resume," "applicant," "candidate" — these flatten people

**Tone reference points:**
- Linear (calm, intentional, restrained)
- Stripe documentation (clear, confident, no hype)
- Pre-COVID General Assembly (clear named outcomes, not bootcamp energy)

---

## 3. Brand System — Visual Tokens

### Colors (use exactly these hex values)

```
Background (cream / pearl)       #F5F2EC
Deep obsidian (headings)         #100C2E
Midnight circuit (body text)     #20175C
Muted plum (secondary text)      #5A537A
Lavender (AI/system signal)      #534AB7
Lavender light (atmospheric)     #9384FB
Pink (interaction only)          #C366A2
Pink light (atmospheric/accent)  #E07DBD
Live/strong indicator green      #1D9E75
Deep green (text/borders)        #0F6E56
Hairline rule                    #D9D2C2
White card backing               #FFFFFF
```

### Color rules (critical)
- **Pink is reserved for interaction signals only** — arrows, "View all" links, the Resume CTA, the "interpret/becoming" italic emphasis in closing lines. Never decorative. Never on body text. Never as a primary surface color.
- **Lavender is for AI/system signals** — module headers, signal bars, calibration indicators, "Currently surfacing" chips.
- **Cream is the canvas** — every surface lives on `#F5F2EC`. No white or grey page backgrounds.
- **Plum/obsidian is the dominant text color** — heading hierarchy, body text, navigation states.

### Typography

```
Primary font (UI):    Plus Jakarta Sans (Google Fonts)
Weights used:         400 (regular), 500 (medium), 600 (semibold), 700 (bold)
PDF fallback font:    Helvetica Neue / Helvetica (system)
Icon font:            Tabler Icons (CDN: @tabler/icons-webfont@3.0.0)
```

**Type scale (matches the HTML files):**
- Hero h1: 38–44px, weight 500, letter-spacing -1.2 to -1.4px, line-height 1.05
- Headline accent (the muted/italic continuation): same size, color rgba(32,23,92,0.45), weight 400
- Section title: 22px, weight 500, letter-spacing -0.5px
- Card name: 15–17px, weight 500, letter-spacing -0.3px
- Body: 12–14px, weight 400, color rgba(32,23,92,0.65–0.7), line-height 1.45–1.55
- Eyebrow label: 10–10.5px, weight 600–700, letter-spacing 1.4–1.8px, uppercase
- Tiny meta: 9–10px, weight 600–700, letter-spacing 1.3–1.5px, uppercase

**Heading pattern:** Most headlines use a two-part structure — the bold statement followed by an italic muted continuation that completes the thought, e.g., *"Trusted infrastructure for **building.**"* where "building" is colored muted/grey. The italic continuation often softens or extends the main beat.

### Surface system (the "frosted glass" aesthetic)

Every card, panel, and pill uses this exact treatment:

```css
background: rgba(255, 255, 255, 0.55);     /* 0.4–0.6 range, never opaque */
backdrop-filter: blur(60px) saturate(180%);
-webkit-backdrop-filter: blur(60px) saturate(180%);
border: 0.5px solid rgba(255, 255, 255, 0.7);
box-shadow:
  0 1px 2px rgba(32, 23, 92, 0.03),
  0 12px 36px rgba(32, 23, 92, 0.04),
  inset 0 1px 0 rgba(255, 255, 255, 0.85),
  inset 0 -0.5px 0 rgba(32, 23, 92, 0.03);
border-radius: 20–24px;
```

**Top-edge highlight:** Every elevated surface has a 1px gradient highlight inset 12–15% from each edge, creating a subtle "glass top" effect:

```css
.surface::before {
  content: '';
  position: absolute; top: 0; left: 14%; right: 14%; height: 1px;
  background: linear-gradient(90deg, transparent, rgba(255,255,255,0.95), transparent);
}
```

### Atmosphere (the breathing background)

Two animated radial gradient "pools" sit fixed behind everything:

```css
.fw-atmos { position: fixed; inset: 0; pointer-events: none; z-index: 0; overflow: hidden; }
.fw-atmos .pool { position: absolute; border-radius: 50%; filter: blur(60px); }

.fw-atmos .key {  /* top-right pink pool */
  top: -400px; right: -300px; width: 1000px; height: 1000px;
  background: radial-gradient(circle, rgba(255,180,200,0.18) 0%, rgba(224,125,189,0.06) 35%, transparent 65%);
  animation: fwBreathe1 24s ease-in-out infinite;
}
.fw-atmos .rim {  /* bottom-left lavender pool */
  bottom: -340px; left: -220px; width: 800px; height: 800px;
  background: radial-gradient(circle, rgba(147,132,251,0.09) 0%, transparent 65%);
  animation: fwBreathe2 28s ease-in-out infinite;
}
```

Plus a subtle grain overlay and a vignette. **These atmospheres are essential to the brand feel** — don't omit them on new screens.

### Animations
- All breathing/glow animations are 20–32 second loops, ease-in-out
- Surface glow pulses on active states are 4 second loops
- Live/strong indicator dots pulse 2.4–2.8 seconds
- Signal bars animate 1.4 seconds (calibrating equalizer)
- Avoid anything faster than 1 second — the whole system should feel calm

---

## 4. Core Components

These are the reusable building blocks. Pull them straight from `freeway-demo.html`.

### Top bar
Always present, always identical across pages:
- **Logo** (left) — real Freeway logo image, 28px height, embedded as PNG data URI
- **Dock nav** (center) — pill-shaped glass container with tabs: Home, Opportunities, Academy, Network, Services, Coach (the last two dimmed, "coming soon")
- **Right cluster:**
  - Search pill (becomes editable input on click — inline, not modal)
  - Filter button — **square** (10px radius, 36×36px) to distinguish from circular bell. Active state = lavender gradient + pink count pill at top-right corner
  - Bell (circular, with pink notification dot)
  - Avatar pill — small gradient circle + first name

### Goal chips (system-wide primitive)
Four chips representing the user's active goals: *Find customers · Find capital · Find talent · Increase rate*. Toggleable, persist via localStorage, shown on every page. Active state uses lavender gradient. Daniela's note: "user should be able to change their goals and the system intelligently recalibrates."

Default active: `['customers', 'rate']`

### Dominant action panel (dark plum)
Used for "Today's move" (Academy), "Operator becoming builder" (Network transition flow), and similar primary actions. Dark plum gradient background (`#100C2E` → `#20175C`), pink atmospheric glow in corner, pink CTA button. One per page, always the visual anchor.

### Opportunity / event / signal card patterns
See `freeway-home.html` and `freeway-demo.html` Opportunities section. Each card has:
- Company logo tile (gradient with initials)
- Bookmark icon (toggles filled/unfilled)
- Role title + company line + 3 small tags (stage, type, location)
- Match pill (lavender "Strong match" or pink "Hiring fast"/"Stretch match")
- One-line *why this matches you* explanation
- Salary + posting age in footer

### Ecosystem pulse band
Single-line dark-tinted band at the bottom of most pages: ecosystem icon + "ECOSYSTEM PULSE" label + a sentence of ambient intelligence + a "See three more →" CTA. Doesn't shout, but it's there.

---

## 5. Design Principles (taste rules learned through iteration)

These are the user's strong preferences. Violate them at your peril.

1. **Tight loops, not catalogs.** Each screen should have one obvious next action. If you find yourself building a 6-card grid of options, you're probably wrong. The Academy page went from 21 decision points down to 6 through ruthless cutting.

2. **One dominant move per screen.** The dark panel ("Today's move," "Transition flow") is always the visual center of gravity. Everything else supports it.

3. **Goals as the organizing primitive.** Content reconfigures around the user's selected goals. Don't organize by "topic" or "category" — organize by *what the user is trying to do.*

4. **Transparent, not opaque.** Show how the system classifies the user. Let them shift it. Never hide the model.

5. **Calm, not loud.** Atmospheric. Frosted glass. Animations 20+ seconds. The product should feel like Linear, not Salesforce.

6. **Pink is precious.** Use it for interaction signals only. Decorative pink = bad demo.

7. **No gamification, no scoring, no badges, no leaderboards.** Anti-gamification is a core stance.

8. **Ecosystem language wins.** "Ecosystem," "founder network," "curated," "in transition," "becoming," "in motion," "signal" — these are the words that land.

9. **Drift sideways is good.** The Academy "Explore the library" section uses this phrase intentionally — it implies non-linear curiosity, not bootcamp progression.

10. **Compensation is evidence, not a score.** When rate ranges appear, they're labeled *"How the market reads this"* with the disclaimer *"A read of the market, not a rating of you."* Never gamify rate.

---

## 6. What's Built vs. What's Open

### Built and approved
- **Demo HTML** (single-file SPA with Home / Opportunities / Academy / Network sections, working dock navigation, search with keyword autocomplete, filter popout with dimming behavior, goal chip sync via localStorage, Academy module modal)
- **Visual one-pager PDF** (A4 portrait, hero copy stack, one big Home screenshot, three smaller thumbnails for Opportunities / Academy / Network, closing line)
- **Product slide** (widescreen, available as .pptx / .pdf / .png — left column copy, right column hero Home screen, closing footer)
- **Pitch deck** (5-slide .pptx — Title / Problem / Insight / Product / Moat)

### Open / not built
- **Onboarding / empty state flow** — how a brand-new user enters and sets goals for the first time. Daniela flagged this as worth designing before broader validation.
- **Profile / positioning detail view** — where founder-market alignment, rate evidence, and signal strength live in detail (not on the daily landing pages)
- **Business-side (founder) dashboard** — the *other* side of the two-sided ecosystem. Founders viewing talent, posting roles, browsing the curated pool. This is genuinely unbuilt.
- **Coach / Services screens** — currently dimmed "coming soon" tabs in the dock
- **Mobile-specific layouts** — current screens work on mobile but weren't designed for it
- **Sign-up / auth flows** — none exist yet

### Files the user has (or should have)
- `freeway-demo.html` — single-file interactive demo, ~170 KB
- `freeway-visual-one-pager.pdf` — A4 portrait visual one-pager, ~10 MB
- `freeway-slide.pdf` / `.png` / `.pptx` — product slide in three formats
- `freeway-pitch.pptx` — 5-slide pitch deck
- `freeway-logo-clean.png` — transparent PNG of the real Freeway logo (pink "ff" interchange mark + deep-plum wordmark)

---

## 7. Working With This User

**The user has strong design sensibility.** Push back from them is usually right. Patterns:

- They reject density. Whenever a screen has more than 6–7 decision points, expect a "too much going on" critique.
- They reject comparative framing. "Better than X" copy gets cut.
- They reject narrow audience framing. "Remote-first preferences" got cut for being too narrow; "for anyone in transformation" is the right register.
- They want to ship visible things. Hand them artifacts (files, screens, PDFs) rather than long explanations.
- They iterate by talking through what they want — sometimes meandering. Listen for the underlying instinct, not just the literal request. "Make it sound innovative" often means "name the three pillars by name."
- They appreciate when you push back honestly. If their request would weaken the design, say so. Don't just comply.

**Practical workflow:**
- Build, render, show. Visual QA every artifact before handing over.
- For HTML: render to image with Playwright + Chromium for visual review
- For PDF: render with `pdftoppm -jpeg -r 110-130` for review
- For PPTX: convert via LibreOffice (`soffice.py`) then render to image
- Keep the outputs folder clean — only canonical files, no scratch work

**One last note:** the user has been explicit that the design system is more important than any individual screen. New components should *feel like* the existing system — same surface treatments, same atmospheric layer, same component vocabulary. If you're building something genuinely new, mock it twice: once strictly inside the system, once with a small deliberate variation, and let the user pick.

---

## 8. Quick Reference — Component CSS Patterns

The cleanest way to learn the system is to view `freeway-demo.html` directly. But for fast reference, here are the most important class names and what they do:

```
.fw-canvas              -- the cream background container
.fw-atmos               -- the fixed atmospheric layer (pools, vignette, grain)
.fw-topbar              -- the always-visible top navigation row
.fw-wordmark            -- the Freeway logo container (28px height)
.fw-dock                -- the pill-shaped navigation container
.fw-dock-tab            -- individual nav tabs (active state: solid white)
.fw-search-pill         -- the search input pill
.fw-glass-icon          -- circular utility buttons (bell, etc.)
.fw-glass-icon.has-filters  -- the SQUARE filter button
.fw-avatar-group        -- the right-side avatar + name pill
.fw-workspace           -- the main content area, max-width 1200px or 1440px
.fw-page-head           -- compact header row with hero copy + goal chips inline
.fw-goal-chip           -- toggleable goal chips (active state: lavender)
.fw-goal-chip.active    -- the active state
.fw-primary-move        -- the dark plum dominant action panel
.fw-primary-cta         -- the pink Resume / Continue CTA button
.fw-module              -- standard glass card surface
.fw-section-head        -- section header with label + heading + "more" link
.fw-opp                 -- opportunity row item (Home page)
.opp-card               -- opportunity card (Opportunities page)
.fw-transition          -- the dark transition flow panel (Network)
.fw-flow                -- the three-node directional flow visualization
.fw-pulse               -- the ecosystem pulse band at page bottom
```

---

When you start working with the user, your first message should be brief: confirm you've read this, ask what we're designing today, and commit to staying inside the system unless they explicitly say otherwise.

Welcome to Freeway.
