# Skill Contract: skill-updater

> Complete specification of what can evolve and what must remain stable.

## Stable (General Knowledge)

**Core Elements:**
- 8-step workflow (Identify → Read Contract → Classify → Verify → Prepare → Apply → Document → Commit)
- Contract compliance checking logic
- Update type classification (reference, SKILL.md, script, structure)
- General vs. project-specific heuristics

**Do not modify:**
- Workflow steps and their order
- Contract respect requirements (must always check contracts)
- Safety checks (verify, test, commit)
- Decision heuristics (would 3+ projects benefit?)

## Mutable (Can Evolve)

**Can be updated during projects:**
- Add new update patterns to "Update Patterns" section
- Add examples of good/bad updates based on experience
- Refine decision heuristics based on accumulated usage
- Add to references/ common pitfalls or edge cases encountered

**Update guidelines:**
- New patterns should be actionable and specific with clear examples
- Examples should be real (anonymized if needed) not hypothetical
- Heuristics should help decision-making, not add confusion
- Prefer adding to references/ over modifying SKILL.md

## Update Rules

**Allowed without review:**
- Add new update patterns with clear examples
- Add clarifying examples to existing sections
- Fix typos, grammar, or improve clarity
- Add edge case documentation to references/
- Add references/ files documenting common mistakes

**Requires review:**
- Modify core workflow steps or their order
- Change contract compliance rules
- Add new major sections to SKILL.md
- Modify decision heuristics fundamentally
- Change integration with other skills

**Prohibited:**
- Skip contract checking step
- Allow breaking skill contracts
- Remove safety verifications (test, commit)
- Change fundamental purpose (skill evolution, not creation)
- Make skill-updater work on skills without contracts

## Knowledge Extraction

**What to extract after projects:**
- Common update patterns that work well across skills
- Mistakes made when updating skills (what went wrong)
- Contract boundary issues (contracts too strict or too loose)
- Successful heuristics for general vs. project-specific decisions
- Common edge cases in skill updates

**When to extract:**
- After updating 5+ skills across different projects
- When a pattern of good/bad updates emerges clearly
- When similar questions arise repeatedly
- After completing a full project cycle with multiple skill updates

**How to extract:**
- Add proven patterns to "Update Patterns" section in SKILL.md
- Document pitfalls in references/common-mistakes.md
- Refine decision heuristics in SKILL.md based on outcomes
- Create references/edge-cases.md for complex scenarios
- Update examples with real anonymized cases

## Usage Notes

**When to use skill-updater:**
- Discovered a pattern worth adding to a skill
- Found better way to explain existing concept
- Encountered edge case not documented
- Need to add project-specific workflow to references

**When NOT to use:**
- Skill has no contract (use skill-contract-generator first)
- Update is project-specific (belongs in CLAUDE.md or LOG.md)
- Would require breaking the contract (propose contract update instead)
- Creating entirely new functionality (create new skill instead)

## Related Skills

- **skill-contract-generator**: Creates contracts that this skill reads
- **project-logger**: Documents updates made by this skill
- **knowledge-extractor**: Uses update history to extract patterns (future)
