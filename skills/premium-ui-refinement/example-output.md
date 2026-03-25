# Example Output: Premium UI Refinement — Pricing Page

## Refinement Summary

**Subject:** Pricing page for a B2B project management SaaS  
**Current State:** Functional but generic — looks like a template  
**Target State:** Premium, trustworthy, conversion-optimized

---

## Before / After Analysis

### 1. Typography Hierarchy — Before: Flat → After: Structured

**Before:**
- Page title: 32px bold
- Plan names: 24px bold
- Prices: 48px bold
- Feature list: 14px regular
- Everything in the same font weight creates visual monotony

**After — Recommended:**
```css
/* Page title */
.pricing-title {
  font-size: var(--typography-display-sm);    /* 30px */
  font-weight: 600;
  letter-spacing: -0.02em;                    /* Tighter tracking for display */
  color: var(--color-text-primary);
  line-height: 1.2;
}

/* Subtitle */
.pricing-subtitle {
  font-size: var(--typography-body-lg);       /* 18px */
  font-weight: 400;
  color: var(--color-text-secondary);
  line-height: 1.5;
  max-width: 560px;                           /* Readable line length */
}

/* Plan name */
.plan-name {
  font-size: var(--typography-heading-sm);    /* 18px */
  font-weight: 600;
  color: var(--color-text-primary);
  letter-spacing: -0.01em;
}

/* Price */
.plan-price {
  font-size: var(--typography-display-lg);    /* 48px */
  font-weight: 700;
  color: var(--color-text-primary);
  letter-spacing: -0.03em;                    /* Tight tracking for large numbers */
  line-height: 1;
}

/* Price period */
.plan-period {
  font-size: var(--typography-body-sm);       /* 14px */
  font-weight: 400;
  color: var(--color-text-tertiary);
}

/* Feature item */
.feature-item {
  font-size: var(--typography-body-md);       /* 14px */
  font-weight: 400;
  color: var(--color-text-secondary);
  line-height: 1.6;
}
```

**Why this matters:** Six distinct typographic levels create a clear scanning path: title → subtitle → plan names → prices → features. The eye moves naturally through the hierarchy without reading every word.

---

### 2. Spacing System — Before: Arbitrary → After: Rhythmic

**Before:**
- Card padding: 24px (all sides equal)
- Gap between cards: 20px
- Feature list item spacing: 12px
- No vertical rhythm — spacing feels random

**After — Recommended:**
```css
.pricing-cards {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: var(--space-lg);                       /* 24px between cards */
  max-width: 1080px;
  margin: 0 auto;
}

.pricing-card {
  padding: var(--space-xl) var(--space-lg);   /* 32px top/bottom, 24px sides */
  border-radius: var(--radius-xl);            /* 16px */
  border: 1px solid var(--color-border-default);
  background: var(--color-surface-default);
  transition: border-color 200ms ease, box-shadow 200ms ease;
}

.pricing-card:hover {
  border-color: var(--color-border-strong);
  box-shadow: var(--elevation-md);
}

.pricing-card--featured {
  border-color: var(--color-border-brand);
  box-shadow: var(--elevation-md);
  position: relative;
}

.plan-header {
  margin-bottom: var(--space-lg);             /* 24px */
}

.plan-price-section {
  margin-bottom: var(--space-lg);             /* 24px */
  padding-bottom: var(--space-lg);            /* 24px */
  border-bottom: 1px solid var(--color-border-subtle);
}

.feature-list {
  display: flex;
  flex-direction: column;
  gap: var(--space-sm);                       /* 12px between features */
  margin-bottom: var(--space-xl);             /* 32px before CTA */
}
```

**Why this matters:** Consistent spacing creates visual rhythm. The card has three clear zones (header, price, features) separated by consistent `space-lg` gaps. The feature list uses tighter `space-sm` for related items.

---

### 3. Visual Weight & Emphasis — Before: Everything Equal → After: Clear Focus

**Before:**
- All three plan cards identical in size, border, and background
- No visual indication of recommended plan
- CTA buttons all same style

