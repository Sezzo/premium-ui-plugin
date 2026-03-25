# Accessibility Rules

## WCAG 2.2 Quick Reference

### Level AA Requirements (Minimum Standard)

#### Perceivable

| Criterion | ID | Requirement |
|-----------|-----|-------------|
| Text Alternatives | 1.1.1 | All non-text content has text alternative |
| Captions | 1.2.2 | All prerecorded audio has captions |
| Audio Description | 1.2.5 | Video has audio description |
| Info and Relationships | 1.3.1 | Structure conveyed through semantic markup |
| Meaningful Sequence | 1.3.2 | Reading order is logical and intuitive |
| Sensory Characteristics | 1.3.3 | Instructions don't rely solely on shape, size, or location |
| Orientation | 1.3.4 | Content not restricted to single orientation |
| Input Purpose | 1.3.5 | Input fields identify their purpose (autocomplete) |
| Contrast (Text) | 1.4.3 | 4.5:1 for normal text, 3:1 for large text |
| Resize Text | 1.4.4 | Text resizable to 200% without loss |
| Images of Text | 1.4.5 | Use real text, not images of text |
| Contrast (Non-text) | 1.4.11 | 3:1 for UI components and graphical objects |
| Text Spacing | 1.4.12 | Content adapts to user text spacing overrides |
| Content on Hover/Focus | 1.4.13 | Hoverable, dismissible, persistent |

#### Operable

| Criterion | ID | Requirement |
|-----------|-----|-------------|
| Keyboard | 2.1.1 | All functionality available via keyboard |
| No Keyboard Trap | 2.1.2 | Focus can always be moved away |
| Skip Navigation | 2.4.1 | Skip to main content link |
| Page Titled | 2.4.2 | Pages have descriptive titles |
| Focus Order | 2.4.3 | Focus order preserves meaning |
| Link Purpose | 2.4.4 | Link purpose clear from text or context |
| Multiple Ways | 2.4.5 | Multiple ways to find pages |
| Headings and Labels | 2.4.6 | Headings and labels are descriptive |
| Focus Visible | 2.4.7 | Keyboard focus indicator is visible |
| Focus Not Obscured | 2.4.11 | Focused element not fully hidden |
| Dragging Movements | 2.5.7 | Drag actions have single-pointer alternative |
| Target Size | 2.5.8 | Touch targets minimum 24×24px (44×44px recommended) |

#### Understandable

| Criterion | ID | Requirement |
|-----------|-----|-------------|
| Language of Page | 3.1.1 | Page language identified in HTML |
| Language of Parts | 3.1.2 | Language changes identified |
| On Focus | 3.2.1 | No unexpected context change on focus |
| On Input | 3.2.2 | No unexpected context change on input |
| Consistent Navigation | 3.2.3 | Navigation consistent across pages |
| Consistent Identification | 3.2.4 | Same function = same label |
| Error Identification | 3.3.1 | Errors clearly identified and described |
| Labels or Instructions | 3.3.2 | Input fields have labels/instructions |
| Error Suggestion | 3.3.3 | Error messages suggest corrections |
| Error Prevention | 3.3.4 | Reversible, checked, or confirmed for legal/financial |

#### Robust

| Criterion | ID | Requirement |
|-----------|-----|-------------|
| Parsing | 4.1.1 | Valid HTML (deprecated in 2.2 but still good practice) |
| Name, Role, Value | 4.1.2 | All UI components expose name, role, value |
| Status Messages | 4.1.3 | Status messages announced without focus change |

## Semantic HTML Patterns

### Use Native Elements First

```
✅ <button>           → clickable actions
✅ <a href>           → navigation links
✅ <input type="..."> → form inputs
✅ <select>           → dropdowns
✅ <dialog>           → modals
✅ <details>/<summary> → accordions
✅ <nav>              → navigation regions
✅ <main>             → primary content
✅ <aside>            → complementary content
✅ <header>/<footer>  → page/section headers and footers

❌ <div onclick>      → never for clickable elements
❌ <span tabindex="0"> → never as a button replacement
❌ <div role="button"> → only when native <button> is impossible
```

### Heading Hierarchy

- One `<h1>` per page
- No skipped levels (h1 → h3 without h2)
- Headings reflect content structure, not visual styling
- Use CSS for visual sizing, HTML for semantic level

### Landmark Regions

Every page must have:
- `<main>` — primary content (exactly one)
- `<nav>` — navigation (label if multiple)
- `<header>` — page header
- `<footer>` — page footer
- `<aside>` — sidebar/complementary (if present)

## Keyboard Navigation

### Focus Management Rules

1. **Tab order** matches visual reading order (left-to-right, top-to-bottom)
2. **Focus indicator** must be visible: minimum 2px outline, contrast ratio 3:1 against adjacent colors
3. **Focus ring style**: `outline: 2px solid [color.border.focus]; outline-offset: 2px`
4. **Skip link**: First focusable element on every page, visible on focus
5. **Modal focus trap**: Tab cycles within modal; Escape closes; focus returns to trigger on close
6. **Roving tabindex**: For composite widgets (tabs, toolbars, menus) — one Tab stop, arrow keys navigate within

