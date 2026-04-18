# TAKATAKA — Design System & Code Guide

> **Single source of truth for design and development.**
> This file is read by AI agents (Claude Code / Claude.ai) before creating or editing any component or page.
> Prototype reference: `takataka-website.html` (original) and `index.html` (current monochrome version).

---

## 1. Brand Identity

**Name:** TakaTaka Records  
**Tagline:** Underground Movement  
**Positioning:** Independent music label and collective, Saint Petersburg. Underground electronic music — microhouse, minimal wave, minimal house. Vinyl + digital releases.  
**Language:** EN (primary), RU (merch/cart UI)  
**Currency:** ₽ (merch), € (international releases)

**Brand Tone:** Understated, editorial, anti-commercial. Silence as a design element. No decorative noise — every visual element must earn its place. Think: underground club flyer meets gallery catalogue.

**Aesthetic references:** Brutalist editorial, early Factory Records, underground techno labels (Ostgut Ton, Perlon), minimal Japanese design.

---

## 2. Color Palette

### Primary Colors

⚠️ **RULE:** This is a strict monochrome system. No accent colors. No gradients with color. No Tailwind default colors.

| Token       | HEX / Value              | CSS Variable      | Usage                                    |
|-------------|--------------------------|-------------------|------------------------------------------|
| `black`     | `#080808`                | `--black`         | Page background, primary surface        |
| `white`     | `#f0ede6`                | `--white`         | Primary text, filled elements           |
| `gray`      | `#141414`                | `--gray`          | Section backgrounds (alternating)       |
| `gray2`     | `#1c1c1c`                | `--gray2`         | Cards, contact items, merch cards       |
| `mid`       | `#2e2e2e`                | `--mid`           | Borders, dividers, subtle separators    |
| `dim`       | `#555555`                | `--dim`           | Secondary text, labels, placeholders    |

### CSS Variables (in `<style>` or `index.css`)

```css
:root {
  --black:  #080808;
  --white:  #f0ede6;
  --gray:   #141414;
  --gray2:  #1c1c1c;
  --mid:    #2e2e2e;
  --dim:    #555555;
}
```

### Opacity Variants

| Pattern                             | Usage                                        |
|-------------------------------------|----------------------------------------------|
| `rgba(240,237,230, 0.06)`           | Grid lines, very subtle backgrounds          |
| `rgba(240,237,230, 0.10–0.15)`      | Borders on dark cards                        |
| `rgba(240,237,230, 0.22–0.28)`      | Outline text stroke (hero l2), rings         |
| `rgba(240,237,230, 0.38)`           | Muted white text (hero secondary line)       |
| `rgba(255,255,255, 0.05)`           | Ticker borders, section borders              |

### Forbidden ❌

- Any hue-based color: blues, purples, greens, reds
- `#c8ff00` acid green (was the old accent — removed entirely)
- Pure `#000000` black (too harsh — use `#080808`)
- Any Tailwind color utility: `blue-500`, `indigo-600`, `red-400`
- Gradients with color (only dark-to-darker or transparent fades allowed)

---

## 3. Typography

### Font Stack

| Role         | Family          | Weights           | CSS Variable      | Usage                          |
|--------------|-----------------|-------------------|-------------------|-------------------------------|
| Display      | `Gilroy`    | 400               | `--display`       | Hero titles, section headings, nav logo |
| Mono / Body  | `Space Mono`    | 400, 700 / italic | `--mono`          | Body text, labels, buttons, forms |

### Google Fonts Import

```html
<link href="Local woff2 — see fonts/Gilroy/" rel="stylesheet">
```

### Heading Hierarchy

| Level         | Size                             | Family      | Weight | Tracking       | Usage                          |
|---------------|----------------------------------|-------------|--------|----------------|-------------------------------|
| Hero Mega     | `clamp(72px, 10vw, 160px)`       | Gilroy  | 400    | `-0.01em`      | TAKA / TAKA hero lockup        |
| Section Title | `clamp(26px, 3.5vw, 48px)`       | Gilroy  | 400    | `-0.025em`     | CONNECT, RELEASES, SHOP        |
| Card Title    | `11–13px`                        | Gilroy  | 700    | `0.02em`       | Merch card names               |
| Player Title  | `20px`                           | Gilroy  | 700    | `-0.01em`      | Podcast player                 |
| Contact Title | `clamp(52px, 8vw, 120px)`        | Gilroy  | 900    | `-0.02em`      | CONNECT section heading        |

### Body / UI Text

