# Design System Setup Rules

This document defines the technical rules for creating and updating `AGENTS.md` and `CLAUDE.md`. For the full list of skills, workflows, and routing guidance, see `SKILL.md` — this file focuses on file handling, content requirements, and patch strategy.

## Core Principle
This setup skill bootstraps the repository so that multiple coding agents can work against the same premium UI and design-system standard. It is not only a file creation step — it is a repository standardization step.

## Required Setup Targets
This skill must manage both root-level files:
- `AGENTS.md` — cross-agent operating guide
- `CLAUDE.md` — Claude-specific operating guide

Both files are required. Both must express aligned design-system standards.

## Template Usage
When creating new files, use the templates in `templates/` as the structural base:
- `templates/AGENTS.md.template` → for `AGENTS.md`
- `templates/CLAUDE.md.template` → for `CLAUDE.md`

The templates provide the required structure and sections. The agent must fill in project-specific details and adapt the content to the repository context.

When updating existing files, do not apply the template blindly. Instead, use it as a reference to identify missing sections and patch them in.

## Required Content Sections

Both `AGENTS.md` and `CLAUDE.md` must include these sections. Use this as a checklist:

### Section 1: Premium UI Standards
- [ ] Premium UI quality expectations defined
- [ ] System-thinking requirements stated
- [ ] Consistency requirements documented
- [ ] Component discipline expectations set
- [ ] Serious and trustworthy product expectations stated

### Section 2: Forbidden Patterns
- [ ] Complete list of forbidden visual patterns (see SKILL.md for full list)
- [ ] Rationale for why these patterns are rejected
- [ ] Clear language: these are non-negotiable

### Section 3: Accessibility & Responsive
- [ ] WCAG 2.2 Level AA as baseline requirement
- [ ] Mobile-first responsive design expectations
- [ ] Keyboard navigation and screen reader requirements

### Section 4: Skill Routing
- [ ] All 12 skills listed with descriptions
- [ ] When to use each skill (routing triggers)
- [ ] Recommended workflow sequences (reference SKILL.md for the full list)

## File-Specific Expectations

### AGENTS.md
Acts as a cross-agent operating guide. Should be readable by any AI agent or human developer:
- Repository design-system mission
- Premium UI standard and forbidden patterns
- All 12 skills with routing guidance
- Recommended workflows for common tasks

### CLAUDE.md
Acts as the Claude-specific operating guide. Can include Claude-specific routing syntax:
- Same core premium UI rules as AGENTS.md
- Concise routing guidance for Claude's skill selection
- All 12 skills listed with routing triggers

## Patch Strategy
When updating existing files:
1. **Inspect first** — read the existing file completely before making changes
2. **Preserve project-specific instructions** — do not erase custom rules
3. **Append clearly labeled sections** if new content is needed
4. **Merge overlapping standards** when possible — avoid duplication
5. **Avoid contradictions** — new content must not conflict with existing content
6. **Use templates as a checklist** — verify all required sections are present
7. **Extend incomplete sections** — add missing content without destroying existing content
8. **Do not duplicate** — if a section already covers a topic adequately, leave it

## Success Criteria
The setup is successful when:
- [ ] Both root files exist (`AGENTS.md` and `CLAUDE.md`)
- [ ] Both files contain aligned premium UI standards
- [ ] All 12 skills are documented with routing guidance
- [ ] The forbidden-patterns section is present and complete
- [ ] Accessibility and responsive design expectations are included
- [ ] At least 3 workflow sequences are documented
- [ ] Existing project-specific instructions are preserved
- [ ] No contradictions between the two files
