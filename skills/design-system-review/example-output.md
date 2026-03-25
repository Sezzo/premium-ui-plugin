# Example Output: Design System Review — E-Commerce Platform

## Review Summary

**System:** Design system for a mid-size e-commerce platform (fashion retail)  
**Maturity Level:** Level 2 — Emerging (structured but incomplete)  
**Overall Score:** 52/100

---

## Token Foundation — Score: 6/10

### What Exists
- Color palette defined with 12 brand colors and 5 neutrals
- Typography scale with 4 sizes (sm, md, lg, xl)
- Spacing uses multiples of 8px (8, 16, 24, 32, 48)

### What's Missing
- **No semantic color tokens.** Colors are referenced by name (`blue-500`, `gray-200`) rather than purpose (`color.action.primary`, `color.surface.default`). This means a brand color change requires updating every usage manually.
- **No elevation/shadow tokens.** Shadows are hardcoded per component with inconsistent values (cards use `0 2px 8px rgba(0,0,0,0.1)`, dropdowns use `0 4px 16px rgba(0,0,0,0.15)`).
- **Typography lacks line-height and letter-spacing definitions.** Only font-size and weight are tokenized.
- **No border-radius tokens.** Components use 4px, 8px, and 12px without a defined scale.

### Recommendation
Introduce a three-tier token architecture: primitive → semantic → component. Map every hardcoded value to a semantic token. Priority: semantic colors first (highest impact), then elevation, then radius.

---

## Component Library — Score: 5/10

### Coverage Assessment

| Component | Exists | States Complete | Variants | System-Integrated |
|-----------|--------|-----------------|----------|-------------------|
| Button | ✅ | ⚠️ Missing loading, focus | 3 (primary, secondary, ghost) | ⚠️ Uses hardcoded colors |
| Input | ✅ | ⚠️ Missing error, disabled | 1 | ❌ Inconsistent with selects |
| Select | ✅ | ❌ Default only | 1 | ❌ Different library |
| Card | ✅ | ✅ | 2 (product, content) | ⚠️ Hardcoded shadows |
| Modal | ✅ | ⚠️ No loading state | 1 | ⚠️ Hardcoded overlay |
| Table | ❌ | — | — | — |
| Tabs | ✅ | ⚠️ No disabled state | 1 | ✅ |
| Badge | ✅ | ✅ | 4 (status colors) | ⚠️ Hardcoded colors |
| Toast | ❌ | — | — | — |
| Tooltip | ❌ | — | — | — |
| Pagination | ✅ | ⚠️ No disabled state | 1 | ⚠️ Hardcoded spacing |
| Navigation | ✅ | ⚠️ No active state | 1 | ❌ Inconsistent with system |

### Critical Gaps
- **No table component** despite the platform having product listings, order history, and admin views. Tables are built ad-hoc per page.
- **No toast/notification component.** Success and error messages use three different patterns across the app.
- **Input and Select are visually mismatched.** Different heights (40px vs 36px), different border radius (8px vs 4px), different border colors.

### Recommendation
Prioritize: (1) Unify input/select components immediately — this is the most visible inconsistency. (2) Build a table component — it's used on 60%+ of pages. (3) Create a toast component to replace ad-hoc notification patterns.

---

## Pattern Consistency — Score: 5/10

### Identified Inconsistencies

**Form Patterns:**
- Product search uses inline validation; checkout uses on-submit validation; account settings uses on-blur validation
- Three different error message styles: red text below field, red border only, tooltip-style popover

**Navigation Patterns:**
- Main nav uses hover-reveal dropdowns; mobile nav uses slide-in drawer; admin nav uses persistent sidebar
- Breadcrumbs appear on product pages but not on category pages or account pages

**Loading Patterns:**
- Product grid uses skeleton screens
- Cart uses a centered spinner
- Checkout uses a full-page overlay
- Account pages show no loading state at all

### Recommendation
Define pattern standards for: form validation (pick one approach), loading states (skeleton for content areas, inline spinner for actions), and navigation (consistent breadcrumb rules). Document these as pattern guidelines alongside the component library.

---

## Naming & Structure — Score: 6/10

