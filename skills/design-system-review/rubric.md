# Design System Review Rubric

This rubric defines the 11 evaluation dimensions, scoring criteria, and thresholds for reviewing a design system.

## Scoring Scale

Each dimension is scored 1–10:

| Score | Level | Meaning |
|-------|-------|---------|
| 1–2 | Critical | Broken or absent — actively harms quality |
| 3–4 | Weak | Exists but inconsistent, incomplete, or poorly executed |
| 5–6 | Adequate | Functional but lacks refinement, has notable gaps |
| 7–8 | Strong | Well-executed with minor gaps — meets premium expectations |
| 9–10 | Excellent | Comprehensive, disciplined, distinctive — world-class quality |

## Dimension 1: Visual Hierarchy — Weight: 12%

**What to evaluate:**
- Is primary vs secondary information immediately clear?
- Are actions, headings, and supporting content intentionally prioritized?
- Does the interface guide attention in a disciplined way?

**Scoring thresholds:**
| Score | Criteria |
|-------|---------|
| 1–3 | No clear hierarchy — everything has equal visual weight |
| 4–5 | Some hierarchy exists but inconsistent across screens |
| 6–7 | Clear hierarchy on most screens, minor inconsistencies |
| 8–9 | Strong, consistent hierarchy with 3+ levels of visual weight |
| 10 | Every element has a deliberate weight — scanning is effortless |

## Dimension 2: Typography — Weight: 10%

**What to evaluate:**
- Is the type scale consistent and reusable?
- Are sizes, weights, line heights, and letter-spacing controlled?
- Does the typography feel refined, readable, and mature?

**Scoring thresholds:**
| Score | Criteria |
|-------|---------|
| 1–3 | No type scale — sizes are arbitrary, weights are random |
| 4–5 | Basic scale exists (3–4 sizes) but missing line-height/tracking control |
| 6–7 | Complete scale (5+ sizes) with weights, some gaps in application |
| 8–9 | Full scale with line-height, tracking, and consistent application |
| 10 | Typography alone creates clear hierarchy — every text style is purposeful |

## Dimension 3: Spacing and Rhythm — Weight: 10%

**What to evaluate:**
- Is spacing systematic (based on a scale)?
- Does the layout breathe with consistent rhythm?
- Are margins and paddings consistent and repeatable?

**Scoring thresholds:**
| Score | Criteria |
|-------|---------|
| 1–3 | Arbitrary spacing — no visible system, values vary randomly |
| 4–5 | Base unit exists but applied inconsistently (>6 unique values per screen) |
| 6–7 | Consistent scale, mostly applied correctly, minor exceptions |
| 8–9 | Strict scale adherence, clear hierarchy (zone > section > component > element) |
| 10 | Spacing creates visual rhythm — the page feels structurally calm |

## Dimension 4: Grid and Alignment — Weight: 8%

**What to evaluate:**
- Are elements precisely aligned to a grid?
- Are there visual edge inconsistencies or uneven patterns?
- Does the layout feel structurally calm?

**Scoring thresholds:**
| Score | Criteria |
|-------|---------|
| 1–3 | No grid — elements are positioned ad-hoc |
| 4–5 | Grid exists but frequently broken, misaligned elements visible |
| 6–7 | Grid is followed on most screens, occasional misalignment |
| 8–9 | Precise alignment throughout, clear column structure |
| 10 | Pixel-perfect alignment — every element sits on the grid |

## Dimension 5: Color Logic — Weight: 10%

**What to evaluate:**
- Are colors restrained and functional?
- Do colors have clear roles (brand, action, status, surface, text)?
- Are interactive and feedback states logically derived?

**Scoring thresholds:**
| Score | Criteria |
|-------|---------|
| 1–3 | Colors are arbitrary — no naming convention, no role assignment |
| 4–5 | Basic palette exists but colors are used inconsistently or decoratively |
| 6–7 | Semantic color tokens defined, mostly applied correctly |
| 8–9 | Complete color system with primitive → semantic → component layers |
| 10 | Every color has a documented purpose — zero decorative color usage |

## Dimension 6: Component Consistency — Weight: 12%

**What to evaluate:**
- Do components feel like one family?
- Are variants, states, and sizes coherent and scalable?
- Is the same logic applied throughout the system?

**Scoring thresholds:**
| Score | Criteria |
|-------|---------|
| 1–3 | Components are built ad-hoc — different styles for same purpose |
| 4–5 | Some shared components but mixed with one-offs, inconsistent states |
| 6–7 | Component library exists, most components have variants and states |
| 8–9 | Comprehensive library — all components share visual DNA (radius, spacing, borders) |
| 10 | Every component is a system citizen — consistent, documented, with all states |

