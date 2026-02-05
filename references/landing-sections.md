# Landing Page Sections Reference

Complete CSS patterns for every section type in a crypto landing page. Each section is a full-width block with its own background treatment and spacing. Use these as starting points and customize per theme.

## Section Base Pattern

Every section shares this base:

```css
.section {
  position: relative;
  width: 100%;
  padding: var(--space-3xl) var(--space-lg);
  overflow: hidden;
}

.section__inner {
  max-width: 1200px;
  margin: 0 auto;
  position: relative;
  z-index: 1;
}

.section__heading {
  font-family: var(--font-display);
  font-size: var(--font-size-2xl);
  font-weight: 700;
  color: var(--text-primary);
  text-align: center;
  margin-bottom: var(--space-sm);
}

.section__subheading {
  font-family: var(--font-body);
  font-size: var(--font-size-md);
  color: var(--text-secondary);
  text-align: center;
  max-width: 60ch;
  margin: 0 auto var(--space-2xl);
}

@media (min-width: 768px) {
  .section { padding: var(--space-3xl) var(--space-xl); }
}

@media (min-width: 1024px) {
  .section { padding: 80px var(--space-2xl); }
}
```

## Alternating Background Pattern

```css
.section--base { background: var(--surface-base); }
.section--raised { background: var(--surface-raised); }
.section--overlay {
  background: var(--surface-overlay);
  border-top: 1px solid var(--border-subtle);
  border-bottom: 1px solid var(--border-subtle);
}
.section--accent-wash {
  background: linear-gradient(
    135deg,
    rgba(0, 255, 136, 0.03) 0%,
    var(--surface-raised) 50%,
    rgba(0, 136, 255, 0.03) 100%
  );
}
```

## Hero Section

```css
.hero {
  position: relative;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  padding: var(--space-3xl) var(--space-lg);
  overflow: hidden;
  background: var(--surface-base);
}

/* Atmospheric glow orbs */
.hero::before {
  content: '';
  position: absolute;
  top: -20%;
  left: -10%;
  width: 60%;
  height: 60%;
  background: radial-gradient(circle, var(--accent-glow) 0%, transparent 70%);
  filter: blur(80px);
  z-index: 0;
  pointer-events: none;
}

.hero::after {
  content: '';
  position: absolute;
  bottom: -15%;
  right: -5%;
  width: 50%;
  height: 50%;
  background: radial-gradient(circle, rgba(0, 136, 255, 0.08) 0%, transparent 70%);
  filter: blur(80px);
  z-index: 0;
  pointer-events: none;
}

.hero > * { position: relative; z-index: 1; }

.hero__badge {
  display: inline-flex;
  align-items: center;
  gap: var(--space-xs);
  padding: var(--space-xs) var(--space-md);
  background: var(--surface-raised);
  border: 1px solid var(--border-subtle);
  border-radius: var(--radius-full);
  font-size: var(--font-size-sm);
  color: var(--text-accent);
  margin-bottom: var(--space-lg);
  animation: fadeUp 0.5s cubic-bezier(0.22, 1, 0.36, 1) both;
}

.hero__headline {
  font-family: var(--font-display);
  font-size: var(--font-size-hero);
  font-weight: 800;
  line-height: var(--line-height-tight);
  color: var(--text-primary);
  max-width: 14ch;
  margin-bottom: var(--space-md);
  animation: fadeUp 0.6s cubic-bezier(0.22, 1, 0.36, 1) 0.1s both;
}

.hero__sub {
  font-family: var(--font-body);
  font-size: var(--font-size-lg);
  color: var(--text-secondary);
  max-width: 50ch;
  margin-bottom: var(--space-xl);
  line-height: var(--line-height-relaxed);
  animation: fadeUp 0.6s cubic-bezier(0.22, 1, 0.36, 1) 0.2s both;
}

.hero__actions {
  display: flex;
  gap: var(--space-md);
  flex-wrap: wrap;
  justify-content: center;
  animation: fadeUp 0.6s cubic-bezier(0.22, 1, 0.36, 1) 0.3s both;
}

@media (max-width: 767px) {
  .hero { min-height: 90vh; padding-top: 100px; }
  .hero__actions { flex-direction: column; width: 100%; max-width: 320px; }
}
```

## Stats Bar

