# Color Systems Reference

Complete color palettes for each theme. Each palette defines surface hierarchy, text hierarchy, accent colors, feedback colors, and glow/effect colors.

## Palette Construction Rules

Every palette follows this structure: 3-4 surface tones (darkest to lightest), 3 text tones (primary, secondary, muted), 1-2 accent colors, 4 feedback colors (success, warning, error, info), and glow/transparency variants of the accents.

Accent colors must have sufficient contrast against all surface tones. Test with WCAG AA minimum (4.5:1 for text, 3:1 for large text and UI components).

## Matrix / Terminal

```css
[data-theme="matrix"] {
  --surface-base: #000000;
  --surface-raised: #0a0f0a;
  --surface-overlay: #0f1a0f;
  --surface-interactive: #152015;
  --text-primary: #00ff41;
  --text-secondary: #00cc33;
  --text-muted: #006622;
  --text-accent: #33ff66;
  --accent-primary: #00ff41;
  --accent-secondary: #00cc33;
  --accent-glow: rgba(0, 255, 65, 0.15);
  --border-subtle: rgba(0, 255, 65, 0.08);
  --border-interactive: rgba(0, 255, 65, 0.2);
  --color-success: #00ff41;
  --color-warning: #ccff00;
  --color-error: #ff3300;
  --color-info: #00ccff;
  --shadow-glow: 0 0 20px rgba(0, 255, 65, 0.2);
}
```

Body text in matrix theme should use `text-shadow: 0 0 8px rgba(0, 255, 65, 0.3)` sparingly on headings and key data.

## Cyberpunk / Neon

```css
[data-theme="cyberpunk"] {
  --surface-base: #0d0221;
  --surface-raised: #150535;
  --surface-overlay: #1a0845;
  --surface-interactive: #220b55;
  --text-primary: #e0d0ff;
  --text-secondary: #a088cc;
  --text-muted: #604888;
  --text-accent: #ff00ff;
  --accent-primary: #ff00ff;
  --accent-secondary: #00ffff;
  --accent-glow: rgba(255, 0, 255, 0.15);
  --border-subtle: rgba(255, 0, 255, 0.08);
  --border-interactive: rgba(255, 0, 255, 0.2);
  --color-success: #00ff88;
  --color-warning: #ffaa00;
  --color-error: #ff2255;
  --color-info: #00ffff;
  --shadow-glow: 0 0 20px rgba(255, 0, 255, 0.25);
}
```

Cyberpunk thrives on dual-accent. Use magenta for primary actions and cyan for secondary/informational. Neon glow text-shadows on headings: `text-shadow: 0 0 10px rgba(255, 0, 255, 0.5), 0 0 40px rgba(255, 0, 255, 0.2)`.

## Clean Fintech

```css
[data-theme="fintech"] {
  --surface-base: #0c0f14;
  --surface-raised: #141820;
  --surface-overlay: #1c2028;
  --surface-interactive: #242830;
  --text-primary: #e4e8f0;
  --text-secondary: #8892a8;
  --text-muted: #505868;
  --text-accent: #3b82f6;
  --accent-primary: #3b82f6;
  --accent-secondary: #10b981;
  --accent-glow: rgba(59, 130, 246, 0.1);
  --border-subtle: rgba(255, 255, 255, 0.06);
  --border-interactive: rgba(255, 255, 255, 0.1);
  --color-success: #10b981;
  --color-warning: #f59e0b;
  --color-error: #ef4444;
  --color-info: #3b82f6;
  --shadow-glow: 0 0 16px rgba(59, 130, 246, 0.12);
}
```

Fintech light mode variant:

```css
[data-theme="fintech-light"] {
  --surface-base: #f8f9fc;
  --surface-raised: #ffffff;
  --surface-overlay: #f0f2f8;
  --surface-interactive: #e8ecf4;
  --text-primary: #111827;
  --text-secondary: #4b5563;
  --text-muted: #9ca3af;
  --text-accent: #2563eb;
  --accent-primary: #2563eb;
  --accent-secondary: #059669;
  --accent-glow: rgba(37, 99, 235, 0.08);
  --border-subtle: rgba(0, 0, 0, 0.06);
  --border-interactive: rgba(0, 0, 0, 0.12);
  --color-success: #059669;
  --color-warning: #d97706;
  --color-error: #dc2626;
  --color-info: #2563eb;
  --shadow-sm: 0 1px 2px rgba(0, 0, 0, 0.05);
  --shadow-md: 0 4px 12px rgba(0, 0, 0, 0.08);
  --shadow-lg: 0 8px 32px rgba(0, 0, 0, 0.1);
  --shadow-glow: 0 0 16px rgba(37, 99, 235, 0.08);
}
```

