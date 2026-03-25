# Example Output: Accessibility Audit — SaaS Dashboard Application

## Audit Summary

**Product:** B2B project management dashboard  
**Standard:** WCAG 2.2 Level AA  
**Pages Audited:** Dashboard, Task List, Task Detail, Settings, Team View  
**Overall Compliance:** 42% — Significant gaps in keyboard navigation, color contrast, and screen reader support

---

## Findings by WCAG Principle

### Perceivable

#### 1.1 Text Alternatives — Partial Compliance

| Element | Issue | WCAG Criterion | Severity |
|---------|-------|---------------|----------|
| Chart images | No `alt` text on SVG charts — screen readers announce "image" with no context | 1.1.1 Non-text Content (A) | Critical |
| Icon buttons | 12 icon-only buttons without `aria-label` (edit, delete, share, etc.) | 1.1.1 Non-text Content (A) | Critical |
| Avatar images | User avatars use `alt=""` — should use `alt="Jane Doe's avatar"` or be decorative with `role="presentation"` | 1.1.1 Non-text Content (A) | Medium |
| Status indicators | Color-only status dots (green/yellow/red) with no text alternative | 1.1.1 Non-text Content (A) | Critical |

**Recommended fix for charts:**
```html
<!-- Before -->
<svg class="chart">...</svg>

<!-- After -->
<figure role="img" aria-label="Task completion trend: 78% this week, up from 65% last week">
  <svg class="chart" aria-hidden="true">...</svg>
  <figcaption class="sr-only">
    Task completion rate over the last 4 weeks: Week 1: 52%, Week 2: 61%, Week 3: 65%, Week 4: 78%
  </figcaption>
</figure>
```

**Recommended fix for status indicators:**
```html
<!-- Before -->
<span class="status-dot status-dot--green"></span>

<!-- After -->
<span class="status-dot status-dot--green" role="status">
  <span class="sr-only">Active</span>
</span>
```

#### 1.3 Adaptable — Major Gaps

| Issue | Location | WCAG Criterion | Severity |
|-------|----------|---------------|----------|
| No landmark regions | All pages — no `<main>`, `<nav>`, `<aside>` landmarks | 1.3.1 Info and Relationships (A) | High |
| Table not marked up as table | Task list uses `<div>` grid instead of `<table>` | 1.3.1 Info and Relationships (A) | High |
| Form labels missing | Settings page — 4 inputs use placeholder as label | 1.3.1 Info and Relationships (A) | Critical |
| Heading hierarchy broken | H1 → H3 → H2 on Dashboard (skips levels, wrong order) | 1.3.1 Info and Relationships (A) | Medium |

**Recommended landmark structure:**
```html
<body>
  <header role="banner">
    <nav aria-label="Main navigation">...</nav>
  </header>
  <main id="main-content">
    <h1>Dashboard</h1>
    ...
  </main>
  <aside aria-label="Notifications panel">...</aside>
</body>
```

#### 1.4 Distinguishable — Contrast Failures

| Element | Foreground | Background | Ratio | Required | Status |
|---------|-----------|-----------|-------|----------|--------|
| Body text | `#333333` | `#FFFFFF` | 12.6:1 | 4.5:1 | ✅ Pass |
| Secondary text | `#999999` | `#FFFFFF` | 2.8:1 | 4.5:1 | ❌ Fail |
| Placeholder text | `#BBBBBB` | `#FFFFFF` | 1.9:1 | 4.5:1 | ❌ Fail |
| Link text | `#4A90D9` | `#FFFFFF` | 3.6:1 | 4.5:1 | ❌ Fail |
| Button text | `#FFFFFF` | `#4A90D9` | 3.6:1 | 4.5:1 | ❌ Fail |
| Success badge | `#FFFFFF` | `#4CAF50` | 3.0:1 | 4.5:1 | ❌ Fail |
| Disabled text | `#CCCCCC` | `#F5F5F5` | 1.6:1 | 4.5:1 | ❌ Fail |

**Recommended color adjustments:**
```css
/* Fix secondary text: #999999 → #6B6B6B (4.6:1) */
--color-text-secondary: #6B6B6B;

/* Fix link/button color: #4A90D9 → #2563EB (4.6:1 on white) */
--color-action-primary: #2563EB;

/* Fix success badge: use dark text on green background */
.badge--success {
  background: #E8F5E9;           /* Light green background */
  color: #1B5E20;                /* Dark green text — 7.1:1 ratio */
}

/* Fix placeholder: #BBBBBB → #767676 (4.5:1 minimum) */
--color-text-placeholder: #767676;
```

---

### Operable

#### 2.1 Keyboard Accessible — Major Failures

| Issue | Location | WCAG Criterion | Severity |
|-------|----------|---------------|----------|
| Modal has no focus trap | Task detail modal — Tab key moves behind modal | 2.1.1 Keyboard (A) | Critical |
| Custom dropdown not keyboard-operable | Filter dropdowns only respond to mouse | 2.1.1 Keyboard (A) | Critical |
| No skip link | All pages — keyboard users must tab through entire nav | 2.1.1 Keyboard (A) | High |
| Drag-and-drop only | Task board — no keyboard alternative for reordering | 2.1.1 Keyboard (A) | Critical |
| Focus not visible | Custom-styled elements override browser focus ring | 2.4.7 Focus Visible (AA) | High |

**Recommended focus style:**
```css
/* Global focus style — visible, consistent, meets 3:1 contrast */
:focus-visible {
  outline: 2px solid var(--color-focus-ring);    /* #2563EB */
  outline-offset: 2px;
  border-radius: var(--radius-sm);
}

/* Remove default outline only when custom focus is applied */
:focus:not(:focus-visible) {
  outline: none;
}
```

