# Animations Reference

Copy-paste keyframe definitions and animation patterns for crypto frontends. All animations use `transform` and `opacity` only for GPU compositing, unless noted otherwise.

## Entry Animations

### Fade Up (default entry)

```css
@keyframes fadeUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-fade-up {
  animation: fadeUp 0.6s cubic-bezier(0.22, 1, 0.36, 1) both;
}
```

### Fade In Scale

```css
@keyframes fadeInScale {
  from {
    opacity: 0;
    transform: scale(0.95);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}

.animate-fade-scale {
  animation: fadeInScale 0.5s cubic-bezier(0.22, 1, 0.36, 1) both;
}
```

### Slide In From Left

```css
@keyframes slideInLeft {
  from {
    opacity: 0;
    transform: translateX(-30px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}
```

### Slide In From Right

```css
@keyframes slideInRight {
  from {
    opacity: 0;
    transform: translateX(30px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}
```

### Stagger Pattern

Apply incrementing delays to child elements for sequenced entry:

```css
.stagger-container > * {
  animation: fadeUp 0.5s cubic-bezier(0.22, 1, 0.36, 1) both;
}
.stagger-container > *:nth-child(1) { animation-delay: 0ms; }
.stagger-container > *:nth-child(2) { animation-delay: 80ms; }
.stagger-container > *:nth-child(3) { animation-delay: 160ms; }
.stagger-container > *:nth-child(4) { animation-delay: 240ms; }
.stagger-container > *:nth-child(5) { animation-delay: 320ms; }
.stagger-container > *:nth-child(6) { animation-delay: 400ms; }
```

For dynamic lists, use CSS `calc()` with custom property:

```css
.stagger-container > * {
  animation-delay: calc(var(--stagger-index, 0) * 80ms);
}
```

Set `--stagger-index` via inline style or JS.

## Hover and Interaction

### Card Lift

```css
.card-hover {
  transition: transform var(--transition-base), box-shadow var(--transition-base);
}
.card-hover:hover {
  transform: translateY(-4px);
  box-shadow: var(--shadow-lg), var(--shadow-glow);
}
```

### Button Press

```css
.btn-press {
  transition: transform var(--transition-fast), background-color var(--transition-fast);
}
.btn-press:hover {
  transform: translateY(-1px);
}
.btn-press:active {
  transform: translateY(1px) scale(0.98);
}
```

### Glow Pulse on Hover

```css
.glow-hover {
  position: relative;
}
.glow-hover::after {
  content: '';
  position: absolute;
  inset: -2px;
  border-radius: inherit;
  background: var(--accent-primary);
  opacity: 0;
  z-index: -1;
  filter: blur(12px);
  transition: opacity var(--transition-base);
}
.glow-hover:hover::after {
  opacity: 0.3;
}
```

### Border Gradient on Hover

```css
.border-gradient-hover {
  position: relative;
  background: var(--surface-raised);
  border-radius: var(--radius-lg);
  padding: 1px;
}
.border-gradient-hover::before {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: inherit;
  padding: 1px;
  background: linear-gradient(135deg, var(--accent-primary), var(--accent-secondary));
  mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
  mask-composite: exclude;
  opacity: 0;
  transition: opacity var(--transition-base);
}
.border-gradient-hover:hover::before {
  opacity: 1;
}
```

## Data and Loading

### Number Counter (CSS)

```css
@property --num {
  syntax: '<integer>';
  inherits: false;
  initial-value: 0;
}

.counter {
  --num: 0;
  counter-reset: num var(--num);
  transition: --num 2s cubic-bezier(0.22, 1, 0.36, 1);
}
.counter::after {
  content: counter(num);
}
.counter.active {
  --num: 1000; /* set target value */
}
```

### Number Counter (JS fallback)

