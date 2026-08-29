---
name: ai-security-guardrails
description: Comprehensive 10-point checklist for defending AI systems against vulnerabilities.
version: 1.0.0
author: Antigravity
metadata:
  tags: [security, ai, guardrails, compliance, infosec]
---

# AI Security Guardrails Checklist

## 1. Input Guardrails
- [ ] Validate input length and format
- [ ] Detect malformed prompts
- [ ] Detect prompt injection attempts
- [ ] Detect jailbreak attempts
- [ ] Detect instruction override attempts
- [ ] Detect encoded or hidden payloads
- [ ] Detect adversarial paraphrasing

## 2. Unsafe Content Detection
- [ ] Detect malware or hacking requests
- [ ] Detect fraud instructions
- [ ] Detect violence/extremism requests
- [ ] Detect self-harm instructions
- [ ] Detect illegal activity requests
- [ ] Detect moderation bypass attempts

## 3. Prompt Injection Protection
- [ ] Protect system prompts
- [ ] Separate trusted vs untrusted context
- [ ] Sanitize retrieved external content
- [ ] Prevent retrieved documents from modifying instructions
- [ ] Track provenance of retrieved content

## 4. Memory Security
- [ ] Validate memory before persistence
- [ ] Prevent memory poisoning
- [ ] Implement memory expiration policies
- [ ] Require confirmation before storing persistent instructions

## 5. Tool Guardrails
- [ ] Restrict tool invocation scope
- [ ] Validate tool arguments before execution
- [ ] Detect SQL injection attempts
- [ ] Detect shell command injection
- [ ] Sandbox executable actions

## 6. Output Guardrails
- [ ] Scan outputs for harmful instructions
- [ ] Detect unsafe advice
- [ ] Detect privacy violations
- [ ] Detect hallucinated content
- [ ] Validate citations and references
- [ ] Detect fabricated URLs or statistics

## 7. Agentic Workflow Guardrails
- [ ] Validate every step in multi-agent workflows
- [ ] Prevent recursive loops
- [ ] Restrict uncontrolled tool chaining
- [ ] Maintain execution traceability

## 8. Reliability & Adversarial Testing
- [ ] Perform jailbreak testing
- [ ] Perform prompt injection testing
- [ ] Test adversarial inputs
- [ ] Test malformed prompts
- [ ] Monitor hallucination rates

## 9. Human Oversight
- [ ] Escalate high-risk outputs for review
- [ ] Maintain audit logs
- [ ] Allow manual override workflows
- [ ] Monitor false positives and negatives

## 10. Deployment Readiness
- [ ] Red-team the system
- [ ] Validate rollback procedures
- [ ] Define incident response plans
- [ ] Monitor system drift over time