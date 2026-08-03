---
name: motionsites-promptcapture
description: "Use when the user asks to create a website (landing page, SaaS site, portfolio, agency site, hero section, etc.) and mentions UI design, or explicitly asks to find website prompts from motionsites.ai. Go to https://motionsites.ai, find the most relevant prompt template for the user's request, and deliver the prompt plus an optimization plan adapted to the user's tech stack. Triggers on natural language like '需要你创建一个网站并且要用到UI设计', '创建一个网站，要用到UI设计', '帮我从 MotionSites 找合适的 prompt', '做一个带动效的落地页'. Do not use for plain coding tasks without UI/website design needs."
---

# MotionSites Prompt Capture

## 目标

用户提出网站/UI 设计需求时，去 motionsites.ai 找到匹配的提示词模板，并给出针对用户项目的优化方案。本 skill 的输出是「推荐 prompt + 优化方案」，不是直接写代码。

## 工作流

### 1. 提炼需求

先确认关键信息，缺失时按合理默认继续，不要反复追问：

- 网站类型：落地页 / SaaS 官网 / 作品集 / Agency 站点 / Hero 区块 / 电商页等
- 视觉风格：暗色、玻璃态、渐变、极简、3D、粒子背景等
- 动效需求：滚动动画、视差、平滑滚动、3D 交互等
- 内容结构：需要哪些区块（导航、Hero、特性、定价、页脚等）
- 技术栈：默认 React/Next.js + Tailwind + shadcn/ui（Build Web Apps 插件环境）；用户指定其他栈则以其为准

### 2. 访问 motionsites.ai

- 优先使用 in-app browser（用户已打开或可用时）打开 https://motionsites.ai/ 并浏览分类（SaaS、Agency、Portfolio、Landing pages、Hero sections 等）。
- 浏览器不可用时，用 open_page 或 web search 获取页面信息。注意该站是 JS 渲染的 SPA，静态抓取可能拿不到分类内容，此时说明使用浏览器查看更准确。
- 按「类型 + 风格 + 动效」三个维度筛选，找出 1-3 个最匹配的 prompt。

### 3. 输出推荐 prompt

- 完整展示选中的 prompt 原文，不要改写、不要翻译。
- 说明每个 prompt 的匹配理由（为什么适合用户的需求）。
- 找不到完全匹配时，选择最接近的并明确指出差异点；绝不编造不存在的 prompt。

### 4. 给出优化方案

围绕用户真实项目逐条列出优化点：

- **技术栈适配**：prompt 默认面向 Lovable/Bolt/Cursor/Claude，说明如何迁移到用户栈（默认 React + Tailwind + shadcn/ui；组件拆分、设计 token 复用）。
- **动效实现**：motionsites 常用 GSAP ScrollTrigger + Lenis 平滑滚动；给出落地时的关键取舍（性能、降级、无障碍、prefers-reduced-motion）。
- **视觉资产**：需要 Hero 图、纹理、图标时，说明可用 imagegen 生成或从提示词要求的资源引入。
- **验证方式**：实现后用 playwright / frontend-testing-debugging 做浏览器验证（响应式、动效、console 错误）。
- **风险提示**：指出 prompt 中可能不适用于当前项目的部分（依赖、性能开销、内容占位）。

### 5. 收尾

最后询问用户是否按优化方案开始实现；用户确认前不要写代码。

## 触发示例

- 「需要你创建一个网站并且要用到UI设计」
- 「我要做一个 SaaS 落地页，帮我从 MotionSites 找提示词」
- 「帮我做一个带 Hero 动效的作品集网站，先给我方案」

## 注意事项

- 不要跳过「找 prompt」直接写代码。
- Prompt 原文保持原样；优化方案针对用户项目，默认不改写 prompt 本身，除非用户要求。
- 优先用浏览器真实浏览 motionsites.ai 再选择，避免凭记忆猜测站点内容。
