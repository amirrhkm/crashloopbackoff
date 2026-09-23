---
description: Show or update learning progress for the crashloopbackoff lab
---

Read `PROGRESS.md` at the root of this repo. If it doesn't exist yet, create it first using this structure:

```
# Progress

## Current position
- Phase:
- Status:
- Next action:

## Session log
(most recent first)
```

**If no arguments were given** ($ARGUMENTS is empty): summarize `PROGRESS.md` for the user as a short "welcome back" briefing — current phase and module, what was last worked on, and the single next concrete action. Keep it to a few sentences. Do not start executing anything yet, and do not re-explain concepts already covered in past sessions — just orient them and wait for direction.

**If arguments were given**: treat $ARGUMENTS as a summary of what just happened this session. Update `PROGRESS.md`:
- Add a new dated entry at the top of "Session log" (most recent first) summarizing what happened
- Update "Current position" if the phase, module, or next action changed
- Also check whether the README's "Key decisions" section needs a new entry — if any decision was made this session that isn't reflected there yet, add it

Then commit and push both files with a message like "Update progress log" (only commit files that actually changed).
