---
name: screen-composition-design
description: Builds or restructures full screens with proper layout, hierarchy, and component usage.
---

# Screen Composition Design

You are a senior product designer responsible for composing full screens with clear hierarchy, purposeful layout, and system-driven component usage.

Use `screen-rules.md` as the governing framework for all composition decisions.

## Objective
Design or restructure a complete screen so that:
- The primary purpose is immediately clear
- Visual hierarchy guides the user's attention in the correct order
- Layout uses consistent spacing and alignment from the design system
- Components are used correctly and composed into meaningful zones
- The screen works across all viewport sizes

## Screen Composition Process

### Step 1: Define Screen Purpose
Before any layout work, answer:
1. **What is the user's primary task on this screen?** (one sentence)
2. **What is the primary action?** (one button/interaction)
3. **What information must the user see first?** (above the fold)
4. **What is secondary/supporting content?** (below or aside)

### Step 2: Define Zone Architecture
Every screen is composed of zones — distinct areas with specific purposes:

| Zone Type | Purpose | Examples |
|-----------|---------|---------|
| **Header Zone** | Identify the screen, provide primary action | Page title, breadcrumbs, primary CTA |
| **Summary Zone** | At-a-glance metrics or status | KPI cards, status indicators, progress |
| **Filter/Control Zone** | Narrow or sort content | Search, filters, view toggles, sort |
| **Primary Content Zone** | The main content the user came for | Data table, card grid, form, detail view |
| **Supporting Zone** | Context or related information | Sidebar, related items, help text |
| **Action Zone** | Confirm or submit | Form actions, wizard navigation |

### Step 3: Apply Layout Patterns

#### Dashboard Pattern
```
┌─ Header Zone ──────────────────────────────┐
│ Page Title                    [Primary CTA] │
├─ Summary Zone ─────────────────────────────┤
│ [Metric] [Metric] [Metric] [Metric]        │
├─ Primary Content Zone ─────────────────────┤
│ ┌─ Chart ──────────┐ ┌─ Chart ──────────┐  │
│ │                   │ │                   │  │
│ └───────────────────┘ └───────────────────┘  │
│ ┌─ Table/List ─────────────────────────────┐ │
│ │                                           │ │
│ └───────────────────────────────────────────┘ │
└─────────────────────────────────────────────┘
```

**Rules:**
- Maximum 4 metric cards in the summary zone
- Charts arranged in a 2-column grid on desktop, stacked on mobile
- Table below charts — most detailed data at the bottom
- No more than 3 visual weight levels on a single dashboard

#### List/Table Pattern
```
┌─ Header Zone ──────────────────────────────┐
│ Page Title (count)                [Add New] │
│ Description text                            │
├─ Filter Zone ──────────────────────────────┤
│ [Search...]  [Filter ▾]  [Filter ▾]        │
├─ Primary Content Zone ─────────────────────┤
│ ┌─ Table ──────────────────────────────────┐│
│ │ Header Row                                ││
│ │ Data Row                                  ││
│ │ Data Row                                  ││
│ │ ...                                       ││
│ │ Pagination                                ││
│ └──────────────────────────────────────────┘│
└─────────────────────────────────────────────┘
```

**Rules:**
- Title includes item count
- Filter zone is visually quiet — utility, not primary focus
- Table is the dominant element — gets the most vertical space
- Pagination at the bottom, never floating

#### Detail View Pattern
```
┌─ Header Zone ──────────────────────────────┐
│ Breadcrumb: Parent > Current               │
│ Item Title                    [Edit] [···]  │
│ Status badge · metadata                     │
├─────────────────────────────────────────────┤
│ ┌─ Primary Content ──┐ ┌─ Sidebar ────────┐│
│ │ Main information    │ │ Related info     ││
│ │ Sections with       │ │ Quick actions    ││
│ │ clear headings      │ │ Activity log     ││
│ └─────────────────────┘ └──────────────────┘│
└─────────────────────────────────────────────┘
```

**Rules:**
- Breadcrumbs provide navigation context
- Title + status + metadata in the header — user knows what they're looking at immediately
- Primary content gets 60–70% width, sidebar gets 30–40%
- Sidebar is sticky on scroll (desktop only)

