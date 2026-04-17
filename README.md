# SETEC

> *"Too Many Secrets"*
> — SETEC ASTRONOMY, *Sneakers* (1992)

A class-based CSS library with a 1980s terminal aesthetic, updated with modern wide-gamut colors that burn bright on dark backgrounds. Think Tailwind in execution — drop classes on HTML — but purpose-built for this specific visual language rather than general-purpose layout.

---

## What it looks like

Monospace everything. Lime green on near-black. Vivid cyan. Hot amber. Bracket-style UI chrome (`[save]`, `[✓]`, `[-] 3 [+]`). Comment text in gray (`// like this`). No rounded corners unless explicitly called for. The kind of interface that feels like it was compiled, not designed.

## What's included

- **Color system** — OKLCH wide-gamut palette (green, cyan, amber, purple, red, neutral) with 5 shades each. All colors exceed the sRGB gamut on P3 displays. A single `--setec-contrast` variable (1–100) scales the entire palette from muted earth tones to full cyberpunk neon.
- **Typography** — Three [Nerd Font](https://www.nerdfonts.com/) choices: JetBrainsMono (default), Hack, and Iosevka. Headers are body size, distinguished only by bold weight and color — no type scale.
- **Components** — Every pattern from the design references: tab navigation, terminal prompt chrome, section headers with collapse, checklist items, form fields, toggles, day-of-week pickers, steppers, color swatches, pills, badges, period filters, progress bars, segmented meters, calendar grids, contribution heatmaps, horizontal bar charts, stat rows, panels, and a mobile-style status bar.
- **Utilities** — Spacing, layout (flex/grid), and state classes (`.is-error`, `.is-warning`, `.is-success`, `.is-disabled`, focus ring).

## Getting started

**1. Build from source**

```bash
npm install
npm run build
```

This produces `dist/setec.css` (full) and `dist/setec.min.css` (minified).

**2. Link the stylesheet**

```html
<link rel="stylesheet" href="dist/setec.css">
```

**3. Set the contrast level** (optional — defaults to 80)

```css
:root {
  --setec-contrast: 80; /* 1 = muted earth tones, 100 = full neon */
}
```

Or override it on any element to scope intensity:

```html
<div style="--setec-contrast: 40">
  <!-- dimmed section -->
</div>
```

**4. Apply classes**

```html
<div class="prompt">
  <span class="prompt-user">shawn</span>
  <span class="prompt-at">@</span>
  <span class="prompt-host">setec</span>
  <span class="prompt-dollar">$</span>
  <span class="prompt-cmd">hello world</span>
</div>

<div class="comment">// this is going to look great</div>

<button class="btn btn-primary">engage</button>
<button class="btn btn-ghost">cancel</button>
```

## Fonts

SETEC uses [Nerd Fonts](https://www.nerdfonts.com/) for the terminal icon glyphs. The `@font-face` declarations in `src/typography/fonts.css` expect woff2 files in `/fonts/` — download your preferred variants from nerdfonts.com and drop them in. If the fonts are already installed on the system, the `@font-face` blocks are optional; the library falls back to the system monospace.

**Default:** JetBrainsMono Nerd Font  
**Alternatives:** `.font-hack`, `.font-iosevka`

## Color classes

```html
<!-- Text -->
<span class="text-green">primary</span>
<span class="text-cyan">secondary</span>
<span class="text-amber">accent</span>
<span class="text-error">error</span>
<span class="text-comment">// muted comment</span>

<!-- Specific shades (100–900) -->
<span class="text-green-300">lighter green</span>
<span class="text-amber-700">darker amber</span>

<!-- Background -->
<div class="bg-surface">base surface</div>
<div class="bg-green-900">deep green</div>
```

## Light theme

A `.light` class is stubbed on `:root` / `body` and overrides surface tokens. Color values are not yet defined — dark theme is the current focus.

## Demo

Open `demo/index.html` directly in a browser. It includes a live contrast slider so you can scrub from earth tones to full neon in real time.

---

## The name

SETEC is a nod to **SETEC ASTRONOMY** — the anagram at the center of the 1992 film *Sneakers*. It means *"too many secrets."* Seemed fitting for a library built around the aesthetic of glowing terminals and things that look like they shouldn't be on your screen.
