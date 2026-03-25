# Example Output: UX Consistency Audit — B2B CRM Platform

## Audit Summary

**Product:** B2B CRM platform (sales pipeline, contacts, reporting)  
**Screens Audited:** 8 (Dashboard, Pipeline, Contact List, Contact Detail, Deal Detail, Reports, Settings, Onboarding)  
**Overall Consistency Score:** 54/100 — Significant inconsistencies across core interaction patterns

---

## Pattern Consistency Matrix

| Pattern | Dashboard | Pipeline | Contacts | Contact Detail | Deal Detail | Reports | Settings | Onboarding |
|---------|-----------|----------|----------|----------------|-------------|---------|----------|------------|
| Navigation | ✅ | ✅ | ✅ | ⚠️ Back arrow | ⚠️ Back arrow | ✅ | ❌ Different sidebar | ✅ |
| Loading | Skeleton | Spinner | Skeleton | None | Spinner | Full overlay | None | None |
| Empty state | ✅ Illustrated | ❌ None | ✅ Illustrated | N/A | N/A | ❌ Blank | N/A | N/A |
| Error handling | Toast | Toast | Inline | None | Modal | Inline | Toast | None |
| Form validation | N/A | On-blur | N/A | On-submit | On-blur | N/A | On-blur | On-submit |
| Button placement | Right-aligned | Right-aligned | Right-aligned | Left-aligned | Left-aligned | Center | Right-aligned | Center |
| Modal pattern | Centered | Slide-in | Centered | N/A | Slide-in | N/A | Centered | N/A |

---

## Critical Inconsistencies

### 1. Loading States — 4 Different Patterns (Severity: High)

**Finding:** The application uses four different loading approaches with no clear logic for when each applies:
- **Dashboard:** Skeleton screens for each card — good, feels fast
- **Pipeline:** Centered spinner with overlay — feels slow, blocks interaction
- **Contact List:** Skeleton screens — consistent with dashboard
- **Reports:** Full-page overlay with spinner — most disruptive, blocks navigation

**Impact:** Users cannot predict how the app will behave during loading. The inconsistency creates a feeling of multiple products stitched together.

**Recommendation:** Standardize on skeleton screens for content areas and inline spinners for actions:

| Context | Loading Pattern |
|---------|----------------|
| Page/section content | Skeleton screen matching content structure |
| Data table refresh | Keep current data visible, show progress bar at top |
| Button action | Inline spinner replacing button text, button disabled |
| Background save | No visible loading — show success toast on completion |
| Navigation | Instant transition, skeleton on target page |

---

### 2. Form Validation Timing — Mixed Approaches (Severity: High)

**Finding:** Forms across the app use two different validation strategies:
- **On-blur validation:** Pipeline, Settings — validates each field when user leaves it
- **On-submit validation:** Contact Detail, Onboarding — validates all fields when form is submitted

**Impact:** Users learn one pattern and are surprised by the other. On-submit validation in Contact Detail is particularly frustrating because the form has 12+ fields — users fill everything out only to discover errors at the top.

**Recommendation:** Standardize on **on-blur validation with on-submit re-validation**:
- Validate each field when the user leaves it (immediate feedback)
- Re-validate all fields on submit (catch any missed validations)
- Show error messages directly below the field using `color.text.error` and `typography.body.sm`
- Scroll to first error on submit if errors exist above the viewport

---

### 3. Detail View Navigation — Inconsistent Back Pattern (Severity: Medium)

**Finding:** Contact Detail and Deal Detail use a back arrow in the top-left corner to return to the list view. All other screens use the sidebar navigation. The back arrow replaces the page title position, creating a layout shift.

**Impact:** Users on detail views lose the familiar navigation landmark. The back arrow is also not keyboard-accessible (no focus state, no `aria-label`).

