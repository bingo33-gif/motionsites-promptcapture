# motionsites-promptcapture

[![Validate skill](https://github.com/bingo33-gif/motionsites-promptcapture/actions/workflows/validate-skill.yml/badge.svg)](https://github.com/bingo33-gif/motionsites-promptcapture/actions/workflows/validate-skill.yml)

Find the right [motionsites.ai](https://motionsites.ai) prompt for your next website and get an actionable optimization plan — without leaving your coding agent.

`motionsites-promptcapture` is a Codex skill (Agent Skills format) that turns a simple request like *"I need a website with great UI design"* into:

1. the best-matching prompt from MotionSites,
2. a clear rationale for that pick, and
3. a step-by-step plan for adapting it to your tech stack.

> 中文说明见 [README.zh-CN.md](README.zh-CN.md).

## What it does

- **Understands your request** — site type (SaaS, agency, portfolio, landing page, hero section…), visual style, animation needs, and tech stack.
- **Finds the right prompt** — browses motionsites.ai by category and style, then selects the 1–3 most relevant templates.
- **Shows the original prompt verbatim** — never rewritten or fabricated, with a note on why it fits.
- **Plans the implementation** — tech-stack migration (default: React + Tailwind + shadcn/ui), animation guidance (GSAP ScrollTrigger + Lenis), visual assets, and browser-based verification.

## Installation

Copy the `motionsites-promptcapture` folder into your Codex skills directory:

```bash
# Windows
Copy-Item -Recurse .\motionsites-promptcapture "$env:USERPROFILE\.codex\skills\"

# macOS / Linux
cp -r motionsites-promptcapture ~/.codex/skills/
```

Restart Codex (or open a new task) and the skill will be available.

## Usage

Ask for a website that involves UI design — for example:

- "I need you to create a website and use UI design."
- "I want to build a SaaS landing page; find a MotionSites prompt for me."
- "Create a portfolio site with an animated hero section and give me a plan first."

The skill returns the recommended prompt plus an optimization plan. It only starts implementing after you confirm.

## Contributing

A GitHub Actions workflow (`.github/workflows/validate-skill.yml`) validates `SKILL.md` and `agents/openai.yaml` on every push and pull request. Run the same check locally:

```bash
pip install pyyaml
python .github/scripts/quick_validate.py .
```

## License

MIT
