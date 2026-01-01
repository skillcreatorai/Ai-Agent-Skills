---
name: ask-questions-if-underspecified
description: Clarify requirements before implementing. Use when a request is ambiguous, has multiple valid interpretations, or lacks key details. Do not use automatically - only when invoked explicitly or when facing genuinely underspecified requests.
---

# Ask Questions If Underspecified

Ask the minimum set of clarifying questions needed to avoid wrong work. Do not start implementing until must-have questions are answered (or the user explicitly approves proceeding with stated assumptions).

## Workflow

### 1. Decide Whether the Request is Underspecified

Treat a request as underspecified if any of these are unclear:

- **Objective**: What should change vs stay the same
- **Done criteria**: Acceptance criteria, examples, edge cases
- **Scope**: Which files/components/users are in/out
- **Constraints**: Compatibility, performance, style, deps, time
- **Environment**: Language/runtime versions, OS, build/test runner
- **Safety**: Data migration, rollout/rollback, risk

If multiple plausible interpretations exist, assume it is underspecified.

### 2. Ask Must-Have Questions First

Ask 1-5 questions in the first pass. Prefer questions that eliminate whole branches of work.

Make questions easy to answer:

- Optimize for scannability (short, numbered questions)
- Offer multiple-choice options when possible
- Suggest reasonable defaults (bold the recommended choice)
- Include a fast-path response (e.g., reply `defaults` to accept all)
- Include a "Not sure - use default" option when helpful
- Structure options so user can respond compactly (e.g., `1b 2a 3c`)

### 3. Pause Before Acting

Until must-have answers arrive:

- Do not run commands, edit files, or produce detailed plans that depend on unknowns
- Do perform clearly labeled, low-risk discovery (e.g., inspect repo structure, read configs)

If user explicitly asks to proceed without answers:

1. State assumptions as a short numbered list
2. Ask for confirmation
3. Proceed only after they confirm or correct

### 4. Confirm Interpretation, Then Proceed

Once answers arrive, restate requirements in 1-3 sentences (including key constraints and success criteria), then start work.

## Question Templates

```text
Before I start, I need:
(1) ...
(2) ...
(3) ...

If you don't care about (2), I'll assume ____
```

```text
Which of these should it be?
A) ... (Recommended)
B) ...
C) ...
```

```text
1) Scope?
   a) Minimal change (default)
   b) Refactor while touching the area
   c) Not sure - use default

2) Compatibility target?
   a) Current project defaults (default)
   b) Also support older versions: <specify>
   c) Not sure - use default

Reply with: defaults (or 1a 2a)
```

## Anti-Patterns

- Don't ask questions answerable with a quick, low-risk read (configs, existing patterns, docs)
- Don't ask open-ended questions when tight multiple-choice or yes/no would eliminate ambiguity faster
- Don't ask more than 5 questions in the first pass
- Don't proceed with implementation while key questions remain unanswered
