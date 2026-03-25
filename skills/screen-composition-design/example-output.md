# Example Output: Screen Composition Design — User Management Dashboard

## Screen Overview

**Screen:** Admin User Management Dashboard  
**Product:** B2B SaaS platform (team collaboration tool)  
**User:** Admin users managing team members, roles, and permissions  
**Primary Tasks:** View team members, invite new users, manage roles, review activity

---

## Layout Structure

```
┌─────────────────────────────────────────────────────────────────┐
│ ┌─ App Header ────────────────────────────────────────────────┐ │
│ │ [Logo]    Dashboard  Users  Settings    [Search] [Avatar ▾] │ │
│ └─────────────────────────────────────────────────────────────┘ │
│                                                                 │
│ ┌─ Page Header ───────────────────────────────────────────────┐ │
│ │ Team Members (24)                        [Invite User]      │ │
│ │ Manage your team's access and permissions                   │ │
│ └─────────────────────────────────────────────────────────────┘ │
│                                                                 │
│ ┌─ Stats Row ─────────────────────────────────────────────────┐ │
│ │ ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐        │ │
│ │ │ 24       │ │ 18       │ │ 3        │ │ 3        │        │ │
│ │ │ Total    │ │ Active   │ │ Pending  │ │ Deactivated│      │ │
│ │ └──────────┘ └──────────┘ └──────────┘ └──────────┘        │ │
│ └─────────────────────────────────────────────────────────────┘ │
│                                                                 │
│ ┌─ Filter Bar ────────────────────────────────────────────────┐ │
│ │ [Search users...]  [Role ▾]  [Status ▾]  [Department ▾]    │ │
│ └─────────────────────────────────────────────────────────────┘ │
│                                                                 │
│ ┌─ User Table ────────────────────────────────────────────────┐ │
│ │ ☐  Name          Email          Role     Status   Last Act. │ │
│ │ ─────────────────────────────────────────────────────────── │ │
│ │ ☐  Jane Doe      jane@...       Admin    Active   2m ago    │ │
│ │ ☐  John Smith    john@...       Editor   Active   1h ago    │ │
│ │ ☐  Maria Lopez   maria@...      Viewer   Pending  —         │ │
│ │ ...                                                         │ │
│ │ Showing 1–10 of 24              [◀] 1 2 3 [▶]              │ │
│ └─────────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────────┘
```

---

## Zone Architecture

### Zone 1: Page Header
**Purpose:** Identify the screen and provide the primary action.

```css
.page-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  padding: var(--space-xl) 0 var(--space-lg);
}

.page-title {
  font-size: var(--typography-heading-lg);     /* 24px */
  font-weight: 600;
  color: var(--color-text-primary);
  line-height: 1.3;
}

.page-title-count {
  font-weight: 400;
  color: var(--color-text-tertiary);
}

.page-description {
  font-size: var(--typography-body-md);        /* 14px */
  color: var(--color-text-secondary);
  margin-top: var(--space-xs);
}
```

**Rules:**
- Title always includes a count when the page lists items
- Primary CTA (Invite User) is always top-right, visually prominent
- Description is optional — use only when the page purpose isn't obvious from the title

### Zone 2: Stats Row
**Purpose:** Provide at-a-glance metrics that help users understand the current state before diving into the table.

```css
.stats-row {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: var(--space-md);
  margin-bottom: var(--space-lg);
}

.stat-card {
  padding: var(--space-md) var(--space-lg);
  background: var(--color-surface-default);
  border: 1px solid var(--color-border-default);
  border-radius: var(--radius-lg);
}

.stat-value {
  font-size: var(--typography-heading-lg);     /* 24px */
  font-weight: 700;
  color: var(--color-text-primary);
  line-height: 1;
}

.stat-label {
  font-size: var(--typography-body-sm);        /* 12px */
  color: var(--color-text-secondary);
  margin-top: var(--space-xs);
}

/* Clickable stat cards filter the table */
.stat-card--interactive {
  cursor: pointer;
  transition: border-color 150ms ease;
}

.stat-card--interactive:hover {
  border-color: var(--color-border-strong);
}

.stat-card--active {
  border-color: var(--color-border-brand);
  background: var(--color-surface-brand-subtle);
}
```

