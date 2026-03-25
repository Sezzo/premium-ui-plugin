# UX Consistency Audit Checklist

## Interaction Consistency
- Are similar actions presented the same way?
- Are similar states represented the same way?
- Are destructive actions clearly differentiated and consistent?
- Are action hierarchies consistent across product areas?
- Do confirmation dialogs follow the same structure and tone?
- Are inline actions vs. page-level actions used consistently?

## Terminology and Labeling
- Are labels and terminology consistent across screens?
- Are different labels used for the same concept anywhere?
- Do CTAs follow a consistent naming pattern?
- Are placeholder texts and helper texts consistent in tone and format?

## Navigation and Flow
- Do navigation patterns behave consistently?
- Are users forced to relearn patterns between screens?
- Are back/cancel/close behaviors predictable across flows?
- Do breadcrumbs, tabs, and steppers follow the same logic?

## Component Reuse
- Is the same component being reinvented multiple times?
- Do similar layouts use the same spacing and grouping logic?
- Are repeated use of ad-hoc UI patterns present?
- Are form patterns (validation, layout, submission) consistent?

## State Handling
- Are empty, loading, error, and success states handled consistently?
- Do skeleton/loading states follow the same visual pattern?
- Are error messages structured and positioned the same way?
- Are success confirmations consistent (toast, inline, page-level)?
- Are disabled states visually and behaviorally consistent?

## Accessibility Consistency
- Is focus order logical and consistent across all screens?
- Are ARIA labels and roles applied consistently to similar components?
- Do color contrast ratios meet standards uniformly (not just on some screens)?
- Are keyboard navigation patterns consistent across interactive elements?
- Are screen reader announcements consistent for similar state changes?
- Do touch targets meet minimum size requirements consistently?

## Motion and Animation Consistency
- Do equivalent transitions use the same duration and easing?
- Are entrance/exit animations consistent for similar elements?
- Do loading indicators follow the same animation pattern?
- Are hover/focus/active micro-interactions consistent across components?
- Is motion used purposefully or inconsistently decorative?

## Feedback Patterns
- Are user action confirmations delivered through the same mechanism?
- Do error states use the same visual language (color, icon, position)?
- Are progress indicators consistent (spinners, bars, skeletons)?
- Do notifications and alerts follow a unified pattern?
- Is inline validation consistent across all forms?

## Error Handling Consistency
- Do error pages (404, 500, etc.) follow the same layout and tone?
- Are form validation errors displayed in the same position and style?
- Are retry/recovery options presented consistently?
- Do timeout and connectivity errors follow the same pattern?
- Are error messages written in a consistent tone and structure?

## Red Flags
- same action, different style
- same state, different behavior
- different labels for the same concept
- repeated use of ad-hoc UI patterns
- inconsistent empty states
- inconsistent filter or search behavior
- visual polish hiding interaction inconsistency
- accessibility passing on some screens but failing on others
- animation present in some flows but absent in equivalent ones
- error handling that varies without clear reason