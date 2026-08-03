<div align="center">

# motionsites-promptcapture

> “别从空白提示词开始。让 MotionSites 先给你设计语言，再把它变成你自己的。”

[![Codex](https://img.shields.io/badge/Codex-Skill-111111)](#)
[![Agent Skills](https://img.shields.io/badge/Agent%20Skills-Compatible-6B7280)](#)
[![License](https://img.shields.io/badge/License-MIT-F7C948)](#)
[![Validate skill](https://github.com/bingo33-gif/motionsites-promptcapture/actions/workflows/validate-skill.yml/badge.svg)](https://github.com/bingo33-gif/motionsites-promptcapture/actions/workflows/validate-skill.yml)

一个把「我需要一个网站并且要用到 UI 设计」变成「精选 MotionSites 提示词 + 可执行实现方案」的 Codex skill。

落地页、SaaS 官网、作品集不知道视觉方向怎么定？  
复制通用 AI 提示词，得到千篇一律的结果？  
看到惊艳的动态网站，却不知道怎么落到自己的技术栈？

本 skill 会前往 [motionsites.ai](https://motionsites.ai) 找到真正匹配你需求的提示词，说明为什么匹配，并给出适配你项目的优化方案。

[安装](#安装) · [快速使用](#快速使用方式) · [工作流](#推荐工作流) · [能力](#当前能力) · [搭配 Skills](#推荐搭配-skills) · [目录结构](#推荐目录结构) · [设计原则](#设计原则) · [限制](#当前限制) · [兼容性](#兼容性) · [English](./README.md)

</div>

## 安装

### 方式 1：使用 Codex skill-installer 直接安装

```powershell
python "${HOME}\.codex\skills\.system\skill-installer\scripts\install-skill-from-github.py" --repo bingo33-gif/motionsites-promptcapture --path . --name motionsites-promptcapture
```

### 方式 2：克隆到本地 skills 目录

```powershell
git clone https://github.com/bingo33-gif/motionsites-promptcapture.git "${HOME}\.codex\skills\motionsites-promptcapture"
```

安装后重启 Codex（或新开一个任务），skill 会被自动发现。更详细的说明见 [INSTALL.md](./INSTALL.md)。

## 快速使用方式

1. 把本仓库链接复制给 Codex，让它帮你安装这个 skill。
2. 在 Codex 中打开你的项目文件夹。
3. 直接说：`我需要你创建一个网站并且要用到UI设计`。
4. 告诉 Codex 网站类型、视觉风格和技术栈（也可以让它先问你）；skill 会找到匹配的提示词并给出优化方案。

只有在你确认方案后，skill 才会进入实现阶段。

## 推荐搭配 Skills

- `figma`（插件）——已有设计稿时，从 Figma 拉取设计上下文
- `frontend-app-builder`（Build Web Apps 插件）——按确认的方案实现高质量 UI
- `playwright` / `frontend-testing-debugging`——用真实浏览器验证动效、响应式和控制台错误

## 当前能力

- 需求提炼：网站类型、视觉风格、动效需求、技术栈
- MotionSites 提示词检索：按「分类 + 风格 + 动效」匹配
- 原样输出提示词并说明匹配理由
- 优化方案：技术栈迁移、动效落地（GSAP ScrollTrigger + Lenis）、视觉资产、浏览器验证

## 推荐工作流

1. 澄清需求。
2. 浏览 motionsites.ai，选出 1–3 个匹配的提示词。
3. 展示提示词并说明匹配理由。
4. 给出优化方案。
5. 用户确认后才开始实现。
6. 用浏览器测试验证结果。

## 推荐目录结构

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

## 设计原则

1. 绝不编造提示词——只展示 motionsites.ai 上真实存在的内容。
2. 提示词原文保持原样；优化的是方案，不是原文。
3. 提示词要匹配用户真实的技术栈和约束。
4. 交付前必须用浏览器验证，而不是直接宣称完成。

## 当前限制

- motionsites.ai 是 JavaScript 渲染的站点，浏览时可能需要 in-app browser。
- skill 每次使用都读取实时站点而不是缓存内容，提示词会随站点更新而变化。
- 本 skill 负责「找提示词 + 给方案」，不直接生成网站。

## 兼容性

- Codex：原生适配。
- 其他兼容 Agent Skills 的客户端（Claude Code、Cursor 等）：`SKILL.md` + `agents/` 结构可移植。

## 贡献

仓库内置 GitHub Actions（`.github/workflows/validate-skill.yml`），每次 push 和 PR 都会校验 `SKILL.md` 与 `agents/openai.yaml`。本地运行同样的校验：

```bash
pip install pyyaml
python .github/scripts/quick_validate.py .
```

## License

MIT
