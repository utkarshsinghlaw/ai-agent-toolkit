---
name: aims-audit
description: ISO 42001 internal audit readiness checklist.
version: 1.1.0
dependencies: [ai-security-guardrails]
---

# AIMS Audit Skill

## Trigger
- User asks for ISO 42001 audit preparation
- Need to validate AI management system controls
- Prepare for internal or external audit

## How to use
1. Provide context about AI systems in scope
2. List current policies and controls
3. Invoke the `ai-security-guardrails` skill as a subagent or dependency to perform technical security checks for Clause 8.
4. Run skill with full context
5. Get audit readiness report with gaps

## Best for
- ISO 42001 internal audit prep
- AI governance documentation
- Control effectiveness validation
- Evidence collection guidance

## Example prompt
"Run AIMS audit for our e-commerce recommendation system. Check Clauses 4-10 compliance. Identify gaps in risk treatment, monitoring, and continual improvement. Output prioritized remediation list."