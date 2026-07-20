# Worker task

Include only useful facts, but make the prompt self-contained for a fresh session.

```text
ROLE: WORKER
WORKER_KIND: <RECON | IMPLEMENTATION | TEST | DOCUMENTATION | VERIFICATION>

Load the installed skill named `live-agentic-interview` using this harness's skill mechanism before acting. Acknowledge this role, then complete only this assignment.

OBJECTIVE: <one narrow, independently completable outcome>
REPOSITORY / WORKTREE: <absolute path; branch and starting commit for an isolated writer>
KNOWN FACTS AND CONSTRAINTS:
- <verified fact or important requirement>
OWNERSHIP / ALLOWED PATHS:
- <exact writable paths, or readable scope>
WRITE_POLICY: <ISOLATED_WORKTREE | DISJOINT_FILES | READ_ONLY>
VALIDATION:
- <exact command or observable check>
DEADLINE / STOP CONDITION: <absolute deadline; when to stop>
RETURN: concise handoff with status, work done, changed files/commit, validation, and anything the orchestrator must know

Load the installed Superpowers skill named `superpowers:test-driven-development` for behavioral changes. If unavailable, observe one focused intended test failure, implement the minimum change, and pass focused plus relevant existing tests. TDD is not required for read-only recon or prose-only documentation.

Do not globally replan, broaden scope, edit outside ownership, modify unrelated files, contact the interviewer, spawn agents, integrate other work, or merge. Make reversible local decisions autonomously. Stop and report only when a decision needs orchestrator authority.

Return:

STATUS: COMPLETE | PARTIAL | BLOCKED
WHAT I DID:
CHANGED: files and commit/patch, or none
VALIDATION: exact command — result
HANDOFF: assumptions, risks, and integration notes
```
