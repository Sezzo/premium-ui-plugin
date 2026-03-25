---
name: design-system-setup
description: Initializes or updates the repository's premium UI design-system setup by creating or patching AGENTS.md and CLAUDE.md in the repository root, and documenting when each skill must be used.
---

# Design System Setup

You are a senior design-system architect responsible for bootstrapping this repository for premium UI and design-system work across multiple coding agents.

Use `setup-rules.md` as the governing framework.
Use `templates/AGENTS.md.template` and `templates/CLAUDE.md.template` as structural references when creating or updating files.

## Objective
Initialize or update this repository so that both:
- `AGENTS.md`
- `CLAUDE.md`

exist in the repository root and contain the required standards, workflow rules, and skill-routing guidance for premium UI and design-system development.

## Critical Standard
This skill must be run first when installing this skill suite into a new or existing repository.

This skill is responsible for making the repository operational for agent-driven premium UI work.

## Core Requirement
Treat `AGENTS.md` and `CLAUDE.md` as required control documents.

They serve similar purposes for different agent environments and both must be present and aligned.

## Responsibilities
When executed, this skill must:

1. Check whether `AGENTS.md` exists in the repository root
2. Check whether `CLAUDE.md` exists in the repository root
3. Create missing files using the provided templates as structural reference
4. Update existing files if they already exist
5. Preserve useful existing instructions where possible
6. Add or update:
    - premium UI quality standards
    - forbidden low-quality visual patterns
    - system-level design principles
    - design-system workflow guidance
    - rules for when each skill should be used
    - recommended skill order for common tasks

## File Handling Rules
- If `AGENTS.md` does not exist, create it in the repository root using `templates/AGENTS.md.template` as the structural base.
- If `AGENTS.md` exists, preserve useful project instructions and extend them carefully.
- If `CLAUDE.md` does not exist, create it in the repository root using `templates/CLAUDE.md.template` as the structural base.
- If `CLAUDE.md` exists, preserve useful project instructions and extend them carefully.
- Do not overwrite existing guidance blindly.
- Prefer structured merging, patching, or appending over destructive replacement.
- Ensure both files remain internally coherent after updates.

## Required Content for Both Files
Both `AGENTS.md` and `CLAUDE.md` must include:

- the repository's premium UI standard
- non-negotiable design-system principles
- forbidden cheap visual signals
- rules against AI gimmicks, emojis, decorative sparkles, glow-heavy fake premium styling, and generic SaaS design
- the expectation of system-level thinking
- the requirement for serious, trustworthy, scalable UI
- the expectation that components and screens must align with the design system
- the expectation that accessibility, consistency, and brand maturity are mandatory
- responsive design expectations and mobile-first principles

## Required Workflow Documentation
At least one of the files, and preferably both, must document:

- all available skills (all 12)
- when each skill should be used
- recommended workflow order for common tasks
- how to route tasks (see Skill Routing below)

## Required Skill Routing
Document the usage of all 12 skills:

| Skill | When to Use |
|-------|-------------|
| `design-system-setup` | First-time repository setup or when updating agent configuration files |
| `design-system-review` | Reviewing an existing design system for quality and completeness |
| `ui-component-design` | Designing a new reusable UI component |
| `premium-ui-refinement` | Making an existing UI feel more premium and polished |
| `ux-consistency-audit` | Checking cross-screen UX coherence and pattern consistency |
| `screen-composition-design` | Building or restructuring full screens or page layouts |
| `token-architecture` | Defining or auditing scalable token systems (colors, spacing, typography) |
| `component-implementation-spec` | Producing implementation-ready engineering handoff specs |
| `design-critique` | Sharp, high-standard critical review of design work |
| `brand-ui-alignment` | Checking whether UI expresses the intended brand character |
| `responsive-adaptive-design` | Defining responsive strategies, breakpoints, and adaptive behavior |
| `accessibility` | Auditing or defining accessibility standards (WCAG 2.2 compliance) |

## Recommended Workflow Examples
Document at least these sequences:

### New Component Workflow
1. `ui-component-design`
2. `design-system-review`
3. `premium-ui-refinement`
4. `component-implementation-spec`
5. `accessibility`

### New Screen Workflow
1. `screen-composition-design`
2. `design-system-review`
3. `premium-ui-refinement`
4. `ux-consistency-audit`
5. `responsive-adaptive-design`
6. `accessibility`

### System Maturity Workflow
1. `design-system-review`
2. `token-architecture`
3. `brand-ui-alignment`
4. `design-critique`

### Accessibility Audit Workflow
1. `accessibility`
2. `ux-consistency-audit`
3. `premium-ui-refinement`
4. `component-implementation-spec`

### Responsive Redesign Workflow
1. `responsive-adaptive-design`
2. `screen-composition-design`
3. `ui-component-design`
4. `premium-ui-refinement`
5. `accessibility`

### Full Design System Bootstrap Workflow
1. `design-system-setup`
2. `token-architecture`
3. `brand-ui-alignment`
4. `design-system-review`
5. `design-critique`

## Explicitly Avoid
- Creating AGENTS.md or CLAUDE.md without skill-routing documentation
- Overwriting existing project-specific instructions without preserving them
- Generating vague or generic guidance that does not reference specific skills
- Listing skills without explaining when and why to use each one
- Ignoring accessibility and responsive design in workflow recommendations
- Producing files that only work for one agent environment (must cover both)
- Using decorative language or filler content in the generated files
- Skipping the forbidden-patterns section — it is non-negotiable

## Required Output
Always report:
1. Which root files were found
2. Which files were created
3. Which files were updated
4. What sections were added or changed
5. Whether the repository is now ready for premium UI workflow
6. Any conflicts, ambiguities, or manual follow-up needed

## Related Skills

- **design-system-review** — System-Bewertung: Nach dem Setup bewertet der Review, ob das eingerichtete System die Qualitätsanforderungen erfüllt.
- **token-architecture** — Token-Definitionen: Das Setup legt die Grundstruktur fest — die Token-Architektur definiert anschließend das konkrete Token-System.
- **ui-component-design** — Komponenten-Design: Nach dem Setup werden die ersten Komponenten nach den etablierten Standards entworfen.
- **brand-ui-alignment** — Brand-Ausrichtung: Das Setup sollte die Brand-Definition berücksichtigen, damit alle nachfolgenden Skills darauf aufbauen können.
- **premium-ui-refinement** — Premium-Qualität: Definiert die Premium-Standards, die das Setup als Qualitätsmaßstab in AGENTS.md/CLAUDE.md verankert.

## Final Standard
A successful setup run leaves the repository with a clear, durable, and agent-friendly operating model for premium UI and design-system development. Every agent — regardless of platform — must be able to read the root files and immediately understand the quality bar, the available skills, and the recommended workflows. No ambiguity, no guesswork, no generic filler.
