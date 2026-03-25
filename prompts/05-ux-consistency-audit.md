# Prompt 05: UX Consistency Audit — Multi-Screen Flow

## Prompt

```
Perform a UX consistency audit on this user onboarding flow using the ux-consistency-audit skill.

The flow has 4 screens:
1. Welcome screen: centered layout, large illustration, "Get Started" button (blue, rounded)
2. Profile setup: left-aligned form, "Next" button (green, square corners), progress bar at top
3. Team invite: centered layout again, "Skip" link (underlined) and "Continue" button (blue, rounded)
4. Dashboard: completely different layout with sidebar navigation, no progress indicator, "Finish Setup" banner at top

Issues I've noticed: button styles change between screens, layout alignment shifts, progress indication disappears on the last screen.
```

## Expected Output Should Include

- **Cross-screen consistency matrix** evaluating each screen
- **Button inconsistency**: Different colors (blue vs green), different radius (rounded vs square)
- **Layout shifts**: Centered vs left-aligned without justification
- **Progress indicator**: Present on some screens, missing on others
- **Navigation pattern**: Skip vs Continue vs Get Started — inconsistent action language
- **Specific fix recommendations** per screen
- **Severity ratings** for each issue

## Red Flags (Plugin Not Working If...)

- Treats each screen in isolation instead of cross-screen analysis
- Doesn't flag the button style inconsistency
- No structured checklist or matrix format
- Missing accessibility evaluation