**Recommended skip link:**
```html
<a href="#main-content" class="skip-link">Skip to main content</a>
```
```css
.skip-link {
  position: absolute;
  top: -100%;
  left: var(--space-md);
  padding: var(--space-sm) var(--space-md);
  background: var(--color-surface-default);
  color: var(--color-text-primary);
  border: 2px solid var(--color-focus-ring);
  border-radius: var(--radius-md);
  font-size: var(--typography-body-md);
  font-weight: 600;
  z-index: 9999;
  transition: top 150ms ease;
}

.skip-link:focus {
  top: var(--space-md);
}
```

**Recommended keyboard alternative for drag-and-drop:**
```html
<!-- Add keyboard reorder controls -->
<div role="listitem" aria-label="Task: Design review, position 3 of 8">
  <span class="task-title">Design review</span>
  <div class="reorder-controls" aria-label="Reorder">
    <button aria-label="Move up" onclick="moveTask(-1)">↑</button>
    <button aria-label="Move down" onclick="moveTask(1)">↓</button>
  </div>
</div>
```

#### 2.4 Navigable — Partial Compliance

| Issue | WCAG Criterion | Severity |
|-------|---------------|----------|
| Page titles are all "App Name" — no page-specific titles | 2.4.2 Page Titled (A) | Medium |
| Focus order illogical on Settings page (jumps between sections) | 2.4.3 Focus Order (A) | High |
| No visible indication of current page in navigation | 2.4.8 Location (AAA) | Low |

---

### Understandable

#### 3.1 Readable

| Issue | WCAG Criterion | Severity |
|-------|---------------|----------|
| No `lang` attribute on `<html>` | 3.1.1 Language of Page (A) | Medium |
| Abbreviations not explained ("ETA", "ROI", "KPI") | 3.1.4 Abbreviations (AAA) | Low |

#### 3.2 Predictable

| Issue | WCAG Criterion | Severity |
|-------|---------------|----------|
| Filter dropdowns auto-submit on change (no "Apply" button) | 3.2.2 On Input (A) | Medium |
| Settings auto-save without confirmation | 3.2.2 On Input (A) | Medium |

#### 3.3 Input Assistance

| Issue | WCAG Criterion | Severity |
|-------|---------------|----------|
| Error messages are generic ("Invalid input") — no specific guidance | 3.3.3 Error Suggestion (AA) | High |
| No error prevention for destructive actions (delete task has no undo) | 3.3.4 Error Prevention (AA) | High |

---

### Robust

#### 4.1 Compatible

| Issue | WCAG Criterion | Severity |
|-------|---------------|----------|
| Duplicate `id` attributes on Dashboard (3 instances) | 4.1.1 Parsing (A) | Medium |
| Custom components missing ARIA roles (`role="tablist"`, `role="dialog"`) | 4.1.2 Name, Role, Value (A) | High |
| Dynamic content updates not announced (new tasks appear silently) | 4.1.3 Status Messages (AA) | High |

**Recommended live region for dynamic updates:**
```html
<div aria-live="polite" aria-atomic="false" class="sr-only" id="status-announcer">
  <!-- Dynamically updated -->
</div>
```
```javascript
// When new task is added:
document.getElementById('status-announcer').textContent = 'New task "Design review" added to backlog';
```

---

## Compliance Summary

| WCAG Level | Total Criteria | Pass | Fail | N/A | Compliance |
|-----------|---------------|------|------|-----|------------|
| Level A | 30 | 12 | 14 | 4 | 46% |
| Level AA | 20 | 8 | 9 | 3 | 47% |
| Level AAA | 28 | 3 | 6 | 19 | 33% |

---

## Recommended Tool Stack

These tools are recommendations — choose based on your workflow:

| Tool | Purpose | Integration |
|------|---------|-------------|
| **axe DevTools** (recommended) | Automated accessibility testing in browser | Browser extension, CI/CD integration |
| **WAVE** | Visual accessibility evaluation | Browser extension |
| **Lighthouse** | General audit including accessibility | Built into Chrome DevTools |
| **NVDA** (recommended) | Free screen reader for Windows testing | Desktop application |
| **VoiceOver** | Screen reader for macOS/iOS testing | Built into macOS |
| **Colour Contrast Analyser** | Manual contrast checking with eyedropper | Desktop application |
| **eslint-plugin-jsx-a11y** | Catch accessibility issues in JSX at build time | ESLint plugin |

---

## Priority Remediation Plan

| Phase | Focus | Issues Fixed | Effort |
|-------|-------|-------------|--------|
| **Phase 1 (Critical)** | Focus trap in modals, keyboard navigation for dropdowns, icon button labels, skip link | 6 critical issues | 1–2 weeks |
| **Phase 2 (High)** | Color contrast fixes, landmark regions, focus styles, form labels | 8 high issues | 2–3 weeks |
| **Phase 3 (Medium)** | Heading hierarchy, page titles, error messages, ARIA roles | 7 medium issues | 2 weeks |
| **Phase 4 (Ongoing)** | Screen reader testing, keyboard testing in CI, automated axe checks | Prevention | Ongoing |

---

## Legal Context

**Note:** This section provides general awareness, not legal advice. Consult legal counsel for your specific situation.

- **European Accessibility Act (EAA):** Requires digital products and services to be accessible by June 2025. Applies to B2B products sold in the EU.
- **ADA (Americans with Disabilities Act):** US courts have increasingly applied ADA requirements to web applications. No explicit WCAG level mandated, but AA is the de facto standard.
- **EN 301 549:** European standard referencing WCAG 2.1 AA for ICT products. Required for public sector procurement.

**Recommendation:** Target WCAG 2.2 Level AA as the baseline. This satisfies most regulatory requirements and represents a responsible accessibility standard.