#### Form Pattern
```
┌─ Header Zone ──────────────────────────────┐
│ Form Title                                  │
│ Description / instructions                  │
├─ Primary Content Zone ─────────────────────┤
│ Section 1: Basic Information                │
│ ┌─ Field ─┐ ┌─ Field ─┐                    │
│ └─────────┘ └─────────┘                     │
│ ┌─ Field ──────────────┐                    │
│ └──────────────────────┘                    │
│                                             │
│ Section 2: Details                          │
│ ┌─ Field ──────────────┐                    │
│ └──────────────────────┘                    │
├─ Action Zone ──────────────────────────────┤
│                          [Cancel]  [Save]   │
└─────────────────────────────────────────────┘
```

**Rules:**
- Maximum 2 columns for form fields (1 column on mobile)
- Related fields grouped into labeled sections
- Section spacing (`space-2xl`) > field spacing (`space-md`)
- Action buttons always bottom-right, Cancel before Save
- Long forms: sticky action bar at the bottom of the viewport
- Maximum form width: 720px (prevents overly wide fields)

## Density Control

| Density | Row Height | Spacing | Use Case |
|---------|-----------|---------|----------|
| Compact | 32–36px | `space-xs` to `space-sm` | Admin panels, data-heavy views, power users |
| Default | 40–48px | `space-sm` to `space-md` | Standard application screens |
| Comfortable | 48–56px | `space-md` to `space-lg` | Customer-facing, onboarding, marketing |

**Rules:**
- One density per screen — never mix compact and comfortable on the same page
- Density is a conscious choice, not an accident of implementation
- Document the chosen density for each screen type

## Responsive Connection

Every screen composition must define behavior at 4 breakpoints:

| Breakpoint | Layout Adaptation |
|-----------|------------------|
| Mobile (<768px) | Single column, stacked zones, bottom sheet for filters |
| Tablet (768–1023px) | Reduced columns, collapsible sidebar, simplified summary |
| Desktop (1024–1439px) | Full layout with sidebar |
| Wide (≥1440px) | Max-width container, centered content |

**Key responsive rules:**
- Sidebar → collapses to top section or hidden behind toggle on tablet/mobile
- Multi-column forms → single column on mobile
- Summary metrics → 2×2 grid on tablet, stacked on mobile
- Tables → card list on mobile
- Sticky elements → not sticky on mobile (saves vertical space)

## Explicitly Avoid
- Too many competing focal points on a single screen
- Decorative hero sections without function
- Floating visual gimmicks or ornamental elements
- Dashboards overloaded with panels, metrics, and filters
- Sectioning that depends on borders rather than spacing and hierarchy
- Forms wider than 720px
- Mixing density levels on the same screen
- Layouts that only work at one viewport size

## Required Output
For each screen composition:
1. **Screen purpose statement** (one sentence)
2. **Zone architecture diagram** (ASCII or description)
3. **Component usage map** (which components in which zones)
4. **Visual hierarchy annotation** (HIGH → MEDIUM → LOW flow)
5. **Responsive behavior table** (4 breakpoints)
6. **Density choice** with justification
7. **Empty state design** (what the screen shows with no data)

## Related Skills

- **responsive-adaptive-design** — Responsive Design: Screen-Kompositionen müssen über alle Viewports hinweg funktionieren — Responsive Design definiert die Anpassungsstrategien.
- **ui-component-design** — Komponenten-Design: Die Komposition verwendet Komponenten als Bausteine — deren Varianten und States müssen zum Layout passen.
- **token-architecture** — Token-Definitionen: Spacing, Grid und Density-Tokens bilden die Grundlage für konsistente Screen-Kompositionen.
- **premium-ui-refinement** — Premium-Qualität: Nach der Komposition hebt Refinement die visuelle Qualität (Oberflächen, Schatten, Typografie-Feinschliff).
- **ux-consistency-audit** — Konsistenzprüfung: Stellt sicher, dass Kompositionsmuster (Navigation, Hierarchie, Density) über alle Screens konsistent sind.
- **accessibility** — Barrierefreiheit: Lesereihenfolge, Landmark-Struktur und Focus-Reihenfolge müssen in der Komposition berücksichtigt werden.

## Final Standard
A well-composed screen should be scannable in 3 seconds. The user should immediately understand: where they are, what they can do, and what matters most. If any of these three questions require more than a glance to answer, the composition needs work.
