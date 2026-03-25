# Example Output: UI Component Design — Data Table

## Component Overview

**Component:** DataTable  
**Context:** B2B analytics platform — used for displaying user activity logs, financial transactions, and report data  
**Design System:** Existing token system with `color.*`, `space.*`, `typography.*`, `radius.*` tokens

---

## Component Anatomy

```
┌─────────────────────────────────────────────────────────┐
│ ┌─ Toolbar ──────────────────────────────────────────┐  │
│ │ [Search]              [Filter] [Columns] [Export]  │  │
│ └────────────────────────────────────────────────────┘  │
│ ┌─ Header Row ───────────────────────────────────────┐  │
│ │ ☐  Name ▲    Email         Role      Last Active   │  │
│ ├────────────────────────────────────────────────────┤  │
│ │ ☐  Jane D.   jane@...     Admin     2 min ago      │  │
│ │ ☐  John S.   john@...     Editor    1 hour ago     │  │
│ │ ☐  Maria L.  maria@...    Viewer    3 days ago     │  │
│ │    ...                                              │  │
│ ├─ Empty State ──────────────────────────────────────┤  │
│ │         No results match your filters.              │  │
│ │         [Clear Filters]                             │  │
│ ├─ Loading State ────────────────────────────────────┤  │
│ │    ░░░░░░░░   ░░░░░░░░   ░░░░░░   ░░░░░░░░░░     │  │
│ │    ░░░░░░░░   ░░░░░░░░   ░░░░░░   ░░░░░░░░░░     │  │
│ ├────────────────────────────────────────────────────┤  │
│ │ Showing 1–25 of 1,248    [◀] 1 2 3 ... 50 [▶]     │  │
│ └────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────┘
```

---

## Variants

### Size Variants

| Variant | Row Height | Font Size | Padding | Use Case |
|---------|-----------|-----------|---------|----------|
| `compact` | 36px | `typography.body.sm` (12px) | `space.xs` (8px) | Dense data views, admin panels |
| `default` | 48px | `typography.body.md` (14px) | `space.sm` (12px) | Standard data tables |
| `comfortable` | 56px | `typography.body.md` (14px) | `space.md` (16px) | Customer-facing, fewer rows |

### Feature Variants

| Variant | Description |
|---------|-------------|
| `basic` | Header + rows + pagination. No selection, no toolbar. |
| `selectable` | Adds checkbox column for row selection with bulk actions. |
| `sortable` | Adds sort indicators to column headers. |
| `full` | All features: selection, sorting, filtering, search, column management, export. |

---

## States

### Row States

| State | Background | Border | Text Color | Trigger |
|-------|-----------|--------|------------|---------|
| Default | `color.surface.default` | — | `color.text.primary` | — |
| Hover | `color.surface.hover` | — | `color.text.primary` | Mouse enter |
| Selected | `color.surface.selected` | — | `color.text.primary` | Checkbox checked |
| Selected + Hover | `color.surface.selected.hover` | — | `color.text.primary` | Hover on selected row |
| Active/Pressed | `color.surface.pressed` | — | `color.text.primary` | Mouse down |
| Disabled | `color.surface.disabled` | — | `color.text.disabled` | Row data condition |
| Focused (keyboard) | `color.surface.default` | `2px solid color.border.focus` | `color.text.primary` | Keyboard navigation |

### Column Header States

| State | Indicator | Cursor |
|-------|-----------|--------|
| Default | — | `default` |
| Sortable (unsorted) | Subtle up/down arrows in `color.icon.tertiary` | `pointer` |
| Sorted ascending | Up arrow in `color.icon.primary` | `pointer` |
| Sorted descending | Down arrow in `color.icon.primary` | `pointer` |
| Hover | Background `color.surface.hover` | `pointer` |
| Resizing | Drag handle visible, column border highlighted | `col-resize` |

### Table-Level States

