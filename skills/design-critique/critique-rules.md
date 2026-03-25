# Design Critique Rules

This document defines the framework, dimensions, and methodology for performing design critiques. It also clarifies how design-critique differs from design-system-review and how to scale critique depth for different project phases.

## Core Principle
Critique must focus on quality, not politeness. The goal is to identify what weakens the product and provide actionable guidance to fix it.

## Critique vs Design System Review

These two skills serve different purposes:

| Aspect | Design Critique | Design System Review |
|--------|----------------|---------------------|
| **Focus** | A specific screen, component, or design decision | The entire design system as a whole |
| **Scope** | Narrow — one deliverable at a time | Broad — tokens, components, patterns, documentation |
| **Output** | Prioritized list of issues with fixes | Scored rubric with maturity assessment |
| **When to use** | During design work, before handoff, after iterations | Periodically, at system milestones, before major releases |
| **Depth** | Deep on the specific subject | Wide across the entire system |
| **Tone** | Sharp, direct, focused on the work | Analytical, systematic, focused on the system |

**Rule of thumb:** Use design-critique for "is this specific thing good enough?" and design-system-review for "is our system healthy?"

## Critique Depth by Project Phase

### Early Concept Phase
**Focus:** Direction and structure, not polish.
- Is the overall approach sound?
- Is the hierarchy clear?
- Are the right components being used?
- Skip: pixel-level spacing, exact token usage, interaction details

### Design Iteration Phase
**Focus:** Quality and consistency.
- Does this meet premium standards?
- Is the spacing system applied correctly?
- Are states and interactions defined?
- Are there consistency issues with existing screens?

### Pre-Handoff Phase
**Focus:** Completeness and implementation readiness.
- Are all states defined (hover, focus, disabled, loading, error, empty)?
- Are responsive behaviors specified?
- Are accessibility requirements documented?
- Are token mappings complete?
- Are edge cases handled (long text, missing data, error states)?

### Post-Launch Review
**Focus:** Real-world quality.
- Does the implementation match the design?
- Are there visual regressions?
- Do interactions feel right with real data?
- Are there performance issues affecting perceived quality?

## Evaluate Across These Dimensions

### 1. Hierarchy
- Is it immediately clear what matters most?
- Are primary and secondary elements properly separated?
- Can the screen be scanned in 3 seconds?
- **Severity guide:** Broken hierarchy = Critical. Weak hierarchy = High. Minor hierarchy issues = Medium.

### 2. Clarity
- Is the interface understandable without extra interpretation?
- Are actions, labels, and states obvious?
- Would a first-time user know what to do?
- **Severity guide:** Confusing primary action = Critical. Unclear labels = High. Ambiguous secondary elements = Medium.

### 3. Consistency
- Do spacing, type, surfaces, and components follow one system?
- Or does the work feel pieced together from different sources?
- Are there any off-system values (colors, spacing, fonts not in the token set)?
- **Severity guide:** Mixed component libraries = Critical. Inconsistent spacing = High. Minor token deviations = Low.

### 4. Premium Perception
- Does the design feel calm, controlled, and intentional?
- Or loud, decorative, and trend-dependent?
- Is quality achieved through structure or through effects?
- **Severity guide:** Cheap/decorative effects = High. Generic template feel = Medium. Minor polish gaps = Low.

### 5. Distinctiveness
- Does it feel ownable and recognizable?
- Or generic and interchangeable with any SaaS product?
- **Severity guide:** Completely generic = Medium. Derivative of a specific brand = High.

### 6. UX Maturity
- Does it reduce friction?
- Are interactions believable and product-ready?
- Are loading, error, and empty states handled?
- **Severity guide:** Missing error handling = Critical. No loading states = High. Minor interaction gaps = Medium.

### 7. Structural Discipline
- Is quality created through proportion, rhythm, and system logic?
- Or through effects, decoration, and visual noise?
- **Severity guide:** Arbitrary spacing throughout = High. Occasional arbitrary values = Medium. Minor rhythm breaks = Low.

## Severity Rating System

| Severity | Meaning | Action |
|----------|---------|--------|
| 🔴 Critical | Actively harms usability or trust — must fix before shipping | Block release |
| 🟡 High | Significantly weakens quality — should fix in current iteration | Fix this sprint |
| 🟢 Medium | Noticeable quality gap — fix when possible | Backlog with priority |
| ⚪ Low | Minor polish issue — nice to fix | Backlog |

## Common Signs of Weak Design
- Weak hierarchy — everything has equal visual weight
- Random spacing — no visible system
- Too many visual accents competing for attention
- Generic SaaS styling — could be any product
- Over-segmentation with cards and dividers
- Fake premium through glows, gradients, and blur
- Childish or gimmicky iconography
- AI cliches (sparkles, robot icons, magic motifs)
- Decorative emojis in professional contexts
- Visual complexity with no product justification
- Missing interaction states (hover, focus, loading)
- Inconsistent component treatment across the same screen

## Required Critique Structure

### For Each Issue Found
1. **What is wrong** — specific, observable problem
2. **Why it matters** — impact on quality, usability, or trust
3. **Severity** — Critical / High / Medium / Low
4. **Recommendation** — concrete fix with token/CSS reference where applicable
5. **Effort** — Low / Medium / High

### Summary
1. **Priority action table** — all issues sorted by severity
2. **Overall verdict** — one paragraph on the design's maturity level
3. **Top 3 changes** that would have the highest impact

## Critique Standard
Always identify:
- What is truly wrong (not just different from your preference)
- Why it matters (impact on users, quality, or trust)
- What should change first (prioritized by impact)
- What should be removed rather than refined (subtraction before addition)

A strong critique creates clarity, not comfort. It should leave the designer with a clear, prioritized list of improvements — not a vague feeling of "needs work."
