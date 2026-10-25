# ROBOKO — Clash of the Steel Samurai

Official event landing page for **ROBOKO III**, the autonomous sumo robotics tournament organized by the **IEEE Student Branch at École Nationale Polytechnique (ENP), El Harrach, Algiers**.

The site is a single-page, statically generated marketing and information hub for competitors and spectators — covering divisions, arena specifications, the tournament rulebook, schedule, registration steps, organizer details, and scrutineering FAQs.

> Steel on steel. Zero retreat. The arena awaits.

---

## Built With

| Layer | Technology |
| --- | --- |
| Framework | [Astro](https://astro.build/) 5 (static output) |
| Styling | [Tailwind CSS](https://tailwindcss.com/) 3 + PostCSS / Autoprefixer |
| Scripting | TypeScript (strict), vanilla inline scripts |
| Fonts | Space Grotesk, JetBrains Mono, Material Symbols (Google Fonts) |
| Build Tool | Vite (via Astro) |

No UI framework, no client-side router, no runtime backend. The final build is plain HTML, CSS, and a small amount of JavaScript.

---

## Features

- **Single-page landing experience** composed of modular Astro components.
- **Neo-brutalist visual identity** — hard offset shadows, hazard stripes, blueprint grids, and a washi-paper / sumi-ink / vermilion palette.
- **Animated samurai hero** — CSS rising sun, torii gate, and falling sakura petals, all pure CSS (no canvas or libraries).
- **Live telemetry marquee** — infinite scrolling ticker that pauses on hover/focus.
- **Shrinking floating header** — full-width bar at the top that collapses into a centered pill on scroll.
- **Fully responsive** layouts for mobile, tablet, and desktop.
- **Accessibility-minded** — focus-visible outlines, ARIA labels on decorative diagrams, semantic sections, and full `prefers-reduced-motion` support that disables all animations.
- **Zero external JS dependencies** at runtime.

---

## Getting Started

### Prerequisites

- **Node.js 18.17+** (or 20+)
- npm (included with Node)

### Installation

```bash
git clone https://github.com/Mohhmdoui2005/robov2.git
cd robov2
npm install
```

### Development

```bash
npm run dev
```

The dev server starts at `http://localhost:4321` with hot module reloading.

### Production Build

```bash
npm run build
```

Static output is emitted to `dist/`.

### Preview the Build

```bash
npm run preview
```

---

## Project Structure

```
roboko v2/
├── public/
│   └── favicon.svg            # Site icon
├── src/
│   ├── components/
│   │   ├── Ticker.astro        # Telemetry marquee banner
│   │   ├── Header.astro        # Sticky nav with shrink-on-scroll behavior
│   │   ├── Hero.astro          # Headline, CTAs, animated samurai panel
│   │   ├── Classification.astro# Uniform division & spec book callout
│   │   ├── Dohyo.astro         # Arena (dohyo) specs + top-view diagram
│   │   ├── Bushido.astro       # Tournament ethics & regulations
│   │   ├── Schedule.astro      # Four-stage championship timeline
│   │   ├── Register.astro      # Free entry & three-step registration
│   │   ├── Branch.astro        # Organizer / IEEE branch facts
│   │   ├── Faq.astro           # Scrutineering protocols
│   │   └── Footer.astro        # Links, credits, hazard strip
│   ├── layouts/
│   │   └── Layout.astro        # HTML shell, meta tags, fonts
│   ├── pages/
│   │   └── index.astro         # Page composition
│   └── styles/
│       └── global.css          # Tailwind layers, design tokens, animations
├── astro.config.mjs            # Astro config (static output + Tailwind)
├── tailwind.config.mjs         # Design tokens, typography, spacing scale
├── postcss.config.mjs          # PostCSS pipeline
└── package.json
```

---

## Design System

All design tokens live in `tailwind.config.mjs` and are consumed as standard Tailwind utilities. The palette intentionally uses Material-style token names (e.g. `primary`, `surface-container`, `on-surface`) remapped to a custom light washi/ink/vermilion theme.

### Colors

| Token | Value | Role |
| --- | --- | --- |
| `surface` / `background` | `#f3eee1` | Washi paper base |
| `primary-container` / `primary` | `#a53410` | Vermilion (hanko / action) |
| `on-surface` | `#211a12` | Sumi ink text |
| `secondary-container` | `#7a5b00` | Gold accent |
| `outline` / `surface-variant` | `#8a7b5e` / `#d9ceaf` | Structural lines |

CSS custom properties in `global.css` (`--color-hazard`, `--color-abyss`, `--color-accent`, etc.) power the hazard stripes and hard shadows.

### Typography

- **Space Grotesk** — display and body (`headline-*`, `body-*`, `label-*`).
- **JetBrains Mono** — telemetry, code, and technical labels (`code-telemetry`, `label-badge`).
- **Material Symbols Outlined** — icons via ligatures.

### Utility Classes (defined in `global.css`)

| Class | Purpose |
| --- | --- |
| `.hazard-stripe` | Diagonal yellow/black caution stripe |
| `.grid-blueprint` | 40px engineering grid background |
| `.shadow-hard-red` | Offset hard shadow (black + vermilion) |
| `.shadow-hard-black` | Offset black hard shadow |
| `.shadow-hard-gold` | Offset black + gold hard shadow |
| `.btn-brutal` | Press-down mechanical click on `:active` |
| `.marquee-track` | Infinite horizontal scroll animation |
| `.sun-rays` | Rotating rising-sun rays |
| `.petal` / `.petal-inner` | Falling sakura petals |

---

## Content & Customization

Most page copy is data-driven and easy to update from the frontmatter of each component:

- **Divisions / spec book** → `src/components/Classification.astro`
- **Arena dimensions and tolerances** → `specs` array in `Dohyo.astro`
- **Rules and penalties** → `principles` array in `Bushido.astro`
- **Tournament stages** → `phases` array in `Schedule.astro`
- **Registration steps** → `steps` array in `Register.astro`
- **FAQ entries** → `faqs` array in `Faq.astro`
- **Ticker messages** → `items` array in `Ticker.astro`
- **Organizer facts** → `facts` array in `Branch.astro`
- **Global title/meta description** → `src/layouts/Layout.astro`

To re-theme the site, edit the color values in `tailwind.config.mjs`; the token names are stable, so component classes do not need to change.

---

## Deployment

Because `astro.config.mjs` sets `output: 'static'`, the contents of `dist/` can be hosted on any static host:

- **GitHub Pages** — publish `dist/` via a workflow or the `gh-pages` branch.
- **Netlify / Vercel / Cloudflare Pages** — build command `npm run build`, output directory `dist`.

No server-side runtime or environment variables are required.

---

## Scripts

| Command | Description |
| --- | --- |
| `npm run dev` | Start the Astro dev server |
| `npm run build` | Build the static production site into `dist/` |
| `npm run preview` | Serve the production build locally |
| `npm run astro` | Run the Astro CLI directly |

---

## Credits

Organized by the **IEEE Student Branch, École Nationale Polytechnique (ENP)** — El Harrach, Algiers. Part of the international IEEE network.

© 2026 IEEE Student Branch — Mechatronics & Robotics Chapter. All rights reserved.
