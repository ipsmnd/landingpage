# landingpage
# MND CODE: 12 Landing Page Animations, 12 Prompts

A single-page website for **MND CODE**. It holds a copy-paste guide of 12 Claude prompts for landing page animations, a services overview, ready-made color palettes, and a downloadable Business Requirements Document (BRD).

**Live page:** https://landingpage-ten-nu-31.vercel.app/

---

## Features

| Section | What it does |
| --- | --- |
| **Intro splash** | Animated logo, wordmark and loading bar for about 3 seconds. Clicking the header logo replays it. |
| **Services** | 5 category cards with filter tabs (All, Web, Mobile App, Marketing, Graphic, Animation). |
| **BRD download** | One button that saves the Business Requirements Document (PDF, 5 pages). |
| **How to use** | Explains the base line. Four brand fields (Primary, Accent, Background, Font) fill it in live. |
| **12 prompts** | One card per prompt. The COPY button copies the prompt plus the filled-in base line. |
| **Color palettes** | 6 palettes. Click a swatch to copy its hex, or use COPY ALL, COPY CSS, or PROMPTS MEIN LAGAO. |
| **Rules** | Short performance and testing tips. |
| **CTA and footer** | Follow link, share button, © MND CODE. |

### Services included

- **Web Design & Development:** Dynamic, Static, E-Commerce, React JS, Angular JS, WordPress, Shopify, PHP, UI & UX Design
- **Mobile App Development:** Android, iOS, Windows
- **Digital Marketing:** SEO, Brand Promotion, Google Keyword Optimization
- **Graphic Design:** Flyer, Brochure, Branding, E-Cards, Marriage Cards
- **Animation & VFX:** 2D/3D Animation, Cartoon Movie Maker, Motion Graphics, Video Advertisements

### Palettes included

Midnight Navy, Dusty Rose, Emerald Depth, Obsidian Plum, Smoked Copper, Blue Hour (6 colors each).

---

## Tech stack

- One self-contained `index.html` file
- Inline CSS and vanilla JavaScript, no libraries and no build step
- Logo cropped from `splash.png` and embedded as a base64 PNG
- BRD PDF embedded as base64 inside the script
- Light and dark theme through CSS variables (`prefers-color-scheme`)
- Animations use `transform` and `opacity`, with `prefers-reduced-motion` support

---

## Project structure

```
index.html   # the whole website (HTML + CSS + JS + embedded assets)
README.md    # this file
```

Inside `index.html`:

```
<style>      design tokens, layout, splash, cards, palettes, services
<body>
  #splash    intro animation
  .brand     header with logo and quick links
  #services  service cards and filter tabs
  #brd       BRD download card
  #how       base line and brand fields
  #prompts   12 prompt cards
  #palettes  color palette cards
  #rules     rules list
  .cta       follow / share card
  footer     © MND CODE
<script>     data arrays (P, PAL, SV, BRD), copy helper, event handlers
```

---

## Customizing

All content is plain data near the bottom of `index.html`.

| To change | Edit this |
| --- | --- |
| Prompts | The `P` array, as `["Title", "Prompt text"]` |
| Palettes | The `PAL` array, as `["Name", "Tagline", [6 hex codes]]` |
| Services | The `SV` array, as `["Category", "Tagline", "emoji", [services]]` |
| Brand accent colors | `--c1` and `--c2` in the CSS (the logo's cyan and violet) |
| Splash length | `animation: splashOut ... 2.6s` and the `setTimeout(hideSplash, 3600)` fallback |
| Follow link | The `@mnd.coding` link inside `.cta` |

---

## How the copy and download buttons work

- **Copy** uses `navigator.clipboard` and falls back to a hidden textarea with `document.execCommand("copy")`.
- **PROMPTS MEIN LAGAO** sets the Background, Accent and Primary fields from a palette (color 1, 4 and 5), then scrolls to the base line.
- **BRD download** uses the Claude artifact `downloads` capability. The viewer sees a confirmation dialog and must accept. If the capability is unavailable, the button shows a message instead of failing silently.

If you host the page outside claude.ai, replace the BRD button handler with a normal link, for example:

```html
<a href="Business_Requirements_Document_Customer_Form.pdf" download>Download BRD</a>
```

---

## Accessibility

- Semantic sections, labelled buttons and `aria-live` toasts
- Keyboard-focusable swatches, tabs and copy buttons
- Reduced-motion users get a shortened splash and no hover or reveal motion

---

## Things to verify

Some source text was garbled, so these values were inferred. Please check them:

- Palette codes: `#E8D2C4`, `#17151B`, `#292531`, `#AAA2B3`, `#604330`, `#C19A94`, `#98A9C9`
- Service names: "Google Keyword Optimization" and "2D/3D Animation"
- Graphic Design and Animation & VFX groupings

---

## Credits and license

© MND CODE. All rights reserved.

The prompt guide content is adapted from the supplied "12 landing page animations, 12 prompts" PDF.
