# ChatGPT Work listeners — no Jules

Provider boundary for this pilot:

- Jules: forbidden.
- Codex automation: not required.
- Trigger: GitHub pull-request activity.
- Runtime: ChatGPT Work event-triggered task.
- Preferred model: GPT-5.6 Sol when available on the account.
- Repository: simondalmasso/bounty-plaza.

Create three Work event-triggered tasks, one per role.

## ARQ1 listener

Trigger on new pull-request comments in this repository.
Condition: control PR title contains `[ORQUEST] AUD-ARQ CONTROL` and the new comment contains `WAKE_ARQ1`.
Prompt: read .orquest/COMMON.md and .orquest/agents/ARQ1.md from the control PR branch, validate the command envelope, execute only the authorized lane, and post the terminal handoff to RETURN_TO.

## ARQ2 listener

Same trigger; condition requires `WAKE_ARQ2`.
Prompt: read COMMON.md and ARQ2.md, remain read-only unless explicitly authorized otherwise, then post the terminal handoff to RETURN_TO.

## ARQ3 listener

Same trigger; condition requires `WAKE_ARQ3`.
Prompt: read COMMON.md and ARQ3.md, remain adversarial/read-only, then post the terminal handoff to RETURN_TO.

## Pilot acceptance

The pilot passes only if a comment written by AUD causes the matching Work task to run without manual copy/paste, the wrong ARQ does not run, and the selected ARQ writes its ACK and terminal handoff back to GitHub.

No merge or deploy is part of this pilot.
