# Token Architecture Rules

## Core Principle
A token system is not just a list of values.
It is the structural foundation that keeps a design system consistent, scalable, and governable.

## Primary Goals
The token architecture must:
- create semantic clarity
- reduce duplication
- support consistent UI quality
- separate reusable system decisions from component-specific implementation
- make future scaling easier

## Recommended Architectural Layers

### 1. Primitive Tokens
Raw foundational values with no product meaning beyond their category.

Examples:
- raw color values
- raw spacing steps
- raw radius values
- raw font sizes
- raw line heights
- raw motion durations
- raw shadow values

Primitive tokens should be stable and minimal.

### 2. Semantic Tokens
Meaning-based tokens that describe intent rather than raw value.

Examples:
- color.text.primary
- color.text.secondary
- color.surface.default
- color.surface.elevated
- color.border.subtle
- color.action.primary.bg
- space.section.md
- radius.interactive.md

Semantic tokens should be the main layer consumed by design work and implementation.

### 3. Component Tokens
Component-scoped tokens only when necessary.

Examples:
- button.primary.bg
- button.primary.text
- input.border.default
- card.padding.default

Component tokens should only exist when semantic tokens are not sufficient on their own.

Do not create component tokens for every possible value unless real reuse or component-specific logic requires it.

## Naming Rules

### General Naming Principles
- Names must express role, not appearance alone.
- Names must be predictable.
- Names must scale across future additions.
- Names must avoid ambiguity.
- Names must not encode temporary screen-specific context.

### Prefer
- color.text.primary
- color.surface.subtle
- color.border.strong
- space.stack.md
- space.inline.sm
- radius.container.md

### Avoid
- blue-500-final
- card-gray-2
- widget-padding-special
- homepage-border
- cool-shadow
- ai-glow

## Token Categories

### Color
Use clearly separated groups such as:
- color.text.*
- color.icon.*
- color.surface.*
- color.border.*
- color.action.*
- color.feedback.success.*
- color.feedback.warning.*
- color.feedback.error.*
- color.focus.*
- color.disabled.*

### Typography
Structure typography tokens by role, not random size dumping.

Examples:
- typography.display.lg
- typography.heading.md
- typography.body.md
- typography.label.sm
- typography.caption.sm

Where needed, separate:
- font family
- font size
- line height
- letter spacing
- font weight

### Spacing
Spacing should be systematic and limited.

Recommended:
- primitive scale for raw space steps
- semantic usage mapping for layout intent

Examples:
- space.2
- space.4
- space.8
- space.stack.sm
- space.stack.md
- space.section.lg
- space.inset.card.md

### Radius
Avoid random radius growth.
Define a restrained system.

Examples:
- radius.none
- radius.sm
- radius.md
- radius.lg
- radius.round

Optional semantic aliases:
- radius.interactive.md
- radius.container.lg

### Elevation / Shadow
Use only if the visual language genuinely requires it.
Elevation should be restrained.

Examples:
- elevation.none
- elevation.subtle
- elevation.raised
- elevation.overlay

Do not create decorative shadow variety without structural meaning.

### Motion
Only define motion tokens that reflect real system usage.

Examples:
- motion.duration.fast
- motion.duration.normal
- motion.easing.standard
- motion.easing.emphasized

Avoid motion token bloat.

## Primitive vs Semantic Token Strategy

### Primitive Tokens
Use primitive tokens as the base layer.

### Semantic Tokens
Use semantic tokens for actual UI meaning.

### Rule
Do not consume primitive tokens directly in most product UI decisions if semantic tokens should exist.

Primitive tokens define the palette.
Semantic tokens define the product language.

## Component Token Rules
Only introduce component tokens when at least one of these is true:
- a component needs component-specific mapping
- a component has variants with stable internal logic
- semantic tokens alone become too generic
- implementation clarity significantly improves

Avoid component-token explosion.

## State Token Rules
State logic must be systematic.

Common state groups:
- default
- hover
- active
- focus
- disabled
- selected
- loading
- error
- success if relevant

State tokens should derive from the same logic as the default system, not become a second uncontrolled color system.

Examples:
- color.action.primary.bg.default
- color.action.primary.bg.hover
- color.action.primary.bg.active
- color.action.primary.text.disabled

## Theme / Mode Strategy
If multiple themes or modes are planned:
- keep primitive values separable from semantic meaning
- map semantic tokens to theme-specific primitives
- do not duplicate the full system unnecessarily
- keep theme logic centralized

This is especially relevant for:
- dark mode
- light mode
- brand themes
- density modes if needed

## Governance Rules

### A new token should only be added if:
- an existing token does not solve the problem cleanly
- the need is repeatable
- the token has a clear semantic role
- the token improves system quality rather than local convenience

### A new token should not be added if:
- it solves only one isolated screen issue
- it exists only to preserve a one-off visual choice
- it duplicates an existing semantic role
- it is named around appearance instead of intent

## Premium UI Guardrails
The token system must not encode cheap aesthetics into the system.

Do not create token structures centered around:
- glow styles
- decorative gradients without product purpose
- AI gimmick visuals
- flashy effect categories
- novelty-first styling

Premium UI should emerge from disciplined typography, spacing, surfaces, hierarchy, and restrained color logic.

## Required Quality Questions
For every token decision ask:
- Is this reusable?
- Is this semantically clear?
- Does this reduce ambiguity?
- Does this scale?
- Does this improve system discipline?
- Is this a true system need or a local workaround?