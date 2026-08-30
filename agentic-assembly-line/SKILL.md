---
name: agentic-assembly-line
description: Implements a 4-Agent Assembly Line (Bun Methodology) with strict compiler enforcement, adversarial review, and isolated git worktrees for massive codebase refactors or complex feature implementations.
---

# Agentic Assembly Line (Bun Methodology)

This skill provides a rigorous, multi-agent process for implementing complex features or massive refactors. It prevents hallucinations, halts lazy workarounds (like `@ts-ignore`), avoids Git corruption, and ensures that knowledge gained during bug-fixing is permanently retained.

## 1. Prerequisites (Blueprinting)
Before launching the assembly line, the Lead Agent **MUST** establish strict architectural blueprints:
1. Update `decisions.md` and `project.md` with the new architecture.
2. Use the `implementation_plan.md` artifact to draft a strict, non-negotiable architectural blueprint.
> [!CAUTION]
> **Negative Constraint:** Do NOT write code until the blueprint is approved by the user.

## 2. Spawning the Assembly Line
For complex tasks, use `invoke_subagent` and `define_subagent` to spawn the following isolated grid:

### A. The Implementer
* **Role**: Primary coder.
* **Workspace**: MUST be set to `"branch"` or `"share"` to prevent Git state collisions.
* **Instructions**: Implement the blueprint exactly. Never use `any` or `// @ts-ignore` as a lazy workaround for compiler errors. Fix the underlying type logic.

### B. The Adversarial Reviewer
* **Role**: Auditor.
* **Instructions**: Review the Implementer's code. Your ONLY job is to find security flaws, architectural deviations from the blueprint, and lazy stubs/bypasses. Reject the code if it fails to strictly adhere to compiler enforcement.

### C. The Compiler / Black-Box Tester
* **Role**: Validator.
* **Instructions**: Run the background tasks (e.g., `npm run build`, `npm run test`) to treat the code as a black box. If it fails, report the exact errors to the Fixer.

### D. The Fixer
* **Role**: Resolution & Documentation.
* **Instructions**: Resolve issues found by the Reviewer or Compiler. 
> [!IMPORTANT]
> **Self-Improvement Loop:** Whenever the Fixer resolves a complex bug or architectural misunderstanding, it MUST immediately write the solution into `decisions.md` or the corresponding `SKILL.md`. This removes the need for the user to manually invoke `/learn`.

## 3. Execution & Git Management
1. The Lead Agent delegates tasks to the Implementer.
2. The Implementer signals completion.
3. The Reviewer and Compiler audit the code.
4. If errors occur, the Fixer resolves them, updates `decisions.md`, and loops back to the Reviewer.
5. Once fully validated, the Lead Agent merges the isolated worktree back into the main branch.