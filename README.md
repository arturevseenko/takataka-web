# TakaTaka Records — Website

> Underground electronic music label — Saint Petersburg  
> Microhouse · Minimal Wave · Underground Movement

---

## Repository Structure

```
takataka-web/
│
├── index.html                        ← Main page (current version)
├── booking.html                      ← Booking page with file upload
├── cart.html                         ← Merch cart and checkout
├── takataka-website.html             ← ⚠️ REFERENCE ONLY — original prototype
│
├── fonts/
│   ├── Gilroy/                       ← Gilroy woff2 (Heavy, ExtraBold, Bold, SemiBold, Medium, Regular, Light)
│   └── SpaceMono/                    ← Space Mono woff2 (Regular, Bold, Italic, BoldItalic)
│
├── assets/
│   └── logo.svg                      ← TakaTaka SVG logo (currentColor)
│
├── design-system/
│   ├── tokens.css                    ← All CSS variables / design tokens
│   ├── components.html               ← All UI component patterns
│   └── brand-notes.md                ← Plain-text brand context for Claude Design
│
├── DESIGN_SYSTEM.md                  ← Full design system documentation
├── CLAUDE.md                         ← AI agent workflow instructions
├── ENGINEERING_GUIDE.md              ← Code quality standards
├── SKILL.md                          ← Discovery interview skill
└── README.md                         ← This file
```

---

## Pages

| Page                    | Description                                                        |
|-------------------------|--------------------------------------------------------------------|
| `index.html`            | Main: hero, releases, events, radio, shop, booking, contact       |
| `booking.html`          | Artist roster, EPK, booking request form + file upload            |
| `cart.html`             | Merch cart, checkout, promo code                                  |
| `takataka-website.html` | ⚠️ Reference prototype only — do not modify                       |

---

## Page Structure (index.html)

Sections in order:

1. **Nav** — fixed, logo left, links center, socials right
2. **Hero** — TAKA/TAKA lockup, perspective grid, vinyl artwork
3. **Ticker** — scrolling text strip
4. **Latest Release** — featured release, tracklist, stream buttons
5. **Releases** — 4-column grid, filter tabs
6. **Events** — upcoming shows with date, venue, city, ticket link
7. **Radio** — podcast episodes, sound wave visualizer, sticky player
8. **Shop** — 3-column merch grid, add to cart
9. **Booking** — set types + quick form + link to booking.html
10. **Contact** — 4-column email grid, social row
11. **Footer** — single minimal row

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
- `Gilroy` — all headings and display text (local woff2)
- `Space Mono` — everything else: body, labels, buttons, forms (local woff2)

**Hero title:** `TAKA` (solid white fill) / `TAKA` (outline only, `-webkit-text-stroke`)

Full documentation → `DESIGN_SYSTEM.md`  
All tokens → `design-system/tokens.css`  
All components → `design-system/components.html`

---

## Setting Up Claude Design

1. Go to [claude.ai/design](https://claude.ai/design) → onboarding → **Connect codebase**
2. Paste: `https://github.com/arturevseenko/takataka-web`
3. Upload fonts and logo from `fonts/` and `assets/` folders
4. Add notes from `design-system/brand-notes.md`

---

## Cart System

Cart state is stored in `localStorage` under key `tkt_cart`.  
All pages share the same cart. Items persist across sessions.

---

*TakaTaka Records — April 2026*
