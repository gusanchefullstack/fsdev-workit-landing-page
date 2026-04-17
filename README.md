# Workit Landing Page

A responsive marketing landing page for a fictional product-data analytics service, built from a Figma design as a [Frontend Mentor challenge](https://www.frontendmentor.io/challenges/workit-landing-page-2fYnyle5lu). The goal is a pixel-accurate, mobile-first implementation using only vanilla HTML, CSS, and Vite — no frameworks.

![License](https://img.shields.io/badge/license-MIT-blue)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-5.x-646CFF?logo=vite&logoColor=white)

## Table of Contents

- [Motivation](#motivation)
- [Screenshots](#screenshots)
- [Built With](#built-with)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Project Structure](#project-structure)
- [What I Learned](#what-i-learned)
- [Tests](#tests)
- [Roadmap](#roadmap)
- [Credits](#credits)
- [License](#license)
- [Author](#author)

## Motivation

Frontend Mentor challenges provide a real design file and asset pack — the same inputs a production frontend developer would receive from a design team. This project was built to practice translating a Figma source of truth into a hand-written, framework-free page: every layout, gradient, and typographic scale is expressed in plain CSS with design tokens, so the result stays easy to re-theme and audit.

## Screenshots

**Mobile — 375px**

![Mobile screenshot](./screenshots/mobile-375.png)

**Desktop — 1440px**

![Desktop screenshot](./screenshots/desktop-1440.png)

## Built With

- Semantic HTML5 (`header`, `nav`, `main`, `section`, `article`, `aside`, `footer`)
- CSS custom properties for colors, gradients, typography, and spacing
- Flexbox + CSS Grid for layout
- Mobile-first responsive workflow with tablet and desktop breakpoints
- Self-hosted variable fonts: **Fraunces** (display) and **Manrope** (body)
- [Vite](https://vitejs.dev/) as the dev server and production bundler
- Zero runtime dependencies — no UI libraries, no CSS frameworks

## Installation

Prerequisites:

- Node.js `>= 18`
- npm `>= 9`

Clone and install:

```bash
git clone https://github.com/gusanchefullstack/fsdev-Workit-landing-page.git
cd fsdev-Workit-landing-page
npm install
```

## Quick Start

```bash
npm run dev        # start dev server on http://localhost:5173
npm run build      # bundle production assets to /dist
npm run preview    # serve the built output locally
```

Open `http://localhost:5173` in the browser to view the page. Edits to files under `src/` hot-reload automatically.

## Project Structure

```
.
├── src/
│   ├── index.html
│   ├── data.json            # copy for the three feature cards
│   ├── js/                  # small progressive-enhancement scripts
│   └── styles/
│       ├── main.css         # entry that imports the partials below
│       ├── _variables.css   # design tokens (colors, gradients, type, spacing)
│       ├── _fonts.css       # @font-face declarations
│       ├── _reset.css       # baseline reset
│       ├── _components.css  # buttons, cards, numbered badges
│       └── _layout.css      # hero, features, founder, footer layouts
├── assets/
│   ├── images/              # SVG illustrations and raster exports
│   └── fonts/               # Fraunces + Manrope variable font files
├── screenshots/             # 375px and 1440px reference captures
├── figma-design/            # local Figma source (git-ignored)
└── vite.config.js
```

## What I Learned

A learning log of the concepts and decisions that shaped this build. Kept here so a future me — or anyone reviewing the repo — can recover the reasoning without re-reading every commit.

### Design tokens as the single source of truth

All colors, gradients, font sizes, line heights, and spacing steps live in `src/styles/_variables.css` as CSS custom properties. Re-theming then becomes a one-file change. Example:

```css
:root {
  --color-dark-purple: hsl(273 85% 13%);
  --color-eucalyptus:  hsl(150 100% 63%);
  --gradient-hero:     radial-gradient(at top, var(--color-dark-purple), #000);

  --font-display: "Fraunces", serif;
  --font-body:    "Manrope", sans-serif;
}
```

### Semantic landmarks over `div` soup

Following guideline #13, the page uses exactly one `<main>` and wraps secondary regions in `<section>`, `<aside>`, `<nav>`, and `<footer>`. This removed the need for most ARIA roles — assistive tech can navigate the page from the native outline alone.

### Mobile-first with a layered curve

The dark hero on mobile crops into a single concave curve; on desktop the same shape must flow around a floating phone mockup. Implementing the curve as an SVG mask (rather than a bottom border-radius) kept the geometry resolution-independent and simplified the breakpoint changes to a handful of grid values.

### Local variable fonts

Using self-hosted Fraunces and Manrope instead of Google Fonts avoids a render-blocking request and gives full control over `font-display: swap` behaviour. The license files ship next to the font binaries under `assets/fonts/`.

### Errors solved along the way

- **Curved hero clipping the nav on small widths** — fixed by moving the SVG mask out of the `header` and applying it to a `::after` pseudo-element on the hero `section`.
- **Fraunces italic axis not animating** — resolved by declaring a single `@font-face` with a `font-variation-settings: "ital" 0..1` range rather than two separate `normal`/`italic` faces.
- **Tablet layout regression between 600–900px** — the feature cards overflowed because the grid used `auto-fit` without a `minmax` floor; switched to `repeat(auto-fit, minmax(min(100%, 20rem), 1fr))`.

### Key references

- [Frontend Mentor — Workit challenge brief](https://www.frontendmentor.io/challenges/workit-landing-page-2fYnyle5lu)
- [MDN — Using CSS custom properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties)
- [MDN — CSS Grid `minmax()`](https://developer.mozilla.org/en-US/docs/Web/CSS/minmax)
- [web.dev — Responsive design patterns](https://web.dev/patterns/layout/)
- [Vite guide](https://vitejs.dev/guide/)

## Tests

Visual regression is verified manually with Playwright screenshots at the two reference viewports defined by the challenge:

```bash
# 375px and 1440px captures — output goes to /screenshots
npx playwright test
```

No unit-test framework is configured; the project is a single static page.

## Roadmap

- [x] Semantic HTML skeleton with one `<main>` landmark
- [x] Design tokens for colors, gradients, typography, spacing
- [x] Mobile-first layout for 375px and 1440px
- [x] Tablet breakpoint inferred from the Figma source
- [x] Playwright screenshots at 375px and 1440px
- [ ] Automated Lighthouse CI on pull requests
- [ ] Visual regression diffing (pixelmatch) against baseline PNGs
- [ ] Deploy preview on Vercel

## Credits

- Design by [Frontend Mentor](https://www.frontendmentor.io/) — challenge assets and Figma file
- Typefaces: [Fraunces](https://fonts.google.com/specimen/Fraunces) by Undercase Type, [Manrope](https://fonts.google.com/specimen/Manrope) by Mikhail Sharanda
- Build tooling: [Vite](https://vitejs.dev/)

## License

Distributed under the MIT License. See [LICENSE](./LICENSE) for details. The Figma design file and challenge assets remain the property of Frontend Mentor.

## Author

**Gustavo Sánchez Galarza**

[![LinkedIn](https://img.shields.io/badge/-LINKEDIN-2F6FEB?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/gustavosanchezgalarza/)
[![GitHub](https://img.shields.io/badge/-GITHUB-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/gusanchefullstack)
[![Hashnode](https://img.shields.io/badge/-HASHNODE-3B5BFE?style=for-the-badge&logo=hashnode&logoColor=white)](https://hashnode.com/@gusanchedev)
[![X](https://img.shields.io/badge/-X-000000?style=for-the-badge&logo=x&logoColor=white)](https://x.com/gusanchedev)
[![Bluesky](https://img.shields.io/badge/-BLUESKY-4A99E9?style=for-the-badge&logo=bluesky&logoColor=white)](https://bsky.app/profile/gusanchedev.bsky.social)
[![freeCodeCamp](https://img.shields.io/badge/-FREECODECAMP-0A0A23?style=for-the-badge&logo=freecodecamp&logoColor=white)](https://www.freecodecamp.org/gusanchedev)
[![Frontend Mentor](https://img.shields.io/badge/-FRONTEND%20MENTOR-3F54A3?style=for-the-badge&logo=frontendmentor&logoColor=white)](https://www.frontendmentor.io/profile/gusanchefullstack)
