# Error Log Template

> Template for ERROR_LOG.md file structure and entry formats

## File Header

```markdown
# Error & Debug Log

> Detailed log of errors, bugs, and debugging sessions encountered during development.
>
> **Purpose:** Track tactical debugging knowledge (errors, root causes, solutions)
> **Complements:** LOG.md (strategic project evolution)
> **Used by:** knowledge-extractor to identify troubleshooting patterns for extraction

**Legend:**
- 🔴 Critical
- 🟠 High
- 🟡 Medium
- 🟢 Low

---
```

## Entry Format (Full)

For complex errors requiring detailed documentation:

```markdown
## [ERROR_TYPE] Error Title

**Timestamp:** YYYY-MM-DD HH:MM
**Severity:** [Critical 🔴 / High 🟠 / Medium 🟡 / Low 🟢]
**Status:** [Resolved / Workaround / Open]

### Location

- File: `path/to/file.py:123`
- Function: `function_name()`
- Component: [which part of the system]

### Context

[What were you doing when this happened? What was the expected behavior vs actual?]

### Error Message

\`\`\`
[Full error traceback or error output - paste exactly as shown]
\`\`\`

### Debugging Process (optional for complex errors)

1. [First hypothesis and what you tried]
2. [Second attempt and result]
3. [Key insight that led to solution]

### Root Cause

[Why did this error occur? What was the underlying issue, not just the symptom?]

### Solution

**Type:** [Fix / Workaround / Refactor / Config / Dependency]

[How was it fixed? What code or configuration changed?]

\`\`\`python
# Code snippet showing the fix (before/after if helpful)
\`\`\`

### Prevention

[How to avoid this in the future?]

- [Prevention strategy 1]
- [Prevention strategy 2]
- [Test added / Documentation updated / Pattern to follow]

### Related

- Similar errors: [Links to related error entries by ##heading-anchor]
- Extracted to: [Which skill was updated with this knowledge]
- Issue tracker: [External issue link if applicable]

---
```

## Entry Format (Condensed)

For simple, quick errors:

```markdown
## [ERROR_TYPE] Brief error description

**Timestamp:** YYYY-MM-DD HH:MM | **Severity:** Low 🟢 | **Status:** Resolved

**Location:** `file.py:45` | **Root Cause:** [One-line explanation]

**Solution:** [One-line fix]

**Prevention:** [Key takeaway]

---
```

## Error Type Taxonomy

### [SYNTAX]
Code syntax errors, typos in code, incorrect language constructs

**Example:**
```markdown
## [SYNTAX] SyntaxError: invalid syntax in skill loader

**Root Cause:** Missing closing parenthesis in function call
**Solution:** Added missing `)` on line 42
**Prevention:** Use editor with syntax highlighting and linting
```

### [TYPE]
Type errors, None errors, attribute errors, incorrect type usage

**Example:**
```markdown
## [TYPE] TypeError: 'NoneType' object is not subscriptable

**Root Cause:** Didn't check if optional config value exists before accessing
**Solution:** Added None check: `if config is not None: value = config['key']`
**Prevention:** Always validate optional values before accessing
```

### [LOGIC]
Logic bugs, incorrect algorithms, flawed conditional logic

**Example:**
```markdown
## [LOGIC] Off-by-one error in skill iteration

**Root Cause:** Used `range(len(skills))` instead of `range(len(skills) - 1)`
**Solution:** Changed to `for skill in skills:` to avoid index math
**Prevention:** Prefer iteration over indexing when possible
```

### [DEPENDENCY]
Import errors, version conflicts, missing packages, dependency issues

**Example:**
```markdown
## [DEPENDENCY] ModuleNotFoundError: No module named 'yaml'

**Root Cause:** PyYAML not installed in environment
**Solution:** Added to requirements.txt and ran `pip install -r requirements.txt`
**Prevention:** Document all dependencies in requirements.txt
```

### [ENVIRONMENT]
Path issues, permission errors, OS-specific problems, environment config

**Example:**
```markdown
## [ENVIRONMENT] PermissionError: [Errno 13] Permission denied

**Root Cause:** Trying to write to .claude/skills/ without proper permissions
**Solution:** Changed directory permissions: `chmod 755 .claude/skills/`
**Prevention:** Check write permissions before file operations
```

### [PERFORMANCE]
Timeouts, memory issues, slow operations, resource exhaustion