```css
.stats-bar {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
  gap: var(--space-lg);
  padding: var(--space-xl) var(--space-lg);
  background: var(--surface-raised);
  border-top: 1px solid var(--border-subtle);
  border-bottom: 1px solid var(--border-subtle);
}

.stats-bar__inner {
  max-width: 1200px;
  margin: 0 auto;
  display: contents;
}

.stats-bar__item {
  text-align: center;
  padding: var(--space-md) 0;
}

.stats-bar__value {
  font-family: var(--font-display);
  font-size: var(--font-size-2xl);
  font-weight: 700;
  color: var(--text-accent);
  font-variant-numeric: tabular-nums;
  display: block;
  line-height: 1.2;
}

.stats-bar__label {
  font-size: var(--font-size-sm);
  color: var(--text-muted);
  text-transform: uppercase;
  letter-spacing: 0.08em;
  margin-top: var(--space-xs);
}

@media (max-width: 767px) {
  .stats-bar {
    grid-template-columns: repeat(2, 1fr);
    gap: var(--space-md);
  }
}
```

## Feature Cards

```css
.features {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: var(--space-lg);
}

.feature-card {
  padding: var(--space-xl);
  background: var(--surface-raised);
  border: 1px solid var(--border-subtle);
  border-radius: var(--radius-xl);
  transition: all var(--transition-base);
}

.feature-card:hover {
  transform: translateY(-4px);
  border-color: var(--border-interactive);
  box-shadow: var(--shadow-lg), var(--shadow-glow);
}

.feature-card__icon {
  width: 48px;
  height: 48px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: var(--accent-glow);
  border-radius: var(--radius-lg);
  color: var(--accent-primary);
  margin-bottom: var(--space-md);
}

.feature-card__title {
  font-family: var(--font-display);
  font-size: var(--font-size-md);
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: var(--space-sm);
}

.feature-card__desc {
  font-size: var(--font-size-base);
  color: var(--text-secondary);
  line-height: var(--line-height-normal);
}

@media (max-width: 767px) {
  .features { grid-template-columns: 1fr; }
}
```

## How It Works / Steps

```css
.steps {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: var(--space-xl);
  counter-reset: step-counter;
}

.step {
  text-align: center;
  position: relative;
  counter-increment: step-counter;
}

.step::before {
  content: counter(step-counter, decimal-leading-zero);
  display: block;
  font-family: var(--font-display);
  font-size: var(--font-size-3xl);
  font-weight: 800;
  color: var(--accent-glow);
  margin-bottom: var(--space-md);
  line-height: 1;
}

.step__title {
  font-family: var(--font-display);
  font-size: var(--font-size-md);
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: var(--space-sm);
}

.step__desc {
  font-size: var(--font-size-base);
  color: var(--text-secondary);
  line-height: var(--line-height-normal);
  max-width: 30ch;
  margin: 0 auto;
}

/* Connector line between steps on desktop */
@media (min-width: 768px) {
  .step:not(:last-child)::after {
    content: '';
    position: absolute;
    top: 24px;
    right: calc(-1 * var(--space-xl) / 2);
    width: var(--space-xl);
    height: 1px;
    background: var(--border-interactive);
  }
}

@media (max-width: 767px) {
  .steps { grid-template-columns: 1fr; max-width: 360px; margin: 0 auto; }
}
```

## CTA Section

```css
.cta-section {
  position: relative;
  padding: var(--space-3xl) var(--space-lg);
  text-align: center;
  overflow: hidden;
  background: linear-gradient(
    135deg,
    var(--surface-raised) 0%,
    var(--surface-overlay) 100%
  );
}

.cta-section::before {
  content: '';
  position: absolute;
  inset: 0;
  background: radial-gradient(
    ellipse at 50% 50%,
    var(--accent-glow) 0%,
    transparent 60%
  );
  pointer-events: none;
}

.cta-section > * { position: relative; z-index: 1; }

.cta-section__headline {
  font-family: var(--font-display);
  font-size: var(--font-size-2xl);
  font-weight: 700;
  color: var(--text-primary);
  margin-bottom: var(--space-md);
}

.cta-section__sub {
  font-size: var(--font-size-md);
  color: var(--text-secondary);
  max-width: 50ch;
  margin: 0 auto var(--space-xl);
}
```

## Footer

