# Spec Driven Development (SDD) Framework

## What This Is

This directory contains a complete **Spec Driven Development (SDD)** framework for cross-functional product teams (PM, Design, Engineering). SDD bridges business planning (Epics in ProductBoard/Jira) with technical implementation (Spec files in Git).

**Status**: Production-ready, awaiting pilot team adoption

## Epic vs Spec Boundary

| Aspect | Epic (ProductBoard/Jira) | Spec (Git Repository) |
|--------|--------------------------|----------------------|
| **Owner** | Product Manager | Collaborative (PM + Design + Eng) |
| **Focus** | WHAT & WHY | HOW |
| **Contains** | User problem, business value, success metrics, high-level scope | Detailed user flows, technical architecture, data models, API contracts, testing strategy |
| **Detail Level** | High-level ("Users can export data") | Specific ("Export button top-right, CSV/JSON, max 10k rows") |

**Golden Rule**: Epic = business case, Spec = implementation blueprint

## Directory Structure

```
/Users/ts73344/sdd/
├── CLAUDE.md                           # This file - context for AI assistants
├── PILOT-DISCUSSION-GUIDE.md          # Guide for PM/Eng pilot planning discussion
├── .gitignore                         # Project artifact exclusions
├── docs/
│   ├── ai-assistant-integration.md    # How to use specs with AI coding assistants
│   └── superpowers/
│       ├── plans/
│       │   └── 2026-03-24-sdd-framework-enhancements.md  # Implementation plan
│       └── specs/
│           └── 2026-03-24-spec-driven-development-design.md  # Framework design doc
└── specs/
    ├── .spec-status-guide.md          # How to track spec status throughout lifecycle
    ├── EXAMPLE-2026-03-csv-export.md  # Reference example showing complete spec
    ├── README.md                      # Quick-start guide for teams
    └── TEMPLATE.md                    # Template for creating new specs
```

## Key Files & Their Purposes

### Core Framework (Team-Facing)
- **[`specs/README.md`](specs/README.md)** - Entry point for teams, explains when/how to create specs
- **[`specs/TEMPLATE.md`](specs/TEMPLATE.md)** - Copy this to create new specs, includes ownership annotations
- **[`specs/EXAMPLE-2026-03-csv-export.md`](specs/EXAMPLE-2026-03-csv-export.md)** - Shows what a complete, high-quality spec looks like

### Supporting Guides
- **[`specs/.spec-status-guide.md`](specs/.spec-status-guide.md)** - Lifecycle management (Draft → In Review → Approved → Implemented)
- **[`docs/ai-assistant-integration.md`](docs/ai-assistant-integration.md)** - Workflows for using specs with Copilot, Cursor, Claude Code
- **[`PILOT-DISCUSSION-GUIDE.md`](PILOT-DISCUSSION-GUIDE.md)** - Facilitates PM/Eng alignment discussion before pilot

### Design Documentation
- **[`docs/superpowers/specs/2026-03-24-spec-driven-development-design.md`](docs/superpowers/specs/2026-03-24-spec-driven-development-design.md)** - Complete framework design rationale
- **[`docs/superpowers/plans/2026-03-24-sdd-framework-enhancements.md`](docs/superpowers/plans/2026-03-24-sdd-framework-enhancements.md)** - Implementation plan for enhancements

## Working with This Framework

### To Extend or Modify

1. **Read the design doc first**: [`docs/superpowers/specs/2026-03-24-spec-driven-development-design.md`](docs/superpowers/specs/2026-03-24-spec-driven-development-design.md)
2. **Understand the Epic/Spec boundary** - this is foundational, don't break it
3. **Follow existing patterns** - ownership annotations, status workflow, section structure
4. **Update all related docs** - if you change the template, update the example and README too

### To Create a New Spec (Team Members)

