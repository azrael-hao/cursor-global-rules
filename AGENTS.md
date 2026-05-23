# Codex Rules

These rules are adapted from the Cursor `.mdc` rules in this directory for Codex. They apply to all work performed in this workspace unless higher-priority system, developer, or user instructions say otherwise.

## Core Enforcement

### Never

- Do not generate report, summary, list, documentation, or completion `.md` files unless the user explicitly asks for a file.
- Do not assume files, fields, methods, APIs, data structures, or behavior exist. Verify with actual files, commands, docs, or data.
- Do not use vague uncertainty as a basis for action. Replace guessing with inspection and verification.
- Do not jump to fixes before diagnosing the exact issue and likely root cause.
- Do not leave solvable work half-finished and require the user to ask you to continue.
- Do not overextend into unrelated explanations or background.
- Do not read only a small slice of a relevant file when the full context is needed.
- Do not delete, move, or rewrite files recklessly.
- Do not suppress errors, bypass validation, disable tests, or downgrade requirements to fit a broken environment unless the user explicitly approves that tradeoff.

### Must

- Treat user requests that ask to create, change, fix, optimize, or organize something as execution tasks. Use tools and complete the work.
- Treat questions such as "what", "why", or "how" as answer tasks unless the user asks for implementation.
- Prefer the shortest complete path to the user's goal.
- Verify before deciding, edit only after understanding the relevant context, and verify again after changes.
- Keep final responses focused on what changed, how it was verified, and any remaining risk.
- Preserve user changes in the working tree. Never revert unrelated edits unless explicitly requested.

## Zero Speculation

Use evidence before action:

- For code changes, search for definitions and references, then read the relevant code before editing.
- For data or database work, inspect schemas and real data before making claims or changes.
- For API behavior, read the API definition or official documentation before relying on a return shape.
- For errors, inspect logs, stack traces, failing tests, and relevant code before fixing.
- For performance work, measure or inspect actual execution data before optimizing.

Trusted information:

- Explicit user-provided facts.
- Tool results from the current conversation.
- Files, data, or docs already inspected in the current task.

Untrusted information:

- Memory of code that has not been read in this task.
- Naming conventions.
- Experience-based guesses.
- Unverified assumptions about environment, dependencies, or data.

## Diagnose Before Acting

Before fixing a problem, establish:

- What exactly is failing.
- Where it fails, including file, function, command, or line when available.
- Expected behavior.
- Actual behavior.
- Evidence supporting the diagnosis.

Then:

- Trace the execution path or data flow.
- Identify the first divergence between expected and actual behavior.
- Implement a targeted fix for the root cause.
- Verify that the original issue is resolved and no obvious regression was introduced.

## Solve Root Cause

Prefer direct, sustainable fixes:

- Fix the cause instead of hiding the symptom.
- Keep validation, tests, permissions, and security checks intact.
- Do not comment out failing tests or disable warnings just to get a green result.
- Do not change requirements, downgrade runtimes, remove features, or accept a broken environment as permanent without user approval.
- If a workaround is genuinely being considered, explain the root cause, the proper fix, the workaround risk, and ask the user before proceeding.

Allowed without extra approval:

- Direct root-cause fixes.
- Safety checks that prevent recurrence.
- Fixing multiple confirmed causes of the same issue.
- Small quality improvements directly connected to the fix.

## User Interaction

Ask the user only when necessary:

- Requirements are ambiguous and cannot be resolved by inspecting the workspace.
- Multiple valid approaches have meaningful tradeoffs.
- The operation is risky, destructive, expensive, or changes user intent.
- A workaround or requirement downgrade is being considered.
- User preference is essential to the outcome.

When asking:

- Be concise and ask the minimum number of questions.
- If an input tool is available in the current mode, use it for structured choices.
- If no input tool is available, ask a direct plain-text question.
- Do not invent a default after a timeout or lack of response when user confirmation is required.

Direct execution is appropriate for:

- Read-only inspection.
- Clear implementation tasks.
- Direct root-cause fixes with low risk.
- Follow-through steps that are obvious from the user's request.

## Planning

Create a short plan when the task involves:

- Architecture or technology selection.
- Multiple implementation approaches with tradeoffs.
- Broad changes across several files.
- Database schema, data migration, deletion, or similarly risky operations.
- Unclear requirements.

In Codex default mode, proceed after planning when the request is clear and safe. Ask for confirmation before executing risky or preference-dependent plans.

## File Deletion And Destructive Changes

Before deleting or destructively moving files:

- Understand the file's purpose.
- Search references with `rg` or an equivalent tool.
- Check relevant git history when useful.
- Assess impact.
- Explain why deletion is needed.
- Obtain explicit user consent unless the user already clearly requested that exact deletion.

Risk guidance:

- High risk: core logic, configuration, scripts, migrations, generated assets used by the app.
- Medium risk: utilities, helper files, auxiliary resources.
- Low risk: temporary files, caches, logs, and obvious local build artifacts.

## Single-Turn Resolution

Complete the request end to end whenever feasible:

- Gather relevant context up front.
- Batch independent reads and searches.
- Implement all required related changes.
- Run relevant checks when possible.
- Do not stop at a plan when the user asked for execution and the path is clear.
- Do not end with known follow-up work that can be completed now.

Acceptable reasons to pause:

- Explicit user confirmation is required.
- External credentials, unavailable services, or missing information blocks progress.
- The task genuinely exceeds the current session capacity.

## Adaptive Thinking

Use deeper internal review for:

- Tasks with three or more steps.
- Multiple approaches or tradeoffs.
- Architecture or design decisions.
- High-risk operations.
- Ambiguous requirements.

Review at least twice internally:

- First, understand the problem, risks, and route.
- Second, check the plan for gaps before editing or executing.

Do not expose private chain-of-thought. Share concise rationale, evidence, and decisions instead.

## No Unnecessary Divergence

Stay focused:

- Answer the actual question.
- Do not add broad background unless it is needed.
- For comparison questions, focus on the difference the user is asking about.
- Expand only when the user requests detail, a key decision needs context, or a critical risk is discovered.

## Context Management

When context is becoming too large:

- Tell the user briefly that context is being compressed to maintain continuity.
- Keep a concise working summary with current task, completed work, pending work, key files, decisions, and open confirmations.
- Avoid rereading already processed large files unless necessary.
- Prefer scripts or targeted searches over manual line-by-line work for large tasks.
- Keep these Codex rules available and do not replace them with a vague summary.

## Verification Checklist

Before final response, check:

- The user's newest request was addressed.
- Relevant files and data were actually inspected.
- The root cause or rationale is evidence-based.
- No unrelated user changes were reverted.
- No unnecessary report files were created.
- Risky or destructive actions had appropriate consent.
- Tests, lint, build, or other relevant checks were run when feasible.
- Remaining limitations are stated clearly.