| Context         | Size     | Family     | Tracking   | Usage                               |
|-----------------|----------|------------|------------|-------------------------------------|
| Body paragraph  | `11px`   | Space Mono | `0.04em`   | Release descriptions, about text    |
| Label / eyebrow | `8–10px` | Space Mono | `0.3–0.4em`| Section labels, badges, nav links   |
| Button text     | `9–10px` | Space Mono | `0.18–0.22em` | All buttons, CTAs               |
| Price           | `10px`   | Space Mono | `0.1em`    | Merch pricing                       |
| Form input      | `10px`   | Space Mono | `0.04em`   | All form fields                     |
| Track list      | `10px`   | Space Mono | `0.04em`   | Release tracklist rows              |
| Footer          | `8px`    | Space Mono | `0.18em`   | Footer text, copyright              |

### Typography Rules ✅

1. **Display font (Gilroy)** — headings, section titles, logo text, nav brand name only
2. **Mono font (Space Mono)** — everything else: body, labels, buttons, forms, nav links
3. **UPPERCASE** — Space Mono labels (and UI text): `text-transform: uppercase`
4. **Hero title treatment:** First line `TAKA` — solid white fill. Second line `TAKA` — outline only (`-webkit-text-stroke: 1px`, `color: transparent`)
5. **Line height for hero:** `0.88` — tightly stacked
6. **Use** Gilroy Heavy (900) or ExtraBold (800) for large display headings — these weights have the most impact
7. **Letter spacing for labels:** `0.3em` – `0.4em` — always very wide
8. **No serif fonts anywhere** — this is a mono + display system only

---

## 4. Spacing System & Layout

### Page Container

No `max-width` wrapper. Content spans edge-to-edge with padding only.

| Context              | Value                         |
|----------------------|-------------------------------|
| Horizontal padding   | `48px` desktop / `20px` mobile|
| Section vertical     | `112px` desktop / `72px` mobile|
| Nav height           | `72px` desktop / `60px` mobile |
| Grid gap (releases)  | `2px` (tight grid — like tiles)|
| Card gap (merch)     | `24px`                         |
| Section gap          | `80px` desktop / `40px` mobile |

### Grid System

| Context           | Grid                                  |
|-------------------|---------------------------------------|
| Hero              | `1fr 1fr` (left content / right art)  |
| Releases          | `repeat(4, 1fr)` → `2fr` mobile       |
| News              | `2fr 1fr 1fr` → `1fr 1fr` → `1fr`    |
| Merch             | `repeat(3, 1fr)` → `2fr` → `1fr`     |
| Contact           | `repeat(4, 1fr)` → `2fr` → `1fr`     |
| Footer (old)      | `2fr 1fr 1fr 1fr`                     |
| Footer (current)  | Single row, `space-between`           |
| Latest Release    | `1fr 1fr` → `1fr` mobile             |
| Podcast           | `1fr 2fr` → `1fr` mobile             |

### Aspect Ratios

| Context         | Ratio              |
|-----------------|--------------------|
| Hero            | `100svh`           |
| Release artwork | `1:1` (square)     |
| Artist card     | `3:4`              |
| News card image | `16:9`             |
| Merch card img  | `3:4`              |
| Vinyl artwork   | `1:1`              |

---

## 5. Animation & Motion

⚠️ **RULE:** Animate only `transform` and `opacity`. Never `transition-all` on large blocks.

### Reveal System (Scroll)

```js
// IntersectionObserver pattern used across all pages
const obs = new IntersectionObserver(entries =>
  entries.forEach(e => {
    if (e.isIntersecting) e.target.classList.add('visible');
  }),
  { threshold: 0.08, rootMargin: '0px 0px -30px 0px' }
);
document.querySelectorAll('.reveal').forEach(el => obs.observe(el));
```

```css
.reveal {
  opacity: 0;
  transform: translateY(22px);
  transition: opacity 0.65s ease, transform 0.65s ease;
}
.reveal.visible {
  opacity: 1;
  transform: translateY(0);
}
```

**Stagger pattern (apply via inline style):**
```html
<div class="reveal" style="transition-delay: 0.1s">...</div>
<div class="reveal" style="transition-delay: 0.2s">...</div>
```

### Hero Entrance

```css
/* Hero title and eyebrow fade up on load */
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(16px); }
  to   { opacity: 1; transform: translateY(0); }
}
.hero-eyebrow { animation: fadeUp 0.8s 0.2s forwards; opacity: 0; }
.hero-title   { animation: fadeUp 0.8s 0.35s forwards; opacity: 0; }
.hero-actions { animation: fadeUp 0.8s 0.55s forwards; opacity: 0; }
```

