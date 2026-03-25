# Premium UI Plugin

A professional design system plugin for Claude that establishes and enforces repository-wide UI standards. This plugin
helps design and engineering teams build serious, trustworthy products by providing structured skills for premium UI
design, component architecture, consistency audits, and design critique.

## What is this?

The Premium UI Plugin is a collection of specialized skills that guide AI agents (particularly Claude) to produce
high-quality, consistent design work. It prevents generic startup aesthetics and enforces thoughtful, system-driven
product design.

This plugin is designed for teams who want:

- **Premium UI quality** without gimmicks or trendy effects
- **Design system consistency** across all screens and components
- **System-thinking discipline** in component architecture
- **Serious, trustworthy product aesthetics** that avoid AI clichés

## 60 Seconds Quick Start

**1. Install** — Copy the `.claude-premium-ui-plugin` directory to your repository root.

**2. Test it** — Paste this prompt into Claude:

```
Review this UI critically using the design-critique skill:

A settings page with white cards on gray background, three different input field 
styles (rounded text inputs, square dropdowns, toggle switches from a different 
library), no focus states, and all text in 14px regular weight. The target product 
is a B2B enterprise analytics platform.
```

**3. Verify** — The response should include:
- A structured critique with severity ratings (not just generic advice)
- Specific callouts for component inconsistency and missing interaction states
- Token-based recommendations (e.g., `typography.heading.sm`, `radius.md`)
- A priority action table

If the output reads like a generic design review without system references or forbidden-pattern awareness, the plugin is not loaded correctly.

## Installation

1. Copy the `.claude-premium-ui-plugin` directory to your repository root
2. Run the `design-system-setup` skill to initialize `AGENTS.md` and `CLAUDE.md`
3. Review and customize the generated files for your project

## Available Skills

### Core Setup

**`design-system-setup`**  
Bootstraps the repository with premium UI standards. Creates or updates `AGENTS.md` and `CLAUDE.md` with aligned
design-system rules, skill-routing logic, and forbidden-pattern guidance.

### Design Skills

**`design-system-review`**  
Reviews an existing design system for consistency, completeness, and premium quality standards.

**`ui-component-design`**  
Designs new reusable UI components with proper states, variants, and design-system integration.

**`premium-ui-refinement`**  
Elevates existing UI to feel more premium through refined spacing, typography, hierarchy, and details.

**`ux-consistency-audit`**  
Checks cross-screen UX coherence, interaction patterns, and navigation consistency.

**`screen-composition-design`**  
Builds or restructures full screens with proper layout, hierarchy, and component usage.

**`token-architecture`**  
Defines scalable token systems (colors, typography, spacing, etc.) for design system foundations.

**`component-implementation-spec`**  
Creates implementation-ready engineering handoff specifications for components.

**`design-critique`**  
Provides sharp, high-standard critical review of design work against premium UI principles.

**`brand-ui-alignment`**  
Checks whether UI properly expresses the intended brand character and values.

### Cross-Cutting Skills

**`responsive-adaptive-design`**  
Defines responsive layout strategies, breakpoint systems, mobile-first patterns, and adaptive behavior across all viewport sizes.

**`accessibility`**  
Audits and defines accessibility standards based on WCAG 2.2, covering screen reader support, keyboard navigation, color contrast, and inclusive design.

## Recommended Workflows

### New Component Workflow

1. `ui-component-design` – Design the component with all states and variants
2. `design-system-review` – Verify consistency with existing system
3. `premium-ui-refinement` – Polish to premium quality
4. `component-implementation-spec` – Prepare engineering handoff

### New Screen Workflow

1. `screen-composition-design` – Structure the screen layout
2. `design-system-review` – Check component usage and patterns
3. `premium-ui-refinement` – Refine visual quality
4. `ux-consistency-audit` – Verify cross-screen consistency

### System Maturity Workflow

1. `design-system-review` – Assess current system state
2. `token-architecture` – Define or refine foundational tokens
3. `brand-ui-alignment` – Check brand expression
4. `design-critique` – Critical review of system quality

## Core Principles

### Premium UI Standards

- Thoughtful spacing and typography hierarchy
- Purposeful color and contrast decisions
- Accessible and inclusive design
- Consistent interaction patterns
- System-driven component architecture

### Forbidden Patterns

This plugin explicitly rejects:

- ❌ Emojis (unless explicitly justified)
- ❌ Sparkle icons and magic motifs
- ❌ Robot-head AI clichés
- ❌ Glowing-brain motifs
- ❌ Floating-orb AI visuals
- ❌ Childish illustrations
- ❌ Sticker-like iconography
- ❌ Decorative gradients without purpose
- ❌ Excessive glow, blur, or glass effects
- ❌ Fake premium through effects
- ❌ Generic startup/SaaS templates
- ❌ Trendy styling without design-system logic

### Quality Expectations

- Serious and trustworthy product design
- Consistent design system application
- Accessibility as a baseline requirement
- Component reusability and scalability
- Clear visual hierarchy and information architecture

## Usage

### With Claude Desktop

Ensure this plugin is loaded in your Claude Desktop configuration. Use skill names in your prompts:

```
"Review my design system for consistency issues" → triggers design-system-review
"Design a new button component" → triggers ui-component-design
"Make this screen feel more premium" → triggers premium-ui-refinement
```

### With Claude Code

Reference the plugin directory in your project. Claude will automatically detect available skills and route tasks accordingly.

## Compatibility & Requirements

- **Claude Desktop** or **Claude Code** with plugin support
- No external dependencies required
- Works with any frontend framework or design tool
- Skills are framework-agnostic and focus on design principles, not implementation details

## Contributing

Contributions are welcome! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

## Author

Created by **sezzo** — building tools for serious, trustworthy product design.