1. Copy [`specs/TEMPLATE.md`](specs/TEMPLATE.md) to `specs/YYYY-MM-DD-feature-name.md`
2. Fill sections according to ownership (PM → Design → Eng)
3. Follow status workflow from [`.spec-status-guide.md`](specs/.spec-status-guide.md)
4. Reference [`EXAMPLE-2026-03-csv-export.md`](specs/EXAMPLE-2026-03-csv-export.md) for quality bar

### To Add New Guides or Examples

- Follow the pattern: clear ownership, actionable guidance, concrete examples
- Update `specs/README.md` to link to new resources
- Maintain consistency in tone, formatting, and structure
- Use markdown tables for comparisons, code blocks for examples

## Key Principles to Preserve

1. **Epic/Spec Boundary**: Epic = business case (WHAT/WHY), Spec = implementation (HOW)
2. **Collaborative Ownership**: Specs are cross-functional (PM + Design + Eng), not siloed
3. **Clear Ownership**: Each spec section has an explicit owner and contributors
4. **Status Workflow**: Draft → In Review → Approved → Implemented (no shortcuts)
5. **Version Control**: Specs live in Git alongside code, not in wikis or docs tools
6. **AI-Friendly**: Specs provide context for AI coding assistants
7. **YAGNI**: Ruthlessly remove unnecessary features from designs
8. **Realistic Detail**: Specific enough to guide implementation, not documentation for its own sake

## Common Modifications You Might Make

### Adjust Template Sections
**If**: Team finds some sections always empty or needs new sections
**Do**:
1. Update [`specs/TEMPLATE.md`](specs/TEMPLATE.md)
2. Update [`specs/EXAMPLE-2026-03-csv-export.md`](specs/EXAMPLE-2026-03-csv-export.md) to show the new structure
3. Update [`specs/README.md`](specs/README.md) to explain the change
4. Document decision in design doc

### Change Status Values
**If**: Team needs different statuses (e.g., "Blocked", "On Hold")
**Do**:
1. Update [`specs/.spec-status-guide.md`](specs/.spec-status-guide.md) status table
2. Update workflow diagram
3. Add examples for new statuses
4. Update [`specs/TEMPLATE.md`](specs/TEMPLATE.md) header

### Add Tool-Specific Guidance
**If**: Team uses a new AI assistant (e.g., new tool emerges)
**Do**:
1. Add section to [`docs/ai-assistant-integration.md`](docs/ai-assistant-integration.md)
2. Follow pattern: tool name, how to load spec, example workflow
3. Update example prompts to reference actual spec files

## Moving This Directory

When moving to a new location:

1. **Update absolute paths** (if any) in documentation
2. **Update git remote** if moving to a different repository
3. **Preserve this CLAUDE.md** - it provides context for future AI sessions
4. **Update team communications** with new location
5. **Consider**: Keep old location briefly with a README pointing to new location

## For AI Assistants Working on This Framework

**Context You Need**:
- This is a documentation framework, not code
- Users are PM/Design/Eng teams, not developers only
- Epic = ProductBoard/Jira (business planning)
- Spec = Git repo (technical blueprint)
- Don't break the Epic/Spec boundary - it's foundational
- Maintain cross-functional ownership model
- Keep examples realistic (like CSV export feature)
- All changes need PM/Design/Eng perspective, not just technical

**When Making Changes**:
- Consider all three roles (PM, Design, Engineering)
- Update related files together (template + example + README)
- Preserve existing patterns and tone
- Add examples, not just theory
- Use tables for comparisons, code blocks for examples
- Link files together with relative paths

**Red Flags** (Don't Do This):
- Merge Epic and Spec into one thing
- Remove ownership annotations
- Make specs too technical (lose PM/Design perspective)
- Add complexity without clear value
- Break cross-references between files
- Change tone to be overly formal or academic

## Questions?

This framework is designed to evolve based on team feedback. If the team discovers better practices during the pilot, update this framework to reflect them.

**Design Philosophy**: Better collaboration through clearer boundaries, explicit ownership, and structured documentation.