## Dark Luxury

```css
[data-theme="luxury"] {
  --surface-base: #0a0a0a;
  --surface-raised: #141414;
  --surface-overlay: #1e1e1e;
  --surface-interactive: #282828;
  --text-primary: #f0e6d3;
  --text-secondary: #a89880;
  --text-muted: #685840;
  --text-accent: #d4a853;
  --accent-primary: #d4a853;
  --accent-secondary: #8b7355;
  --accent-glow: rgba(212, 168, 83, 0.12);
  --border-subtle: rgba(212, 168, 83, 0.08);
  --border-interactive: rgba(212, 168, 83, 0.15);
  --color-success: #4ade80;
  --color-warning: #d4a853;
  --color-error: #f87171;
  --color-info: #60a5fa;
  --shadow-glow: 0 0 20px rgba(212, 168, 83, 0.1);
}
```

Gold accent on near-black surfaces. Minimal glow, more reliance on sharp borders and shadow depth. Serif display fonts amplify this palette.

## Brutalist

```css
[data-theme="brutalist"] {
  --surface-base: #ffffff;
  --surface-raised: #f0f0f0;
  --surface-overlay: #e0e0e0;
  --surface-interactive: #cccccc;
  --text-primary: #000000;
  --text-secondary: #333333;
  --text-muted: #666666;
  --text-accent: #ff0000;
  --accent-primary: #ff0000;
  --accent-secondary: #0000ff;
  --accent-glow: none;
  --border-subtle: #000000;
  --border-interactive: #000000;
  --color-success: #00aa00;
  --color-warning: #ff8800;
  --color-error: #ff0000;
  --color-info: #0000ff;
  --shadow-sm: none;
  --shadow-md: 4px 4px 0 #000000;
  --shadow-lg: 8px 8px 0 #000000;
  --shadow-glow: none;
}
```

Hard shadows, no gradients, no glow. Black borders, high contrast. The aesthetic power comes from typography scale and whitespace, not color effects.

## Vapor / Gradient

```css
[data-theme="vapor"] {
  --surface-base: #1a0030;
  --surface-raised: #250045;
  --surface-overlay: #300055;
  --surface-interactive: #3a0068;
  --text-primary: #f0e0ff;
  --text-secondary: #bb99dd;
  --text-muted: #7755aa;
  --text-accent: #ff77cc;
  --accent-primary: #ff77cc;
  --accent-secondary: #77ddff;
  --accent-glow: rgba(255, 119, 204, 0.15);
  --border-subtle: rgba(255, 119, 204, 0.08);
  --border-interactive: rgba(255, 119, 204, 0.18);
  --color-success: #77ffaa;
  --color-warning: #ffcc55;
  --color-error: #ff5577;
  --color-info: #77ddff;
  --shadow-glow: 0 0 24px rgba(255, 119, 204, 0.2);
}
```

Gradient overlays on cards and buttons. Background uses multi-stop gradients with purple, pink, and teal. Heavy use of `backdrop-filter: blur()` for glassmorphism.

## Military / Tactical

```css
[data-theme="tactical"] {
  --surface-base: #0a0c08;
  --surface-raised: #12150f;
  --surface-overlay: #1a1e16;
  --surface-interactive: #22261e;
  --text-primary: #c8d0b8;
  --text-secondary: #8a9478;
  --text-muted: #556048;
  --text-accent: #7cfc00;
  --accent-primary: #7cfc00;
  --accent-secondary: #ff6600;
  --accent-glow: rgba(124, 252, 0, 0.1);
  --border-subtle: rgba(124, 252, 0, 0.06);
  --border-interactive: rgba(124, 252, 0, 0.15);
  --color-success: #7cfc00;
  --color-warning: #ff6600;
  --color-error: #ff2200;
  --color-info: #00aaff;
  --shadow-glow: 0 0 16px rgba(124, 252, 0, 0.12);
}
```

Olive and dark green surfaces, lawn green accent, orange for warnings. Crosshair cursors on interactive elements, stencil fonts, and scanline overlays reinforce the aesthetic.
