# CLAUDE.md

This file provides guidance for AI assistants working in this repository.

## Project Overview

**a-claymorphism-demo** is a static HTML/CSS prototype showcasing the claymorphism design trend. It is a landing page with sections for features, a styleguide, a gallery, and pricing. There is no JavaScript, no build system, and no package manager — everything runs by opening `index.html` directly in a browser.

## Repository Structure

```
a-claymorphism-demo/
├── index.html            # Single-page HTML landing page (247 lines)
├── assets/
│   └── css/
│       └── styles.css    # All styling (483 lines)
├── README.md             # Project overview and design reference
├── hello.txt             # Empty placeholder file (ignore)
└── .gitattributes        # LF line ending normalization
```

## Tech Stack

| Layer        | Technology                            |
|--------------|---------------------------------------|
| Markup       | HTML5 (semantic elements only)        |
| Styling      | CSS3 (no preprocessors)               |
| Typography   | Poppins via Google Fonts CDN          |
| JavaScript   | None                                  |
| Build tools  | None                                  |
| Package mgr  | None                                  |
| Testing      | None                                  |
| Deployment   | Static file — open in browser         |

## Design System

The project implements **claymorphism**, a UI design trend. Key visual properties:

### CSS Custom Properties (defined in `:root`)
- `--color-bg` — page background gradient (`#f7d9ff → #c1e5ff`)
- `--color-surface` — neutral surface (`#f1f0ff`)
- `--color-text` — dark purple (`#2f2a4a`)
- `--color-accent` — vibrant purple (`#7a5cff`)
- `--shadow-outer` — `12px 12px 24px rgba(15, 23, 42, 0.25)`
- `--shadow-inner` — `inset -8px -8px 16px rgba(255, 255, 255, 0.75)`

### Claymorphism Visual Principles
1. **Soft gradients** — pastel backgrounds (lavender → sky blue)
2. **Diffused outer shadows** — large, soft drop shadows for depth
3. **Inner highlights** — inset white shadow simulates a raised surface
4. **Noise texture overlay** — SVG fractal noise applied over cards for tactile realism
5. **Glassmorphism nav** — `backdrop-filter: blur()` on the navigation bar

## HTML Conventions

- Use **semantic HTML5** elements: `<header>`, `<main>`, `<section>`, `<footer>`, `<article>`, `<nav>`
- Class naming follows a **BEM-inspired** pattern: `.component__element--modifier`
- Common component classes: `.card`, `.btn`, `.tile`, `.section`, `.container`
- Include `aria-label` attributes on interactive elements for accessibility
- Inline emoji are used for decorative visual elements (intentional)
- Indentation: **2 spaces**

## CSS Conventions

- All global tokens live in the `:root {}` block at the top of `styles.css`
- Component styles are grouped below the root variables, organized by section order matching the HTML
- Use CSS custom properties (`var(--...)`) rather than hard-coded values for colors and shadows
- Responsive design uses a single mobile breakpoint: `@media (max-width: 768px)`
- Prefer **CSS Grid** for two-dimensional layouts, **Flexbox** for one-dimensional alignment
- Hover transitions use `transition: all 0.3s ease`
- No vendor prefixes (modern browsers only)

## Page Sections (in order)

1. **Header / Navigation** — `.navbar` with logo, nav links, and CTA buttons
2. **Hero** — Large headline with gradient text and primary CTA
3. **Features** — Three `.card` components with icon, title, and description
4. **Styleguide** — Typography scale, color palette, depth effects demo
5. **Gallery** — `.tile` inspiration cards (control clusters, dialogue bubbles, product display)
6. **Pricing** — Three `.pricing-card` tiers: Starter (free), Studio ($18), Agency ($49)
7. **Footer** — Social links (Instagram, Dribbble, Behance)

## Development Workflow

Since there is no build step:

1. **Edit** `index.html` or `assets/css/styles.css` directly
2. **Preview** by opening `index.html` in any modern browser
3. **Refresh** the browser to see changes (no hot reload)

No installations, no compilation, no servers required.

## Git Workflow

- The main integration branch is `main` (remote) / `master` (local default)
- Feature work is done on `claude/...` branches
- Commit messages should be short and descriptive in the imperative mood (e.g., "Add pricing section")
- Keep commits focused — one logical change per commit

## What to Avoid

- Do **not** introduce JavaScript unless explicitly requested; the project is intentionally JS-free
- Do **not** add build tooling (webpack, vite, npm) without a clear requirement
- Do **not** add a CSS preprocessor (SCSS/LESS); keep plain CSS
- Do **not** duplicate CSS custom property values inline — always reference `var(--...)`
- Do **not** use `!important` in CSS
- Do **not** add framework dependencies (React, Tailwind, Bootstrap, etc.)
- Do **not** modify `hello.txt` — it is an empty placeholder with no purpose

## Common Tasks

### Add a new section
1. Add the HTML block in `index.html` following the existing section structure
2. Add corresponding styles in `styles.css`, grouped near related sections
3. Use existing CSS custom properties for colors and shadows

### Add a new card / component
- Copy an existing `.card` or `.tile` block as a starting template
- Apply the standard shadow pattern: `box-shadow: var(--shadow-outer), var(--shadow-inner)`
- Add a gradient background consistent with the palette

### Update the color palette
- Change values only in the `:root {}` block in `styles.css`; all components inherit automatically

### Responsive adjustments
- Add rules inside the existing `@media (max-width: 768px)` block at the bottom of `styles.css`
