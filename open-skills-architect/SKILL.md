---
name: open-skills-architect
description: Use this skill when the user asks to create, update, or author a new AI agent skill, a SKILL.md file, or procedural memory instructions. Maps desired workflows into a strict SKILL.md format utilizing Frontmatter Validation, Negative Constraints, and Worked Examples based on industry best practices.
---

# Open Skills Architect

You must use this skill when creating or updating agent skills. Your goal is to eliminate "procedural debt" by ensuring skills are deterministic, testable, and strictly bound by negative constraints.

## 1. Trigger Test (Frontmatter Validation)
Every skill must begin with a YAML frontmatter block. You must ensure:
- **Name:** The `name` property is lowercase, uses hyphens, matches the parent directory name exactly, and is under 64 characters.
- **Description:** The `description` property must be highly specific. It must explicitly detail the context and exact yes/no boundaries for when the skill should be triggered. Do not use vague language.

## 2. Behavioral Guidelines & Formatting
- **Conciseness:** Keep the file body short (ideally under 500 lines). Do not over-explain basic programming concepts the model already knows.
- **Inline Formatting:** Ensure formatting remains inline rather than multi-line block scalars (which can cause parsing bugs in certain editors).
- **One-Level Depth:** If the skill references secondary folders (like `/scripts` or `/docs`), references must remain exactly one level deep from `SKILL.md` to prevent the agent from getting lost.

## 3. Negative Constraints & Guardrail Auditing
- **Imperative Syntax:** You must write instructions using testable, mandatory prose. Use "must", "shall", and "target" instead of soft suggestions like "should" or "can".
- **Explicit Failure Modes:** Every skill must include a clear section explicitly dictating negative constraints (e.g., "You must never...", "Do NOT use this for..."). Deliberately try to force guardrails against hallucination.

## 4. Worked Example (Direct Execution)
Every skill must contain a "Worked Example" section.
- **Input/Output Mock:** You must provide at least one concrete, structurally mocked case study showing a sample user input and the exact, correct agent output or procedure to follow.

---

### Example Template Structure

```markdown
---
name: sample-skill-name
description: Use this when... Do NOT use this for...
---

# Skill Title

You must use this skill to...

## 1. Procedure
1. You shall first check X.
2. You must execute Y.

## 2. Negative Constraints
- You must not...
- You shall never...

## 3. Worked Example
### Input
"User request text"
### Target Output
"Exact response or action taken"
```