## Dimension 7: Premium Quality — Weight: 10%

**What to evaluate:**
- Does the system feel calm, controlled, and precise?
- Are there any cheap, decorative, or overly trendy visual signals?
- Is refinement achieved through structure rather than effects?

**Scoring thresholds:**
| Score | Criteria |
|-------|---------|
| 1–3 | Feels cheap — decorative effects, inconsistent quality, template-like |
| 4–5 | Functional but generic — could be any SaaS product |
| 6–7 | Clean and professional, but lacks distinctive refinement |
| 8–9 | Feels premium — disciplined, intentional, every detail considered |
| 10 | World-class — the system itself communicates quality and care |

## Dimension 8: Distinctiveness — Weight: 8%

**What to evaluate:**
- Does the system feel ownable and recognizable?
- Or generic and replaceable?
- Does it avoid derivative product styling?

**Scoring thresholds:**
| Score | Criteria |
|-------|---------|
| 1–3 | Completely generic — indistinguishable from any other product |
| 4–5 | Some brand elements but overall anonymous |
| 6–7 | Recognizable brand expression in color and typography |
| 8–9 | Distinctive character expressed through structural decisions |
| 10 | Unmistakably this product — brand is embedded in the system DNA |

## Dimension 9: UX Maturity — Weight: 8%

**What to evaluate:**
- Does the system reduce friction?
- Are interactions understandable and predictable?
- Are users guided without confusion?

**Scoring thresholds:**
| Score | Criteria |
|-------|---------|
| 1–3 | Confusing interactions — users must guess how things work |
| 4–5 | Basic patterns work but inconsistent across screens |
| 6–7 | Consistent interaction patterns, clear feedback for most actions |
| 8–9 | Predictable, efficient interactions with proper loading/error/empty states |
| 10 | Every interaction is immediate, predictable, and confidence-building |

## Dimension 10: Accessibility — Weight: 7%

**What to evaluate:**
- Are contrast ratios sufficient (WCAG AA)?
- Are focus states visible and consistent?
- Are state changes clearly communicated?
- Does the system remain usable under real conditions?

**Scoring thresholds:**
| Score | Criteria |
|-------|---------|
| 1–3 | Major failures — contrast issues, no focus states, no ARIA |
| 4–5 | Some awareness but inconsistent — focus states on some elements only |
| 6–7 | WCAG AA met for most elements, focus states present, basic ARIA |
| 8–9 | Full AA compliance, keyboard navigation, screen reader support |
| 10 | Accessibility is a first-class system concern — documented, tested, enforced |

## Dimension 11: Responsiveness — Weight: 5%

**What to evaluate:**
- Does the system remain coherent across breakpoints?
- Do layouts and components adapt without losing hierarchy or clarity?

**Scoring thresholds:**
| Score | Criteria |
|-------|---------|
| 1–3 | Desktop-only — no responsive behavior |
| 4–5 | Basic responsive but layout breaks or hierarchy is lost on mobile |
| 6–7 | Responsive at standard breakpoints, some components don't adapt well |
| 8–9 | Full responsive system with documented breakpoints and component adaptations |
| 10 | Responsive behavior is a system feature — every component has defined breakpoint behavior |

## Overall Score Calculation

| Dimension | Weight |
|-----------|--------|
| Visual Hierarchy | 12% |
| Typography | 10% |
| Spacing and Rhythm | 10% |
| Grid and Alignment | 8% |
| Color Logic | 10% |
| Component Consistency | 12% |
| Premium Quality | 10% |
| Distinctiveness | 8% |
| UX Maturity | 8% |
| Accessibility | 7% |
| Responsiveness | 5% |
| **Total** | **100%** |

**Formula:** Overall Score = Σ (Dimension Score × Weight × 10)

**Example:** If Visual Hierarchy = 7/10, weighted = 7 × 0.12 × 10 = 8.4 points out of 12 possible.

## Red Flags (Automatic Score Reduction)

These issues reduce the overall score by 5 points each (applied after calculation):
- Generic SaaS look with no distinctive character
- AI-themed cliches (sparkles, robot icons, magic motifs)
- Emoji usage in professional UI without justification
- More than 3 different component libraries mixed together
- No documented design tokens
- Decorative effects used to compensate for weak hierarchy

## Final Quality Questions
For every recommendation ask:
- Does this feel intentional or accidental?
- Does this feel premium or only superficially modern?
- Does this reduce noise and increase clarity?
- Can this scale across the system?
- Would this be credible in a serious premium product?
