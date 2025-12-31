# Skill Contract: error-logger

> Complete specification of what can evolve and what must remain stable.

## Stable (General Knowledge)

**Core Elements:**
- 8-step workflow (Identify → Gather Info → Classify → Debug → Implement Solution → Prevention → Write Entry → Link to Extraction)
- Error type taxonomy (SYNTAX, TYPE, LOGIC, DEPENDENCY, etc.)
- Severity levels (Critical, High, Medium, Low)
- Entry format structure (Timestamp, Location, Context, Error Message, Root Cause, Solution, Prevention)
- Integration point with knowledge-extractor

**Do not modify:**
- Workflow steps and their order
- Core entry format (must remain structured and searchable)
- Error classification system (error types and severity)
- Principle of separating tactical (ERROR_LOG.md) from strategic (LOG.md)
- Requirement to document root cause, not just symptoms

## Mutable (Can Evolve)

**Can be updated during projects:**
- Add new error type categories based on encountered errors
- Add example patterns for different error scenarios
- Refine prevention strategies based on effectiveness
- Add debugging techniques to references/
- Improve error classification criteria
- Add templates for specific error types

**Update guidelines:**
- New error types should be distinct from existing types
- Example patterns should be real cases (anonymized if needed)
- Prevention strategies should be actionable and specific
- Debugging techniques should be generally applicable
- Prefer adding to references/ over expanding SKILL.md

## Update Rules

**Allowed without review:**
- Add new error type to taxonomy (if clearly distinct)
- Add example error patterns with solutions
- Add prevention strategies based on experience
- Fix typos, grammar, or improve clarity
- Add references/ files with debugging guides or checklists
- Add debugging techniques or tools

**Requires review:**
- Modify core workflow steps or their order
- Change entry format structure
- Modify severity level definitions
- Add new major sections to SKILL.md
- Change integration with other skills (knowledge-extractor, project-logger)

**Prohibited:**
- Remove required fields from entry format (breaks searchability)
- Skip root cause analysis (defeats the purpose)
- Merge ERROR_LOG.md with LOG.md (different purposes)
- Change from structured to unstructured format
- Remove error classification system

## Knowledge Extraction

**What to extract after projects:**
- Recurring error patterns (same error type appears 3+ times)
- Effective debugging techniques that worked across errors
- Prevention strategies that successfully avoided future errors
- Common root causes for specific error types
- Troubleshooting guides for complex errors
- Error resolution patterns by technology or domain

**When to extract:**
- After encountering same error pattern 3+ times
- When an error reveals general debugging technique
- After completing project with significant debugging
- When ERROR_LOG.md reveals technology-specific patterns
- When prevention strategies prove effective over time

**How to extract:**
- Add recurring patterns to skill troubleshooting sections
- Create references/debugging-guide.md with proven techniques
- Document prevention strategies in relevant skill contracts
- Update error taxonomy if new error types emerge consistently
- Create domain-specific troubleshooting skills (e.g., python-debugging, git-troubleshooting)

## Usage Notes

**When to use error-logger:**
- Encountered error or exception
- Debugging session >15 minutes
- Found non-obvious solution
- Discovered edge case or workaround

**When NOT to use:**
- Simple typos (<5 min fix)
- Expected validation errors
- Trivial issues with obvious solutions
- Errors already documented in ERROR_LOG.md (just reference existing entry)

**Relationship to other skills:**
- **project-logger**: Logs strategic decisions (when), error-logger logs tactical debugging (how)
- **knowledge-extractor**: Analyzes ERROR_LOG.md to identify extractable troubleshooting knowledge
- **skill-updater**: Applies extraction recommendations to add troubleshooting content to skills

## Related Skills

- **project-logger**: Strategic project log (complements ERROR_LOG.md)
- **knowledge-extractor**: Analyzes ERROR_LOG.md for patterns to extract
- **skill-updater**: Executes extraction to add troubleshooting guides to skills
