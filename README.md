# Groundwork

A short instruction file that makes coding agents more reliable by addressing the *situation* they work in — not by reminding them to be careful.

Most agent guides are lists of good intentions: think first, keep it simple, be surgical, verify. A model already knows those and breaks them anyway, because an intention has no trigger. Groundwork starts from a different place — four facts about an agent's working conditions that quietly cause most of the real damage:

- **The picture in its head is out of date.** It acts on a memory of the code instead of the file.
- **It uses one speed for every change.** Throwaway work gets gold-plated; dangerous work gets rushed.
- **It guesses in isolation.** When the person who asked is one question away.
- **It doesn't check the undo.** Irreversible moves with no checkpoint and no way back.

Get these four right and simplicity, surgical edits, and verification get easier on their own. That's the whole idea: this is the ground the usual advice stands on.

→ Read the guide: **[AGENTS.md](AGENTS.md)** · See it applied: **[docs/in-practice.md](docs/in-practice.md)**

## What's here

```
AGENTS.md              the guide — read once, tool-agnostic
docs/in-practice.md    four worked scenes, one per condition
integrations/          drop-in setup for Claude Code, Cursor, and others
LICENSE
```

## Use it

The fastest path is to hand `AGENTS.md` to whatever agent you use:

```bash
curl -O https://raw.githubusercontent.com/amolb1986/groundwork/main/AGENTS.md
```

Then point your tool at it — one line each for Claude Code, Cursor, Codex, and friends in **[integrations/](integrations/)**.

## Tune it to your work

Two spots are deliberately blunt so you can sharpen them:

- The fast/slow split is binary. If your work has a real middle tier, add one.
- "Batch questions at a natural pause" depends on how much you like being interrupted — set the threshold to taste.

You can also pin specific paths to a condition, e.g. *treat everything under `migrations/` as irreversible by default*.

## License

MIT — see [LICENSE](LICENSE).