| State | Behavior |
|-------|----------|
| Loading (initial) | Show skeleton rows (5 rows matching `compact`/`default`/`comfortable` height) |
| Loading (pagination) | Keep current rows visible, show subtle loading bar at top |
| Loading (sort/filter) | Fade current rows to 50% opacity, show loading bar |
| Empty | Centered illustration + message + action button |
| Error | Centered error message + retry button |
| No search results | "No results match your search" + clear search action |

---

## Token Mapping

```css
/* Surface */
--table-bg: var(--color-surface-default);
--table-header-bg: var(--color-surface-secondary);
--table-row-hover: var(--color-surface-hover);
--table-row-selected: var(--color-surface-selected);
--table-row-stripe: var(--color-surface-tertiary);

/* Borders */
--table-border: var(--color-border-default);
--table-border-header: var(--color-border-strong);

/* Typography */
--table-header-font: var(--typography-label-sm);
--table-header-color: var(--color-text-secondary);
--table-header-weight: 600;
--table-cell-font: var(--typography-body-md);
--table-cell-color: var(--color-text-primary);

/* Spacing */
--table-cell-padding-x: var(--space-sm);
--table-cell-padding-y: var(--space-xs);
--table-toolbar-gap: var(--space-sm);
--table-toolbar-padding: var(--space-md);

/* Radius */
--table-radius: var(--radius-lg);

/* Elevation */
--table-shadow: var(--elevation-sm);
```

---

## Interaction Specifications

### Sorting
- Click column header to sort ascending → click again for descending → click again to remove sort
- Multi-column sort: hold `Shift` + click additional columns
- Sort indicator animates with 150ms ease-in-out transition
- Current sort state must be communicated via `aria-sort`

### Selection
- Header checkbox: selects/deselects all rows on current page
- Indeterminate state when some (but not all) rows are selected
- Selection count shown in toolbar: "3 of 1,248 selected"
- Bulk action bar appears when ≥1 row selected, pushing toolbar content

### Pagination
- Default page size: 25 rows (options: 10, 25, 50, 100)
- Show "Showing X–Y of Z" text using `typography.body.sm` in `color.text.secondary`
- Truncate page numbers with ellipsis when >7 pages
- Keyboard: `←`/`→` to navigate pages when pagination is focused

### Column Resizing
- Drag handle appears on hover at column border (right edge)
- Minimum column width: 80px
- Cursor changes to `col-resize` during drag
- Other columns adjust proportionally

---

## Accessibility Requirements

- `role="table"` on container, `role="row"`, `role="columnheader"`, `role="cell"` on respective elements
- `aria-sort="ascending|descending|none"` on sortable column headers
- `aria-selected="true|false"` on selectable rows
- `aria-label` on the table describing its content (e.g., "User activity log")
- Keyboard navigation: `Tab` to enter table → arrow keys to navigate cells → `Space` to select row → `Enter` to activate row action
- Focus must be visible on the current cell/row with `color.border.focus`
- Screen reader announcement when sort changes: "Sorted by Name, ascending"
- Pagination controls must be keyboard accessible with clear labels

---

## Responsive Behavior

| Breakpoint | Behavior |
|-----------|----------|
| Desktop (≥1024px) | Full table with all columns visible |
| Tablet (768–1023px) | Hide lower-priority columns, show column toggle |
| Mobile (<768px) | Switch to card/list layout — each row becomes a stacked card |

### Mobile Card Layout
```
┌──────────────────────────┐
│ ☐ Jane Doe          Admin│
│   jane@example.com       │
│   Last active: 2 min ago │
│                    [···] │
└──────────────────────────┘
```

---

## Do / Don't

✅ **Do:** Use skeleton loading that matches actual row structure  
❌ **Don't:** Use a single centered spinner for table loading

✅ **Do:** Provide a clear empty state with actionable guidance  
❌ **Don't:** Show a blank white area when no data exists

✅ **Do:** Use `color.text.secondary` for less important columns (email, date)  
❌ **Don't:** Make all columns the same visual weight

✅ **Do:** Truncate long cell content with ellipsis and show full content on hover/focus  
❌ **Don't:** Let long content break the table layout or wrap unpredictably

✅ **Do:** Keep the header row sticky when scrolling long tables  
❌ **Don't:** Let the header scroll out of view
