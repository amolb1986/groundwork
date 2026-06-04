# In practice

Four short scenes — one per idea in [AGENTS.md](../AGENTS.md). Each shows the cheap mistake, then the move.

## A stale memory bites

The agent read `auth.py` early in the session and noted `verify_token(token)`. Many steps later it adds a caller and writes `verify_token(request.token)` — clean, plausible, wrong. Two edits ago the signature became `verify_token(token, *, audience)`, and the agent never looked back.

The move costs one file read. Re-open `auth.py` before calling into it, see the new required argument, pass it. The bug would have cost a full debugging round-trip and a "done" that wasn't.

## One speed for two very different jobs

Same session, two tasks: a quick script to count rows in a CSV, and a migration that drops a column. The tempting move is to give them equal weight — and an agent often gives the *wrong* one the attention: an over-built row counter with argparse and three error branches, and a column-drop run straight against the database because it "looked fine."

Flip it to match the cost of being wrong. The counter is cheap and local: a few lines, no ceremony, fix forward. The migration is irreversible: confirm intent, back up, write the down-migration, wait for a yes. Two speeds, set by blast radius.

## A question worth fifty lines

"Add export for user data." Format unspecified; there's a `created_at` field that may be internal. The cheap mistake is to pick CSV silently, include every column, build the whole endpoint, and only surface the format question after a hundred-odd lines — forcing a rewrite when the answer turns out to be "JSON, public fields only."

Instead, ask before building, batched and with a default: "Two quick calls before I build — JSON or CSV, and public fields only or include internals like `created_at`? I'd default to JSON + public-only." One message, no rewrite.

## Knowing the undo before the do

A refactor left the suite red. The agent wants to tidy up by deleting a now-unused module and force-pushing the branch. It deletes, force-pushes, then learns another service imported the module — and the history that would have proven it safe is gone.

The reversible path instead: commit the current state as a checkpoint, remove the module in its own commit, push normally. And because the suite is red from the refactor, restore a working state first and diagnose second, rather than stacking a deletion on a broken base.
