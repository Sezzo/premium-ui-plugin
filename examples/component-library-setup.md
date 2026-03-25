# Example: Component Library Setup Workflow

This example demonstrates how to use the Premium UI Plugin to establish a component library from scratch for a new product.

## Scenario

You are building a B2B analytics platform and need to establish a component library that ensures consistency across all screens. The product has no existing design system — components are currently built ad-hoc by different developers.

## Step-by-Step Workflow

### 1. Bootstrap the Repository

Use `design-system-setup` to initialize the design system infrastructure:

```
Set up this repository for premium UI development.
Create AGENTS.md and CLAUDE.md with our design standards.
Our product is a B2B analytics platform for enterprise customers.
The tone should be serious, trustworthy, and data-focused.
```

### 2. Define Token Foundations

Use `token-architecture` to establish the design tokens:

```
Define a complete token architecture for our analytics platform.
We need:
- Color tokens: neutral palette, one brand color (deep blue), status colors
- Typography: Inter as primary font, tabular figures for data
- Spacing: 8px base unit
- Border radius: conservative (4px-8px, nothing too rounded)
- Elevation: 3 levels (flat, raised, floating)
- Motion: fast transitions (150ms) for a responsive feel
```

### 3. Establish Brand Character

Use `brand-ui-alignment` to define the brand expression:

```
Define the brand-UI alignment for our analytics platform.
Brand attributes: precise, trustworthy, data-focused, professional, calm.
Target audience: enterprise data analysts and business intelligence teams.
The UI should feel like a Bloomberg terminal's modern cousin — serious about data
but more approachable.
```

### 4. Design Core Components

Use `ui-component-design` for each foundational component. Start with the most-used components:

**Buttons:**
```
Design a Button component for our analytics platform.
We need: primary, secondary, ghost, and destructive variants.
Sizes: sm (32px), md (40px), lg (48px).
Must include all states: default, hover, active, focus, disabled, loading.
```

**Data Table:**
```
Design a DataTable component for our analytics platform.
This is our most critical component — used on 70% of screens.
Must support: sorting, selection, pagination, column resizing.
Must handle: loading, empty, error states.
Must be responsive: column hiding on tablet, card layout on mobile.
```

**Form Fields:**
```
Design a unified form field system: Input, Select, Textarea, Checkbox, Radio.
All fields must share the same height (40px), border treatment, and error pattern.
Include: labels, helper text, error messages, required indicators.
Validation: on-blur with on-submit re-validation.
```

### 5. Review the System

Use `design-system-review` to check the emerging system:

```
Review our component library so far: Button, DataTable, Input, Select,
Textarea, Checkbox, Radio. Check for:
- Token consistency across all components
- Visual coherence (do they feel like one family?)
- Missing states or variants
- Accessibility gaps
```

### 6. Create Implementation Specs

Use `component-implementation-spec` for engineering handoff:

```
Create implementation specs for our Button component.
Include: complete prop interface, all state CSS, token mapping,
accessibility requirements, keyboard behavior, and responsive rules.
Target framework: React with CSS custom properties.
```

### 7. Final Quality Check

Use `design-critique` for a critical review:

```
Critique our component library. Be strict.
Does it feel premium? Is it consistent? Would an enterprise customer
trust a product built with these components?
Focus on: visual coherence, interaction quality, and system discipline.
```

## Expected Outcome

After completing this workflow, you should have:

- Token foundations driving all visual decisions (colors, typography, spacing, radius, elevation)
- A documented brand character guiding design decisions
- Core components (Button, DataTable, Form Fields) fully specified
- All components sharing consistent visual DNA (same tokens, same states, same patterns)
- Implementation-ready specs for engineering
- A critical review identifying any remaining gaps
- A repository configured for ongoing premium UI development

## Key Principle

Build the system before building the screens. A strong component library makes every future screen faster and more consistent. The investment in tokens and core components pays off exponentially as the product grows.
