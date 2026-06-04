# Integrations

The guide lives in one place: [`AGENTS.md`](../AGENTS.md). Point your tool at it.

## Claude Code

Claude Code reads `CLAUDE.md`. Either keep `AGENTS.md` and create a thin pointer, or copy it:

```bash
# copy
cp AGENTS.md CLAUDE.md

# or symlink, so edits stay in one file
ln -s AGENTS.md CLAUDE.md
```

To use it across every project rather than per-repo, drop the contents into your global `~/.claude/CLAUDE.md`.

## Cursor

Copy the ready-made rule into the project:

```bash
mkdir -p .cursor/rules
cp integrations/cursor.mdc .cursor/rules/groundwork.mdc
```

It's committed with `alwaysApply: true`, so it loads automatically. Confirm under **Settings → Rules**.

## Codex, Aider, and other tools

Most agent tools accept an `AGENTS.md` or an equivalent root instructions file directly — no extra step. If yours expects a different filename, copy `AGENTS.md` to it.

## Want a packaged plugin?

This repo is deliberately a plain guide, not a plugin bundle — it's smaller and works everywhere. If you specifically want a one-command Claude Code plugin install, that scaffolding can be added; open an issue or ask.
