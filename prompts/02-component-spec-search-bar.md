# Prompt 02: Component Implementation Spec — Search Bar

## Prompt

```
Create a component implementation spec for a global search bar component.

Context: This is for a B2B SaaS project management tool. The search bar appears in the top navigation and supports searching across projects, tasks, people, and documents. It should support keyboard shortcuts, recent searches, and type-ahead suggestions.
```

## Expected Output Should Include

- **15-section structured spec** (Overview → Acceptance Criteria)
- **Props table** with types, defaults, and required flags
- **Variants**: collapsed (icon-only), expanded, focused with dropdown
- **States**: idle, focused, loading, results, empty, error
- **Keyboard behavior**: Cmd/Ctrl+K shortcut, arrow navigation in results, Escape to close
- **Accessibility**: combobox role, aria-expanded, live region for result count
- **Token usage table** mapping every visual property to semantic tokens
- **Edge cases**: long queries, no results, offline state, rapid typing (debounce)
- **Acceptance criteria** as checkboxes

## Red Flags (Plugin Not Working If...)

- Missing sections (fewer than 10 of the 15 required sections)
- No accessibility requirements
- Vague descriptions instead of concrete prop definitions
- No token references
- Missing edge cases
