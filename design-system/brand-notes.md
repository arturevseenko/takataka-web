# TakaTaka Records — Brand Notes for Claude Design

## What this project is

TakaTaka Records is an independent underground electronic music label based in Saint Petersburg, Russia.
Genre focus: microhouse, minimal wave, minimal house.
Releases: vinyl + digital. Events: club nights and festivals.

This website is the label's primary digital presence.
Pages: main (index.html), booking (booking.html), merch cart (cart.html).

---

## Aesthetic

**Underground editorial.** Think Factory Records, Ostgut Ton, Perlon — record labels whose visual identity is as considered as their music.

The design is deliberately restrained:
- Strict monochrome: black, off-white, and grays only
- No accent colors, no gradients with hue, no decorative noise
- Every visual element must earn its place
- White space is intentional — silence is part of the design

**References:** brutalist editorial layouts, underground club flyers from the 90s–00s, minimal Japanese print design.

---

## What Claude Design should know

### Do this when creating new visuals for TakaTaka:

1. **Stay monochrome.** The palette is: `#080808` (background), `#f0ede6` (white/text), `#141414` (gray), `#1c1c1c` (card bg), `#2e2e2e` (borders), `#555` (dim text). Nothing else.

2. **Use these two fonts only:**
   - `Bebas Neue` — all headings, section titles, display text
   - `Space Mono` — all body text, labels, buttons, forms, nav links

3. **Hero title rule:** The word "TAKA" appears twice stacked. Top line: solid white fill. Bottom line: outline only (transparent fill + thin white stroke). This is the signature treatment of the brand.

4. **Hover = border reveal.** Cards don't change background on hover. They reveal a subtle white border (`1px solid rgba(240,237,230,0.1)`).

5. **No border-radius** (except circular cursor and cart counter badge).

6. **No box-shadows.**

7. **Grids are tight.** Release and news tiles use `2px` gaps — like tiles touching, not card grids with generous spacing.

8. **Uppercase labels everywhere.** Section labels, buttons, nav links, badges — all uppercase, wide letter-spacing (0.2em–0.4em).

### Don't do this:

- No color accents of any kind — not even a subtle purple or teal tint
- No rounded corners on panels, cards, or buttons
- No card backgrounds changing on hover (border-only hover states)
- No decorative gradients with hue
- No emoji or playful illustration — this is serious underground music
- Don't mix in Inter, Helvetica, or any sans-serif that isn't Space Mono

---

## Page structure (index.html)

1. Fixed navigation (logo + links + cart icon)
2. Hero — full-screen, TAKA/TAKA lockup, perspective grid background, vinyl artwork
3. Ticker — scrolling horizontal text strip
4. Latest Release — featured release with artwork, tracklist, stream buttons
5. Releases grid — 4-column, filter tabs (All / Album / EP / Single)
6. News — 3-column grid
7. Radio/Podcast — episode list + sticky player
8. Merch — 3-column store grid with add-to-cart
9. Contact/Connect — 4-column email grid + social row
10. Footer — single-row minimal footer

---

## Technical constraints

- Vanilla HTML + CSS + JS only. No React, no build tools.
- All code lives in single HTML files (no separate .css or .js files).
- Cart persists via localStorage (key: `tkt_cart`).
- Custom cursor (white dot + lagging ring) on every page.
- Scroll reveal via IntersectionObserver (class `.reveal` → `.visible`).

---

## Files in this repo

| File                        | Purpose                                                  |
|-----------------------------|----------------------------------------------------------|
| `index.html`                | Main page — current monochrome version, production-ready |
| `booking.html`              | Booking page with drag-and-drop file upload              |
| `cart.html`                 | Merch cart and checkout                                  |
| `takataka-website.html`     | ⚠️ REFERENCE ONLY — original prototype, do not edit      |
| `DESIGN_SYSTEM.md`          | Full design system documentation                         |
| `design-system/tokens.css`  | All CSS variables / design tokens                        |
| `design-system/components.html` | All component patterns with CSS                     |
| `CLAUDE.md`                 | AI agent workflow instructions                           |

---

*TakaTaka Records — April 2026*