**After — Recommended:**
```css
/* Featured plan badge */
.featured-badge {
  position: absolute;
  top: calc(-1 * var(--space-sm));
  left: 50%;
  transform: translateX(-50%);
  background: var(--color-surface-brand);
  color: var(--color-text-on-brand);
  font-size: var(--typography-label-sm);
  font-weight: 600;
  padding: var(--space-2xs) var(--space-md);
  border-radius: var(--radius-full);
  letter-spacing: 0.02em;
  text-transform: uppercase;
}

/* Primary CTA (featured plan) */
.cta-primary {
  width: 100%;
  padding: var(--space-sm) var(--space-lg);
  background: var(--color-action-primary);
  color: var(--color-text-on-action);
  border: none;
  border-radius: var(--radius-md);
  font-size: var(--typography-label-md);
  font-weight: 600;
  cursor: pointer;
  transition: background 150ms ease;
}

.cta-primary:hover {
  background: var(--color-action-primary-hover);
}

/* Secondary CTA (other plans) */
.cta-secondary {
  width: 100%;
  padding: var(--space-sm) var(--space-lg);
  background: transparent;
  color: var(--color-action-primary);
  border: 1px solid var(--color-border-strong);
  border-radius: var(--radius-md);
  font-size: var(--typography-label-md);
  font-weight: 600;
  cursor: pointer;
  transition: background 150ms ease, border-color 150ms ease;
}

.cta-secondary:hover {
  background: var(--color-surface-hover);
  border-color: var(--color-action-primary);
}
```

---

### 4. Micro-Details That Signal Premium

**Feature checkmarks:**
```css
.feature-item::before {
  content: "";
  display: inline-flex;
  width: 18px;
  height: 18px;
  background: var(--color-surface-success-subtle);
  border-radius: var(--radius-full);
  /* Checkmark icon via mask or SVG background */
  flex-shrink: 0;
  margin-right: var(--space-sm);
}

/* Unavailable features in lower plans */
.feature-item--unavailable {
  color: var(--color-text-disabled);
  text-decoration: line-through;
  text-decoration-color: var(--color-border-default);
}

.feature-item--unavailable::before {
  background: var(--color-surface-disabled);
  /* X icon instead of checkmark */
}
```

**Billing toggle (monthly/annual):**
```css
.billing-toggle {
  display: inline-flex;
  align-items: center;
  gap: var(--space-sm);
  background: var(--color-surface-secondary);
  padding: var(--space-2xs);
  border-radius: var(--radius-full);
}

.billing-option {
  padding: var(--space-xs) var(--space-md);
  border-radius: var(--radius-full);
  font-size: var(--typography-label-sm);
  font-weight: 500;
  color: var(--color-text-secondary);
  cursor: pointer;
  transition: all 150ms ease;
}

.billing-option--active {
  background: var(--color-surface-default);
  color: var(--color-text-primary);
  box-shadow: var(--elevation-xs);
}

.billing-savings {
  font-size: var(--typography-label-sm);
  color: var(--color-text-success);
  font-weight: 600;
}
```

---

### 5. Elevation & Depth

**Before:** All cards flat on the same plane, no depth differentiation.

**After:**
```css
/* Elevation scale for pricing context */
/* Default cards: no shadow, border only */
/* Featured card: subtle elevation to lift it */
/* Hover state: increased elevation for interactivity feedback */

.pricing-card {
  box-shadow: none;                           /* Flat by default */
}

.pricing-card:hover {
  box-shadow: var(--elevation-sm);            /* 0 1px 3px rgba(0,0,0,0.08) */
}

.pricing-card--featured {
  box-shadow: var(--elevation-md);            /* 0 4px 12px rgba(0,0,0,0.08) */
}

.pricing-card--featured:hover {
  box-shadow: var(--elevation-lg);            /* 0 8px 24px rgba(0,0,0,0.1) */
}
```

---

## Refinement Checklist

| Area | Before | After | Impact |
|------|--------|-------|--------|
| Typography levels | 2 | 6 | High — scanning efficiency |
| Spacing consistency | Arbitrary | Token-based rhythm | High — perceived quality |
| Featured plan emphasis | None | Badge + border + elevation | High — conversion |
| CTA differentiation | All identical | Primary vs secondary | Medium — clarity |
| Hover states | None | Border + elevation transitions | Medium — interactivity |
| Feature list styling | Plain text list | Checkmarks + unavailable states | Medium — scannability |
| Billing toggle | Text links | Pill toggle with savings badge | Low — polish |
| Letter-spacing | Default | Tightened for display sizes | Low — typographic refinement |

---

## What Makes This Premium

1. **Restraint over decoration.** No gradients, no glows, no decorative elements. Premium comes from precision in spacing, typography, and hierarchy.
2. **System-driven decisions.** Every value references a token. Nothing is hardcoded or arbitrary.
3. **Clear information hierarchy.** Users can compare plans in seconds because the visual hierarchy guides their eyes.
4. **Subtle interaction feedback.** Hover states use gentle transitions (150–200ms) that feel responsive without being flashy.
5. **Purposeful emphasis.** The featured plan stands out through structural means (badge, border, elevation) rather than color overload.
