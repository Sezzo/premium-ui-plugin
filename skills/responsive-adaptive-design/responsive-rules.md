# Responsive & Adaptive Design Rules

This document defines the rules, techniques, and patterns for building responsive interfaces that maintain premium quality across all viewport sizes.

## Core Principle
Responsive design is not about making things fit — it is about maintaining hierarchy, usability, and quality at every viewport size. A premium product must feel intentionally designed for each breakpoint, not squeezed into it.

## Breakpoint System

### Standard Breakpoints
```css
/* Mobile-first breakpoints */
--breakpoint-sm: 640px;    /* Large phones, small tablets */
--breakpoint-md: 768px;    /* Tablets */
--breakpoint-lg: 1024px;   /* Small desktops, landscape tablets */
--breakpoint-xl: 1280px;   /* Standard desktops */
--breakpoint-2xl: 1440px;  /* Wide desktops */
```

### Breakpoint Usage Rules
- **Mobile-first:** Write base styles for mobile, enhance with `min-width` media queries
- **Content-driven:** Breakpoints should align with where the content breaks, not arbitrary device widths
- **Minimum 3 layouts:** Mobile, tablet, desktop. Wide desktop is optional but recommended.
- **No breakpoint gaps:** Every pixel between 320px and 1920px must be accounted for

## Layout Grid

```css
:root {
  --grid-columns-mobile: 4;
  --grid-columns-tablet: 8;
  --grid-columns-desktop: 12;
  
  --grid-gutter-mobile: 16px;
  --grid-gutter-tablet: 24px;
  --grid-gutter-desktop: 24px;
  --grid-gutter-wide: 32px;
  
  --grid-margin-mobile: 16px;
  --grid-margin-tablet: 32px;
  --grid-margin-desktop: 48px;
  --grid-margin-wide: auto;    /* Centered with max-width */
  
  --grid-max-width: 1360px;
}
```

## Container Queries

Container queries allow components to adapt to their container size rather than the viewport. Use them for components that appear in different layout contexts.

```css
/* Define a container */
.card-grid {
  container-type: inline-size;
  container-name: card-grid;
}

/* Component adapts to container, not viewport */
@container card-grid (min-width: 600px) {
  .card {
    flex-direction: row;  /* Side-by-side layout when container is wide */
  }
}

@container card-grid (max-width: 599px) {
  .card {
    flex-direction: column;  /* Stacked layout when container is narrow */
  }
}
```

### When to Use Container Queries vs Media Queries
| Use Case | Approach |
|----------|---------|
| Page-level layout changes | Media queries (`@media`) |
| Component in sidebar vs main content | Container queries (`@container`) |
| Navigation responsive behavior | Media queries |
| Card layout within a grid | Container queries |
| Typography scale changes | Media queries |
| Component internal layout | Container queries |

## Modern CSS Techniques

### Fluid Typography
```css
/* Fluid font size: 16px at 320px viewport → 20px at 1440px viewport */
.body-text {
  font-size: clamp(1rem, 0.929rem + 0.357vw, 1.25rem);
}

/* Fluid heading: 24px → 36px */
.heading {
  font-size: clamp(1.5rem, 1.143rem + 1.786vw, 2.25rem);
}
```

### Fluid Spacing
```css
/* Fluid section spacing: 32px → 64px */
.section {
  padding-block: clamp(2rem, 1.143rem + 4.286vw, 4rem);
}

/* Fluid container margin */
.container {
  padding-inline: clamp(1rem, 0.429rem + 2.857vw, 3rem);
}
```

### Intrinsic Sizing with Grid
```css
/* Auto-fit grid: cards fill available space, minimum 280px each */
.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: var(--space-lg);
}

/* Sidebar layout: sidebar fixed, content fills remaining space */
.layout-with-sidebar {
  display: grid;
  grid-template-columns: 260px 1fr;
  gap: var(--space-xl);
}

@media (max-width: 1023px) {
  .layout-with-sidebar {
    grid-template-columns: 1fr;  /* Stack on tablet/mobile */
  }
}
```

### Logical Properties
```css
/* Use logical properties for internationalization support */
.card {
  padding-block: var(--space-lg);      /* top/bottom */
  padding-inline: var(--space-md);     /* left/right (flips in RTL) */
  margin-block-end: var(--space-lg);   /* margin-bottom (logical) */
}
```

## Responsive Patterns for Common Components

### Tables
Tables are the most challenging responsive component. Three strategies:

**Strategy 1: Column Hiding (recommended for data tables)**
```css
/* Hide low-priority columns progressively */
.col-priority-3 { display: none; }  /* Hidden on mobile */

@media (min-width: 768px) {
  .col-priority-3 { display: table-cell; }  /* Show on tablet */
}

/* Always visible: name, primary data, actions */
/* Hidden on mobile: email, date, secondary data */
/* Hidden on tablet: metadata, tertiary data */
```

**Strategy 2: Card Transformation (recommended for list views)**
```css
@media (max-width: 767px) {
  .data-table { display: block; }
  .data-table thead { display: none; }
  .data-table tr {
    display: block;
    padding: var(--space-md);
    border: 1px solid var(--color-border-default);
    border-radius: var(--radius-md);
    margin-bottom: var(--space-sm);
  }
  .data-table td {
    display: flex;
    justify-content: space-between;
    padding: var(--space-xs) 0;
  }
  .data-table td::before {
    content: attr(data-label);
    font-weight: 600;
    color: var(--color-text-secondary);
  }
}
```

