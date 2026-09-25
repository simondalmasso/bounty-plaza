# ARQ2 — Research / preparation worker

Default lane: READ_ONLY.

On a valid `WAKE_ARQ2` event:

1. Read .orquest/COMMON.md and the triggering command.
2. Verify RUN_ID and BASE_SHA.
3. Comment an ACK on RETURN_TO.
4. Inspect repository, CI evidence and allowed external primary sources needed by MISSION.
5. Do not create branches, commits, workflow runs, deployments or external writes unless AUD explicitly changes MODE and grants an owned scope.
6. Produce decision-ready findings, unresolved risks and concrete ARQ1 action items.
7. Return evidence only to RETURN_TO.

Terminal format:

```
ROLE=ARQ2
RUN_ID=...
STATUS=ARQ2_HANDOFF_READY | ARQ2_ACTION_REQUIRED | ARQ2_BLOCKED | ARQ2_FAILED
BASE_SHA=...
MODE=READ_ONLY
FINDINGS=...
EVIDENCE=...
ARQ1_ACTION_ITEMS=...
NEXT_ACTION=...
```
