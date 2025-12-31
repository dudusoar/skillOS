# Project: SkillOS

> **A personal operating system for managing AI skills with lifecycle support, context separation, and meta-skill governance**

---

## 1. Project Overview

### Goals and Success Criteria

**Primary Goals:**
- Enable skills to evolve as living units rather than static artifacts
- Separate general skill knowledge from project-specific context
- Create meta-skills that operate on other skills (generation, analysis, updating, extraction)
- Build a reusable personal skill library that grows with experience

**Success Criteria:**
- Skills can be reused across projects without modification
- Project context is cleanly separated in CLAUDE.md files
- Meta-skills successfully automate skill management workflows
- Knowledge extracted from projects feeds back into general skills

### Target Users and Use Cases

**Target Users:**
- Individual researchers and engineers working across multiple projects
- AI practitioners exploring skill-based agent architectures
- Developers seeking structured knowledge management for AI workflows

**Primary Use Cases:**
- Starting a new project: Generate project context and select relevant skills
- During development: Use skills to guide implementation with project-specific context
- Project completion: Extract learnings and update general skill knowledge
- Skill evolution: Update and refine skills based on accumulated experience

---

## 2. Technical Architecture

### Technology Stack

**Core Technologies:**
- Markdown: Skill definitions (SKILL.md), project context (CLAUDE.md), documentation
- Python: Automation scripts for skill management and processing
- Git: Version control for skill library

**Dependencies:**
- Anthropic Claude Code CLI: Skill execution environment
- Anthropic skill format: Standard for skill structure and frontmatter

**Infrastructure:**
- Local filesystem: Skill storage in `.claude/skills/`
- Git repository: SkillOS library versioning and distribution

### Project Structure

```
SkillOS/
├── .claude/
│   └── skills/               # Skills loaded by Claude
│       ├── project-context-generator/
│       │   ├── SKILL.md
│       │   └── references/
│       │       └── claude_md_template.md
│       ├── skill-analyzer/
│       │   └── SKILL.md
│       └── skill-updater/    # (Planned)
│           └── SKILL.md
├── CLAUDE.md                 # This file - SkillOS project context
└── README                    # Project documentation
```

### Key Architectural Decisions

**Decision 1: Skills Stay Independent**
- **Choice:** Project context lives in CLAUDE.md, not injected into skills
- **Rationale:** Preserves skill reusability across projects; avoids skill pollution with project-specific details
- **Trade-offs:** Requires CLAUDE.md to be comprehensive; skills must be generic enough to work across contexts

**Decision 2: Meta-Skills for Skill Management**
- **Choice:** Create specialized meta-skills for skill operations (generation, analysis, updating)
- **Rationale:** Follows "small, composable steps" principle; each meta-skill has single responsibility
- **Trade-offs:** More skills to maintain, but each is simpler and more focused

**Decision 3: Local-First with Git Distribution**
- **Choice:** Skills stored locally in `.claude/skills/`, managed via Git
- **Rationale:** Simple, transparent, version-controlled; no complex infrastructure
- **Trade-offs:** Manual Git operations required; no automatic synchronization across machines

---

## 3. Project Constraints

### Performance Requirements

- N/A: This is a knowledge management system, not a runtime system
- Skill loading should be fast enough for interactive Claude sessions

### Security and Compliance

- Skills may contain proprietary knowledge - keep repository private if needed
- No sensitive data (API keys, credentials) in skill files
- Scripts should be auditable and safe to execute

### Resource Limitations

- Solo developer project - prioritize simplicity and maintainability
- No budget constraints - all tools are free and open-source
- Designed for personal use, not production infrastructure

### Timeline and Milestones

- **Phase 1 (Current):** Core meta-skills (project-context-generator, skill-analyzer, skill-updater)
- **Phase 2:** Build general skill library through real project usage
- **Phase 3:** Knowledge extraction and skill refinement workflows
- **Ongoing:** Iterate based on usage and emerging patterns

---

## 4. Development Conventions

### Naming Conventions

**Files and Directories:**
- Skills: `kebab-case` (e.g., `project-context-generator/`)
- Skill definition: Always `SKILL.md` (uppercase)
- Python scripts: `snake_case.py` (e.g., `analyze_skills.py`)
- References: `snake_case.md` (e.g., `claude_md_template.md`)

**Skill Naming:**
- Meta-skills: Descriptive of operation (e.g., `skill-analyzer`, `knowledge-extractor`)
- General skills: Domain-focused (e.g., `frontend-design`, `api-design`)
- Project-specific skills: Prefix with domain (e.g., `ecommerce-catalog`, `payment-integration`)

### Skill Structure

Every skill follows Anthropic's standard format:

```
skill-name/
├── SKILL.md              # Required: frontmatter + instructions
├── scripts/              # Optional: executable code
├── references/           # Optional: documentation to load as needed
└── assets/               # Optional: files used in output
```

**SKILL.md frontmatter:**
```yaml
---
name: skill-name
description: What the skill does and when to use it (be comprehensive - this triggers skill selection)
---
```

### Code Style

**Markdown:**
- Use ATX-style headers (`#` not `===`)
- Maximum line length: 100 characters for readability
- Code blocks: Always specify language (```python not ```)

**Python:**
- Follow PEP 8 style guide
- Use type hints for function signatures
- Docstrings for all public functions
- Prefer pathlib over os.path for file operations