**Rules:**
- Stats are clickable — clicking "Pending (3)" filters the table to pending users
- Active filter state shown with brand border and subtle background
- Maximum 4 stat cards on this row — more would dilute focus

### Zone 3: Filter Bar
**Purpose:** Enable users to narrow down the table content.

```css
.filter-bar {
  display: flex;
  align-items: center;
  gap: var(--space-sm);
  padding: var(--space-sm) 0;
  margin-bottom: var(--space-md);
}

.filter-search {
  flex: 1;
  max-width: 320px;
}

.filter-dropdown {
  min-width: 140px;
}

/* Active filter indicator */
.filter-dropdown--active {
  border-color: var(--color-border-brand);
}

.filter-dropdown--active::after {
  content: "";
  width: 6px;
  height: 6px;
  background: var(--color-action-primary);
  border-radius: var(--radius-full);
  position: absolute;
  top: -2px;
  right: -2px;
}
```

**Rules:**
- Search is always the first (leftmost) filter element
- Dropdown filters show a dot indicator when active
- "Clear all filters" link appears when any filter is active
- Filter bar is sticky when scrolling long tables

### Zone 4: Data Table
**Purpose:** The primary content area — displays the user list with all relevant information.

Follows the DataTable component specification (see `ui-component-design` skill). Key composition decisions for this screen:

- **Columns:** Name (with avatar), Email, Role (badge), Status (badge), Last Active
- **Row actions:** Three-dot menu with Edit, Change Role, Deactivate/Activate, Remove
- **Bulk actions:** When rows selected, show bulk action bar (Change Role, Deactivate, Remove)
- **Default sort:** Last Active (most recent first)
- **Pagination:** 10 rows per page (admin tables are typically scanned, not scrolled)

---

## Responsive Behavior

| Breakpoint | Layout Changes |
|-----------|---------------|
| Desktop (≥1280px) | Full layout as shown above |
| Large tablet (1024–1279px) | Stats row: 4 columns → 2×2 grid |
| Tablet (768–1023px) | Hide Email column, collapse filters into "Filter" button with dropdown panel |
| Mobile (<768px) | Stats row: single column stack; Table → card list; Filters in bottom sheet |

### Mobile Layout
```
┌──────────────────────────┐
│ Team Members (24)        │
│ [Invite User]            │
├──────────────────────────┤
│ 24 Total  │  18 Active   │
│ 3 Pending │  3 Deactivated│
├──────────────────────────┤
│ [Search...]  [Filter]    │
├──────────────────────────┤
│ ┌────────────────────┐   │
│ │ 🟢 Jane Doe        │   │
│ │    Admin · 2m ago   │   │
│ │              [···]  │   │
│ └────────────────────┘   │
│ ┌────────────────────┐   │
│ │ 🟢 John Smith      │   │
│ │    Editor · 1h ago  │   │
│ └────────────────────┘   │
└──────────────────────────┘
```

---

## Component Usage Map

| Zone | Components Used |
|------|----------------|
| Page Header | `Heading`, `Text`, `Button` (primary) |
| Stats Row | `StatCard` (custom composition of `Card` + `Text`) |
| Filter Bar | `SearchInput`, `Select` (dropdown), `TextButton` (clear filters) |
| Data Table | `DataTable`, `Avatar`, `Badge` (role, status), `DropdownMenu` (row actions) |
| Pagination | `Pagination` |

---

## Hierarchy & Visual Weight

```
[HIGH]    Page title + Primary CTA (Invite User)
  ↓
[MEDIUM]  Stats row — scannable numbers
  ↓
[LOW]     Filter bar — utility, not primary focus
  ↓
[HIGH]    Data table — primary content
  ↓
[LOW]     Pagination — utility
```

The page has a clear **high → medium → low → high → low** rhythm. Users land on the title, scan the stats, then focus on the table. The filter bar is visually quiet until needed.

---

## Empty State

When no team members exist (new account):

```
┌─────────────────────────────────────────┐
│                                         │
│         [Team illustration]             │
│                                         │
│     Your team is waiting                │
│     Invite your first team member       │
│     to start collaborating.             │
│                                         │
│         [Invite Team Member]            │
│                                         │
└─────────────────────────────────────────┘
```

- No stats row shown (all zeros is not useful)
- No filter bar shown (nothing to filter)
- Illustration is purposeful, not decorative
- Single CTA matches the page header CTA
