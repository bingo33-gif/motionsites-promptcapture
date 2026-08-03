# motionsites-promptcapture

[![Validate skill](https://github.com/bingo33-gif/motionsites-promptcapture/actions/workflows/validate-skill.yml/badge.svg)](https://github.com/bingo33-gif/motionsites-promptcapture/actions/workflows/validate-skill.yml)

A Codex skill that finds matching prompt templates on [motionsites.ai](https://motionsites.ai) when you ask for a website / UI design, then delivers the prompt plus an optimization plan adapted to your tech stack.

> 中文版说明见 [README.zh-CN.md](README.zh-CN.md).

## Features

- Extracts your requirements (site type, visual style, animations, tech stack)
- Browses motionsites.ai to find matching prompts (SaaS, Agency, Portfolio, landing pages, hero sections, and more)
- Shows the original prompt verbatim with a matching rationale
- Provides an optimization plan: tech-stack adaptation, animation implementation (GSAP ScrollTrigger + Lenis), visual assets, and browser verification

## Installation

Copy the `motionsites-promptcapture` folder into your Codex skills directory:

```bash
# Windows
Copy-Item -Recurse .\motionsites-promptcapture "$env:USERPROFILE\.codex\skills\"

# macOS / Linux
cp -r motionsites-promptcapture ~/.codex/skills/
```

Restart Codex (or open a new task) and the skill will be available.

## Trigger examples

- "I need you to create a website and use UI design"
- "I want to build a SaaS landing page, find a prompt from MotionSites for me"
- "Create a portfolio site with an animated hero section and give me a plan first"

## How it works

This skill is responsible for "find prompt + deliver optimization plan" only. It does not start implementing until you confirm. Original prompts are preserved verbatim and never fabricated.

## Contributing

This repository includes a GitHub Actions workflow ([`.github/workflows/validate-skill.yml`](.github/workflows/validate-skill.yml)) that validates `SKILL.md` and the agent metadata on every push and pull request. Run the same check locally with:

```bash
pip install pyyaml
python .github/scripts/quick_validate.py .
```

## License

MIT
