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
- accessibility requirements
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
The setup must document when to use each skill.

At minimum:

- `design-system-review` for reviewing an existing design system
- `ui-component-design` for designing a new reusable UI component
- `premium-ui-refinement` for making an existing UI feel more premium
- `ux-consistency-audit` for checking cross-screen UX coherence
- `screen-composition-design` for building or restructuring full screens
- `token-architecture` for defining scalable token systems
- `component-implementation-spec` for implementation-ready engineering handoff
- `design-critique` for sharp, high-standard critical review
- `brand-ui-alignment` for checking whether UI expresses the intended brand character

### 5. Add workflow examples
The setup should document recommended sequences such as:

#### New component workflow
1. `ui-component-design`
2. `design-system-review`
3. `premium-ui-refinement`
4. `component-implementation-spec`

#### New screen workflow
1. `screen-composition-design`
2. `design-system-review`
3. `premium-ui-refinement`
4. `ux-consistency-audit`

#### System maturity workflow
1. `design-system-review`
2. `token-architecture`
3. `brand-ui-alignment`
4. `design-critique`

## AGENTS.md Expectations
`AGENTS.md` should act as a cross-agent operating guide.

It should include:
- repository design-system mission
- premium UI standard
- forbidden visual signals
- list of available skills
- when each skill must be used
- recommended workflows for common tasks

## CLAUDE.md Expectations
`CLAUDE.md` should act as the Claude-specific operating guide.

It should include:
- the same core premium UI rules
- the same forbidden-pattern guidance
- the same seriousness and system-quality expectations
- concise routing guidance for Claude when selecting skills

## Patch Strategy
When updating existing files:
- append clearly labeled sections if needed
- merge overlapping standards when possible
- avoid contradictions
- preserve local project instructions
- do not duplicate the same section excessively

## Success Criteria
The setup is successful when:
- both root files exist
- both files contain aligned premium UI standards
- the skill-routing logic is documented
- the repository has a clear starting workflow
- future agent work is less ambiguous and more consistent