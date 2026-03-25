# UI Component Design Rules

## Core Principle
A component is not a mockup fragment.
It is a reusable system object.

## Every new component must define

### 1. Purpose
- What problem does it solve?
- Why is it needed as a separate component?
- Why is it not already covered by an existing pattern?

### 2. Scope
- What belongs inside the component?
- What should remain outside?
- What responsibilities belong to layout rather than the component itself?

### 3. Anatomy
Define all structural parts clearly.
Examples:
- container
- label
- title
- description
- icon
- action
- supporting text
- media
- status indicator

### 4. Variants
Define only meaningful variants.
Avoid cosmetic-only variation without product value.

### 5. Sizes
Sizes must follow a clear density or usage logic.

### 6. States
At minimum evaluate:
- default
- hover
- active
- focus
- disabled
- loading
- error
- selected
- expanded/collapsed if applicable

### 7. Accessibility
- keyboard access
- visible focus state
- contrast
- semantic role
- screen reader labeling
- touch target size if relevant

### 8. Responsiveness
- stacking behavior
- truncation rules
- content priority on smaller screens
- overflow handling

### 9. Token Dependency
Map the component to:
- typography tokens
- spacing tokens
- color tokens
- radius tokens
- border tokens
- shadow/elevation tokens
- motion tokens

### 10. Composition Rules
- which components may contain it
- which components it may contain
- spacing rules around it
- interaction boundaries

## Premium Guardrails
The component must not rely on:
- decorative emojis
- sparkles or AI cliché motifs
- loud gradients or glows
- fake futuristic styling
- excessive shadow to create importance
- visual complexity used to compensate for weak hierarchy

## Red Flags
- one-off styling
- unclear purpose
- too many variants
- inaccessible states
- style that breaks system consistency
- solving layout problems inside the component that belong to the page layout