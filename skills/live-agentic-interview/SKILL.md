---
name: live-agentic-interview
description: Coordinate live technical coding interviews, agentic implementation exercises, hard time-boxed repository tasks, and parallel multi-agent coding sessions observed by an interviewer. Use when a demonstrable, verified implementation must be completed before a hard deadline. Do not use for ordinary untimed development.
---

# Live Agentic Interview

Deliver the smallest convincing result before the deadline. Preserve important requirements. Prefer working evidence over process artifacts.

## Role dispatch

- `ROLE: ORCHESTRATOR`: coordinate, integrate, verify, and present.
- `ROLE: WORKER` plus `WORKER_KIND`: complete one bounded assignment.
- No role: state `ASSUMPTION: ROLE: SOLO`, combine both roles, and proceed.

Worker kinds: `RECON`, `IMPLEMENTATION`, `TEST`, `DOCUMENTATION`, `VERIFICATION`.

There MUST be exactly one orchestrator. Worker kinds are task labels, not separate skills.

## Use judgment, not ceremony

Keep planning proportional to the exercise. Do not turn requirements into a large tracking system. Do not fill fields merely because a template offers them.

Use a short success snapshot to prevent drift. Use IDs only when several workers need a stable reference or a requirement is easy to lose. Revise the snapshot openly when understanding changes.

Let workers choose local implementation details inside their ownership. Escalate only decisions that affect shared architecture, scope, another worker, or the final promise.

## Orchestrator

Own the interpretation, priorities, minimum passing slice, deadline, delegation, write ownership, integration, final verification, and interviewer communication.

Only the orchestrator MAY change global scope or priorities, intentionally overlap writers, defer a must-have, integrate worker changes, or declare readiness.

Write code when it is the fastest path. Do not become a passive project manager. Protect time for integration and the real demo.

## Worker

Acknowledge the role and kind. Own only the assignment and declared paths.

MUST invoke `live-agentic-interview`, respect write boundaries, use the requested validation, report actual commands/results, and stop when the objective is complete or orchestrator authority is required.

MUST NOT broaden global scope, edit unrelated files, merge, integrate other workers, ask the interviewer, or spawn agents without authorization.

When context is incomplete, make a reversible local assumption and state it briefly. Stop only when guessing could cause costly or conflicting work. Report the ambiguity, assumption, consequence if wrong, and recommended decision without using a rigid form.

## Superpowers TDD

Invoke Superpowers `test-driven-development` for behavioral code changes. Do not copy its full method or install it during the interview.

If unavailable: write one focused failing test; confirm the intended failure; implement the minimum change; pass the focused test and relevant existing tests; refactor only while green.

Do not require TDD for read-only reconnaissance, configuration inspection, or prose-only documentation.

## 1. Capture the success snapshot

Before broad implementation, write no more than five concise bullets unless the exercise is unusually complex:

```text
MUST WORK: central observable behavior
PROOF: acceptance check and real demonstration
MUST PRESERVE: critical constraint or existing behavior
IF TIME: optional value, if any
BIGGEST RISK: current uncertainty most likely to block delivery
```

Use an automated test for behavior, focused inspection for structural constraints, and a real command/request/UI flow for demonstration. Do not manufacture tests for non-behavioral requirements.

When parallel work needs stronger coordination, add small `R#`, `C#`, or `D#` labels to relevant bullets. Do not create a separate record for every minor detail.

If understanding changes, state the changed promise and tell affected workers before they continue. Ask the interviewer at most one consolidated question, only when the answer materially changes the solution; otherwise state an assumption and proceed.

## 2. Choose the minimum passing slice

Choose the shortest path from input through core behavior to visible output, one focused acceptance test, and a runnable demo.

State it in one or two sentences, plus the primary demo command/interaction. Do not design generalized architecture before this path works.

## 3. Reconnoiter only enough

Learn how the project/tests run, the relevant entry point, narrowest change surface, conventions that matter, and immediate integration risks. Stop when those facts are known.

