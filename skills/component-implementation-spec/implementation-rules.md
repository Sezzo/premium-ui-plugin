# Component Implementation Rules

## Core Principle
A component specification must eliminate ambiguity between design intent and engineering implementation.

## Every spec must define

### 1. Purpose
- What problem does the component solve?
- Why is it a reusable system object?

### 2. Use Cases
- Where should it be used?
- What product scenarios does it support?

### 3. Non-Goals
- What should this component not try to solve?
- What belongs to layout, business logic, or another component?

### 4. Anatomy
Define all structural parts explicitly.

Examples:
- container
- label
- title
- description
- leading icon
- trailing action
- helper text
- status indicator
- media area

### 5. Props / Inputs
Define the minimum stable API.
Examples:
- variant
- size
- disabled
- loading
- selected
- value
- label
- description
- icon
- action
- error
- helperText

Do not create prop bloat without real reuse value.

### 6. States
Define all relevant states.
At minimum consider:
- default
- hover
- active
- focus
- disabled
- loading
- error
- selected
- expanded / collapsed if applicable
- empty if relevant

### 7. Interaction Rules
Specify:
- click / tap behavior
- keyboard behavior
- focus movement
- toggle behavior if applicable
- dismissal behavior if applicable
- validation timing if relevant

### 8. Accessibility
Define:
- semantic role
- labeling requirements
- focus visibility
- keyboard support
- screen reader expectations
- contrast expectations
- touch target expectations if relevant

### 9. Content Rules
Clarify:
- allowed text lengths
- truncation behavior
- wrapping behavior
- icon usage limits
- empty or missing content behavior

### 10. Composition Rules
Clarify:
- where the component may appear
- what may appear inside it
- spacing around it
- prohibited nesting patterns

### 11. Token Usage
Map the component to approved token groups:
- typography
- spacing
- color
- border
- radius
- elevation
- motion

Do not hardcode one-off values where system tokens should apply.

### 12. Edge Cases
Always think through:
- long text
- no icon
- too many actions
- error + helper text
- loading + disabled overlap
- small screens
- localization expansion

## Premium Guardrails
Implementation must not introduce:
- decorative emoji usage
- sparkle or AI cliché motifs
- arbitrary gradients or glows
- effect-heavy visual styling used to fake importance
- ad-hoc spacing or radius changes inside implementation

## Complex Component Guidance

### Data Table Spec Requirements
Tables require the most detailed specs. Always include:

```typescript
// Minimum prop interface for a DataTable
interface DataTableProps {
  columns: ColumnDef[];        // Column definitions with header, accessor, sortable, priority
  data: Row[];                 // Row data
  variant?: 'basic' | 'selectable' | 'sortable' | 'full';
  size?: 'compact' | 'default' | 'comfortable';
  loading?: boolean;
  emptyState?: ReactNode;      // Custom empty state content
  onSort?: (column: string, direction: 'asc' | 'desc') => void;
  onSelect?: (selectedIds: string[]) => void;
  onPageChange?: (page: number, pageSize: number) => void;
  stickyHeader?: boolean;
  pagination?: { page: number; pageSize: number; total: number };
}

interface ColumnDef {
  id: string;
  header: string;
  accessor: string | ((row: Row) => ReactNode);
  sortable?: boolean;
  width?: string;              // CSS width (e.g., '200px', '1fr')
  priority?: 1 | 2 | 3;       // Responsive: 1=always visible, 3=hidden on mobile
  align?: 'left' | 'center' | 'right';
}
```

### Modal/Dialog Spec Requirements
```typescript
interface ModalProps {
  open: boolean;
  onClose: () => void;
  size?: 'sm' | 'md' | 'lg';  // sm=400px, md=560px, lg=720px
  title: string;
  description?: string;
  children: ReactNode;         // Body content
  actions?: ReactNode;         // Footer actions
  closeOnOverlay?: boolean;    // Default: true for non-destructive, false for forms
  preventClose?: boolean;      // Disable all close methods (for critical flows)
}
```

**Implementation notes:**
- Focus trap: first focusable element on open, return to trigger on close
- Escape key: closes unless `preventClose` is true
- Body scroll lock: `overflow: hidden` on `<body>` when open
- Mobile: full-screen below 768px

### Form Field Spec Requirements
```css
/* Token mapping for form fields */
.form-field {
  /* Label */
  --field-label-font: var(--font-size-sm);
  --field-label-weight: 500;
  --field-label-color: var(--color-text-primary);
  --field-label-gap: var(--space-xs);          /* Gap between label and input */

  /* Input */
  --field-input-height: 40px;
  --field-input-padding: var(--space-sm);
  --field-input-font: var(--font-size-md);
  --field-input-bg: var(--color-surface-default);
  --field-input-border: 1px solid var(--color-border-default);
  --field-input-radius: var(--radius-md);

  /* States */
  --field-input-border-hover: var(--color-border-strong);
  --field-input-border-focus: var(--color-border-focus);
  --field-input-border-error: var(--color-status-error);
  --field-input-bg-disabled: var(--color-surface-secondary);

  /* Helper/Error text */
  --field-helper-font: var(--font-size-xs);
  --field-helper-color: var(--color-text-secondary);
  --field-error-color: var(--color-status-error);
  --field-helper-gap: var(--space-2xs);        /* Gap between input and helper */
}
```

## Acceptance Criteria
A good component spec should make all of the following clear:
- how it behaves in all states
- how it scales across viewport sizes
- how it remains accessible (keyboard, screen reader, contrast)
- how it stays consistent with the design system tokens
- how a developer knows when they built it correctly
- how it handles edge cases (long text, missing data, error states)
- what the complete CSS token mapping looks like