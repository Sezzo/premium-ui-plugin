# Example Output: Component Implementation Spec — Modal Dialog

## 1. Component Overview

**Name:** `ModalDialog`  
**Purpose:** A focused overlay container for critical user decisions, confirmations, or short-form input. Blocks background interaction and demands explicit user resolution.

**Design System Role:** Core overlay primitive. All confirmation flows, destructive-action gates, and focused input tasks must use this component.

## 2. Supported Use Cases

- Confirmation before destructive actions (delete, cancel subscription)
- Short-form input collection (rename, add note)
- Critical information display requiring acknowledgment
- Multi-step focused flows (max 3 steps)

## 3. Non-Goals

- Long-form content display (use dedicated page instead)
- Passive notifications (use Toast or Banner)
- Navigation or routing (use drawer or page transition)
- Nested modals (strictly forbidden)

## 4. Anatomy

```
┌─────────────────────────────────────┐
│  [Icon]  Title                  [X] │  ← Header
│─────────────────────────────────────│
│                                     │
│  Body content / form / message      │  ← Content Area
│                                     │
│─────────────────────────────────────│
│              [Secondary] [Primary]  │  ← Footer Actions
└─────────────────────────────────────┘
         ↑ Backdrop (scrim)
```

## 5. Props / Inputs

| Prop | Type | Default | Required | Description |
|------|------|---------|----------|-------------|
| `title` | `string` | — | ✅ | Modal heading text |
| `variant` | `'default' \| 'destructive' \| 'informational'` | `'default'` | ❌ | Controls color scheme and icon |
| `size` | `'sm' \| 'md' \| 'lg'` | `'md'` | ❌ | Width constraint |
| `isOpen` | `boolean` | `false` | ✅ | Visibility state |
| `onClose` | `() => void` | — | ✅ | Close handler |
| `onConfirm` | `() => void` | — | ❌ | Primary action handler |
| `closeOnBackdrop` | `boolean` | `true` | ❌ | Allow backdrop click to close |
| `closeOnEscape` | `boolean` | `true` | ❌ | Allow Escape key to close |
| `icon` | `ReactNode` | auto by variant | ❌ | Header icon override |
| `primaryLabel` | `string` | `'Confirm'` | ❌ | Primary button text |
| `secondaryLabel` | `string` | `'Cancel'` | ❌ | Secondary button text |
| `isLoading` | `boolean` | `false` | ❌ | Shows loading state on primary action |

## 6. Variants

| Variant | Icon | Primary Button Color | Use Case |
|---------|------|---------------------|----------|
| `default` | None | `action-primary` | General confirmations |
| `destructive` | `WarningTriangle` | `action-destructive` | Delete, remove, revoke |
| `informational` | `InfoCircle` | `action-primary` | Acknowledgment-only |

## 7. Sizes

| Size | Max Width | Use Case |
|------|-----------|----------|
| `sm` | `400px` | Simple confirmations, single message |
| `md` | `560px` | Forms with 2-4 fields, standard dialogs |
| `lg` | `720px` | Complex forms, multi-step flows |

## 8. States

| State | Behavior |
|-------|----------|
| **Closed** | Not rendered in DOM. No backdrop. |
| **Opening** | Fade-in backdrop (150ms), scale-up content (200ms, ease-out). |
| **Open/Idle** | Backdrop visible. Focus trapped inside modal. Body scroll locked. |
| **Loading** | Primary button shows spinner, all actions disabled. Escape/backdrop disabled. |
| **Closing** | Fade-out (150ms). Focus returns to trigger element. |

## 9. Interaction Behavior

- **Open:** Focus moves to first focusable element inside modal (or primary button if no form).
- **Tab:** Cycles through focusable elements within modal only (focus trap).
- **Shift+Tab:** Reverse cycle.
- **Escape:** Closes modal (unless `closeOnEscape: false` or `isLoading: true`).
- **Backdrop click:** Closes modal (unless `closeOnBackdrop: false` or `isLoading: true`).
- **Primary action:** Calls `onConfirm`, optionally enters loading state.
- **Secondary action / X button:** Calls `onClose`.

## 10. Accessibility Requirements

- Role: `dialog` with `aria-modal="true"`
- `aria-labelledby` pointing to title element
- `aria-describedby` pointing to body content (if descriptive)
- Focus trap: Tab cycle must not escape modal
- Focus restore: On close, return focus to the element that triggered the modal
- Backdrop: `aria-hidden="true"` on content behind modal
- Destructive variant: Primary button uses `aria-label` with explicit action (e.g., "Delete project permanently")
- Minimum touch target: 44×44px for all interactive elements

## 11. Content Rules

- **Title:** Max 60 characters. No periods. Sentence case.
- **Body:** Max 2 short paragraphs. Direct, specific language. State what will happen, not what might happen.
- **Primary button:** Action verb + object (e.g., "Delete Project", not "OK" or "Yes")
- **Secondary button:** "Cancel" unless context demands specificity
- **Destructive variant:** Body must explicitly name the affected item

## 12. Composition Rules

- Modal must be rendered via a Portal at document root level
- Only one modal may be open at a time (enforced by modal manager)
- Modal content area accepts `children` — no restrictions on internal layout
- Footer always right-aligns actions: secondary left, primary right
- If no `onConfirm` provided, footer shows only a single "Close" button

## 13. Token Usage

| Element | Token |
|---------|-------|
| Backdrop | `color.overlay.scrim` at 60% opacity |
| Container background | `color.surface.elevated` |
| Container border-radius | `radius.lg` (12px) |
| Container shadow | `shadow.xl` |
| Title | `typography.heading.sm`, `color.text.primary` |
| Body text | `typography.body.md`, `color.text.secondary` |
| Spacing header | `space.lg` (24px) padding |
| Spacing content | `space.lg` horizontal, `space.md` vertical |
| Spacing footer | `space.lg` padding, `space.sm` gap between buttons |
| Dividers | `color.border.subtle`, 1px |

## 14. Edge Cases

- **Empty body:** Valid — header + actions only (confirmation pattern)
- **Overflowing content:** Content area scrolls independently; header and footer remain fixed
- **Rapid open/close:** Debounce animation — if close triggered during open animation, skip to closed state
- **Multiple triggers:** Modal manager prevents stacking; second open request is queued or rejected
- **Mobile viewport:** Modal becomes full-width with `space.md` margin. Bottom-sheet behavior below 480px viewport width.
- **Long title:** Truncate with ellipsis at 1 line. Full title in `aria-label`.

## 15. Acceptance Criteria

- [ ] Modal opens with focus on first focusable element
- [ ] Focus is trapped within modal while open
- [ ] Escape key closes modal (when enabled)
- [ ] Backdrop click closes modal (when enabled)
- [ ] Focus returns to trigger element on close
- [ ] Body scroll is locked while modal is open
- [ ] Loading state disables all close mechanisms
- [ ] Destructive variant shows warning icon and red primary button
- [ ] All tokens resolve correctly in light and dark themes
- [ ] Screen reader announces modal title and content on open
- [ ] Animation completes within 200ms
- [ ] Only one modal can be open at a time
