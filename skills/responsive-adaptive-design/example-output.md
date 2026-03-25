# Example Output: Responsive Adaptive Design — E-Commerce Product Listing

## Design Summary

**Screen:** Product listing page (category view) for a fashion e-commerce platform  
**Breakpoints:** Mobile (320–767px), Tablet (768–1023px), Desktop (1024–1439px), Wide (≥1440px)  
**Approach:** Mobile-first with progressive enhancement

---

## Breakpoint Strategy

### Layout Grid

| Breakpoint | Columns | Gutter | Margin | Max Width |
|-----------|---------|--------|--------|-----------|
| Mobile (320–767px) | 4 | 16px | 16px | 100% |
| Tablet (768–1023px) | 8 | 24px | 32px | 100% |
| Desktop (1024–1439px) | 12 | 24px | 48px | 100% |
| Wide (≥1440px) | 12 | 32px | auto | 1360px |

### Product Grid

| Breakpoint | Products/Row | Card Style | Image Ratio |
|-----------|-------------|-----------|-------------|
| Mobile | 2 | Compact — image + name + price | 3:4 |
| Tablet | 3 | Standard — image + name + price + color swatches | 3:4 |
| Desktop | 4 | Full — image + name + price + color swatches + quick-add | 3:4 |
| Wide | 4 (larger cards) | Full with hover zoom | 3:4 |

---

## CSS Implementation

### Base Layout (Mobile-First)

```css
/* Product grid — mobile first */
.product-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: var(--space-sm);
  padding: 0 var(--space-md);
}

/* Product card — mobile */
.product-card {
  display: flex;
  flex-direction: column;
  gap: var(--space-xs);
}

.product-image {
  aspect-ratio: 3 / 4;
  width: 100%;
  object-fit: cover;
  border-radius: var(--radius-md);
  background: var(--color-surface-secondary);
}

.product-name {
  font-size: var(--typography-body-sm);
  font-weight: 500;
  color: var(--color-text-primary);
  line-height: 1.3;
  /* Truncate to 2 lines on mobile */
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

.product-price {
  font-size: var(--typography-body-sm);
  font-weight: 600;
  color: var(--color-text-primary);
}

/* Hidden on mobile */
.product-swatches,
.product-quick-add {
  display: none;
}
```

### Tablet Enhancement

```css
@media (min-width: 768px) {
  .product-grid {
    grid-template-columns: repeat(3, 1fr);
    gap: var(--space-md);
    padding: 0 var(--space-lg);
  }

  .product-name {
    font-size: var(--typography-body-md);
  }

  .product-price {
    font-size: var(--typography-body-md);
  }

  /* Show color swatches on tablet */
  .product-swatches {
    display: flex;
    gap: var(--space-2xs);
  }

  .product-swatch {
    width: 16px;
    height: 16px;
    border-radius: var(--radius-full);
    border: 1px solid var(--color-border-default);
  }
}
```

### Desktop Enhancement

```css
@media (min-width: 1024px) {
  .product-grid {
    grid-template-columns: repeat(4, 1fr);
    gap: var(--space-lg);
    padding: 0 var(--space-xl);
    max-width: 1360px;
    margin: 0 auto;
  }

  /* Show quick-add on hover */
  .product-quick-add {
    display: block;
    opacity: 0;
    transform: translateY(8px);
    transition: opacity 200ms ease, transform 200ms ease;
    position: absolute;
    bottom: var(--space-sm);
    left: var(--space-sm);
    right: var(--space-sm);
  }

  .product-card:hover .product-quick-add {
    opacity: 1;
    transform: translateY(0);
  }

  /* Image hover zoom */
  .product-image-wrapper {
    overflow: hidden;
    border-radius: var(--radius-md);
  }

  .product-card:hover .product-image {
    transform: scale(1.03);
    transition: transform 400ms ease;
  }

  .product-swatch {
    width: 20px;
    height: 20px;
  }
}
```

### Container Query for Product Card

```css
/* Container query — card adapts to its container, not viewport */
.product-card {
  container-type: inline-size;
  container-name: product-card;
}

@container product-card (min-width: 200px) {
  .product-name {
    -webkit-line-clamp: 2;
  }
}

@container product-card (min-width: 280px) {
  .product-name {
    -webkit-line-clamp: unset;
  }
  
  .product-meta {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
}
```

---

## Filter Sidebar — Responsive Pattern

### Desktop: Persistent Sidebar
```
┌──────────┬──────────────────────────────────┐
│ Filters  │  Product Grid                    │
│          │  ┌────┐ ┌────┐ ┌────┐ ┌────┐    │
│ Category │  │    │ │    │ │    │ │    │    │
│ Price    │  └────┘ └────┘ └────┘ └────┘    │
│ Size     │  ┌────┐ ┌────┐ ┌────┐ ┌────┐    │
│ Color    │  │    │ │    │ │    │ │    │    │
│ Brand    │  └────┘ └────┘ └────┘ └────┘    │
└──────────┴──────────────────────────────────┘
```

