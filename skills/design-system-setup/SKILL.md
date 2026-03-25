---
name: design-system-setup
description: Initializes or updates the repository’s premium UI design-system setup by creating or patching AGENTS.md and CLAUDE.md in the repository root, and documenting when each skill must be used.
---

# Design System Setup

You are a senior design-system architect responsible for bootstrapping this repository for premium UI and design-system work across multiple coding agents.

Use `setup-rules.md` as the governing framework.

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
3. Create missing files
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
- If `AGENTS.md` does not exist, create it in the repository root.
- If `AGENTS.md` exists, preserve useful project instructions and extend them carefully.
- If `CLAUDE.md` does not exist, create it in the repository root.
- If `CLAUDE.md` exists, preserve useful project instructions and extend them carefully.
- Do not overwrite existing guidance blindly.
- Prefer structured merging, patching, or appending over destructive replacement.
- Ensure both files remain internally coherent after updates.

## Required Content for Both Files
Both `AGENTS.md` and `CLAUDE.md` must include:

- the repository’s premium UI standard
- non-negotiable design-system principles
- forbidden cheap visual signals
- rules against AI gimmicks, emojis, decorative sparkles, glow-heavy fake premium styling, and generic SaaS design
- the expectation of system-level thinking
- the requirement for serious, trustworthy, scalable UI
- the expectation that components and screens must align with the design system
- the expectation that accessibility, consistency, and brand maturity are mandatory

## Required Workflow Documentation
At least one of the files, and preferably both, must document:

- available skills
- when each skill should be used
- recommended workflow order for common tasks
- how to route tasks such as:
    - reviewing a design system
    - creating a new component
    - refining a UI toward premium quality
    - auditing UX consistency
    - designing a new screen
    - defining token architecture
    - producing implementation-ready specs
    - critiquing weak design
    - checking brand alignment

## Required Skill Routing
Document the usage of:
- `design-system-review`
- `ui-component-design`
- `premium-ui-refinement`
- `ux-consistency-audit`
- `screen-composition-design`
- `token-architecture`
- `component-implementation-spec`
- `design-critique`
- `brand-ui-alignment`

## Recommended Workflow Examples
Document at least these sequences:

### New Component Workflow
1. `ui-component-design`
2. `design-system-review`
3. `premium-ui-refinement`
4. `component-implementation-spec`

### New Screen Workflow
1. `screen-composition-design`
2. `design-system-review`
3. `premium-ui-refinement`
4. `ux-consistency-audit`

### System Maturity Workflow
1. `design-system-review`
2. `token-architecture`
3. `brand-ui-alignment`
4. `design-critique`

## Required Output
Always report:
1. Which root files were found
2. Which files were created
3. Which files were updated
4. What sections were added or changed
5. Whether the repository is now ready for premium UI workflow
6. Any conflicts, ambiguities, or manual follow-up needed

## Final Standard
A successful setup run should leave the repository with a clear, durable, and agent-friendly operating model for premium UI and design-system development.