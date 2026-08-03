<div align="center">

# motionsites-promptcapture

> “Don't start from a blank prompt. Let MotionSites show you the design language — then make it yours.”

[![Codex](https://img.shields.io/badge/Codex-Skill-111111)](#)
[![Agent Skills](https://img.shields.io/badge/Agent%20Skills-Compatible-6B7280)](#)
[![License](https://img.shields.io/badge/License-MIT-F7C948)](#)
[![Validate skill](https://github.com/bingo33-gif/motionsites-promptcapture/actions/workflows/validate-skill.yml/badge.svg)](https://github.com/bingo33-gif/motionsites-promptcapture/actions/workflows/validate-skill.yml)

A Codex skill that turns *“I need a website with great UI design”* into a curated MotionSites prompt and a concrete implementation plan.

Stuck on the visual direction for your landing page, SaaS site, or portfolio?  
Copying generic AI prompts and getting generic results?  
Wondering how to turn a beautiful animated-site prompt into something that fits your stack?

This skill goes to [motionsites.ai](https://motionsites.ai), finds the prompt that actually matches your request, explains why it fits, and gives you a plan to adapt it to your project.

[Install](#installation) · [Quick start](#quick-start) · [Workflow](#recommended-workflow) · [Capabilities](#current-capabilities) · [Companion skills](#recommended-companion-skills) · [Directory](#directory-structure) · [Principles](#design-principles) · [Limitations](#current-limitations) · [Compatibility](#compatibility) · [中文版](./README.zh-CN.md)

</div>

## Installation

### Method 1: Codex skill-installer

```powershell
python "${HOME}\.codex\skills\.system\skill-installer\scripts\install-skill-from-github.py" --repo bingo33-gif/motionsites-promptcapture --path . --name motionsites-promptcapture
```

### Method 2: Clone into your skills directory

```powershell
git clone https://github.com/bingo33-gif/motionsites-promptcapture.git "${HOME}\.codex\skills\motionsites-promptcapture"
```

Restart Codex (or open a new task) and the skill will be discovered automatically. More details in [INSTALL.md](./INSTALL.md).

## Quick start

1. Copy this repository link to Codex and let it install the skill for you.
2. Open your project folder in Codex.
3. Say: *“I need you to create a website and use UI design.”*
4. Tell Codex the site type, visual style, and tech stack (or let it ask); the skill will find the matching prompt and present an optimization plan.

The skill only starts implementing after you confirm the plan.

## Recommended companion skills

- `figma` (plugin) — pull design context from Figma when you already have a design file
- `frontend-app-builder` (Build Web Apps plugin) — implement the approved plan with high-quality UI
- `playwright` / `frontend-testing-debugging` — verify animations, responsiveness, and console errors in a real browser

## Current capabilities

- Requirement extraction: site type, visual style, animation needs, tech stack
- MotionSites prompt discovery: category + style + motion matching
- Verbatim prompt output with a matching rationale
- Optimization plan: stack migration, animation guidance (GSAP ScrollTrigger + Lenis), visual assets, browser verification

## Recommended workflow

1. Clarify the request.
2. Browse motionsites.ai and select 1–3 matching prompts.
3. Present the prompt(s) with a rationale.
4. Deliver the optimization plan.
5. Implement only after user confirmation.
6. Verify the result with browser testing.

## Directory structure

```text
motionsites-promptcapture/
├── SKILL.md
├── INSTALL.md
├── README.md
├── README.zh-CN.md
├── LICENSE
├── agents/
│   └── openai.yaml
└── .github/
    ├── scripts/
    │   └── quick_validate.py
    └── workflows/
        └── validate-skill.yml
```

## Design principles

1. Never fabricate a prompt — only show what actually exists on motionsites.ai.
2. Keep the original prompt verbatim; optimize the plan, not the source text.
3. Match the prompt to the user's real stack and constraints.
4. Recommend browser verification before calling a UI done.

## Current limitations

- motionsites.ai is a JavaScript-rendered site; browsing it may require the in-app browser.
- The skill reads the live site on each use rather than relying on cached content, so prompts can change as the site evolves.
- The skill delivers prompts + plans; it does not generate sites by itself.

## Compatibility

- Codex: native support.
- Other Agent Skills-compatible clients (Claude Code, Cursor, etc.): the `SKILL.md` + `agents/` structure is portable.

## Contributing

A GitHub Actions workflow (`.github/workflows/validate-skill.yml`) validates `SKILL.md` and `agents/openai.yaml` on every push and pull request. Run the same check locally:

```bash
pip install pyyaml
python .github/scripts/quick_validate.py .
```

## License

MIT
