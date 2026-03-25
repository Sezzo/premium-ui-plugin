# Screen Composition Rules

This document defines the rules and principles that govern screen-level layout decisions. Every screen composition must follow these rules.

## A Premium Screen Must Define
- A clear primary purpose (one sentence)
- A visible hierarchy of attention (what the user sees first, second, third)
- Disciplined grouping (related content together, unrelated content separated)
- Controlled density (intentional choice of compact, default, or comfortable)
- Clear action priority (one primary action per screen)
- Visual rhythm (consistent spacing between zones)
- Structural calm (no competing focal points)

## Zone Hierarchy Rules

### Visual Weight Distribution
Every screen should follow a clear weight pattern:

```
HIGH    → Page title + Primary action (user knows where they are and what they can do)
  ↓
MEDIUM  → Summary/context (user understands the current state)
  ↓
LOW     → Controls/filters (utility — available but not dominant)
  ↓
HIGH    → Primary content (the reason the user is on this screen)
  ↓
LOW     → Pagination/footer (utility)
```

### Zone Spacing Rules
```css
/* Between major zones */
.zone + .zone {
  margin-top: var(--space-xl);     /* 32px */
}

/* Between sections within a zone */
.section + .section {
  margin-top: var(--space-lg);     /* 24px */
}

/* Between components within a section */
.component + .component {
  margin-top: var(--space-md);     /* 16px */
}

/* Between elements within a component */
.element + .element {
  margin-top: var(--space-sm);     /* 12px */
}
```

**Rule:** Each nesting level uses a smaller spacing step. Zone > Section > Component > Element. No exceptions.

## Layout Grid Rules

### Container Widths
```css
/* Content containers */
--container-sm: 640px;    /* Forms, narrow content */
--container-md: 960px;    /* Standard content */
--container-lg: 1200px;   /* Wide content with sidebar */
--container-xl: 1360px;   /* Full-width dashboards */
```

### Column Rules
| Content Type | Max Columns | Rationale |
|-------------|-------------|-----------|
| Forms | 2 | Readability — users scan top-to-bottom |
| Card grids | 4 | Scannability — more than 4 per row loses focus |
| Data tables | Full width | Tables need horizontal space for columns |
| Detail + sidebar | 2 (60/40 or 70/30) | Primary content dominates, sidebar supports |
| Dashboard charts | 2 | Side-by-side comparison, stacked on mobile |

## Responsive Layout Zones

### Mobile (<768px)
- **All zones stack vertically** — no side-by-side layouts
- Sidebar content moves above or below primary content
- Filter zone collapses into a trigger button + bottom sheet
- Summary metrics: max 2 per row
- Action buttons: full width, stacked if multiple
- No sticky elements (preserves vertical space)

### Tablet (768–1023px)
- **Two-column layouts allowed** but simplified
- Sidebar can be collapsible (toggle to show/hide)
- Summary metrics: 2×2 grid
- Filter zone: inline but may truncate with "More filters" overflow
- Tables: hide low-priority columns, show column toggle

### Desktop (1024–1439px)
- **Full layout** with sidebar, multi-column grids, persistent filters
- Sticky sidebar and sticky table headers
- All summary metrics visible in a single row (max 4)

### Wide (≥1440px)
- **Max-width container** — content does not stretch infinitely
- Center the container with `margin: 0 auto`
- Increased gutters for breathing room
- Consider using the extra space for a persistent sidebar or wider content area

## Density Control Rules

### When to Use Each Density

| Density | Characteristics | Use When |
|---------|----------------|----------|
| **Compact** | 32–36px rows, `space-xs`–`space-sm` gaps, smaller text | Power users, admin panels, data-heavy views where information density matters |
| **Default** | 40–48px rows, `space-sm`–`space-md` gaps, standard text | Most application screens — the safe default |
| **Comfortable** | 48–56px rows, `space-md`–`space-lg` gaps, larger touch targets | Customer-facing pages, onboarding, mobile-first views |

### Density Rules
1. **One density per screen.** Never mix compact headers with comfortable content.
2. **Document the choice.** Every screen should state its density level and why.
3. **Density affects all elements.** Row heights, padding, font sizes, and spacing must all align with the chosen density.
4. **Mobile defaults to comfortable.** Touch targets require at least 44px, which naturally pushes toward comfortable density.

## Empty State Rules

Every screen that can be empty must define an empty state:

1. **Purposeful visual** — icon or illustration that relates to the content type (not decorative)
2. **Clear headline** — "No [items] yet" or "No results match your filters"
3. **Helpful description** — one sentence explaining what will appear here or what to do
4. **Primary CTA** — the action that creates the first item
5. **No clutter** — hide filters, pagination, and other controls that serve no purpose when empty

### Empty State Variants
| Variant | When | Content |
|---------|------|---------|
| First-time empty | User has never created content | Encouraging headline + CTA to create first item |
| Filtered empty | Filters exclude all results | "No results match your filters" + Clear Filters button |
| Error empty | Data failed to load | Error message + Retry button |
| Permission empty | User lacks access | Explanation + Request Access or contact info |

## Composition Quality Questions

For every screen, verify:
- [ ] What is the user supposed to understand first? (Is it visually dominant?)
- [ ] What is the primary action? (Is it immediately findable?)
- [ ] What can be removed without losing meaning? (Is anything decorative?)
- [ ] Does the screen feel calm or fragmented? (Count competing focal points — max 2)
- [ ] Does the spacing create rhythm or noise? (Are zone gaps consistent?)
- [ ] Does the layout support trust and maturity? (No gimmicks, no clutter)
- [ ] Does the screen work at all 4 breakpoints? (Mobile, tablet, desktop, wide)
- [ ] Is the density intentional and consistent? (One density per screen)
- [ ] Is there an empty state? (What does the user see with no data?)

## Avoid
- Too many competing focal points (more than 2 HIGH-weight zones)
- Decorative hero sections without function
- Floating visual gimmicks or ornamental elements
- Emoji-based signifiers or AI-themed illustration clichés
- Decorative cards used only to fill space
- Dashboards overloaded with panels, metrics, and filters
- Sectioning that depends on borders rather than hierarchy and spacing
- Forms wider than 720px
- Layouts that only work at one viewport size
- Mixing density levels on the same screen
