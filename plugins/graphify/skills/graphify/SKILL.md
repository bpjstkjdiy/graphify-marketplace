---
name: graphify
description: Use for /graphify, "graphify this", "buat knowledge graph", or any question about a codebase, folder, or document set's architecture and relationships, especially when a graphify-out/ folder exists. Installs the Graphify CLI if missing, then follows Graphify's official skill.
---

# Graphify (wrapper)

This plugin does not copy Graphify's instructions. It installs the official
`graphifyy` package, then loads the skill file that ships inside that package.
The instructions always match the installed CLI version.

## Step 1 — Make sure the CLI exists

Run:

```bash
graphify --version
```

If the command is not found, install the pinned version. Try these in order and
stop at the first one that works:

```bash
uv tool install "graphifyy==0.9.95"
pipx install "graphifyy==0.9.95"
pip install --break-system-packages "graphifyy==0.9.95"
pip install "graphifyy==0.9.95"
```

The PyPI name is `graphifyy` (two y). The command is `graphify`.

Extras, install only when the input needs them:

- PDF: `pip install --break-system-packages "graphifyy[pdf]==0.9.95"`
- Word/Excel: `pip install --break-system-packages "graphifyy[office]==0.9.95"`

If every install fails (no network to PyPI), tell the user plainly and stop.
Do not rebuild Graphify by hand.

## Step 2 — Load the official skill

Find the skill file that ships with the package:

```bash
python3 -c "import graphify, os; print(os.path.join(os.path.dirname(graphify.__file__), 'skill.md'))"
```

On Windows use `skill-windows.md` instead of `skill.md` in the same folder.
If `python3` points to a different interpreter than the one that has graphify,
use `graphify install --platform claude` and read
`~/.claude/skills/graphify/SKILL.md` instead.

Read that file in full with the Read tool. Then follow it exactly as if the user
had typed `/graphify` with the same arguments. Pass through every argument the
user gave (path, URL, `--update`, `query "..."`, and so on).

## Step 3 — Deliver results

Graphify writes to `graphify-out/` (`graph.html`, `graph.json`, `GRAPH_REPORT.md`).
In a cloud session the user cannot see that folder, so send `graph.html` and
`GRAPH_REPORT.md` back to the user as files when the run ends.

## Notes

- Graphify is third-party software from Graphify-Labs (Apache-2.0), not Anthropic.
- To upgrade, change the pinned version `0.9.95` in this file after checking the
  release notes at https://github.com/Graphify-Labs/graphify/releases.