**Example:**
```markdown
## [PERFORMANCE] Skill loading timeout after 30 seconds

**Root Cause:** Regex pattern recompiled inside loop for each skill
**Solution:** Moved regex compilation outside loop (30s → 0.3s)
**Prevention:** Move loop-invariant computations outside loops
```

### [INTEGRATION]
API errors, external service failures, integration issues

**Example:**
```markdown
## [INTEGRATION] Claude API rate limit exceeded

**Root Cause:** Making API calls in tight loop without rate limiting
**Solution:** Added exponential backoff and request throttling
**Prevention:** Always implement rate limiting for external APIs
```

### [DATA]
Data format issues, parsing errors, validation failures, encoding problems

**Example:**
```markdown
## [DATA] JSONDecodeError: Expecting property name

**Root Cause:** YAML frontmatter contains single quotes breaking JSON parsing
**Solution:** Changed YAML parser from json.loads to yaml.safe_load
**Prevention:** Use appropriate parser for data format (YAML != JSON)
```

### [EDGE_CASE]
Unexpected input or state, boundary conditions, corner cases

**Example:**
```markdown
## [EDGE_CASE] IndexError on empty skill list

**Root Cause:** Assumed skills list always has at least one skill
**Solution:** Added empty check: `if not skills: return []`
**Prevention:** Test with empty collections, None values, edge cases
```

### [REGRESSION]
Previously working code now broken, unintended side effects

**Example:**
```markdown
## [REGRESSION] Skill loading broke after refactor

**Root Cause:** Refactored file path handling broke relative path resolution
**Solution:** Restored original path.resolve() logic
**Prevention:** Add regression tests for critical paths before refactoring
```

## Example ERROR_LOG.md

```markdown
# Error & Debug Log

> Detailed log of errors, bugs, and debugging sessions.

**Legend:** 🔴 Critical | 🟠 High | 🟡 Medium | 🟢 Low

---

## [PERFORMANCE] Skill loading timeout after 30 seconds

**Timestamp:** 2025-12-31 14:30
**Severity:** High 🟠
**Status:** Resolved

### Location
- File: `.claude/core/skill_loader.py:234`
- Function: `load_all_skills()`

### Context
Loading 50+ skills from directory causes timeout. Expected <1s, actual >30s.

### Error Message
\`\`\`
TimeoutError: Skill loading exceeded 30 second timeout
  at skill_loader.py:234 in load_all_skills()
\`\`\`

### Root Cause
Regex pattern for frontmatter parsing recompiled inside loop, causing O(n) compilations.

### Solution
**Type:** Refactor

Moved regex compilation outside loop:
\`\`\`python
# Before: O(n) compilations
for skill in skills:
    pattern = re.compile(r'^---\n(.*?)\n---', re.DOTALL)

# After: O(1) compilation
pattern = re.compile(r'^---\n(.*?)\n---', re.DOTALL)
for skill in skills:
    match = pattern.search(content)
\`\`\`

Load time: 30s → 0.3s (100x improvement)

### Prevention
- Profile before optimizing
- Cache compiled patterns
- Move invariant computations out of loops

### Related
- Extracted to: skill-creator/references/performance-patterns.md

---

## [TYPE] AttributeError: 'NoneType' object has no attribute 'get'

**Timestamp:** 2025-12-31 12:15 | **Severity:** Medium 🟡 | **Status:** Resolved

**Location:** `skill_analyzer.py:67`

**Root Cause:** Didn't check if CLAUDE.md section 5 exists before accessing

**Solution:** Added None check: `if section_5 is not None:`

**Prevention:** Always validate optional data before accessing attributes

---

## [DEPENDENCY] ImportError: cannot import name 'yaml' from 'ruamel'

**Timestamp:** 2025-12-30 16:45 | **Severity:** Low 🟢 | **Status:** Resolved

**Location:** `skill_parser.py:3`

**Root Cause:** Using wrong YAML library import

**Solution:** Changed to `from ruamel.yaml import YAML`

**Prevention:** Check library documentation for correct import statements

---
```

## Best Practices

### DO:
- ✅ Document root cause, not just symptom
- ✅ Include full error traceback
- ✅ Note what you tried before finding solution
- ✅ Add prevention strategies
- ✅ Link to extracted knowledge
- ✅ Use consistent formatting
- ✅ Add timestamp for debugging timeline

### DON'T:
- ❌ Log trivial typos (<5 min fix)
- ❌ Skip root cause analysis
- ❌ Paste without context
- ❌ Forget prevention strategies
- ❌ Duplicate entries (reference existing ones)
- ❌ Mix with strategic LOG.md content
