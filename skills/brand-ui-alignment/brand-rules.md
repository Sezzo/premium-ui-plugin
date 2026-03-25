# Brand UI Alignment Rules

This document defines the methodology, audit dimensions, and concrete criteria for evaluating whether a UI properly expresses its intended brand character.

## Core Principle
Brand alignment in UI is not decoration. It is the consistent expression of product character through system decisions — tokens, spacing, typography, density, and interaction patterns.

## Brand Audit Methodology

### Phase 1: Establish Brand Baseline
Before auditing, the brand must be defined. If no brand documentation exists, derive it from:
1. The product's marketing site and messaging
2. The product's target audience and market position
3. Competitor analysis — what character do competitors project?
4. Stakeholder interviews — how do founders/designers describe the product?

### Phase 2: Map Brand to UI Dimensions
Translate each brand attribute into concrete UI expectations:

| Brand Attribute | Typography | Color | Spacing | Radius | Motion |
|----------------|-----------|-------|---------|--------|--------|
| **Serious** | Neutral sans-serif, tight hierarchy | Muted, restrained palette | Generous, structured | Small (4–8px) | Minimal, fast |
| **Playful** | Rounded sans-serif, varied sizes | Vibrant, diverse palette | Generous, relaxed | Large (12–16px) | Bouncy, expressive |
| **Precise** | Monospace accents, tabular figures | Minimal palette, high contrast | Tight, grid-aligned | Sharp (2–4px) | Instant, no easing |
| **Warm** | Humanist sans-serif, comfortable sizes | Warm neutrals, earth tones | Generous padding | Medium (8–12px) | Gentle, smooth |
| **Technical** | System/mono fonts, dense hierarchy | Cool neutrals, blue accents | Compact, efficient | Small (2–6px) | Fast, functional |
| **Premium** | Refined sans-serif, tight tracking | Restrained, purposeful | Generous, rhythmic | Consistent scale | Subtle, confident |

### Phase 3: Audit Each Dimension
For each of the 6 dimensions, evaluate:
1. **What the brand promises** (expected UI expression)
2. **What the UI delivers** (actual implementation)
3. **Where they diverge** (specific misalignments)
4. **How to fix it** (system-level recommendation)

### Phase 4: Score and Prioritize
Use the scoring matrix from SKILL.md. Prioritize fixes by:
1. **Visibility** — How many users see this misalignment?
2. **Severity** — How much does it contradict the brand?
3. **Effort** — How hard is it to fix?

## Detailed Audit Dimensions

### Dimension 1: Color Character

**Audit checklist:**
- [ ] Primary brand color is clearly defined and consistently used
- [ ] Color palette size is appropriate (not too many, not too few)
- [ ] Colors feel ownable — not default Bootstrap/Tailwind blue
- [ ] Status colors (success, warning, error) don't conflict with brand colors
- [ ] Dark/light mode maintains brand character (if applicable)
- [ ] Color usage is consistent across all screens

**Common misalignments:**
| Issue | Brand Impact | Fix |
|-------|-------------|-----|
| Default blue (#007bff) as primary | Feels generic, unownable | Choose a distinctive brand color |
| Too many accent colors | Chaotic, no clear identity | Reduce to 1 primary + 1 secondary accent |
| Different colors on marketing vs product | Brand disconnect | Unify palette across all touchpoints |
| Saturated colors everywhere | Feels cheap, overwhelming | Reserve saturation for actions and status |

### Dimension 2: Typography Character

**Audit checklist:**
- [ ] Typeface choice supports brand tone (serious vs friendly vs technical)
- [ ] Same typeface used across marketing and product
- [ ] Type hierarchy communicates brand confidence (not timid, not shouting)
- [ ] Number presentation matches brand precision (tabular figures for data-heavy brands)
- [ ] No conflicting typeface moods (e.g., playful headings + serious body)

**Typeface-to-brand mapping (recommendations):**
| Brand Tone | Recommended Typefaces |
|-----------|----------------------|
| Professional/Serious | Inter, IBM Plex Sans, Söhne |
| Friendly/Approachable | Nunito, DM Sans, Plus Jakarta Sans |
| Technical/Precise | JetBrains Mono (code), IBM Plex Mono, Space Grotesk |
| Premium/Refined | Satoshi, General Sans, Cabinet Grotesk |
| Neutral/Versatile | Inter, system-ui stack |

### Dimension 3: Component Personality

**Audit checklist:**
- [ ] Border-radius is consistent and matches brand tone
- [ ] Elevation/shadow style matches brand weight (light vs heavy)
- [ ] Button styles express brand confidence (not timid, not aggressive)
- [ ] Form elements feel cohesive with the overall brand
- [ ] Empty states and error states maintain brand tone

**Component personality mapping:**
| Brand Attribute | Border Radius | Elevation | Button Style |
|----------------|--------------|-----------|-------------|
| Serious | 4–6px | Subtle, layered | Solid fill, no effects |
| Friendly | 12–16px | Soft, diffused | Rounded, gentle hover |
| Technical | 2–4px | Minimal or none | Sharp, high contrast |
| Premium | 8–12px | Refined, multi-layer | Restrained, confident |

### Dimension 4: Interaction & Motion

**Audit checklist:**
- [ ] Transition timing matches brand energy (fast for dynamic, measured for calm)
- [ ] Hover effects are consistent and brand-appropriate
- [ ] Loading states maintain brand tone (no playful spinners for serious brands)
- [ ] Success/error feedback matches brand voice
- [ ] No motion that contradicts brand attributes (e.g., bouncy animations for a "precise" brand)

### Dimension 5: Copywriting & Tone

**Audit checklist:**
- [ ] UI labels are consistent in formality level
- [ ] Error messages match brand voice (helpful vs technical vs casual)
- [ ] Empty states maintain brand tone
- [ ] Onboarding copy matches product copy (no tone shift)
- [ ] No emojis or casual language in serious-brand products
- [ ] No overly formal language in friendly-brand products

### Dimension 6: Visual Distinctiveness

**Audit checklist:**
- [ ] The UI has at least one ownable visual characteristic
- [ ] The product is not visually interchangeable with competitors
- [ ] Brand expression comes from structure, not decoration
- [ ] Distinctiveness is sustainable (works across all screens, not just the homepage)
- [ ] New screens can be designed without losing brand character

## Red Flags

These patterns almost always indicate brand misalignment:
- Generic SaaS identity (could be any product)
- Copied aesthetics from major brands (Apple-like, Google-like)
- Trendy but anonymous styling (glassmorphism, gradients without purpose)
- Trying to look premium through effects rather than structure
- Inconsistent tone across screens (formal settings, casual onboarding)
- Emoji-like UI accents in serious products
- AI-themed gimmicks (sparkles, robot icons, magic wands)
- Decorative iconography with no brand logic

## System-Level Brand Rules

Strong brand alignment comes from system decisions, not surface decoration:

1. **Token-level brand:** Brand colors, typeface, and radius defined as tokens — used everywhere
2. **Density as brand:** Compact = technical/precise, comfortable = friendly/warm
3. **Spacing as brand:** Tight spacing = efficient/technical, generous spacing = calm/premium
4. **Motion as brand:** Fast/instant = precise, smooth/gentle = warm, minimal = serious
5. **Copy as brand:** Every string in the UI should pass a tone-of-voice check

## Final Questions
For every brand alignment audit, answer:
- Does this UI actually express the intended brand?
- Does it feel ownable — or could it belong to any product?
- Does it support trust for the target audience?
- Does it avoid cliche and imitation?
- Can the same brand logic scale across future screens and components?
- Would a new team member understand the brand from the UI alone?
