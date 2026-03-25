# Example Output: Design Critique — SaaS Settings Page

## Critique Summary

**Subject:** Settings page for a B2B project management tool  
**Overall Rating:** 4/10 — Functional but visually undisciplined, inconsistent with system patterns, and lacking premium quality.

---

## Detailed Critique

### 1. Visual Hierarchy — Weak

**Issue:** The page treats all settings sections with equal visual weight. Account settings, notification preferences, and billing information all use identical card containers with identical padding and identical heading sizes.

**Impact:** Users cannot scan the page efficiently. Nothing signals priority or frequency of use. The page reads as a flat list rather than a structured experience.

**Recommendation:** Establish clear hierarchy through differentiated section treatment. Primary settings (account, security) should use prominent cards with `space.xl` padding. Secondary settings (notifications, preferences) should use compact rows. Billing should be visually separated as a distinct zone with a subtle background shift using `color.surface.secondary`.

### 2. Spacing System — Inconsistent

**Issue:** Spacing between form fields alternates between 16px, 20px, and 24px with no discernible logic. The gap between section cards varies between 24px and 32px. Label-to-input spacing is 4px in some places and 8px in others.

**Impact:** The page feels hand-placed rather than system-driven. This erodes trust in the product's attention to detail — exactly the opposite of premium.

**Recommendation:** Enforce a strict spacing scale. Use `space.md` (16px) between form fields within a section, `space.xl` (32px) between sections, and `space.xs` (8px) consistently for label-to-input gaps. No exceptions.

### 3. Typography — Underutilized

**Issue:** The page uses only two type styles: a 14px regular for everything and a 16px semi-bold for section headings. No distinction between labels, values, helper text, or descriptions.

**Impact:** Information density feels monotonous. Users must read every word because the typography provides no scanning shortcuts.

**Recommendation:** Apply the full type scale:
- Section headings: `typography.heading.sm` (18px/semibold)
- Field labels: `typography.label.md` (14px/medium)
- Field values: `typography.body.md` (14px/regular)
- Helper text: `typography.body.sm` (12px/regular) in `color.text.tertiary`
- Section descriptions: `typography.body.md` in `color.text.secondary`

### 4. Component Consistency — Broken

**Issue:** The page uses three different input field styles. Text inputs have rounded corners (8px), select dropdowns have sharp corners (0px), and the toggle switches appear to be from a different component library entirely (different height, different active color).

**Impact:** This is the most damaging issue. Mixed component styles signal that the product was assembled from parts rather than designed as a system. It directly undermines perceived quality.

**Recommendation:** Audit every interactive element on this page against the design system component library. All inputs must use `radius.md` (8px), consistent height (`40px`), and the same border treatment (`color.border.default`, 1px). Toggles must match the system toggle component exactly.

### 5. Color Usage — Flat

**Issue:** The page is almost entirely monochrome — white cards on a gray background with black text. The only color is a blue "Save" button. No use of color to indicate status, group related items, or create visual interest.

**Impact:** The page feels administrative and cold. While restraint is good, this crosses into lifeless.

**Recommendation:** Introduce purposeful color accents:
- Use `color.surface.secondary` to differentiate the billing section
- Apply `color.status.success` to verified email/phone indicators
- Use `color.text.secondary` and `color.text.tertiary` to create text hierarchy
- Consider a subtle left-border accent (`color.border.brand`, 2px) on the active/expanded section

### 6. Interaction Feedback — Missing

**Issue:** Form fields have no visible focus state beyond the browser default. The "Save" button has no hover state. There is no indication of unsaved changes. No success/error feedback after saving.

**Impact:** Users operate without confidence. They don't know if their changes registered, if the save worked, or which field they're currently editing.

**Recommendation:** Implement complete interaction states:
- Focus: `border-color: color.border.focus` + `box-shadow: 0 0 0 2px color.focus.ring`
- Hover on save: darken by 8% or use `color.action.primary.hover`
- Unsaved changes: show a subtle banner or dot indicator
- Save success: inline success message with `color.status.success`, auto-dismiss after 3s

### 7. Accessibility — Below Baseline

**Issue:** Form labels are visually present but not programmatically associated with inputs (missing `for`/`id` pairing). The toggle switches lack accessible names. Color contrast on helper text (light gray on white) measures approximately 3.2:1, below the WCAG AA minimum of 4.5:1.

**Recommendation:** Fix label associations, add `aria-label` to all toggles, and adjust helper text to `color.text.tertiary` which must meet 4.5:1 contrast minimum.

---

## Priority Actions

| Priority | Action | Effort |
|----------|--------|--------|
| 🔴 Critical | Fix component consistency (inputs, toggles) | Medium |
| 🔴 Critical | Fix accessibility issues (labels, contrast) | Low |
| 🟡 High | Enforce spacing system | Low |
| 🟡 High | Add interaction feedback states | Medium |
| 🟢 Medium | Improve typography hierarchy | Low |
| 🟢 Medium | Introduce purposeful color usage | Low |
| ⚪ Low | Restructure visual hierarchy of sections | Medium |

---

## Final Verdict

This settings page is functional but not premium. It reads as a developer-built page that was never reviewed by a designer. The component inconsistency alone would be a blocker for any product claiming design quality. The good news: most fixes are systematic (enforce existing tokens, use existing components correctly) rather than requiring new design work. A disciplined pass applying the design system consistently would elevate this page significantly.