### Ticker

```css
@keyframes tick {
  from { transform: translateX(0); }
  to   { transform: translateX(-50%); }
}
.ticker-track { animation: tick 22s linear infinite; }
```

### Vinyl Rotation

```css
@keyframes spin {
  from { transform: rotate(0deg); }
  to   { transform: rotate(360deg); }
}
.vinyl { animation: spin 8s linear infinite; }
```

### Scroll Indicator Bob

```css
@keyframes bob {
  0%, 100% { transform: translateY(0); }
  50%       { transform: translateY(8px); }
}
.hero-scroll { animation: bob 2.2s ease-in-out infinite; }
```

### CSS Hover Transitions

| Element              | Transition                              |
|----------------------|-----------------------------------------|
| Nav links            | `color 0.2s`, underline `width 0.25s`  |
| Cards (all)          | `border-color 0.2s`                    |
| Release card artwork | `transform 0.4s` (scale 1.05 on hover) |
| Buttons              | `background 0.25s, color 0.25s`        |
| Social/stream links  | `color 0.2s, border-color 0.2s`        |
| Merch add button     | `background 0.2s, color 0.2s`          |

### Custom Cursor

```css
.cursor {
  position: fixed; width: 8px; height: 8px;
  background: var(--white); border-radius: 50%;
  pointer-events: none; z-index: 9999;
  transform: translate(-50%, -50%);
  transition: transform 0.12s;
}
.cursor-ring {
  position: fixed; width: 34px; height: 34px;
  border: 1px solid rgba(240,237,230, 0.22); border-radius: 50%;
  pointer-events: none; z-index: 9998;
  transform: translate(-50%, -50%);
  transition: left 0.1s ease, top 0.1s ease;
}
```

```js
// Cursor JS
const cursor = document.getElementById('cursor');
const ring   = document.getElementById('cursor-ring');
let mx = 0, my = 0;
document.addEventListener('mousemove', e => {
  mx = e.clientX; my = e.clientY;
  cursor.style.left = mx + 'px';
  cursor.style.top  = my + 'px';
});
setInterval(() => {
  ring.style.left = mx + 'px';
  ring.style.top  = my + 'px';
}, 80);
```

---

## 6. Hero Section

### Title Treatment

The hero title is the most important visual element. The `TAKA / TAKA` lockup follows this rule strictly:

```css
/* Line 1 — solid white fill */
.hero-title .l1 {
  display: block;
  color: var(--white);          /* filled */
}

/* Line 2 — outline only, no fill */
.hero-title .l2 {
  display: block;
  color: transparent;
  -webkit-text-stroke: 1px rgba(240,237,230, 0.28);  /* thin outline, low opacity */
}
```

**Font:** Gilroy, `clamp(72px, 10vw, 160px)`, `line-height: 0.88`

### Perspective Grid Background

```html
<div class="hero-grid">
  <svg ...>
    <!-- Radial lines converging to vanishing point (720, 460) -->
    <!-- Ellipses creating horizontal depth lines -->
    <!-- Gradient overlays: top/bottom fade, left darkening -->
  </svg>
</div>
```

Grid lines: `rgba(240,237,230, 0.06)` — barely visible, purely atmospheric.

### Eyebrow Label

```css
.hero-eyebrow {
  font-size: 10px; letter-spacing: 0.35em;
  text-transform: uppercase; color: var(--dim);
  display: flex; align-items: center; gap: 12px;
}
.hero-eyebrow::before {
  content: ''; display: block;
  width: 36px; height: 1px; background: var(--dim);
}
```

---

## 7. Component Patterns

### Buttons

**Primary (filled white / inverts on hover):**
```css
.btn-primary {
  background: var(--white); color: var(--black);
  border: 1px solid var(--white);
  padding: 14px 32px;
  font-size: 10px; letter-spacing: 0.22em; text-transform: uppercase;
  transition: background 0.25s, color 0.25s;
}
.btn-primary:hover {
  background: transparent; color: var(--white);
}
```

**Ghost (outline only):**
```css
.btn-ghost {
  background: transparent; color: var(--white);
  border: 1px solid rgba(240,237,230, 0.2);
  padding: 14px 32px;
  font-size: 10px; letter-spacing: 0.22em; text-transform: uppercase;
  transition: border-color 0.25s;
}
.btn-ghost:hover { border-color: rgba(240,237,230, 0.6); }
```

