# Theme Presets Reference

Complete `data-theme` override blocks ready to drop into any stylesheet. Each preset overrides every custom property from the base `:root` set defined in SKILL.md.

## Implementation Pattern

Place all theme blocks after the `:root` declaration. The active theme is controlled by a `data-theme` attribute on `<html>`.

```html
<html data-theme="matrix">
```

```css
:root { /* base defaults from SKILL.md */ }
[data-theme="matrix"] { /* overrides */ }
[data-theme="cyberpunk"] { /* overrides */ }
/* ... */
```

## Theme Toggle Component

Minimal toggle that cycles through available themes:

```html
<div class="theme-switcher" role="radiogroup" aria-label="Theme selector">
  <button class="theme-btn" data-set-theme="matrix" aria-label="Matrix theme">
    <span class="theme-btn__swatch" style="background:#00ff41"></span>
    <span class="theme-btn__label">Matrix</span>
  </button>
  <button class="theme-btn" data-set-theme="cyberpunk" aria-label="Cyberpunk theme">
    <span class="theme-btn__swatch" style="background:#ff00ff"></span>
    <span class="theme-btn__label">Cyberpunk</span>
  </button>
  <!-- add more as needed -->
</div>
```

```css
.theme-switcher {
  display: flex;
  gap: var(--space-sm);
  padding: var(--space-sm);
  background: var(--surface-raised);
  border-radius: var(--radius-lg);
  border: 1px solid var(--border-subtle);
}

.theme-btn {
  display: flex;
  align-items: center;
  gap: var(--space-xs);
  padding: var(--space-xs) var(--space-sm);
  background: transparent;
  border: 1px solid transparent;
  border-radius: var(--radius-md);
  color: var(--text-secondary);
  cursor: pointer;
  transition: all var(--transition-fast);
  font-family: inherit;
  font-size: var(--font-size-sm);
}

.theme-btn:hover {
  background: var(--surface-interactive);
  border-color: var(--border-interactive);
  color: var(--text-primary);
}

.theme-btn[aria-checked="true"] {
  background: var(--surface-overlay);
  border-color: var(--accent-primary);
  color: var(--text-accent);
}

.theme-btn__swatch {
  width: 12px;
  height: 12px;
  border-radius: var(--radius-full);
  flex-shrink: 0;
}
```

```js
const themeButtons = document.querySelectorAll('[data-set-theme]');

function setTheme(name) {
  document.documentElement.setAttribute('data-theme', name);
  localStorage.setItem('preferred-theme', name);
  themeButtons.forEach(btn => {
    btn.setAttribute('aria-checked', btn.dataset.setTheme === name ? 'true' : 'false');
  });
}

themeButtons.forEach(btn => {
  btn.addEventListener('click', () => setTheme(btn.dataset.setTheme));
});

const saved = localStorage.getItem('preferred-theme');
if (saved) setTheme(saved);
```

## Dark/Light Toggle

For simpler two-state toggles (dark vs light), use a switch-style button:

```js
function toggleDarkLight() {
  const current = document.documentElement.getAttribute('data-theme');
  const next = current === 'light' ? 'dark' : 'light';
  setTheme(next);
}
```

Respect system preference on first visit:

```js
if (!localStorage.getItem('preferred-theme')) {
  const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
  setTheme(prefersDark ? 'dark' : 'light');
}
```

## Transition Between Themes

Add a smooth transition when switching themes to avoid a jarring flash:

```css
html.theme-transitioning,
html.theme-transitioning *,
html.theme-transitioning *::before,
html.theme-transitioning *::after {
  transition: background-color 300ms ease, color 300ms ease, border-color 300ms ease, box-shadow 300ms ease !important;
}
```

```js
function setThemeSmooth(name) {
  document.documentElement.classList.add('theme-transitioning');
  setTheme(name);
  setTimeout(() => {
    document.documentElement.classList.remove('theme-transitioning');
  }, 350);
}
```

## Complete Theme Variable Reference

Every theme must override all of these properties to avoid fallback inconsistencies. See `references/color-systems.md` for the actual color values per theme. The full property list that each `[data-theme]` block must include:

```
--surface-base
--surface-raised
--surface-overlay
--surface-interactive
--text-primary
--text-secondary
--text-muted
--text-accent
--accent-primary
--accent-secondary
--accent-glow
--border-subtle
--border-interactive
--color-success
--color-warning
--color-error
--color-info
--shadow-sm
--shadow-md
--shadow-lg
--shadow-glow
```

Spacing, radius, and transition variables generally stay constant across themes unless the theme's aesthetic demands different spatial treatment (brutalist might use sharper radii, vapor might use rounder ones).
