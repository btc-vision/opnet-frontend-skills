# Typography Reference

The default body font for all outputs is **Poppins**. Every theme uses Poppins as the body unless the user overrides it or the theme is fully monospaced (matrix/terminal). Display fonts are paired with Poppins per theme.

## Default Stack (all themes unless overridden)

```css
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700;800&display=swap');

:root {
  --font-body: 'Poppins', sans-serif;
  --font-display: 'Poppins', sans-serif;
}
```

When a theme needs a distinct display font, only `--font-display` changes. `--font-body` stays Poppins.

## Matrix / Terminal (exception: fully monospace)

Display: `"Share Tech Mono", monospace`
Body: `"IBM Plex Mono", monospace` (overrides Poppins for full terminal commitment)
Data: `"JetBrains Mono", monospace`

This is the only theme where Poppins is replaced entirely. The terminal aesthetic demands monospace everywhere. Use `letter-spacing: 0.05em` on body text for readability.

```css
@import url('https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=IBM+Plex+Mono:wght@400;500;600&display=swap');

[data-theme="matrix"] {
  --font-body: 'IBM Plex Mono', monospace;
  --font-display: 'Share Tech Mono', monospace;
}
```

## Cyberpunk / Neon

Display: `"Orbitron", sans-serif` or `"Rajdhani", sans-serif`
Body: `'Poppins', sans-serif` (default)
Data: `"Space Mono", monospace`

Orbitron for hero headings with `text-transform: uppercase` and `letter-spacing: 0.1em`. Poppins handles all body text.

```css
@import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@500;700;900&family=Poppins:wght@300;400;500;600;700&family=Space+Mono:wght@400;700&display=swap');

[data-theme="cyberpunk"] {
  --font-display: 'Orbitron', sans-serif;
}
```

## Clean Fintech

Display: `"Outfit", sans-serif` or `"Sora", sans-serif`
Body: `'Poppins', sans-serif` (default)
Data: Poppins with `font-variant-numeric: tabular-nums`

Outfit for section headings provides geometric contrast against Poppins body text. Clean and trustworthy.

```css
@import url('https://fonts.googleapis.com/css2?family=Outfit:wght@400;500;600;700&family=Poppins:wght@300;400;500;600;700&display=swap');

[data-theme="fintech"] {
  --font-display: 'Outfit', sans-serif;
}
```

## Dark Luxury

Display: `"Playfair Display", serif` or `"Cormorant Garamond", serif`
Body: `'Poppins', sans-serif` (default)
Data: Poppins with `font-weight: 300`

Serif display with Poppins body creates a high-end editorial feel. Use `font-weight: 300` on body for elegance in this theme.

```css
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;600;800&family=Poppins:wght@300;400;500;600;700&display=swap');

[data-theme="luxury"] {
  --font-display: 'Playfair Display', serif;
}
```

## Brutalist

Display: `"Archivo Black", sans-serif` or `"Space Grotesk", sans-serif`
Body: `'Poppins', sans-serif` (default)
Data: `"Space Mono", monospace`

Heavy display weights, tight line-heights, aggressive sizing. `font-size` on display headings should be noticeably large (clamp 3rem to 6rem).

```css
@import url('https://fonts.googleapis.com/css2?family=Archivo+Black&family=Poppins:wght@400;500;600;700&family=Space+Mono:wght@400;700&display=swap');

[data-theme="brutalist"] {
  --font-display: 'Archivo Black', sans-serif;
}
```

## Vapor / Gradient

Display: `"Righteous", sans-serif` or `"Megrim", cursive`
Body: `'Poppins', sans-serif` (default)
Data: `"Overpass Mono", monospace`

Righteous provides the retro-future display weight that pairs well with Poppins as the readable body.

```css
@import url('https://fonts.googleapis.com/css2?family=Righteous&family=Poppins:wght@300;400;500;600;700&family=Overpass+Mono:wght@400;700&display=swap');

[data-theme="vapor"] {
  --font-display: 'Righteous', sans-serif;
}
```

## Military / Tactical

Display: `"Black Ops One", sans-serif` or `"Saira Stencil One", sans-serif`
Body: `'Poppins', sans-serif` (default)
Data: `"Share Tech Mono", monospace`

Stencil display fonts for headings, Poppins for body. All-caps headings with wide letter-spacing.

```css
@import url('https://fonts.googleapis.com/css2?family=Black+Ops+One&family=Poppins:wght@400;500;600;700&family=Share+Tech+Mono&display=swap');

[data-theme="tactical"] {
  --font-display: 'Black Ops One', sans-serif;
}
```

## Typography Scale

Consistent modular scale, ratio 1.25 (major third):

```css
:root {
  --font-size-xs: clamp(0.64rem, 0.6rem + 0.2vw, 0.75rem);
  --font-size-sm: clamp(0.8rem, 0.76rem + 0.2vw, 0.875rem);
  --font-size-base: clamp(1rem, 0.95rem + 0.25vw, 1.0625rem);
  --font-size-md: clamp(1.125rem, 1.05rem + 0.35vw, 1.25rem);
  --font-size-lg: clamp(1.25rem, 1.1rem + 0.65vw, 1.5rem);
  --font-size-xl: clamp(1.5rem, 1.3rem + 0.9vw, 2rem);
  --font-size-2xl: clamp(2rem, 1.7rem + 1.3vw, 2.75rem);
  --font-size-3xl: clamp(2.5rem, 2rem + 2vw, 4rem);
  --font-size-hero: clamp(3rem, 2.2rem + 3.5vw, 6rem);
  --line-height-tight: 1.1;
  --line-height-snug: 1.25;
  --line-height-normal: 1.5;
  --line-height-relaxed: 1.625;
}
```

## Numeric Typography

Financial data, token amounts, and statistics always use tabular figures:

```css
.data-value {
  font-variant-numeric: tabular-nums;
  font-feature-settings: "tnum";
  letter-spacing: -0.01em;
}
```

Wallet addresses and transaction hashes use a monospace font with middle-truncation: `0x742d...f2bD18`.