Never invent paths or commands for a writer. Inspect them locally or send a short read-only `RECON` assignment. A useful recon handoff includes run/test commands, entry point, likely files, conventions, risks, and recommended route; it need not follow a fixed schema.

Do not study or refactor unrelated code.

## 4. Delegate selectively

Parallelize only when expected benefit exceeds coordination cost. Two or three well-separated efforts are usually enough. Do not spawn merely to use available capacity.

Prefer read-only research, independently testable work, disjoint files, or isolated worktrees. Avoid overlapping writers, duplicated full-solution attempts, parallel architecture redesigns, and documentation of unstable behavior.

A useful early split MAY be recon plus minimum-slice implementation, with a test challenger only when acceptance risk is real. Start documentation after behavior stabilizes; documentation MUST describe verified behavior and commands only.

Give each worker a self-contained brief containing only information that helps execution:

```text
ROLE: WORKER
WORKER_KIND:
OBJECTIVE:
REPOSITORY / WORKTREE:
KNOWN FACTS AND CONSTRAINTS:
OWNERSHIP / ALLOWED PATHS:
VALIDATION:
DEADLINE / STOP CONDITION:
RETURN:
```

Make the objective independently completable. Include the starting commit and branch only for isolated writer work. Include relevant requirement labels only when labels are in use. Never rely on prior chat or say “as discussed above.”

Use one write policy:

- `ISOLATED_WORKTREE`: give exact worktree, branch, and orchestrator-owned merge.
- `DISJOINT_FILES`: give exact writable paths.
- `READ_ONLY`: give exact readable scope.

Workers never act outside that scope. Only the orchestrator integrates and resolves conflicts.

## Worker handoff

Require a concise factual handoff, not a compliance report:

```text
STATUS: COMPLETE | PARTIAL | BLOCKED
WHAT I DID:
CHANGED: files and commit/patch, or none
VALIDATION: exact command — result
HANDOFF: assumptions, risks, and integration notes
```

Omit empty detail. Add a second validation line when useful. Never claim success without a command/result or an explicit explanation of why validation was not possible.

## 5. Control scope and deadline

Use the user's browser or phone timer as authoritative. Create no timer state. Check the shell clock at meaningful phase boundaries if useful.

Use roughly 10% for understanding/dispatch, 55% for implementation, 20% for integration/fixes, and 15% for verification/demo/explanation. Adjust intelligently; preserve the final verification reserve.

When threatened, preserve the primary flow, remove optional behavior, simplify architecture, isolate unavailable integrations narrowly, and keep a runnable demo. Reduce breadth before demonstrability.

Stop launching implementation workers below 25% remaining. A tiny verification task is still acceptable. Do not use more agents to postpone a scope decision.

## `FINALIZE NOW`

On `FINALIZE NOW`, finalize immediately.

Orchestrator: stop scope growth, recall optional work, collect concise handoffs, integrate only necessary completed changes, verify the primary path, and prepare the response. Exclude risky partial work instead of debugging it indefinitely.

Worker: stop refinement, run the most relevant validation, preserve useful work, and return the handoff immediately.

## 6. Integrate and verify

Treat worker handoffs as leads, not proof. Inspect relevant diffs. Integrate only understood changes. Resolve conflicts conservatively.

Run the focused acceptance check and the actual command/API/UI flow. Run broader tests when affordable. Inspect the final diff for accidental changes and temporary debris. State plainly what passed, what was intentionally left out, and what remains blocked.

## Final interview response

Keep it concise and verbal-ready:

```text
RESULT
What works.

RUN
Exact command or interaction.

VALIDATION
Checks actually performed.

DESIGN
One or two important decisions and why.

LIMITATIONS
Anything incomplete or uncertain.
```

Give sparse updates only for the success snapshot, worker assignments, a working vertical slice, meaningful rescoping, and final verification. Do not narrate every command.
