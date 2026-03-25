# Example: Form Redesign Workflow

This example demonstrates how to use the Premium UI Plugin to redesign a complex form that currently feels inconsistent and unprofessional.

## Scenario

You have a multi-step onboarding form for a B2B SaaS product. The form was built by different developers over time and has accumulated inconsistencies: different input styles, mixed validation patterns, inconsistent spacing, and no clear visual hierarchy. Users frequently abandon the form at step 3 of 5.

## Step-by-Step Workflow

### 1. Audit Current Consistency

Use `ux-consistency-audit` to identify all inconsistencies:

```
Audit our onboarding form (5 steps) for UX consistency.
Focus on:
- Input field styles (are they all the same?)
- Validation patterns (when do errors appear?)
- Button placement (where are Next/Back/Skip?)
- Spacing between fields and sections
- Error message format and positioning
- Loading states during form submission
```

### 2. Define Form Component Standards

Use `ui-component-design` to establish unified form components:

```
Design a unified form field system for our onboarding flow.
Components needed: TextInput, Select, Checkbox, RadioGroup, FileUpload.
Requirements:
- All inputs must be 40px height with consistent border treatment
- Labels above inputs, helper text below
- Error messages below input in red, with error icon
- Required fields marked with asterisk after label
- Disabled and read-only states must be visually distinct
- On-blur validation with on-submit re-validation
```

### 3. Redesign the Form Layout

Use `screen-composition-design` for each step:

```
Redesign step 1 of our onboarding form: "Company Information"
Fields: Company name, Industry (select), Company size (radio), Website URL
Layout requirements:
- Maximum 720px form width
- 2-column grid for short fields, full-width for long fields
- Clear section heading with step indicator (1/5)
- Progress bar at the top
- Actions: [Back] [Skip] [Continue] — right-aligned
```

### 4. Refine to Premium Quality

Use `premium-ui-refinement` to polish the form:

```
Refine our onboarding form to premium quality.
Current issues:
- All fields have equal visual weight (no hierarchy)
- Spacing between fields varies (12px, 16px, 20px)
- Step indicator is a plain "Step 1 of 5" text
- No visual feedback when completing a step
- The form feels like a government form, not a premium product

Make it feel intentional, calm, and confidence-inspiring.
```

### 5. Ensure Accessibility

Use `accessibility` to audit the form:

```
Audit our onboarding form for accessibility.
Check:
- All fields have proper label associations
- Error messages are announced by screen readers
- Tab order is logical through all 5 steps
- Required fields are communicated to assistive technology
- Color is not the only indicator of errors
- The form works entirely with keyboard navigation
```

### 6. Define Responsive Behavior

Use `responsive-adaptive-design` for mobile form experience:

```
Define responsive behavior for our 5-step onboarding form.
Desktop: 2-column layout, 720px max-width, inline step indicator
Tablet: 2-column layout, full-width
Mobile: Single column, sticky bottom action bar, simplified step indicator
Ensure touch targets are 44px minimum on mobile.
```

### 7. Critical Review

Use `design-critique` for final quality check:

```
Critique our redesigned onboarding form. Be strict.
Does it feel premium? Is the hierarchy clear?
Would a user feel confident entering their company information?
Is the 5-step flow clear and non-intimidating?
Check: spacing discipline, typography hierarchy, interaction feedback,
error handling, and overall form UX maturity.
```

## Expected Outcome

After completing this workflow, you should have:

- Unified form components with consistent styling across all 5 steps
- Standardized validation pattern (on-blur + on-submit)
- Clear visual hierarchy within each step
- Consistent spacing using design system tokens
- A progress indicator that communicates completion
- Proper accessibility: labels, error announcements, keyboard navigation
- Responsive layout: 2-column on desktop, single column on mobile
- A form that feels intentional and premium, not assembled from parts

## Key Principle

Forms are where users commit to your product. A form that feels inconsistent or confusing directly undermines trust. Premium form design is not about decoration — it is about clarity, consistency, and confidence. Every field, every label, every error message should feel like it belongs to the same carefully designed system.
