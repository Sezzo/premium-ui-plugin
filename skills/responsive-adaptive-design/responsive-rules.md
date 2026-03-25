# Responsive Design Rules

## Breakpoint System

### Standard Breakpoints

| Token | Value | Viewport Class | Columns | Margins | Gutter |
|-------|-------|---------------|---------|---------|--------|
| `breakpoint.sm` | 640px | Mobile landscape | 4 | 16px | 16px |
| `breakpoint.md` | 768px | Tablet portrait | 8 | 24px | 24px |
| `breakpoint.lg` | 1024px | Tablet landscape / small desktop | 12 | 32px | 24px |
| `breakpoint.xl` | 1280px | Desktop | 12 | 40px | 32px |
| `breakpoint.2xl` | 1536px | Large desktop | 12 | auto (max-width container) | 32px |

### Breakpoint Selection Rules

- Choose breakpoints based on where content breaks, not device names
- Never add a breakpoint "just in case" — every breakpoint must solve a real layout problem
- Test content at every 50px increment between breakpoints to catch edge cases
- Container queries preferred for component-level adaptation; media queries for page-level layout

## Mobile-First Principles

### Mandatory

1. **Base styles target mobile** — all CSS starts at the smallest viewport
2. **Progressive enhancement** — add complexity as viewport grows, never subtract
3. **Content-first** — mobile forces content priority decisions that benefit all viewports
4. **Touch-first** — assume touch input as default, enhance for pointer devices

### Content Priority

- Define a content priority matrix for every screen
- Priority 1 content: visible on all viewports, no exceptions
- Priority 2 content: visible on tablet+, collapsed/accordion on mobile
- Priority 3 content: visible on desktop+, accessible via "Show more" on smaller viewports
- Never hide functionality — only restructure access patterns

## Layout Strategy

### Grid Behavior

| Viewport | Strategy | Notes |
|----------|----------|-------|
| < 640px | Single column, full-width | Stack everything vertically |
| 640–767px | Single column with wider content area | Slight breathing room |
| 768–1023px | 2-column where appropriate | Sidebar collapses to top/bottom |
| 1024–1279px | Full grid, sidebar visible | Standard desktop layout |
| 1280px+ | Full grid, max-width container | Prevent ultra-wide line lengths |

### Component Adaptation Patterns

| Pattern | Description | Example |
|---------|-------------|---------|
| **Stack** | Horizontal → vertical | Card row → card stack |
| **Collapse** | Visible → accordion/expandable | Sidebar → hamburger menu |
| **Reflow** | Grid rearrangement | 3-col → 2-col → 1-col |
| **Truncate** | Full → abbreviated | Full label → icon-only |
| **Promote** | Secondary → primary position | Mobile: key actions move to thumb zone |
| **Defer** | Eager → lazy | Desktop: show all; Mobile: load on demand |

## Typography Scaling

### Scale Adjustments

| Token | Mobile | Tablet | Desktop |
|-------|--------|--------|---------|
| `typography.display.lg` | 28px | 32px | 36px |
| `typography.display.md` | 24px | 28px | 30px |
| `typography.heading.lg` | 20px | 22px | 24px |
| `typography.heading.md` | 18px | 18px | 20px |
| `typography.heading.sm` | 16px | 16px | 18px |
| `typography.body.lg` | 16px | 16px | 16px |
| `typography.body.md` | 14px | 14px | 14px |
| `typography.body.sm` | 12px | 12px | 12px |

### Rules

- Body text does not scale — 14px/16px is readable at all viewports
- Only display and heading tokens scale down on mobile
- Line length: 45–75 characters optimal; enforce `max-width` on text containers
- Never use viewport units (vw) for font size — breaks zoom accessibility

## Spacing Scaling

| Token | Mobile | Tablet+ |
|-------|--------|---------|
| `space.xs` | 4px | 4px |
| `space.sm` | 8px | 8px |
| `space.md` | 12px | 16px |
| `space.lg` | 16px | 24px |
| `space.xl` | 24px | 32px |
| `space.2xl` | 32px | 48px |
| `space.3xl` | 48px | 64px |

## Touch Target Rules

### Minimum Sizes

- **All interactive elements**: 44×44px minimum touch target (WCAG 2.5.8)
- **Inline links in text**: Exempt from size requirement but must have sufficient line-height
- **Icon buttons**: Visual size can be smaller if touch target (padding) meets 44px
- **Spacing between targets**: Minimum 8px gap to prevent mis-taps

### Thumb Zone Optimization

- Primary actions in bottom 1/3 of mobile viewport (thumb-reachable)
- Destructive actions away from thumb zone (prevent accidental taps)
- Navigation: bottom tab bar preferred over top hamburger on mobile

## Navigation Patterns

| Viewport | Pattern | Notes |
|----------|---------|-------|
| Mobile (< 768px) | Bottom tab bar (≤5 items) or hamburger | Primary actions always visible |
| Tablet (768–1023px) | Collapsible sidebar or top nav | Context-dependent |
| Desktop (1024px+) | Persistent sidebar or top nav | Full navigation visible |

### Rules

- Bottom navigation: max 5 items, icon + label, active state clearly marked
- Hamburger menu: only when navigation items exceed 5 and viewport is constrained
- Never hide primary navigation behind a hamburger on desktop
- Breadcrumbs: show on desktop, truncate to "< Back" on mobile

## Image & Media

### Responsive Images

- Use `srcset` with width descriptors for all content images
- Provide at minimum: 1x, 2x, and 3x density variants
- Art direction: use `<picture>` element for different crops per viewport
- Lazy load all images below the fold (`loading="lazy"`)
- Always set explicit `width` and `height` attributes to prevent layout shift

### Video & Embeds

- Use `aspect-ratio` CSS property for responsive containers
- Autoplay only on desktop, and only if muted
- Provide poster images for all video elements

## Layout Shift Prevention

### Critical Rules

1. **Reserve space** for all dynamic content (images, ads, embeds)
2. **Set dimensions** on all media elements before load
3. **Avoid inserting content above existing content** after initial render
4. **Font loading**: Use `font-display: swap` with size-adjusted fallback fonts
5. **Skeleton screens** for async content — match exact dimensions of final content
6. **Target CLS score**: < 0.1 (Good)

## Testing Checklist

- [ ] All layouts tested at: 320px, 375px, 414px, 768px, 1024px, 1280px, 1440px, 1920px
- [ ] No horizontal scrolling at any viewport width ≥ 320px
- [ ] All touch targets meet 44×44px minimum on touch devices
- [ ] Typography remains readable (no text smaller than 12px)
- [ ] No content is inaccessible on any viewport (hidden without alternative access)
- [ ] Images load appropriate size per viewport (no desktop images on mobile)
- [ ] Navigation is usable and discoverable on all viewport classes
- [ ] Forms are fully usable on mobile (proper input types, no tiny fields)
- [ ] CLS score < 0.1 on all viewport sizes
- [ ] Zoom to 200% does not break layout or hide content
