# Repository agent instructions

This file applies to every agent working in this repository.

## Handoff prompt lifecycle

`agents-temp` may contain at most one current, dependency-valid handoff prompt.
When a slice is completed, its prompt and instructions must disappear from
`main`. Replace the entire file with exactly one successor prompt when concrete
next work remains; otherwise clear or remove it. Never append a new prompt below
completed prompts, preserve completed instructions as history, or accumulate
multiple prompts. Active operator add-ons may be carried into the single current
prompt, but the completed prompt around them must still be removed.

Never merge, enable auto-merge, or force-push without explicit operator approval.