```css
.footer {
  padding: var(--space-2xl) var(--space-lg) var(--space-xl);
  background: var(--surface-base);
  border-top: 1px solid var(--border-subtle);
}

.footer__inner {
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 2fr repeat(3, 1fr);
  gap: var(--space-2xl);
}

.footer__brand-desc {
  font-size: var(--font-size-sm);
  color: var(--text-secondary);
  line-height: var(--line-height-normal);
  max-width: 30ch;
  margin-top: var(--space-md);
}

.footer__heading {
  font-size: var(--font-size-sm);
  font-weight: 600;
  color: var(--text-primary);
  text-transform: uppercase;
  letter-spacing: 0.05em;
  margin-bottom: var(--space-md);
}

.footer__links {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: var(--space-sm);
}

.footer__link {
  font-size: var(--font-size-sm);
  color: var(--text-secondary);
  transition: color var(--transition-fast);
}

.footer__link:hover {
  color: var(--text-accent);
}

.footer__bottom {
  max-width: 1200px;
  margin: var(--space-xl) auto 0;
  padding-top: var(--space-lg);
  border-top: 1px solid var(--border-subtle);
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: var(--font-size-xs);
  color: var(--text-muted);
}

.footer__socials {
  display: flex;
  gap: var(--space-md);
}

.footer__social-icon {
  color: var(--text-muted);
  transition: color var(--transition-fast);
}

.footer__social-icon:hover {
  color: var(--text-accent);
}

@media (max-width: 767px) {
  .footer__inner {
    grid-template-columns: 1fr;
    gap: var(--space-xl);
  }
  .footer__bottom {
    flex-direction: column;
    gap: var(--space-md);
    text-align: center;
  }
}
```

## Primary Button

```css
.btn-primary {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: var(--space-sm);
  padding: var(--space-md) var(--space-xl);
  background: var(--accent-primary);
  color: var(--surface-base);
  border: none;
  border-radius: var(--radius-lg);
  font-family: var(--font-body);
  font-size: var(--font-size-base);
  font-weight: 600;
  cursor: pointer;
  transition: all var(--transition-fast);
  text-decoration: none;
  position: relative;
  overflow: hidden;
}

.btn-primary::before {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, transparent 40%, rgba(255,255,255,0.15) 50%, transparent 60%);
  transform: translateX(-100%);
  transition: transform 0.5s ease;
}

.btn-primary:hover {
  box-shadow: var(--shadow-glow);
  transform: translateY(-2px);
}

.btn-primary:hover::before {
  transform: translateX(100%);
}

.btn-primary:active {
  transform: translateY(0) scale(0.98);
}
```

## Secondary Button

```css
.btn-secondary {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: var(--space-sm);
  padding: var(--space-md) var(--space-xl);
  background: transparent;
  color: var(--text-primary);
  border: 1px solid var(--border-interactive);
  border-radius: var(--radius-lg);
  font-family: var(--font-body);
  font-size: var(--font-size-base);
  font-weight: 500;
  cursor: pointer;
  transition: all var(--transition-fast);
  text-decoration: none;
}

.btn-secondary:hover {
  background: var(--surface-interactive);
  border-color: var(--accent-primary);
  color: var(--text-accent);
}

.btn-secondary:active {
  transform: scale(0.98);
}
```

## Navigation Bar

```css
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  padding: var(--space-md) var(--space-lg);
  background: rgba(10, 10, 15, 0.8);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  border-bottom: 1px solid var(--border-subtle);
  transition: background var(--transition-base);
}

.navbar__inner {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.navbar__logo {
  font-family: var(--font-display);
  font-size: var(--font-size-md);
  font-weight: 700;
  color: var(--text-primary);
}

.navbar__links {
  display: flex;
  align-items: center;
  gap: var(--space-xl);
  list-style: none;
}

.navbar__link {
  font-size: var(--font-size-sm);
  color: var(--text-secondary);
  transition: color var(--transition-fast);
  font-weight: 500;
}

.navbar__link:hover { color: var(--text-primary); }
.navbar__link--active { color: var(--text-accent); }

/* Mobile hamburger */
.navbar__toggle {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
  border: none;
  cursor: pointer;
  padding: var(--space-xs);
}

.navbar__toggle span {
  display: block;
  width: 24px;
  height: 2px;
  background: var(--text-primary);
  transition: all var(--transition-fast);
}

@media (max-width: 767px) {
  .navbar__toggle { display: flex; }
  .navbar__links {
    display: none;
    position: absolute;
    top: 100%;
    left: 0;
    right: 0;
    flex-direction: column;
    background: var(--surface-raised);
    border-bottom: 1px solid var(--border-subtle);
    padding: var(--space-lg);
    gap: var(--space-md);
  }
  .navbar__links--open { display: flex; }
}
```