### Tablet: Collapsible Sidebar
```
┌─────────────────────────────────────────────┐
│ [Filter ▾]  Showing 48 results  [Sort ▾]    │
├─────────────────────────────────────────────┤
│  ┌────┐ ┌────┐ ┌────┐                      │
│  │    │ │    │ │    │                      │
│  └────┘ └────┘ └────┘                      │
└─────────────────────────────────────────────┘
```

### Mobile: Bottom Sheet Filter
```
┌──────────────────────────┐
│ [Filter (3)]  [Sort ▾]   │
├──────────────────────────┤
│  ┌─────┐ ┌─────┐        │
│  │     │ │     │        │
│  └─────┘ └─────┘        │
└──────────────────────────┘

  ↓ Tap "Filter" opens bottom sheet:

┌──────────────────────────┐
│ ═══ Filters         [✕]  │
│                          │
│ Category                 │
│ ☐ Dresses  ☐ Tops       │
│ ☐ Pants    ☐ Shoes      │
│                          │
│ Price                    │
│ [───●────────] $0–$200   │
│                          │
│ [Show 48 Results]        │
└──────────────────────────┘
```

```css
/* Filter responsive behavior */
.filter-sidebar {
  display: none; /* Hidden on mobile */
}

@media (min-width: 1024px) {
  .filter-sidebar {
    display: block;
    width: 260px;
    flex-shrink: 0;
    position: sticky;
    top: var(--space-lg);
    max-height: calc(100vh - var(--header-height) - var(--space-xl));
    overflow-y: auto;
  }

  .product-listing {
    display: flex;
    gap: var(--space-xl);
  }
}

/* Mobile: bottom sheet trigger */
.filter-trigger {
  display: flex;
  align-items: center;
  gap: var(--space-xs);
}

.filter-trigger-count {
  background: var(--color-action-primary);
  color: var(--color-text-on-action);
  font-size: var(--typography-label-xs);
  padding: 2px 6px;
  border-radius: var(--radius-full);
}

@media (min-width: 1024px) {
  .filter-trigger {
    display: none;
  }
}
```

---

## Navigation — Responsive Pattern

| Breakpoint | Navigation Style |
|-----------|-----------------|
| Mobile | Hamburger menu → slide-in drawer from left |
| Tablet | Horizontal nav with overflow scroll, active indicator |
| Desktop | Full horizontal nav with dropdowns on hover |

```css
/* Mobile: hamburger + drawer */
.nav-desktop { display: none; }
.nav-hamburger { display: flex; }

@media (min-width: 768px) {
  .nav-desktop {
    display: flex;
    overflow-x: auto;
    scrollbar-width: none;
    gap: var(--space-md);
  }
  .nav-hamburger { display: none; }
}

@media (min-width: 1024px) {
  .nav-desktop {
    overflow-x: visible; /* Allow dropdowns */
    gap: var(--space-lg);
  }
}
```

---

## Touch Target Compliance

| Element | Desktop Size | Mobile Size | Minimum |
|---------|-------------|-------------|---------|
| Product card tap area | Full card | Full card | ✅ |
| Filter checkbox | 20×20px | 44×44px (padded) | ✅ 44px min |
| Swatch selector | 20×20px | 36×36px | ⚠️ Below 44px — add padding |
| Pagination button | 32×32px | 44×44px | ✅ |
| Sort dropdown | 36px height | 44px height | ✅ |

```css
/* Ensure touch targets on mobile */
@media (pointer: coarse) {
  .product-swatch {
    width: 36px;
    height: 36px;
    /* Visual size stays 20px, touch target is 36px via padding */
    padding: 8px;
    background-clip: content-box;
  }

  .filter-checkbox-label {
    min-height: 44px;
    display: flex;
    align-items: center;
    padding: var(--space-xs) 0;
  }
}
```

---

## Performance Considerations

### Image Loading
```html
<!-- Responsive images with art direction -->
<picture>
  <source media="(min-width: 1024px)" srcset="product-lg.webp" />
  <source media="(min-width: 768px)" srcset="product-md.webp" />
  <img src="product-sm.webp" alt="Product name" loading="lazy" />
</picture>
```

### Critical CSS
- Inline above-the-fold CSS for the first 4 product cards (mobile) or 8 cards (desktop)
- Defer filter sidebar CSS on mobile (not visible initially)
- Use `content-visibility: auto` on product cards below the fold

---

## Accessibility Across Breakpoints

- **Mobile drawer navigation:** Must trap focus when open, close on `Escape`, return focus to hamburger button
- **Bottom sheet filter:** Must trap focus, announce "Filter panel opened" to screen readers
- **Touch targets:** All interactive elements ≥44×44px on touch devices
- **Reduced motion:** Disable hover zoom and quick-add animations when `prefers-reduced-motion: reduce`

```css
@media (prefers-reduced-motion: reduce) {
  .product-card:hover .product-image {
    transform: none;
  }

  .product-quick-add {
    transition: none;
    opacity: 1;
    transform: none;
  }
}
```