### Common Keyboard Patterns

| Component | Keys | Behavior |
|-----------|------|----------|
| Button | Enter, Space | Activate |
| Link | Enter | Navigate |
| Checkbox | Space | Toggle |
| Radio group | Arrow keys | Move selection |
| Tab panel | Arrow keys | Switch tabs |
| Menu | Arrow keys, Enter, Escape | Navigate, select, close |
| Dialog | Tab (trapped), Escape | Navigate within, close |
| Combobox | Arrow keys, Enter, Escape | Navigate options, select, close |
| Accordion | Enter, Space | Toggle section |

## Color & Contrast

### Minimum Ratios

| Element | Ratio | Standard |
|---------|-------|----------|
| Normal text (< 18px or < 14px bold) | 4.5:1 | AA |
| Large text (≥ 18px or ≥ 14px bold) | 3:1 | AA |
| UI components (borders, icons) | 3:1 | AA |
| Graphical objects | 3:1 | AA |
| Enhanced (normal text) | 7:1 | AAA |
| Enhanced (large text) | 4.5:1 | AAA |

### Rules

- Never use color alone to convey information (add icons, patterns, or text)
- Error states: red color + error icon + text description
- Success states: green color + checkmark icon + text description
- Links: underline or other non-color indicator in addition to color
- Charts: use patterns/shapes in addition to color for data series
- Test with simulated color blindness (protanopia, deuteranopia, tritanopia)

## ARIA Patterns

### When to Use ARIA

1. **First**: Can you use a native HTML element? → Use it.
2. **Second**: Can you add a role to an existing element? → Do it.
3. **Third**: Create a custom widget with full ARIA support → Last resort.

### Common ARIA Patterns

| Pattern | Key Attributes |
|---------|---------------|
| Alert | `role="alert"`, `aria-live="assertive"` |
| Dialog | `role="dialog"`, `aria-modal="true"`, `aria-labelledby` |
| Tab Panel | `role="tablist"`, `role="tab"`, `role="tabpanel"`, `aria-selected` |
| Combobox | `role="combobox"`, `aria-expanded"`, `aria-controls`, `aria-activedescendant` |
| Menu | `role="menu"`, `role="menuitem"`, `aria-expanded` |
| Tree | `role="tree"`, `role="treeitem"`, `aria-expanded`, `aria-level` |
| Live Region | `aria-live="polite"` or `"assertive"`, `aria-atomic` |
| Loading | `aria-busy="true"`, status announcement on complete |

### ARIA Anti-Patterns

- `aria-label` on non-interactive `<div>` or `<span>` — screen readers may ignore it
- `role="button"` without keyboard handler — broken for keyboard users
- `aria-hidden="true"` on focusable elements — creates ghost focus
- Redundant ARIA: `<button role="button">` — unnecessary
- `aria-live` on large content areas — causes excessive announcements

## Form Accessibility

### Required Pattern

```html
<label for="email">Email address</label>
<input 
  id="email" 
  type="email" 
  aria-describedby="email-hint email-error"
  aria-required="true"
  aria-invalid="false"
  autocomplete="email"
/>
<span id="email-hint">We'll never share your email</span>
<span id="email-error" role="alert" hidden>Please enter a valid email</span>
```

### Rules

- Every input has a visible `<label>` with matching `for`/`id`
- Required fields: `aria-required="true"` + visual indicator (not just asterisk color)
- Error messages: `role="alert"` or `aria-live="assertive"`, linked via `aria-describedby`
- Group related fields with `<fieldset>` and `<legend>`
- Use appropriate `autocomplete` values for personal data fields
- Inline validation: announce errors as they occur, don't wait for submit

## Motion & Animation

### Rules

- Respect `prefers-reduced-motion: reduce` — disable or minimize all non-essential animation
- Essential animations (loading spinners): reduce to simple opacity fade
- No content that flashes more than 3 times per second
- Parallax scrolling: disable entirely when reduced motion preferred
- Auto-advancing carousels: provide pause control, stop on hover/focus

