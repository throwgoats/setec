# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**SETEC** is a class-based CSS utility library with a 1980s terminal aesthetic and modern wide-gamut OKLCH colors. Like Tailwind in execution — apply HTML classes to style elements — but purpose-built for this visual language. Outputs a single linkable CSS file.

Design references are in `/docs/insp/` — these define the target aesthetic.

## Build Commands

```bash
npm run build   # Produces dist/setec.css (full) and dist/setec.min.css (minified)
npm run watch   # Rebuilds on file save
```

Open `demo/index.html` directly in a browser to view the component reference (no server needed). It includes a live contrast slider.

## Architecture

**Tech stack:** PostCSS (`postcss-import`, `postcss-nesting`, `autoprefixer`, `cssnano`)  
**Entry point:** `src/index.css` — imports all partials in order  
**Output:** `dist/` (git-ignored)

### Color System

`--setec-contrast: 1–100` (default `80`) is the master intensity knob. Set it on `:root` or any ancestor element. All color tokens reference it:

```css
oklch(L calc(C * var(--setec-c)) H)
```

At 100 → vivid P3 wide-gamut neons. At ~30 → muted earth tones. The chroma (`C`) scales linearly; lightness (`L`) shifts slightly to maintain contrast at low values. All tokens live in `src/base/root.css`.

### Source Layout

```
src/
├── base/        root.css (tokens), reset.css, base.css
├── typography/  fonts.css (@font-face for 3 Nerdfonts), text.css
├── colors/      palette.css (.text-*, .bg-*, .border-*)
├── components/  one file per component
└── utilities/   spacing.css, layout.css, states.css
```

### Class Naming Conventions

- Components use semantic names: `.btn-primary`, `.field-input`, `.nav-tab`, `.progress-bar`
- Color utilities: `.text-{hue}`, `.text-{hue}-{100|300|500|700|900}`, `.bg-{hue}`, `.border-{hue}`
- State modifiers: `.is-error`, `.is-warning`, `.is-success`, `.is-disabled`, `.active`, `.collapsed`
- Font selectors: `.font-jetbrains` (default), `.font-hack`, `.font-iosevka`

### Typography

Headers are the same font-size as body — distinguished only by `font-weight: 700` and color. No size scale. Three Nerdfonts loaded via `@font-face` from `/fonts/` (woff2 files not yet committed — users can install fonts locally or provide their own woff2 files).

### Checkered Pattern

Used for inactive calendar cells, unfilled progress segments. Applied via the CSS custom property `--setec-checkered` (defined in `root.css`) as a `background-image` on any element.

### Light Theme

`.light` class on the root element overrides surface tokens. Color values are stubbed — not built yet.