**Recommendation:**
- Keep the sidebar visible on detail views (don't hide it)
- Add breadcrumbs below the page header: `Contacts > Jane Doe` / `Deals > Acme Corp`
- Remove the standalone back arrow — breadcrumbs serve the same purpose with better context
- Ensure breadcrumbs are keyboard-navigable with proper `aria-label="Breadcrumb"`

---

### 4. Button Placement — Left vs Right vs Center (Severity: Medium)

**Finding:**
- List views and Settings: Primary action buttons right-aligned (consistent)
- Detail views: Primary action buttons left-aligned (inconsistent)
- Reports and Onboarding: Buttons centered (inconsistent)

**Impact:** Users must visually search for the primary action on each screen. This adds cognitive load and slows task completion.

**Recommendation:** Standardize button placement:

| Context | Primary Button Position |
|---------|------------------------|
| Page-level actions (Create, Export) | Top-right of content area |
| Form actions (Save, Cancel) | Bottom-right of form, Cancel left of Save |
| Modal actions (Confirm, Cancel) | Bottom-right of modal, Cancel left of Confirm |
| Wizard/Onboarding steps | Bottom-right, with Back button bottom-left |

---

### 5. Empty States — Inconsistent Treatment (Severity: Medium)

**Finding:**
- Dashboard and Contact List have well-designed empty states with illustrations and CTAs
- Pipeline has no empty state — shows a blank kanban board with column headers only
- Reports shows a completely blank white area with no guidance

**Impact:** New users hitting the Pipeline or Reports screens with no data receive no guidance on what to do next. This is a critical onboarding gap.

**Recommendation:** Every screen that can be empty must have:
1. A purposeful illustration or icon (not decorative — informational)
2. A clear headline explaining the state: "No deals in your pipeline yet"
3. A description with guidance: "Create your first deal to start tracking your sales pipeline."
4. A primary CTA button: "Create Deal"
5. Optional: link to documentation or help

---

### 6. Modal vs Slide-in Panel — No Clear Rule (Severity: Low)

**Finding:**
- Dashboard and Contact List use centered modals for create/edit actions
- Pipeline and Deal Detail use slide-in panels from the right
- No documented rule for when to use which pattern

**Impact:** Minor — both patterns work. But the inconsistency signals lack of design governance.

**Recommendation:** Define a clear rule:

| Action Type | Pattern |
|-------------|---------|
| Quick create/edit (≤5 fields) | Centered modal |
| Complex create/edit (>5 fields) | Slide-in panel (keeps context visible) |
| Confirmation/destructive action | Centered modal (small, focused) |
| Detail preview | Slide-in panel |

---

## Interaction Pattern Inventory

### Patterns That Are Consistent ✅
- **Typography hierarchy** — Headings, body text, and labels use the same scale across all screens
- **Color usage** — Status colors (success, warning, error) are consistent
- **Icon style** — All icons use the same stroke-based icon set
- **Table row actions** — All tables use the same three-dot menu pattern

### Patterns That Need Standardization ⚠️
- Loading states (4 patterns → 1 standard)
- Form validation (2 approaches → 1 standard)
- Button placement (3 positions → 1 rule set)
- Empty states (2 good, 2 missing → all screens covered)
- Modal vs slide-in (no rule → clear decision tree)
- Back navigation (arrow vs sidebar → breadcrumbs)

---

## Priority Action Plan

| Priority | Issue | Effort | Impact |
|----------|-------|--------|--------|
| 🔴 P1 | Standardize loading states | Medium | High — affects perceived performance |
| 🔴 P1 | Standardize form validation | Medium | High — affects task completion |
| 🟡 P2 | Fix empty states for Pipeline and Reports | Low | High — affects onboarding |
| 🟡 P2 | Standardize button placement | Low | Medium — reduces cognitive load |
| 🟢 P3 | Replace back arrows with breadcrumbs | Low | Medium — improves navigation |
| 🟢 P3 | Define modal vs slide-in rule | Low | Low — governance improvement |

---

## Projected Score After Fixes

| Category | Current | After P1 | After P2 | After P3 |
|----------|---------|----------|----------|----------|
| Loading consistency | 3/10 | 9/10 | 9/10 | 9/10 |
| Form patterns | 4/10 | 9/10 | 9/10 | 9/10 |
| Navigation | 6/10 | 6/10 | 6/10 | 9/10 |
| Empty states | 5/10 | 5/10 | 9/10 | 9/10 |
| Button placement | 5/10 | 5/10 | 9/10 | 9/10 |
| Modal patterns | 6/10 | 6/10 | 6/10 | 8/10 |
| **Overall** | **54/100** | **68/100** | **80/100** | **89/100** |