**Strategy 3: Horizontal Scroll (use sparingly)**
```css
.table-wrapper {
  overflow-x: auto;
  -webkit-overflow-scrolling: touch;
}

/* Scroll indicator shadow */
.table-wrapper {
  background:
    linear-gradient(to right, white 30%, transparent),
    linear-gradient(to left, white 30%, transparent),
    linear-gradient(to right, rgba(0,0,0,0.1), transparent),
    linear-gradient(to left, rgba(0,0,0,0.1), transparent);
  background-position: left, right, left, right;
  background-size: 40px 100%, 40px 100%, 20px 100%, 20px 100%;
  background-repeat: no-repeat;
  background-attachment: local, local, scroll, scroll;
}
```

### Navigation
```css
/* Desktop: horizontal nav */
.nav { display: flex; gap: var(--space-lg); }
.nav-drawer { display: none; }
.nav-hamburger { display: none; }

/* Mobile: hamburger + drawer */
@media (max-width: 767px) {
  .nav { display: none; }
  .nav-hamburger { display: flex; }
  
  .nav-drawer {
    position: fixed;
    inset: 0;
    background: var(--color-surface-default);
    transform: translateX(-100%);
    transition: transform var(--transition-normal);
    z-index: 100;
  }
  
  .nav-drawer--open {
    transform: translateX(0);
  }
}

/* Tablet: scrollable horizontal nav */
@media (min-width: 768px) and (max-width: 1023px) {
  .nav {
    overflow-x: auto;
    scrollbar-width: none;
    -ms-overflow-style: none;
  }
  .nav::-webkit-scrollbar { display: none; }
}
```

### Forms
```css
/* Desktop: 2-column form */
.form-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: var(--space-md) var(--space-lg);
  max-width: 720px;
}

/* Full-width fields span both columns */
.form-field--full {
  grid-column: 1 / -1;
}

/* Mobile: single column */
@media (max-width: 767px) {
  .form-grid {
    grid-template-columns: 1fr;
  }
}
```

### Modals
```css
/* Desktop: centered modal */
.modal {
  position: fixed;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: var(--space-xl);
}

.modal-content {
  width: 100%;
  max-width: 560px;
  max-height: 80vh;
  border-radius: var(--radius-xl);
  overflow-y: auto;
}

/* Mobile: full-screen modal */
@media (max-width: 767px) {
  .modal {
    padding: 0;
  }
  
  .modal-content {
    max-width: 100%;
    max-height: 100%;
    height: 100%;
    border-radius: 0;
  }
}
```

### Filter Sidebar
```css
/* Desktop: persistent sidebar */
.filter-sidebar {
  width: 260px;
  flex-shrink: 0;
  position: sticky;
  top: var(--space-lg);
}

/* Mobile: bottom sheet */
@media (max-width: 1023px) {
  .filter-sidebar {
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
    max-height: 80vh;
    border-radius: var(--radius-xl) var(--radius-xl) 0 0;
    transform: translateY(100%);
    transition: transform var(--transition-normal);
    z-index: 100;
    background: var(--color-surface-default);
    box-shadow: var(--elevation-lg);
  }
  
  .filter-sidebar--open {
    transform: translateY(0);
  }
}
```

## Touch Target Rules

```css
/* Minimum touch target: 44×44px (WCAG 2.5.8) */
@media (pointer: coarse) {
  .interactive-element {
    min-height: 44px;
    min-width: 44px;
  }
  
  /* Increase spacing between touch targets */
  .button + .button {
    margin-left: var(--space-sm);  /* Prevent accidental taps */
  }
  
  /* Larger checkbox/radio targets */
  .form-check-label {
    min-height: 44px;
    display: flex;
    align-items: center;
    padding: var(--space-xs) 0;
  }
}
```

## Performance Considerations

### Image Optimization
```html
<!-- Responsive images with srcset -->
<img
  src="image-400.webp"
  srcset="image-400.webp 400w, image-800.webp 800w, image-1200.webp 1200w"
  sizes="(max-width: 767px) 100vw, (max-width: 1023px) 50vw, 33vw"
  alt="Description"
  loading="lazy"
/>
```

### CSS Containment
```css
/* Improve rendering performance for off-screen content */
.card {
  content-visibility: auto;
  contain-intrinsic-size: 0 300px;  /* Estimated height */
}
```

### Reduced Motion
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

## Responsive Testing Checklist
- [ ] Test at 320px (smallest supported mobile)
- [ ] Test at 375px (common mobile)
- [ ] Test at 768px (tablet portrait)
- [ ] Test at 1024px (tablet landscape / small desktop)
- [ ] Test at 1280px (standard desktop)
- [ ] Test at 1440px (wide desktop)
- [ ] Test at 1920px (full HD)
- [ ] Test with zoom at 200% (accessibility requirement)
- [ ] Test with `prefers-reduced-motion: reduce`
- [ ] Test with `pointer: coarse` (touch devices)
- [ ] Test landscape orientation on mobile
- [ ] Verify no horizontal scroll at any breakpoint
