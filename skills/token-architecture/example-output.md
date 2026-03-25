# Example Output: Token Architecture — Fintech Dashboard

## Token System Overview

**Product:** B2B fintech dashboard for portfolio management  
**Brand Character:** Precise, trustworthy, data-dense, quietly confident  
**Theme Support:** Light + Dark  
**Target Platforms:** Web (React), iOS (SwiftUI)

---

## 1. Color Tokens

### Primitive Colors (Raw Palette)

```
gray.50:   #FAFAFA
gray.100:  #F5F5F5
gray.200:  #E5E5E5
gray.300:  #D4D4D4
gray.400:  #A3A3A3
gray.500:  #737373
gray.600:  #525252
gray.700:  #404040
gray.800:  #262626
gray.900:  #171717

blue.50:   #EFF6FF
blue.100:  #DBEAFE
blue.500:  #3B82F6
blue.600:  #2563EB
blue.700:  #1D4ED8

green.50:  #F0FDF4
green.500: #22C55E
green.700: #15803D

red.50:    #FEF2F2
red.500:   #EF4444
red.700:   #B91C1C

amber.50:  #FFFBEB
amber.500: #F59E0B
amber.700: #B45309
```

### Semantic Color Tokens

| Token | Light Value | Dark Value | Usage |
|-------|-------------|------------|-------|
| `color.bg.primary` | `#FFFFFF` | `gray.900` | Main app background |
| `color.bg.secondary` | `gray.50` | `gray.800` | Card/section backgrounds |
| `color.bg.tertiary` | `gray.100` | `gray.700` | Nested containers, table rows (alt) |
| `color.bg.inverse` | `gray.900` | `gray.50` | Inverted sections (hero, banners) |
| `color.text.primary` | `gray.900` | `gray.50` | Headings, primary content |
| `color.text.secondary` | `gray.600` | `gray.400` | Descriptions, secondary info |
| `color.text.tertiary` | `gray.500` | `gray.500` | Captions, timestamps, metadata |
| `color.text.disabled` | `gray.300` | `gray.600` | Disabled labels |
| `color.text.inverse` | `#FFFFFF` | `gray.900` | Text on inverse backgrounds |
| `color.border.default` | `gray.200` | `gray.700` | Card borders, dividers |
| `color.border.subtle` | `gray.100` | `gray.800` | Subtle separators |
| `color.border.focus` | `blue.500` | `blue.500` | Focus rings |
| `color.action.primary` | `blue.600` | `blue.500` | Primary buttons, links |
| `color.action.primary.hover` | `blue.700` | `blue.600` | Primary hover state |
| `color.action.destructive` | `red.500` | `red.500` | Delete, remove actions |
| `color.status.success` | `green.500` | `green.500` | Positive values, confirmations |
| `color.status.success.bg` | `green.50` | `green.700/15%` | Success badge backgrounds |
| `color.status.error` | `red.500` | `red.500` | Errors, negative values |
| `color.status.error.bg` | `red.50` | `red.700/15%` | Error badge backgrounds |
| `color.status.warning` | `amber.500` | `amber.500` | Warnings, caution states |
| `color.status.warning.bg` | `amber.50` | `amber.700/15%` | Warning badge backgrounds |
| `color.overlay.scrim` | `gray.900/60%` | `gray.900/80%` | Modal/dialog backdrops |
| `color.data.series.1` | `blue.500` | `blue.500` | Chart primary series |
| `color.data.series.2` | `green.500` | `green.500` | Chart secondary series |
| `color.data.series.3` | `amber.500` | `amber.500` | Chart tertiary series |
| `color.data.series.4` | `red.500` | `red.500` | Chart quaternary series |

---

## 2. Typography Tokens

### Type Scale

| Token | Size | Line Height | Weight | Tracking |
|-------|------|-------------|--------|----------|
| `typography.display.lg` | 36px | 44px | 600 | -0.02em |
| `typography.display.md` | 30px | 38px | 600 | -0.02em |
| `typography.heading.lg` | 24px | 32px | 600 | -0.01em |
| `typography.heading.md` | 20px | 28px | 600 | -0.01em |
| `typography.heading.sm` | 18px | 24px | 600 | 0 |
| `typography.label.lg` | 16px | 24px | 500 | 0 |
| `typography.label.md` | 14px | 20px | 500 | 0 |
| `typography.label.sm` | 12px | 16px | 500 | 0.01em |
| `typography.body.lg` | 16px | 24px | 400 | 0 |
| `typography.body.md` | 14px | 20px | 400 | 0 |
| `typography.body.sm` | 12px | 16px | 400 | 0.01em |
| `typography.mono.md` | 14px | 20px | 400 | 0 |
| `typography.mono.sm` | 12px | 16px | 400 | 0 |
| `typography.data.lg` | 28px | 36px | 600 | -0.02em |
| `typography.data.md` | 20px | 28px | 600 | -0.01em |
| `typography.data.sm` | 14px | 20px | 600 | 0 |