**General:**
- Keep skills concise - respect the context window
- Use progressive disclosure: core info in SKILL.md, details in references/
- Write for another Claude instance to read and execute

### Documentation Philosophy

- **SKILL.md:** Imperative voice, action-oriented ("Create X", "Analyze Y")
- **CLAUDE.md:** Declarative, describes the "what" and "why"
- **README:** User-facing, explains concepts and usage
- Avoid duplication: information lives in one canonical place

---

## 5. Available Skills

> **Note:** This section is populated by the `skill-analyzer` meta-skill.
>
> It contains skills from the SkillOS library that are relevant to this project,
> along with guidance on how to use them in this specific context.

### project-context-generator
**Relevance:** Core meta-skill for creating CLAUDE.md files for new projects.

**Key use cases:**
- Starting a new project: Generate initial project context
- Onboarding Claude to an existing project
- Updating project context after architectural changes

**Related skills:** Works with `skill-analyzer` to complete project setup.

---

### skill-analyzer
**Relevance:** Core meta-skill for selecting relevant skills and identifying missing ones.

**Key use cases:**
- After creating CLAUDE.md: Populate skills sections
- When requirements change: Update skill selection
- Discovering gaps: Identify project-specific skills to create

**Related skills:** Works with `project-context-generator` for initial setup, `skill-creator` for building missing skills.

---

### skill-contract-generator
**Relevance:** Meta-skill for defining evolution rules for skills.

**Key use cases:**
- After creating new skills: Define update boundaries
- Formalizing which parts can evolve vs. must stay stable
- Setting knowledge extraction guidelines

**Related skills:** Output consumed by `skill-updater` to guide safe updates.

---

### skill-updater
**Relevance:** Meta-skill for evolving skills during project work.

**Key use cases:**
- Discovered pattern worth adding to skill
- Found better way to explain existing concept
- Encountered edge case not documented
- Need to add project-specific workflow to references

**Related skills:** Reads contracts from `skill-contract-generator`, logs changes via `project-logger`.

---

### git-workflow
**Relevance:** Quick reference for Git commands and workflows.

**Key use cases:**
- Need Git command syntax
- Resolving merge conflicts
- Managing branches
- Troubleshooting Git issues

**Related skills:** General-purpose reference, no specific dependencies.

---

### project-logger
**Relevance:** Maintains chronological log of project evolution.

**Key use cases:**
- Completed significant task or milestone
- Made architectural decision
- Encountered and resolved issue
- Need to review project history

**Related skills:** Works with all skills to document their usage and evolution.

---

### knowledge-extractor
**Relevance:** Meta-skill for extracting generalizable knowledge from completed projects.

**Key use cases:**
- After project completion: Extract learnings to skills
- Identify patterns that appeared across multiple projects
- Analyze LOG.md for skill update opportunities
- Generate extraction recommendations (EXTRACTIONS.md)

**Related skills:** Analyzes history from `project-logger`, generates recommendations for `skill-updater` (user-invoked).

**Important:** This skill only analyzes and recommends - it does NOT execute updates. User reviews EXTRACTIONS.md and decides whether to invoke skill-updater.

---

### error-logger
**Relevance:** Maintains detailed log of errors, bugs, and debugging sessions (tactical debugging knowledge).

**Key use cases:**
- Encountered error or exception
- Debugging session >15 minutes
- Found non-obvious solution or workaround
- Discovered edge case

**Complements:** project-logger (strategic decisions) with tactical debugging knowledge in ERROR_LOG.md

**Related skills:** Works with `knowledge-extractor` to identify troubleshooting patterns for extraction to skills.

**Important:** Separates tactical debugging (ERROR_LOG.md) from strategic project evolution (LOG.md). Enables accumulation of troubleshooting wisdom across projects.

---

### test-writer
**Relevance:** Generates comprehensive test files for functions and classes.

**Key use cases:**
- Just finished writing a function or class
- Adding test coverage to existing code
- Need to systematically test edge cases
- Setting up testing infrastructure

**Supports:** Multiple frameworks (pytest, unittest, jest, mocha) with AAA pattern and best practices

**Related skills:** Uses error patterns from `error-logger` to identify test edge cases.

**Important:** Follows progressive disclosure - concise 8-step workflow in SKILL.md, detailed patterns in references/ (test patterns, framework guides, mocking strategies). Automates test scaffolding while enforcing test independence and comprehensive coverage.

**Design note:** Refactored from 618 to 244 lines (60% reduction) following skill-creator principles.

---

## 6. Missing Skills (Project-Specific)

> **Note:** This section is populated by the `skill-analyzer` meta-skill.
>
> It identifies project-specific skills that should be created to capture
> domain knowledge, workflows, or patterns unique to this project.

*No missing skills identified at this time.*

SkillOS core meta-skills are now complete. Additional skills will be identified as we use SkillOS across different projects.

---

## Maintenance Notes

**Last Updated:** 2025-12-31

**Recent Changes:**
- Added `skill-contract-generator` and `skill-updater` meta-skills (2025-12-31)
- Added `git-workflow` and `project-logger` general skills (2025-12-30)
- Initial CLAUDE.md created for SkillOS project (2025-12-30)
- Added `project-context-generator` and `skill-analyzer` meta-skills (2025-12-30)
- Defined core architecture and conventions (2025-12-30)

**Known Issues:**
- None yet - early stage

---

*This CLAUDE.md file is a living document. Update it as SkillOS evolves.*
