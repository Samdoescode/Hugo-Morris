# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm run dev          # Start dev server
npm run build        # Production build
npm run preview      # Preview production build
npm run check        # Type-check with svelte-check
npm run lint         # Prettier + ESLint check
npm run format       # Auto-format with Prettier
```

## Architecture

This is a **SvelteKit 2 + Svelte 5** single-page portfolio site for filmmaker Hugo Morris, using **Tailwind CSS v4**.

**Page structure** (`src/routes/`): The single route (`+page.svelte`) composes three full-screen sections stacked vertically:

1. **`VideoSection.svelte`** — Hero: fullscreen looping background video (`$lib/bgvideov2.mov`) with a masked text overlay effect using CSS `mask-image` and `mix-blend-mode: exclusion`.
2. **`AboutSection.svelte`** — Bio section: sticky headshot on left, scrolling bio text + film festival laurels on right. Uses `import.meta.glob` with `enhanced: true` to load all wreath images from `$lib/images/wreaths/` as optimized `<enhanced:img>` elements.
3. **`Portfolio.svelte`** — Film stills ticker: three rows of horizontally scrolling `MovieCards` with alternating left/right CSS keyframe animations (`tickerLeft`/`tickerRight` defined in `layout.css`).

**`MovieCards.svelte`** uses `import.meta.glob` with `?url` query to load all stills from `$lib/images/imagestills/Stills/`, shuffles them randomly, and assigns random heights for a mosaic effect.

**`Mousecursor.svelte`** — Custom SVG cursor rendered globally via `+layout.svelte`, using Svelte 5 `Spring` motion with two concentric circles (outer lags behind, inner follows tightly). The native cursor is hidden via `cursor: none` in `layout.css` and a `:global(body)` style.

**`+layout.svelte`** imports `layout.css` globally and renders `Mousecursor` outside the page slot so it persists across routes.

## Key details

- **Tailwind v4**: Config is via `@import 'tailwindcss'` and `@plugin` directives in `layout.css` — no `tailwind.config.js` file.
- **Custom font**: `Gasoline` (`/fonts/TG-Gasoline.otf`) loaded via `@font-face` in `layout.css`, applied with the `.gas` utility class.
- **`@sveltejs/enhanced-img`**: Used in `AboutSection` for optimized wreath images. Standard `<img>` tags are used in `MovieCards` (loaded as URLs).
- **Adapter**: `adapter-auto` — no deployment target locked in yet.
- **No tests** exist in this project.