```js
function animateCounter(element, target, duration = 2000) {
  const start = performance.now();
  const initial = 0;
  function update(now) {
    const elapsed = now - start;
    const progress = Math.min(elapsed / duration, 1);
    const eased = 1 - Math.pow(1 - progress, 3);
    const current = Math.floor(initial + (target - initial) * eased);
    element.textContent = current.toLocaleString();
    if (progress < 1) requestAnimationFrame(update);
  }
  requestAnimationFrame(update);
}
```

### Skeleton Loading Pulse

```css
@keyframes shimmer {
  0% { background-position: -200% 0; }
  100% { background-position: 200% 0; }
}

.skeleton {
  background: linear-gradient(
    90deg,
    var(--surface-raised) 25%,
    var(--surface-overlay) 50%,
    var(--surface-raised) 75%
  );
  background-size: 200% 100%;
  animation: shimmer 1.5s ease-in-out infinite;
  border-radius: var(--radius-sm);
}
```

### Progress Bar Fill

```css
.progress-fill {
  width: 0%;
  height: 100%;
  background: linear-gradient(90deg, var(--accent-primary), var(--accent-secondary));
  border-radius: inherit;
  transition: width 1s cubic-bezier(0.22, 1, 0.36, 1);
}
```

### Spinning Loader

```css
@keyframes spin {
  to { transform: rotate(360deg); }
}

.spinner {
  width: 20px;
  height: 20px;
  border: 2px solid var(--border-subtle);
  border-top-color: var(--accent-primary);
  border-radius: 50%;
  animation: spin 0.8s linear infinite;
}
```

## Ambient / Theme Effects

### Matrix Rain (CSS-only, lightweight)

```css
@keyframes matrixFall {
  0% {
    transform: translateY(-100vh);
    opacity: 1;
  }
  100% {
    transform: translateY(100vh);
    opacity: 0;
  }
}

.matrix-rain {
  position: fixed;
  inset: 0;
  overflow: hidden;
  pointer-events: none;
  z-index: 0;
}

.matrix-rain span {
  position: absolute;
  top: 0;
  color: var(--accent-primary);
  font-family: 'Share Tech Mono', monospace;
  font-size: 14px;
  opacity: 0.6;
  animation: matrixFall linear infinite;
  writing-mode: vertical-rl;
}
```

Generate spans with varying `left`, `animation-duration` (8-20s), and `animation-delay` (0-10s) via JS or server-side.

### Scanline Overlay

```css
.scanlines::after {
  content: '';
  position: fixed;
  inset: 0;
  pointer-events: none;
  background: repeating-linear-gradient(
    0deg,
    transparent,
    transparent 2px,
    rgba(0, 0, 0, 0.08) 2px,
    rgba(0, 0, 0, 0.08) 4px
  );
  z-index: 9999;
}
```

### Subtle Gradient Drift

```css
@keyframes gradientDrift {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}

.gradient-drift {
  background: linear-gradient(
    135deg,
    var(--surface-base),
    var(--surface-raised),
    var(--surface-overlay),
    var(--surface-raised),
    var(--surface-base)
  );
  background-size: 400% 400%;
  animation: gradientDrift 15s ease infinite;
}
```

### Pulse Glow

```css
@keyframes pulseGlow {
  0%, 100% {
    box-shadow: 0 0 8px var(--accent-glow);
  }
  50% {
    box-shadow: 0 0 24px var(--accent-glow), 0 0 48px var(--accent-glow);
  }
}

.pulse-glow {
  animation: pulseGlow 3s ease-in-out infinite;
}
```

### Flicker (cyberpunk)

```css
@keyframes flicker {
  0%, 100% { opacity: 1; }
  92% { opacity: 1; }
  93% { opacity: 0.8; }
  94% { opacity: 1; }
  96% { opacity: 0.9; }
  97% { opacity: 1; }
}

.flicker {
  animation: flicker 4s linear infinite;
}
```

## Reduced Motion

Always include this block at the end of the stylesheet:

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}
```
