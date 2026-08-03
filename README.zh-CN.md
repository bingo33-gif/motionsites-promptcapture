# motionsites-promptcapture

Codex skill：当用户提出网站 / UI 设计需求时，自动前往 [motionsites.ai](https://motionsites.ai) 查找匹配的提示词模板，并输出「推荐 prompt + 针对用户技术栈的优化方案」。

> 英文版说明见 [README.md](README.md)。

## 功能

- 提炼用户需求（网站类型、视觉风格、动效、技术栈）
- 访问 motionsites.ai 检索匹配的 prompt（SaaS、Agency、Portfolio、落地页、Hero 区块等分类）
- 完整展示 prompt 原文并说明匹配理由
- 输出优化方案：技术栈适配、动效实现（GSAP ScrollTrigger + Lenis）、视觉资产、浏览器验证

## 安装

将 `motionsites-promptcapture` 目录复制到 Codex skills 目录：

```bash
# Windows
Copy-Item -Recurse .\motionsites-promptcapture "$env:USERPROFILE\.codex\skills\"

# macOS / Linux
cp -r motionsites-promptcapture ~/.codex/skills/
```

重启 Codex（或新开一个任务）后生效。

## 触发示例

- 「需要你创建一个网站并且要用到UI设计」
- 「我要做一个 SaaS 落地页，帮我从 MotionSites 找提示词」
- 「帮我做一个带 Hero 动效的作品集网站，先给我方案」

## 说明

本 skill 只负责「找 prompt + 给优化方案」，用户确认后才进入实现阶段。Prompt 原文保持原样，不做编造。

## License

MIT
