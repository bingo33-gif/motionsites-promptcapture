# Installation

## Requirements

- Codex (CLI or desktop app) — or any Agent Skills-compatible client
- Python 3.9+ (only required for the skill-installer script)

## Method 1: skill-installer

Install directly from this repository:

```powershell
python "${HOME}\.codex\skills\.system\skill-installer\scripts\install-skill-from-github.py" --repo bingo33-gif/motionsites-promptcapture --path . --name motionsites-promptcapture
```

The skill will be installed to `~/.codex/skills/motionsites-promptcapture`.

## Method 2: Manual clone / copy

```powershell
git clone https://github.com/bingo33-gif/motionsites-promptcapture.git "${HOME}\.codex\skills\motionsites-promptcapture"
```

Or copy the folder manually:

```bash
# macOS / Linux
cp -r motionsites-promptcapture ~/.codex/skills/
```

## Verification

1. Restart Codex, or open a new task.
2. Check that `motionsites-promptcapture` appears in the skills list.
3. Say: *“I need you to create a website and use UI design.”*
4. The skill should respond by browsing motionsites.ai and presenting a prompt + optimization plan.

## Uninstall

Delete the skill directory:

```powershell
Remove-Item -Recurse "${HOME}\.codex\skills\motionsites-promptcapture"
```

## Compatibility notes

- Codex: native support.
- Claude Code / Cursor and other Agent Skills-compatible clients: the `SKILL.md` + `agents/` structure is portable, but this repository does not ship `.claude/` wrappers.