### Strengths
- Component file naming is consistent (`ComponentName.tsx`, `ComponentName.styles.ts`)
- Props follow a predictable pattern (`variant`, `size`, `disabled`)

### Weaknesses
- **Token naming is inconsistent.** Mix of `blue-500` (primitive), `primary` (vague semantic), and `btn-bg` (component-specific) at the same level.
- **No documented naming convention.** New contributors guess at naming patterns.
- **CSS class naming mixes BEM and utility classes** within the same components.

### Recommendation
Establish and document a naming convention: `{category}.{property}.{variant}.{state}` for tokens (e.g., `color.action.primary.default`). Choose one CSS methodology and migrate incrementally.

---

## Documentation — Score: 4/10

### What Exists
- README with installation instructions
- Storybook with basic component demos

### What's Missing
- **No usage guidelines** — when to use which component variant
- **No do/don't examples** — common misuse patterns
- **No composition examples** — how components work together
- **No token documentation** — what each token means and when to use it
- **No contribution guidelines** — how to add new components consistently
- **No changelog** — no record of system changes

### Recommendation
Start with usage guidelines for the 5 most-used components. Add do/don't examples for each. Create a token reference page. This alone would move documentation from 4/10 to 7/10.

---

## Accessibility Baseline — Score: 4/10

### Findings
- **Color contrast:** 3 of 5 text colors fail WCAG AA (4.5:1) on their intended backgrounds
- **Focus states:** Only buttons have visible focus indicators; inputs, links, and tabs rely on browser defaults
- **Keyboard navigation:** Modal has no focus trap; tab order in forms is inconsistent
- **ARIA usage:** Minimal — no `aria-label` on icon buttons, no `role` on custom components
- **Screen reader testing:** No evidence of screen reader testing or documentation

### Recommendation
Immediate fixes: (1) Adjust text colors to meet 4.5:1 minimum. (2) Add consistent focus ring using `box-shadow: 0 0 0 2px var(--color-focus-ring)` to all interactive elements. (3) Add focus trap to modal. These three changes address the highest-impact accessibility gaps.

---

## Premium Quality Assessment — Score: 5/10

### What Works
- Color palette is restrained and professional — no garish colors or gratuitous gradients
- Typography choices are appropriate (Inter for UI, serif for editorial content)
- Overall visual direction is clean and modern

### What Undermines Premium
- **Inconsistency is the primary quality killer.** Mismatched inputs, varying spacing, different loading patterns — these signal "assembled" rather than "designed."
- **Missing interaction polish.** No hover transitions, no micro-animations, no loading skeletons on key flows.
- **No elevation system.** Everything feels flat and same-level. Cards, dropdowns, modals, and tooltips need a clear elevation hierarchy.

### Recommendation
Focus on consistency before adding new features. A consistent 7/10 system feels more premium than an inconsistent system with some 9/10 components and some 4/10 components.

---

## Score Summary

| Category | Score | Weight | Weighted |
|----------|-------|--------|----------|
| Token Foundation | 6/10 | 20% | 12 |
| Component Library | 5/10 | 25% | 12.5 |
| Pattern Consistency | 5/10 | 20% | 10 |
| Naming & Structure | 6/10 | 10% | 6 |
| Documentation | 4/10 | 10% | 4 |
| Accessibility | 4/10 | 10% | 4 |
| Premium Quality | 5/10 | 5% | 2.5 |
| **Total** | | **100%** | **52/100** |

---

## Priority Roadmap

| Phase | Focus | Expected Impact |
|-------|-------|-----------------|
| **Phase 1 (Week 1–2)** | Unify input components, fix contrast issues, add focus states | Consistency +2, Accessibility +2 |
| **Phase 2 (Week 3–4)** | Introduce semantic tokens, build table component | Tokens +2, Components +2 |
| **Phase 3 (Week 5–6)** | Standardize patterns (loading, validation, navigation) | Consistency +2 |
| **Phase 4 (Week 7–8)** | Documentation sprint — usage guidelines, do/don'ts | Documentation +3 |

**Target score after Phase 4: 72/100 (Level 3 — Structured)**
