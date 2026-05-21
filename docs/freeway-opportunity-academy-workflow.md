# Freeway — Opportunity → Academy Workflow Spec

## Overview

A connected flow across three screens that links a role a user wants to an intelligent Academy recommendation. When a user finds an opportunity they're interested in but isn't fully ready for, Freeway shows them exactly what's missing and routes them directly to the Academy modules that close the gap. Applying to a role enrolls them and lights up the recommended modules on the Academy screen.

---

## The Three Screens

| Screen | File |
|---|---|
| Opportunities list (with career path banner + sidebar) | `wireframes/freeway-opportunities-list_V2.html` |
| Opportunity detail modal (skill gap + Academy rec) | `wireframes/freeway-opportunity-modal.html` |
| Academy recommended state (glowing modules) | `wireframes/freeway-academy-recommended.html` |

---

## Screen 1 — Opportunities List

### Career Path Banner (top, dark plum)

Always visible above the opportunity list. Shows the user's current position, what they're building toward, and their target role as a 3-node flow with a connecting gradient line.

- **Node 1 (left):** Where you are — current role/title
- **Node 2 (center):** Building toward — transitional state
- **Node 3 (right):** Target — goal role, glowing pink dot

**Progress bar** sits in the footer of the banner. After a user applies to a role, a live pill appears next to the progress bar showing the applied role name + company with a pulsing pink dot.

> Applied state example: `● Head of Product · Lyra Health — applied`

### Organic Academy Nudge (inline, between opportunity rows)

A lavender-tinted card placed naturally between opportunity rows — not a banner, not a popup. Low pressure.

- Lavender gradient icon (Academy icon)
- Eyebrow: `ACADEMY`
- Headline: "Close the gap on 3 roles you're almost ready for"
- Subtext: Specific to the user's skill gaps and nearby opportunities
- CTA: "Explore Academy →" in lavender

**Rules:**
- One per page, never at the top
- Never interrupts the first 2 rows
- Does not use "upgrade", "unlock", or gamification language

---

## Screen 2 — Opportunity Detail Modal

Triggered when the user clicks any opportunity row. Opens as a centered overlay with a blurred backdrop.

### Modal Structure (top to bottom)

**Header**
- Company logo tile (gradient initials)
- Role title, company name, stage, location, salary range
- Tag pills: role type, stage, location, employment type, posting age
- Close button (top right)

**Skill Readiness Section**

A scannable checklist showing matched vs. missing skills:

- Badge: `X skills to close` in pink
- Subtext: "You're close — build these and this becomes a strong match."
- Each skill row has a status icon:
  - Green checkmark circle = user has this skill
  - Pink alert circle = not yet on their profile
- Label: skill name
- Meta: "You have this" or "Not yet on your profile"

**Academy Recommendation Box** (lavender-tinted, below skill rows)

- Lavender gradient icon + label: `RECOMMENDED IN ACADEMY`
- Title: "X modules will close this gap"
- Module list: each module shows icon, name, session count, and a `Closes gap` pill
- Primary CTA button (full width, lavender gradient): "Go to Academy — enroll in these modules →"

**Footer**

- Save button (secondary, ghost)
- Apply button (primary, pink): "Apply to this role →"
- Note below buttons: "Applying adds this role to your opportunity path and enrolls you in recommended Academy modules."

### On Apply

1. Modal closes
2. Applied role pill appears in the career path banner progress bar (pulsing dot + role name + company)
3. User is enrolled in the recommended Academy modules
4. Academy tab shows a notification pip

---

## Screen 3 — Academy (Recommended State)

This is the Academy screen as it appears after a user applies to a role or clicks "Go to Academy" from the modal.

### Sidebar Changes

An **Opportunity Tracker** card appears at the top of the sidebar above the filter sections:

- Label: `APPLIED ROLE`
- Role name + company
- Progress bar (starts near 0%, fills as modules are completed)
- Meta: "X modules recommended to close skill gap"

### Recommended Modules (top section)

Section header: "Recommended for [Role Title] · [Company]" with a "View role →" link in pink on the right.

Recommended modules appear in a 2-column grid **above** all other modules. Each recommended card has:

**Visual treatment — glowing outline:**
```css
border: 2px solid #534AB7;
box-shadow:
  0 0 0 4px rgba(83,74,183,.1),
  0 0 24px rgba(83,74,183,.2);
animation: moduleGlow 3s ease-in-out infinite;
```

**Badge:** Top-right corner — pulsing pink dot + `RECOMMENDED` label on lavender gradient pill

**Tag below badge:** "Closes skill gap for this role" in lavender, with a search icon

**Enroll button:** Full-width lavender gradient button at the bottom of the card — "Enroll now"

### Other Modules

Standard modules appear below in the same grid with no special treatment. They are still browsable and accessible — recommended modules don't gate anything.

---

## Design Rules for This Workflow

1. **Never use "you're not ready" language** — frame as "you're close" and "build toward"
2. **Skill gaps are evidence, not scores** — no numerical readiness %, no match scores on the gap section
3. **Academy is a path, not a requirement** — "Go to Academy" is always a CTA, never a gate to applying
4. **Apply is always accessible** — users can apply without going to Academy. The note below the button explains enrollment happens automatically on apply.
5. **Glow is calm** — the module glow animation is 3s ease-in-out. Not flashing, not urgent. It draws the eye without shouting.
6. **One recommended section, not scattered** — all recommended modules group together at the top. Once enrolled, they move to an "Enrolled" filter in the sidebar.
7. **Pink stays on interaction** — Apply button, "View role" link, "Go to Academy" CTA are pink. The recommendation box and module highlights are lavender (system signal).

---

## Voice Notes

- Skill gap label: "X skills to close" not "missing X skills"
- Academy nudge headline: "Close the gap on roles you're almost ready for" not "Improve your profile"
- Enroll CTA: "Enroll now" not "Start learning" or "Unlock"
- Apply note: "Applying adds this role to your opportunity path" — ownership language, not tracking language
- Academy section header: "Recommended for [Role]" not "Skills needed for [Role]"
