# UI Component Design Rules

This document defines the rules and standards that every UI component must follow to be a valid system citizen.

## Core Principle
A component is not a mockup fragment. It is a reusable system object with defined structure, behavior, states, and token dependencies.

## Every New Component Must Define

### 1. Purpose
- What problem does it solve?
- Why is it needed as a separate component?
- Why is it not already covered by an existing pattern?
- When should it be used vs when should an alternative be used?

### 2. Scope
- What belongs inside the component?
- What should remain outside?
- What responsibilities belong to layout rather than the component itself?
- Rule: Components should not control their own external spacing (margin). That belongs to the parent layout.

### 3. Anatomy
Define all structural parts clearly:
- Container
- Label / Title
- Description / Supporting text
- Icon / Media
- Action(s)
- Status indicator
- Badge / Count
- Divider (if applicable)

Provide an ASCII anatomy diagram:
```
┌─ Container ────────────────────────┐
│ [Icon]  Title              [Action]│
│         Description                │
│         Supporting text            │
└────────────────────────────────────┘
```

### 4. Variants
Define only meaningful variants — each must serve a distinct product need:

| Variant | Purpose | Visual Difference |
|---------|---------|------------------|
| `primary` | Main action or emphasis | Filled background, high contrast |
| `secondary` | Supporting action | Border only, lower contrast |
| `ghost` | Tertiary or inline action | No border, no background |
| `destructive` | Dangerous action | Error color treatment |

**Rule:** If two variants look different but serve the same purpose, merge them. If they serve different purposes but look the same, differentiate them.

### 5. Sizes
Sizes must follow density logic:

| Size | Height | Font | Padding | Use Case |
|------|--------|------|---------|----------|
| `sm` | 32px | `typography.body.sm` | `space-xs` | Compact contexts, inline usage |
| `md` | 40px | `typography.body.md` | `space-sm` | Default — most contexts |
| `lg` | 48px | `typography.body.md` | `space-md` | Prominent placement, touch targets |

**Rule:** All interactive components in the same context must use the same size. Never mix `sm` buttons with `lg` inputs.

### 6. States
At minimum, evaluate and define these states:

| State | Visual Change | Trigger |
|-------|--------------|---------|
| Default | Base appearance | — |
| Hover | Background/border shift | Mouse enter |
| Active/Pressed | Darker background, slight scale | Mouse down |
| Focus | Focus ring (`2px solid color.focus.ring`) | Keyboard Tab |
| Disabled | Reduced opacity (0.5) or muted colors | `disabled` attribute |
| Loading | Spinner replaces content or inline indicator | Async action |
| Error | Error border + error message | Validation failure |
| Selected | Brand accent background/border | User selection |
| Expanded | Content revealed, chevron rotated | Toggle action |

**Rule:** Every state must be visually distinct from every other state. If two states look the same, users cannot distinguish them.

### 7. Accessibility
Every component must define:
- **Keyboard access:** How to reach and operate the component with keyboard only
- **Focus state:** Visible focus ring meeting 3:1 contrast ratio
- **ARIA role:** Semantic role (`role="button"`, `role="dialog"`, etc.)
- **ARIA labels:** `aria-label` for icon-only elements, `aria-expanded` for toggles
- **Screen reader behavior:** What is announced when the component receives focus
- **Touch target:** Minimum 44×44px on touch devices
- **Color independence:** Information must not rely on color alone

### 8. Responsiveness
Define behavior at each breakpoint:
- **Stacking:** Does the component stack vertically on mobile?
- **Truncation:** How is overflow text handled? (ellipsis, line clamp, wrap)
- **Content priority:** What is hidden on smaller screens?
- **Touch adaptation:** Larger touch targets, swipe gestures if applicable
- **Full-width:** Does the component go full-width on mobile?

### 9. Token Dependency
Map every visual property to a system token:

```css
/* Example: Button token mapping */
.button {
  /* Typography */
  font-size: var(--typography-label-md);
  font-weight: 600;
  
  /* Spacing */
  padding: var(--space-sm) var(--space-md);
  gap: var(--space-xs);
  
  /* Color */
  background: var(--color-action-primary);
  color: var(--color-text-on-action);
  border: 1px solid transparent;
  
  /* Shape */
  border-radius: var(--radius-md);
  
  /* Elevation */
  box-shadow: none;
  
  /* Motion */
  transition: background var(--transition-fast), box-shadow var(--transition-fast);
}
```

**Rule:** No hardcoded values. Every color, spacing, radius, and font value must reference a token.

### 10. Composition Rules
Define how the component relates to other components:

- **Contains:** What child components can appear inside this component?
- **Contained by:** What parent components can wrap this component?
- **Adjacent spacing:** What spacing token applies between this component and its siblings?
- **Interaction boundaries:** Does clicking this component affect other components?

## Complex Component Patterns

### Table Composition
```
┌─ Table Container ──────────────────────────────┐
│ ┌─ Toolbar ──────────────────────────────────┐ │
│ │ [Search] [Filters] [Columns] [Export]      │ │
│ ├─ Bulk Action Bar (when selected) ──────────┤ │
│ │ "3 selected" [Action] [Action] [Deselect]  │ │
│ ├─ Header Row ───────────────────────────────┤ │
│ │ [☐] Column A ▲  Column B  Column C  [···]  │ │
│ ├─ Body ─────────────────────────────────────┤ │
│ │ [☐] Data       Data      Data      [···]   │ │
│ │ [☐] Data       Data      Data      [···]   │ │
│ ├─ Footer ───────────────────────────────────┤ │
│ │ "Showing 1–25 of 100"  [◀] 1 2 3 ... [▶]  │ │
│ └────────────────────────────────────────────┘ │
└────────────────────────────────────────────────┘
```

### Modal Composition
```
┌─ Overlay (click to close) ─────────────────────┐
│  ┌─ Modal Container ────────────────────────┐  │
│  │ ┌─ Header ─────────────────────────────┐ │  │
│  │ │ Title                          [✕]   │ │  │
│  │ ├─ Body ───────────────────────────────┤ │  │
│  │ │ Content (scrollable if needed)       │ │  │
│  │ ├─ Footer ─────────────────────────────┤ │  │
│  │ │              [Cancel] [Confirm]      │ │  │
│  │ └─────────────────────────────────────┘ │  │
│  └──────────────────────────────────────────┘  │
└────────────────────────────────────────────────┘
```

### Form Field Composition
```
┌─ Field Container ──────────────────────────────┐
│ Label *                                        │
│ ┌─ Input ────────────────────────────────────┐ │
│ │ Placeholder text                     [Icon]│ │
│ └────────────────────────────────────────────┘ │
│ Helper text or Error message                   │
└────────────────────────────────────────────────┘
```

## Premium Guardrails
The component must not rely on:
- Decorative emojis
- Sparkles or AI cliche motifs
- Loud gradients or glows
- Fake futuristic styling
- Excessive shadow to create importance
- Visual complexity used to compensate for weak hierarchy

## Red Flags
- One-off styling that doesn't match the system
- Unclear purpose — "what is this component for?"
- Too many variants (>5 usually signals scope creep)
- Missing states (especially focus, disabled, loading)
- Style that breaks system consistency
- Solving layout problems inside the component
- Hardcoded values instead of token references