**Stream / small link button:**
```css
.s-btn {
  font-size: 8px; letter-spacing: 0.2em; text-transform: uppercase;
  padding: 8px 14px; border: 1px solid rgba(255,255,255, 0.1);
  color: var(--dim); transition: all 0.18s;
}
.s-btn:hover { border-color: var(--white); color: var(--white); }
```

### Section Label

```css
.section-label {
  font-size: 10px; letter-spacing: 0.4em; text-transform: uppercase;
  color: var(--dim); margin-bottom: 56px;
  display: flex; align-items: center; gap: 14px;
}
.section-label::after {
  content: ''; flex: 1; max-width: 72px;
  height: 1px; background: var(--mid);
}
```

### Release / Merch Cards

```css
.rel-card, .merch-card, .news-card {
  border: 1px solid transparent;
  transition: border-color 0.2s;
}
.rel-card:hover, .merch-card:hover, .news-card:hover {
  border-color: rgba(240,237,230, 0.1);
}
```

**Badges (outline only, no fill):**
```css
.badge {
  font-size: 7px; letter-spacing: 0.22em; text-transform: uppercase;
  padding: 5px 11px;
  border: 1px solid rgba(240,237,230, 0.3);
  color: var(--white); background: transparent;
}
```

### Contact Grid Item

```css
.c-item {
  padding: 32px 24px; background: var(--gray2);
  border: 1px solid transparent; transition: border-color 0.2s;
}
.c-item:hover { border-color: rgba(240,237,230, 0.1); }
.c-type {
  font-size: 8px; letter-spacing: 0.3em; text-transform: uppercase;
  color: var(--dim); margin-bottom: 14px;
}
.c-val { font-size: 11px; color: var(--white); }
```

### Social Row

```css
.soc-item {
  flex: 1; padding: 20px 16px; background: var(--gray2);
  font-size: 8px; letter-spacing: 0.25em; text-transform: uppercase;
  text-align: center; color: var(--dim);
  border: 1px solid transparent; transition: all 0.2s;
}
.soc-item:hover { color: var(--white); border-color: rgba(240,237,230, 0.1); }
```

### Ticker

```css
.ticker {
  background: var(--gray);
  border-top: 1px solid rgba(255,255,255, 0.05);
  border-bottom: 1px solid rgba(255,255,255, 0.05);
  padding: 11px 0;
}
.ticker-item {
  font-family: var(--display); font-size: 10px; font-weight: 700;
  letter-spacing: 0.18em; text-transform: uppercase;
  color: rgba(255,255,255, 0.12); padding-right: 64px;
}
```

### Form Inputs

```css
.f-input {
  width: 100%; background: var(--gray);
  border: 1px solid transparent; color: var(--white);
  font-family: var(--mono); font-size: 10px; letter-spacing: 0.04em;
  padding: 15px 18px; outline: none; transition: border-color 0.2s;
}
.f-input::placeholder { color: var(--dim); }
.f-input:focus { border-color: var(--white); }
```

### Cart Counter

```css
.nav-cart-count {
  background: var(--white); color: var(--black);
  width: 16px; height: 16px; border-radius: 50%;
  font-size: 8px; font-weight: 700;
}
```

### Divider

```css
.divider {
  height: 1px;
  background: linear-gradient(to right, transparent, rgba(240,237,230,0.1), transparent);
  margin: 0 48px;
}
```

---

## 8. Navigation

```css
nav (or .site-nav) {
  position: fixed; top: 0; left: 0; right: 0; z-index: 100;
  height: 72px; padding: 0 48px;
  display: flex; justify-content: space-between; align-items: center;
  background: linear-gradient(to bottom, rgba(8,8,8,0.97) 0%, transparent 100%);
}
```

**Logo:** Outline SVG (white stroke, no fill), opacity `0.85`, `36px` wide  
**Nav links:** Space Mono, `9px`, `letter-spacing: 0.22em`, uppercase, `color: var(--dim)`  
**Nav link hover:** underline expands from 0 to 100%, `background: var(--white)`  
**Mobile:** Burger menu → full-screen drawer overlay

---

## 9. TakaTaka Logo

The logo is an abstract SVG path. It is used in three treatments:

| Treatment     | CSS                                       | Opacity | Usage                  |
|---------------|-------------------------------------------|---------|------------------------|
| Outline       | `fill: none; stroke: var(--white); stroke-width: 1.5` | 0.85  | Nav, footer            |
| Solid dim     | `fill: white`                             | 0.13    | Release artwork watermark |
| Solid mid     | `fill: white`                             | 0.5     | Footer simple mark     |

