# UX Consistency Audit Checklist

This checklist defines the audit categories, their priority levels, and resolution strategies for common inconsistencies.

## Checklist Categories by Priority

### Priority 1: High-Impact Patterns (Fix First)
These patterns are encountered by every user on every session. Inconsistencies here have the highest impact on perceived quality.

#### Loading States
- [ ] Are loading patterns consistent across all screens?
- [ ] Do content areas use skeleton screens (not spinners)?
- [ ] Do action buttons use inline spinners (not page-level loading)?
- [ ] Is the loading-to-content transition smooth and consistent?

**Standard pattern:**
| Context | Loading Pattern |
|---------|----------------|
| Page/section content | Skeleton screen matching content structure |
| Data table refresh | Keep current data, show progress bar at top |
| Button action | Inline spinner, button disabled |
| Background save | No visible loading, success toast on completion |
| Navigation | Instant transition, skeleton on target page |

#### Form Validation
- [ ] Is validation timing consistent? (on-blur, on-submit, or hybrid)
- [ ] Are error messages positioned consistently? (below field, inline, tooltip)
- [ ] Do error states use the same visual treatment? (border color, icon, text color)
- [ ] Is the error message tone consistent? (helpful, specific, not generic)

**Standard pattern:** On-blur validation with on-submit re-validation. Error message below the field in `color.text.error` with `typography.body.sm`.

#### Error Handling
- [ ] Do all screens handle errors the same way?
- [ ] Are error pages (404, 500) consistent in layout and tone?
- [ ] Are form errors, API errors, and network errors distinguished?
- [ ] Is there always a recovery action (retry, go back, contact support)?

**Standard pattern:**
| Error Type | Pattern |
|-----------|---------|
| Form validation | Inline error below field + scroll to first error |
| API error (recoverable) | Toast notification with retry action |
| API error (fatal) | Inline error message with retry button |
| Network error | Banner at top of page with retry |
| 404 | Dedicated page with search + navigation |
| 500 | Dedicated page with retry + support contact |

### Priority 2: Navigation & Flow Patterns
These patterns affect how users move through the product. Inconsistencies cause confusion and lost context.

#### Navigation
- [ ] Do navigation patterns behave consistently across all screens?
- [ ] Is the active/current state clearly indicated everywhere?
- [ ] Are back/cancel/close behaviors predictable?
- [ ] Do breadcrumbs appear consistently on detail views?

#### Button Placement
- [ ] Are primary actions in the same position on every screen?
- [ ] Is the Cancel/Confirm order consistent? (Cancel left, Confirm right)
- [ ] Are destructive actions visually differentiated consistently?

**Standard pattern:**
| Context | Primary Button Position |
|---------|------------------------|
| Page-level actions | Top-right of content area |
| Form actions | Bottom-right, Cancel left of Save |
| Modal actions | Bottom-right, Cancel left of Confirm |
| Wizard steps | Bottom-right, Back button bottom-left |

#### Modal vs Panel Usage
- [ ] Is there a clear rule for when to use modals vs slide-in panels?
- [ ] Are confirmation dialogs always modals (not panels)?
- [ ] Do modals and panels have consistent header/footer structure?

### Priority 3: State Handling Patterns
These patterns affect how users understand the current state of the product.

#### Empty States
- [ ] Does every screen that can be empty have a designed empty state?
- [ ] Do empty states include a headline, description, and CTA?
- [ ] Are empty state illustrations/icons consistent in style?
- [ ] Are filtered-empty states different from first-time-empty states?

**Resolution strategy for missing empty states:**
1. Inventory all screens that can be empty
2. Categorize: first-time empty, filtered empty, error empty, permission empty
3. Design a template for each category
4. Apply consistently across all screens

#### Success Feedback
- [ ] Are success confirmations delivered through the same mechanism?
- [ ] Is the success pattern appropriate for the action weight?

**Standard pattern:**
| Action Weight | Success Pattern |
|--------------|----------------|
| Low (toggle, minor edit) | No explicit feedback — UI state change is sufficient |
| Medium (save, update) | Toast notification, auto-dismiss after 3s |
| High (create, delete, submit) | Inline success message or redirect with toast |

### Priority 4: Component-Level Consistency
These patterns affect the visual coherence of individual elements.

#### Interaction Consistency
- [ ] Are similar actions presented the same way across screens?
- [ ] Are similar states represented the same way?
- [ ] Are destructive actions clearly differentiated and consistent?
- [ ] Do confirmation dialogs follow the same structure and tone?

#### Terminology and Labeling
- [ ] Are labels and terminology consistent across screens?
- [ ] Are different labels used for the same concept anywhere?
- [ ] Do CTAs follow a consistent naming pattern?
- [ ] Are placeholder texts and helper texts consistent in tone?

#### Component Reuse
- [ ] Is the same component being reinvented on different screens?
- [ ] Do similar layouts use the same spacing and grouping logic?
- [ ] Are form patterns (layout, validation, submission) consistent?

### Priority 5: Cross-Cutting Consistency
These patterns span the entire product and affect overall polish.

#### Accessibility Consistency
- [ ] Is focus order logical and consistent across all screens?
- [ ] Are ARIA labels applied consistently to similar components?
- [ ] Do color contrast ratios meet standards uniformly?
- [ ] Are keyboard navigation patterns consistent?
- [ ] Are screen reader announcements consistent for similar state changes?
- [ ] Do touch targets meet minimum size requirements consistently?

#### Motion and Animation Consistency
- [ ] Do equivalent transitions use the same duration and easing?
- [ ] Are entrance/exit animations consistent for similar elements?
- [ ] Do loading indicators follow the same animation pattern?
- [ ] Are hover/focus micro-interactions consistent across components?

## Resolution Strategies

### Strategy 1: Pick the Best, Apply Everywhere
When multiple variants exist for the same pattern:
1. Evaluate which variant is the best (most usable, most accessible, most consistent with the system)
2. Document it as the standard
3. Apply it to all screens
4. Remove all other variants

### Strategy 2: Define a Decision Tree
When variation is sometimes justified:
1. Define the conditions under which each variant is appropriate
2. Document the decision tree
3. Verify that current usage matches the decision tree
4. Fix any usage that doesn't match

### Strategy 3: Create a Missing Pattern
When no good variant exists:
1. Design the standard pattern from scratch
2. Follow the design system's visual language
3. Document it with usage guidelines
4. Apply it to all affected screens

## Red Flags
- Same action, different style
- Same state, different behavior
- Different labels for the same concept
- Repeated use of ad-hoc UI patterns
- Inconsistent empty states
- Inconsistent filter or search behavior
- Visual polish hiding interaction inconsistency
- Accessibility passing on some screens but failing on others
- Animation present in some flows but absent in equivalent ones
- Error handling that varies without clear reason
