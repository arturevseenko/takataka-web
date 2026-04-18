# CLAUDE.md — TakaTaka Project Instructions

> **Read this file first. Every time. Before touching any code.**
> This file orchestrates all other documentation for the TakaTaka Records website project.

---

## Project Overview

**TakaTaka Records** — independent underground electronic music label, Saint Petersburg.  
**Stack:** Vanilla HTML + CSS Variables + Vanilla JS. No frameworks, no build tools, no dependencies.  
**Pages:** `index.html` (main), `booking.html`, `cart.html`  
**Reference:** `takataka-website.html` (original prototype — do not modify, reference only)

---

## Documentation Structure

| File                  | Purpose                                      | When to Read              |
|-----------------------|----------------------------------------------|---------------------------|
| **CLAUDE.md** (this)  | Workflow, project context, quick rules        | Always — read first       |
| **DESIGN_SYSTEM.md**  | Colors, typography, spacing, components       | Any UI/visual change      |
| **ENGINEERING_GUIDE.md** | Code quality, structure, review standards | Any logic/structure change|

### Decision Tree

```
Incoming task
    │
    ├─ Visual / layout / styling?
    │   └─> Read DESIGN_SYSTEM.md
    │
    ├─ Interactivity / JS / refactor / performance?
    │   └─> Read ENGINEERING_GUIDE.md
    │
    └─ New page / feature / full section?
        └─> Read BOTH
```

---

## Workflow: Always Plan Before Coding

### Step 1 — Classify the task

**BIG** (plan required, wait for approval):
- New page or full section
- Changing layout structure
- Adding new interactive feature
- Changing multiple files

**SMALL** (proceed directly):
- Color/text adjustment
- CSS fix in one component
- Adding one element matching existing pattern
- Copying existing component to new location

### Step 2 — Read the right docs

Always read this file.  
Then DESIGN_SYSTEM.md for visual, ENGINEERING_GUIDE.md for logic, or both.

### Step 3 — For BIG tasks: present a plan

```
## Plan: [Task Name]

Files to modify: [list]
Approach: [steps]
Design system check: [what I verified in DESIGN_SYSTEM.md]
Potential issues: [list]

Proceed?
```

### Step 4 — Implement

For each file change:
- Follow DESIGN_SYSTEM.md patterns exactly
- Match existing code style (indentation, naming)
- Test in browser (open file, check desktop + mobile)

---

## TakaTaka-Specific Rules (Memorize These)

### Design

1. **Monochrome only** — `--black`, `--white`, `--gray`, `--gray2`, `--mid`, `--dim`. Nothing else.
2. **Hero title:** L1 = filled white, L2 = outline only (`-webkit-text-stroke`). Never change this.
3. **Fonts:** Bebas Neue for headings / display. Space Mono for everything else. No exceptions.
4. **Hover on cards:** border reveals (`border-color` only), never background color.
5. **No border-radius** except cursor (50%) and cart counter (50%).
6. **No box-shadows** — flat design, depth through color only.

### Code

7. **No frameworks** — Vanilla JS and CSS only. No React, Vue, Alpine, jQuery.
8. **No new external dependencies** — Fonts from Google Fonts is OK. Nothing else.
9. **Cart in localStorage** — key: `tkt_cart`. All three pages share this.
10. **Custom cursor on every page** — `.cursor` + `.cursor-ring` + JS. Don't remove or forget.
11. **Single-file pages** — All CSS and JS stays inline in each HTML file. No separate files.
12. **`.reveal` system** — Every new section element should have the `.reveal` class for scroll animation.

### Don'ts

- Never add `accent`, `primary`, `success`, `danger` color concepts — this is not a UI framework project
- Never use `transition-all` on anything larger than a button
- Never add `box-shadow` or `border-radius` to cards/sections
- Never introduce a build step or package.json
- Never modify `takataka-website.html` — it is a frozen reference

---

## Pages: What Each File Does

### index.html — Main Page
Sections in order:
1. Nav (fixed, with cart icon, login, burger)
2. Hero (TAKA / TAKA lockup, perspective grid, vinyl artwork)
3. Ticker (scrolling text strip)
4. Latest Release (artwork + tracklist + stream buttons)
5. Releases (4-col grid, filter tabs)
6. News (3-col grid)
7. Radio / Podcast (episodes + sticky player)
8. Merch (3-col, add to cart)
9. Contact / Connect (4-col email grid + social row)
10. Footer (simple single row)

Interactive: cart drawer, auth modal, burger/drawer, filter tabs, scroll reveal, custom cursor.

### booking.html — Booking Page
Sections: Nav → Roster → EPK → Request Form (with file drag-and-drop upload)  
Interactive: File upload with progress, format tabs (DJ Set / Live / B2B), auth modal, cart.

### cart.html — Cart Page
Sections: Nav → Cart items → Promo code → Order total → Checkout form  
Interactive: Remove items, qty adjustment, promo code, payment form.

---

## Adding a New Section — Checklist

When adding a new section to any page:

```
□ Uses section.section-wrap (or appropriate wrapper with correct padding)
□ Has a .section-label with dash line
□ Has .reveal on animated elements
□ Background alternates: --black / --gray (check neighboring sections)
□ No new colors introduced
□ Followed existing component pattern from DESIGN_SYSTEM.md
□ Mobile responsive (check at 768px and 480px)
□ Added a .divider before or after if between major sections
```

---

## Adding Interactivity — Checklist

```
□ Vanilla JS only
□ No new global variables (namespace or use const/let in scope)
□ Error handling: what if element doesn't exist on this page?
□ localStorage usage consistent with existing cart pattern
□ Works without breaking cart, auth modal, or cursor
□ Tested: click, hover, keyboard (if applicable)
```

---

## Response Format

### Planning Phase
```
## Plan: [Name]
Scope: BIG / SMALL
Files: [list]
Approach:
1. ...
2. ...
Design system: [what I confirmed]
Issues: [if any]
→ Proceed? [Y/N]
```

### After Implementation
```
✅ Done: [what changed]
Files modified: [list]
Pattern used: [from DESIGN_SYSTEM.md section X]
Test: [what to check in browser]
```

---

## Start of Session Protocol

When the user starts a new task, respond:

```
📋 [Task summary]

Scope: BIG / SMALL
Reading: DESIGN_SYSTEM.md [yes/no] · ENGINEERING_GUIDE.md [yes/no]

[Plan or immediate action]
```

---

## Hard Rules — Never Break

1. **Read DESIGN_SYSTEM.md before any visual change**
2. **Don't introduce colors not in the palette**
3. **Don't change the hero title treatment** (L1 fill / L2 outline)
4. **Don't add frameworks or build tools**
5. **Don't modify `takataka-website.html`**
6. **Always keep custom cursor on every page**
7. **Cart must use `tkt_cart` localStorage key**
8. **Mobile must work — check all breakpoints: 1100, 900, 768, 480px**

---

*TakaTaka Records — April 2026*
