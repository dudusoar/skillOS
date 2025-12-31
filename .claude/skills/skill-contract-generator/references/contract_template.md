# Skill Contract Template

This template can be customized and inserted into any skill's SKILL.md file.

---

## Skill Contract

> This section defines what can evolve and what must remain stable as this skill is used across projects.

### Stable (General Knowledge)

**Core Elements:**
- [Primary workflow, algorithm, or knowledge that defines this skill]
- [Essential patterns or best practices]
- [Fundamental structure or organization]

**Do not modify:**
- [Specific sections that must remain unchanged]
- [Core examples or references]
- [Integration points with other skills]

### Mutable (Can Evolve)

**Can be updated during projects:**
- Add new examples to [section name]
- Add reference files to `references/` for [type of content]
- Add scripts to `scripts/` for [type of automation]
- Refine explanations in [section name] for clarity

**Update guidelines:**
- New references should follow [format/structure]
- New examples should demonstrate [criteria]
- Scripts must be [requirements: tested, documented, etc.]
- Prefer adding to `references/` over modifying SKILL.md

### Update Rules

**Allowed without review:**
- Add new examples that follow existing patterns
- Add reference files documenting project-specific patterns
- Fix typos, grammar, or formatting issues
- Clarify confusing wording without changing meaning
- Add tips or warnings based on real usage

**Requires review:**
- Modify core workflow or process steps
- Change established best practices or recommendations
- Add new sections to SKILL.md
- Modify templates or critical scripts
- Change integration points with other skills

**Prohibited:**
- Remove existing best practices or essential content
- Change the fundamental purpose of the skill
- Break backward compatibility with existing usage
- Contradict established conventions

### Knowledge Extraction

**What to extract after projects:**
- [Type 1: e.g., "Common edge cases encountered"]
- [Type 2: e.g., "Frequently asked questions"]
- [Type 3: e.g., "Reusable code patterns"]
- [Type 4: e.g., "Project-specific workflows that proved valuable"]

**When to extract:**
- When same pattern appears in 2+ projects
- When a question is asked multiple times
- When a workaround is repeatedly needed
- After completing [N] projects using this skill

**How to extract:**
- Add generalizable patterns to `references/[topic].md`
- Update examples in SKILL.md with anonymized real cases
- Create new reference files for complex patterns
- Propose new skills for distinct domains (don't bloat this skill)

---

## Example Contracts by Skill Type

### Example 1: Reference Skill (like git-workflow)

```markdown
## Skill Contract

### Stable (General Knowledge)

**Core Elements:**
- All Git command reference content (Daily Workflow, Branching, Undoing Changes, etc.)
- Command syntax and examples
- Best practices for commit messages and branch naming
- Overall structure and organization

**Do not modify:**
- Git command syntax (these are from Git documentation)
- Section organization (Daily Workflow → Branching → Undoing → etc.)

### Mutable (Can Evolve)

**Can be updated during projects:**
- Add project-specific workflows to `references/workflows/`
- Add new "Quick Tips" based on common usage
- Add examples for complex scenarios
- Clarify explanations that cause confusion

**Update guidelines:**
- New workflows in `references/` should be named `[project-type]-workflow.md`
- Tips should be concise (1-2 lines)
- Preserve existing command examples

### Update Rules

**Allowed without review:**
- Add new tips to "Quick Tips" section
- Add workflow files to `references/`
- Fix typos or improve clarity

**Requires review:**
- Add new main sections
- Change recommended workflows
- Modify best practices

**Prohibited:**
- Change Git command syntax
- Remove established best practices

### Knowledge Extraction

**What to extract:**
- Project-specific workflows that proved useful
- Common mistake patterns
- Advanced techniques discovered

**When to extract:**
- After using in 3+ projects of similar type

**How to extract:**
- Create workflow files in `references/`
- Add advanced tips to main SKILL.md if generally applicable
```

### Example 2: Workflow Skill (like project-context-generator)

```markdown
## Skill Contract

### Stable (General Knowledge)

**Core Elements:**
- 4-step workflow (Gather → Generate → Review → Next Steps)
- CLAUDE.md template structure (6 sections)
- Questions to ask for each context category

**Do not modify:**
- Workflow step order
- CLAUDE.md section structure
- Core question categories

### Mutable (Can Evolve)

**Can be updated during projects:**
- Add new example questions to each step
- Add section templates to `references/` for specific project types
- Refine CLAUDE.md template with new subsections
- Add validation prompts

**Update guidelines:**
- New questions should be open-ended, not yes/no
- Template additions must fit within existing 6-section structure
- Keep SKILL.md workflow description stable; details in `references/`

### Update Rules

**Allowed without review:**
- Add example questions to Step 1
- Add project-type templates to `references/`
- Clarify step instructions

**Requires review:**
- Change workflow steps
- Modify CLAUDE.md template structure
- Add new mandatory sections

**Prohibited:**
- Remove workflow steps
- Change CLAUDE.md section order
- Break compatibility with skill-analyzer

### Knowledge Extraction

**What to extract:**
- Project types that need specialized templates
- Common missing context areas
- Frequently forgotten constraints

**When to extract:**
- After 5+ projects reveal a pattern

**How to extract:**
- Create project-type templates in `references/templates/`
- Add common pitfalls to SKILL.md
- Update example questions with real scenarios
```

### Example 3: Meta-Skill (like skill-analyzer)

```markdown
## Skill Contract

### Stable (General Knowledge)

**Core Elements:**
- 7-step workflow (Read CLAUDE.md → Scan skills → Match → Identify missing → Update → Report)
- Matching criteria (tech stack, domain, workflow, explicit mentions)
- Relevance scoring (High/Medium/Low)

**Do not modify:**
- Workflow steps and order
- Output format (sections 5 & 6 in CLAUDE.md)
- Integration with project-context-generator

### Mutable (Can Evolve)

**Can be updated during projects:**
- Refine matching heuristics based on results
- Add new matching criteria
- Improve missing skill identification logic
- Add validation rules

**Update guidelines:**
- Matching changes should improve accuracy, not change behavior dramatically
- Test changes against existing CLAUDE.md files
- Document rationale for heuristic adjustments

### Update Rules

**Allowed without review:**
- Add new matching keywords to existing criteria
- Improve skill description parsing
- Add examples to SKILL.md

**Requires review:**
- Change matching algorithm fundamentally
- Modify CLAUDE.md section structure
- Add new workflow steps

**Prohibited:**
- Remove existing matching criteria
- Break compatibility with CLAUDE.md format
- Change output section numbers

### Knowledge Extraction

**What to extract:**
- Skill matching patterns that work well
- False positive/negative patterns
- Common skill gaps across projects

**When to extract:**
- After analyzing 10+ projects

**How to extract:**
- Document matching patterns in `references/patterns.md`
- Update heuristics based on accumulated data
- Create skill category taxonomy if patterns emerge
```

---

## Customization Guide

When creating a contract for a specific skill:

1. **Read the skill's SKILL.md** - Understand its purpose and structure
2. **Identify core vs. details** - What makes it unique vs. what's implementation
3. **Consider evolution scenarios** - How might projects improve this skill?
4. **Set appropriate boundaries** - Not too rigid, not too loose
5. **Think about knowledge flow** - What should feed back into this skill?

Use the examples above as templates, replacing bracketed content with skill-specific details.
