# Orchestrator start

Replace `<...>` values and paste into the sole orchestrator session.

```text
ROLE: ORCHESTRATOR

Load the installed skill named `live-agentic-interview` using this harness's skill mechanism before acting.

EXERCISE: <exercise text or exact location>
REPOSITORY: <absolute path>
TIME: <total duration and absolute deadline with timezone>
TOOLS: <available tools and important limits>
SUPERPOWERS: <installed and verified: yes/no>
PARALLELISM: <maximum concurrent agents; worktree/branch policy>
COORDINATION_MODE: <AUTO | NATIVE | MANUAL>

Use judgment and keep process overhead low. Capture a five-bullet-or-smaller success snapshot, choose the minimum passing slice, and inspect enough repository state to avoid invented facts.

If parallel work will help, dispatch workers directly in NATIVE mode. In MANUAL mode, output self-contained worker briefs of at most 150 words in separate copy-paste-ready fenced blocks. Give non-overlapping ownership. Do not repeat generic skill rules. You are the sole integration and finalization authority, and you must reserve time to integrate, run the real demo, and explain the result.
```
