# Premium UI Principles

This document defines the principles, techniques, and measurable criteria that govern premium UI quality. Every refinement recommendation must trace back to one or more of these principles.

## Core Philosophy

Premium UI is not about adding — it is about controlling. A premium interface communicates quality through discipline: consistent spacing, purposeful typography, restrained color, and intentional detail. The absence of arbitrary decisions is what separates premium from generic.

## Principle 1: Hierarchy Through Typography

Typography is the primary tool for creating visual hierarchy. Before reaching for color, size, or decoration, exhaust typographic options first.

### Techniques

**Weight contrast creates hierarchy without size changes:**
```css
/* Primary information */
.data-value { font-weight: 600; color: var(--color-text-primary); }

/* Secondary context */
.data-label { font-weight: 400; color: var(--color-text-secondary); }

/* Tertiary metadata */
.data-meta { font-weight: 400; color: var(--color-text-tertiary); font-size: var(--typography-body-sm); }
```

**Letter-spacing signals importance:**
```css
/* Display text: tighter tracking = more premium */
.display { letter-spacing: -0.02em; }

/* Labels: slightly wider tracking = utility feel */
.label-uppercase { letter-spacing: 0.04em; text-transform: uppercase; font-size: var(--typography-label-xs); }
```

**Line-height controls density and readability:**
- Display/Headings: `1.1–1.3` — tight, impactful
- Body text: `1.5–1.6` — comfortable reading
- UI labels: `1.2–1.4` — compact but legible

### Checklist
- [ ] At least 5 distinct typographic levels are defined
- [ ] Display text uses tightened letter-spacing
- [ ] Body text line length does not exceed 75 characters
- [ ] No two adjacent elements share the same typographic style unless they are the same content type
- [ ] Font weights are used purposefully (not randomly)

## Principle 2: Spacing as Structure

Spacing is not empty space — it is structure. Consistent spacing creates rhythm, groups related elements, and separates unrelated ones. Arbitrary spacing is the most common quality killer.

### Techniques

**Spacing scale with clear ratios:**
```css
:root {
  --space-2xs: 4px;
  --space-xs: 8px;
  --space-sm: 12px;
  --space-md: 16px;
  --space-lg: 24px;
  --space-xl: 32px;
  --space-2xl: 48px;
  --space-3xl: 64px;
}
```

**Spacing hierarchy rule:**
- Within a component: `space-xs` to `space-sm`
- Between components in a group: `space-md` to `space-lg`
- Between sections: `space-xl` to `space-2xl`
- Between major page zones: `space-2xl` to `space-3xl`

**Padding asymmetry for premium feel:**
```css
/* More vertical padding than horizontal creates a calmer, more spacious feel */
.card {
  padding: var(--space-xl) var(--space-lg);  /* 32px top/bottom, 24px sides */
}

/* Section headers benefit from more top spacing (separation) than bottom (connection) */
.section-header {
  margin-top: var(--space-2xl);
  margin-bottom: var(--space-md);
}
```

### Checklist
- [ ] All spacing values map to the defined scale — no arbitrary pixel values
- [ ] Section spacing is at least 2× internal component spacing
- [ ] Consistent padding within same component types
- [ ] Vertical rhythm is maintained across the page
- [ ] No spacing value appears only once (signals an arbitrary decision)

## Principle 3: Restrained Color

Color should inform, not decorate. Premium interfaces use color sparingly and purposefully. Every color must answer the question: "What information does this color communicate?"

### Techniques

**Text color hierarchy:**
```css
:root {
  --color-text-primary: #111827;     /* Main content — highest contrast */
  --color-text-secondary: #4B5563;   /* Supporting content */
  --color-text-tertiary: #9CA3AF;    /* Metadata, timestamps — must still meet 4.5:1 on background */
  --color-text-disabled: #D1D5DB;    /* Disabled states */
}
```

**Surface color for zoning (not decoration):**
```css
/* Use surface shifts to create visual zones */
.page-background { background: var(--color-surface-secondary); }
.content-card { background: var(--color-surface-default); }
.sidebar { background: var(--color-surface-tertiary); }

/* NOT: random colored backgrounds for visual interest */
```

**Status colors — functional, not decorative:**
```css
:root {
  --color-status-success: #059669;
  --color-status-warning: #D97706;
  --color-status-error: #DC2626;
  --color-status-info: #2563EB;
}
```

