# Design System Setup Rules

## Core Principle
This setup skill bootstraps the repository so that multiple coding agents can work against the same premium UI and design-system standard.

It is not only a file creation step.
It is a repository standardization step.

## Required Setup Targets
This skill must manage both root-level files:
- `AGENTS.md`
- `CLAUDE.md`

Both files are required.
Both must express aligned design-system standards.
Both must remain useful after the setup.

## Template Usage
When creating new files, use the templates in `templates/` as the structural base:
- `templates/AGENTS.md.template` → for `AGENTS.md`
- `templates/CLAUDE.md.template` → for `CLAUDE.md`

The templates provide the required structure and sections. The agent must fill in project-specific details and adapt the content to the repository context.

When updating existing files, do not apply the template blindly. Instead, use it as a reference to identify missing sections and patch them in.

## Setup Priorities

### 1. Preserve useful existing guidance
If either file already exists:
- inspect it
- preserve relevant instructions
- extend it carefully
- do not erase important project-specific rules

### 2. Add premium UI standards
Both files must establish:
- premium UI quality expectations
- system-thinking requirements
- consistency requirements
- component discipline
- accessibility requirements (WCAG 2.2)
- responsive design expectations (mobile-first)
- non-gimmicky visual standards
- serious and trustworthy product expectations

### 3. Add forbidden-pattern guidance
Both files must reject:
- emojis unless explicitly justified
- sparkle icons
- magic motifs
- robot-head AI clichés
- glowing-brain motifs
- floating-orb AI visuals
- childish illustrations
- sticker-like iconography
- decorative gradients without purpose
- excessive glow, blur, or glass effects
- fake premium through effects
- generic startup/SaaS templates
- trendy styling without design-system logic

### 4. Add skill-routing logic
The setup must document when to use each of the 12 skills:

- `design-system-setup` for first-time repository setup or updating agent configuration
- `design-system-review` for reviewing an existing design system
- `ui-component-design` for designing a new reusable UI component
- `premium-ui-refinement` for making an existing UI feel more premium
- `ux-consistency-audit` for checking cross-screen UX coherence
- `screen-composition-design` for building or restructuring full screens
- `token-architecture` for defining scalable token systems
- `component-implementation-spec` for implementation-ready engineering handoff
- `design-critique` for sharp, high-standard critical review
- `brand-ui-alignment` for checking whether UI expresses the intended brand character
- `responsive-adaptive-design` for defining responsive strategies, breakpoints, and adaptive behavior
- `accessibility` for auditing or defining accessibility standards (WCAG 2.2)

### 5. Add workflow examples
The setup should document recommended sequences such as:

#### New component workflow
1. `ui-component-design`
2. `design-system-review`
3. `premium-ui-refinement`
4. `component-implementation-spec`
5. `accessibility`

#### New screen workflow
1. `screen-composition-design`
2. `design-system-review`
3. `premium-ui-refinement`
4. `ux-consistency-audit`
5. `responsive-adaptive-design`
6. `accessibility`

#### System maturity workflow
1. `design-system-review`
2. `token-architecture`
3. `brand-ui-alignment`
4. `design-critique`

#### Accessibility audit workflow
1. `accessibility`
2. `ux-consistency-audit`
3. `premium-ui-refinement`
4. `component-implementation-spec`

#### Responsive redesign workflow
1. `responsive-adaptive-design`
2. `screen-composition-design`
3. `ui-component-design`
4. `premium-ui-refinement`
5. `accessibility`

#### Full design system bootstrap workflow
1. `design-system-setup`
2. `token-architecture`
3. `brand-ui-alignment`
4. `design-system-review`
5. `design-critique`

## AGENTS.md Expectations
`AGENTS.md` should act as a cross-agent operating guide.

It should include:
- repository design-system mission
- premium UI standard
- forbidden visual signals
- list of all 12 available skills with descriptions
- when each skill must be used
- recommended workflows for common tasks
- accessibility and responsive design expectations

## CLAUDE.md Expectations
`CLAUDE.md` should act as the Claude-specific operating guide.

It should include:
- the same core premium UI rules
- the same forbidden-pattern guidance
- the same seriousness and system-quality expectations
- concise routing guidance for Claude when selecting skills
- all 12 skills listed with routing triggers
- accessibility and responsive design expectations

## Patch Strategy
When updating existing files:
- append clearly labeled sections if needed
- merge overlapping standards when possible
- avoid contradictions
- preserve local project instructions
- do not duplicate the same section excessively
- use the templates as a checklist to verify all required sections are present
- if a required section is missing, add it in the appropriate location
- if a required section exists but is incomplete, extend it without destroying existing content

## Success Criteria
The setup is successful when:
- both root files exist
- both files contain aligned premium UI standards
- all 12 skills are documented with routing guidance
- the forbidden-patterns section is present and complete
- accessibility and responsive design expectations are included
- the repository has a clear starting workflow
- future agent work is less ambiguous and more consistent
