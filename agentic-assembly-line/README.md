# Agentic Assembly Line (Bun Methodology)

This skill provides a rigorous, multi-agent process for implementing complex features or massive codebase refactors. It is directly inspired by the Bun team's 2026 AI-driven rewrite from Zig to Rust.

## Features
- **4-Agent Grid:** Separate Implementer, Adversarial Reviewer, Compiler, and Fixer agents.
- **Git Sharding:** Uses isolated Git worktrees to prevent corruption when multiple agents operate simultaneously.
- **Strict Compiler Enforcement:** Banny lazy code (like `// @ts-ignore`) and forces genuine type resolution.
- **Automated Self-Improvement:** The Fixer agent is instructed to document bugs in `decisions.md` automatically, ensuring future agents do not repeat mistakes.

## Disclaimer
> **Note:** This skill is experimental. Running 4 simultaneous sub-agents can consume high amounts of compute depending on the underlying model and context window. Use only for high-complexity architectural shifts or massive refactoring tasks. Ensure your target repository is backed up before initiating a large-scale assembly line process.