### Checklist
- [ ] Maximum 3 accent colors per view (excluding status colors)
- [ ] Every colored element has a functional justification
- [ ] Text colors form a clear 3-level hierarchy
- [ ] No decorative gradients or colored backgrounds without purpose
- [ ] All text-on-background combinations meet WCAG AA contrast (4.5:1)

## Principle 4: Elevation With Purpose

Depth communicates interactivity and importance. Elements that are interactive or overlapping should appear elevated. Static content should remain flat.

### Techniques

**Three-level elevation system:**
```css
:root {
  /* Level 0: Flat — default content, static elements */
  --elevation-none: none;

  /* Level 1: Raised — cards, interactive surfaces */
  --elevation-sm: 0 1px 2px rgba(0,0,0,0.04), 0 2px 6px rgba(0,0,0,0.06);

  /* Level 2: Floating — dropdowns, tooltips, modals */
  --elevation-md: 0 2px 4px rgba(0,0,0,0.04), 0 4px 12px rgba(0,0,0,0.08);

  /* Level 3: Overlay — modal overlays, popovers */
  --elevation-lg: 0 4px 8px rgba(0,0,0,0.04), 0 8px 24px rgba(0,0,0,0.1);
}
```

**Elevation rules:**
- Static content: no shadow
- Interactive cards: `elevation-sm` on hover (not by default)
- Dropdowns and popovers: `elevation-md`
- Modals: `elevation-lg` + backdrop overlay
- Never use more than one elevation level difference between adjacent elements

### Checklist
- [ ] Elevation hierarchy is defined with at least 3 levels
- [ ] Shadows use multi-layered values (not single box-shadow)
- [ ] Static content has no shadow
- [ ] Interactive elements gain elevation on hover/focus
- [ ] Modals and overlays use the highest elevation level

## Principle 5: Interaction Confidence

Every interaction should feel immediate, predictable, and intentional. Users should never wonder "did that work?" or "what will happen if I click this?"

### Techniques

**Transition timing:**
```css
/* Fast: state changes (hover, active, focus) */
--transition-fast: 150ms ease;

/* Normal: content changes (expand, collapse, show/hide) */
--transition-normal: 200ms ease;

/* Slow: layout changes (page transitions, large animations) */
--transition-slow: 300ms ease;
```

**Hover feedback pattern:**
```css
/* Subtle but clear — background shift + optional border change */
.interactive-element {
  transition: background var(--transition-fast), border-color var(--transition-fast);
}

.interactive-element:hover {
  background: var(--color-surface-hover);
}

/* NOT: color explosions, scale transforms, or dramatic shadow changes */
```

**Focus ring standard:**
```css
:focus-visible {
  outline: 2px solid var(--color-focus-ring);
  outline-offset: 2px;
}
```

### Checklist
- [ ] Every interactive element has a visible hover state
- [ ] Transitions use consistent timing (150ms / 200ms / 300ms)
- [ ] Focus states are visible and meet 3:1 contrast
- [ ] Loading states exist for every async action
- [ ] No interaction takes more than 100ms to show feedback

## Principle 6: Consistency as Quality Signal

Inconsistency is the fastest way to undermine perceived quality. A single misaligned element, a single off-system color, or a single inconsistent spacing value signals "this was not designed carefully."

### Rules
- Same component type = same visual treatment everywhere
- Same content type = same typographic style everywhere
- Same interaction type = same feedback pattern everywhere
- Same spacing context = same spacing value everywhere
- Exceptions must be documented and justified — never accidental

## Anti-Patterns: What Premium Is Not

| Anti-Pattern | Why It Fails | Premium Alternative |
|-------------|-------------|-------------------|
| Gradient backgrounds for visual interest | Decorative, not functional | Subtle surface color shifts |
| Glow effects on buttons | Cheap, attention-seeking | Subtle elevation change on hover |
| Animated illustrations | Distracting, not informational | Static, purposeful iconography |
| Multiple accent colors competing | Chaotic, no hierarchy | Single primary accent, muted secondary |
| Oversized hero sections | Wastes space, delays content | Compact, content-forward headers |
| Rounded everything (pill shapes) | Feels casual, not professional | Consistent radius scale (sm/md/lg) |
| Decorative dividers or ornaments | Adds noise, no information | Spacing and surface shifts for separation |
