# live-agentic-interview

`live-agentic-interview` is a minimal Codex skill for live, hard-deadline coding interviews. It keeps the central promise visible, drives a demonstrable vertical slice, enables careful parallel work, and protects integration and verification time without turning the interview into project-management theater.

This MVP has **not yet been empirically validated in a real interview**. Practice with it before relying on it.

## Design

Every session invokes the same skill and receives an explicit role:

- `ROLE: ORCHESTRATOR`: owns interpretation, priorities, delegation, integration, final verification, and presentation. There is exactly one.
- `ROLE: WORKER`: owns one bounded assignment. Kinds are `RECON`, `IMPLEMENTATION`, `TEST`, `DOCUMENTATION`, and `VERIFICATION`.
- No role: the skill states a `SOLO` assumption and proceeds with both responsibilities.

The design deliberately uses a lightweight success snapshot instead of a requirement ledger. IDs, detailed status tracking, and longer reports are optional coordination tools, not mandatory ceremony. The hard rules are limited to what prevents costly live failures: one integration owner, clear write boundaries, actual validation evidence, TDD for behavior, and deadline-triggered finalization.

## Prerequisites

Before the interview:

1. Install this skill at user scope.
2. Install the Superpowers plugin.
3. Verify this skill and Superpowers `test-driven-development` in a fresh session.
4. Practice using separate terminals and worktrees.

Do not install Superpowers during the timed exercise. The skill includes a concise red-green fallback if it is unexpectedly unavailable.

### User-scoped installation

Copy or symlink the skill directory into your user skill directory:

```bash
mkdir -p ~/.codex/skills
ln -s /absolute/path/to/live-agentic-interview/skills/live-agentic-interview \
  ~/.codex/skills/live-agentic-interview
```

If the destination exists, inspect it instead of overwriting it blindly. Refresh Codex if needed, then invoke `$live-agentic-interview` in a fresh session.

## Recommended workflow

1. Install and verify the skill and Superpowers before the interview.
2. Open the exercise repository.
3. Start one orchestrator session with [the orchestrator template](templates/orchestrator-start.md).
4. Let it capture the success snapshot, choose the minimum slice, and generate any useful worker briefs.
5. Paste briefs into separate terminals or isolated worktrees.
6. Return concise handoffs or commits to the orchestrator.
7. Let only the orchestrator integrate and verify the actual flow.
8. Say `FINALIZE NOW` near the deadline.

Separate terminals make roles obvious. Isolated worktrees are safest for writers; exact disjoint-file ownership is fine for small changes. Parallelism is optional and should earn its coordination cost.

The browser or phone timer remains authoritative. The skill does not implement timer state.

## Minimal orchestrator example

```text
ROLE: ORCHESTRATOR
Invoke `live-agentic-interview`.
EXERCISE: Implement the requirements in /tmp/exercise.md.
REPOSITORY: /work/interview-app
TIME: 60 minutes; deadline 2026-07-20 15:30 Asia/Jerusalem
TOOLS: shell, editor, git, tests
SUPERPOWERS: installed and verified
PARALLELISM: up to 3 agents; writers use isolated worktrees

Keep coordination lightweight. Capture the success snapshot, choose the minimum passing slice, and output only useful copy-paste-ready worker briefs with non-overlapping ownership. You alone integrate, verify, and finalize.
```

## Minimal worker example

Use [the worker template](templates/worker-task.md) for writing tasks. A read-only worker can be this small:

```text
ROLE: WORKER
WORKER_KIND: RECON
Invoke `live-agentic-interview`.
OBJECTIVE: Identify verified run/test commands and the narrowest change surface for the requested endpoint.
REPOSITORY / WORKTREE: /work/interview-app
KNOWN FACTS AND CONSTRAINTS: Do not edit; report only facts observed in the repository.
OWNERSHIP / ALLOWED PATHS: Read-only under /work/interview-app.
WRITE_POLICY: READ_ONLY
VALIDATION: Inspect the actual project configuration and test layout.
DEADLINE / STOP CONDITION: Return when those facts are known or access is blocked.
RETURN: concise worker handoff.
```

## Worker handoff

```text
STATUS: COMPLETE | PARTIAL | BLOCKED
WHAT I DID:
CHANGED: files and commit/patch, or none
VALIDATION: exact command — result
HANDOFF: assumptions, risks, and integration notes
```

Add detail only when it helps integration. The orchestrator still inspects changes and reruns integrated validation.

## `FINALIZE NOW`

`FINALIZE NOW` is an explicit operator control. It tells the orchestrator to stop scope growth, recall optional work, integrate only essential completed changes, verify the primary path, and prepare the interview response. It tells workers to stop refinement, run the most relevant validation, preserve useful work, and immediately hand off.

## MVP non-goals

The MVP does not provide:

- automatic agent spawning or prompt delivery;
- shared agent state;
- automatic merging or timer management;
- benchmark evaluation or model-specific adapters;
- guaranteed conflict-free parallel development.

It contains no runtime code, dependencies, CLI, terminal automation, harness adapters, registries, or evaluation infrastructure.

## Deferred milestones

- Practice-task benchmark and scoring.
- Evidence-based refinement from real interview usage.
- Optional task-brief generation tooling.
- Optional orchestration adapters.
- Measured comparison against an unassisted baseline.

These are future experiments, not current features.
