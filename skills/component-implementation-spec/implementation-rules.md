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

## Acceptance Criteria
A good component spec should make all of the following clear:
- how it behaves
- how it scales
- how it remains accessible
- how it stays consistent with the system
- how a developer knows when they built it correctly