# Skill Contract: knowledge-extractor

> Complete specification of what can evolve and what must remain stable.

## Stable (General Knowledge)

**Core Elements:**
- 7-step workflow (Identify Scope → Read History → Identify Candidates → Check Contracts → Generate Recommendations → Present → Document)
- Decision heuristics (general vs. project-specific, update vs. new skill)
- Recommendation format and structure (EXTRACTIONS.md template)
- Non-execution principle (this skill only analyzes, does not modify skills)

**Do not modify:**
- Workflow steps and their order
- Core decision criteria (rule of three, generalizability tests)
- Separation of analysis from execution
- EXTRACTIONS.md output structure
- Contract compliance checking requirement

## Mutable (Can Evolve)

**Can be updated during projects:**
- Add new extraction patterns to "Extraction Patterns" section
- Refine evaluation criteria based on extraction outcomes
- Add examples of good/bad extraction decisions
- Improve recommendation templates
- Add to references/ checklist items or decision trees

**Update guidelines:**
- New patterns should include real examples (anonymized if needed)
- Criteria refinements should be based on multiple extraction sessions
- Examples should show both what to extract and what NOT to extract
- Templates should maintain consistent structure
- Prefer adding to references/ over expanding SKILL.md

## Update Rules

**Allowed without review:**
- Add new extraction patterns with clear examples
- Add evaluation criteria based on experience
- Add examples to existing sections
- Fix typos, grammar, or improve clarity
- Add references/ files with checklists or decision trees
- Add edge cases encountered during extraction

**Requires review:**
- Modify core workflow steps or their order
- Change fundamental decision heuristics (e.g., rule of three)
- Change EXTRACTIONS.md output format
- Add new major sections to SKILL.md
- Modify relationship with other skills

**Prohibited:**
- Allow knowledge-extractor to execute updates (must remain analysis-only)
- Skip contract checking step
- Remove generalizability tests
- Change from recommendation-based to automatic execution
- Make knowledge-extractor invoke other skills directly

## Knowledge Extraction

**What to extract after projects:**
- Successful extraction patterns (what types of knowledge extract well)
- Failed extractions (what seemed general but wasn't)
- Decision criteria that proved accurate (or inaccurate)
- Common extraction mistakes and how to avoid them
- Patterns for when to create new skills vs. update existing
- Heuristics for prioritizing extractions

**When to extract:**
- After performing 5+ knowledge extractions across different projects
- When a pattern of good/bad extraction decisions emerges
- When same questions arise repeatedly ("Should I extract this?")
- After completing multiple extraction sessions and seeing outcomes

**How to extract:**
- Add proven patterns to "Extraction Patterns" section in SKILL.md
- Document failed extractions in references/common-mistakes.md
- Refine decision heuristics in SKILL.md based on outcomes
- Create references/extraction-checklist.md with evaluation criteria
- Update examples with real anonymized cases
- Add decision trees for complex extraction scenarios

## Usage Notes

**When to use knowledge-extractor:**
- Completing a project and want to extract learnings
- Multiple projects have used similar patterns worth generalizing
- LOG.md shows repeated updates that should be consolidated
- Developed domain knowledge worth preserving

**When NOT to use:**
- In the middle of active project work (use during/after project completion)
- For obviously project-specific knowledge (no extraction needed)
- When skill updates were already generalized during project (via skill-updater)
- For knowledge that hasn't been validated through usage

**Relationship to skill-updater:**
- knowledge-extractor produces recommendations
- User reviews and decides what to apply
- skill-updater executes the approved updates
- NO direct invocation between skills

## Related Skills

- **skill-updater**: Executes extraction recommendations (invoked by user after reviewing EXTRACTIONS.md)
- **project-logger**: Provides LOG.md history that knowledge-extractor analyzes
- **skill-contract-generator**: Creates contracts that knowledge-extractor checks
- **skill-creator**: Creates new skills recommended by knowledge-extractor (invoked by user)
