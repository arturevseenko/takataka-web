# TakaTaka Records — Website

> Underground electronic music label — Saint Petersburg  
> Microhouse · Minimal Wave · Underground Movement

---

## Repository Structure

```
takataka-web/
│
├── index.html                        ← Main page (current monochrome version)
├── booking.html                      ← Booking page with file upload
├── cart.html                         ← Merch cart and checkout
├── takataka-website.html             ← ⚠️ REFERENCE ONLY — original prototype
│
├── design-system/
│   ├── tokens.css                    ← All CSS variables / design tokens
│   ├── components.html               ← All UI component patterns
│   └── brand-notes.md                ← Plain-text brand context
│
├── DESIGN_SYSTEM.md                  ← Full design system documentation
├── CLAUDE.md                         ← AI agent workflow instructions
├── ENGINEERING_GUIDE.md              ← Code quality standards
├── SKILL.md                          ← Discovery interview skill
└── README.md                         ← This file
```

---

## Setting Up Claude Design

Claude Design reads this repository during onboarding to build your design system automatically.

### Step 1 — Point Claude Design at this repo

Go to [claude.ai/design](https://claude.ai/design) → onboarding → **Connect codebase** → paste the GitHub repo URL.

Claude Design will read:
- `design-system/tokens.css` — all color and typography tokens
- `design-system/components.html` — all UI component patterns
- `design-system/brand-notes.md` — brand context and rules
- `DESIGN_SYSTEM.md` — full design documentation
- `index.html` — to understand the actual codebase

### Step 2 — Every project inherits the design system

After onboarding, every new project in Claude Design will automatically use:
- The monochrome color palette (`#080808`, `#f0ede6`, `#141414` etc.)
- Bebas Neue + Space Mono typefaces
- The TAKA/TAKA hero treatment (L1 filled / L2 outline)
- All component patterns (cards, buttons, labels, ticker etc.)

### Step 3 — Refine through conversation

Describe what you want. Claude Design will build it using the TakaTaka design system. Refine with inline comments, direct edits, or conversation.

### Step 4 — Export or hand off to Claude Code

Export as HTML, PPTX, PDF, or Canva. Or hand off directly to Claude Code for implementation.

---

## Working with Claude Code / Claude.ai Projects

If using Claude Code (terminal) or Claude.ai Projects:

| File to provide         | Why                                       |
|-------------------------|-------------------------------------------|
| `CLAUDE.md`             | Workflow instructions — read first always |
| `DESIGN_SYSTEM.md`      | Visual rules for any design task          |
| `ENGINEERING_GUIDE.md`  | Code standards for any logic task         |
| `index.html`            | Upload when working on main page          |

In Claude Code, `CLAUDE.md` is read automatically at session start.

---

## Design System Quick Reference

**Palette (monochrome only):**

| Token    | Value     | Usage                           |
|----------|-----------|---------------------------------|
| `black`  | `#080808` | Page background                 |
| `white`  | `#f0ede6` | Primary text, filled elements   |
| `gray`   | `#141414` | Alternate section background    |
| `gray2`  | `#1c1c1c` | Cards, panels                   |
| `mid`    | `#2e2e2e` | Borders, dividers               |
| `dim`    | `#555555` | Secondary text, labels          |

**Fonts:**
- `Bebas Neue` — all headings and display text
- `Space Mono` — everything else (body, labels, buttons, forms)

**Hero title:** `TAKA` (filled white) / `TAKA` (outline only, `-webkit-text-stroke`)

Full documentation → `DESIGN_SYSTEM.md`  
All tokens → `design-system/tokens.css`  
All components → `design-system/components.html`

---

## Pages

| Page                    | Description                                                 |
|-------------------------|-------------------------------------------------------------|
| `index.html`            | Main: hero, releases, news, radio, merch, contact          |
| `booking.html`          | Artist roster, EPK, booking request form + file upload     |
| `cart.html`             | Merch cart, checkout, promo code                           |
| `takataka-website.html` | ⚠️ Reference prototype only — do not modify                |

---

*TakaTaka Records — April 2026*