**SVG path** (short version for solid):
```svg
<path d="M128.507 350.375C192.024 289.144...M126.298 644.957C328.423 578.22..." fill="white"/>
```
Full path is in all HTML files. Always reference `#logo` symbol if defined in-page, or copy the path directly.

---

## 10. Page Structure

```
index.html        → Main page (hero, ticker, releases, news, radio, merch, contact/connect, footer)
booking.html      → Booking: roster, EPK, request form with file upload
cart.html         → Merch cart + checkout
takataka-website.html → REFERENCE ONLY — original prototype (not linked in production)
```

### Section Order (index.html)

1. `<nav>` — fixed navigation
2. `#home` — Hero (TAKA / TAKA, grid background, vinyl artwork)
3. `.ticker` — scrolling text strip
4. `.release-feat` — Latest Release (artwork + tracklist + stream links)
5. `#releases` — Releases grid (4-col, filter tabs)
6. `#news` — News grid (3-col)
7. `#radio` — Podcast (episodes list + player)
8. `#merch` — Merch store (3-col)
9. `#contact` — Connect section (4-col grid + social row)
10. `footer` — Simple single-row footer

---

## 11. Interactive Features (Current)

| Feature             | Location          | Notes                                      |
|---------------------|-------------------|--------------------------------------------|
| Cart system         | index + cart.html | localStorage, add/remove/qty              |
| Auth modal          | all pages         | Login / Register tabs, overlay             |
| Burger / drawer nav | all pages         | Mobile only, full-screen overlay           |
| Scroll reveal       | all pages         | IntersectionObserver, `.reveal` → `.visible` |
| Custom cursor       | all pages         | Dot + lagging ring, white                  |
| File upload         | booking.html      | Drag-and-drop zone + progress bars         |
| Release filter      | index.html        | Filter tabs (All / Album / EP / Single)    |

---

## 12. Development Rules (For AI Agents)

1. **Monochrome only** — No color additions without explicit approval. If in doubt: white, gray, or transparent.

2. **Don't break typography** — Gilroy for headings, Space Mono for everything else. No exceptions.

3. **Preserve grid tightness** — The `2px` gap in release/news grids is intentional. Don't change to larger gaps.

4. **Preserve hero title treatment** — L1 filled, L2 outline. Never both filled, never both outline.

5. **Hover states: border-based** — Cards reveal white border on hover, not background color change.

6. **Mobile-first** — Default styles for mobile, desktop via `@media(min-width: ...)`.

7. **No new JS dependencies** — Vanilla JS only for this project (no React, no Vue). All interactivity is pure DOM.

8. **Custom cursor everywhere** — Every page has `.cursor` + `.cursor-ring` + JS. Never remove.

9. **Cart state via localStorage** — Key: `tkt_cart`. All pages share the same cart.

10. **When adding sections** — Follow pattern: `section.section-wrap` → `.section-label` → `.section-h` → content → `.divider`.

---

## 13. Do's & Don'ts

### ✅ DO

- Use `var(--white)` with low opacity for subtle effects: `rgba(240,237,230, 0.06)`
- Animate only `transform` and `opacity`
- Keep sections alternating between `--black` and `--gray` backgrounds
- Use `border: 1px solid transparent` + hover `border-color` for card hover states
- Maintain `0.28–0.38` opacity for the outline text stroke on hero L2
- Keep Gilroy for anything headline-sized
- Keep Space Mono for labels even at very small sizes (7–8px)

### ❌ DON'T

- Add any hue-based color — not even a subtle tint
- Change the hero title treatment (L1 filled / L2 outline)
- Use `font-weight: bold` with Gilroy (already visually heavy)
- Use `transition-all` on section-level or card-level blocks
- Add box shadows (not used in this design system)
- Use `border-radius` except for cursor (50%) and cart counter (50%)
- Make the grid gaps larger than `24px` for tight tile layouts
- Add background-color to hover states on cards (border only)

---

## 14. Tech Stack

| Technology    | Purpose                                |
|---------------|----------------------------------------|
| Vanilla HTML  | All pages — single-file architecture   |
| CSS Variables | Design tokens (`--black`, `--white` etc.) |
| Space Mono    | Body / UI typeface (Google Fonts)      |
| Gilroy    | Display typeface (local woff2, fonts/)   |
| Vanilla JS    | Cursor, cart, modals, reveal, filters  |
| localStorage  | Cart persistence across pages          |
| IntersectionObserver | Scroll reveal system          |

---

*Last updated: April 2026 — reflects current monochrome version with perspective grid hero and TAKA/TAKA filled+outline title treatment.*