### Implementation

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}
```

## Testing Protocol

### Automated (Catches ~30% of Issues)

- axe-core or Lighthouse accessibility audit
- HTML validation
- Color contrast checker
- Heading structure validator

### Manual (Catches ~70% of Issues)

- [ ] Navigate entire page with keyboard only (no mouse)
- [ ] Complete all critical flows with keyboard only
- [ ] Test with screen reader (VoiceOver on Mac, NVDA on Windows)
- [ ] Verify all images have meaningful alt text
- [ ] Check focus order matches visual order
- [ ] Verify focus indicator is always visible
- [ ] Test at 200% zoom — no content loss or overlap
- [ ] Test with high contrast mode enabled
- [ ] Test with `prefers-reduced-motion: reduce`
- [ ] Verify all form errors are announced by screen reader
- [ ] Check all interactive elements have accessible names
- [ ] Verify no content is conveyed by color alone

## WCAG Level Prioritization

### Level A — Baseline (Must Have)
These are non-negotiable. Failure at Level A means the product is fundamentally inaccessible.

**Priority A criteria to fix first:**
1. **Keyboard access (2.1.1)** — All functionality must work with keyboard
2. **No keyboard trap (2.1.2)** — Focus must never get stuck
3. **Text alternatives (1.1.1)** — All images, icons, and charts need alt text
4. **Info and relationships (1.3.1)** — Semantic HTML, proper headings, form labels
5. **Error identification (3.3.1)** — Errors must be clearly described

### Level AA — Standard (Should Have)
This is the target for most products. Level AA satisfies most legal requirements.

**Priority AA criteria:**
1. **Color contrast (1.4.3, 1.4.11)** — Text 4.5:1, UI components 3:1
2. **Focus visible (2.4.7)** — Keyboard focus must be clearly visible
3. **Error suggestion (3.3.3)** — Error messages must suggest how to fix
4. **Status messages (4.1.3)** — Dynamic updates announced to screen readers
5. **Target size (2.5.8)** — Touch targets minimum 24×24px

### Level AAA — Enhanced (Nice to Have)
Target selectively based on audience needs. Full AAA compliance is rarely required.

**Valuable AAA criteria to consider:**
- Enhanced contrast (1.4.6) — 7:1 for normal text
- Sign language (1.2.6) — For video-heavy products
- Abbreviations (3.1.4) — For technical/medical products
- Reading level (3.1.5) — For public-facing government/health products

## Recommended Tool Stack

These are recommendations — choose based on your workflow and tech stack.

### Automated Testing Tools

| Tool | Type | Best For | Cost |
|------|------|----------|------|
| **axe DevTools** | Browser extension + CI | Comprehensive automated testing, CI/CD integration | Free (core) / Paid (pro) |
| **Lighthouse** | Built into Chrome | Quick audits during development | Free |
| **WAVE** | Browser extension | Visual accessibility evaluation with inline annotations | Free |
| **eslint-plugin-jsx-a11y** | ESLint plugin | Catching JSX accessibility issues at build time | Free |
| **pa11y** | CLI / CI tool | Automated testing in CI pipelines | Free |

### Manual Testing Tools

| Tool | Type | Best For | Cost |
|------|------|----------|------|
| **NVDA** | Screen reader (Windows) | Testing screen reader experience on Windows | Free |
| **VoiceOver** | Screen reader (macOS/iOS) | Testing on Apple platforms | Free (built-in) |
| **TalkBack** | Screen reader (Android) | Testing on Android devices | Free (built-in) |
| **Colour Contrast Analyser** | Desktop app | Manual contrast checking with eyedropper | Free |
| **Accessibility Insights** | Browser extension | Guided manual testing with checklists | Free |

### Design Tools

| Tool | Type | Best For | Cost |
|------|------|----------|------|
| **Stark** | Figma/Sketch plugin | Contrast checking and vision simulation in design tools | Free / Paid |
| **A11y Annotation Kit** | Figma library | Annotating designs with accessibility specs | Free |

### Recommended Minimum Setup
1. **axe DevTools** browser extension for development
2. **eslint-plugin-jsx-a11y** for build-time checks (if using React/JSX)
3. **NVDA** or **VoiceOver** for manual screen reader testing
4. **Lighthouse** for periodic audits

## Legal Context

**Note:** This section provides general awareness, not legal advice. Consult legal counsel for your specific situation and jurisdiction.

### European Accessibility Act (EAA)
- **Effective:** June 28, 2025
- **Scope:** Products and services sold in the EU, including websites, mobile apps, e-commerce, and digital services
- **Standard:** References EN 301 549, which maps to WCAG 2.1 Level AA
- **Applies to:** Both B2C and B2B products offered in EU markets
- **Enforcement:** National authorities in each EU member state

### Americans with Disabilities Act (ADA)
- **Scope:** US businesses, including web-based services
- **Standard:** No explicit WCAG level mandated, but courts consistently reference WCAG 2.0/2.1 Level AA
- **Risk:** Increasing litigation — thousands of web accessibility lawsuits filed annually
- **Recommendation:** Target WCAG 2.2 Level AA to minimize legal risk

### EN 301 549
- **Scope:** European standard for ICT accessibility
- **Required for:** Public sector procurement in the EU
- **Standard:** Maps directly to WCAG 2.1 Level AA with additional requirements for software and hardware
- **Relevance:** If your product is sold to government or public sector clients in Europe

### Section 508 (US)
- **Scope:** US federal agencies and their contractors
- **Standard:** References WCAG 2.0 Level AA
- **Relevance:** Required if your product is used by or sold to US government agencies

### Practical Recommendation
Target **WCAG 2.2 Level AA** as the baseline for all products. This:
- Satisfies the EAA requirements
- Meets the de facto ADA standard
- Covers EN 301 549 and Section 508
- Represents a responsible, defensible accessibility standard
- Benefits all users, not just those with disabilities