### Font Stack

```
font.family.sans:  "Inter", -apple-system, BlinkMacSystemFont, sans-serif
font.family.mono:  "JetBrains Mono", "SF Mono", "Fira Code", monospace
```

---

## 3. Spacing Tokens

| Token | Value | Usage |
|-------|-------|-------|
| `space.2xs` | 2px | Micro adjustments, icon-to-text inline gap |
| `space.xs` | 4px | Tight element gaps, badge padding |
| `space.sm` | 8px | Form field gaps, compact list items |
| `space.md` | 16px | Standard content gaps, card internal padding |
| `space.lg` | 24px | Section gaps, card padding |
| `space.xl` | 32px | Major section separation |
| `space.2xl` | 48px | Page-level section breaks |
| `space.3xl` | 64px | Hero/feature section spacing |

---

## 4. Border Radius Tokens

| Token | Value | Usage |
|-------|-------|-------|
| `radius.none` | 0px | Sharp edges (tables, full-bleed elements) |
| `radius.sm` | 4px | Badges, tags, small chips |
| `radius.md` | 8px | Buttons, inputs, cards |
| `radius.lg` | 12px | Modals, popovers, large cards |
| `radius.xl` | 16px | Feature cards, hero sections |
| `radius.full` | 9999px | Avatars, circular indicators |

---

## 5. Shadow Tokens

| Token | Value | Usage |
|-------|-------|-------|
| `shadow.sm` | `0 1px 2px rgba(0,0,0,0.05)` | Subtle lift (buttons, inputs) |
| `shadow.md` | `0 4px 6px -1px rgba(0,0,0,0.07), 0 2px 4px -2px rgba(0,0,0,0.05)` | Cards, dropdowns |
| `shadow.lg` | `0 10px 15px -3px rgba(0,0,0,0.08), 0 4px 6px -4px rgba(0,0,0,0.04)` | Popovers, floating elements |
| `shadow.xl` | `0 20px 25px -5px rgba(0,0,0,0.08), 0 8px 10px -6px rgba(0,0,0,0.04)` | Modals, dialogs |

---

## 6. Motion Tokens

| Token | Value | Usage |
|-------|-------|-------|
| `duration.instant` | 100ms | Hover states, toggles |
| `duration.fast` | 150ms | Fade in/out, color transitions |
| `duration.normal` | 200ms | Expand/collapse, slide |
| `duration.slow` | 300ms | Modal open/close, page transitions |
| `easing.default` | `cubic-bezier(0.4, 0, 0.2, 1)` | General transitions |
| `easing.in` | `cubic-bezier(0.4, 0, 1, 1)` | Elements exiting |
| `easing.out` | `cubic-bezier(0, 0, 0.2, 1)` | Elements entering |

---

## 7. Z-Index Tokens

| Token | Value | Usage |
|-------|-------|-------|
| `z.base` | 0 | Default stacking |
| `z.dropdown` | 100 | Dropdowns, select menus |
| `z.sticky` | 200 | Sticky headers, fixed nav |
| `z.overlay` | 300 | Backdrop/scrim |
| `z.modal` | 400 | Modals, dialogs |
| `z.popover` | 500 | Popovers, tooltips |
| `z.toast` | 600 | Toast notifications |

---

## 8. Breakpoint Tokens

| Token | Value | Usage |
|-------|-------|-------|
| `breakpoint.sm` | 640px | Mobile landscape |
| `breakpoint.md` | 768px | Tablet portrait |
| `breakpoint.lg` | 1024px | Tablet landscape / small desktop |
| `breakpoint.xl` | 1280px | Desktop |
| `breakpoint.2xl` | 1536px | Large desktop / data-dense views |

---

## Token Naming Convention

```
{category}.{property}.{variant}.{state}

Examples:
  color.text.primary
  color.action.primary.hover
  color.status.success.bg
  typography.heading.md
  space.lg
  radius.md
  shadow.xl
```

**Rules:**
- Always semantic, never raw values in component code
- Primitives (gray.500, blue.600) are internal only — never referenced directly in UI code
- All component styling must resolve to semantic tokens
- Dark mode is handled at the token level, not the component level
